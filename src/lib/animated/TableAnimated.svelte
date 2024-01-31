<script lang="ts">
	import Object from './Object.svelte';
	import Primitive from './Primitive.svelte';

	export let data: any;

	let component: any = null;
	$: {
		switch (typeof data) {
			case 'boolean':
			case 'number':
			case 'string':
			case 'undefined':
				component = Primitive;
				break;
			case 'object':
				if (data === null) {
					component = Primitive;
					break;
				}
				component = Object;
				break;
		}
	}
</script>

{#if data != null}
	<svelte:component this={component} {data} />
{/if}
