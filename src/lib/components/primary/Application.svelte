<script>
	import Gradient from './Gradient.svelte';
    export let historicalApplication = '';
    export let contemporaryApplication = '';
</script>

<div>
    <h2 id="application">
        <a href="#application">
            <strong>Application</strong>
        </a>
    </h2>
    <h3 id="historicalApplication">
        <a href="#historicalApplication">
            <strong>Historical Application</strong>
        </a>
    </h3>
        <p>{historicalApplication}</p>
    <h3 id="contemporaryApplication">
        <a href="#contemporaryApplication">
            <strong>Contemporary Application</strong>
        </a>
    </h3>
    <p>{contemporaryApplication}</p>
</div>