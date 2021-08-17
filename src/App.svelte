<script>
  import Block from "./Block.svelte"
  import Moment from "moment";

  let startDate = "2015-07-17";
  let day = Moment(startDate).format("dddd, MMMM Do YYYY");
  
</script>

<main>
  <header>
    <h1>Ditte & Donald</h1>
    <p class="subtitle">Together since {day}.</p>
  </header>

  <Block title="Married for.." startDate="2020-07-04" />
  <Block title="A couple for.." startDate={startDate} />
</main>

<style>
  @import url("https://fonts.googleapis.com/css?family=Lato:300,400,700&display=swap");

  :global(body) {
    background-color: #f1f2f6;
  }

  main {
    text-align: center;
    font-family: "Lato", sans-serif;
  }

  header {
    margin-top: 1em;
  }

  h1 {
    margin: 0;
    font-weight: 300;
  }

  .subtitle {
    margin: 4px 0;
    color: rgb(150, 150, 150);
    font-size: 12px;
  }
</style>