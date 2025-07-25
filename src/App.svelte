<script>
  import { cubicOut } from "svelte/easing";
  import { fade, fly, scale } from "svelte/transition";
  const advantages = [
    "Truly reactive: no virtual DOM, updates are compiled to efficient JS.",
    "Small bundle size: ships less code to the browser.",
    "Simple syntax: easy to learn and use.",
    "Blazing fast: minimal overhead, great performance.",
    "Great developer experience: built-in transitions, stores, and more.",
  ];
  const links = [
    { name: "Official Website", url: "https://svelte.dev/" },
    { name: "Tutorial", url: "https://svelte.dev/tutorial" },
    { name: "Docs", url: "https://svelte.dev/docs" },
    { name: "REPL", url: "https://svelte.dev/repl" },
    { name: "GitHub", url: "https://github.com/sveltejs/svelte" },
    { name: "Community", url: "https://svelte.dev/community" },
  ];
  const navLinks = [
    { label: "Home", target: "hero" },
    { label: "About", target: "about" },
    { label: "Advantages", target: "advantages" },
    { label: "Get Started", target: "getting-started" },
    { label: "Links", target: "links" },
  ];
  function scrollToSection(id) {
    document.getElementById(id)?.scrollIntoView({ behavior: "smooth" });
  }
  function advFly(i) {
    return { y: 20 + i * 10, duration: 500 + i * 100, easing: cubicOut };
  }
  function linkScale(i) {
    return { duration: 400 + i * 100 };
  }
</script>

<div class="animated-bg">
  <svg
    width="100%"
    height="100%"
    viewBox="0 0 1440 900"
    fill="none"
    xmlns="http://www.w3.org/2000/svg"
    style="position:absolute;top:0;left:0;z-index:0;"
  >
    <defs>
      <linearGradient id="grad1" x1="0" y1="0" x2="1" y2="1">
        <stop offset="0%" stop-color="#ffecd2" />
        <stop offset="100%" stop-color="#ffb300" />
      </linearGradient>
    </defs>
    <ellipse
      cx="1200"
      cy="200"
      rx="320"
      ry="120"
      fill="url(#grad1)"
      opacity="0.18"
    >
      <animate
        attributeName="cx"
        values="1200;900;1200"
        dur="12s"
        repeatCount="indefinite"
      />
    </ellipse>
    <ellipse cx="400" cy="700" rx="340" ry="140" fill="#ff3e00" opacity="0.10">
      <animate
        attributeName="cy"
        values="700;600;700"
        dur="10s"
        repeatCount="indefinite"
      />
    </ellipse>
    <ellipse cx="900" cy="500" rx="180" ry="80" fill="#fff" opacity="0.08">
      <animate
        attributeName="rx"
        values="180;220;180"
        dur="14s"
        repeatCount="indefinite"
      />
    </ellipse>
  </svg>
</div>

<nav class="floating-nav">
  {#each navLinks as nav}
    <a href="javascript:void(0)" on:click={() => scrollToSection(nav.target)}
      >{nav.label}</a
    >
  {/each}
</nav>

<main>
  <section
    id="hero"
    class="hero glass-card"
    in:fly={{ y: -40, duration: 700, easing: cubicOut }}
  >
    <img
      src="/favicon.png"
      alt="Svelte Logo"
      class="logo floating"
      in:scale={{ duration: 700, start: 0.5 }}
    />
    <h1 in:fade={{ duration: 800 }}>Svelte<span>JS</span></h1>
    <p class="subtitle" in:fade={{ duration: 900 }}>
      Cybernetically enhanced web apps
    </p>
    <a
      class="cta ripple"
      href="https://svelte.dev/tutorial"
      target="_blank"
      rel="noopener"
      in:fly={{ y: 20, duration: 800 }}>Get Started</a
    >
  </section>

  <section
    id="about"
    class="about glass-card"
    in:fly={{ x: -60, duration: 700, easing: cubicOut }}
  >
    <h2 in:fade>What is Svelte?</h2>
    <p in:fade={{ duration: 700 }}>
      <strong>Svelte</strong> is a cutting-edge JavaScript framework for building
      lightning-fast, highly interactive user interfaces. Unlike traditional frameworks,
      Svelte compiles your code to tiny, framework-less JavaScript at build time,
      resulting in apps that load faster and feel more responsive. With Svelte, you
      write less code and get more done, all while enjoying a delightful developer
      experience.
    </p>
  </section>

  <section
    id="advantages"
    class="advantages glass-card"
    in:fly={{ x: 60, duration: 700, easing: cubicOut }}
  >
    <h2 in:fade>Why Choose Svelte?</h2>
    <ul>
      {#each advantages as adv, i}
        <li in:fly={{ ...advFly(i) }}>
          <span class="adv-icon floating" in:scale={{ duration: 400 }}>🔥</span>
          {adv}
        </li>
      {/each}
    </ul>
  </section>

  <section
    id="getting-started"
    class="getting-started glass-card"
    in:fly={{ y: 60, duration: 700, easing: cubicOut }}
  >
    <h2 in:fade>Getting Started</h2>
    <ol>
      <li in:fade={{ duration: 600 }}>
        Explore the <a
          href="https://svelte.dev/tutorial"
          target="_blank"
          rel="noopener">interactive tutorial</a
        > and see Svelte in action.
      </li>
      <li in:fade={{ duration: 700 }}>
        Create a new project instantly: <code
          >npm create vite@latest my-svelte-app -- --template svelte</code
        >
      </li>
      <li in:fade={{ duration: 800 }}>
        Dive into the <a
          href="https://svelte.dev/docs"
          target="_blank"
          rel="noopener">official documentation</a
        > for advanced features and tips.
      </li>
    </ol>
  </section>

  <section
    id="links"
    class="links glass-card"
    in:fly={{ y: 80, duration: 700, easing: cubicOut }}
  >
    <h2 in:fade>Useful Links</h2>
    <ul>
      {#each links as link, i}
        <li in:scale={{ ...linkScale(i) }}>
          <a href={link.url} target="_blank" rel="noopener">{link.name}</a>
        </li>
      {/each}
    </ul>
  </section>
</main>

<style>
  .animated-bg {
    z-index: 0;
  }
  .floating-nav {
    font-family: "Montserrat", "Roboto", sans-serif;
    font-size: 1.08rem;
    font-weight: 700;
    letter-spacing: 0.5px;
    box-shadow: 0 2px 16px 0 #ffb30033;
    backdrop-filter: blur(12px);
    -webkit-backdrop-filter: blur(12px);
    border: 1.5px solid rgba(255, 255, 255, 0.18);
    animation: navFadeIn 1.2s cubic-bezier(0.4, 0, 0.2, 1);
  }
  .floating-nav a {
    color: var(--color-primary);
    padding: 0.4em 1.2em;
    border-radius: 1.2em;
    transition:
      background 0.2s,
      color 0.2s,
      transform 0.2s;
    text-decoration: none;
    position: relative;
  }
  .floating-nav a:hover {
    background: var(--color-primary);
    color: #fff;
    transform: scale(1.08);
  }
  .floating-nav a:active {
    background: var(--color-secondary);
    color: #fff;
  }
  .glass-card {
    background: var(--color-glass);
    border-radius: var(--radius);
    box-shadow: var(--shadow);
    backdrop-filter: blur(var(--blur));
    -webkit-backdrop-filter: blur(var(--blur));
    border: 1.5px solid rgba(255, 255, 255, 0.25);
  }
  .floating {
    animation: float 3.5s ease-in-out infinite alternate;
  }
  @keyframes float {
    0% {
      transform: translateY(0);
    }
    100% {
      transform: translateY(-16px) scale(1.04);
    }
  }
  .ripple {
    position: relative;
    overflow: hidden;
  }
  .ripple:after {
    content: "";
    position: absolute;
    left: 50%;
    top: 50%;
    width: 0;
    height: 0;
    background: rgba(255, 179, 0, 0.18);
    border-radius: 100%;
    transform: translate(-50%, -50%);
    transition:
      width 0.4s cubic-bezier(0.4, 0, 0.2, 1),
      height 0.4s cubic-bezier(0.4, 0, 0.2, 1);
    pointer-events: none;
  }
  .ripple:active:after {
    width: 220px;
    height: 220px;
  }
  main {
    font-family: "Montserrat", "Roboto", sans-serif;
    color: var(--color-text);
    background: transparent;
    max-width: 900px;
    margin: 3.5rem auto 2.5rem auto;
    padding: 2rem 1.5rem 3rem 1.5rem;
    position: relative;
    z-index: 1;
  }
  .hero {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 0.5rem;
    margin-bottom: 2.5rem;
    padding: 3.2rem 1.5rem 2.2rem 1.5rem;
    position: relative;
    overflow: hidden;
    animation: heroGlow 3s ease-in-out infinite alternate;
  }
  @keyframes heroGlow {
    0% {
      box-shadow: 0 4px 32px 0 rgba(255, 62, 0, 0.08);
    }
    100% {
      box-shadow: 0 8px 48px 0 rgba(255, 179, 0, 0.18);
    }
  }
  .logo {
    width: 100px;
    height: 100px;
    margin-bottom: 0.5rem;
    filter: drop-shadow(0 2px 12px #ffb30044);
    transition: transform 0.3s;
  }
  .logo:hover {
    transform: rotate(-8deg) scale(1.08);
  }
  h1 {
    font-size: 3.4rem;
    font-weight: 800;
    color: var(--color-primary);
    margin: 0;
    letter-spacing: -2px;
    text-shadow: 0 2px 8px #ffb30022;
    transition: color 0.3s;
  }
  h1 span {
    color: var(--color-text);
    font-weight: 300;
  }
  .subtitle {
    font-size: 1.3rem;
    color: #666;
    margin-bottom: 1.2rem;
    font-family: "Roboto", sans-serif;
    letter-spacing: 0.5px;
  }
  .cta {
    display: inline-block;
    background: linear-gradient(
      90deg,
      var(--color-primary) 60%,
      var(--color-secondary) 100%
    );
    color: #fff;
    padding: 0.95em 2.4em;
    border-radius: 2em;
    font-size: 1.18rem;
    font-weight: 700;
    text-decoration: none;
    box-shadow: 0 2px 12px 0 rgba(255, 62, 0, 0.12);
    transition:
      background 0.2s,
      transform 0.2s,
      box-shadow 0.2s;
    margin-top: 0.7rem;
    letter-spacing: 1px;
  }
  .cta:hover {
    background: linear-gradient(
      90deg,
      var(--color-secondary) 0%,
      var(--color-primary) 100%
    );
    transform: translateY(-2px) scale(1.06);
    box-shadow: 0 6px 24px 0 rgba(255, 179, 0, 0.18);
  }
  .card {
    background: var(--color-surface);
    border-radius: var(--radius);
    box-shadow: var(--shadow);
    padding: 2rem 1.5rem 1.5rem 1.5rem;
    margin-bottom: 2.5rem;
    position: relative;
    animation: cardPop 1.2s cubic-bezier(0.4, 0, 0.2, 1);
  }
  @keyframes cardPop {
    0% {
      transform: scale(0.97) translateY(30px);
      opacity: 0.2;
    }
    100% {
      transform: scale(1) translateY(0);
      opacity: 1;
    }
  }
  h2 {
    color: var(--color-primary);
    font-size: 2.2rem;
    margin-bottom: 0.7rem;
    font-weight: 700;
    letter-spacing: -1px;
    text-shadow: 0 1px 4px #ffb30011;
  }
  .about p {
    font-size: 1.22rem;
    line-height: 1.85;
    color: #333;
    font-family: "Roboto", sans-serif;
    margin-bottom: 0.2rem;
  }
  .advantages ul {
    list-style: none;
    padding-left: 0;
    margin: 0;
  }
  .advantages li {
    display: flex;
    align-items: center;
    margin-bottom: 0.7em;
    font-size: 1.18rem;
    font-weight: 500;
    background: linear-gradient(90deg, #fff7f0 60%, #ffe0c3 100%);
    border-radius: 1em;
    padding: 0.5em 1em;
    box-shadow: 0 1px 6px 0 #ffb30011;
    transition:
      transform 0.2s,
      box-shadow 0.2s;
  }
  .advantages li:hover {
    transform: scale(1.03) translateX(6px);
    box-shadow: 0 4px 16px 0 #ffb30033;
  }
  .adv-icon {
    font-size: 1.4em;
    margin-right: 0.7em;
    animation: flame 1.5s infinite alternate;
  }
  @keyframes flame {
    0% {
      filter: drop-shadow(0 0 0 #ffb300);
    }
    100% {
      filter: drop-shadow(0 0 8px #ffb300);
    }
  }
  .getting-started ol {
    padding-left: 1.2em;
  }
  .getting-started li {
    margin-bottom: 0.7em;
    font-size: 1.13rem;
    font-family: "Roboto", sans-serif;
    background: #fff8f3;
    border-radius: 0.7em;
    padding: 0.5em 1em;
    box-shadow: 0 1px 6px 0 #ffb30011;
    transition: box-shadow 0.2s;
  }
  .getting-started li:hover {
    box-shadow: 0 4px 16px 0 #ffb30033;
  }
  .getting-started code {
    background: #ffe0c3;
    padding: 0.2em 0.5em;
    border-radius: 0.4em;
    font-size: 0.98em;
    font-family: "Roboto Mono", monospace;
    color: var(--color-primary);
  }
  .links ul {
    list-style: none;
    padding: 0;
    display: flex;
    flex-wrap: wrap;
    gap: 1.2em;
    margin: 0;
  }
  .links li {
    margin: 0;
    transition: transform 0.2s;
  }
  .links a {
    color: var(--color-primary);
    font-weight: 700;
    font-size: 1.08rem;
    padding: 0.4em 1.1em;
    border-radius: 1.2em;
    background: #fff7f0;
    box-shadow: 0 1px 6px 0 #ffb30011;
    transition:
      color 0.2s,
      background 0.2s,
      box-shadow 0.2s,
      transform 0.2s;
    display: inline-block;
  }
  .links a:hover {
    color: #fff;
    background: linear-gradient(
      90deg,
      var(--color-primary) 60%,
      var(--color-secondary) 100%
    );
    box-shadow: 0 4px 16px 0 #ffb30033;
    transform: scale(1.07);
  }
  @media (max-width: 600px) {
    main {
      padding: 1rem 0.5rem 2rem 0.5rem;
    }
    h1 {
      font-size: 2.1rem;
    }
    h2 {
      font-size: 1.3rem;
    }
    .logo {
      width: 56px;
      height: 56px;
    }
    .card,
    .hero {
      padding: 1.2rem 0.7rem 1.2rem 0.7rem;
    }
    .floating-nav {
      font-size: 0.98rem;
      gap: 1em;
      padding: 0.4em 1em;
    }
  }
</style>
