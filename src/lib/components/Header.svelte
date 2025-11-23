<script>
  function scrollToSection(id) {
    const element = document.getElementById(id);
    if (element) {
      element.scrollIntoView({ behavior: "smooth" });
    }
  }
</script>

<header class="header">
  <div class="container">
    <div class="logo">Portfolio</div>

    <nav class="nav">
      <button on:click={() => scrollToSection("home")}>Home</button>
      <button on:click={() => scrollToSection("about")}>About</button>
      <button on:click={() => scrollToSection("portfolio")}>Portfolio</button>
      <button on:click={() => scrollToSection("contact")}>Contact</button>
    </nav>
  </div>
</header>

<style>
  .header {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    z-index: 1000;
    background: rgba(15, 7, 40, 0.8);
    backdrop-filter: blur(10px);
    border-bottom: 1px solid rgba(255, 255, 255, 0.1);
  }

  .container {
    max-width: 1400px;
    margin: 0 auto;
    padding: 1.25rem 2rem;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  .logo {
    font-size: 1.5rem;
    font-weight: 900;
    background: linear-gradient(90deg, #a855f7, #3b82f6);
    -webkit-background-clip: text;
    background-clip: text;
    -webkit-text-fill-color: transparent;
  }

  .nav {
    display: flex;
    gap: 2.5rem;
  }

  .nav button {
    background: none;
    border: none;
    font-size: 1rem;
    color: rgba(255, 255, 255, 0.8);
    cursor: pointer;
    transition: all 0.3s ease;
    padding: 0.5rem 0;
    position: relative;
    font-weight: 500;
  }

  .nav button::after {
    content: "";
    position: absolute;
    bottom: 0;
    left: 0;
    width: 0;
    height: 2px;
    background: linear-gradient(90deg, #a855f7, #3b82f6);
    transition: width 0.3s ease;
  }

  .nav button:hover {
    color: white;
  }

  .nav button:hover::after {
    width: 100%;
  }

  @media (max-width: 768px) {
    .nav {
      display: none;
    }
  }
</style>
