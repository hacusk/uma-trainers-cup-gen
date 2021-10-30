<script lang="ts">
	import Tailwindcss from './Tailwindcss.svelte';
	import races from './races.json';

	type drawResult = {
		label: string,
		value: string
	}

	let drawHost
	let drawRacetrack
	let drawResult: Array<drawResult>

	function draw() {
		// reset
		drawResult = []

		// drawing race
		drawHost =
			races.racecourse[Math.floor(Math.random() * races.racecourse.length)]
		drawRacetrack = 
			drawHost.configurable[Math.floor(Math.random() * drawHost.configurable.length)]

		// race infomation
		drawResult.push({label: "開催地", value: drawHost.host})
		drawResult.push({label: "バ場", value: drawRacetrack.racetrack})
		drawResult.push({
			label: "距離",
			value: drawRacetrack.distance[Math.floor(Math.random() * drawRacetrack.distance.length)]
		})
		drawResult.push({
			label: "右回り・左回り",
			value: drawRacetrack.handed[Math.floor(Math.random() * drawRacetrack.handed.length)]
		})
		drawResult.push({
			label: "内回り・外回り",
			value: drawRacetrack.course[Math.floor(Math.random() * drawRacetrack.course.length)]
		})

		// race condition
		const condition = races.condition
		drawResult.push({
			label: "季節",
			value: condition.seasons[Math.floor(Math.random() * condition.seasons.length)]
		})
		drawResult.push({
			label: "天気・バ場状態",
			value: condition.weather[Math.floor(Math.random() * condition.weather.length)]
		})
		drawResult.push({
			label: "やる気",
			value: condition.motivation[Math.floor(Math.random() * condition.motivation.length)]
		})
	}

	draw()
</script>

<Tailwindcss />
<main class="flex flex-col">
	<div class="flex justify-center content-center">
		<p class="m-4 text-xl">トレーナーズカップジェネレーター</p>
	</div>

  <div class="flex flex-wrap justify-center content-center">
		<div class="grid grid-cols-2 grid-rows-{drawResult.length}">
			{#each drawResult as result}
				<p class="p-4 bg-green-300 border border-gray-800">{result.label}</p>
				<p class="p-4 bg-green-100 border border-gray-800">{result.value}</p>
			{/each}
		</div>
	</div>
	<button on:click={draw} class="m-4 p-4 w-auto">再抽選</button>

	<div class="flex justify-center content-center">
		<p class="p-4 text-sm">Copyright (c) 2021 hacusk</p>
	</div>

</main>
