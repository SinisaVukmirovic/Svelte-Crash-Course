<script>

	import { Router, Route } from 'svero'; 

	import Header from './Header.svelte';
	import Home from './pages/Home.svelte';
	import About from './pages/About.svelte';
	import Footer from './Footer.svelte';

</script>

<style>
	:global(body) {
		margin: 0;
		padding: 0;
		background-color: #333;
		color: #eee;
	}

	.container {
		width: 60%;
		margin: 4em auto;
	}
</style>

<!-- Mark Up -->

<Header />

<div class="container">

	<Router>
		<Route path="*" component={Home} />
		<Route path="/about" component={About} />
	</Router>

</div>

<Footer />