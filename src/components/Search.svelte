<script>
  import axios from "axios";
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();
  export let movie;

  $: {
    if (movie) {
      axios
        .get(`http://www.omdbapi.com/?apikey=7d164321&t=${movie}`)
        .then(({ data }) => {
          if (data.Response == "True") dispatch("result", data);
          else dispatch("not_found", data.Error);
          console.log(data);
        })
        .catch((err) => dispatch("not_found", err));
    }
  }
</script>
