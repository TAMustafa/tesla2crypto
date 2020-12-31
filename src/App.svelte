<script>
	import Tesla from "./components/Tesla.svelte";
	import Crypto from "./components/Crypto.svelte";
	import Result from "./components/Result.svelte";
	import Footer from "./components/Footer.svelte";

let tesla
let coin

	const handleTesla = (e) => {
		tesla = e.detail;
	};

	const handleCoin = (e) => {
		coin = e.detail;
	};

</script>

<style>
	main {
		max-width: 600px;
		margin: 10% auto;
		text-align: center;
	}

	footer {
		text-align: center;
	}

	img {
		width: 150px;
	}
</style>

<main>
	<Tesla on:teslaData={handleTesla} />
	<img src="/images/Tesla2Crypto.svg" alt="Test">
	<Crypto on:coinData={handleCoin} />

	{#if tesla && coin}
		<Result {coin} {tesla} />
	{/if}
</main>

<footer>
	<Footer />
</footer>
