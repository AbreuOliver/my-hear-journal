<script>
	import Gradient from './Gradient.svelte';
    export let passageContext = '';
    export let mySummary = '';
</script>

<div>
    <h2>Explanation</h2>
        <h3>Context of Passage</h3>
            <blockquote style="font-weight: bold !important">
                <p>{passageContext}</p>
            </blockquote>
        <h3>Key Word(s) of Passage<h3>
            <p><slot></slot></p>
        <h3>My Summary of Highlight<h3>
            <p>{mySummary}</p>
</div>