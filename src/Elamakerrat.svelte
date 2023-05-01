<script>
  import Kirja from './Kirja.svelte';
  export let elamanKerrat = [];

  //**Täällä käydään elamanKerrat taulukko läpi.*/
</script>

{#each elamanKerrat as elamankerta}
  <Kirja
    nimi={elamankerta.nimi}
    aihe={elamankerta.aihe}
    julkaisuvuosi={elamankerta.julkaisuvuosi}
    on:omat
  />
{/each}
