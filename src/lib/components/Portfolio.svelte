<script>
  let activeTab = "skills";
  let darkMode = false;

  const techStack = [
    { name: "Python", icon: "🐍", color: "#3776ab" },
    { name: "JavaScript", icon: "JS", color: "#f0db4f" },
    { name: "React", icon: "⚛️", color: "#61dafb" },
    { name: "Node.js", icon: "📗", color: "#68a063" },
    { name: "LangChain", icon: "🔗", color: "#a855f7" },
    { name: "Azure", icon: "☁️", color: "#0078d4" },
    { name: "AWS", icon: "🟠", color: "#ff9900" },
    { name: "Docker", icon: "🐳", color: "#2496ed" },
    { name: "TensorFlow", icon: "🧠", color: "#ff6f20" },
    { name: "SQL", icon: "💾", color: "#336791" },
    { name: "Svelte", icon: "⚡", color: "#ff3e00" },
    { name: "PyTorch", icon: "🔥", color: "#ee4c2c" },
    { name: "Agentic AI", icon: "🧠", color: "#8b5cf6" },
  ];

  const projects = [
    {
      title: "Agentic Research Assistant",
      description:
        "Expert-level research system with 4-stage workflow: Decomposition → Research → Synthesis → Evaluation. 85% accuracy score on complex analysis tasks",
      tech: ["Python", "LangChain", "OpenAI", "Prompt Engineering"],
      image: "🧠",
    },
    {
      title: "Multi Agent System For Data Collection And Processing",
      description:
        "Multi-agent system with zero manual intervention featuring self-healing web scraping, ML-based anomaly detection, and NLP entity extraction. Processed 5 sources with 100% success rate and 85.4% data quality score",
      tech: [
        "Python",
        "LangChain",
        "CrewAI",
        "scikit-learn",
        "spaCy",
        "BeautifulSoup",
      ],
      image: "🤖",
    },
    {
      title: "RAG Powered AI Chatbot",
      description:
        "RAG chatbot with ChromaDB vector retrieval and Flask + Streamlit stack. Supports document ingestion (Word/PDF/Markdown), semantic search, and real-time AI responses with modular architecture for easy scaling",
      tech: [
        "Python",
        "LangChain",
        "ChromaDB",
        "HuggingFace",
        "OpenAI",
        "Flask",
        "Streamlit",
      ],
      image: "💬",
    },
    {
      title: "Secure Cloud Backup Tool",
      description:
        "Security-driven backup tool with AES-256 encryption, SHA-256 integrity checks, and proper key management. Features timestamped backups, integrity manifests, and 100% successful encrypt/decrypt operations with sub-second performance",
      tech: ["Python", "Cryptography", "JSON"],
      image: "🔐",
    },
    {
      title: "AWS DeepRacer Competition",
      description:
        "Led a team of 4 students at the AWS DeepRacer event with MOD. Completed 25 hours of hands-on ML training, achieving one of the best simulation results. Applied reinforcement learning, model optimisation, and AWS tools for autonomous racing simulation.",
      tech: ["AWS", "Reinforcement Learning", "Machine Learning", "Python"],
      image: "🏎️",
    },
    {
      title: "Azure Financial Management PoC",
      description:
        "Real-time cloud cost monitoring & governance with Azure SQL, Power BI, Logic Apps",
      tech: ["Azure", "Power BI", "SQL"],
      image: "💰",
    },
    {
      title: "Portfolio Website",
      description:
        "Professional full-stack animated portfolio website built with SvelteKit featuring glassmorphism design, particle systems, bouncing letter animations, and smooth transitions. Includes functional contact form with email integration, responsive design, and optimised performance with Vite build system.",
      tech: ["Svelte", "SvelteKit", "Vite", "CSS3", "JavaScript", "Web3Forms"],
      image: "💼",
    },
  ];

  const certificates = [
    {
      title: "Machine Learning with Python",
      issuer: "IBM (Coursera)",
      date: "2025",
      icon: "🎓",
    },
    {
      title: "AWS Generative AI For Developers",
      issuer: "AWS",
      date: "In Progress",
      icon: "🤖",
    },
    {
      title: "IEUK 2025: Technology & Engineering",
      issuer: "Institution of Engineering UK",
      date: "2025",
      icon: "📜",
    },
  ];

  const internships = [
    {
      title: "Data Analyst Intern",
      company: "Maharishi",
      location: "London",
      date: "Nov 2023",
      description:
        "Analysed social media metrics for Maharishi x Arsenal campaign, improving engagement by 15%. Structured and cleaned supplier and wholesaler data for reporting and decision-making.",
      icon: "📊",
    },
  ];
</script>

<section id="portfolio" class="portfolio">
  <div class="container">
    <div class="header">
      <h2>Portfolio Showcase</h2>
      <p class="subtitle">
        Explore my projects, certifications, and technical expertise
      </p>
    </div>
    <div class="tabs">
      <button
        class="tab"
        class:active={activeTab === "skills"}
        on:click={() => (activeTab = "skills")}
      >
        Certificates
      </button>
      <button
        class="tab"
        class:active={activeTab === "internships"}
        on:click={() => (activeTab = "internships")}
      >
        Internships
      </button>
      <button
        class="tab"
        class:active={activeTab === "projects"}
        on:click={() => (activeTab = "projects")}
      >
        Tech Stack
      </button>
    </div>

    <div class="tab-content">
      {#if activeTab === "skills"}
        <div class="tech-grid">
          {#each techStack as tech}
            <div class="tech-card">
              <div
                class="tech-icon"
                style="background: {tech.color}20; color: {tech.color}"
              >
                {tech.icon}
              </div>
              <p>{tech.name}</p>
            </div>
          {/each}
        </div>
      {:else if activeTab === "internships"}
        <div class="internship-grid">
          {#each internships as internship}
            <div class="internship-card">
              <div class="internship-header"></div>
              <div class="internship-icon">{internship.icon}</div>
              <div class="internship-title-section">
                <h4>{internship.title}</h4>
                <p class="company">
                  {internship.company} • {internship.location}
                </p>
                <p class="date">{internship.date}</p>
              </div>
              <p class="internship-description">{internship.description}</p>
            </div>
          {/each}
        </div>
      {:else if activeTab === "certificates"}
        <div class="cert-grid">
          {#each certificates as cert}
            <div class="cert-card">
              <div class="cert-icon">{cert.icon}</div>
              <h3>{cert.title}</h3>
              <p class="issuer">{cert.issuer}</p>
              <p class="date">{cert.date}</p>
            </div>
          {/each}
        </div>
      {:else if activeTab === "projects"}
        <div class="project-grid">
          {#each projects as project}
            <div class="project-card">
              <div class="project-icon">{project.image}</div>
              <h3>{project.title}</h3>
              <p class="project-desc">{project.description}</p>
              <div class="project-tech">
                {#each project.tech as tech}
                  <span class="tech-badge">{tech}</span>
                {/each}
              </div>
            </div>
          {/each}
        </div>
      {/if}
    </div>
  </div>
</section>

<style>
  .portfolio {
    min-height: auto;
    padding: 1.5rem 2rem 1.5rem 2rem;
    background: linear-gradient(135deg, #0a0e27 #1a1f3a);
    position: relative;
  }
  .portfolio::before {
    content: "";
    position: absolute;
    inset: 0;
    background: radial-gradient(
        circle at 20% 30%,
        rgba(138, 43, 226, 0.15),
        transparent 40%
      ),
      radial-gradient(
        circle at 80% 70%,
        rgba(0, 191, 255, 0.15),
        transparent 40%
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
    font-size: clamp(1.8rem, 5vw, 2.8rem);
    font-weight: 900;
    background: linear-gradient(90deg, #a855f7, #3b82f6);
    -webkit-background-clip: text;
    background-clip: text;
    -webkit-text-fill-color: transparent;
    margin-bottom: 0.5rem;
  }
  .subtitle {
    color: rgba(255, 255, 255, 0.6);
    font-size: 0.9rem;
  }
  .tabs {
    display: flex;
    justify-content: center;
    gap: 0.75rem;
    margin-bottom: 1rem;
  }
  .tab {
    padding: 0.5rem 1.25rem;
    background-color: rgba(225, 225, 255, 0.05);
    border: 1px solid rgba(225, 225, 255, 0.1);
    border-radius: 0.75rem;
    color: rgba(225, 225, 255, 0.7);
    font-size: 0.75rem;
    cursor: pointer;
    transition: all 0.3s ease;
  }
  .tab.active {
    background: linear-gradient(90deg, #a855f7, #3b82f6);
    color: white;
    border-color: transparent;
    box-shadow: 0 8px 20px rgba(168, 85, 247, 0.3);
  }
  .tab:hover:not(.active) {
    background: rgba(225, 225, 225, 0.1);
    border-color: rgba(168, 85, 247, 0.3);
  }
  .tab-content {
    animation: fade-in 0.5s ease;
  }
  @keyframes fade-in {
    from {
      opacity: 0;
      transform: translateY(20px);
    }
    to {
      opacity: 1;
      transform: translateY(0);
    }
  }
  .tech-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(120px, 1fr));
    gap: 1rem;
  }
  .tech-card {
    background: rgba(255, 255, 255, 0.05);
    backdrop-filter: blur(10px);
    border: 1px solid rgba(255, 255, 255, 0.1);
    border-radius: 1rem;
    padding: 1rem 0.75rem;
    text-align: center;
    transition: all 0.3s ease;
  }
  .tech-card:hover {
    transform: translateY(-8px);
    background: rgba(225, 225, 255, 0.8);
    box-shadow: 0 10px 30px rgba(168, 85, 247, 0.2);
  }
  .tech-icon {
    width: 60px;
    height: 60px;
    margin: 0 auto 0.75rem;
    border-radius: 1rem;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 2rem;
    font-weight: 700;
  }

  .tech-card p {
    font-size: 0.95rem;
    font-weight: 600;
    color: white;
  }
  .internship-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 1 rem;
  }
  .internship-card {
    background: rgba(255, 255, 255, 0.05);
    backdrop-filter: blur(10px);
    border: 1px solid rgba(255, 255, 255, 0.1);
    border-radius: 1rem;
    padding: 1.25rem;
    transition: all 0.3s ease;
  }
  .internship-header {
    display: flex;
    gap: 1rem;
    margin-bottom: 1rem;
  }
  .internship-icon {
    min-width: 60px;
    font-size: 2.5rem;
    display: flex;
    align-items: center;
  }
  .internship-title-section h4 {
    font-size: 1rem;
    font-weight: 700;
    color: white;
    margin: 0;
    margin-bottom: 0.25rem;
  }
  .company {
    font-size: 0.85rem;
    color: rgba(168, 85, 247, 0.8);
    margin: 0;
    margin-bottom: 0.1rem;
  }
  .date {
    font-size: 0.8rem;
    color: rgba(255, 255, 255, 0.5);
    margin: 0;
  }
  .internship-description {
    font-size: 0.85rem;
    color: rgba(255, 255, 255, 0.7);
    line-height: 1.5rem;
    margin: 0;
  }
  .cert-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  }
  .cert-card {
    background: rgba(255, 255, 255, 0.05);
    backdrop-filter: blur(10px);
    border: 1px solid rgba(255, 255, 255, 0.1);
    border-radius: 1.5rem;
    padding: 1.5rem;
    text-align: center;
    transition: all 0.3s ease;
  }
  .cert-card:hover {
    transform: translateY(-5px);
    background: rgba(255, 255, 255, 0.08);
    box-shadow: 0 15px 40px rgba(168, 85, 247, 0.3);
  }

  .cert-icon {
    font-size: 4rem;
    margin-bottom: 1rem;
  }

  .cert-card h3 {
    color: white;
    font-size: 1.5rem;
    margin-bottom: 0.5rem;
  }

  .issuer {
    color: #a855f7;
    font-weight: 600;
    margin-bottom: 0.25rem;
  }

  .date {
    color: rgba(255, 255, 255, 0.5);
    font-size: 0.9rem;
  }

  /* Projects Grid */
  .project-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 2rem;
  }

  .project-card {
    background: rgba(255, 255, 255, 0.05);
    backdrop-filter: blur(10px);
    border: 1px solid rgba(255, 255, 255, 0.1);
    border-radius: 1.5rem;
    padding: 2rem;
    transition: all 0.3s ease;
  }

  .project-card:hover {
    transform: translateY(-5px);
    background: rgba(255, 255, 255, 0.08);
    box-shadow: 0 15px 40px rgba(168, 85, 247, 0.3);
  }

  .project-icon {
    font-size: 3.5rem;
    margin-bottom: 1rem;
  }

  .project-card h3 {
    color: white;
    font-size: 1.4rem;
    margin-bottom: 0.75rem;
  }

  .project-desc {
    color: rgba(255, 255, 255, 0.6);
    line-height: 1.6;
    margin-bottom: 1.25rem;
  }

  .project-tech {
    display: flex;
    flex-wrap: wrap;
    gap: 0.5rem;
    margin-bottom: 1.5rem;
  }

  .tech-badge {
    padding: 0.4rem 0.9rem;
    background: rgba(168, 85, 247, 0.2);
    color: #a855f7;
    border-radius: 2rem;
    font-size: 0.85rem;
    font-weight: 600;
  }

  .view-btn {
    width: 100%;
    padding: 0.875rem;
    background: linear-gradient(90deg, #a855f7, #3b82f6);
    color: white;
    border: none;
    border-radius: 0.5rem;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.3s ease;
  }

  .view-btn:hover {
    transform: translateY(-2px);
    box-shadow: 0 8px 20px rgba(168, 85, 247, 0.4);
  }

  @media (max-width: 768px) {
    .tabs {
      flex-direction: column;
    }

    .tech-grid {
      grid-template-columns: repeat(auto-fit, minmax(120px, 1fr));
    }
  }
</style>
