<script>
	import Gradient from './Gradient.svelte';
    export let verseText = '';
    export let reference = '';
</script>

<div>
    <h2 id="highlight">
        <a href="#highlight">
            <strong>
                Highlight
            </strong>
        </a>
    </h2>

    <blockquote style="font-weight: bold !important"> 
    <Gradient>"{verseText}"</Gradient>
    <p style="font-weight: 600;"> - {reference}</p>
    </blockquote>
</div>