<script>
  export let currentEmoji = emoji;
  let current = "";
</script>

<div>{currentEmoji}</div>

<button
  class="btn"
  class:btn-primary={current === "button1"}
  on:click={() => (current = "button1")}>Button 1</button
>
<button
  class="btn"
  class:btn-primary={current === "button2"}
  on:click={() => (current = "button2")}>Button 2</button
>
<button
  class="btn"
  class:btn-primary={current === "button3"}
  on:click={() => (current = "button3")}>Button 3</button
>

<style>
  div {
    font-size: 3em;
    margin-bottom: 0.5em;
  }
</style>
