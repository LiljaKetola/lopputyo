<script>
  //** Tässä on komponentti isompaa painiketta varten. */
</script>

<section>
  <button on:click><slot /></button>
</section>

<style>
  button {
    background-color: rgb(200, 237, 237);
    border-radius: 2em;
    font-size: 20px;
    padding-left: 15px;
    padding-right: 15px;
    padding-top: 15px;
    padding-bottom: 15px;
  }
</style>
