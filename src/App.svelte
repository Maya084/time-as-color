<script lang="ts">
  import { onMount } from "svelte";

  $: str = "#123456";

  function convertNum(time: number): string {
    return ("0" + time).slice(-2);
  }

  function doDate() {
    let time = new Date();
    const helper =
      "#" +
      convertNum(time.getHours()) + 
      convertNum(time.getMinutes()) + 
      convertNum(time.getSeconds());

    str = helper;
    document.documentElement.style.setProperty("--background-color", str);
  }
  onMount(() => {
    setInterval(doDate, 1000);
  });
</script>

<main class="main-content">
  <div class="time-value">{str}</div>
</main>

<style>

  .time-value {
    font-family: "Roboto Mono";
    color: #e3ede5;
    font-size: 13vw;
    font-weight: 700;
  }
</style>
