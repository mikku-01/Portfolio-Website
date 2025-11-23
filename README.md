ontinuing from Part 1, this section covers the remaining components with animations, interactivity, and email integration.

---

## 🎬 Component 2: Hero Section with Animations

### File: `src/lib/components/Hero.svelte`

#### 1. Script Section (Setup & Logic)

```svelte
<script>
  import { onMount } from "svelte";
  let showWelcome = true;
  let particles = [];
  onMount(() => {
    // Create 30 floating particles
    for (let i = 0; i < 30; i++) {
      particles.push({
        x: Math.random() * 100,
        y: Math.random() * 100,
        size: Math.random() * 3 + 1,
        duration: Math.random() * 3 + 2,
      });
    }
    particles = particles;
    // Auto-transition after 3.5 seconds
    const timer = setTimeout(() => {
      showWelcome = false;
    }, 3500);
    return () => clearTimeout(timer);
  });
</script>
```

**Explanation:**

- Imports Svelte's `onMount` for running code after component mounts.
- Initializes `showWelcome` (controls welcome screen) and `particles` (for animation).
- Fills `particles` with 30 random objects for floating effect.
- After 3.5 seconds, hides welcome screen.

#### 2. Markup Section (HTML Structure)

```svelte
<section class="hero">
  <div class="gradient-bg"></div>
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
    <div class="welcome-content">
      <h1>
        <!-- Bouncing welcome letters -->
        <span class="bounce-letter" style="animation-delay: 0s">W</span>
        <span class="bounce-letter" style="animation-delay: 0.1s">e</span>
        <span class="bounce-letter" style="animation-delay: 0.2s">l</span>
        <span class="bounce-letter" style="animation-delay: 0.3s">c</span>
        <span class="bounce-letter" style="animation-delay: 0.4s">o</span>
        <span class="bounce-letter" style="animation-delay: 0.5s">m</span>
        <span class="bounce-letter" style="animation-delay: 0.6s">e</span>
        <span class="bounce-letter" style="animation-delay: 0.7s"></span>
        <span class="bounce-letter" style="animation-delay: 0.8s">T</span>
        <span class="bounce-letter" style="animation-delay: 0.9s">o</span>
        <span class="bounce-letter" style="animation-delay: 1s"></span>
        <span class="bounce-letter" style="animation-delay: 1.1s">M</span>
        <span class="bounce-letter" style="animation-delay: 1.2s">y</span>
        <br />
        <span class="highlight bounce-letter" style="animation-delay: 1.3s">P</span>
        <span class="highlight bounce-letter" style="animation-delay: 1.4s">o</span>
        <span class="highlight bounce-letter" style="animation-delay: 1.5s">r</span>
        <span class="highlight bounce-letter" style="animation-delay: 1.6s">t</span>
        <span class="highlight bounce-letter" style="animation-delay: 1.7s">f</span>
        <span class="highlight bounce-letter" style="animation-delay: 1.8s">o</span>
        <span class="highlight bounce-letter" style="animation-delay: 1.9s">l</span>
        <span class="highlight bounce-letter" style="animation-delay: 2s">i</span>
        <span class="highlight bounce-letter" style="animation-delay: 2.1s">o</span>
        <span class="highlight bounce-letter" style="animation-delay: 2.2s"></span>
        <span class="highlight bounce-letter" style="animation-delay: 2.3s">W</span>
        <span class="highlight bounce-letter" style="animation-delay: 2.4s">e</span>
        <span class="highlight bounce-letter" style="animation-delay: 2.5s">b</span>
        <span class="highlight bounce-letter" style="animation-delay: 2.6s">s</span>
        <span class="highlight bounce-letter" style="animation-delay: 2.7s">i</span>
        <span class="highlight bounce-letter" style="animation-delay: 2.8s">t</span>
        <span class="highlight bounce-letter" style="animation-delay: 2.9s">e</span>
      </h1>
      <button class="cta-btn">View Portfolio</button>
    </div>
  {:else}
    <div class="developer-content">
      <div class="text-section">
        <h2>AI & ML<br /><span class="highlight">Software Engineer</span></h2>
        <p class="tagline">CS Student | Cloud Computing | Security</p>
        <p class="description">
          BSc Software Engineering student at Bournemouth University. Passionate
          about building intelligent systems, autonomous agents, and scalable
          cloud infrastructure. Experienced in Python, LangChain, Azure, and AWS.
        </p>
        <div class="cta-buttons">
          <button class="btn-primary">View My Work</button>
          <button class="btn-secondary">Get In Touch</button>
        </div>
        <div class="social-links">
          <a
            href="https://www.linkedin.com/in/mikku-matysik-aa2810274"
            target="_blank"
            rel="noopener noreferrer"
            class="social-icon"
            aria-label="LinkedIn"
          >
            <!-- LinkedIn SVG icon -->
            <svg viewBox="0 0 24 24" fill="currentColor">
              <path d="M19 0h-14c-2.761 0-5 2.239-5 5v14c0 2.761 2.239 5 5 5h14c2.762 0 5-2.239 5-5v-14c0-2.761-2.238-5-5-5zm-11 19h-3v-11h3v11zm-1.5-12.268c-.966 0-1.75-.79-1.75-1.764s.784-1.764 1.75-1.764 1.75.79 1.75 1.764-.783 1.764-1.75 1.764zm13.5 12.268h-3v-5.604c0-3.368-4-3.113-4 0v5.604h-3v-11h3v1.765c1.396-2.586 7-2.777 7 2.476v6.759z"/>
            </svg>
          </a>
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
```

**Explanation:**

- Renders a gradient background and animated particles.
- Shows a bouncing "Welcome" message for 3.5s, then reveals developer intro.
- Uses Svelte `{#each}` for particles and `{#if}` for conditional content.

---

#### 3. CSS Animations and Styles

```css
@keyframes bounce-letter {
  0%,
  100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-20px);
  }
}
@keyframes float-particle {
  0% {
    transform: translateY(0) translateX(0);
    opacity: 0;
  }
  10%,
  90% {
    opacity: 1;
  }
  100% {
    transform: translateY(-100vh) translateX(50px);
    opacity: 0;
  }
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
.gradient-bg {
  position: absolute;
  inset: 0;
  background: radial-gradient(
      circle at 20% 50%,
      rgba(138, 43, 226, 0.15),
      transparent 50%
    ), radial-gradient(circle at 80% 50%, rgba(0, 191, 255, 0.15), transparent
        50%);
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
```

**Explanation:**

- `bounce-letter`: Bounces each letter up and down.
- `float-particle`: Animates particles floating upward.
- `fade-in`: Smoothly fades elements in.
- `.gradient-bg`: Animated glowing background.

## 👤 Component 3: About Section

### 1. Section Structure

```svelte
<section id="about" class="about">
  <div class="container">
    <div class="header">
      <h2>About Me</h2>
      <p class="subtitle">My introduction and what I do professionally</p>
    </div>
    <div class="content-grid">
      <!-- Profile and stats go here -->
    </div>
  </div>
</section>
```

**Explanation:**

- The About section uses a container with a header and a grid for profile and stats.

### 2. Profile Card

```svelte
<div class="profile-section">
  <div class="profile-card">
    <div class="profile-image">
      <div class="image-placeholder">
        <svg viewBox="0 0 24 24" fill="currentColor">
          <path d="M12 12c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm0 2c-2.67 0-8 1.34-8 4v2h16v-2c0-2.66-5.33-4-8-4z"/>
        </svg>
      </div>
    </div>
    <h3>Hello, I'm<br /><span class="name">Mikku Matysik</span></h3>
    <p class="bio">
      BSc Software Engineering student at Bournemouth University.<br>
      Passionate about AI, Machine Learning, Cloud Computing, and building scalable systems.
      Experienced in Python, JavaScript, and modern web technologies.
    </p>
    <button class="download-cv">Download CV</button>
  </div>
</div>
```

**Explanation:**

- Shows a profile image (SVG placeholder), name, bio, and a download CV button.

### 3. Stats Grid

```svelte
<div class="stats-section">
  <div class="stat-card">
    <div class="stat-icon">
      <!-- SVG icon -->
    </div>
    <div class="stat-info">
      <h4>2+</h4>
      <p>Years CS Education</p>
    </div>
  </div>
  <!-- Repeat for each stat: AI/ML Projects, Cloud, Security, Problem Solving, Competitive Gamer -->
</div>
```

**Explanation:**

- Each stat card shows an icon, a headline, and a description. Repeat for all 6 stats.

### 4. Styles (Glassmorphism, Grid, Hover)

```css
.about {
  min-height: auto;
  padding: 0rem 2rem 1.5rem 2rem;
  margin-top: -2rem;
  background: linear-gradient(135deg, #0f0728, #1a0b2e, #0a3d62);
  position: relative;
}
.content-grid {
  display: grid;
  grid-template-columns: 1fr 1.5fr;
  gap: 1.5rem;
  align-items: start;
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
  background: rgba(255, 255, 255, 0.08);
  transform: translateY(-5px);
  box-shadow: 0 10px 30px rgba(168, 85, 247, 0.2);
}
```

**Explanation:**

- `.about` uses a gradient background.
- `.content-grid` arranges profile and stats in two columns.
- `.stat-card` uses glassmorphism and hover effects for a modern look.

---

## 💼 Component 4: Portfolio Section

### 1. Script Section (Tabs, Data)

```svelte
<script>
  let activeTab = "skills";
  const techStack = [
    { name: "Python", icon: "🐍", color: "#3776ab" },
    { name: "JavaScript", icon: "JS", color: "#f0db4f" },
    // ...other techs...
  ];
  const projects = [
    {
      title: "Agentic Data Collection System",
      description: "Multi-agent Python system for autonomous web data collection & processing with 95% data quality",
      tech: ["Python", "LangChain", "AutoGen", "CrewAI"],
      image: "🤖",
    },
    // ...other projects...
  ];
</script>
```

**Explanation:**

- `activeTab` controls which tab is shown (skills or projects).
- `techStack` and `projects` arrays hold the data for each tab.

### 2. Markup Section (Tabs, Content)

```svelte
<section id="portfolio" class="portfolio">
  <div class="container">
    <div class="header">
      <h2>Portfolio Showcase</h2>
    </div>
    <div class="tabs">
      <button class="tab" class:active={activeTab === "skills"} on:click={() => (activeTab = "skills")}>Skills</button>
      <button class="tab" class:active={activeTab === "projects"} on:click={() => (activeTab = "projects")}>Projects</button>
    </div>
    <div class="tab-content">
      {#if activeTab === "skills"}
        <div class="tech-grid">
          {#each techStack as tech}
            <div class="tech-card">
              <div class="tech-icon" style="background: {tech.color}20; color: {tech.color}">{tech.icon}</div>
              <p>{tech.name}</p>
            </div>
          {/each}
        </div>
      {:else if activeTab === "projects"}
        <div class="projects-grid">
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
```

**Explanation:**

- Renders tab buttons and switches content based on `activeTab`.
- Skills tab shows a grid of tech cards; Projects tab shows a grid of project cards.

### 3. Styles (Tabs, Grids, Hover)

```css
.tabs {
  display: flex;
  justify-content: center;
  gap: 0.75rem;
  margin-bottom: 1rem;
}
.tab {
  padding: 0.5rem 1.25rem;
  background: rgba(255, 255, 255, 0.05);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 0.75rem;
  color: rgba(255, 255, 255, 0.7);
  cursor: pointer;
  transition: all 0.3s ease;
}
.tab.active {
  background: linear-gradient(90deg, #a855f7, #3b82f6);
  color: white;
  border-color: transparent;
  box-shadow: 0 8px 20px rgba(168, 85, 247, 0.3);
}
.tech-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(120px, 1fr));
  gap: 1rem;
}
.tech-card:hover {
  transform: translateY(-8px);
  background: rgba(255, 255, 255, 0.08);
  box-shadow: 0 10px 30px rgba(168, 85, 247, 0.2);
}
.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
}
.project-card:hover {
  transform: translateY(-5px);
  background: rgba(255, 255, 255, 0.08);
  box-shadow: 0 15px 40px rgba(168, 85, 247, 0.3);
}
```

**Explanation:**

- `.tabs` and `.tab` style the tab buttons.
- `.tech-grid` and `.projects-grid` create responsive layouts for skills and projects.
- Hover effects add interactivity to cards.

---

## 📧 Component 5: Contact Section with Email

### 1. Script Section (EmailJS, State)

```svelte
<script>
  import emailjs from "emailjs-com";
  import { onMount } from "svelte";
  let formData = { name: "", email: "", message: "" };
  let isSubmitting = false;
  let submitMessage = "";
  onMount(() => {
    emailjs.init("YOUR_PUBLIC_KEY_HERE");
  });
  async function handleSubmit(e) {
    e.preventDefault();
    isSubmitting = true;
    submitMessage = "";
    try {
      const result = await emailjs.send(
        "service_portfolio",
        "template_portfolio",
        {
          from_name: formData.name,
          from_email: formData.email,
          message: formData.message,
          to_email: "your-email@example.com",
        }
      );
      if (result.status === 200) {
        submitMessage = "Message sent successfully!";
        formData = { name: "", email: "", message: "" };
        setTimeout(() => { submitMessage = ""; }, 5000);
      }
    } catch (error) {
      submitMessage = "Failed to send message. Please try again.";
      setTimeout(() => { submitMessage = ""; }, 5000);
    } finally {
      isSubmitting = false;
    }
  }
</script>
```

**Explanation:**

- Imports EmailJS and Svelte's `onMount`.
- Initializes EmailJS with your public key.
- Handles form state and async submission with feedback.

### 2. Markup Section (Form, Feedback)

```svelte
<section id="contact" class="contact">
  <div class="container">
    <div class="header">
      <h2>Contact Me</h2>
      <p class="subtitle">Get in touch for any inquiries</p>
    </div>
    <div class="form-section">
      <div class="form-card">
        <h3>Get In Touch</h3>
        <form on:submit={handleSubmit}>
          <div class="form-group">
            <label for="name">Your Name</label>
            <input id="name" type="text" bind:value={formData.name} placeholder="Enter your name" required />
          </div>
          <div class="form-group">
            <label for="email">Email</label>
            <input id="email" type="email" bind:value={formData.email} placeholder="Enter your email" required />
          </div>
          <div class="form-group">
            <label for="message">Message</label>
            <textarea id="message" bind:value={formData.message} placeholder="Enter your message" rows="5" required></textarea>
          </div>
          <button type="submit" class="submit-btn" disabled={isSubmitting}>
            {isSubmitting ? "Sending..." : "Send Message"}
          </button>
          {#if submitMessage}
            <div class="message-feedback">{submitMessage}</div>
          {/if}
        </form>
      </div>
    </div>
  </div>
</section>
```

**Explanation:**

- Renders a contact form with name, email, and message fields.
- Shows feedback message after submission.

### 3. Styles (Form, Feedback)

```css
.form-card {
  background: rgba(255, 255, 255, 0.05);
  backdrop-filter: blur(10px);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 1.5rem;
  padding: 1.2rem;
}
input,
textarea {
  width: 100%;
  padding: 0.8rem 1rem;
  background: rgba(255, 255, 255, 0.05);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 0.75rem;
  color: white;
  font-size: 0.95rem;
  transition: all 0.3s ease;
}
input:focus,
textarea:focus {
  outline: none;
  background: rgba(255, 255, 255, 0.08);
  border-color: #a855f7;
  box-shadow: 0 0 0 3px rgba(168, 85, 247, 0.1);
}
.submit-btn:hover:not(:disabled) {
  transform: translateY(-2px);
  box-shadow: 0 10px 30px rgba(168, 85, 247, 0.4);
}
.submit-btn:disabled {
  opacity: 0.7;
  cursor: not-allowed;
}
.message-feedback {
  margin-top: 1rem;
  padding: 1rem;
  background: rgba(34, 197, 94, 0.1);
  border: 1px solid rgba(34, 197, 94, 0.3);
  border-radius: 0.75rem;
  color: rgba(34, 197, 94, 0.9);
}
```

**Explanation:**

- `.form-card` uses glassmorphism for the form background.
- Inputs and textarea are styled for clarity and focus.
- Feedback message is styled for visibility after submission.

---

## 🚀 Getting Started - Full Checklist

### Step 1: Create project

```bash
mkdir my-svelte-portfolio && cd my-svelte-portfolio
npm init -y
npm install --save-dev svelte vite @sveltejs/vite-plugin-svelte
npm install emailjs-com
```

### Step 2: Create folder structure

```bash
mkdir -p src/lib/components
```

### Step 3: Create all files with code from tutorial

### Step 4: Run development server

```bash
npm run dev
```

Visit: http://localhost:5173

### Step 5: Email setup (optional but recommended)

1. Go to https://www.emailjs.com/
2. Sign up for free account
3. Create email service (connect Gmail)
4. Create email template with variables: `{from_name}`, `{from_email}`, `{message}`
5. Copy Public Key, Service ID, Template ID
6. Paste into Contact.svelte lines 13, 25, 26

### Step 6: Deploy

```bash
npm run build
# Upload `dist/` folder to hosting (Vercel, Netlify, GitHub Pages, etc.)
```

---

## 💡 What You've Learned

✅ Svelte component structure and lifecycle  
✅ CSS animations and keyframes  
✅ Reactive state management with `bind:`  
✅ Conditional rendering with `{#if}`  
✅ Loops with `{#each}`  
✅ Event handling with `on:`  
✅ Glass-morphism UI design  
✅ Gradient backgrounds and text  
✅ Email integration with EmailJS  
✅ Responsive design with CSS Grid and Flexbox

**Congratulations! You've built a professional portfolio! 🎉**
