<script>
  import { Link } from "svelte-navigator";
    import { onMount } from "svelte";
    let data;
    const audioPlayer = new Audio();

    onMount(() => {
        fetch("/husn_en.json").then(res => res.json()).then(({English}) => data = English)
    })

    const playAudio = (audioURL) => {
        audioPlayer.pause();
        audioPlayer.src = audioURL;
        audioPlayer.play();
    }
</script>

{#if data}
<div class="container">
  <h1 class="display-4 text-center my-5">Hisn Muslim</h1>
  <table class="table table-bordered table-striped">
    <thead>
      <tr>
        <th scope="col">Title</th>
        <th scope="col">Audio</th>
      </tr>
    </thead>
    <tbody>
      {#each data as hadith}
        <tr>
          <th>
            <Link to={`hadith/${hadith.ID}`}>{hadith.TITLE}</Link>
          </th>
          <td>
            <button 
            on:click={() => playAudio(hadith.AUDIO_URL)}
            class="btn btn-sm btn-primary"
            >audio</button>
          </td>
        </tr>
      {/each}
    </tbody>
  </table>
</div>
{:else}
<h1 class="text-center">Loading</h1>
{/if}