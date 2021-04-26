<script>
  import { useTracker } from "meteor/rdb:svelte-meteor-data";
  import { Resolutions } from "../api/resolutions";

  let newRes = "";

  //^ Reactive Variable

  $: resolutions = useTracker(() => Resolutions.find({}).fetch());

  function handleSubmit(e) {
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
    <h2>{resolution.title}</h2>
  {/each}
</header>
