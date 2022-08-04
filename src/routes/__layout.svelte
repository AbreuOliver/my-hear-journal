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
  <div class="mx-auto flex flex-col flex-grow w-full" style="position: sticky; top: 0; display: flex; flex-direction: column; justifiy-content: center; align-items: center;">
    <div class="nav flex flex-col justify-between items-center border-b border-slate-900/15 lg:px-8 lg:border-0 dark:border-slate-300/15 lg:mx-0" style="position: sticky; top: 0; height: auto; width: 100vw;">
      <div class="flex h-18 px-5 py-4 justify-between items-center" id="navbar">
        <h2 style="flex-grow: 1;">
          {#if prefersLight}
            <a class="text-slate-500 text-lg sm:text-2xl font-bold" href="/">
              {name}
            </a>
          {:else}
            <a class="text-slate-400 text-lg sm:text-2xl font-bold" href="/">
              {name}
            </a>
          {/if}
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
      </div>
      <main
        class="prose prose-slate prose-sm sm:prose sm:prose-slate sm:prose-lg sm:max-w-none dark:prose-invert flex flex-col w-full flex-grow py-4 px-4" style="margin-top: 0.5rem; max-width: 70ch;"
      > 
        <slot />
      </main>
    </div>
</div>

<style>
  .nav {
    backdrop-filter: blur(5px) !important;
    position: sticky; top: 0 !important;
    z-index: 999;
  }

  @media (prefers-color-scheme: dark) {
    .nav {
      background-color: rgba(0, 0, 0, 0.8) !important;
    }
  }

  @media (prefers-color-scheme: light) {
    .nav {
      background-color: rgba(255, 255, 255, 0.9) !important;
    }
  }
  #navbar {
    width: 90vw; 
    max-width: 80ch; 
  }

  @media only screen and (max-device-width: 767px) and (orientation: portrait)  {
    #navbar {
      width: 100vw;
    }
  }
</style>