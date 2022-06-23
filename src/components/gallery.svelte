<script lang="ts">

    interface Image {
        title: string;
        path: string;
        link: string;
        height: number;
    }

    interface Column {
        images: Image[]
    }

    export let columns: Column[];

    let margin = 0.05;

    let w: number;
</script>

<main>
    {#each columns as column}
        <div class="column" 
            style="width: {(1/columns.length - margin) * 100}%;"
            bind:clientWidth={w}>

            {#each column.images as image}
                <a href={image.link}>
                    <div class="image" style="height: {w*image.height}px; margin: {margin * 100}%;">
                        <div class="image-background" style="background-image: url({image.path}); height: {w*image.height}px;" />
                        <h4 class="image-title" style="margin-top: {-w*image.height}px">{image.title}</h4>
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
    }

    .image {
        transition: .25s;
        opacity: .8;
    }

    .image:hover {
        opacity: 1;

        transition: .25s;
        transform: scale(1.05);
    }

    .image-title {
        user-select: none;
        
        display: flex;
        
        width: 100%;
        height: 100%;
        
        align-items: center;
        justify-content: center;

        color: #ffba00;
        opacity: 0;

        filter: drop-shadow(5px 5px 4px black);
        
        transition: .25s;
    }

    .image:hover .image-title{
        opacity: 1;
        transition: .25s;
        transform: scale(1.1);
    }

    .image:hover .image-background{
        opacity: 1;
        transition: .25s;
        filter: blur(3px);
    }

    
</style>