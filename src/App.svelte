<script>
  import RhymeList from "./lib/RhymeList.svelte";

  let inputValue;
  let rhymeData = [];

  function unpackBody(response) {
      return response.json();
  }

  function populateList(data) {
    console.log(data);
    rhymeData = data;
  }

  function handleInput() {
    console.log("input changed", inputValue);

    if (inputValue.length < 3) {
      rhymeData = [];
      return;
    }
    
    fetch("https://rhymebrain.com/talk?function=getRhymes&word=" + inputValue)
      .then(unpackBody)
      .then(populateList);
  }
</script>

<main>
  <input bind:value={inputValue} on:input={handleInput} id="word-box" type="text">
  
  <RhymeList rhymeData={rhymeData}/>
</main>

<style>
  
</style>
