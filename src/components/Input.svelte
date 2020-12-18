<script>
  import { createEventDispatcher } from "svelte";
  let disptach = createEventDispatcher();
  let movie_name;
</script>

<style>
  :global(body) input {
    border: none;
    border-bottom: 1px solid #ececec;
  }
  :global(body.dark-mode) input {
    border: none;
    border-bottom: 1px solid #ececec;
    background-color: #000;
    color: #fff;
  }
</style>

<form on:submit|preventDefault={disptach('MOVIE_NAME', movie_name)}>
  <input type="text" bind:value={movie_name} placeholder="Movie Name" />
</form>
