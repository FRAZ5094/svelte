<script lang="ts">
  import { createEventDispatcher } from 'svelte';

  const dispatch = createEventDispatcher();

  let name=""; 

  const onSubmit = (e) => {
    e.preventDefault();
    dispatch("removeplayer", name);
  };

</script>


<form on:submit={onSubmit} class="grid-3">
  <input type="text" placeholder="Player Name" bind:value={name}/>
  <input type="submit" class="btn btn-primary" value="Remove player"/>
</form>
