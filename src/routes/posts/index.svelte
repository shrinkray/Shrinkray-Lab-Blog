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

<!-- Below: TailwindUI Simple, centered branded component. Added classes
'card' & 'card-body' to pick up DaisyUI styles-->

<div class="bg-indigo-700 mb-20 card">
  <div class="max-w-2xl mx-auto text-center py-16 px-4 sm:py-20 sm:px-6 lg:px-8 card-body">
    <h2 class="text-3xl font-extrabold text-white sm:text-4xl">
      <span class="block">Boost your productivity.</span>
      <span class="block">Start using Workflow today.</span>
    </h2>
    <p class="mt-4 text-lg leading-6 text-indigo-200">Ac euismod vel sit maecenas id pellentesque eu sed consectetur. Malesuada adipiscing sagittis vel nulla nec.</p>
    <a href="/home" class="mt-8 w-full inline-flex items-center justify-center px-5 py-3 border border-transparent text-base font-medium rounded-md text-indigo-600 bg-white hover:bg-indigo-50 sm:w-auto">
      Sign up for free
    </a>
  </div>
</div>

<h1 class='text-4xl mb-10 font-extrabold'>Shrinkray Labs Blog</h1>

<div class='grid grid-flow-row-dense grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-4'>
{#each posts as { title, slug, excerpt, coverImage, tags }}
  <div class="card text-center shadow-2xl mb-20">
    <figure class="px-10 pt-10">
      <img
				class="rounded-xl"
				src={coverImage.url}
				alt={`Cover image for ${title}`}
			/>
    </figure>
		<div class='card-body'>
			<h2 class='text-2xl font-bold'>{title}</h2>
			<p>{excerpt}</p>
			<div class='flex justify-center mt-5 space-x-2'>
				{#each tags as tag}
					<span
						class='badge badge-primary text-white'>
						{tag}
					</span>
				{/each}
			</div>
			<div class='justify-center card-actions'>
				<a
					class='btn btn-outline btn-primary'
					href={`/posts/${slug}`}>
					Read 👉🏼
				</a>
			</div>
		</div>
  </div>
{/each}
	</div>