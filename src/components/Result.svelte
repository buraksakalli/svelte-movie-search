<script>
  export let data;
  /* 
	Released
	Writer
	Year
	Country
	Awards
	Genre (Drama, etc)
	Type (series, movie)
	Language
	*/
</script>

<style>
  ul {
    list-style-type: none;
    margin: 0;
    padding: 0;
    margin-bottom: 10px;
  }
  .imdb {
    width: 50px;
    height: auto;
    object-fit: contain;
  }
  .title {
    background-color: #ff3e00;
    width: 200px;
  }
  .poster {
    width: 200px;
    height: auto;
    object-fit: cover;
  }
  .result {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
  }
</style>

<div class="result">
  <h2 class="title">{data.Title}</h2>
  <img src={data.Poster} alt="movie_poster" class="poster"/>
  <p>{data.Runtime}</p>
  <p>{data.Plot}</p>
  <p>{data.Actors}</p>
  <ul>
    <p>Ratings</p>
    {#each data.Ratings as rate}
      <li>{rate.Source} | {rate.Value}</li>
    {/each}
  </ul>
  <a href={`https://www.imdb.com/title/${data.imdbID}`} target="_blank">
    <img src="1200px-IMDB_Logo_2016.svg.png" class="imdb" alt="imdb" />
  </a>
</div>
