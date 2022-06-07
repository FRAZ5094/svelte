<script lang="ts">
  let max=210;
  let reps;
  let weight;
  let RPE=9;

  let RPE_grid=[
    [100.,95.5,92.2,89.2,86.3,83.7,81.1,78.6,76.2,73.9,70.7,68.0],
    [97.8,93.9,90.7,87.8,85.0,82.4,79.9,77.4,75.1,72.3,69.4,66.7],
    [95.5,92.2,89.2,86.3,83.7,81.1,78.6,76.2,73.9,70.7,68.0,65.3],
    [93.9,90.7,87.8,85.0,82.4,79.9,77.4,75.1,72.3,69.4,66.7,64.0],
    [92.2,89.2,86.3,83.7,81.1,78.6,76.2,73.9,70.7,68.0,65.3,62.6],
    [90.7,87.8,85.0,82.4,79.9,77.4,75.1,72.3,69.4,66.7,64.0,61.3],
    [89.2,86.3,83.7,81.1,78.6,76.2,73.9,70.7,68.0,65.3,62.6,59.9],
    [87.8,85.0,82.4,79.9,77.4,75.1,72.3,69.4,66.7,64.0,61.3,58.8],
    [86.3,83.7,81.1,78.6,76.2,73.9,70.7,68.0,65.3,62.6,59.6,57.2],
    [0,0,0,0,0,0,0,0,0,0,0,0]
  ]

  $: {
    weight=max*(RPE_grid[RPE][reps-1]/100);
    weight=weight.toFixed(1);
  }

</script>

<div class="flex flex-col my-8 items-center">
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
  <h1 class="text-3xl">Weight:</h1>
    <h1 class="text-2xl"> {weight} kg</h1>
  </div>

<style>
  input { @apply text-sky-500 }
</style>
