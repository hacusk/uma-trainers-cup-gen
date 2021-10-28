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
<main>
	<h2 class="text-xl">トレーナーズカップジェネレーター</h2>

  <div class="h-screen grid grid-cols-2 grid-rows-8">
	<p>開催地:</p><p>{host}</p>
	<p>バ場:</p><p>{racetrack}</p>
	<p>距離:</p><p>{distance}</p>
	<p>右回り・左回り:</p><p>{handed}</p>
	<p>内回り・外回り:</p><p>{course}</p>
	<p>季節:</p><p>{season}</p>
	<p>天気・バ場状態:</p><p>{weather}</p>
	<p>やる気:</p><p>{motivation}</p>
	</div>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		margin: 0 auto;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>
