<script lang="ts">
  import PredictedMax from "./PredictedMax.svelte";
  import Tailwindcss from "./Tailwindcss.svelte";
  import Header from "./Header.svelte";
  import FindWeight from "./FindWeight.svelte";
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

  let max;
  const calculateMax = (values) => {
    let { weight, reps, RPE } = values.detail;
    max=(weight)/(RPE_grid[RPE][reps-1]/100);
    max=max.toFixed(1);
  }
  let weight;
  const calculateWeight = (values) => {
      let { reps, RPE } = values.detail;
      weight=max*(RPE_grid[RPE][reps-1]/100);
      weight=weight.toFixed(1);
    }
  
</script>
<Tailwindcss />
<body class="bg-sky-500 h-screen text-white">
  <Header />
  <PredictedMax on:calculateweight={calculateWeight} on:calculatemax={calculateMax} max={max} />
  <FindWeight on:calculateweight={calculateWeight} weight={weight} max={max} />
</body>
