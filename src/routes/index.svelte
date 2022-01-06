<script context="module">
  export const load = async ({ fetch }) => {
		const res = await fetch('/posts.json')
		if (res.ok) {
			const { posts } = await res.json()
			return {
				props: { posts },
			}
		}
	}
</script>

<script>
  export let posts
</script>

<svelte:head>
  <title>Shrinkray Labs Blog | Welcome</title>
</svelte:head>

<h1 class='text-4xl mb-10 font-extrabold'>Shrinkray Labs Blog</h1>

{#each posts as { title, slug, excerpt, coverImage, tags }}
  <div class="card text-center shadow-2xl mb-20">
    <figure class="px-10 pt-10">
      <img
				class="rounded-xl"
				src={coverImage.url}
				alt={`Cover image for ${title}`}
			/>
    </figure>
  </div>
{/each}