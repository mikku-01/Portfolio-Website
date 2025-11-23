<script>
  import { onMount } from "svelte";

  let showWelcome = true;
  let particles = [];

  onMount(() => {
    // Create particles
    for (let i = 0; i < 30; i++) {
      particles.push({
        x: Math.random() * 100,
        y: Math.random() * 100,
        size: Math.random() * 3 + 1,
        duration: Math.random() * 3 + 2,
      });
    }
    particles = particles;

    // Auto-transition after bounce animation completes (3.5 seconds)
    const timer = setTimeout(() => {
      showWelcome = false;
    }, 3500);

    return () => clearTimeout(timer);
  });
</script>

<section id="home" class="hero">
  <!-- Animated background -->
  <div class="gradient-bg"></div>

  <!-- Particles -->
  <div class="particles">
    {#each particles as particle}
      <div
        class="particle"
        style="
          left: {particle.x}%; 
          top: {particle.y}%; 
          width: {particle.size}px; 
          height: {particle.size}px;
          animation-duration: {particle.duration}s;
        "
      ></div>
    {/each}
  </div>

  {#if showWelcome}
    <div class="welcome-content" class:fade-out={!showWelcome}>
      <h1>
        <span class="bounce-letter" style="animation-delay: 0s">W</span><span
          class="bounce-letter"
          style="animation-delay: 0.1s">e</span
        ><span class="bounce-letter" style="animation-delay: 0.2s">l</span><span
          class="bounce-letter"
          style="animation-delay: 0.3s">c</span
        ><span class="bounce-letter" style="animation-delay: 0.4s">o</span><span
          class="bounce-letter"
          style="animation-delay: 0.5s">m</span
        ><span class="bounce-letter" style="animation-delay: 0.6s">e</span><span
          class="bounce-letter"
          style="animation-delay: 0.7s"
        >
        </span><span class="bounce-letter" style="animation-delay: 0.8s">T</span
        ><span class="bounce-letter" style="animation-delay: 0.9s">o</span><span
          class="bounce-letter"
          style="animation-delay: 1s"
        >
        </span><span class="bounce-letter" style="animation-delay: 1.1s">M</span
        ><span class="bounce-letter" style="animation-delay: 1.2s">y</span><br
        /><span class="highlight bounce-letter" style="animation-delay: 1.3s"
          >P</span
        ><span class="highlight bounce-letter" style="animation-delay: 1.4s"
          >o</span
        ><span class="highlight bounce-letter" style="animation-delay: 1.5s"
          >r</span
        ><span class="highlight bounce-letter" style="animation-delay: 1.6s"
          >t</span
        ><span class="highlight bounce-letter" style="animation-delay: 1.7s"
          >f</span
        ><span class="highlight bounce-letter" style="animation-delay: 1.8s"
          >o</span
        ><span class="highlight bounce-letter" style="animation-delay: 1.9s"
          >l</span
        ><span class="highlight bounce-letter" style="animation-delay: 2s"
          >i</span
        ><span class="highlight bounce-letter" style="animation-delay: 2.1s"
          >o</span
        ><span class="highlight bounce-letter" style="animation-delay: 2.2s">
        </span><span
          class="highlight bounce-letter"
          style="animation-delay: 2.3s">W</span
        ><span class="highlight bounce-letter" style="animation-delay: 2.4s"
          >e</span
        ><span class="highlight bounce-letter" style="animation-delay: 2.5s"
          >b</span
        ><span class="highlight bounce-letter" style="animation-delay: 2.6s"
          >s</span
        ><span class="highlight bounce-letter" style="animation-delay: 2.7s"
          >i</span
        ><span class="highlight bounce-letter" style="animation-delay: 2.8s"
          >t</span
        ><span class="highlight bounce-letter" style="animation-delay: 2.9s"
          >e</span
        >
      </h1>
    </div>
  {:else}
    <div class="developer-content">
      <div class="text-section">
        <h2>
          <br /><span class="highlight">Software Developer</span>
        </h2>
        <p class="tagline">CS Student | AI/ML Enthusiast</p>
        <p class="description">
          Second-year Software Engineering student at Bournemouth University
          with hands-on experience in full-stack development and AI projects. Experienced with Python, Svelte, JavaScript, and cloud
          technologies. Passionate about building autonomous AI systems,
          scalable web applications, and secure cloud infrastructure.
        </p>
        <div class="cta-buttons">
          <button
            class="btn-primary"
            on:click={() => {
              const el = document.querySelector("#portfolio");
              el && el.scrollIntoView({ behavior: "smooth" });
            }}>View My Work</button
          >
          <button
            class="btn-secondary"
            on:click={() => {
              const el = document.querySelector("#contact");
              el && el.scrollIntoView({ behavior: "smooth" });
            }}>Get In Touch</button
          >
        </div>
      </div>

      <div class="illustration">
        <div class="tech-illustration">
          <div class="laptop">
            <div class="screen">
              <div class="code-lines">
                <div class="code-line"></div>
                <div class="code-line short"></div>
                <div class="code-line"></div>
                <div class="code-line medium"></div>
              </div>
            </div>
            <div class="keyboard"></div>
          </div>
          <div class="floating-icon icon-1">⚙️</div>
          <div class="floating-icon icon-2">💻</div>
          <div class="floating-icon icon-3">🎨</div>
          <div class="floating-icon icon-4">📱</div>
        </div>
      </div>
    </div>
  {/if}
</section>

<style>
  .hero {
    min-height: 110vh;
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative;
    overflow: hidden;
    background: linear-gradient(135deg, #1e0533, #110a1f, #0a4d68);
  }

  .gradient-bg {
    position: absolute;
    inset: 0;
    background: radial-gradient(
        circle at 20% 50%,
        rgba(138, 43, 226, 0.15),
        transparent 50%
      ),
      radial-gradient(
        circle at 80% 50%,
        rgba(0, 191, 255, 0.15),
        transparent 50%
      );
    animation: pulse 8s ease-in-out infinite;
  }

  @keyframes pulse {
    0%,
    100% {
      opacity: 0.5;
    }
    50% {
      opacity: 0.8;
    }
  }

  .particles {
    position: absolute;
    inset: 0;
    pointer-events: none;
  }

  .particle {
    position: absolute;
    background: rgba(255, 255, 255, 0.6);
    border-radius: 50%;
    animation: float-particle linear infinite;
  }

  @keyframes float-particle {
    0% {
      transform: translateY(0) translateX(0);
      opacity: 0;
    }
    10% {
      opacity: 1;
    }
    90% {
      opacity: 1;
    }
    100% {
      transform: translateY(-100vh) translateX(50px);
      opacity: 0;
    }
  }

  @keyframes float-welcome {
    0%,
    100% {
      transform: translateY(0);
    }
    50% {
      transform: translateY(-30px);
    }
  }

  /* Welcome Content */
  .welcome-content {
    text-align: center;
    z-index: 10;
    animation: fade-in 1s ease;
  }

  .welcome-content.fade-out {
    animation: fade-out 0.5s ease forwards;
  }

  @keyframes fade-in {
    from {
      opacity: 0;
      transform: scale(0.9);
    }
    to {
      opacity: 1;
      transform: scale(1);
    }
  }

  @keyframes fade-out {
    from {
      opacity: 1;
      transform: scale(1);
    }
    to {
      opacity: 0;
      transform: scale(0.9);
    }
  }

  .welcome-content h1 {
    font-size: clamp(2.5rem, 6vw, 4rem);
    font-weight: 700;
    color: white;
    margin-bottom: 2rem;
    line-height: 1.2;
  }

  .bounce-letter {
    display: inline-block;
    animation: bounce-letter 0.6s ease-in-out forwards;
  }

  @keyframes bounce-letter {
    0%,
    100% {
      transform: translateY(0);
    }
    50% {
      transform: translateY(-20px);
    }
  }

  .highlight {
    background: linear-gradient(90deg, #a855f7, #3b82f6);
    -webkit-background-clip: text;
    background-clip: text;
    -webkit-text-fill-color: transparent;
  }

  .cta-btn {
    padding: 1rem 3rem;
    background: linear-gradient(90deg, #a855f7, #3b82f6);
    color: white;
    border: none;
    border-radius: 2rem;
    font-size: 1.1rem;
    font-weight: 600;
    cursor: pointer;
    transition:
      transform 0.3s ease,
      box-shadow 0.3s ease;
  }

  .cta-btn:hover {
    transform: translateY(-3px);
    box-shadow: 0 10px 30px rgba(168, 85, 247, 0.4);
  }

  /* Developer Content */
  .developer-content {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 4rem;
    max-width: 1200px;
    padding: 2rem;
    z-index: 10;
    animation: fade-in 1s ease;
  }

  .text-section h2 {
    font-size: clamp(3rem, 7vw, 5rem);
    font-weight: 900;
    color: white;
    margin-top: -1rem;
    margin-bottom: 0.5rem;
    line-height: 1.1;
  }

  .tagline {
    color: #a855f7;
    font-size: 1.2rem;
    margin-bottom: 1.5rem;
  }

  .description {
    color: rgba(255, 255, 255, 0.7);
    line-height: 1.8;
    margin-bottom: 2rem;
    font-size: 1.05rem;
  }

  .cta-buttons {
    display: flex;
    gap: 1rem;
    margin-bottom: 2rem;
  }

  .btn-primary,
  .btn-secondary {
    padding: 0.875rem 2rem;
    border: none;
    border-radius: 0.5rem;
    font-size: 1rem;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.3s ease;
  }

  .btn-primary {
    background: linear-gradient(90deg, #a855f7, #3b82f6);
    color: white;
  }

  .btn-primary:hover {
    transform: translateY(-2px);
    box-shadow: 0 8px 20px rgba(168, 85, 247, 0.4);
  }

  .btn-secondary {
    background: transparent;
    color: white;
    border: 2px solid rgba(255, 255, 255, 0.3);
  }

  .btn-secondary:hover {
    background: rgba(255, 255, 255, 0.1);
    border-color: rgba(255, 255, 255, 0.5);
  }

  .social-links {
    display: flex;
    gap: 1rem;
  }

  .social-icon {
    width: 40px;
    height: 40px;
    display: flex;
    align-items: center;
    justify-content: center;
    background: rgba(255, 255, 255, 0.1);
    border-radius: 0.5rem;
    color: white;
    transition: all 0.3s ease;
  }

  .social-icon:hover {
    background: linear-gradient(90deg, #a855f7, #3b82f6);
    transform: translateY(-3px);
  }

  .social-icon svg {
    width: 20px;
    height: 20px;
  }

  /* Tech Illustration */
  .illustration {
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .tech-illustration {
    position: relative;
    width: 100%;
    max-width: 500px;
  }

  .laptop {
    position: relative;
    width: 100%;
  }

  .screen {
    background: linear-gradient(135deg, #2d1b4e, #1a1a2e);
    border-radius: 1rem 1rem 0 0;
    padding: 2rem;
    border: 3px solid #3b2667;
    box-shadow: 0 20px 60px rgba(0, 0, 0, 0.5);
    animation: screen-glow 3s ease-in-out infinite;
  }

  @keyframes screen-glow {
    0%,
    100% {
      box-shadow: 0 20px 60px rgba(168, 85, 247, 0.3);
    }
    50% {
      box-shadow: 0 20px 60px rgba(59, 130, 246, 0.3);
    }
  }

  .code-lines {
    display: flex;
    flex-direction: column;
    gap: 0.75rem;
  }

  .code-line {
    height: 8px;
    background: linear-gradient(90deg, #a855f7, #3b82f6);
    border-radius: 4px;
    animation: code-pulse 2s ease-in-out infinite;
  }

  .code-line.short {
    width: 60%;
  }

  .code-line.medium {
    width: 80%;
  }

  @keyframes code-pulse {
    0%,
    100% {
      opacity: 0.6;
    }
    50% {
      opacity: 1;
    }
  }

  .keyboard {
    height: 20px;
    background: linear-gradient(135deg, #1a1a2e, #0f0f1e);
    border-radius: 0 0 1rem 1rem;
    border: 3px solid #3b2667;
    border-top: none;
  }

  .floating-icon {
    position: absolute;
    font-size: 2.5rem;
    animation: float-icon 3s ease-in-out infinite;
  }

  .icon-1 {
    top: -10%;
    right: 10%;
    animation-delay: 0s;
  }

  .icon-2 {
    top: 20%;
    right: -10%;
    animation-delay: 0.5s;
  }

  .icon-3 {
    bottom: 20%;
    left: -10%;
    animation-delay: 1s;
  }

  .icon-4 {
    bottom: -5%;
    right: 20%;
    animation-delay: 1.5s;
  }

  @keyframes float-icon {
    0%,
    100% {
      transform: translateY(0) rotate(0deg);
    }
    50% {
      transform: translateY(-20px) rotate(10deg);
    }
  }

  @media (max-width: 968px) {
    .developer-content {
      grid-template-columns: 1fr;
      text-align: center;
    }

    .cta-buttons {
      justify-content: center;
    }

    .social-links {
      justify-content: center;
    }
  }
</style>
