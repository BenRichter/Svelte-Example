<script>
  import { onMount } from "svelte";

  // export - Property with default
  export let url = "https://academy.valentinog.com/api/link/";
  export let searchTerm = undefined;

  // state
  let jsonResponse = [];

  // $: - labeled statement = computed
  $: regex = new RegExp(searchTerm, "gi");
  $: data = searchTerm
          ? jsonResponse.filter(element => element.title.match(regex))
          : jsonResponse;

  // lifecycle async
  onMount(async function() {
    const response = await fetch(url);
    jsonResponse = await response.json();
  });
</script>

<!-- render default template or "scoped" slot -->
<slot {data}>
  <ul>
      {#each data as link}
        <li>
          <a href={link.url}>{link.title}</a>
        </li>
      {/each}
  </ul>
</slot>

