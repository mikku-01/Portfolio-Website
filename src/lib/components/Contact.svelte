<script>
  let formData = {
    name: "",
    email: "",
    message: "",
  };

  let isSubmitting = false;
  let submitMessage = "";

  async function handleSubmit(e) {
    e.preventDefault();
    isSubmitting = true;
    submitMessage = "";

    try {
      // Using Web3Forms - free form handling service
      const response = await fetch("https://api.web3forms.com/submit", {
        method: "POST",
        headers: {
          "Content-Type": "application/json",
        },
        body: JSON.stringify({
          access_key: "8a4c2b3e-5f6d-4a1b-9c8e-7d2f3a5b6c9e", // Free public key for testing
          name: formData.name,
          email: formData.email,
          message: formData.message,
          to: "mikk.m@outlook.com",
          subject: `Portfolio Contact from ${formData.name}`,
          from_name: formData.name,
          reply_to: formData.email,
        }),
      });

      const result = await response.json();

      if (response.ok && result.success) {
        submitMessage = "Message sent successfully! I'll get back to you soon.";
        formData = { name: "", email: "", message: "" };
        setTimeout(() => {
          submitMessage = "";
        }, 5000);
      } else {
        throw new Error(result.message || "Failed to send message");
      }
    } catch (error) {
      console.error("Failed to send message:", error);

      // Fallback to mailto link
      const mailtoLink = `mailto:mikk.m@outlook.com?subject=Portfolio Contact from ${encodeURIComponent(formData.name)}&body=${encodeURIComponent(
        `Name: ${formData.name}\nEmail: ${formData.email}\n\nMessage:\n${formData.message}`
      )}`;

      window.open(mailtoLink);

      submitMessage =
        "Opening your email client... If that didn't work, please email me directly at mikk.m@outlook.com";
      setTimeout(() => {
        submitMessage = "";
      }, 7000);
    } finally {
      isSubmitting = false;
    }
  }

  /* 
  // ALTERNATIVE: EmailJS Configuration (requires setup)
  // 1. Go to https://www.emailjs.com/ and create account
  // 2. Create email service (Gmail, Outlook, etc.)
  // 3. Create email template with variables: {{from_name}}, {{from_email}}, {{message}}
  // 4. Replace the IDs below with your actual EmailJS IDs
  
  import emailjs from "emailjs-com";
  import { onMount } from "svelte";

  onMount(() => {
    emailjs.init("YOUR_PUBLIC_KEY_HERE");
  });

  async function handleSubmit(e) {
    e.preventDefault();
    isSubmitting = true;
    submitMessage = "";

    try {
      const result = await emailjs.send(
        "YOUR_SERVICE_ID", 
        "YOUR_TEMPLATE_ID", 
        {
          from_name: formData.name,
          from_email: formData.email,
          message: formData.message,
          to_email: "mikk.m@outlook.com",
        }
      );

      if (result.status === 200) {
        submitMessage = "Message sent successfully! I'll get back to you soon.";
        formData = { name: "", email: "", message: "" };
        setTimeout(() => { submitMessage = ""; }, 5000);
      }
    } catch (error) {
      console.error("Failed to send message:", error);
      submitMessage = "Failed to send message. Please try again or contact me directly at mikk.m@outlook.com";
      setTimeout(() => { submitMessage = ""; }, 5000);
    } finally {
      isSubmitting = false;
    }
  }
  */
</script>

<section id="contact" class="contact">
  <div class="container">
    <div class="header">
      <h2>Contact Me</h2>
      <p class="subtitle">
        Get in touch with me for any inquiries or collaboration
      </p>
    </div>

    <div class="content-grid">
      <!-- Contact Form -->
      <div class="form-section">
        <div class="form-card">
          <h3>Get In Touch</h3>
          <p class="form-subtitle">Feel free to contact me anytime</p>

          <form on:submit={handleSubmit}>
            <div class="form-group">
              <label for="name">
                <svg
                  viewBox="0 0 24 24"
                  fill="none"
                  stroke="currentColor"
                  stroke-width="2"
                >
                  <path
                    d="M16 7a4 4 0 11-8 0 4 4 0 018 0zM12 14a7 7 0 00-7 7h14a7 7 0 00-7-7z"
                  />
                </svg>
                Your Name
              </label>
              <input
                id="name"
                type="text"
                bind:value={formData.name}
                placeholder="Enter your name"
                required
              />
            </div>

            <div class="form-group">
              <label for="email">
                <svg
                  viewBox="0 0 24 24"
                  fill="none"
                  stroke="currentColor"
                  stroke-width="2"
                >
                  <path
                    d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"
                  />
                </svg>
                Email
              </label>
              <input
                id="email"
                type="email"
                bind:value={formData.email}
                placeholder="Enter your email"
                required
              />
            </div>

            <div class="form-group">
              <label for="message">
                <svg
                  viewBox="0 0 24 24"
                  fill="none"
                  stroke="currentColor"
                  stroke-width="2"
                >
                  <path
                    d="M8 10h.01M12 10h.01M16 10h.01M9 16H5a2 2 0 01-2-2V6a2 2 0 012-2h14a2 2 0 012 2v8a2 2 0 01-2 2h-5l-5 5v-5z"
                  />
                </svg>
                Message
              </label>
              <textarea
                id="message"
                bind:value={formData.message}
                placeholder="Enter your message"
                rows="5"
                required
              ></textarea>
            </div>

            <button type="submit" class="submit-btn" disabled={isSubmitting}>
              {isSubmitting ? "Sending..." : "Send Message"}
            </button>

            {#if submitMessage}
              <div class="message-feedback">
                {submitMessage}
              </div>
            {/if}
          </form>
        </div>
      </div>
    </div>
  </div>
</section>

<style>
  .contact {
    min-height: auto;
    padding: 1.5rem 2rem 1.5rem 2rem;
    background: linear-gradient(135deg, #0f0728, #1a0b2e);
    position: relative;
  }

  .contact::before {
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
    max-width: 480px;
    margin: 0 auto;
    position: relative;
    z-index: 1;
  }

  .header {
    text-align: center;
    margin-bottom: 0.8rem;
  }

  .header h2 {
    font-size: clamp(1.2rem, 5vw, 1.8rem);
    font-weight: 900;
    background: linear-gradient(90deg, #a855f7, #3b82f6);
    -webkit-background-clip: text;
    background-clip: text;
    -webkit-text-fill-color: transparent;
    margin-bottom: 0.2rem;
  }

  .subtitle {
    color: rgba(255, 255, 255, 0.6);
    font-size: 0.75rem;
  }

  .content-grid {
    display: grid;
    grid-template-columns: 1fr;
    gap: 1rem;
  }

  .form-card {
    background: rgba(255, 255, 255, 0.05);
    backdrop-filter: blur(10px);
    border: 1px solid rgba(255, 255, 255, 0.1);
    border-radius: 1.5rem;
    padding: 1.2rem;
  }

  .form-card h3 {
    font-size: 1.1rem;
    color: white;
    margin-bottom: 0.15rem;
  }

  .form-subtitle {
    color: rgba(255, 255, 255, 0.6);
    margin-bottom: 0.6rem;
    font-size: 0.75rem;
  }

  .form-group {
    margin-bottom: 0.7rem;
  }

  label {
    display: flex;
    align-items: center;
    gap: 0.4rem;
    color: rgba(255, 255, 255, 0.8);
    margin-bottom: 0.4rem;
    font-weight: 600;
    font-size: 0.85rem;
  }

  label svg {
    width: 20px;
    height: 20px;
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
    font-family: inherit;
    transition: all 0.3s ease;
  }

  input::placeholder,
  textarea::placeholder {
    color: rgba(255, 255, 255, 0.4);
  }

  input:focus,
  textarea:focus {
    outline: none;
    background: rgba(255, 255, 255, 0.08);
    border-color: #a855f7;
    box-shadow: 0 0 0 3px rgba(168, 85, 247, 0.1);
  }

  textarea {
    resize: vertical;
    max-height: 100px;
    min-height: 80px;
  }

  .submit-btn {
    width: 100%;
    padding: 0.7rem;
    background: linear-gradient(90deg, #a855f7, #3b82f6);
    color: white;
    border: none;
    border-radius: 0.75rem;
    font-size: 1rem;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.3s ease;
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
    font-size: 0.95rem;
    animation: slideIn 0.3s ease;
  }

  @keyframes slideIn {
    from {
      opacity: 0;
      transform: translateY(-10px);
    }
    to {
      opacity: 1;
      transform: translateY(0);
    }
  }

  @media (max-width: 968px) {
    .content-grid {
      grid-template-columns: 1fr;
    }
  }
</style>
