<script>
  import ThemeSelect from './theme-select.svelte'
  export let pages
</script>

<div class="navbar mb-2 mt-4 shadow-lg bg-neutral text-neutral-content overflow-hidden">
  <div class="flex-none px-2 mx-2">
   <span class="text-lg font-bold"><a href={`/`} class='btn btn-ghost btn-sm rounded-btn'>
              <span class="text-red-700 text-3xl font-extrabold italic mr-1 -leading-3">S</span> Labs
          </a></span>
  </div>
  <div class="flex-1 px-2 mx-2">
    <div class="flex-auto">
      <!-- <a class="btn btn-ghost btn-sm rounded-btn"
         href={`/`}>Home</a> -->
      
      {#each pages as {title, slug}}
        <a class="btn btn-ghost btn-sm rounded-btn"
          href={`/${slug}`}>{title}</a>
      {/each}
    </div>
  </div>
  <div class='absolute top-0 right-0'>
    <ThemeSelect />
  </div>
</div>