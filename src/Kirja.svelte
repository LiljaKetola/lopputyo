<script>
  export let nimi;

  export let aihe;
  export let julkaisuvuosi;
  import { createEventDispatcher } from 'svelte';
  const dispatch = createEventDispatcher();

  import Painike from './Painike.svelte';
</script>

<section>
  <div class="kirja">
    <p class="nimi">{nimi}</p>
    <p class="aihe">Aihe: {aihe}</p>
    <p class="teksti">Julkaisuvuosi: {julkaisuvuosi}</p>
    <Painike on:click={() => dispatch('omat', nimi)}>Lisää</Painike>
  </div>
</section>

<style>
  .kirja {
    background-color: rgb(221, 245, 245);
    border: 5px dotted rgb(200, 237, 237);
    border-radius: 15%;
    margin: 5px;
    padding-left: 5px;
    padding-right: 5px;
    max-width: 200px;
    margin-top: 10px;
  }

  .teksti {
    font-size: 12px;
  }

  .aihe {
    font-size: 12px;
    display: block;
  }

  .nimi {
    font-size: 15px;
  }
</style>
