<script>
  import Kirja from './Kirja.svelte';

  export let tietokirjat = [];
</script>

{#each tietokirjat as tietokirja}
  <Kirja
    nimi={tietokirja.nimi}
    aihe={tietokirja.aihe}
    julkaisuvuosi={tietokirja.julkaisuvuosi}
    on:omat
  />
{/each}
