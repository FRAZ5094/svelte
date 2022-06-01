<script lang="ts">
  import Navbar from "./Navbar.svelte";
  import Player from "./Player.svelte";
  import AddPlayer from "./AddPlayer.svelte";
  import RemovePlayer from "./RemovePlayer.svelte";

  let players = [ 
    {
      name: "Fraser",
      points: 53
    },
    {
      name: "Scott",
      points: 24 
    },
    {
      name: "Eerik",
      points: 2
    },
  ]

  const addPlayer = (e) => {
    const newPlayer = e.detail;

    players = [...players, newPlayer];
  }

  const removePlayer = (e) => {
    players= players.filter(player => player.name !== e.detail);
  }


</script>
<style>

</style>

<Navbar />
<div class="container">
  <AddPlayer on:addplayer={addPlayer} />
  {#if players.length ===0}
    <p>No Players</p>
  {:else}
    {#each players as player} 
      <Player name={player.name} points={player.points} on:removeplayer={removePlayer} />
    {/each}
    <RemovePlayer on:removeplayer={removePlayer}/>
  {/if}
</div>
