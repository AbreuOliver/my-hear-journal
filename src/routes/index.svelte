<script context="module">
  import * as readingPlan from '../../static/plan.json';

  export const prerender = true

  export const load = async ({ fetch }) => {
    return {
      props: {
        recentPosts: await fetch('/posts.json?limit=4').then((res) => res.json())
      }
    }
  }

  let currentdate = new Date();
  let oneJan = new Date(currentdate.getFullYear(), 0, 1);
  let numberOfDays = Math.floor((currentdate - oneJan) / (24 * 60 * 60 * 1000));
  let currentWeekNumberOfTheYear = Math.ceil((currentdate.getDay() + 1 + numberOfDays) / 7);
  let dayOfWeekName = new Date().toLocaleString('default', { weekday: 'long' })

  // console.log('Day of Week Name:', dayOfWeekName)

  let readingStatus = ''

  if (dayOfWeekName == 'Friday') {
    readingStatus = 'Meeting to discuss reading '
  } else if (dayOfWeekName == 'Saturday') {
    readingStatus = 'Started reading '
  } else {
    readingStatus = 'Currently reading '
  }


  let currentReadingWeek = ''

  if (dayOfWeekName == 'Saturday') {
    currentReadingWeek = currentWeekNumberOfTheYear;
  } else {
    currentReadingWeek = currentWeekNumberOfTheYear - 1;
  }

  // console.log("Week Number:", `${currentWeekNumberOfTheYear - 1}`);
  // console.log("Reading Status:", readingStatus);
  // console.log("Current Plan Week:", currentReadingWeek); 
  // console.log("Reading Plan", readingPlan.data)

  let readingPlanResult = readingPlan.data.find(e => e.week === currentReadingWeek);

  let memoryVerseResult = readingPlanResult.memoryVerses;

  // console.log("This weeks' reading plan is: ", readingPlanResult.plan);
  // console.log("This weeks' memory verses are: ", memoryVerseResult);

</script>

<script>
  import ButtonLink from '$lib/components/ButtonLink.svelte'
  import PostPreview from '$lib/components/PostPreview.svelte'
  import { name } from '$lib/info.js'

  export let recentPosts
</script>

<svelte:head>
  <title>{name}</title>
</svelte:head>

<div class="flex flex-col flex-grow">
  <!-- replace with a bio about you, or something -->
  <div class="flex flex-col items-start justify-start text-xl h-full">
    <h1 class="pt-6" style="margin-bottom: 0 !important">
      <span
        class="!text-transparent bg-clip-text bg-gradient-to-r from-blue-500 to-teal-500 dark:from-violet-500 dark:to-pink-500"
        >Study</span
      > to show thyself approved unto God.
    </h1>
    <h4 style="color: #485163; margin-bottom: 1.75rem">
      Observations and study notes from the F260 Bible reading plan using the <a style="text-decoration: underline" target="_blank" href="https://replicate.org/what-is-a-hear-journal/">H.E.A.R. journaling method</a>.<br /><br />
      <strong>Current Reading Status:</strong> <br />
      {readingStatus} plan for
      <strong
        ><span
          class="!text-transparent bg-clip-text bg-gradient-to-r from-blue-500 to-teal-500 dark:from-violet-500 dark:to-pink-500"
          >Week {currentReadingWeek}</span
        ></strong
      >
    </h4>
    <div style="margin-left: 1rem; margin-top: -2.15rem; margin-bottom: -2.5rem;">
      {#each readingPlanResult.plan as plan, index}
        <h4 style="font-family: monospace;">
          {#if prefersLight}
            <span class="text-slate-500">Day {index + 1}:</span>
          {:else}
            <span class="text-slate-400">Day {index + 1}:</span>
          {/if}
            {plan}
        </h4>
      {/each}
      <br style="margin-bottom: 1rem;" />
    </div>
    <h4 style="color: #485163; margin-bottom: 1.75rem">
      <strong style="color: #485163;">Memory Verses:</strong> <br /></h4>
    <div style="margin-left: 1rem; margin-top: -2.15rem; ">
      {#each readingPlanResult.memoryVerses as reference, index}
      <h4 style="font-family: monospace;">
        {#if prefersLight}
          <span class="text-slate-500">Reference {index + 1}:</span>
        {:else}
          <span class="text-slate-400">Reference {index + 1}:</span>
        {/if}
          {reference}
      </h4>
      {/each}
      <br style="margin-bottom: 1rem;" />
    </div>
    <ButtonLink
    size="large"
    target="_blank"
    href="https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&ved=2ahUKEwjQrsCR8vv4AhUMGFkFHfrJD1QQFnoECBAQAQ&url=https%3A%2F%2Freplicate.org%2Fwp-content%2Fuploads%2F2014%2F12%2FF260-Reading-Plan-2018.pdf&usg=AOvVaw2NJGxjsgRqKjhjmO8GLzhl"
  >
    <slot slot="icon-start">
      <svg
        class="fill-white dark:fill-dark h-6 w-6"
        xmlns="http://www.w3.org/2000/svg"
        viewBox="0 0 24 24"
        width="24"
        height="24"
        fill="none"
        stroke="#000000"
        stroke-width="2"
        stroke-linecap="round"
        stroke-linejoin="round"
        ><path d="M14 2H6a2 2 0 0 0-2 2v16c0 1.1.9 2 2 2h12a2 2 0 0 0 2-2V8l-6-6z" /><path
          d="M14 3v5h5M16 13H8M16 17H8M10 9H8"
        /></svg
      >
    </slot>
    View the F260 reading plan (PDF)
    <slot slot="icon-end" />
  </ButtonLink>
  </div>
  <br style="margin-bottom: 1rem;" />
  <!-- recent posts -->
  <h2 class="flex items-baseline gap-4 !mb-2">
    Recent Posts
    <ButtonLink href="/posts" size="small" raised={false} class="opacity-60">View All</ButtonLink>
  </h2>
  <div class="grid gap-4 grid-cols-1 sm:grid-cols-2">
    {#each recentPosts as post}
      <div class="flex p-4 border border-slate-300 dark:border-slate-700 rounded-lg">
        <PostPreview {post} small />
      </div>
    {/each}
  </div>
</div>
