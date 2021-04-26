<script>
  import { useTracker } from "meteor/rdb:svelte-meteor-data";
  import { Resolutions } from "../api/resolutions";
  import Resolution from "./resolutions/Resolutions.svelte";
  let newRes = "";

  //^ Reactive Variable

  $: resolutions = useTracker(() => Resolutions.find({}).fetch());

  function handleSubmit() {
    console.log(newRes);
    Resolutions.insert({
      title: newRes,
    });
    newRes = "";
  }
</script>

<header>
  <h1>Yooo!!</h1>

  <form action="" on:submit|preventDefault={handleSubmit}>
    <input type="text" placeholder="Add Your Resolution" bind:value={newRes} />
    <button type="submit">Submit</button>
  </form>

  {#each $resolutions as resolution}
    <Resolution {resolution} />
  {/each}
</header>
