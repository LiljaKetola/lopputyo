<script>
  function changevalue(e) {
    value = e.target.value;
  }

  export let id;
  export let value;
  export let cols = 30;
  export let rows = 5;

  export let valid = true;
  export let virheViesti = 'Tekstikenttä ei voi olla tyhjä!';

  //**Tämä komponentti on tekstialuetta varten.*/
</script>

<section>
  <textarea
    {id}
    {rows}
    {cols}
    on:input={changevalue}
    placeholder="Jätä kommentti! Voit esimerkiksi jättää kirjaehdotuksen!"
    >{value}</textarea
  >

  {#if !valid}
    <div class="virhe">{virheViesti}</div>
  {/if}
</section>

<style>
  .virhe {
    color: rgb(225, 94, 94);
  }
</style>
