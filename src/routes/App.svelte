<script>
	import AudioPlayer from './AudioPlayer.svelte';
	import { tracks } from './tracks.js';
	let y
	import Split from 'split-grid';
	import { onMount } from 'svelte';
	import Image from './Image.svelte'

	// 	Mock API Data
	let colors = [
		"#fff989",
		"#89d9ff"
	]
	let deg = 45
	
	// 	Convert deg number to string for CSS
	$: degString = `${deg}deg`

	
	onMount(() => {
		Split({
			rowGutters: [{
				track: 1,
				element: rowSplitter,
			}],
			columnGutters: [{
				track: 1,
				element: columnSplitter,
			}],
		})
	});


	import Youtube from "svelte-youtube-embed";

  let overlayBGColor = "#e5a50a";
  let overlayTransitionDuration = 50;

  let titleColor = "#000000";
  let titleShadowColor = "#ffffff";
  let titleFontFamily = "'Segoe UI', Geneva, Verdana, sans-serif";

  let altThumb = false;
</script>

<div class="root">
	<div class="top-bar">
		Sol FitzGerald - Composer
	</div>
	<div class="top-right-bar">
		Game Music | Film Music
	</div>
	<div class="side-bar">
		<img src="https://solfitzgerald.github.io/Portfolio/Sol%20FitzGerald%20Photo.jpg"
			alt = "Sol FitzGerald"
			width = 100%;
	/>

		<p>
	Sol FitzGerald is a game and film composer, jazz pianist, and private music teacher primarily based in Boston and Baltimore. Coming from a background in jazz, Sol started their musical journey studying under Washington Capitals organist Bruce Anderson, learning piano performance, an understanding of jazz harmony and music theory, and composition. Sol continued to develop their skills in jazz piano and composition, eventually earning themselves an admission into Berklee College of Music with a full tuition scholarship. Now at Berklee, Sol studies Film and Media Scoring with a double major in Game and Interactive Media Scoring, and continues to expand their compositional abilities through film and game collaborations with students in MassArt, Emerson, Tufts, and Maryland Institute College of Art. 

			</p>

	<img src="https://solfitzgerald.github.io/Portfolio/IMG_3917.jpeg"
			alt = "Sol FitzGerald"
			width = 100%;
	/>
		
	</div>
	
	<div class="contents">
		
		{#each tracks as track}
		<AudioPlayer {...track} />
	{/each}

		<Youtube id="CW3ZGP0QlI4" />
	</div>

	<div class="row-splitter" bind:this={rowSplitter} />
	<div class="column-splitter" bind:this={columnSplitter} />
</div>


<style>
	p {
		color: white;
		font-family: '';
		font-size: 0.9em;
	}
	
	.centered {
		display: flex;
		flex-direction: column;
		height: 100%;
		justify-content: right;
		gap: 0.5em;
		max-width: 40em;
		margin-top: 50px;
	}
	.navbar {color: white; background: red; ; height: 50px; width: 100%;}
	.main {height: 200vh; background: yellow;  margin-top: 50px;}


	.root {
		display: grid;
		grid-template-areas:
			'top      top     top-right'
			'r-split  r-split r-split'
			'side     c-split contents';
		grid-template-rows: 55px 5px 1fr;
		grid-template-columns: 2fr 5px 3fr;
		width: 100%;
		height: 100%;
	}




	
	.top-bar {
		grid-area: top;
		background: #062e0e;
		text-align: center;
		font-family: 'Castoro Titling';
		font-size: 2em;
	}
	.side-bar {
		grid-area: side;
	}
	.top-right-bar {
		grid-area: top-right;
		background: #011204;
		text-align: center;
		font-family: 'Castoro Titling';
		font-size: 2em;
	}
	.contents {
		grid-area: contents;
	}	

	.row-splitter {
		grid-area: r-split;
	}

	.column-splitter {
		grid-area: c-split;
	}

</style>



<div class="container">
  
</div>


<svelte:window bind:scrollY={y} />

