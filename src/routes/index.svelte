<script lang="ts">
	import Banner from '../components/banner.svelte';
	import Gallery from '../components/gallery.svelte';

	let games = [
		{
			images: [
				{
					title: 'Wally and the FANTASTIC PREDATORS',
					path: '/images/games/Wally.jpg',
					link: 'test',
					height: 0.5
				},
				{
					title: 'Craft Jam',
					path: '/images/games/Craft.gif',
					link: 'test',
					height: 1
				},
				{
					title: '-Sprout-',
					path: '/images/games/Sprout.jpg',
					link: 'test',
					height: 0.5
				}
			]
		},
		{
			images: [
				{
					title: 'Purple Desert',
					path: '/images/games/Purple.gif',
					link: 'test',
					height: 1
				},
				{
					title: "Duck 'n ufo",
					path: '/images/games/Duck.jpg', //find a higher rez pic
					link: 'test',
					height: 1.1
				}
			]
		}
	];
    let w: number = 0;
</script>

<Banner />

<svelte:window bind:innerWidth={w}/>

<h3 style="font-size: {Math.min(w, 20)}px">
    the website is under construction
</h3>

<h1 style="font-size: {Math.min(w, 30)}px">
    Projects:
</h1>

<Gallery columns={games} />

<style>
	h1 {
		color: #b92855;
		text-align: center;
	}
    h3 {
		color: #ffba00;
		text-align: center;
	}
</style>
