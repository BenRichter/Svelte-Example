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
			{#if link.completed == true}
				<li class="completed">{link.title}</li>
			{:else}
				<li class="remaining">{link.title}</li>
			{/if}
		{/each}
	</ul>
</Fetch>

<!--<Fetch />-->

<style>
	h1 {
		color: purple;
	}
	.completed {
		background-color: rgb(132, 214, 132);
		padding: 5px;
		width: auto;
	}
	.remaining {
		background-color: rgb(92, 172, 218);
		padding: 5px;
		width: auto;
	}
	li {
		margin: 2px;
	}
</style>
