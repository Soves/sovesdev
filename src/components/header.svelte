<script lang="ts">
    import Navigation from "./navigation.svelte";

    interface Page {
        name: string;
        url: string;
    }

    export let pages: Page[];

    let navActive = false;

    function toggleNav()
    {
        navActive = !navActive;
    }

    //transition
    import { fade } from 'svelte/transition';
    function crossFade(node: any){
		return {
			duration: 2000
		};
	}

</script>

<main lang="ts">
    <header>
        <div class="start">
            <slot></slot>
        </div>
        <div class="center"></div>

        <div class="end">
            <div class="burger" on:click={toggleNav}>
                <div class="{navActive === true ? 'bar a active' : 'bar a'}"/>
                <div class="{navActive === true ? 'bar b active' : 'bar b'}"/>
                <div class="{navActive === true ? 'bar c active' : 'bar c'}"/>
            </div>
        </div>
        
        <div class="{navActive === true ? 'nav active' : 'nav'}">
            <Navigation pages={pages} pageCallback={toggleNav}/>
        </div>
    </header>


</main>

<style>
    header {
        padding: 0;
        margin: 0;
        background-color: #0a0015;
        display: flex;
        height: 50px;
        width: 100vw;
        margin-bottom: 50px;

        position: fixed;
        top: 0;

        z-index: 1;
        
    }

    .start {
        display: flex;
        flex-direction: row;
        align-items: center;
        background-color: #0a0015;

        padding: 0px 20px;
    }

    .center {
        display: flex;
        flex-direction: row;
        flex: 1;

        background-color: #0a0015;

        transition: 1s;
    }

    .end {
        display: flex;
        justify-content: flex-end;
        flex: none;
        background-color: #0a0015;

        padding: 0px 20px;
    }

    .nav {
        position: absolute;
        flex-direction: row;
        right: -100vw;
        width: 25vw;
        height: 100vh;
        top: 50px;

        transition: 1s;
        
        
        
        transform-origin: top right;
    }

    @media only screen and (max-width: 600px) {
        .nav {
            width: 100%;
        }
    }

    .nav.active{
        right: 0px;
        transition: 1s;
        
    }

    .burger {
        display: flex;
        width: 50px;
        height: 100%;
        align-items: center;
        justify-content: center;

        flex-direction: column;
    }

    .bar {
        position: absolute;
        background-color: #b92855;
        width: 25px;
        height: 5px;

        border-radius: 50px;

        transition: 1s;
        
    }

    .bar.active {
        background-color: white;
        
    }

    .bar.a {
        transform: translateY(-10px);
    }

    .bar.b {
        transform: translateY(10px);
    }

    .bar.c {
        transform: translateY(0px);
    }

    .bar.a.active{
        transform: rotate(45deg);
    }

    .bar.b.active{
        transform: rotate(-45deg);
    }

    .bar.c.active{
        transform: rotate(45deg);
    }

</style>