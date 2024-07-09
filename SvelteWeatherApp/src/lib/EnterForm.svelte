<script>
  export let handleSearchCity;
  let enterCity = "";

  const search = () => {
    handleSearchCity(enterCity);
  };
</script>

<form on:submit|preventDefault={search}>
  <input type="text" placeholder="Enter a location!" bind:value={enterCity} />
  <button type="submit">Search</button>
</form>
