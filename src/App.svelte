<script>
  import header from "./lib/components/header.svelte";
  import hero from "./lib/components/hero.svelte";
  import about from "./lib/components/about.svelte";
  import portfolio from "./lib/components/portfolio.svelte";
  import contact from "./lib/components/contact.svelte";
</script>

<main>
  <Header />
  <Hero />
  <About />
  <Portfolio />
  <Contact />
</main>

<style>
  :global(body) {
    margin: 0;
    padding: 0;
    background: #0a0e27;
    color: white;
    font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
    overflow-x: hidden;
  }
  :global(*) {
    box-sizing: border-box;
  }

  main {
    min-height: 100vh;
    width: 100%;
  }
</style>
