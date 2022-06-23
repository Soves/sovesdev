<script lang="ts">
    import { page } from '$app/stores';
    
    interface Page {
        name: string;
        url: string;
    }

    export let pages: Page[];

    export let pageCallback: Function;
</script>

<main>
    <div class="pages">
        {#each pages as Page}
            <div class="{Page.url == $page.url.pathname ? 'page selected' : 'page'}">
                <a href={Page.url} on:click={pageCallback()}>
                    {Page.name}
                </a>
            </div>
        {/each}
    </div>
</main>

<style>

    main {
        position: relative;
        display: flex;
        width: 100%;
        height: 100vh;
        background-color: #0a0015;
        justify-content: center;
        margin: 0;
        padding: 0;
        align-items: center;
        text-align: center;
    }
    
    .pages{
        position: absolute;
        font-size: 1.5rem;
        padding: 0;
        width: 100%;
    }

    .page {
        display: flex;
        width: 100%;
        margin: 5px 0;
    }

    .page a {
        text-decoration: none;
        width: 100%;
        color: #ffba00;
        
        transition: 0.25s;
    }

    .page:hover a {
        text-decoration: none;
        color: white;
        transition: 0.25s;
    }

    .page.selected a {
        text-decoration: none;
        color: #0a0015;
        background-color: #b92855;
    }
    
</style>