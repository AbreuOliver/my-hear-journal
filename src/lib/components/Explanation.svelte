<script>
	import Gradient from './Gradient.svelte';
    export let passageContext = '';
    export let mySummary = '';
</script>

<div>
    <h2>Explanation</h2>
        <h3>Passage Context</h3>
            <!-- <blockquote style="font-weight: bold !important"> -->
                <p style="font-weight: bold !important">{passageContext}</p>
            <!-- </blockquote> -->
        <h3>Passage Key Terms</h3>
            <p><slot></slot></p>
        <h3>My Summary of Highlight<h3>
            <p style="font-weight: bold !important">{mySummary}</p>
</div>