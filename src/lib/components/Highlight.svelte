<script>
	import Gradient from './Gradient.svelte';
    export let passage = '';
    export let reference = '';
</script>

<div>
    <h2>Highlight</h2>

    <blockquote style="font-weight: bold !important"> 
    <Gradient>"{passage}"</Gradient>
    </blockquote> - {reference}
</div>