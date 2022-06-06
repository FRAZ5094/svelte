<script lang="ts">
  let weight;
  let reps;
  let RPE=0;
  let max=0;

  let RPE_grid=[
    [100.,95.5,92.2,89.2,86.3,83.7,81.1,78.6,76.2,73.9,70.7,68.0],
    [97.8,93.9,90.7,87.8,85.0,82.4,79.9,77.4,75.1,72.3,69.4,66.7],
    [95.5,92.2,89.2,86.3,83.7,81.1,78.6,76.2,73.9,70.7,68.0,65.3],
    [93.9,90.7,87.8,85.0,82.4,79.9,77.4,75.1,72.3,69.4,66.7,64.0],
    [92.2,89.2,86.3,83.7,81.1,78.6,76.2,73.9,70.7,68.0,65.3,62.6],
    [90.7,87.8,85.0,82.4,79.9,77.4,75.1,72.3,69.4,66.7,64.0,61.3],
    [89.2,86.3,83.7,81.1,78.6,76.2,73.9,70.7,68.0,65.3,62.6,59.9],
    [87.8,85.0,82.4,79.9,77.4,75.1,72.3,69.4,66.7,64.0,61.3,58.8],
    [86.3,83.7,81.1,78.6,76.2,73.9,70.7,68.0,65.3,62.6,59.6,57.2]
  ]

  $:{
    max=(weight)/(RPE_grid[RPE][reps-1]/100);
    max=max.toFixed(1);
  };

</script>


<div class="flex flex-col justify-center items-center">
  <div class="flex flex-row w-3/4 justify-center">
    <div class="flex flex-col w-1/3">
      <h1>Enter weight:</h1>
      <input class="border-2" type="number" bind:value={weight}/>
    </div>
    <div class="flex flex-col w-1/3">
      <h1>Enter reps:</h1>
    <input class="border-2" type="number" bind:value={reps}/>
    </div>
    <select class="w-1/3" bind:value={RPE}>
        <option value=0>Choose RPE</option>
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
  <h1> Predicted Max:</h1>
  <p> {max} kg</p>
</div>
