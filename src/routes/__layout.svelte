<script context="module">
	
  export const load = async ({ fetch }) => {
		const res = await fetch('/pages.json')
		if (res.ok) {
			const { pages } = await res.json()
			return {
				props: { pages },
			}
		}
	}
</script>

<script>
	import Nav from '$lib/nav.svelte'
	import Footer from '$lib/footer.svelte'
	import { onMount } from 'svelte'
	import { themeChange } from 'theme-change'
	import '../app.css'
	
	onMount(async () => {
		themeChange(false)
	})
	
	export let pages
</script>

<Nav {pages} />

<main class='container max-w-7xl mx-auto px-4 mb-12'>
	<slot />
</main>
<Footer {pages} />