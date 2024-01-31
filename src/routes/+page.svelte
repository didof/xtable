<script lang="ts">
	import TableAnimated from '$lib/animated/TableAnimated.svelte';

	let template = {
		foo: true,
		bar: false,
		hello: 'world',
		object: {
			a: 1,
            b: 2,
            c: 3,
            nested: {
                deep: "a lot"
            }
		}
	};

	let input = JSON.stringify(template, null, 2);
	let data: string | null;
	$: {
		try {
			data = JSON.parse(input);
			localStorage.setItem('input', input);
		} catch (err) {
			data = null;
		}
	}
</script>

<div>
	<textarea bind:value={input} cols="50" rows="20"></textarea>

	<pre>{JSON.stringify(data, null, 2)}</pre>

	<span>
		<TableAnimated {data} />
	</span>
</div>

<style>
	div {
		width: 100vw;
		height: 100vh;
		display: flex;
		max-width: 1080px;
		margin-inline: auto;
		column-gap: 20px;
		align-items: center;
		justify-content: center;
	}
	span {
		width: 400px;
	}
</style>
