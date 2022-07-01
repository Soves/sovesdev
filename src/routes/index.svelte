<script lang="ts">
	import Banner from '../components/banner.svelte';
	import Gallery from '../components/gallery.svelte';

	let games = [
		{
			images: [
				{
					title: 'Wally and the FANTASTIC PREDATORS',
					description: '\
						rim lighting\n\
						shaders/effects\
					',
					path: '/images/games/Wally.jpg',
					link: 'https://store.steampowered.com/app/1077450/Wally_and_the_FANTASTIC_PREDATORS/',
					height: 0.5
				},
				{
					title: 'Craft Jam',
					description: '\
						techinal programming\n\
						audio synchronization \n\
						visual effects/techinal art\n\
					',
					path: '/images/games/Craft.gif',
					link: 'https://booon.itch.io/craft-jam',
					height: 1
				},
				{
					title: '-Sprout-',
					description: '\
						localization\n\
						Finnish translation\
					',
					path: '/images/games/Sprout.jpg',
					link: 'https://store.steampowered.com/app/1336340/SPROUT/',
					height: 0.5
				}
			]
		},
		{
			images: [
				{
					title: 'Purple Desert',
					description: '\
						3D background effects\n\
						technical art\n\
						menu UI/UX\n\
					',
					path: '/images/games/Purple.gif',
					link: 'https://booon.itch.io/purple-desert',
					height: 1
				},
				{
					title: "Duck 'n ufo",
					description: '\
						programming\n\
						music/sfx\n\
						art\n\
						everything\
					',
					path: '/images/games/Duck.jpg', //find a higher rez pic
					link: 'https://gamejolt.com/games/ducknufo/636265',
					height: 1.1
				}
			]
		}
	];
	let w: number = 0;
</script>

<Banner />

<div class="spacer">
	<h1 class="title">Games</h1>
</div>

<svelte:window bind:innerWidth={w} />

<Gallery columns={games} />

<div class="spacer">
	<div class="client s1" />
</div>


<style>
	h1 {
		color: #b92855;
		text-align: center;
	}
	h3 {
		color: #ffba00;
		text-align: center;
	}

	.spacer {
		width: 100%;
		height: 2px;

		background-color: #68480b;
		display: flex;
		justify-content: center;
		align-items: center;

		flex-direction: row;

		margin-top: 80px;
		margin-bottom: 100px;
	}

	.client {
		height: 120px;
		width: 140px;

		position: relative;

		background-position: center;
		background-size: contain;
		background-repeat: no-repeat;
	}

	.spacer .title {
		display: flex;
		align-items: center;
		justify-content: center;

		height: 140px;
		width: 150px;

		background-color: #0a0015;
		color: #68480b;
		font-size: 1.5em;
	}
	.s1 {
		border: solid 10px #0a0015;
		background-color: #0a0015;
		background-image: url('/images/redwood.png');
	}

	.s2 {
		border: solid 10px #0a0015;
		background-color: #0a0015;
		background-image: url('/images/logo.svg');
	}
</style>
