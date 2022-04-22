<script>
  import { onMount, onDestroy, beforeUpdate, afterUpdate } from "svelte";

  let description = "";
  $: characters = description.length;
  $: words = description.split(" ").length;

  $: if (description.length >= 10) {
    console.log(`----------`);
    console.log(`Description adalah: ${description}`);
  }

  // function handleSubmit(e) {
  //   e.preventDefault();
  //   console.log(`Thanks, ini tersubmit`);
  //   description = "";
  // }

  /*
     preventDefault berguna untuk supaya menghandle untuk browser tidak direload
  */

  const handleSubmit = () => {
    console.log(`Thanks, ini tersubmit`);
    description = "";
  };

  onMount(() => {
    console.log(`OnMount`);
  });
  onDestroy(() => {
    console.log(`OnDestroy`);
  });
  beforeUpdate(() => {
    console.log(`beforeUpdate`);
  });
  afterUpdate(() => {
    console.log(`afterUpdate`);
  });
</script>

<div class="form-group">
  <p>{description}</p>
  <form on:submit|preventDefault={handleSubmit}>
    <textarea bind:value={description} rows="7" />
    <button type="submit" class="btn btn-primary">Save</button>
  </form>

  <p>Character count: {characters}</p>
  <p>Word count: {words}</p>
</div>

<style>
  div {
    margin-top: 1em;
    margin-bottom: 1em;
  }
</style>
