<script lang="ts">
  import { Router, Link, Route } from "svelte-routing";
  import Home from './pages/Home.svelte';
  import Test from './pages/Test.svelte';

  export let url = '';
</script>

<Router url="{url}">
  <div class="logo">
    <img src="./images/dog-treat.svg" alt="dog treat" />
    <p>Bones</p>
  </div>
  <div>
    <Route path='/'><Home /></Route>
    <Route path='/test'><Test /></Route>
  </div>
</Router>

<style lang="scss">
  main {
    padding: 1em;
    text-align: center;
  }

  div.logo {
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 2em 0 0 0;
    img {
      max-width: 8rem;
      margin: -2em;
      transform: rotate(45deg);
    }
    p {
      margin: -1rem 0;
      font-size: 4em;
      font-family: "Baloo 2", cursive;
      font-weight: bolder;
    }
  }

  svg {
    display: inline-block;
    width: 1050px;
    height: 500px;
    margin: auto;
    pointer-events: none;
  }
  path:hover {
    transform: translateY(-5px);
  }
  path {
    pointer-events: auto;
  }
</style>
