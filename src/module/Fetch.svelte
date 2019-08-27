<script>
  import { onMount } from "svelte";

  // Accessible Property with default
  export let url = "https://academy.valentinog.com/api/link/";

  let data = [];

  // lifecycle async
  onMount(async function() {
    const response = await fetch(url)
    const json = await response.json();
    data = json;
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

