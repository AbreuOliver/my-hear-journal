<script>
	import Gradient from './Gradient.svelte';
    export let passageContext = '';
    export let mySummary = '';
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
            <p>{passageContext}</p>
        <h3 id="passageKeyTerms">
            <a href="#passageKeyTerms">
                <strong>Passage Key Terms</strong>
            </a>
        </h3>
            <p><slot></slot></p>
        <h3>My Summary of Highlight<h3>
        <p>{mySummary}</p>
</div>