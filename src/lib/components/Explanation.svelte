<script>
	import Gradient from './Gradient.svelte';
    export let passageContext = '';
    export let mySummary = '';
    export let citation = '';
    export let citationURL = '';
</script>

<div>
    <h2 id="explanation">
        <a href="#explanation">
            <strong>Explanation</strong>
        </a>
    </h2>
    <h3 id="passageContext">
        <a href="#passageContext">
            <strong>Passage Context</strong>
        </a>
    </h3>
        <blockquote>
            <p>{passageContext}</p>
            {#if citationURL}
            <a href="{citationURL}">{citation}</a>
            {/if}
        </blockquote>
    <h3 id="passageKeyTerms">
        <a href="#passageKeyTerms">
            <strong>Passage Key Terms</strong>
        </a>
    </h3>
        <p><slot></slot></p>
    <h3 id="mySummary">
        <a href="#mySummary">
            <strong>My Summary</strong>
        </a>
    </h3>
    <p>{mySummary}</p>
</div>