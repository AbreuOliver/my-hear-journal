<script>
  import { format, parseISO } from 'date-fns'
  import ButtonLink from './ButtonLink.svelte'

  export let post
  export let small = false
</script>

<div class="flex flex-col preview">
  <div>
    {#if !small}
      <h1 class="!mt-0 !mb-2">
        <a style="font-weight: 800" class="!text-transparent bg-clip-text bg-gradient-to-r from-blue-500 to-teal-500 dark:from-violet-500 dark:to-pink-500" href={`/posts/${post.slug}`}>{post.title}</a>
      </h1>
    {:else}
      <h3 class="!mt-0 !mb-2">
        <a style="font-weight:700 !important" href={`/posts/${post.slug}`}>{post.title}</a>
      </h3>
    {/if}
    <div class="opacity-70">
      <time>{format(new Date(parseISO(post.date)), 'MMMM d, yyyy')}</time>
      •
      <span>{post.readingTime}</span>
    </div>
  </div>
  <div class="flex-1">{@html post.preview.html}</div>
  <slot name="actions">
    <div class="flex justify-end w-full">
      <ButtonLink href={`/posts/${post.slug}`}>Read More</ButtonLink>
    </div>
  </slot>
</div>
