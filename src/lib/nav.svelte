<script>
  import ThemeSelect from './theme-select.svelte'
  export let pages
</script>

<div class="navbar mb-2 shadow-lg bg-neutral text-neutral-content">
  <div class="flex-none px-2 mx-2">
   <span class="text-lg font-bold"><a href={`/`} class='btn btn-ghost btn-sm rounded-btn'>
            Shrinkray Labs
          </a></span>
  </div>
  <div class="flex-1 px-2 mx-2">
    <div class="items-stretch ">
      <a class="btn btn-ghost btn-sm rounded-btn"
         href={`/`}>Home</a>
      
      {#each pages as {title, slug}}
        <a class="btn btn-ghost btn-sm rounded-btn"
          href={`/${slug}`}>{title}</a>
      {/each}
    </div>
  </div>
  <div class='navbar-end'>
    <ThemeSelect />
  </div>
</div>