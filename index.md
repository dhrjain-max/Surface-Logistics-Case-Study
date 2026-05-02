<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Case Study — Logistics Diagnostic | Dhruv Jain</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Fraunces:ital,opsz,wght@0,9..144,300;0,9..144,400;0,9..144,600;1,9..144,300;1,9..144,400&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #f7f6f3;
    --ink: #111111;
    --ink-muted: #6b6b6b;
    --ink-light: #b0afa9;
    --accent: #1a3d2b;
    --accent-light: #e8f0eb;
    --rule: #d8d6d0;
    --font-display: 'Fraunces', Georgia, serif;
    --font-body: 'DM Sans', sans-serif;
  }
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
  html { background: var(--bg); color: var(--ink); font-family: var(--font-body); font-size: clamp(15px, 1.1vw, 17px); line-height: 1.7; -webkit-font-smoothing: antialiased; }
  .page { max-width: 720px; margin: 0 auto; padding: clamp(40px, 8vw, 80px) clamp(24px, 5vw, 48px); }
  .reveal { opacity: 0; transform: translateY(18px); transition: opacity 0.65s ease, transform 0.65s ease; }
  .reveal.visible { opacity: 1; transform: none; }
  .site-header { display: flex; justify-content: space-between; align-items: center; margin-bottom: clamp(48px, 8vw, 80px); padding-bottom: 20px; border-bottom: 1px solid var(--rule); }
  .site-header .name { font-family: var(--font-body); font-size: 0.85rem; font-weight: 500; letter-spacing: 0.08em; text-transform: uppercase; color: var(--ink); text-decoration: none; }
  .site-header .label { font-size: 0.78rem; color: var(--ink-muted); font-weight: 300; letter-spacing: 0.06em; text-transform: uppercase; }
  .hero { margin-bottom: clamp(48px, 8vw, 72px); }
  .case-label { font-size: 0.75rem; font-weight: 500; letter-spacing: 0.12em; text-transform: uppercase; color: var(--accent); margin-bottom: 16px; display: flex; align-items: center; gap: 10px; }
  .case-label::after { content: ''; display: block; height: 1px; width: 40px; background: var(--accent); }
  .hero h1 { font-family: var(--font-display); font-size: clamp(2rem, 5vw, 3rem); font-weight: 400; line-height: 1.15; letter-spacing: -0.01em; color: var(--ink); margin-bottom: 20px; }
  .hero h1 em { font-style: italic; font-weight: 300; color: var(--ink-muted); }
  .hero-meta { display: flex; gap: 24px; flex-wrap: wrap; }
  .meta-item { font-size: 0.8rem; color: var(--ink-muted); font-weight: 300; }
  .meta-item strong { color: var(--ink); font-weight: 500; margin-right: 4px; }
  .results-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 1px; background: var(--rule); border: 1px solid var(--rule); margin-bottom: clamp(48px, 8vw, 72px); border-radius: 2px; overflow: hidden; }
  .result-cell { background: var(--bg); padding: clamp(20px, 4vw, 32px) clamp(20px, 4vw, 28px); }
  .result-cell.featured { background: var(--accent); color: white; }
  .result-number { font-family: var(--font-display); font-size: clamp(2.4rem, 6vw, 3.6rem); font-weight: 600; line-height: 1; letter-spacing: -0.02em; color: var(--accent); margin-bottom: 6px; display: block; }
  .result-cell.featured .result-number { color: white; }
  .result-label { font-size: 0.78rem; font-weight: 400; color: var(--ink-muted); line-height: 1.4; }
  .result-cell.featured .result-label { color: rgba(255,255,255,0.75); }
  .section { margin-bottom: clamp(40px, 7vw, 64px); }
  .section-header { display: flex; align-items: baseline; gap: 14px; margin-bottom: 20px; }
  .section-num { font-size: 0.7rem; font-weight: 500; letter-spacing: 0.1em; text-transform: uppercase; color: var(--ink-light); }
  .section h2 { font-family: var(--font-display); font-size: clamp(1.1rem, 2.5vw, 1.35rem); font-weight: 400; letter-spacing: -0.01em; color: var(--ink); }
  .section p { font-size: 0.95rem; color: #333; font-weight: 300; margin-bottom: 14px; line-height: 1.8; }
  .section p:last-child { margin-bottom: 0; }
  .process-steps { margin: 20px 0; }
  .process-step { padding: 16px 0; border-bottom: 1px solid var(--rule); display: flex; gap: 20px; align-items: baseline; }
  .process-step:first-child { border-top: 1px solid var(--rule); }
  .step-num { font-family: var(--font-display); font-size: 1.1rem; font-weight: 300; color: var(--ink-light); flex-shrink: 0; width: 24px; }
  .step-content { flex: 1; }
  .step-label { font-size: 0.78rem; font-weight: 500; letter-spacing: 0.08em; text-transform: uppercase; color: var(--accent); margin-bottom: 4px; }
  .step-content p { font-size: 0.9rem; color: #444; font-weight: 300; line-height: 1.7; margin-bottom: 0; }
  .diagnostic-grid { margin: 20px 0; display: flex; flex-direction: column; gap: 1px; background: var(--rule); border: 1px solid var(--rule); border-radius: 2px; overflow: hidden; }
  .diagnostic-item { background: var(--bg); padding: 20px 24px; }
  .diagnostic-label { font-size: 0.72rem; font-weight: 500; letter-spacing: 0.1em; text-transform: uppercase; color: var(--accent); margin-bottom: 6px; }
  .diagnostic-headline { font-family: var(--font-display); font-size: 1rem; font-weight: 400; color: var(--ink); margin-bottom: 6px; }
  .diagnostic-item p { font-size: 0.88rem; color: #555; font-weight: 300; line-height: 1.7; margin-bottom: 0; }
  .diagnostic-item .stat { font-family: var(--font-display); font-size: 1.4rem; font-weight: 600; color: var(--accent); display: inline; margin-right: 4px; }
  .deliverables { margin: 20px 0; }
  .deliverable { padding: 14px 0; border-bottom: 1px solid var(--rule); display: flex; gap: 16px; align-items: baseline; }
  .deliverable:first-child { border-top: 1px solid var(--rule); }
  .del-num { font-family: var(--font-display); font-size: 0.85rem; font-weight: 300; color: var(--ink-light); flex-shrink: 0; width: 20px; }
  .del-content { flex: 1; }
  .del-title { font-size: 0.88rem; font-weight: 500; color: var(--ink); margin-bottom: 2px; }
  .del-desc { font-size: 0.85rem; color: var(--ink-muted); font-weight: 300; line-height: 1.6; }
  .callout { background: var(--accent-light); border-left: 3px solid var(--accent); padding: 18px 22px; margin: 24px 0; border-radius: 0 2px 2px 0; }
  .callout p { font-size: 0.9rem; color: var(--accent); font-weight: 400; font-style: italic; margin: 0; line-height: 1.6; }
  .opportunity { display: grid; grid-template-columns: 1fr 1fr; gap: 1px; background: var(--rule); border: 1px solid var(--rule); border-radius: 2px; overflow: hidden; margin: 20px 0; }
  .opp-cell { background: var(--bg); padding: 20px 22px; }
  .opp-label { font-size: 0.72rem; font-weight: 500; letter-spacing: 0.1em; text-transform: uppercase; color: var(--ink-muted); margin-bottom: 6px; }
  .opp-number { font-family: var(--font-display); font-size: clamp(1.6rem, 4vw, 2.2rem); font-weight: 600; color: var(--accent); line-height: 1; margin-bottom: 4px; display: block; }
  .opp-sub { font-size: 0.8rem; color: var(--ink-muted); font-weight: 300; line-height: 1.4; }
  .about-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 1px; background: var(--rule); border: 1px solid var(--rule); border-radius: 2px; overflow: hidden; margin: 20px 0; }
  .about-cell { background: var(--bg); padding: 20px 22px; }
  .about-cell-label { font-size: 0.72rem; font-weight: 500; letter-spacing: 0.1em; text-transform: uppercase; color: var(--ink-light); margin-bottom: 8px; }
  .about-cell p { font-size: 0.88rem; color: #444; font-weight: 300; line-height: 1.7; margin-bottom: 0; }
  hr { border: none; border-top: 1px solid var(--rule); margin: clamp(32px, 5vw, 48px) 0; }
  .cta-block { padding: clamp(28px, 5vw, 40px); border: 1px solid var(--ink); border-radius: 2px; margin-top: clamp(40px, 7vw, 64px); }
  .cta-block h3 { font-family: var(--font-display); font-size: clamp(1.1rem, 2.5vw, 1.4rem); font-weight: 400; letter-spacing: -0.01em; margin-bottom: 10px; }
  .cta-block p { font-size: 0.9rem; color: var(--ink-muted); font-weight: 300; line-height: 1.7; margin-bottom: 20px; }
  .contact-row { display: flex; flex-wrap: wrap; gap: 12px; }
  .contact-link { font-size: 0.82rem; font-weight: 500; color: var(--accent); text-decoration: none; letter-spacing: 0.03em; border-bottom: 1px solid var(--accent); padding-bottom: 1px; transition: opacity 0.2s; }
  .contact-link:hover { opacity: 0.65; }
  .contact-sep { color: var(--ink-light); font-size: 0.82rem; line-height: 1; align-self: center; }
  .site-footer { margin-top: clamp(40px, 7vw, 64px); padding-top: 20px; border-top: 1px solid var(--rule); font-size: 0.75rem; color: var(--ink-light); font-weight: 300; }
  @media (max-width: 480px) {
    .results-grid { grid-template-columns: 1fr 1fr; }
    .opportunity { grid-template-columns: 1fr; }
    .about-grid { grid-template-columns: 1fr; }
    .site-header { flex-direction: column; align-items: flex-start; gap: 4px; }
  }
</style>
</head>
<body>
<div class="page">

  <header class="site-header reveal">
    <a href="mailto:dhrv_jain@hotmail.com" class="name">Dhruv Jain</a>
    <span class="label">Operations &amp; Growth Consultant</span>
  </header>

  <div class="hero reveal" style="transition-delay:0.1s">
    <div class="case-label">Case Study</div>
    <h1>Logistics Diagnostic &#8212;<br><em>finding &#8377;44&#8211;53&nbsp;Cr<br>hiding in plain sight</em></h1>
    <div class="hero-meta">
      <span class="meta-item"><strong>Industry</strong> Surface Logistics</span>
      <span class="meta-item"><strong>Engagement</strong> Paid Diagnostic</span>

      <span class="meta-item"><strong>Group Topline</strong> &#8377;2,000+ Cr</span>
    </div>
  </div>

  <div class="results-grid reveal" style="transition-delay:0.2s">
    <div class="result-cell featured">
      <span class="result-number">&#8377;44&#8211;53 Cr</span>
      <span class="result-label">Total opportunity identified across margin and revenue</span>
    </div>
    <div class="result-cell">
      <span class="result-number">~0%</span>
      <span class="result-label">Net margin on &#8377;400 Cr PTL revenue &#8212; the starting problem</span>
    </div>
    <div class="result-cell">
      <span class="result-number">9,800+</span>
      <span class="result-label">High and mid-value dormant customers identified as recoverable</span>
    </div>
    <div class="result-cell">
      <span class="result-number">49K+</span>
      <span class="result-label">Annual trips analyzed across a pan-India network to surface the findings</span>
    </div>
  </div>

  <!-- 01 THE ASK -->
  <div class="section reveal" style="transition-delay:0.25s">
    <div class="section-header">
      <span class="section-num">01</span>
      <h2>The Ask</h2>
    </div>
    <p>A decades-old, family-owned surface logistics company &#8212; part of a &#8377;2,000+ Cr group &#8212; was running &#8377;400 Cr in Part Truck Load (PTL) revenue across 100+ cities and 49,000+ trips a year. At breakeven. Nobody had a clear, data-backed answer for why.</p>
    <p>The brief was to run a structured technology and automation study across operations, commercial, finance, CRM, and technology. Find where the real opportunities were. Put numbers on them. Deliver a plan the internal team could actually build from &#8212; not a summary of observations.</p>
  </div>

  <hr>

  <!-- 02 THE PROCESS -->
  <div class="section reveal">
    <div class="section-header">
      <span class="section-num">02</span>
      <h2>The Process</h2>
    </div>
    <p>The study started wide &#8212; PTL, FTL, Projects, 3PL &#8212; and narrowed to where the improvement potential was most concentrated. LLM-assisted analysis cut through five to six years of operational data fast, surfacing patterns that would have taken weeks to isolate manually and letting hypotheses get tested and revised against real numbers in rapid iteration.</p>

    <div class="process-steps">
      <div class="process-step">
        <span class="step-num">1</span>
        <div class="step-content">
          <div class="step-label">Stakeholder Conversations</div>
          <p>Seven conversations: CEO, IT Lead, Commercial and Finance Lead, Branch Manager, Sales Manager, Data Analyst. Each one mapped a different layer &#8212; what leadership believed, what branch teams actually dealt with, where the two diverged. Those gaps became the first set of hypotheses to test in the data.</p>
        </div>
      </div>
      <div class="process-step">
        <span class="step-num">2</span>
        <div class="step-content">
          <div class="step-label">AI-Accelerated Data Analysis</div>
          <p>Route revenue, cargo economics, trip-level margins, vendor quoting behaviour, three years of customer dormancy data. Processed with LLM-based tools. Patterns that are invisible in any single year became clear across the full dataset &#8212; and that is where the three root causes came from.</p>
        </div>
      </div>
      <div class="process-step">
        <span class="step-num">3</span>
        <div class="step-content">
          <div class="step-label">Hypothesis Validation</div>
          <p>Every finding was tested against the client's own numbers before it made it into the output. Where the commercial team had previously estimated an opportunity figure, those estimates were used as anchors &#8212; and the analysis confirmed and broke them down into specific levers. Nothing was included on vibes alone.</p>
        </div>
      </div>
      <div class="process-step">
        <span class="step-num">4</span>
        <div class="step-content">
          <div class="step-label">Focus Identification</div>
          <p>PTL had the widest margin gap, the richest historical data already sitting in their systems, and three compounding levers where automation could have outsized impact without adding steps for branch teams already under pressure. That is where the study focused.</p>
        </div>
      </div>
    </div>
  </div>

  <hr>

  <!-- 03 WHAT WAS FOUND -->
  <div class="section reveal">
    <div class="section-header">
      <span class="section-num">03</span>
      <h2>What Was Found</h2>
    </div>
    <p>Three root causes. Each one significant on its own. Together, they explained the margin problem &#8212; and pointed to &#8377;44&#8211;53 Cr sitting on the table.</p>

    <div class="diagnostic-grid">
      <div class="diagnostic-item">
        <div class="diagnostic-label">Finding 1 &#8212; Margin</div>
        <div class="diagnostic-headline">Trucks full. Margins flat.</div>
        <p>Fill rate was <span class="stat">92.5%</span> &#8212; capacity wasn't the issue. Cargo mix was. Light freight earns a 48% revenue premium per ton over heavy loads but made up only 7.8% of what went on the trucks. Branch teams were optimising for fill rate and dispatch speed &#8212; rational, given how they were measured. No system was evaluating the margin contribution of each item at intake, so better-paying cargo kept getting displaced by cheaper freight that filled the space first.</p>
      </div>
      <div class="diagnostic-item">
        <div class="diagnostic-label">Finding 2 &#8212; Cost</div>
        <div class="diagnostic-headline">&#8377;200+ Cr in truck hire. Almost none of it round-trip.</div>
        <p>Backhaul &#8212; booking a return load at the time of outbound dispatch &#8212; was running at <span class="stat">2%</span> of trips. The business was paying one-way rates on more than &#8377;200 Cr of annual truck hire. The commercial case for round-trip booking was understood internally. The problem was bandwidth: branches had no time to plan return loads alongside time-critical dispatch, and no system to predict what cargo would be available at the destination with enough lead time to act on it.</p>
      </div>
      <div class="diagnostic-item">
        <div class="diagnostic-label">Finding 3 &#8212; Revenue</div>
        <div class="diagnostic-headline">A pattern everyone knew about. No system to do anything with it.</div>
        <p>Every Q4, logistics capacity tightens across the industry. Businesses rushing to close the year overflow into whoever has truck space. The company knew this happened and benefited from it. What three years of dormancy data revealed was how much recoverable revenue was inside that pattern: <span class="stat">~23,500</span> customers going dormant every June, last active in March, the same spike three years running. Of those, <span class="stat">9,800+</span> were above the &#8377;25K revenue threshold &#8212; worth &#8377;22&#8211;29 Cr annually if re-engaged before the next season. The knowledge was there. A system to act on it wasn't.</p>
      </div>
    </div>

    <div class="callout">
      <p>The vendor bidding system averaged 1.09 quotes per trip &#8212; branches called trusted vendors directly because the system added steps to an already time-pressured workflow. That became a design constraint for everything built: replace manual effort, don't add to it.</p>
    </div>
  </div>

  <hr>

  <!-- 04 WHAT WAS DELIVERED -->
  <div class="section reveal">
    <div class="section-header">
      <span class="section-num">04</span>
      <h2>What Was Delivered</h2>
    </div>
    <p>Not a list of recommendations. A build-ready blueprint &#8212; opportunity sized from the client's own data, systems architected, module logic fully specified, pilot designed with a control methodology. Everything needed for an internal technical team to start building without external dependency.</p>

    <div class="opportunity">
      <div class="opp-cell">
        <div class="opp-label">Margin Opportunity</div>
        <span class="opp-number">&#8377;22&#8211;24 Cr</span>
        <div class="opp-sub">Load composition optimisation (&#8377;20 Cr) + backhaul conversion (&#8377;2&#8211;4 Cr). Conservative estimates, grounded in the client's own operational data.</div>
      </div>
      <div class="opp-cell">
        <div class="opp-label">Revenue Opportunity</div>
        <span class="opp-number">&#8377;22&#8211;29 Cr</span>
        <div class="opp-sub">15&#8211;20% reactivation of 9,800+ dormant customers above the &#8377;25K threshold, plus an unquantified long tail of 48,000+ smaller accounts reachable through automated outreach.</div>
      </div>
    </div>

    <div class="deliverables">
      <div class="deliverable">
        <span class="del-num">1</span>
        <div class="del-content">
          <div class="del-title">Validated Opportunity Sizing</div>
          <div class="del-desc">Every figure came from the client's own operational data. Nothing extrapolated from industry benchmarks. Where the commercial team had previously estimated an opportunity, those numbers were used as anchors &#8212; the analysis confirmed them and decomposed them into specific, addressable levers.</div>
        </div>
      </div>
      <div class="deliverable">
        <span class="del-num">2</span>
        <div class="del-content">
          <div class="del-title">Two System Architectures, Fully Specified</div>
          <div class="del-desc">A PTL Profit Maximisation Engine: camera-based cargo dimension capture at intake, load composition optimiser, 3D loading plan with physical placement sequence, backhaul booking committed at dispatch, routing decision logic. A CRM Intelligence system: dormancy scoring by customer, tiered outreach by value, AI-generated messaging at scale, pre-season re-engagement workflows. Both specified component by component, with integration specs and data flow definitions.</div>
        </div>
      </div>
      <div class="deliverable">
        <span class="del-num">3</span>
        <div class="del-content">
          <div class="del-title">Module-Level Model Logic</div>
          <div class="del-desc">For every system component: the objective function, the input variables and data sources, the decision logic, override and exception handling, and how accuracy gets measured and improved over time. The load composition optimiser, backhaul prediction engine, customer cadence scoring model, and AI outreach system were each specified at the level a technical team needs to build &#8212; not the level a consultant needs to present.</div>
        </div>
      </div>
      <div class="deliverable">
        <span class="del-num">4</span>
        <div class="del-content">
          <div class="del-title">The Procurement Loop</div>
          <div class="del-desc">The connection between both systems: load optimiser spots a cargo gap on a lane &#8212; CRM scores customers likely to ship that route &#8212; targeted outreach goes out at a competitive rate &#8212; gap filled, customer retained. Each system makes the other more effective. Run them separately and you leave value on the table.</div>
        </div>
      </div>
      <div class="deliverable">
        <span class="del-num">5</span>
        <div class="del-content">
          <div class="del-title">Pilot Design</div>
          <div class="del-desc">Branch selection based on trip volume and bidirectional lane presence &#8212; the top 10 cities cover 73% of PTL revenue, pilot scoped to 2&#8211;3 high-fit branches. Matched control branches to separate system impact from market effects. Override rate tracked from day one as a model-improvement signal and an adoption visibility tool for central operations.</div>
        </div>
      </div>
      <div class="deliverable">
        <span class="del-num">6</span>
        <div class="del-content">
          <div class="del-title">Four-Phase Deployment Roadmap</div>
          <div class="del-desc">Year 1: system recommends, team approves, overrides improve the model. Month 13: live monitoring, humans still decide. Month 19: routine decisions automated, exceptions handled by people. Month 25+: intelligent operations within defined scope, human oversight on strategy. Autonomy earned through demonstrated accuracy at each stage &#8212; not assumed upfront.</div>
        </div>
      </div>
    </div>
  </div>

  <hr>

  <!-- 05 ABOUT -->
  <div class="section reveal">
    <div class="section-header">
      <span class="section-num">05</span>
      <h2>About</h2>
    </div>
    <p>Nine years across growth, operations, and account management. MBA from ISB Hyderabad. Previously AVP at Axis Bank managing a &#8377;350+ Cr fintech portfolio; before that, large-scale programs for Google and Mastercard. I work with businesses that are stuck and leave when they aren't.</p>

    <div class="about-grid" style="grid-template-columns:1fr 1fr">
      <div class="about-cell">
        <div class="about-cell-label">How I work</div>
        <p>Embedded alongside the client team. First engagement is a fixed deliverable: problem identified, opportunity sized, solution specified. You know what you are getting before committing to a build.</p>
      </div>
      <div class="about-cell">
        <div class="about-cell-label">What this is not</div>
        <p>Not AI for its own sake. Not a permanent hire. Not 80-slide decks. The goal is to make myself unnecessary &#8212; systems the team owns, not services they keep paying for.</p>
      </div>
    </div>
  </div>

  <!-- CTA -->
  <div class="cta-block reveal">
    <h3>Revenue is there. Margins aren't. Sound familiar?</h3>
    <p>Most margin problems aren't pricing problems. They're visibility problems &#8212; the data exists, the pattern is there, but nobody has looked across enough of it at once. The diagnostic surfaces what's actually happening and puts a rupee figure on what fixing it is worth.</p>
    <p>First engagement is a fixed deliverable: problem identified, opportunity sized, solution specified, roadmap ready. You know what's broken and what it's worth to fix before committing to a build.</p>
    <div class="contact-row">
      <a href="mailto:dhrv_jain@hotmail.com" class="contact-link">dhrv_jain@hotmail.com</a>
      <span class="contact-sep">&middot;</span>
      <a href="tel:+918284084645" class="contact-link">+91 82840 84645</a>
      <span class="contact-sep">&middot;</span>
      <a href="https://wa.me/918284084645" class="contact-link">WhatsApp</a>
    </div>
  </div>

  <footer class="site-footer reveal">
    <p>Dhruv Jain &middot; Operations &amp; Growth Consulting</p>
  </footer>

</div>
<script>
  const reveals = document.querySelectorAll('.reveal');
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) { entry.target.classList.add('visible'); observer.unobserve(entry.target); }
    });
  }, { threshold: 0.08 });
  reveals.forEach(el => observer.observe(el));
</script>
</body>
</html>
