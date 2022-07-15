<script>
	import Gradient from './Gradient.svelte';
    export let passageContext = '';
    export let mySummary = '';
</script>

<div>
    <h2>Explanation</h2>
          <strong 
        style="font-weight: 800; font-size: clamp(1.42em, 1.5em, 1.67em); line-height: 1.3333333"
    >Context of Passage</strong>
    <br/>
    <br/>
            <blockquote style="font-weight: bold 
            !important">
                <p>{passageContext}</p>
            </blockquote>
          <strong 
        style="font-weight: 800; font-size: clamp(1.42em, 1.5em, 1.67em); line-height: 1.3333333"
    >Key Word(s) of Passage</strong>
            <p><slot></slot></p>
        <h3>My Summary of Highlight<h3>
            <p>{mySummary}</p>
</div>