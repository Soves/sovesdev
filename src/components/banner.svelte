<script lang="ts">
	import { tweened } from 'svelte/motion';
	import { cubicOut } from 'svelte/easing';

	let rot = tweened(0, {
		duration: 600,
		easing: cubicOut
	});

	let y: number = 0;

	$: $rot = y;
</script>

<div class="banner">
	<div class="solar" />

    <div class="mountains">
		<div class="mtn-3" style="--yp: {Math.min(y*0.5 - 200, 0)}px"/>
		<div class="mtn-2" style="--yp: {Math.min(y*0.25 - 100, 0)}px"/>
		<div class="mtn-1" />
	</div>

    <div class="logo_anim" style="--rotation: {$rot}deg" />
	<div class="logo" />

    <div class="overlay" />
</div>

<svelte:window bind:scrollY={y} />

<style>
	.banner {
		display: flex;
		width: 100%;
		height: 100vh;

		align-items: center;
		justify-content: center;

        
	}

	.mountains {
        display: flex;

		width: 100%;
		height: 100%;

		align-items: flex-end;
        justify-content: flex-end;
	}

	.mtn-1 {
		position: absolute;

		width: 100%;
        height: 400px;

		background-image: url('/images/mtn_1.svg');
		background-position: bottom;
		background-size: 600px;
		background-repeat: repeat-x;
	}

	.mtn-2 {
		position: absolute;

		width: 100%;
        height: 400px;

		background-image: url('/images/mtn_2.svg');
		background-position: bottom;
		background-size: 600px;
		background-repeat: repeat-x;

        transform: translateY(var(--yp));
	}

	.mtn-3 {
		position: absolute;

		width: 100%;
		height: 400px;
        
		background-image: url('/images/mtn_3.svg');
		background-position: bottom;
		background-size: 600px;
		background-repeat: repeat-x;

        transform: translateY(var(--yp));
	}

	.filler {
		position: absolute;
		width: 100%;
		height: 30%;    

        bottom: 0;

        background-color: black;
	}

	.solar {
		position: absolute;
		width: 100%;
		height: 100%;

		background-image: url('/images/solar.svg');
		background-position: center;
		background-size: contain;
		background-repeat: no-repeat;
        
	}

	.logo_anim {
		position: absolute;

		width: 25%;
		height: 25%;

		max-width: 150px;

		transform: rotateZ(var(--rotation));

		max-width: 150px;

		background-image: url('/images/logo_anim.svg');
		background-position: center;
		background-size: contain;
		background-repeat: no-repeat;

		opacity: 20%;
	}

    .logo {
		position: absolute;

		width: 25%;
		height: 25%;

		max-width: 150px;

		background-image: url('/images/logo_plain.svg');
		background-position: center;
		background-size: contain;
		background-repeat: no-repeat;

		opacity: 80%;
	}

	.overlay {
		position: absolute;

		width: 100%;
		height: 100%;

		background-image: linear-gradient(to top, #0a0015ff, #5d450041);
	}
</style>
