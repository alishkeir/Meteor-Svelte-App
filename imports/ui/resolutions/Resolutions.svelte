<script>
  export let resolution;
  import { Resolutions } from "../../api/resolutions";

  let updateRes = "";

  function handleDelete() {
    Resolutions.remove(resolution._id);
  }

  function handleSubmit() {
    Resolutions.update(
      {
        _id: resolution._id,
      },
      {
        title: updateRes,
      }
    );
    updateRes = "";
  }
</script>

<br />
<li>
  {resolution.title}
  
  <form action="" on:submit|preventDefault={handleSubmit}>
    <input type="text" bind:value={updateRes} />
  </form>

  <button on:click={handleDelete}>Delete</button>
</li>
