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