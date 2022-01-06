<script context="module">
	export const load = async ({ fetch }) => {
	const res = await fetch('/posts.json')
		if (res.ok) {
			const {posts} = await res.json()
			return {
				props: { posts },
			}
		}
	};
</script>

<script>
	export let posts;
</script>

<svelte:head>
	<title>Shrinkray Lab Blog | Welcome </title>
</svelte:head>

<h1 class='text-4xl mb-10 font-extrabold'>Welcome to SvelteKit</h1>

<!-- This works -->
<pre>{JSON.stringify(posts, null, 2)}</pre>

<!-- This is not returning data -->
{#each posts as {title, coverImage}}
	<div class='card text-center shadow-2xl mb-20'>
		<figure class='px-10 pt-10'>
			<img src={coverImage.url} alt= {`Cover image for ${title}`} />
		</figure>
	</div>
{/each}