<script>
	import Fetch from './module/Fetch.svelte'
	import Form from './module/Form.svelte'

	export let name;

	let searchTerm;
	function handleSubmit() {
		const {value} = this.elements.search;
		searchTerm = value;
	}
</script>

<h1>Hello {name}!</h1>

<!-- prop handleSubmit={handleSubmit} -->
<Form {handleSubmit}/>

<Fetch url="https://jsonplaceholder.typicode.com/todos"
	   {searchTerm}
	   let:data
>
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
