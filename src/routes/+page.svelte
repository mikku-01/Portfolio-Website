<script>
  import Header from "$lib/components/Header.svelte";
  import Hero from "$lib/components/Hero.svelte";
  import About from "$lib/components/About.svelte";
  import Portfolio from "$lib/components/Portfolio.svelte";
  import Contact from "$lib/components/Contact.svelte";
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
