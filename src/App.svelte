<script>
  export let name;

  import Button from './Button.svelte';
  import Elamakerrat from './Elamakerrat.svelte';
  import Tieto from './Tieto.svelte';
  import Kentta from './Kentta.svelte';
  import ReseptiKirjat from './ReseptiKirjat.svelte';
  /**
   * Tässä tuodaan muut komponentit App.Svelte tiedostoon.
   */

  $: kommentti = '';

  let elamanKerrat = [
    {
      id: 1,
      nimi: 'Wiwi Lönn',
      aihe: 'Arkkitehti Wivi Lönniä käsittelevä teos pohjautuu vanhoihin valokuviin ja rakennuspiirustuksiin',
      julkaisuvuosi: 2021,
    },
  ];
  let reseptikirjat = [
    {
      id: 2,
      nimi: 'Kotiruokaa',
      aihe: 'Keittokirjojen klassikko',
      julkaisuvuosi: 2018,
    },
    {
      id: 3,
      nimi: 'Makeeta',
      aihe: 'Makeeta on huippukondiittori Markus Hurskaisen uusi kirja, joka vie lukijat makeiden leivonnaisten maailmaan.',
      julkaisuvuosi: 2020,
    },
  ];
  let tietokirjat = [
    {
      id: 4,
      nimi: 'Lahden kartano',
      aihe: 'Härkätien varrella Someron Lahden kylässä on kohonnut komea empiretyylinen kartanon päärakennus jo toistasataa vuotta.',
      julkaisuvuosi: 2023,
    },
  ];

  /**
   * Ylempää löytyy taulukot kategorioittain. Yksittäiset kirjat ovat objekteja.
   */

  $: omatKommentit = [];
  let omatSuosikit = [];
  let naytaElamakerrat = false;
  let naytaReseptikirjat = false;
  let naytaTietokirjat = false;

  function avaaElamanKerrat() {
    naytaElamakerrat = !naytaElamakerrat;
  }

  function avaaReseptiKirjat() {
    naytaReseptikirjat = !naytaReseptikirjat;
  }

  function avaaTietokirjat() {
    naytaTietokirjat = !naytaTietokirjat;
  }

  function lisaa() {
    omatKommentit.push(kommentti);
    omatKommentit = omatKommentit;
    kommentti = '';
  }

  //**Tässä lisätään syöte taulukkoon. */

  function omat(ce) {
    omatSuosikit.push(ce.detail);
    omatSuosikit = omatSuosikit;
  }

  /** */

  $: validiSyote = kommentti.trim().length > 1;
</script>

<main>
  <h1>{name}!</h1>
  <p>Täältä löytyy kirja ehdotuksia kategorioittain!</p>

  <div class="asettelu">
    <Button on:click={avaaElamanKerrat}>Elämäkerrat</Button>
    {#if naytaElamakerrat}
      <div id="kokeilu"><Elamakerrat {elamanKerrat} on:omat={omat} /></div>
    {/if}
    <Button on:click={avaaReseptiKirjat}>Reseptikirjat</Button>

    {#if naytaReseptikirjat}
      <ReseptiKirjat {reseptikirjat} on:omat={omat} />
    {/if}
    <Button on:click={avaaTietokirjat}>TietoKirjat</Button>
    {#if naytaTietokirjat}
      <Tieto {tietokirjat} on:omat={omat} />
    {/if}
  </div>
  <div class="laatikko">
    <p id="suosikit">Omat suosikit:</p>
    <p id="suosikkiTeksti">{omatSuosikit}</p>
  </div>

  <Kentta
    id="kommentti"
    valid={validiSyote}
    bind:value={kommentti}
    placeholder="Jätä kommentti"
  />

  <button id="lisaa" on:click={lisaa} disabled={!validiSyote}>Lisää</button>
  <br />

  <div id="kommentteja">
    <p id="kommenttiTeksti">Kommentit:</p>
    <p id="kommentti-teksti">{omatKommentit}</p>
  </div>
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
    background-color: beige;
  }

  h1 {
    color: #9ad7e8;
    font-size: 4em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }

  .asettelu {
    display: flex;
    justify-content: center;
    margin-right: 10px;
  }

  #kokeilu {
    margin-right: 20px;
  }

  #suosikkiTeksti {
    font-size: larger;
    color: rgb(88, 88, 208);
  }

  .laatikko {
    background-color: white;
    margin-left: 250px;
    margin-right: 250px;
    border: solid rgb(200, 237, 237);

    margin-bottom: 30px;
    margin-top: 25px;
  }

  #lisaa {
    background-color: rgb(200, 237, 237);
    border-radius: 2em;
    font-size: 20px;
    padding-left: 15px;
    padding-right: 15px;
    padding-top: 15px;
    padding-bottom: 15px;
  }

  #kommentteja {
    background-color: #ffffff;
    margin-left: 250px;
    margin-right: 250px;
    border: solid rgb(200, 237, 237);
  }

  #kommentti-teksti {
    color: black;
    font-size: 15px;
    font-weight: bold;
    font-style: oblique;
  }

  #suosikit {
    font-size: 15px;
    font-weight: bold;
  }

  #kommenttiTeksti {
    font-size: 15px;
    font-weight: bold;
  }
</style>
