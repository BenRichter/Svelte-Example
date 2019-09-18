<script>
	import Fetch from './module/Fetch.svelte'
	import Form from './module/Form.svelte'

	export let name
</script>

<h1>Hello {name}!</h1>

<Form />

<Fetch url="https://jsonplaceholder.typicode.com/todos" let:data>
	Template without links:
	<ul>
		{#each data as link}
			<li>{link.title}</li>
		{/each}
	</ul>
</Fetch>

<!--<Fetch />-->

<style>
	h1 {
		color: purple;
	}
</style>
