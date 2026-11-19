<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <meta
    name="description"
    content="Make laundry day easier with SpinClub. Choose a monthly laundry membership for self-service, wash and fold, or pickup and delivery."
  />
  <meta name="theme-color" content="#f6f7f1" />
  <title>SpinClub — Laundry, on your terms</title>
  <style>
    :root {
      --ink: #17362d;
      --muted: #64746d;
      --green: #17684f;
      --green-dark: #10513d;
      --mint: #dceee4;
      --lime: #d6ef79;
      --cream: #f6f7f1;
      --white: #fff;
      --coral: #ff8369;
      --line: #e2e8df;
      --shadow: 0 20px 60px rgba(23, 54, 45, .09);
      --radius: 24px;
    }

    * { box-sizing: border-box; }
    html { scroll-behavior: smooth; }
    body {
      margin: 0;
      background: var(--cream);
      color: var(--ink);
      font-family: Inter, ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
      line-height: 1.6;
    }
    a { color: inherit; text-decoration: none; }
    button, input, select { font: inherit; }
    button, a { -webkit-tap-highlight-color: transparent; }
    .container { width: min(1160px, calc(100% - 40px)); margin: 0 auto; }
    .section { padding: 94px 0; }
    .eyebrow {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      color: var(--green);
      font-size: .77rem;
      font-weight: 800;
      letter-spacing: .12em;
      text-transform: uppercase;
    }
    .eyebrow::before {
      content: "";
      width: 8px;
      height: 8px;
      border-radius: 50%;
      background: var(--coral);
    }
    h1, h2, h3, p { margin-top: 0; }
    h1, h2, h3 { letter-spacing: -.045em; }
    h1 { font-size: clamp(3rem, 7vw, 5.6rem); line-height: .98; margin: 18px 0; }
    h2 { font-size: clamp(2.2rem, 4vw, 3.5rem); line-height: 1.05; margin: 12px 0 18px; }
    h3 { font-size: 1.3rem; margin-bottom: 8px; }
    p { color: var(--muted); }
    .btn {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 9px;
      min-height: 50px;
      padding: 0 22px;
      border: 0;
      border-radius: 999px;
      background: var(--green);
      color: var(--white);
      font-weight: 750;
      cursor: pointer;
      transition: transform .18s ease, background .18s ease;
    }
    .btn:hover { background: var(--green-dark); transform: translateY(-2px); }
    .btn-light { background: var(--white); color: var(--ink); }
    .btn-light:hover { background: var(--lime); color: var(--ink); }
    .btn-outline { background: transparent; border: 1px solid var(--line); color: var(--ink); }
    .btn-outline:hover { background: var(--white); }
    .text-link { color: var(--green); font-weight: 750; }
    .text-link:hover { text-decoration: underline; }

    /* Navigation */
    .site-header {
      position: sticky;
      top: 0;
      z-index: 20;
      background: rgba(246, 247, 241, .92);
      border-bottom: 1px solid rgba(23, 54, 45, .08);
      backdrop-filter: blur(14px);
    }
    .nav { min-height: 76px; display: flex; align-items: center; justify-content: space-between; gap: 24px; }
    .brand { display: inline-flex; align-items: center; gap: 10px; font-size: 1.45rem; font-weight: 900; letter-spacing: -.06em; }
    .brand-mark {
      display: grid;
      place-items: center;
      width: 36px;
      height: 36px;
      background: var(--lime);
      border-radius: 50%;
      font-size: 1.1rem;
    }
    .nav-links { display: flex; align-items: center; gap: 27px; color: var(--muted); font-size: .92rem; font-weight: 650; }
    .nav-links a:hover { color: var(--green); }
    .nav-join { min-height: 42px; padding: 0 18px; }
    .menu-toggle {
      display: none;
      width: 44px;
      height: 44px;
      border: 1px solid var(--line);
      border-radius: 13px;
      background: var(--white);
      color: var(--ink);
      font-size: 1.3rem;
      cursor: pointer;
    }

    /* Hero */
    .hero { padding: 72px 0 62px; overflow: hidden; }
    .hero-grid { display: grid; grid-template-columns: 1.02fr .98fr; align-items: center; gap: 54px; }
    .hero-copy > p { max-width: 520px; font-size: 1.1rem; margin-bottom: 26px; }
    .hero-actions { display: flex; gap: 12px; flex-wrap: wrap; }
    .hero-note { display: flex; align-items: center; gap: 10px; margin-top: 22px; color: var(--muted); font-size: .9rem; }
    .avatar-stack { display: flex; }
    .avatar-stack i {
      display: grid; place-items: center; width: 29px; height: 29px; margin-left: -6px;
      border: 2px solid var(--cream); border-radius: 50%; background: var(--mint); color: var(--green);
      font-style: normal; font-size: .7rem; font-weight: 800;
    }
    .avatar-stack i:first-child { margin-left: 0; background: #ffe0d8; }
    .hero-art {
      min-height: 440px;
      position: relative;
      display: grid;
      place-items: center;
      border-radius: 42% 58% 55% 45% / 49% 44% 56% 51%;
      background: var(--mint);
    }
    .hero-art::before {
      content: "";
      position: absolute;
      inset: 30px;
      border: 1px dashed rgba(23, 104, 79, .22);
      border-radius: inherit;
      transform: rotate(-8deg);
    }
    .washer {
      position: relative;
      z-index: 1;
      width: min(300px, 72%);
      aspect-ratio: .79;
      border: 10px solid #fff;
      border-radius: 30px;
      background: linear-gradient(145deg, #f8faf5, #e8eee6);
      box-shadow: 0 28px 45px rgba(23, 54, 45, .16);
      transform: rotate(4deg);
    }
    .washer-top { height: 28%; padding: 23px 20px; border-bottom: 1px solid #dfe7df; }
    .washer-brand { color: var(--green); font-size: .7rem; font-weight: 900; letter-spacing: .12em; }
    .washer-dial { width: 34px; height: 34px; border: 4px solid #c7d4ca; border-radius: 50%; margin-top: 9px; }
    .washer-door {
      position: absolute;
      width: 64%;
      aspect-ratio: 1;
      left: 18%;
      bottom: 11%;
      display: grid;
      place-items: center;
      border: 12px solid #d5dfd5;
      border-radius: 50%;
      background: radial-gradient(circle at 38% 30%, #fff 0 7%, #b8ded0 8% 44%, #79b99e 45% 68%, #427e67 69%);
      box-shadow: inset 0 0 0 7px rgba(255,255,255,.55);
    }
    .floating-card {
      position: absolute;
      z-index: 2;
      background: var(--white);
      border-radius: 17px;
      padding: 14px 17px;
      box-shadow: var(--shadow);
      font-size: .86rem;
    }
    .floating-card strong { display: block; font-size: 1rem; }
    .floating-card small { color: var(--muted); }
    .card-one { left: -12px; bottom: 48px; }
    .card-two { top: 44px; right: -14px; transform: rotate(4deg); }
    .sparkle { position: absolute; color: var(--coral); font-size: 2rem; }
    .sparkle-a { top: 40px; left: 15%; }
    .sparkle-b { right: 12%; bottom: 62px; font-size: 1.3rem; }

    /* Value strip */
    .benefit-strip { padding: 24px 0; background: var(--ink); color: var(--white); }
    .benefit-row { display: grid; grid-template-columns: repeat(3, 1fr); gap: 24px; }
    .benefit { display: flex; align-items: center; justify-content: center; gap: 12px; font-weight: 700; }
    .benefit span:first-child { color: var(--lime); font-size: 1.3rem; }

    /* Shared cards and section headings */
    .section-head { max-width: 650px; margin-bottom: 38px; }
    .section-head p { max-width: 570px; }
    .center { margin-left: auto; margin-right: auto; text-align: center; }
    .center .eyebrow { justify-content: center; }
    .services-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 18px; }
    .service-card {
      min-height: 260px;
      padding: 28px;
      border: 1px solid var(--line);
      border-radius: var(--radius);
      background: var(--white);
      box-shadow: 0 9px 28px rgba(23, 54, 45, .035);
    }
    .service-icon {
      display: grid; place-items: center; width: 52px; height: 52px; margin-bottom: 25px;
      border-radius: 17px; background: var(--mint); font-size: 1.5rem;
    }
    .service-card:nth-child(2) .service-icon { background: #fff0d6; }
    .service-card:nth-child(3) .service-icon { background: #ffe3dc; }

    /* Memberships */
    .membership { background: #edf2e9; }
    .plans { display: grid; grid-template-columns: repeat(4, 1fr); gap: 15px; align-items: stretch; }
    .plan {
      position: relative; display: flex; flex-direction: column; padding: 25px 22px;
      background: var(--white); border: 1px solid var(--line); border-radius: 22px;
    }
    .plan.popular { border: 2px solid var(--green); box-shadow: var(--shadow); }
    .popular-label {
      position: absolute; top: -13px; left: 20px; padding: 4px 11px; border-radius: 99px;
      background: var(--lime); color: var(--ink); font-size: .72rem; font-weight: 850;
    }
    .plan h3 { margin: 4px 0; }
    .plan-for { min-height: 42px; color: var(--muted); font-size: .86rem; }
    .price { margin: 15px 0 3px; font-size: 2.45rem; font-weight: 900; letter-spacing: -.07em; }
    .price small { color: var(--muted); font-size: .88rem; font-weight: 600; letter-spacing: 0; }
    .plan-detail { color: var(--green); font-size: .87rem; font-weight: 750; }
    .plan ul { padding: 15px 0 20px; margin: 15px 0 20px; list-style: none; border-top: 1px solid var(--line); }
    .plan li { position: relative; padding: 7px 0 7px 23px; color: var(--muted); font-size: .88rem; }
    .plan li::before { content: "✓"; position: absolute; left: 0; color: var(--green); font-weight: 900; }
    .plan .btn { width: 100%; margin-top: auto; padding: 0 12px; font-size: .9rem; }
    .pricing-note { margin: 22px 0 0; text-align: center; font-size: .82rem; }

    /* How it works */
    .steps { display: grid; grid-template-columns: repeat(3, 1fr); gap: 30px; counter-reset: step; }
    .step { position: relative; padding-top: 18px; }
    .step-number {
      display: grid; place-items: center; width: 49px; height: 49px; margin-bottom: 18px;
      border-radius: 50%; background: var(--lime); color: var(--ink); font-weight: 900;
    }
    .step:not(:last-child)::after {
      content: ""; position: absolute; top: 42px; left: 68px; width: calc(100% - 40px);
      border-top: 1px dashed #b6c6b8;
    }

    /* Feature band */
    .fold-band { padding: 0 0 94px; }
    .fold-card {
      display: grid; grid-template-columns: 1.1fr .9fr; gap: 30px; align-items: center;
      padding: 48px; border-radius: 32px; background: var(--green); color: var(--white); overflow: hidden;
    }
    .fold-card h2 { max-width: 520px; }
    .fold-card p { color: rgba(255,255,255,.78); max-width: 500px; }
    .fold-card .eyebrow { color: var(--lime); }
    .fold-card .eyebrow::before { background: var(--coral); }
    .fold-visual {
      min-height: 210px; display: grid; place-items: center; position: relative;
      border-radius: 25px; background: rgba(255,255,255,.1);
    }
    .laundry-basket {
      width: 180px; height: 128px; position: relative; border-radius: 14px 14px 30px 30px;
      background: var(--lime); transform: rotate(-5deg);
    }
    .laundry-basket::before {
      content: ""; position: absolute; width: 116px; height: 60px; left: 32px; top: -37px;
      border-radius: 50% 50% 0 0; background: #f9f7ed;
      box-shadow: -24px 10px 0 -5px #ffb9a7, 23px 7px 0 -7px #b5d8c6;
    }
    .fold-visual::after { content: "FRESH + FOLDED"; position: absolute; bottom: 19px; color: var(--white); font-size: .68rem; font-weight: 850; letter-spacing: .16em; }

    /* FAQ and location */
    .faq-layout { display: grid; grid-template-columns: .75fr 1.25fr; gap: 60px; }
    .faq-list details { border-bottom: 1px solid var(--line); }
    .faq-list summary {
      position: relative; padding: 19px 36px 19px 0; cursor: pointer; list-style: none; font-weight: 750;
    }
    .faq-list summary::-webkit-details-marker { display: none; }
    .faq-list summary::after { content: "+"; position: absolute; right: 5px; top: 14px; color: var(--green); font-size: 1.4rem; }
    .faq-list details[open] summary::after { content: "−"; }
    .faq-list details p { padding-right: 35px; margin: 0 0 19px; }
    .location { background: #edf2e9; }
    .location-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 30px; align-items: stretch; }
    .location-card, .hours-card { padding: 30px; border-radius: var(--radius); background: var(--white); }
    .map-placeholder {
      min-height: 250px; display: grid; place-items: center; margin-top: 20px; border-radius: 18px;
      background:
        linear-gradient(30deg, transparent 47%, rgba(23,104,79,.12) 48% 51%, transparent 52%),
        linear-gradient(120deg, transparent 47%, rgba(23,104,79,.12) 48% 51%, transparent 52%),
        #e6eee2;
      color: var(--green); font-weight: 800; text-align: center;
    }
    .hours-row { display: flex; justify-content: space-between; gap: 20px; padding: 12px 0; border-bottom: 1px solid var(--line); }
    .hours-row:last-child { border-bottom: 0; }

    /* Signup */
    .signup { background: var(--lime); }
    .signup-grid { display: grid; grid-template-columns: 1fr .85fr; gap: 45px; align-items: center; }
    .signup p { max-width: 520px; }
    .signup-form { padding: 26px; border-radius: 22px; background: var(--white); box-shadow: var(--shadow); }
    .form-row { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; }
    .signup-form label { display: block; margin: 0 0 6px; color: var(--ink); font-size: .82rem; font-weight: 750; }
    .signup-form input, .signup-form select {
      width: 100%; min-height: 48px; margin-bottom: 14px; padding: 0 13px;
      border: 1px solid var(--line); border-radius: 11px; background: #fbfcf9; color: var(--ink);
    }
    .signup-form .btn { width: 100%; }
    .form-message { margin: 12px 0 0; font-size: .85rem; }
    .form-message.error { color: #b13628; }
    .form-message.success { color: var(--green); font-weight: 700; }

    /* Footer */
    footer { padding: 30px 0; background: var(--ink); color: var(--white); }
    .footer-row { display: flex; align-items: center; justify-content: space-between; gap: 20px; flex-wrap: wrap; }
    footer .brand-mark { color: var(--ink); }
    footer p { margin: 0; color: rgba(255,255,255,.65); font-size: .88rem; }
    .footer-links { display: flex; gap: 18px; color: rgba(255,255,255,.75); font-size: .88rem; }
    .footer-links a:hover { color: var(--lime); }

    @media (max-width: 950px) {
      .nav-links { gap: 16px; }
      .plans { grid-template-columns: repeat(2, 1fr); gap: 20px; }
      .hero-grid { gap: 28px; }
      .hero-art { min-height: 380px; }
    }
    @media (max-width: 740px) {
      .section { padding: 72px 0; }
      .menu-toggle { display: block; }
      .nav-links {
        display: none; position: absolute; top: 68px; left: 20px; right: 20px;
        padding: 18px; border: 1px solid var(--line); border-radius: 18px;
        background: var(--white); box-shadow: var(--shadow); flex-direction: column; align-items: stretch;
      }
      .nav-links.open { display: flex; }
      .nav-links a { padding: 7px 4px; }
      .nav-links .nav-join { align-self: stretch; }
      .hero { padding-top: 48px; }
      .hero-grid, .fold-card, .faq-layout, .location-grid, .signup-grid { grid-template-columns: 1fr; }
      .hero-art { min-height: 360px; margin: 10px 15px 0; }
      .benefit-row { grid-template-columns: 1fr; gap: 14px; }
      .benefit { justify-content: flex-start; }
      .services-grid { grid-template-columns: 1fr; }
      .service-card { min-height: 0; }
      .steps { grid-template-columns: 1fr; gap: 20px; }
      .step:not(:last-child)::after { display: none; }
      .fold-card { padding: 30px 24px; }
      .faq-layout { gap: 22px; }
      .signup-grid { gap: 15px; }
    }
    @media (max-width: 500px) {
      .container { width: min(100% - 30px, 1160px); }
      .plans { grid-template-columns: 1fr; }
      .form-row { grid-template-columns: 1fr; gap: 0; }
      .hero-actions .btn { width: 100%; }
      .hero-art { min-height: 310px; }
      .floating-card { padding: 11px 13px; }
      .card-one { left: -8px; bottom: 24px; }
      .card-two { right: -10px; top: 25px; }
      .footer-row { align-items: flex-start; flex-direction: column; }
    }
    @media (prefers-reduced-motion: reduce) {
      html { scroll-behavior: auto; }
      *, *::before, *::after { transition-duration: .01ms !important; }
    }
  </style>
</head>
<body>
  <header class="site-header">
    <div class="container nav">
      <a class="brand" href="#home" aria-label="SpinClub home">
        <span class="brand-mark" aria-hidden="true">↻</span> SpinClub
      </a>
      <button class="menu-toggle" aria-label="Toggle navigation" aria-expanded="false">☰</button>
      <nav class="nav-links" aria-label="Main navigation">
        <a href="#services">Services</a>
        <a href="#memberships">Memberships</a>
        <a href="#how-it-works">How it works</a>
        <a href="#faq">FAQs</a>
        <a href="#location">Location</a>
        <a class="btn nav-join" href="#join">Join SpinClub <span aria-hidden="true">↗</span></a>
      </nav>
    </div>
  </header>

  <main>
    <section class="hero" id="home">
      <div class="container hero-grid">
        <div class="hero-copy">
          <span class="eyebrow">Laundry day, made lighter</span>
          <h1>More life.<br />Less laundry.</h1>
          <p>
            Meet SpinClub: a simple monthly membership for clean clothes, predictable costs,
            and one less thing on your to-do list.
          </p>
          <div class="hero-actions">
            <a class="btn" href="#memberships">Explore memberships <span aria-hidden="true">→</span></a>
            <a class="btn btn-outline" href="#how-it-works">How it works</a>
          </div>
          <div class="hero-note">
            <span class="avatar-stack" aria-hidden="true"><i>S</i><i>J</i><i>A</i></span>
            A fresh approach for students, busy people, and households.
          </div>
        </div>

        <div class="hero-art" aria-label="Illustration of a modern washing machine">
          <span class="sparkle sparkle-a" aria-hidden="true">✳</span>
          <span class="sparkle sparkle-b" aria-hidden="true">✦</span>
          <div class="washer">
            <div class="washer-top"><div class="washer-brand">SPINCLUB</div><div class="washer-dial"></div></div>
            <div class="washer-door"></div>
          </div>
          <div class="floating-card card-one"><strong>Fresh start!</strong><small>Your next wash is sorted.</small></div>
          <div class="floating-card card-two"><strong>One easy monthly price</strong><small>Memberships from $19/mo*</small></div>
        </div>
      </div>
    </section>

    <section class="benefit-strip" aria-label="Membership benefits">
      <div class="container benefit-row">
        <div class="benefit"><span aria-hidden="true">↻</span> Predictable monthly pricing</div>
        <div class="benefit"><span aria-hidden="true">♡</span> Flexible plans for real life</div>
        <div class="benefit"><span aria-hidden="true">✦</span> More time for what matters</div>
      </div>
    </section>

    <section class="section" id="services">
      <div class="container">
        <div class="section-head">
          <span class="eyebrow">Our services</span>
          <h2>Your laundry routine,<br />your way.</h2>
          <p>Drop in for a quick wash or let us take laundry off your hands. Choose the service that fits your day.</p>
        </div>
        <div class="services-grid">
          <article class="service-card">
            <div class="service-icon" aria-hidden="true">🫧</div>
            <h3>Self-service laundry</h3>
            <p>Modern washers and dryers, ready when you are. Use your membership visits or pay as you go.</p>
            <a class="text-link" href="#memberships">See membership options →</a>
          </article>
          <article class="service-card">
            <div class="service-icon" aria-hidden="true">🧺</div>
            <h3>Wash, dry & fold</h3>
            <p>Drop off your laundry and pick it up clean, dry, and neatly folded. Add-on pricing may apply.</p>
            <a class="text-link" href="#join">Ask about wash & fold →</a>
          </article>
          <article class="service-card">
            <div class="service-icon" aria-hidden="true">🚲</div>
            <h3>Pickup & delivery</h3>
            <p>Prefer to stay home? Arrange a pickup and delivery in eligible local areas for an additional fee.</p>
            <a class="text-link" href="#location">Check service area →</a>
          </article>
        </div>
      </div>
    </section>

    <section class="section membership" id="memberships">
      <div class="container">
        <div class="section-head center">
          <span class="eyebrow">Memberships</span>
          <h2>Find your laundry happy place.</h2>
          <p>Pick a plan that suits your routine. You can update these example prices and inclusions to match your business.</p>
        </div>
        <div class="plans">
          <article class="plan">
            <h3>Basic</h3>
            <p class="plan-for">A little help for lighter laundry loads.</p>
            <div class="price">$19<small> / month</small></div>
            <div class="plan-detail">4 wash credits / month</div>
            <ul>
              <li>Self-service washer access</li>
              <li>Member pricing on dryers</li>
              <li>Credits refresh monthly</li>
            </ul>
            <a class="btn btn-outline choose-plan" href="#join" data-plan="Basic">Choose Basic</a>
          </article>

          <article class="plan popular">
            <span class="popular-label">Most popular</span>
            <h3>Standard</h3>
            <p class="plan-for">A good fit for regular weekly laundry.</p>
            <div class="price">$39<small> / month</small></div>
            <div class="plan-detail">10 wash credits / month</div>
            <ul>
              <li>Everything in Basic</li>
              <li>Priority booking access</li>
              <li>Member discount on wash & fold</li>
            </ul>
            <a class="btn choose-plan" href="#join" data-plan="Standard">Choose Standard</a>
          </article>

          <article class="plan">
            <h3>Premium</h3>
            <p class="plan-for">For busy schedules and bigger loads.</p>
            <div class="price">$69<small> / month</small></div>
            <div class="plan-detail">20 wash credits / month</div>
            <ul>
              <li>Everything in Standard</li>
              <li>Extra dryer credits included</li>
              <li>More savings on service add-ons</li>
            </ul>
            <a class="btn btn-outline choose-plan" href="#join" data-plan="Premium">Choose Premium</a>
          </article>

          <article class="plan">
            <h3>Family</h3>
            <p class="plan-for">Shared laundry support for households.</p>
            <div class="price">$99<small> / month</small></div>
            <div class="plan-detail">32 shared wash credits / month</div>
            <ul>
              <li>Share credits with your household</li>
              <li>Priority booking access</li>
              <li>Member discount on add-ons</li>
            </ul>
            <a class="btn btn-outline choose-plan" href="#join" data-plan="Family">Choose Family</a>
          </article>
        </div>
        <p class="pricing-note">*Example pricing for website demonstration only. Final prices, credit rules, and terms should be confirmed before launch.</p>
      </div>
    </section>

    <section class="section" id="how-it-works">
      <div class="container">
        <div class="section-head center">
          <span class="eyebrow">How it works</span>
          <h2>Three steps to laundry freedom.</h2>
        </div>
        <div class="steps">
          <article class="step">
            <div class="step-number">01</div>
            <h3>Choose your plan</h3>
            <p>Compare the memberships and find the one that matches your laundry routine.</p>
          </article>
          <article class="step">
            <div class="step-number">02</div>
            <h3>Join SpinClub</h3>
            <p>Sign up for a membership and get your account details. Manage your plan online.</p>
          </article>
          <article class="step">
            <div class="step-number">03</div>
            <h3>Get laundry done</h3>
            <p>Use your monthly credits in-store, or ask about wash and fold or delivery options.</p>
          </article>
        </div>
      </div>
    </section>

    <section class="fold-band">
      <div class="container">
        <div class="fold-card">
          <div>
            <span class="eyebrow">A little extra help</span>
            <h2>Hand us the laundry. Take back your time.</h2>
            <p>Let SpinClub handle the washing, drying, and folding while you get on with your day. Add-on availability and pricing depend on your location.</p>
            <a class="btn btn-light" href="#join">Ask about wash & fold <span aria-hidden="true">→</span></a>
          </div>
          <div class="fold-visual" aria-hidden="true"><div class="laundry-basket"></div></div>
        </div>
      </div>
    </section>

    <section class="section" id="faq">
      <div class="container faq-layout">
        <div>
          <span class="eyebrow">Good to know</span>
          <h2>Questions?<br />We’ve got you.</h2>
          <p>Need help choosing a plan? Get in touch and we’ll help you find the right fit.</p>
          <a class="text-link" href="#join">Contact SpinClub →</a>
        </div>
        <div class="faq-list">
          <details>
            <summary>What does a SpinClub membership include?</summary>
            <p>Each membership includes a set number of monthly wash credits and the benefits listed in its plan. Confirm the final credit rules and any additional fees with your local SpinClub.</p>
          </details>
          <details>
            <summary>Can I use wash and fold or pickup and delivery?</summary>
            <p>These can be offered as optional services for an additional fee. Availability may vary by location, so contact SpinClub to confirm service areas and current pricing.</p>
          </details>
          <details>
            <summary>What happens if I don’t use all my credits?</summary>
            <p>Credit rollover rules depend on the membership terms. This example site does not set or enforce rollover; add your actual policy before taking subscriptions.</p>
          </details>
          <details>
            <summary>Can I change or cancel my membership?</summary>
            <p>Membership changes and cancellations should be handled through your customer account or by contacting SpinClub. Add your actual notice period and cancellation terms here.</p>
          </details>
          <details>
            <summary>Do I need to bring detergent?</summary>
            <p>Update this answer with your laundromat’s policy, including whether detergent is available for purchase or included in any service.</p>
          </details>
        </div>
      </div>
    </section>

    <section class="section location" id="location">
      <div class="container">
        <div class="section-head">
          <span class="eyebrow">Find your SpinClub</span>
          <h2>Close to home. Easy to fit in.</h2>
          <p>Replace this section with your laundromat address, opening hours, and pickup and delivery service area.</p>
        </div>
        <div class="location-grid">
          <div class="location-card">
            <h3>Visit us</h3>
            <p><strong>SpinClub — Your Neighborhood</strong><br />Add your street address here<br />Your City, ZIP / Postcode</p>
            <a class="text-link" href="mailto:hello@spinclub.example">hello@spinclub.example →</a>
            <div class="map-placeholder">Add your map or directions link here</div>
          </div>
          <div class="hours-card">
            <h3>Opening hours</h3>
            <p>Example hours — update before publishing.</p>
            <div class="hours-row"><span>Monday – Friday</span><strong>7:00 am – 9:00 pm</strong></div>
            <div class="hours-row"><span>Saturday</span><strong>8:00 am – 8:00 pm</strong></div>
            <div class="hours-row"><span>Sunday</span><strong>8:00 am – 6:00 pm</strong></div>
            <p style="margin:20px 0 0">Pickup and delivery availability may vary by neighborhood.</p>
          </div>
        </div>
      </div>
    </section>

    <section class="section signup" id="join">
      <div class="container signup-grid">
        <div>
          <span class="eyebrow">Your next laundry day starts here</span>
          <h2>Ready to make room for more?</h2>
          <p>Choose your membership and leave your details. We’ll be in touch with the next steps.</p>
          <p><strong>Note:</strong> This demo form doesn’t create an account or take payment yet.</p>
        </div>
        <form class="signup-form" id="signupForm">
          <div class="form-row">
            <div>
              <label for="name">Your name</label>
              <input id="name" name="name" autocomplete="name" required placeholder="Alex Taylor" />
            </div>
            <div>
              <label for="email">Email address</label>
              <input id="email" name="email" type="email" autocomplete="email" required placeholder="alex@example.com" />
            </div>
          </div>
          <label for="planSelect">Membership you’re interested in</label>
          <select id="planSelect" name="plan" required>
            <option value="">Select a plan</option>
            <option>Basic</option>
            <option>Standard</option>
            <option>Premium</option>
            <option>Family</option>
            <option>Not sure yet</option>
          </select>
          <button class="btn" type="submit">Request membership info <span aria-hidden="true">→</span></button>
          <p class="form-message" id="formMessage" role="status" aria-live="polite"></p>
        </form>
      </div>
    </section>
  </main>

  <footer>
    <div class="container footer-row">
      <a class="brand" href="#home"><span class="brand-mark" aria-hidden="true">↻</span> SpinClub</a>
      <p>© <span id="year"></span> SpinClub. Laundry, on your terms.</p>
      <div class="footer-links">
        <a href="#services">Services</a>
        <a href="#memberships">Memberships</a>
        <a href="#faq">FAQs</a>
      </div>
    </div>
  </footer>

  <script>
    const menuButton = document.querySelector(".menu-toggle");
    const navLinks = document.querySelector(".nav-links");

    menuButton.addEventListener("click", () => {
      const isOpen = navLinks.classList.toggle("open");
      menuButton.setAttribute("aria-expanded", String(isOpen));
      menuButton.setAttribute("aria-label", isOpen ? "Close navigation" : "Toggle navigation");
      menuButton.textContent = isOpen ? "×" : "☰";
    });

    navLinks.querySelectorAll("a").forEach((link) => {
      link.addEventListener("click", () => {
        navLinks.classList.remove("open");
        menuButton.setAttribute("aria-expanded", "false");
        menuButton.setAttribute("aria-label", "Toggle navigation");
        menuButton.textContent = "☰";
      });
    });

    document.querySelectorAll(".choose-plan").forEach((button) => {
      button.addEventListener("click", () => {
        document.querySelector("#planSelect").value = button.dataset.plan;
      });
    });

    document.querySelector("#signupForm").addEventListener("submit", (event) => {
      event.preventDefault();
      const form = event.currentTarget;
      const message = document.querySelector("#formMessage");
      message.className = "form-message success";
      message.textContent =
        "Thanks! This demo form is ready to connect to your sign-up service.";
      form.reset();
    });

    document.querySelector("#year").textContent = new Date().getFullYear();
  </script>
</body>
</html>
