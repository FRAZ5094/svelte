<script lang="ts">
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();

  let reps;
  export let weight;
  export let max;
  let RPE=9;

  $: {
    dispatch("calculateweight",{reps,RPE});
  }

</script>

<div class="flex flex-col items-center">
  <h1 class="text-3xl py-4"> Find weight for set </h1>
    <div class="flex flex-row py-2 w-3/4 justify-center">
      <h1 class="w-1/2 text-2xl text-left">Enter Reps:</h1>
      <input class="text-center text-2xl w-1/4 rounded-xl" type="number" bind:value={reps}/>
    </div>
    <div class="flex flex-row py-2 w-3/4 justify-center">
      <h1 class="w-1/2 text-2xl text-left">Select RPE:</h1>
      <select class="text-center text-xl w-1/4 rounded-xl text-sky-500" bind:value={RPE}>
          <option value=8>6</option>
          <option value=7>6.5</option>
          <option value=6>7</option>
          <option value=5>7.5</option>
          <option value=4>8</option>
          <option value=3>8.5</option>
          <option value=2>9</option>
          <option value=1>9.5</option>
          <option value=0>10</option>
      </select>
    </div>
    <h1 class="text-3xl bg-sky-700 rounded-xl p-6 my-8">
      {#if max==undefined}
        Find predicted max first
      {:else if weight==undefined}
        Enter values for set
      {:else}
        {weight} kg
      {/if}
    </h1>
</div>
<style>
  input { @apply text-sky-500 }
</style>
