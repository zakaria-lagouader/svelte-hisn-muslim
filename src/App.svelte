<script>  
import { Router, Link, Route } from "svelte-navigator";
import Home from "./pages/Home.svelte";
import Single from "./pages/Single.svelte";
  
</script>


<Router>
    <nav class="navbar navbar-light bg-light">
      <div class="container">
        <Link to="/" class="navbar-brand">Home</Link>
      </div>
    </nav>
    <div class="my-5">
    <Route path="/"  component={Home} />
    <Route path="/hadith/:id"  component={Single} />
    </div>
  </Router>
