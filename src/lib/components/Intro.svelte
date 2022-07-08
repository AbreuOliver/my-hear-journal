<script>
	import Gradient from './Gradient.svelte';
</script>

<div>
    <strong 
        style="font-weight: 800; font-size: clamp(1.42em, 1.5em, 1.67em); line-height: 1.3333333"
    >
        Today's Scripture Reading
    </strong>
    <br/>
    <br/>
    <strong 
        style="font-weight: 700; color: inherit; font-size: clamp(1.42em, 1.5em, 1.67em); line-height: 1.5"
    >
        <Gradient>
            <slot></slot>
        </Gradient>
    </strong>
</div>