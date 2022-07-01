<script lang="ts">
	interface Image {
		title: string;
		description: string;
		path: string;
		link: string;
		height: number;
	}

	interface Column {
		images: Image[];
	}

	export let columns: Column[];

	let margin = 0.05;

	let w: number;
</script>

<main>
	{#each columns as column}
		<div class="column" style="width: {(1 / columns.length - margin) * 100}%;" bind:clientWidth={w}>
			{#each column.images as image}
				<a href={image.link}>
					<div class="image" style="height: {w * image.height}px; margin: {margin * 100}%;">
                        
						<div
							class="image-background"
							style='background-image: url({image.path}); height: {w * image.height}px;'
                        />

                        <div
							class="image-glow"
							style="background-image: url({image.path}); width: {100-margin*100 * 2}%;height: {w * image.height}px; margin-top: {-w * image.height}px;"
						/>
                        
                        <h4 class="image-title" style="margin-top: {-w * image.height}px">{image.title}</h4>
                        
                        
						<h5 class="image-desc" style="margin-top: {-w * image.height}px">
							{image.description}
						</h5>
                        
					</div>
				</a>
			{/each}
		</div>
	{/each}
</main>

<style>
	a {
		text-decoration: none;
	}

	main {
		display: flex;
		justify-content: center;
		
	}

	.column {
		display: flex;

		flex-direction: column;
		max-width: 400px;
	}

	.image-background {
		background-repeat: no-repeat;
		background-position: center;
		background-size: cover;
        transition: .2s;

        opacity: 1;
	}

	.image {
		user-select: none;
	}

    .image-glow {
        opacity: 0.35;
        filter: blur(40px);
        
        position: absolute;
        
        

		background-size: cover;
		background-repeat: no-repeat;
		background-position: center;

		z-index: 1;
		transition: opacity 0.2s;
    }

	.image-title,
	.image-desc {
		user-select: none;

		display: flex;

		width: 100%;
		height: 100%;

		opacity: 0;

		filter: drop-shadow(5px 5px 3px black);

		transform: scale(0.5);
		transition: .2s;

		align-items: center;

		user-select: none;
		
	}

	.image-title {
		justify-content: center;

		color: #b92855;
		margin-bottom: 60px;

        white-space: nowrap;

        text-decoration: underline;
        text-underline-offset: 5px;
        text-decoration-color: #68480b;
		z-index: 3;
	}

	.image-desc {
        justify-content: center;
		color: #ffba00;
        
		white-space: pre-line;
		z-index: 3;
	}

	.image:hover .image-title {
		opacity: 1;
		transition: 0.2s;
		transform: scale(1.4);
	}

	.image:hover .image-desc {
		opacity: 1;
		transition: 0.2s;
		transform: scale(1);
	}

	.image:hover .image-background {
		opacity: 0.2;
		transition: .1s;
		
        transform: scale(0.95);
	}

	.image:hover .image-glow {
		opacity: 0.0;
		transition: 0.2s;
	}

</style>
