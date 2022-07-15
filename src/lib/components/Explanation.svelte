<script>
	import Gradient from './Gradient.svelte';
    export let passageContext = '';
    export let mySummary = '';
</script>

<div>
    <h2>Explanation</h2>
        <h3>Context of Passage</h3>
            <blockquote>{passageContext}</blockquote>
        <h3>Key Word(s) of Passage<h3>
            <slot></slot>
        <h3>My Summary of Highlight<h3>
            <p>{mySummary}</p>
</div>