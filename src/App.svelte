<svelte:head>
	<link rel="preconnect" href="https://fonts.gstatic.com">
<link href="https://fonts.googleapis.com/css2?family=Roboto:wght@100;300;400&display=swap" rel="stylesheet">
</svelte:head>

<script>
	import router from 'page';
	import { activeNavLink } from './stores';
	import { onDestroy } from 'svelte';

	import Home from './pages/Home.svelte';
	import About from './pages/About.svelte';
	import NotFound from './pages/NotFound.svelte';	

	router('/', () => page = Home);
	router('/about', () => page = About);	
	router('/*', () => page = NotFound);

	let page;
	let currentPage;

	const unsubscribe = activeNavLink.subscribe(active => {
		currentPage = active;
	});

	onDestroy(unsubscribe);
	router.start();
</script>


<nav>
	<a href='/'
		class={$activeNavLink === 'home' ? 'active' : ''}
		on:click={() => activeNavLink.set('home')}>
		Home
	</a>
	<a href='/about'
		class={$activeNavLink === 'about' ? 'active' : ''}
		on:click={() => activeNavLink.set('about')}>
		About
	</a>
</nav>

<svelte:component this={page} />

<style type="text/scss">
	@import 'public/global.scss';

	.active {
		color: #afe
	}

	nav {
		width: 100vw;
		display: flex;
		justify-content: center;

		a {
			font-size: 1.6rem;
			text-decoration: none;
			color: inherit;

			&:hover {
				color: #afe;
			}

			&:first-of-type {
				margin-right: 20px;
			}
		}
	}
</style>