<script>
  import '../app.css'
  import '../prism.css'
  import 'focus-visible'
  import MoonIcon from 'heroicons-svelte/solid/MoonIcon.svelte'
  import SunIcon from 'heroicons-svelte/solid/SunIcon.svelte'
  import { browser } from '$app/env'
  import { name } from '$lib/info'

  let prefersLight = browser ? Boolean(JSON.parse(localStorage.getItem('prefersLight'))) : false
</script>

<div class="flex flex-col min-h-screen">
  <div class="mx-auto flex flex-col flex-grow w-full max-w-4xl" style="color: white">
      <div class="nav flex h-18 px-5 py-4 justify-between items-center">
        <h2 style="color: #677489">
          <a class="text-lg sm:text-2xl font-bold" href="/">
            {name}
          </a>
        </h2>
        {#if browser}
          <button
            type="button"
            role="switch"
            aria-label="Toggle Dark Mode"
            aria-checked={!prefersLight}
            class="h-4 w-4 sm:h-8 sm:w-8 sm:p-1"
            on:click={() => {
              prefersLight = !prefersLight
              localStorage.setItem('prefersLight', prefersLight.toString())

              if (prefersLight) {
                document.querySelector('html').classList.remove('dark')
              } else {
                document.querySelector('html').classList.add('dark')
              }
            }}
          >
            {#if prefersLight}
              <MoonIcon class="text-slate-500" />
            {:else}
              <SunIcon class="text-slate-400" />
            {/if}
          </button>
        {/if}
      </div>
      <main
        class="prose prose-slate prose-sm sm:prose sm:prose-slate sm:prose-lg sm:max-w-none dark:prose-invert flex flex-col w-full flex-grow py-4 px-4" style="margin-top: 0.5rem"
      > 
        <slot />
      </main>
    </div>
</div>

<style>
  @media only screen and (max-device-width: 768px) and (orientation: portrait)  {
    .nav {
      background-color: #FFE548;
    }
  }
</style>