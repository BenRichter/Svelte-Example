<script>
  // handleSubmit as prop with default function
  export let handleSubmit = function(event) {
    // default prop
  };
</script>

<form on:submit|preventDefault={handleSubmit}>
  <label for="search">Search:</label>
  <input type="search" id="search" required />
  <button type="submit">Search</button>
</form>

