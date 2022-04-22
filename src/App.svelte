<script>
  import EmojiDisplay from "./EmojiDisplay.svelte";
  import EmojiDescription from "./EmojiDescription.svelte";
  import Button from "./Button.svelte";
  import { fly, fade } from "svelte/transition";

  let isLoaded = false;
  let currentEmoji = "🤖";
  const emojis = ["😁", "😚", "🚀", "🥌", "🧑‍🚀"];

  let m = {
    x: 0,
    y: 0,
  };

  const randomizeEmoji = () => {
    return emojis[Math.floor(Math.random() * emojis.length)];
  };

  const handleRandomButton = () => {
    currentEmoji = randomizeEmoji();
  };

  setTimeout(() => {
    isLoaded = true;
  }, 2500);

  const handleMosemove = () => {
    m.x = event.clientX;
    m.y = event.clientY;
  };
</script>

<svelte:head>
  <link rel="stylesheet" href="style.css" />
</svelte:head>

<div class="container" on:mousemove={handleMosemove}>
  <p>The mouse position: {m.x} x {m.y}</p>
  <h1>Randomize Emoji</h1>
  <ul>
    {#each emojis as emoji}
      <li>{emoji}</li>
    {/each}
  </ul>

  {#if isLoaded === true}
    <div in:fly={{y:200, duration:2000 }} out:fade>
      <EmojiDisplay {currentEmoji} />
      <EmojiDescription />
      <Button
        class="btn btn-primary"
        on:click={handleRandomButton}
        title={"🔃Randomize"}
      />
    </div>
  {:else}
    <h2>Loading ...</h2>
  {/if}

  <Button title={"Toggle"} on:click={() => (isLoaded = !isLoaded)} />
</div>

<style>
  div {
    margin: 2em;
  }
  .container {
    padding-bottom: 10em;
  }
</style>
