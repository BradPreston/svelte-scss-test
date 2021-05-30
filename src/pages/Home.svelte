<svelte:head>
	<link rel="preconnect" href="https://fonts.gstatic.com">
<link href="https://fonts.googleapis.com/css2?family=Roboto:wght@100;300;400&display=swap" rel="stylesheet">
</svelte:head>

<script>
    import { activeNavLink } from '../stores.js';

    
</script>

<div class="wrapper">
    <h1>Home</h1>
    <a href='/about' on:click={() => activeNavLink.set('about')}>About</a>
</div>

<style lang="scss">
    @import 'public/global.scss';

    .wrapper {
        margin: 0 auto;
        text-align: center;
    }
</style>