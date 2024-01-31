<script lang="ts">
	import { slide } from 'svelte/transition';
	import TableAnimated from './TableAnimated.svelte';

	export let data: Record<string, any>;
</script>

<ul>
	{#each Object.entries(data) as [key, value]}
		<li transition:slide|global>
			<strong>{key}</strong>
			<span><TableAnimated data={value} /></span>
		</li>
	{/each}
</ul>

<style>
	ul {
		list-style: none;
		padding-left: 0;
		margin-top: 0;
		margin-bottom: 0;
        display: flex;
        flex-direction: column;
	}

    li {
        display: flex;
        justify-content: space-between;
        align-items: center;
        row-gap: 4px;
        column-gap: 4px;
        padding: 4px;
        border: 1px solid white;
    }
</style>
