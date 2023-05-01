<script>
  import Kirja from './Kirja.svelte';
  export let reseptikirjat = [];

  //**Täällä käydään reseptikirjat taulukko läpi*/
</script>

<section>
  {#each reseptikirjat as reseptikirja}
    <Kirja
      nimi={reseptikirja.nimi}
      aihe={reseptikirja.aihe}
      julkaisuvuosi={reseptikirja.julkaisuvuosi}
      on:omat
    />
  {/each}
</section>
