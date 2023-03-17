<script>
  import google from "googlethis";

  const defaultOptions = {
    page: 0,
    safe: false, // Safe Search
    parse_ads: false, // If set to true sponsored results will be parsed
  };
  let settings = {
    additional_params: {
      hl: "en",
    },
  };

  let input = "";
  let sent = "";

  let keyDownEnter = (e) => {
    if (!e) e = window.event;
    var keyCode = e.code || e.key;
    if (keyCode == "Enter") {
      search();
    }
  };

  let search = () => {
    sent = input;
    google
      .search(sent, {...defaultOptions, ...settings})
      .then((results) => {
        console.log(results);
      })
      .catch((err) => {
        console.log(err);
      });
  };
</script>

<main>
  <h1>My app</h1>
  <p>My app is working : {sent}</p>
  <input type="text" bind:value={input} on:keypress={keyDownEnter} />
  <button on:click={search}>Search</button>
</main>

<style>
</style>
