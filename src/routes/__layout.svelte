<script lang="ts">
	import Header from '../components/header.svelte';
</script>

<Header pages={[
    {name: "home", url:"/"},
    {name: "about", url:"/about"},
]}>
    
    <img src="/images/logo.svg" height="75%" alt="soVes"/>
    <h1>soVes</h1>
</Header>

<div class="main">
    <slot />
</div>

<style>
	:global(body) { 
		margin: 0; 
		padding: 0;
		-ms-overflow-style: none;
		scrollbar-width: none;
		background-color: #0a0015;
	}

	:global(body)::-webkit-scrollbar {
		display: none;
	}

    .main {
        margin-top: 50px;
    }

    h1 {
        margin-left: 15px;
        font-size: 2em;
        color: #b92855;
        text-align: center;
    }
</style>