<script>
  //**Tämä on komponentti pienemmälle nappulalle.*/
</script>

<section>
  <button on:click><slot /></button>
</section>

<style>
  button {
    background-color: rgb(200, 237, 237);

    border-radius: 1.5em;
    padding-left: 15px;
    padding-right: 15px;
  }
</style>
