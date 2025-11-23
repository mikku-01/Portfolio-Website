<script>
  // no script logic needed here right now
</script>

<section id="about" class="about">
  <div class="container">
    <div class="header">
      <h2>About Me</h2>
      <p class="subtitle">My introduction and what I do professionally</p>
    </div>
    <div class="content-grid">
      <div class="profile-section">
        <div class="profile-card">
          <div class="profile-image">
            <div class="image-placeholder">
              <svg viewBox="0 0 24 24" fill="currentColor">
                <path
                  d="M12 12c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm0 2c-2.67 0-8 1.34-8 4v2h16v-2c0-2.66-5.33-4-8-4z"
                />
              </svg>
            </div>
          </div>

          <h3>
            Hello, I'm<br />
            <span class="name">Mikku Matysik</span>
          </h3>

          <p class="bio">
            What started as curiosity has grown into a genuine passion for
            coding. I love the problem-solving aspect of development and find
            immense satisfaction in bringing ideas to life through code.
            Currently studying Software Engineering at Bournemouth University,
            I'm constantly discovering new technologies and enjoying every step
            of this journey into becoming a skilled developer.
          </p>
        </div>
      </div>

      <div class="stats-section">
        <div class="stat-card">
          <div class="stat-icon">
            <svg
              viewBox="0 0 24 24"
              fill="none"
              stroke="currentColor"
              stroke-width="2"
            >
              <path d="M9 1212 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z" />
            </svg>
          </div>
          <div class="stat-info">
            <h4>2+</h4>
            <p>Years CS Education</p>
          </div>
        </div>

        <div class="stat-card">
          <div class="stat-icon">
            <svg
              viewBox="0 0 24 24"
              fill="none"
              stroke="currentColor"
              stroke-width="2"
            >
              <path
                d="M19 21V5a2 2 0 00-2-2H7a2 2 0 00-2 2v16m1...-1 4h1m4-4h1m-1 4h1m-5 10v-5a1 1 0 011-1h2a1 1 0 011 1v5m-4 0h4"
              />
            </svg>
          </div>
          <div class="stat-info">
            <h4>7+</h4>
            <p>Projects</p>
          </div>
        </div>

        <div class="stat-card">
          <div class="stat-icon">
            <svg
              viewBox="0 0 24 24"
              fill="none"
              stroke="currentColor"
              stroke-width="2"
            >
              <path d="M4 4h16v4H4zM4 10h10v4H4zM4 16h7v4H4z" />
            </svg>
          </div>
          <div class="stat-info">
            <h4>Cloud</h4>
            <p>Azure & AWS</p>
          </div>
        </div>

        <div class="stat-card">
          <div class="stat-icon">
            <svg
              viewBox="0 0 24 24"
              fill="none"
              stroke="currentColor"
              stroke-width="2"
            >
              <path d="M12 2v20m8-10H4" />
              <circle cx="12" cy="12" r="3" />
            </svg>
          </div>
          <div class="stat-info">
            <h4>5+ Years</h4>
            <p>Sports & Fitness</p>
          </div>
        </div>

        <div class="stat-card">
          <div class="stat-icon">
            <svg
              viewBox="0 0 24 24"
              fill="none"
              stroke="currentColor"
              stroke-width="2"
            >
              <path
                d="M9.663 17h4.673M12 3v1m6.364 1.636l-.707...21 12h-1M4 12H3m3.343-5.657l-.707-.707m2.828 9.9a5 5 0 117.072 0l-.548.547A3.374 3.374 0 0014 18.469V19a2 2 0 11-4 0v-.531c0-.895-.356-1.754-.988-2.386l-.548-.547z"
              />
            </svg>
          </div>
          <div class="stat-info">
            <h4>Problems</h4>
            <p>Solving Mindset</p>
          </div>
        </div>

        <div class="stat-card">
          <div class="stat-icon">
            <svg
              viewBox="0 0 24 24"
              fill="none"
              stroke="currentColor"
              stroke-width="2"
            >
              <path
                d="M5 3v4M3 5h4M6 17v4m-2-2h4m5-16l2.286 6.857L2...-6.857L5 12l5.714-2.143L13 3z"
              />
            </svg>
          </div>
          <div class="stat-info">
            <h4>Top 0.6%</h4>
            <p>Competitive Gamer</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<style>
  .about {
    min-height: auto;
    padding: 0rem 2rem 1.5rem 2rem;
    margin-top: -2rem;
    background: linear-gradient(135deg, #0f0728, #1e0b2e, #0a3d62);
    position: relative;
  }
  .about::before {
    content: "";
    position: absolute;
    inset: 0;
    background: radial-gradient(
        circle at 30% 50%,
        rgba(138, 43, 226, 0.1),
        transparent 50%
      ),
      radial-gradient(
        circle at 70% 50%,
        rgba(0, 191, 255, 0.1),
        transparent 50%
      );
    pointer-events: none;
  }

  .container {
    max-width: 1200px;
    margin: 0 auto;
    position: relative;
    z-index: 1;
  }
  .header {
    text-align: center;
    margin-bottom: 1rem;
  }

  .header h2 {
    font-size: clamp(1.8rem, 5vw, 2.5rem);
    font-weight: 900;
    background: linear-gradient(90deg, #a855f7, #3b82f6);
    -webkit-background-clip: text;
    background-clip: text;
    -webkit-text-fill-color: transparent;
    margin-bottom: 0.25rem;
  }
  .subtitle {
    color: rgba(255, 255, 255, 0.6);
    font-size: 0.9rem;
  }
  .content-grid {
    display: grid;
    grid-template-columns: 1fr 1.5fr;
    gap: 1.5rem;
    align-items: start;
  }

  .stats-section {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(140px, 1fr));
    gap: 1rem;
  }

  .stat-card {
    background: rgba(255, 255, 255, 0.05);
    backdrop-filter: blur(10px);
    border: 1px solid rgba(255, 255, 255, 0.1);
    border-radius: 1rem;
    padding: 0.9rem 1rem;
    display: flex;
    align-items: center;
    gap: 0.75rem;
    transition: all 0.3s ease;
  }

  .stat-card:hover {
    transform: translateY(-5px);
    background: rgba(255, 255, 255, 0.08);
    box-shadow: 0 15px 40px rgba(168, 85, 247, 0.3);
    border-color: rgba(168, 85, 247, 0.3);
  }

  .stat-icon {
    width: 48px;
    height: 48px;
    background: linear-gradient(135deg, #6366f1, #8b5cf6, #a855f7);
    border-radius: 14px;
    display: flex;
    align-items: center;
    justify-content: center;
    color: white;
    box-shadow: 0 8px 25px rgba(168, 85, 247, 0.25);
    position: relative;
    overflow: hidden;
  }

  .stat-icon svg {
    width: 24px;
    height: 24px;
    color: #ffffff;
    filter: drop-shadow(0 1px 2px rgba(0, 0, 0, 0.2));
    z-index: 1;
  }

  .stat-info h4 {
    font-size: 1rem;
    font-weight: 700;
    color: #cbd5e1;
    margin-bottom: 0.15rem;
  }

  .stat-info p {
    font-size: 0.8rem;
    color: #94a3b8;
  }

  .profile-card {
    background: rgba(255, 255, 255, 0.05);
    backdrop-filter: blur(10px);
    border: 1px solid rgba(255, 255, 255, 0.1);
    border-radius: 1.5rem;
    padding: 1.25rem;
    text-align: center;
  }

  .profile-image {
    width: 150px;
    height: 150px;
    margin: 0 auto 2rem;
    border-radius: 50%;
    background: linear-gradient(135deg, #a855f7, #3b82f6);
    padding: 4px;
    position: relative;
  }
  .image-placeholder {
    width: 100%;
    height: 100%;
    border-radius: 50%;
    background: linear-gradient(135deg, #1e0533, #0a4d68);
    display: flex;
    align-items: center;
    justify-content: center;
    color: rgba(255, 255, 255, 0.3);
  }
  .image-placeholder svg {
    width: 80px;
    height: 80px;
  }
  .profile-card h3 {
    font-size: 1rem;
    color: rgba(255, 255, 255, 0.7);
    margin: 0.75rem;
    line-height: 1.4;
  }

  .name {
    display: block;
    font-size: 1rem;
    font-weight: 700;
    background: linear-gradient(90deg, #a855f7, #3b82f6);
    -webkit-background-clip: text;
    background-clip: text;
    -webkit-text-fill-color: transparent;
  }
  .bio {
    color: rgba(255, 255, 255, 0.6);
    line-height: 1.5;
    margin-bottom: 0.75rem;
    font-size: 0.85rem;
  }
  .stats-section {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 0.75rem;
  }
  .stat-card {
    background: rgba(255, 255, 255, 0.05);
    backdrop-filter: blur(10px);
    border: 1px solid rgba(255, 255, 255, 0.1);
    border-radius: 1rem;
    padding: 0.75rem;
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
    transition: all 0.3s ease;
  }
  .stat-card:hover {
    background: rgba(255, 255, 255, 0.12);
    transform: translateY(-8px);
    box-shadow: 0 15px 35px rgba(168, 85, 247, 0.15);
    border-color: rgba(168, 85, 247, 0.3);
  }

  .stat-icon {
    width: 48px;
    height: 48px;
    background: linear-gradient(135deg, #6366f1, #8b5cf6, #a855f7);
    border-radius: 14px;
    display: flex;
    align-items: center;
    justify-content: center;
    margin-bottom: 1rem;
    color: white;
    box-shadow:
      0 8px 25px rgba(168, 85, 247, 0.25),
      inset 0 1px 0 rgba(255, 255, 255, 0.1);
    position: relative;
    overflow: hidden;
  }
  .stat-icon::before {
    content: "";
    position: absolute;
    top: 0;
    left: -100%;
    width: 100%;
    height: 100%;
    background: linear-gradient(
      90deg,
      transparent,
      rgba(255, 255, 255, 0.15),
      transparent
    );
    transition: left 0.5s ease;
  }

  .stat-card:hover .stat-icon::before {
    left: 100%;
  }

  .stat-icon svg {
    width: 24px;
    height: 24px;
    filter: drop-shadow(0 1px 2px rgba(0, 0, 0, 0.2));
    z-index: 1;
  }
  .stat-info h4 {
    font-size: 1.1rem;
    font-weight: 700;
    color: #e2e8f0;
    margin-bottom: 0.05rem;
  }
  .stat-info p {
    color: rgba(255, 255, 255, 0.6);
    font-size: 0.8rem;
  }

  @media (max-width: 968px) {
    .content-grid {
      grid-template-columns: 1fr;
    }

    .stats-section {
      grid-template-columns: repeat(2, 1fr);
    }
  }
  @media (max-width: 640px) {
    .stats-section {
      grid-template-columns: 1fr;
    }
  }
</style>
