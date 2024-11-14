<script lang="ts">
	const content = `
<a href="/about">Won't reload</a>
<a href="/docs">Will reload</a>
`;

	let shouldReload = false;
</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<!-- svelte-ignore a11y_click_events_have_key_events -->
<!-- svelte-ignore a11y_no_static_element_interactions -->
<section data-sveltekit-reload={shouldReload} onclick={(event) => {
	const isAnchorElement = event.target && 'href' in event.target;
	if (isAnchorElement) {
		const url = new URL((event.target as HTMLAnchorElement).href);
		shouldReload = url.pathname.startsWith('/docs');
	}
}}>
  {@html content}
</section>

<style>
	section {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		flex: 0.6;
	}

	h1 {
		width: 100%;
	}

	.welcome {
		display: block;
		position: relative;
		width: 100%;
		height: 0;
		padding: 0 0 calc(100% * 495 / 2048) 0;
	}

	.welcome img {
		position: absolute;
		width: 100%;
		height: 100%;
		top: 0;
		display: block;
	}
</style>
