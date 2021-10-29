<script lang="ts">
	import Tailwindcss from './Tailwindcss.svelte';
	import races from './races.json';

	// drawing race
	const drawHost =
		races.racecourse[Math.floor(Math.random() * races.racecourse.length)]
	const drawRacetrack = 
		drawHost.configurable[Math.floor(Math.random() * drawHost.configurable.length)]

	// race infomation
	const host = drawHost.host
	const racetrack = drawRacetrack.racetrack
	const distance = drawRacetrack.distance[Math.floor(Math.random() * drawRacetrack.distance.length)]
	const handed = drawRacetrack.handed[Math.floor(Math.random() * drawRacetrack.handed.length)]
	const course = drawRacetrack.course[Math.floor(Math.random() * drawRacetrack.course.length)]

	// race condition
	const condition = races.condition
	const season = condition.seasons[Math.floor(Math.random() * condition.seasons.length)]
	const weather = condition.weather[Math.floor(Math.random() * condition.weather.length)]
	const motivation = condition.motivation[Math.floor(Math.random() * condition.motivation.length)]
</script>

<Tailwindcss />
<main class="flex flex-col">
	<div class="flex justify-center content-center">
		<p class="p-4 text-xl">トレーナーズカップジェネレーター</p>
	</div>

  <div class="flex flex-wrap justify-center content-center">
		<div class="grid grid-cols-2 grid-rows-8">
			<p class="p-4 bg-green-300 border border-gray-800">開催地</p>
			<p class="p-4 bg-green-100 border border-gray-800">{host}</p>
	
			<p class="p-4 bg-green-300 border border-gray-800">バ場</p>
			<p class="p-4 bg-green-100 border border-gray-800">{racetrack}</p>
	
			<p class="p-4 bg-green-300 border border-gray-800">距離</p>
			<p class="p-4 bg-green-100 border border-gray-800">{distance}</p>
	
			<p class="p-4 bg-green-300 border border-gray-800">右回り・左回り</p>
			<p class="p-4 bg-green-100 border border-gray-800">{handed}</p>
	
			<p class="p-4 bg-green-300 border border-gray-800">内回り・外回り</p>
			<p class="p-4 bg-green-100 border border-gray-800">{course}</p>
	
			<p class="p-4 bg-green-300 border border-gray-800">季節</p>
			<p class="p-4 bg-green-100 border border-gray-800">{season}</p>
	
			<p class="p-4 bg-green-300 border border-gray-800">天気・バ場状態</p>
			<p class="p-4 bg-green-100 border border-gray-800">{weather}</p>
	
			<p class="p-4 bg-green-300 border border-gray-800">やる気</p>
			<p class="p-4 bg-green-100 border border-gray-800">{motivation}</p>
		</div>
	</div>

	<div class="flex justify-center content-center">
		<p class="p-4 text-sm">Copyright (c) 2021 hacusk</p>
	</div>

</main>
