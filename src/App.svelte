<script>
  import Devs from "./lib/Devs.svelte";
  import { Router, Route, Link } from "svelte-navigator"
  import Home from "./lib/Home.svelte";


  let name = 'Trevor'
  let password = 123456

  let devs = false

  let user = {}

  const checkForm = () => {
    if(user.name == name && user.password == password) {
      document.getElementById('form').style.display="none"
      devs = true
    } else {
      alert("Wrong name or password" )
      return
    }
  }


</script>

<main>

  

  <Router>

    <nav>
      <Link class="links" to="/">Home</Link>
      {#if devs }
        <Link class="links" to="/devs">Developers</Link>
      {/if}
    </nav>

    <Route path="/devs"> <Devs/> </Route>
    <Route path="/"><Home /></Route>
  </Router>

  <div class="form" id="form">
    <form on:submit|preventDefault={checkForm}>
      <input type="text" placeholder="name" bind:value={user.name}>
      <input type="password" placeholder="password" bind:value={user.password}>
      <button>Enter System</button>
    </form>
  </div>
  
</main>

<style>
  nav {
    margin: 1rem auto;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .form {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: #fff;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  form {
    display: flex;
    flex-direction: column;
  }
  input {
    background: #e0e0e0;
    margin-bottom: 1rem;
    padding: 0.5rem 1rem;
    border-radius: 0.5rem;
    border: none;
    outline: none;
  }
  button {
    border: none;
    background-color: #000070;
    color: #fff;
    padding: 0.5rem 1rem;
    border-radius: 0.5rem;
    outline: none;
    cursor: pointer;
  }

</style>