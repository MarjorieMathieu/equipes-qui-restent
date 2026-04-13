<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Équilibre Performance — Pilote 2026</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link href="https://fonts.googleapis.com/css2?family=Lora:ital,wght@0,400;0,500;0,600;0,700;1,400;1,500;1,600;1,700&family=Jost:wght@300;400;500;600&display=swap" rel="stylesheet">
    <style>
        :root {
            --navy:       #1B365D;
            --navy-dark:  #151c3a;
            --coral:      #E07A5F;
            --coral-light:#f4a68e;
            --silver:     #6B6560;
            --white:      #ffffff;
            --grid-line:  rgba(21,28,58,0.07);
            --serif: 'Lora', Georgia, serif;
            --sans:  'Jost', sans-serif;
        }

        * { margin:0; padding:0; box-sizing:border-box; }
        html { scroll-behavior:smooth; }

        body {
            font-family: var(--sans);
            color: var(--navy);
            background-color: #fff;
            background-image:
                linear-gradient(var(--grid-line) 1px, transparent 1px),
                linear-gradient(90deg, var(--grid-line) 1px, transparent 1px);
            background-size: 30px 30px;
            background-attachment: fixed;
            line-height: 1.7;
            overflow-x: hidden;
            -webkit-font-smoothing: antialiased;
        }

        /* ── NAV ─────────────────────────────── */
        nav {
            position: fixed; top:0; left:0; right:0; z-index:200;
            padding: 1.1rem 6%;
            display: flex; justify-content:space-between; align-items:center;
            background: rgba(255,255,255,0.94);
            backdrop-filter: blur(14px);
            border-bottom: 1px solid rgba(27,54,93,0.1);
            transition: box-shadow 0.3s;
        }
        .nav-logo {
            font-family: var(--serif);
            font-style: italic;
            font-size: 1.05rem;
            color: var(--navy);
            letter-spacing: 0.01em;
        }
        .nav-right { display:flex; align-items:center; gap:1rem; }

        /* ── LANG TOGGLE ─────────────────────── */
        .lang-toggle {
            display: flex;
            align-items: center;
            background: rgba(27,54,93,0.06);
            border: 1px solid rgba(27,54,93,0.12);
            border-radius: 100px;
            padding: 3px;
            gap: 2px;
        }
        .lang-btn {
            padding: 0.28rem 0.75rem;
            border-radius: 100px;
            font-size: 0.7rem;
            font-weight: 700;
            letter-spacing: 0.12em;
            text-transform: uppercase;
            cursor: pointer;
            border: none;
            background: transparent;
            color: rgba(27,54,93,0.4);
            transition: all 0.22s ease;
            line-height: 1;
        }
        .lang-btn.active {
            background: var(--navy);
            color: #fff;
            box-shadow: 0 2px 8px rgba(27,54,93,0.2);
        }
        .lang-btn:not(.active):hover {
            color: var(--navy);
            background: rgba(27,54,93,0.08);
        }

        .nav-cta {
            background: var(--coral);
            color: #fff;
            padding: 0.6rem 1.4rem;
            border-radius: 4px;
            font-size: 0.82rem;
            font-weight: 600;
            text-decoration: none;
            letter-spacing: 0.02em;
            transition: all 0.3s;
        }
        .nav-cta:hover { background:#c9634a; transform:translateY(-1px); }

        /* ── HERO ────────────────────────────── */
        .hero {
            min-height: 100vh;
            padding: 9rem 6% 5rem;
            position: relative;
            overflow: hidden;
            display: flex;
            flex-direction: column;
            justify-content: center;
        }
        .hero::before {
            content:'';
            position:absolute; top:0; right:0;
            width:50%; height:100%;
            background: radial-gradient(ellipse 70% 80% at 70% 40%, rgba(224,122,95,0.06) 0%, transparent 70%);
            pointer-events:none;
        }
        .hero-ornament {
            position:absolute; right:4%; top:50%;
            transform:translateY(-50%);
            font-family: var(--serif);
            font-size: clamp(200px,24vw,360px);
            font-weight:700; font-style:italic;
            color: rgba(27,54,93,0.03);
            line-height:1; pointer-events:none; user-select:none;
        }
        .hero-inner { max-width:760px; position:relative; z-index:1; }
        .eyebrow { display:flex; align-items:center; gap:0.8rem; margin-bottom:2rem; opacity:0; animation: up 0.9s ease 0.2s forwards; }
        .eyebrow-line { width:28px; height:1px; background:var(--coral); }
        .eyebrow-text { font-size:0.72rem; font-weight:700; text-transform:uppercase; letter-spacing:0.2em; color:var(--coral); }
        .hero h1 { font-family:var(--serif); font-size:clamp(2.6rem,5.5vw,4.8rem); font-weight:700; line-height:1.08; color:var(--navy); margin-bottom:2rem; opacity:0; animation: up 1s ease 0.35s forwards; }
        .hero h1 em { font-style:italic; color:var(--coral); }
        .hero h1 .aside { display:block; font-size:0.48em; font-weight:400; font-style:italic; color:var(--silver); margin-top:0.5em; line-height:1.5; }
        .hero-quote { font-family:var(--serif); font-style:italic; font-size:1.1rem; color:#4a5e7a; border-left:2px solid var(--coral); padding-left:1.4rem; max-width:540px; margin-bottom:1.5rem; line-height:1.8; opacity:0; animation: up 1s ease 0.5s forwards; }
        .hero-body { font-size:0.97rem; color:#3d4f6b; max-width:500px; margin-bottom:2.8rem; line-height:1.75; opacity:0; animation: up 1s ease 0.65s forwards; }
        .hero-body strong { color:var(--navy); font-weight:600; }
        .hero-actions { display:flex; align-items:center; gap:1.5rem; flex-wrap:wrap; opacity:0; animation: up 1s ease 0.8s forwards; }
        .btn-cta { display:inline-flex; align-items:center; gap:0.6rem; background:var(--coral); color:#fff; padding:1rem 2rem; border-radius:4px; font-size:0.92rem; font-weight:700; text-decoration:none; letter-spacing:0.01em; transition:all 0.3s; }
        .btn-cta:hover { background:#c9634a; transform:translateY(-2px); box-shadow:0 8px 28px rgba(224,122,95,0.3); }
        .btn-arrow { transition:transform 0.3s; }
        .btn-cta:hover .btn-arrow { transform:translateX(4px); }
        .cta-meta { font-size:0.78rem; color:#3d4f6b; line-height:1.5; }
        .cta-meta strong { color:var(--navy); font-weight:600; display:block; }
        .spots-row { display:flex; align-items:center; gap:0.5rem; margin-top:1.8rem; opacity:0; animation: up 1s ease 0.95s forwards; }
        .spot { width:9px; height:9px; border-radius:50%; }
        .spot.gone { background:rgba(27,54,93,0.12); border:1px solid rgba(27,54,93,0.2); }
        .spot.open  { background:var(--coral); }
        .spots-txt { font-size:0.75rem; color:#3d4f6b; margin-left:0.3rem; }
        .spots-txt strong { color:var(--coral); }
        .scroll-down { position:absolute; bottom:2.5rem; left:6%; display:flex; align-items:center; gap:0.7rem; font-size:0.7rem; text-transform:uppercase; letter-spacing:0.15em; color:#3d4f6b; opacity:0; animation: fadein 1s ease 1.4s forwards; }
        .scroll-line { width:30px; height:1px; background:#3d4f6b; animation: pulse 2s ease infinite; }
        @keyframes pulse { 0%,100%{width:30px;opacity:.4} 50%{width:50px;opacity:.9} }

        /* ── STATS ───────────────────────────── */
        .stats-band { background:var(--navy-dark); padding:4rem 6%; position:relative; overflow:hidden; }
        .stats-band::before { content:''; position:absolute; inset:0; background:radial-gradient(ellipse 60% 80% at 85% 50%, rgba(224,122,95,0.07) 0%, transparent 70%); }
        .stats-band-inner { max-width:1000px; margin:0 auto; display:grid; grid-template-columns:1.2fr 2fr; gap:3rem; align-items:center; position:relative; }
        .stats-intro h2 { font-family:var(--serif); font-size:clamp(1.6rem,3vw,2.4rem); font-weight:600; font-style:italic; color:#fff; line-height:1.3; }
        .stats-intro h2 em { font-style:normal; color:var(--coral-light); }
        .stats-intro p { font-size:0.88rem; color:rgba(255,255,255,0.6); margin-top:0.8rem; line-height:1.7; }
        .stats-grid { display:grid; grid-template-columns:repeat(3,1fr); gap:1rem; }
        .stat-box { background:rgba(255,255,255,0.04); border:1px solid rgba(255,255,255,0.08); border-radius:10px; padding:1.5rem 1.2rem; transition:all 0.3s; }
        .stat-box:hover { background:rgba(255,255,255,0.07); transform:translateY(-3px); }
        .stat-num { font-family:var(--serif); font-size:2.3rem; font-weight:700; color:var(--coral-light); line-height:1; margin-bottom:0.4rem; }
        .stat-label { font-size:0.8rem; color:rgba(255,255,255,0.6); line-height:1.5; }
        .stat-src { font-size:0.65rem; color:rgba(255,255,255,0.25); margin-top:0.4rem; }

        /* ── PROBLEM ─────────────────────────── */
        .problem { padding:6rem 6%; }
        .problem-inner { max-width:820px; margin:0 auto; }
        .section-label { display:flex; align-items:center; gap:0.7rem; margin-bottom:1.8rem; }
        .section-label-line { width:28px; height:1px; background:var(--coral); }
        .section-label-text { font-size:0.72rem; font-weight:700; text-transform:uppercase; letter-spacing:0.2em; color:var(--coral); }
        .problem h2 { font-family:var(--serif); font-size:clamp(1.8rem,3.5vw,3rem); font-weight:700; line-height:1.15; color:var(--navy); margin-bottom:1.5rem; }
        .problem h2 em { font-style:italic; color:var(--coral); }
        .problem-story { font-family:var(--serif); font-style:italic; font-size:1.1rem; color:#4a5e7a; border-left:2px solid var(--silver); padding-left:1.4rem; margin-bottom:2rem; line-height:1.8; }
        .problem-body { font-size:0.97rem; color:#3d4f6b; line-height:1.75; margin-bottom:1rem; }
        .problem-body strong { color:var(--navy); font-weight:600; }
        .problem-traps { display:grid; grid-template-columns:1fr 1fr; gap:0.8rem; margin-top:2.5rem; }
        .trap { display:flex; gap:0.8rem; align-items:flex-start; padding:1rem 1.2rem; background:#fff; border:1px solid rgba(27,54,93,0.08); border-radius:8px; }
        .trap-x { color:rgba(27,54,93,0.2); font-size:1rem; flex-shrink:0; margin-top:2px; }
        .trap-text { font-size:0.84rem; color:#3d4f6b; line-height:1.5; }
        .trap-text strong { color:var(--navy); }

        /* ── METHOD ──────────────────────────── */
        .method { background:var(--navy-dark); padding:6rem 6%; position:relative; overflow:hidden; }
        .method::before { content:''; position:absolute; inset:0; background:radial-gradient(ellipse 50% 60% at 10% 80%, rgba(224,122,95,0.06) 0%, transparent 70%); }
        .method-inner { max-width:1000px; margin:0 auto; position:relative; }
        .method-header { text-align:center; margin-bottom:3.5rem; }
        .method-eyebrow { font-size:0.72rem; font-weight:700; text-transform:uppercase; letter-spacing:0.2em; color:var(--coral-light); margin-bottom:1rem; }
        .method h2 { font-family:var(--serif); font-size:clamp(1.8rem,3.5vw,3rem); font-weight:700; line-height:1.15; color:#fff; }
        .method h2 em { font-style:italic; color:var(--coral-light); }
        .method-sub { font-size:0.95rem; color:rgba(255,255,255,0.65); margin-top:0.8rem; }
        .rituals { display:grid; grid-template-columns:repeat(2,1fr); gap:1.2rem; margin-bottom:3rem; }
        .ritual { background:rgba(255,255,255,0.04); border:1px solid rgba(255,255,255,0.08); border-radius:12px; padding:2rem; display:flex; gap:1.2rem; align-items:flex-start; transition:all 0.3s; }
        .ritual:hover { background:rgba(255,255,255,0.07); border-color:rgba(224,122,95,0.25); transform:translateY(-3px); }
        .ritual-icon { width:46px; height:46px; min-width:46px; background:rgba(255,255,255,0.06); border-radius:10px; display:flex; align-items:center; justify-content:center; font-size:1.3rem; }
        .ritual-tag { font-size:0.7rem; font-weight:700; text-transform:uppercase; letter-spacing:0.08em; color:var(--coral-light); margin-bottom:0.3rem; }
        .ritual h4 { font-family:var(--serif); font-size:1.2rem; font-weight:700; color:#fff; margin-bottom:0.5rem; }
        .ritual p { font-size:0.84rem; color:rgba(255,255,255,0.75); line-height:1.6; }
        .phases { background:rgba(255,255,255,0.04); border:1px solid rgba(255,255,255,0.08); border-radius:12px; overflow:hidden; }
        .phase { display:grid; grid-template-columns:80px 1fr; border-bottom:1px solid rgba(255,255,255,0.05); }
        .phase:last-child { border-bottom:none; }
        .phase-badge { background:rgba(27,54,93,0.6); color:var(--coral-light); display:flex; align-items:center; justify-content:center; font-family:var(--serif); font-size:0.88rem; font-weight:700; letter-spacing:0.04em; padding:1.2rem 0.5rem; text-align:center; }
        .phase:nth-child(1) .phase-badge { background:rgba(224,122,95,0.2); }
        .phase-content { padding:1.2rem 1.6rem; }
        .phase-when { font-size:0.7rem; font-weight:700; text-transform:uppercase; letter-spacing:0.08em; color:var(--coral-light); margin-bottom:0.2rem; }
        .phase-name { font-weight:700; font-size:0.95rem; color:#fff; margin-bottom:0.2rem; }
        .phase-desc { font-size:0.82rem; color:rgba(255,255,255,0.65); line-height:1.55; }

        /* ── ROI ─────────────────────────────── */
        .roi { padding:6rem 6%; }
        .roi-inner { max-width:900px; margin:0 auto; }
        .roi-header { margin-bottom:3rem; }
        .roi h2 { font-family:var(--serif); font-size:clamp(1.8rem,3.5vw,3rem); font-weight:700; line-height:1.15; color:var(--navy); }
        .roi h2 em { font-style:italic; color:var(--coral); }
        .roi-sub { font-size:0.97rem; color:#3d4f6b; margin-top:0.7rem; }
        .roi-calc { background:var(--navy-dark); border-radius:12px; padding:2.5rem; margin-bottom:1.5rem; position:relative; overflow:hidden; }
        .roi-calc::before { content:''; position:absolute; top:0; right:0; width:200px; height:200px; background:radial-gradient(circle, rgba(224,122,95,0.08) 0%, transparent 70%); }
        .roi-calc-tag { font-size:0.7rem; font-weight:700; text-transform:uppercase; letter-spacing:0.15em; color:rgba(255,255,255,0.55); margin-bottom:1.5rem; }
        .roi-equation { display:grid; grid-template-columns:1fr auto 1fr auto 1fr; gap:0.8rem; align-items:center; margin-bottom:1.5rem; }
        .roi-eq-block { background:rgba(255,255,255,0.05); border:1px solid rgba(255,255,255,0.07); border-radius:8px; padding:1.2rem; text-align:center; }
        .roi-eq-num { font-family:var(--serif); font-size:1.8rem; font-weight:700; color:#fff; line-height:1; }
        .roi-eq-label { font-size:0.72rem; color:rgba(255,255,255,0.6); margin-top:0.3rem; }
        .roi-eq-op { font-size:1.5rem; color:rgba(255,255,255,0.2); text-align:center; }
        .roi-eq-block.result { border-color:rgba(224,122,95,0.3); background:rgba(224,122,95,0.1); }
        .roi-eq-block.result .roi-eq-num { color:var(--coral-light); font-size:2.1rem; }
        .roi-footnote { font-size:0.68rem; color:rgba(255,255,255,0.45); }
        .roi-extras { display:grid; grid-template-columns:repeat(3,1fr); gap:1rem; }
        .roi-extra { background:#fff; border:1px solid rgba(27,54,93,0.08); border-radius:10px; padding:1.5rem; }
        .roi-extra-num { font-family:var(--serif); font-size:2rem; font-weight:700; color:var(--navy); line-height:1; }
        .roi-extra-text { font-size:0.8rem; color:#3d4f6b; margin-top:0.3rem; line-height:1.5; }
        .roi-extra-src { font-size:0.65rem; color:#8a9ab5; margin-top:0.4rem; }

        /* ── COMPARE ─────────────────────────── */
        .compare { padding:6rem 6%; background:var(--navy-dark); }
        .compare-inner { max-width:880px; margin:0 auto; }
        .compare-header { text-align:center; margin-bottom:3rem; }
        .compare-eyebrow { font-size:0.72rem; font-weight:700; text-transform:uppercase; letter-spacing:0.2em; color:var(--coral-light); margin-bottom:1rem; }
        .compare h2 { font-family:var(--serif); font-size:clamp(1.8rem,3.5vw,3rem); font-weight:700; line-height:1.15; color:#fff; }
        .compare h2 em { font-style:italic; color:var(--coral-light); }
        .compare-intro { font-size:0.95rem; color:rgba(255,255,255,0.6); margin-top:0.7rem; }
        .compare-wrap { border-radius:12px; overflow:hidden; box-shadow:0 8px 40px rgba(0,0,0,0.3); }
        table { width:100%; border-collapse:collapse; background:#fff; }
        thead th { padding:1rem 1.3rem; font-size:0.72rem; font-weight:700; text-transform:uppercase; letter-spacing:0.1em; text-align:left; }
        thead th:first-child { background:rgba(27,54,93,0.05); color:#4a5570; width:34%; }
        thead th:nth-child(2) { background:rgba(27,54,93,0.08); color:#4a5570; text-align:center; }
        thead th:nth-child(3) { background:var(--navy); color:#fff; text-align:center; position:relative; }
        thead th:nth-child(3)::after { content:''; position:absolute; bottom:0; left:0; right:0; height:2px; background:var(--coral); }
        tbody tr { border-bottom:1px solid rgba(27,54,93,0.06); transition:background 0.2s; }
        tbody tr:last-child { border-bottom:none; }
        tbody tr:hover { background:rgba(27,54,93,0.02); }
        td { padding:1rem 1.3rem; font-size:0.87rem; vertical-align:middle; }
        td:first-child { font-weight:600; color:var(--navy); background:rgba(27,54,93,0.02); }
        td:nth-child(2) { color:#4a5570; text-align:center; }
        td:nth-child(3) { font-weight:600; color:var(--navy); text-align:center; background:rgba(27,54,93,0.02); }
        .badge { display:inline-flex; align-items:center; gap:0.3rem; padding:0.28rem 0.75rem; border-radius:100px; font-size:0.77rem; font-weight:600; }
        .badge-no { background:rgba(0,0,0,0.04); color:#bbb; }
        .badge-no::before { content:'—'; }
        .badge-yes { background:rgba(224,122,95,0.12); color:var(--coral); border:1px solid rgba(224,122,95,0.25); }
        .badge-yes::before { content:'✓'; font-weight:700; }

        /* ── PRICING ─────────────────────────── */
        .pricing { padding:6rem 6%; }
        .pricing-inner { max-width:680px; margin:0 auto; text-align:center; }
        .pricing-eyebrow { font-size:0.72rem; font-weight:700; text-transform:uppercase; letter-spacing:0.2em; color:var(--coral); margin-bottom:1rem; }
        .pricing h2 { font-family:var(--serif); font-size:clamp(1.8rem,3.5vw,3rem); font-weight:700; color:var(--navy); margin-bottom:0.7rem; }
        .pricing h2 em { font-style:italic; color:var(--coral); }
        .pricing-sub { font-size:0.95rem; color:#3d4f6b; margin-bottom:2.5rem; }
        .pricing-card { background:#fff; border:1px solid rgba(27,54,93,0.1); border-radius:16px; padding:3rem 2.5rem; box-shadow:0 20px 60px rgba(27,54,93,0.08); position:relative; overflow:hidden; }
        .pricing-card::before { content:''; position:absolute; top:0; left:0; right:0; height:3px; background:linear-gradient(90deg, var(--coral), var(--coral-light)); }
        .pricing-badge { display:inline-block; background:rgba(224,122,95,0.1); border:1px solid rgba(224,122,95,0.25); color:var(--coral); font-size:0.72rem; font-weight:700; text-transform:uppercase; letter-spacing:0.1em; padding:0.3rem 0.9rem; border-radius:4px; margin-bottom:1.5rem; }
        .price { font-family:var(--serif); font-size:5.5rem; font-weight:700; line-height:1; color:var(--navy); }
        .price sup { font-size:0.35em; vertical-align:super; opacity:0.5; font-weight:400; }
        .price-detail { font-size:0.8rem; color:#3d4f6b; margin-top:0.3rem; margin-bottom:2rem; }
        .price-items { display:grid; grid-template-columns:1fr 1fr; gap:0.5rem 1.5rem; text-align:left; margin-bottom:2rem; }
        .price-item { display:flex; gap:0.5rem; align-items:flex-start; font-size:0.84rem; color:#4a5e7a; padding:0.25rem 0; }
        .price-check { color:var(--coral); font-weight:700; flex-shrink:0; }
        .btn-book { display:block; background:var(--coral); color:#fff; padding:1.1rem 2rem; border-radius:6px; text-decoration:none; font-size:0.97rem; font-weight:700; letter-spacing:0.02em; transition:all 0.3s; margin-bottom:0.8rem; }
        .btn-book:hover { background:#c9634a; transform:translateY(-2px); box-shadow:0 10px 30px rgba(224,122,95,0.35); }
        .book-note { font-size:0.75rem; color:#3d4f6b; }
        .guarantee { margin-top:1.8rem; padding:1.4rem 1.6rem; background:rgba(27,54,93,0.03); border:1px solid rgba(27,54,93,0.08); border-radius:8px; display:flex; gap:0.9rem; text-align:left; }
        .guarantee-icon { font-size:1.4rem; flex-shrink:0; }
        .guarantee-title { font-weight:700; font-size:0.9rem; color:var(--navy); margin-bottom:0.2rem; }
        .guarantee-text { font-size:0.8rem; color:#3d4f6b; line-height:1.6; }

        /* ── ABOUT ───────────────────────────── */
        .about { padding:6rem 6%; background:var(--navy-dark); }
        .about-inner { max-width:860px; margin:0 auto; display:grid; grid-template-columns:auto 1fr; gap:3.5rem; align-items:center; }
        .about-avatar { width:150px; height:150px; min-width:150px; border-radius:50%; background:rgba(255,255,255,0.05); border:2px solid rgba(184,176,164,0.3); display:flex; align-items:center; justify-content:center; font-family:var(--serif); font-style:italic; font-size:3rem; font-weight:300; color:var(--silver); }
        .about-eyebrow { font-size:0.72rem; font-weight:700; text-transform:uppercase; letter-spacing:0.2em; color:var(--coral-light); margin-bottom:1rem; }
        .about h3 { font-family:var(--serif); font-size:clamp(1.6rem,3vw,2.4rem); font-weight:700; line-height:1.2; color:#fff; margin-bottom:1rem; }
        .about h3 em { font-style:italic; color:var(--coral-light); }
        .about p { font-size:0.92rem; color:rgba(255,255,255,0.75); line-height:1.75; margin-bottom:0.8rem; }
        .about-tags { display:flex; flex-wrap:wrap; gap:0.5rem; margin-top:1.2rem; }
        .about-tag { background:rgba(255,255,255,0.05); border:1px solid rgba(255,255,255,0.1); padding:0.3rem 0.8rem; border-radius:4px; font-size:0.75rem; color:rgba(255,255,255,0.65); }
        .about-link { display:inline-flex; align-items:center; gap:0.4rem; color:var(--coral-light); font-size:0.85rem; font-weight:600; text-decoration:none; border-bottom:1px solid rgba(244,166,142,0.3); padding-bottom:2px; margin-top:1rem; transition:all 0.3s; }
        .about-link:hover { border-color:var(--coral-light); }

        /* ── FINALE ──────────────────────────── */
        .finale { padding:7rem 6%; text-align:center; position:relative; overflow:hidden; }
        .finale::before { content:''; position:absolute; inset:0; background:radial-gradient(ellipse 50% 60% at 50% 50%, rgba(224,122,95,0.05) 0%, transparent 70%); }
        .finale-inner { max-width:660px; margin:0 auto; position:relative; }
        .finale-ornament { font-family:var(--serif); font-size:7rem; line-height:0.6; color:rgba(224,122,95,0.12); display:block; margin-bottom:1.5rem; }
        .finale h2 { font-family:var(--serif); font-size:clamp(1.8rem,4vw,3.2rem); font-weight:700; font-style:italic; color:var(--navy); line-height:1.2; margin-bottom:1.2rem; }
        .finale h2 em { font-style:normal; color:var(--coral); }
        .finale-sub { font-size:1rem; color:#3d4f6b; margin-bottom:2.5rem; line-height:1.8; }
        .finale-sep { width:40px; height:1px; background:rgba(27,54,93,0.15); margin:2rem auto; }
        .finale-spots { display:flex; justify-content:center; gap:0.5rem; margin-bottom:0.6rem; }
        .f-spot { width:10px; height:10px; border-radius:50%; }
        .f-spot.gone { background:rgba(27,54,93,0.12); border:1px solid rgba(27,54,93,0.2); }
        .f-spot.open { background:var(--coral); }
        .finale-spots-txt { font-size:0.75rem; color:#3d4f6b; margin-bottom:2rem; }
        .finale-spots-txt strong { color:var(--coral); }
        .btn-finale { display:block; max-width:360px; margin:0 auto 1rem; background:var(--coral); color:#fff; padding:1.15rem 2rem; border-radius:6px; text-decoration:none; font-size:0.97rem; font-weight:700; text-align:center; transition:all 0.3s; }
        .btn-finale:hover { background:#c9634a; transform:translateY(-2px); box-shadow:0 10px 32px rgba(224,122,95,0.3); }
        .finale-note { font-size:0.75rem; color:#3d4f6b; }

        /* ── FOOTER ──────────────────────────── */
        footer { background:var(--navy-dark); padding:2rem 6%; display:flex; justify-content:space-between; align-items:center; flex-wrap:wrap; gap:1rem; border-top:1px solid rgba(255,255,255,0.05); }
        .footer-brand { font-family:var(--serif); font-style:italic; font-size:0.88rem; color:rgba(255,255,255,0.35); }
        .footer-contact { font-size:0.75rem; color:rgba(255,255,255,0.25); }
        .footer-contact a { color:rgba(255,255,255,0.4); text-decoration:none; }

        /* ── ANIMATIONS ──────────────────────── */
        @keyframes up { from{opacity:0;transform:translateY(24px)} to{opacity:1;transform:translateY(0)} }
        @keyframes fadein { from{opacity:0} to{opacity:1} }
        .reveal { opacity:0; transform:translateY(24px); transition:opacity .8s ease, transform .8s ease; }
        .reveal.visible { opacity:1; transform:translateY(0); }
        .d1{transition-delay:.1s} .d2{transition-delay:.2s} .d3{transition-delay:.3s}

        /* ── LANG SWITCH TRANSITION ──────────── */
        #lang-fr, #lang-en { transition: opacity 0.25s ease; }

        /* ── RESPONSIVE ──────────────────────── */
        @media (max-width:900px) {
            .stats-band-inner { grid-template-columns:1fr; gap:2rem; }
            .stats-grid { grid-template-columns:1fr 1fr; }
            .rituals { grid-template-columns:1fr; }
            .problem-traps { grid-template-columns:1fr; }
            .roi-equation { grid-template-columns:1fr; }
            .roi-eq-op { display:none; }
            .roi-extras { grid-template-columns:1fr; }
            .about-inner { grid-template-columns:1fr; text-align:center; }
            .about-tags { justify-content:center; }
            .about-avatar { margin:0 auto; }
        }
        @media (max-width:680px) {
            .hero h1 { font-size:2.2rem; }
            .hero-ornament { display:none; }
            .price-items { grid-template-columns:1fr; }
            thead th:nth-child(2), td:nth-child(2) { display:none; }
            footer { flex-direction:column; text-align:center; }
            .roi-extras { grid-template-columns:1fr 1fr; }
            .nav-right { gap:0.6rem; }
        }
        @media (max-width:420px) {
            .stats-grid { grid-template-columns:1fr; }
            .roi-extras { grid-template-columns:1fr; }
        }
    </style>
</head>
<body>

<!-- ═══ NAV (commun aux deux langues) ════════════ -->
<nav id="nav">
    <div class="nav-logo">Équilibre Performance</div>
    <div class="nav-right">
        <div class="lang-toggle" role="group" aria-label="Language selector">
            <button class="lang-btn active" id="btn-fr" onclick="setLang('fr')" aria-pressed="true">FR</button>
            <button class="lang-btn" id="btn-en" onclick="setLang('en')" aria-pressed="false">EN</button>
        </div>
        <a href="https://calendly.com/equilibre_performance/equilibreperformance" target="_blank" class="nav-cta" id="nav-cta-text">Diagnostic gratuit →</a>
    </div>
</nav>

<!-- ════════════════════════════════════════════════
     BLOC FRANÇAIS
     ════════════════════════════════════════════════ -->
<div id="lang-fr">

<section class="hero">
    <div class="hero-ornament">EP</div>
    <div class="hero-inner">
        <div class="eyebrow">
            <div class="eyebrow-line"></div>
            <div class="eyebrow-text">Pour DRH · Responsables Prévention · CEO</div>
        </div>
        <h1>
            Vous avez tout essayé.<br>
            <em>Ils partent quand même.</em>
            <span class="aside">Parce que la culture ne se construit pas lors d'un séminaire annuel — elle se pratique, chaque matin, dans le travail réel.</span>
        </h1>
        <p class="hero-quote">"On a refait les bureaux, instauré le télétravail, lancé une newsletter interne. Rien n'a changé en profondeur. Les gens restaient polis. Et ils partaient quand même."</p>
        <p class="hero-body">Ce que vous vivez a un nom : une <strong>culture cosmétique</strong>. Des gestes visibles qui n'entrent jamais dans les workflows quotidiens. En 3 semaines, j'installe 4 rituels opérationnels dans votre organisation — et je forme 2 ambassadeurs internes pour les faire vivre <strong>6 mois après mon départ.</strong></p>
        <div class="hero-actions">
            <a href="https://calendly.com/equilibre_performance/equilibreperformance" target="_blank" class="btn-cta">Réserver mon diagnostic gratuit <span class="btn-arrow">→</span></a>
            <div class="cta-meta"><strong>15 minutes · Zéro engagement</strong>Je vous dis si votre entreprise correspond au profil — ou pas.</div>
        </div>
        <div class="spots-row">
            <div class="spot gone"></div><div class="spot open"></div><div class="spot open"></div>
            <span class="spots-txt">Pilote 2026 — <strong>2 places restantes</strong> sur 3 · 1 500€ HTVA</span>
        </div>
    </div>
    <div class="scroll-down"><div class="scroll-line"></div>Voir les chiffres</div>
</section>

<section class="stats-band">
    <div class="stats-band-inner">
        <div class="stats-intro reveal">
            <h2>Ce que coûte le désengagement <em>dans votre bilan.</em></h2>
            <p>Ces chiffres concernent des entreprises belges ordinaires. Peut-être la vôtre.</p>
        </div>
        <div class="stats-grid">
            <div class="stat-box reveal d1"><div class="stat-num">80 000€</div><div class="stat-label">Coût annuel de l'absentéisme pour 50 collaborateurs</div><div class="stat-src">SD Worx 2024–2025</div></div>
            <div class="stat-box reveal d2"><div class="stat-num">+44%</div><div class="stat-label">D'arrêts longue durée en 5 ans en Belgique</div><div class="stat-src">VRT News / INAMI 2025</div></div>
            <div class="stat-box reveal d3"><div class="stat-num">×3</div><div class="stat-label">Meilleure rétention dans les entreprises à culture forte</div><div class="stat-src">Securex / Graydon 2024</div></div>
        </div>
    </div>
</section>

<section class="problem">
    <div class="problem-inner">
        <div class="section-label reveal"><div class="section-label-line"></div><div class="section-label-text">Ce qui ne fonctionne pas</div></div>
        <h2 class="reveal d1">On installe un babyfoot<br>et on s'étonne que les gens <em>démissionnent encore.</em></h2>
        <p class="problem-story reveal d1">"Super journée de team building en septembre. Deux mois plus tard, l'ambiance était exactement la même. On a dépensé 4 000€ pour un souvenir."</p>
        <p class="problem-body reveal d2">Les approches classiques partagent un point commun : elles se déroulent <strong>en dehors du travail réel.</strong> Un jour de séminaire ne change pas une habitude. Une conférence sur le bien-être n'ancre rien dans les workflows. Et quand le consultant repart, tout s'évapore en 6 semaines.</p>
        <p class="problem-body reveal d2">La culture se construit dans les micro-moments du quotidien — le lundi matin, la réunion de 9h, la pause de 15h. Pas dans une salle de séminaire.</p>
        <div class="problem-traps reveal d3">
            <div class="trap"><div class="trap-x">✗</div><div class="trap-text"><strong>Team buildings événementiels</strong> — bonne humeur 48h, zéro changement structurel</div></div>
            <div class="trap"><div class="trap-x">✗</div><div class="trap-text"><strong>Séminaires bien-être ponctuels</strong> — le consultant part, la culture reste identique</div></div>
            <div class="trap"><div class="trap-x">✗</div><div class="trap-text"><strong>Avantages en nature</strong> — frigo à smoothies, salle de sport : cosmétique</div></div>
            <div class="trap"><div class="trap-x">✗</div><div class="trap-text"><strong>Formations ponctuelles</strong> — sans ancrage dans les outils et workflows existants</div></div>
        </div>
    </div>
</section>

<section class="method">
    <div class="method-inner">
        <div class="method-header reveal">
            <div class="method-eyebrow">La méthode Équilibre Performance</div>
            <h2>4 rituels. <em>Dans vos workflows.</em><br>Pas en dehors.</h2>
            <p class="method-sub">Intégrés dans vos agendas, vos outils, votre organisation existante. Zéro disruption, impact immédiat.</p>
        </div>
        <div class="rituals">
            <div class="ritual reveal"><div class="ritual-icon">🏋️</div><div><div class="ritual-tag">10 min · Chaque matin</div><h4>Radio Taiso</h4><p>Pratiqué chez Toyota depuis 70 ans. 27 millions de Japonais quotidiennement. Zéro entreprise belge ne l'utilise encore — c'est précisément pourquoi ça crée une cohésion immédiate et mémorable dès le Jour 1.</p></div></div>
            <div class="ritual reveal d1"><div class="ritual-icon">⏸️</div><div><div class="ritual-tag">5-10 min · 2× par jour</div><h4>Pauses intelligentes (cycles 90 min)</h4><p>Le cerveau fonctionne par cycles ultrадiens de 90 minutes. Ignorer ces cycles coûte de la productivité. Les respecter avec étirements et respiration guidée : +15-20% de concentration mesurée.</p></div></div>
            <div class="ritual reveal d2"><div class="ritual-icon">📅</div><div><div class="ritual-tag">4h de formation · Intégré dans vos outils</div><h4>Time Blocking</h4><p>Formation pratique avec intégration directe dans vos calendriers Outlook, Teams ou Google. Résultat cible : 2 à 3 heures de travail profond récupérées par collaborateur, par jour.</p></div></div>
            <div class="ritual reveal d3"><div class="ritual-icon">🤝</div><div><div class="ritual-tag">6 mois · Suivi inclus</div><h4>Ambassadeurs internes</h4><p>Je forme 2 relais dans votre équipe. Ce sont eux qui pilotent les rituels après mon départ. Pas de dépendance consultante, pas de rechute. La culture devient autonome — c'est l'objectif.</p></div></div>
        </div>
        <div class="phases reveal">
            <div class="phase"><div class="phase-badge">Phase 0</div><div class="phase-content"><div class="phase-when">1 semaine avant démarrage</div><div class="phase-name">Diagnostic & co-construction</div><div class="phase-desc">Audit culture actuelle, identification des ambassadeurs, concertation avec DRH / Direction / Responsable Prévention. Mesure de base (engagement, absentéisme, productivité).</div></div></div>
            <div class="phase"><div class="phase-badge">S1–3</div><div class="phase-content"><div class="phase-when">3 semaines intensives · 1h/jour</div><div class="phase-name">Implémentation des 4 rituels</div><div class="phase-desc">Formation quotidienne sur site. Mise en place progressive des rituels dans les workflows. Mesures d'engagement avant/après. Ajustements en temps réel selon les retours terrain.</div></div></div>
            <div class="phase"><div class="phase-badge">M1–6</div><div class="phase-content"><div class="phase-when">6 mois · Check-ins mensuels</div><div class="phase-name">Consolidation par les ambassadeurs</div><div class="phase-desc">Suivi à J+30, J+60, J+120, J+180. Les ambassadeurs pilotent, j'accompagne à distance. Rapport final complet avec données avant/après — à vous de le valoriser en interne.</div></div></div>
        </div>
    </div>
</section>

<section class="roi">
    <div class="roi-inner">
        <div class="roi-header reveal">
            <div class="section-label"><div class="section-label-line"></div><div class="section-label-text">Impact financier</div></div>
            <h2>L'absentéisme vous coûte déjà.<br><em>La question, c'est combien.</em></h2>
            <p class="roi-sub">Calcul basé sur une cible de réduction de 20% de l'absentéisme — objectif réaliste sur 6 mois, pas une promesse.</p>
        </div>
        <div class="roi-calc reveal d1">
            <div class="roi-calc-tag">Pour une entreprise de 50 collaborateurs · Source SD Worx 2024</div>
            <div class="roi-equation">
                <div class="roi-eq-block"><div class="roi-eq-num">80 000€</div><div class="roi-eq-label">Coût absentéisme actuel/an</div></div>
                <div class="roi-eq-op">×</div>
                <div class="roi-eq-block"><div class="roi-eq-num">−20%</div><div class="roi-eq-label">Cible de réduction</div></div>
                <div class="roi-eq-op">=</div>
                <div class="roi-eq-block result"><div class="roi-eq-num">16 000€</div><div class="roi-eq-label">Économies potentielles/an</div></div>
            </div>
            <div class="roi-footnote">Investissement pilote : 1 500€ HTVA — soit un retour potentiel ×10. Ce sont des cibles transparentes, pas des garanties contractuelles.</div>
        </div>
        <div class="roi-extras reveal d2">
            <div class="roi-extra"><div class="roi-extra-num">+39%</div><div class="roi-extra-text">De productivité pour les équipes engagées vs désengagées</div><div class="roi-extra-src">Securex / Graydon 2024</div></div>
            <div class="roi-extra"><div class="roi-extra-num">+2–3h</div><div class="roi-extra-text">De travail productif récupérées par jour via time blocking</div><div class="roi-extra-src">Goldman Sachs / Yale</div></div>
            <div class="roi-extra"><div class="roi-extra-num">+15%</div><div class="roi-extra-text">De concentration mesurée avec les pauses intelligentes 90 min</div><div class="roi-extra-src">INRS / Applied Psychology</div></div>
        </div>
    </div>
</section>

<section class="compare">
    <div class="compare-inner">
        <div class="compare-header reveal">
            <div class="compare-eyebrow">La différence</div>
            <h2>Ce que les autres font.<br><em>Ce que je fais, moi.</em></h2>
            <p class="compare-intro">Pas pour critiquer — pour être honnête sur pourquoi certaines approches ne tiennent pas dans le temps.</p>
        </div>
        <div class="compare-wrap reveal d1">
            <table>
                <thead><tr><th>Critère</th><th>Approches classiques</th><th>Équilibre Performance</th></tr></thead>
                <tbody>
                    <tr><td>Durée réelle</td><td><span class="badge badge-no">1 à 2 jours</span></td><td><span class="badge badge-yes">3 semaines + 6 mois suivi</span></td></tr>
                    <tr><td>Ancrage après départ</td><td><span class="badge badge-no">Aucun</span></td><td><span class="badge badge-yes">2 ambassadeurs formés</span></td></tr>
                    <tr><td>Intégration workflows</td><td><span class="badge badge-no">En dehors du travail</span></td><td><span class="badge badge-yes">Dans le quotidien réel</span></td></tr>
                    <tr><td>Mesure avant / après</td><td><span class="badge badge-no">Rarement</span></td><td><span class="badge badge-yes">Données J1 → J180</span></td></tr>
                    <tr><td>Risque financier</td><td><span class="badge badge-no">Budget engagé sans filet</span></td><td><span class="badge badge-yes">Sortie Jour 3, 50% remboursé</span></td></tr>
                    <tr><td>Effet dans le temps</td><td><span class="badge badge-no">Éphémère (6–8 semaines)</span></td><td><span class="badge badge-yes">Culture auto-entretenue</span></td></tr>
                    <tr><td>Dépendance consultante</td><td><span class="badge badge-no">Souvent, pour renouveler</span></td><td><span class="badge badge-yes">Zéro — vous êtes autonomes</span></td></tr>
                </tbody>
            </table>
        </div>
    </div>
</section>

<section class="pricing">
    <div class="pricing-inner">
        <div class="pricing-eyebrow reveal">Investissement & retour sur investissement</div>
        <h2 class="reveal d1">Tout inclus.<br><em>Zéro risque.</em></h2>
        <p class="pricing-sub reveal d2">L'absentéisme vous coûte déjà. La question n'est pas de savoir si vous pouvez vous permettre d'investir — c'est de savoir combien vous perdez chaque mois à ne rien faire.</p>
        <div class="pricing-card reveal d1" style="margin-bottom:1.2rem;">
            <div style="display:flex;justify-content:space-between;align-items:flex-start;flex-wrap:wrap;gap:1rem;margin-bottom:1.2rem;">
                <div>
                    <div class="pricing-badge" style="background:rgba(27,54,93,0.06);border-color:rgba(27,54,93,0.15);color:var(--navy);">Tarif entreprise</div>
                    <div style="font-family:var(--serif);font-size:1rem;color:#3d4f6b;margin-top:0.5rem;">Investissement HTVA</div>
                    <div class="price" style="font-size:3.5rem;margin-top:0.2rem;"><sup>€</sup>4 500<span style="font-size:0.3em;font-weight:400;color:var(--silver);vertical-align:middle;"> et +</span></div>
                    <div class="price-detail">selon la taille de l'entreprise</div>
                </div>
                <div style="display:flex;flex-direction:column;gap:0.7rem;min-width:220px;">
                    <div style="display:flex;align-items:center;gap:0.6rem;font-size:0.84rem;color:#3d4f6b;"><span style="color:var(--coral);font-weight:700;">✓</span> Retour sur investissement mesuré à J+180</div>
                    <div style="display:flex;align-items:center;gap:0.6rem;font-size:0.84rem;color:#3d4f6b;"><span style="color:var(--coral);font-weight:700;">✓</span> Garantie Jour 3 — 50% remboursé si ça ne colle pas</div>
                </div>
            </div>
        </div>
        <div class="pricing-card reveal d2">
            <div class="pricing-badge">Tarif partenaire pilote 2026 · 3 places</div>
            <div style="display:flex;align-items:baseline;gap:1rem;flex-wrap:wrap;margin-bottom:0.3rem;">
                <div class="price"><sup>€</sup>1 500</div>
                <div style="font-family:var(--serif);font-size:1.3rem;color:rgba(27,54,93,0.3);text-decoration:line-through;">4 500€</div>
            </div>
            <div class="price-detail">HTVA · Par entreprise · Tout inclus · Aucun frais caché</div>
            <div style="display:flex;align-items:center;gap:0.5rem;margin:1.2rem 0;padding:0.8rem 1rem;background:rgba(224,122,95,0.06);border:1px solid rgba(224,122,95,0.2);border-radius:6px;">
                <div style="display:flex;gap:0.4rem;"><div class="spot gone"></div><div class="spot open"></div><div class="spot open"></div></div>
                <span style="font-size:0.82rem;color:#3d4f6b;"><strong style="color:var(--coral);">3 places disponibles</strong> — Pilote 2026</span>
            </div>
            <div class="price-items">
                <div class="price-item"><span class="price-check">✓</span> Diagnostic culture (1 semaine avant)</div>
                <div class="price-item"><span class="price-check">✓</span> 3 semaines sur site · 1h/jour</div>
                <div class="price-item"><span class="price-check">✓</span> Formation 2 ambassadeurs internes</div>
                <div class="price-item"><span class="price-check">✓</span> Tous outils, templates & supports</div>
                <div class="price-item"><span class="price-check">✓</span> 6 mois de check-ins mensuels</div>
                <div class="price-item"><span class="price-check">✓</span> Rapport final données avant / après</div>
            </div>
            <div style="margin-bottom:1.5rem;padding:1rem 1.2rem;background:rgba(27,54,93,0.03);border:1px solid rgba(27,54,93,0.08);border-radius:8px;">
                <div style="font-size:0.72rem;font-weight:700;text-transform:uppercase;letter-spacing:0.1em;color:var(--silver);margin-bottom:0.7rem;">Contreparties partenaire pilote</div>
                <div style="display:grid;grid-template-columns:1fr 1fr;gap:0.4rem;">
                    <div style="display:flex;gap:0.5rem;font-size:0.82rem;color:#3d4f6b;"><span style="color:var(--navy);font-weight:600;">→</span> Accès direct aux équipes</div>
                    <div style="display:flex;gap:0.5rem;font-size:0.82rem;color:#3d4f6b;"><span style="color:var(--navy);font-weight:600;">→</span> Participation active direction</div>
                    <div style="display:flex;gap:0.5rem;font-size:0.82rem;color:#3d4f6b;"><span style="color:var(--navy);font-weight:600;">→</span> Feedback honnête J+21 et J+180</div>
                    <div style="display:flex;gap:0.5rem;font-size:0.82rem;color:#3d4f6b;"><span style="color:var(--navy);font-weight:600;">→</span> Témoignage client en fin de mission</div>
                </div>
            </div>
            <a href="https://calendly.com/equilibre_performance/equilibreperformance" target="_blank" class="btn-book">→ Discutons-en — Diagnostic gratuit</a>
            <p class="book-note">15 minutes · Zéro engagement · Je vous dis franchement si ça correspond</p>
            <div class="guarantee">
                <div class="guarantee-icon">🛡️</div>
                <div><div class="guarantee-title">Garantie Jour 3 — Risque zéro</div><div class="guarantee-text">Après 3 jours, si la méthode ne convient pas à votre organisation : vous résiliez. 50% remboursé immédiatement. Vous conservez tous les outils, formations et supports reçus. Aucune question posée.</div></div>
            </div>
        </div>
    </div>
</section>

<section class="about">
    <div class="about-inner">
        <div class="about-avatar reveal">MM</div>
        <div class="reveal d1">
            <div class="about-eyebrow">Marjorie Mathieu</div>
            <h3>Je ne théorise pas.<br>Je <em>m'immerge.</em></h3>
            <p>15 ans dans des environnements corporate exigeants — BNP Paribas, Serco Europe, KONE, STIB — m'ont appris une chose : les séminaires s'oublient, les habitudes restent. C'est pour ça que je ne fais pas de conférences. Je viens dans vos bureaux, je forme vos équipes, et je construis avec vous une culture qui tient.</p>
            <p>Mon approche combine rigueur opérationnelle et rituels collectifs éprouvés. Du concret intégré dans vos outils existants — pas de la théorie sur slides, pas de jargon bien-être. Des résultats mesurables, avec données avant/après transparentes.</p>
            <div class="about-tags">
                <span class="about-tag">BNP Paribas · Serco · KONE · STIB</span>
                <span class="about-tag">15 ans corporate</span>
                <span class="about-tag">10+ ans pratique & enseignement</span>
                <span class="about-tag">Formatrice IA — Kitchy Agency</span>
                <span class="about-tag">Smart Coop · Ath, Hainaut</span>
            </div>
            <a href="https://www.linkedin.com/in/equilibreperformance/" target="_blank" class="about-link">Mon parcours complet sur LinkedIn →</a>
        </div>
    </div>
</section>

<section class="finale">
    <div class="finale-inner">
        <span class="finale-ornament reveal">"</span>
        <h2 class="reveal d1">La culture ne se décrète pas.<br>Elle se <em>pratique, chaque matin.</em></h2>
        <p class="finale-sub reveal d2">15 minutes pour voir si votre organisation est prête. Je vous dis franchement ce que j'observe — et si le pilote a du sens pour vous. Sans argumentaire de vente. Sans engagement.</p>
        <div class="finale-sep reveal"></div>
        <div class="finale-spots reveal"><div class="f-spot gone"></div><div class="f-spot open"></div><div class="f-spot open"></div></div>
        <p class="finale-spots-txt reveal"><strong>2 places disponibles</strong> sur 3 — Pilote 2026 · 1 500€ HTVA</p>
        <a href="https://calendly.com/equilibre_performance/equilibreperformance" target="_blank" class="btn-finale reveal d2">→ Réserver mon diagnostic gratuit</a>
        <p class="finale-note reveal d3">15 minutes · Zéro engagement · Diagnostic offert</p>
    </div>
</section>

<footer>
    <div class="footer-brand">Marjorie Mathieu — Équilibre Performance</div>
    <div class="footer-contact"><a href="mailto:hello@marjoriemathieu.be">hello@marjoriemathieu.be</a> · +32 477 09 18 03 · Ath, Hainaut — Belgique</div>
</footer>

</div><!-- /lang-fr -->


<!-- ════════════════════════════════════════════════
     BLOC ANGLAIS
     ════════════════════════════════════════════════ -->
<div id="lang-en" style="display:none">

<section class="hero">
    <div class="hero-ornament">EP</div>
    <div class="hero-inner">
        <div class="eyebrow">
            <div class="eyebrow-line"></div>
            <div class="eyebrow-text">For HR Directors · Prevention Managers · CEOs</div>
        </div>
        <h1>
            You've tried everything.<br>
            <em>They still leave.</em>
            <span class="aside">Because company culture isn't built at an annual offsite — it's practised every morning, inside the work itself.</span>
        </h1>
        <p class="hero-quote">"We refurbished the offices, introduced remote work, launched an internal newsletter. Nothing changed at a deeper level. People stayed polite. And they left anyway."</p>
        <p class="hero-body">What you're experiencing has a name: <strong>cosmetic culture</strong>. Visible gestures that never make it into daily workflows. In 3 weeks, I install 4 operational rituals inside your organisation — and train 2 internal ambassadors to sustain them <strong>6 months after I leave.</strong></p>
        <div class="hero-actions">
            <a href="https://calendly.com/equilibre_performance/equilibreperformance" target="_blank" class="btn-cta">Book my free diagnostic <span class="btn-arrow">→</span></a>
            <div class="cta-meta"><strong>15 minutes · Zero commitment</strong>I'll tell you honestly whether your company fits the profile — or not.</div>
        </div>
        <div class="spots-row">
            <div class="spot gone"></div><div class="spot open"></div><div class="spot open"></div>
            <span class="spots-txt">2026 Pilot — <strong>2 spots remaining</strong> out of 3 · €1,500 excl. VAT</span>
        </div>
    </div>
    <div class="scroll-down"><div class="scroll-line"></div>See the numbers</div>
</section>

<section class="stats-band">
    <div class="stats-band-inner">
        <div class="stats-intro reveal">
            <h2>What disengagement costs <em>on your balance sheet.</em></h2>
            <p>These figures apply to ordinary Belgian companies. Possibly yours.</p>
        </div>
        <div class="stats-grid">
            <div class="stat-box reveal d1"><div class="stat-num">€80,000</div><div class="stat-label">Annual absenteeism cost for 50 employees</div><div class="stat-src">SD Worx 2024–2025</div></div>
            <div class="stat-box reveal d2"><div class="stat-num">+44%</div><div class="stat-label">Increase in long-term sick leave in Belgium over 5 years</div><div class="stat-src">VRT News / INAMI 2025</div></div>
            <div class="stat-box reveal d3"><div class="stat-num">×3</div><div class="stat-label">Better talent retention in strong-culture organisations</div><div class="stat-src">Securex / Graydon 2024</div></div>
        </div>
    </div>
</section>

<section class="problem">
    <div class="problem-inner">
        <div class="section-label reveal"><div class="section-label-line"></div><div class="section-label-text">What doesn't work</div></div>
        <h2 class="reveal d1">You install a foosball table<br>and wonder why people <em>keep resigning.</em></h2>
        <p class="problem-story reveal d1">"Great team-building day in September. Two months later, the atmosphere was exactly the same. We spent €4,000 on a memory."</p>
        <p class="problem-body reveal d2">Classic approaches share one thing in common: they happen <strong>outside of real work.</strong> A seminar day doesn't change a habit. A wellbeing talk doesn't anchor anything into workflows. And when the consultant leaves, it all evaporates within 6 weeks.</p>
        <p class="problem-body reveal d2">Culture is built in the micro-moments of daily life — Monday morning, the 9am meeting, the 3pm break. Not in a seminar room.</p>
        <div class="problem-traps reveal d3">
            <div class="trap"><div class="trap-x">✗</div><div class="trap-text"><strong>One-off team buildings</strong> — good mood for 48h, zero structural change</div></div>
            <div class="trap"><div class="trap-x">✗</div><div class="trap-text"><strong>Standalone wellbeing seminars</strong> — the consultant leaves, culture stays the same</div></div>
            <div class="trap"><div class="trap-x">✗</div><div class="trap-text"><strong>Perks and benefits</strong> — smoothie fridge, gym access: cosmetic at best</div></div>
            <div class="trap"><div class="trap-x">✗</div><div class="trap-text"><strong>Isolated training sessions</strong> — no anchor in existing tools and daily workflows</div></div>
        </div>
    </div>
</section>

<section class="method">
    <div class="method-inner">
        <div class="method-header reveal">
            <div class="method-eyebrow">The Équilibre Performance Method</div>
            <h2>4 rituals. <em>Inside your workflows.</em><br>Not around them.</h2>
            <p class="method-sub">Integrated into your calendars, your tools, your existing organisation. Zero disruption, immediate impact.</p>
        </div>
        <div class="rituals">
            <div class="ritual reveal"><div class="ritual-icon">🏋️</div><div><div class="ritual-tag">10 min · Every morning</div><h4>Radio Taiso</h4><p>Practised at Toyota for 70 years. 27 million Japanese daily. Zero Belgian company uses it yet — which is precisely why it creates immediate, memorable team cohesion from Day 1.</p></div></div>
            <div class="ritual reveal d1"><div class="ritual-icon">⏸️</div><div><div class="ritual-tag">5-10 min · 2× per day</div><h4>Smart breaks (90-min cycles)</h4><p>The brain operates on 90-minute ultradian cycles. Ignoring these cycles costs productivity. Respecting them with guided stretching and breathing: +15–20% measured concentration.</p></div></div>
            <div class="ritual reveal d2"><div class="ritual-icon">📅</div><div><div class="ritual-tag">4h training · Integrated into your tools</div><h4>Time Blocking</h4><p>Hands-on training with direct integration into your Outlook, Teams, or Google calendars. Target outcome: 2 to 3 hours of deep work recovered per employee, per day.</p></div></div>
            <div class="ritual reveal d3"><div class="ritual-icon">🤝</div><div><div class="ritual-tag">6 months · Follow-up included</div><h4>Internal Ambassadors</h4><p>I train 2 internal relays within your team. They run the rituals after I leave. No consultant dependency, no relapse. Culture becomes self-sustaining — that's the goal.</p></div></div>
        </div>
        <div class="phases reveal">
            <div class="phase"><div class="phase-badge">Phase 0</div><div class="phase-content"><div class="phase-when">1 week before kick-off</div><div class="phase-name">Diagnostic & co-design</div><div class="phase-desc">Culture audit, ambassador identification, alignment with HR / Management / Prevention. Baseline measurement (engagement, absenteeism, productivity).</div></div></div>
            <div class="phase"><div class="phase-badge">W1–3</div><div class="phase-content"><div class="phase-when">3 intensive weeks · 1h/day</div><div class="phase-name">Implementation of the 4 rituals</div><div class="phase-desc">Daily on-site training. Progressive rollout of rituals into real workflows. Before/after engagement measurements. Real-time adjustments based on team feedback.</div></div></div>
            <div class="phase"><div class="phase-badge">M1–6</div><div class="phase-content"><div class="phase-when">6 months · Monthly check-ins</div><div class="phase-name">Consolidation by ambassadors</div><div class="phase-desc">Follow-up at D+30, D+60, D+120, D+180. Ambassadors lead, I support remotely. Full final report with before/after data — yours to leverage internally.</div></div></div>
        </div>
    </div>
</section>

<section class="roi">
    <div class="roi-inner">
        <div class="roi-header reveal">
            <div class="section-label"><div class="section-label-line"></div><div class="section-label-text">Financial impact</div></div>
            <h2>Absenteeism is already costing you.<br><em>The question is how much.</em></h2>
            <p class="roi-sub">Calculation based on a 20% absenteeism reduction target — a realistic 6-month objective, not a promise.</p>
        </div>
        <div class="roi-calc reveal d1">
            <div class="roi-calc-tag">For a company of 50 employees · Source: SD Worx 2024</div>
            <div class="roi-equation">
                <div class="roi-eq-block"><div class="roi-eq-num">€80,000</div><div class="roi-eq-label">Current annual absenteeism cost</div></div>
                <div class="roi-eq-op">×</div>
                <div class="roi-eq-block"><div class="roi-eq-num">−20%</div><div class="roi-eq-label">Reduction target</div></div>
                <div class="roi-eq-op">=</div>
                <div class="roi-eq-block result"><div class="roi-eq-num">€16,000</div><div class="roi-eq-label">Potential annual savings</div></div>
            </div>
            <div class="roi-footnote">Pilot investment: €1,500 excl. VAT — a potential ×10 return. These are transparent targets, not contractual guarantees.</div>
        </div>
        <div class="roi-extras reveal d2">
            <div class="roi-extra"><div class="roi-extra-num">+39%</div><div class="roi-extra-text">Higher productivity in engaged vs disengaged teams</div><div class="roi-extra-src">Securex / Graydon 2024</div></div>
            <div class="roi-extra"><div class="roi-extra-num">+2–3h</div><div class="roi-extra-text">Of productive work recovered per day through time blocking</div><div class="roi-extra-src">Goldman Sachs / Yale</div></div>
            <div class="roi-extra"><div class="roi-extra-num">+15%</div><div class="roi-extra-text">Measured concentration improvement with 90-min smart breaks</div><div class="roi-extra-src">INRS / Applied Psychology</div></div>
        </div>
    </div>
</section>

<section class="compare">
    <div class="compare-inner">
        <div class="compare-header reveal">
            <div class="compare-eyebrow">The difference</div>
            <h2>What others do.<br><em>What I do.</em></h2>
            <p class="compare-intro">Not to criticise — but to be honest about why certain approaches don't hold over time.</p>
        </div>
        <div class="compare-wrap reveal d1">
            <table>
                <thead><tr><th>Criterion</th><th>Standard approaches</th><th>Équilibre Performance</th></tr></thead>
                <tbody>
                    <tr><td>Actual duration</td><td><span class="badge badge-no">1 to 2 days</span></td><td><span class="badge badge-yes">3 weeks + 6-month follow-up</span></td></tr>
                    <tr><td>Anchoring after departure</td><td><span class="badge badge-no">None</span></td><td><span class="badge badge-yes">2 trained ambassadors</span></td></tr>
                    <tr><td>Workflow integration</td><td><span class="badge badge-no">Outside of real work</span></td><td><span class="badge badge-yes">Inside daily operations</span></td></tr>
                    <tr><td>Before / after measurement</td><td><span class="badge badge-no">Rarely</span></td><td><span class="badge badge-yes">Data from D1 to D180</span></td></tr>
                    <tr><td>Financial risk</td><td><span class="badge badge-no">Budget committed, no safety net</span></td><td><span class="badge badge-yes">Day 3 exit, 50% refunded</span></td></tr>
                    <tr><td>Long-term effect</td><td><span class="badge badge-no">Short-lived (6–8 weeks)</span></td><td><span class="badge badge-yes">Self-sustaining culture</span></td></tr>
                    <tr><td>Consultant dependency</td><td><span class="badge badge-no">Often, to renew</span></td><td><span class="badge badge-yes">Zero — you're autonomous</span></td></tr>
                </tbody>
            </table>
        </div>
    </div>
</section>

<section class="pricing">
    <div class="pricing-inner">
        <div class="pricing-eyebrow reveal">Investment & return on investment</div>
        <h2 class="reveal d1">All-inclusive.<br><em>Zero risk.</em></h2>
        <p class="pricing-sub reveal d2">Absenteeism is already costing you. The question isn't whether you can afford to invest — it's how much you're losing every month by doing nothing.</p>
        <div class="pricing-card reveal d1" style="margin-bottom:1.2rem;">
            <div style="display:flex;justify-content:space-between;align-items:flex-start;flex-wrap:wrap;gap:1rem;margin-bottom:1.2rem;">
                <div>
                    <div class="pricing-badge" style="background:rgba(27,54,93,0.06);border-color:rgba(27,54,93,0.15);color:var(--navy);">Standard rate</div>
                    <div style="font-family:var(--serif);font-size:1rem;color:#3d4f6b;margin-top:0.5rem;">Investment excl. VAT</div>
                    <div class="price" style="font-size:3.5rem;margin-top:0.2rem;"><sup>€</sup>4,500<span style="font-size:0.3em;font-weight:400;color:var(--silver);vertical-align:middle;"> and up</span></div>
                    <div class="price-detail">depending on company size</div>
                </div>
                <div style="display:flex;flex-direction:column;gap:0.7rem;min-width:220px;">
                    <div style="display:flex;align-items:center;gap:0.6rem;font-size:0.84rem;color:#3d4f6b;"><span style="color:var(--coral);font-weight:700;">✓</span> Return on investment measured at D+180</div>
                    <div style="display:flex;align-items:center;gap:0.6rem;font-size:0.84rem;color:#3d4f6b;"><span style="color:var(--coral);font-weight:700;">✓</span> Day 3 guarantee — 50% refunded if it's not the right fit</div>
                </div>
            </div>
        </div>
        <div class="pricing-card reveal d2">
            <div class="pricing-badge">2026 Pilot Partner rate · 3 spots</div>
            <div style="display:flex;align-items:baseline;gap:1rem;flex-wrap:wrap;margin-bottom:0.3rem;">
                <div class="price"><sup>€</sup>1,500</div>
                <div style="font-family:var(--serif);font-size:1.3rem;color:rgba(27,54,93,0.3);text-decoration:line-through;">€4,500</div>
            </div>
            <div class="price-detail">Excl. VAT · Per company · All-inclusive · No hidden fees</div>
            <div style="display:flex;align-items:center;gap:0.5rem;margin:1.2rem 0;padding:0.8rem 1rem;background:rgba(224,122,95,0.06);border:1px solid rgba(224,122,95,0.2);border-radius:6px;">
                <div style="display:flex;gap:0.4rem;"><div class="spot gone"></div><div class="spot open"></div><div class="spot open"></div></div>
                <span style="font-size:0.82rem;color:#3d4f6b;"><strong style="color:var(--coral);">3 spots available</strong> — 2026 Pilot</span>
            </div>
            <div class="price-items">
                <div class="price-item"><span class="price-check">✓</span> Culture diagnostic (1 week before)</div>
                <div class="price-item"><span class="price-check">✓</span> 3 weeks on-site · 1h/day</div>
                <div class="price-item"><span class="price-check">✓</span> Training of 2 internal ambassadors</div>
                <div class="price-item"><span class="price-check">✓</span> All tools, templates & materials</div>
                <div class="price-item"><span class="price-check">✓</span> 6 months of monthly check-ins</div>
                <div class="price-item"><span class="price-check">✓</span> Final report with before / after data</div>
            </div>
            <div style="margin-bottom:1.5rem;padding:1rem 1.2rem;background:rgba(27,54,93,0.03);border:1px solid rgba(27,54,93,0.08);border-radius:8px;">
                <div style="font-size:0.72rem;font-weight:700;text-transform:uppercase;letter-spacing:0.1em;color:var(--silver);margin-bottom:0.7rem;">Pilot partner commitments</div>
                <div style="display:grid;grid-template-columns:1fr 1fr;gap:0.4rem;">
                    <div style="display:flex;gap:0.5rem;font-size:0.82rem;color:#3d4f6b;"><span style="color:var(--navy);font-weight:600;">→</span> Direct access to teams</div>
                    <div style="display:flex;gap:0.5rem;font-size:0.82rem;color:#3d4f6b;"><span style="color:var(--navy);font-weight:600;">→</span> Active management participation</div>
                    <div style="display:flex;gap:0.5rem;font-size:0.82rem;color:#3d4f6b;"><span style="color:var(--navy);font-weight:600;">→</span> Honest feedback at D+21 and D+180</div>
                    <div style="display:flex;gap:0.5rem;font-size:0.82rem;color:#3d4f6b;"><span style="color:var(--navy);font-weight:600;">→</span> Client testimonial at end of programme</div>
                </div>
            </div>
            <a href="https://calendly.com/equilibre_performance/equilibreperformance" target="_blank" class="btn-book">→ Let's talk — Free diagnostic</a>
            <p class="book-note">15 minutes · Zero commitment · I'll tell you honestly whether it's the right fit</p>
            <div class="guarantee">
                <div class="guarantee-icon">🛡️</div>
                <div><div class="guarantee-title">Day 3 Guarantee — Zero risk</div><div class="guarantee-text">After 3 days, if the method doesn't suit your organisation: you exit. 50% refunded immediately. You keep all tools, training materials, and resources received. No questions asked.</div></div>
            </div>
        </div>
    </div>
</section>

<section class="about">
    <div class="about-inner">
        <div class="about-avatar reveal">MM</div>
        <div class="reveal d1">
            <div class="about-eyebrow">Marjorie Mathieu</div>
            <h3>I don't theorise.<br>I <em>get inside.</em></h3>
            <p>15 years in demanding corporate environments — BNP Paribas, Serco Europe, KONE, STIB — taught me one thing: seminars are forgotten, habits stay. That's why I don't give talks. I come to your offices, I train your teams, and I build with you a culture that holds.</p>
            <p>My approach combines operational rigour with proven collective rituals. Concrete methods integrated into your existing tools — no theory on slides, no wellness jargon. Measurable results, with transparent before/after data.</p>
            <div class="about-tags">
                <span class="about-tag">BNP Paribas · Serco · KONE · STIB</span>
                <span class="about-tag">15 years corporate</span>
                <span class="about-tag">10+ years practice & teaching</span>
                <span class="about-tag">AI Trainer — Kitchy Agency</span>
                <span class="about-tag">Smart Coop · Ath, Hainaut</span>
            </div>
            <a href="https://www.linkedin.com/in/equilibreperformance/" target="_blank" class="about-link">My full background on LinkedIn →</a>
        </div>
    </div>
</section>

<section class="finale">
    <div class="finale-inner">
        <span class="finale-ornament reveal">"</span>
        <h2 class="reveal d1">Culture can't be decreed.<br>It is <em>practised, every morning.</em></h2>
        <p class="finale-sub reveal d2">15 minutes to see if your organisation is ready. I'll tell you frankly what I observe — and whether the pilot makes sense for you. No sales pitch. No commitment.</p>
        <div class="finale-sep reveal"></div>
        <div class="finale-spots reveal"><div class="f-spot gone"></div><div class="f-spot open"></div><div class="f-spot open"></div></div>
        <p class="finale-spots-txt reveal"><strong>2 spots available</strong> out of 3 — 2026 Pilot · €1,500 excl. VAT</p>
        <a href="https://calendly.com/equilibre_performance/equilibreperformance" target="_blank" class="btn-finale reveal d2">→ Book my free diagnostic</a>
        <p class="finale-note reveal d3">15 minutes · Zero commitment · Free diagnostic</p>
    </div>
</section>

<footer>
    <div class="footer-brand">Marjorie Mathieu — Équilibre Performance</div>
    <div class="footer-contact"><a href="mailto:hello@marjoriemathieu.be">hello@marjoriemathieu.be</a> · +32 477 09 18 03 · Ath, Hainaut — Belgium</div>
</footer>

</div><!-- /lang-en -->

<script>
    // ── LANGUAGE SWITCHER ──────────────────────────
    function setLang(lang) {
        const fr = document.getElementById('lang-fr');
        const en = document.getElementById('lang-en');
        const btnFr = document.getElementById('btn-fr');
        const btnEn = document.getElementById('btn-en');
        const navCta = document.getElementById('nav-cta-text');
        const html = document.documentElement;

        if (lang === 'en') {
            fr.style.opacity = '0';
            setTimeout(() => {
                fr.style.display = 'none';
                en.style.display = 'block';
                setTimeout(() => { en.style.opacity = '1'; }, 10);
            }, 200);
            btnFr.classList.remove('active');
            btnEn.classList.add('active');
            btnFr.setAttribute('aria-pressed', 'false');
            btnEn.setAttribute('aria-pressed', 'true');
            navCta.textContent = 'Free diagnostic →';
            html.setAttribute('lang', 'en');
            document.title = 'Équilibre Performance — 2026 Pilot Programme';
        } else {
            en.style.opacity = '0';
            setTimeout(() => {
                en.style.display = 'none';
                fr.style.display = 'block';
                setTimeout(() => { fr.style.opacity = '1'; }, 10);
            }, 200);
            btnEn.classList.remove('active');
            btnFr.classList.add('active');
            btnEn.setAttribute('aria-pressed', 'false');
            btnFr.setAttribute('aria-pressed', 'true');
            navCta.textContent = 'Diagnostic gratuit →';
            html.setAttribute('lang', 'fr');
            document.title = 'Équilibre Performance — Pilote 2026';
        }

        window.scrollTo({ top: 0, behavior: 'smooth' });

        // Re-trigger scroll reveal for newly visible elements
        setTimeout(() => {
            document.querySelectorAll('.reveal:not(.visible)').forEach(el => obs.observe(el));
        }, 300);
    }

    // ── SCROLL REVEAL ──────────────────────────────
    const obs = new IntersectionObserver(entries => {
        entries.forEach(e => { if (e.isIntersecting) e.target.classList.add('visible'); });
    }, { threshold: 0.08, rootMargin: '0px 0px -30px 0px' });
    document.querySelectorAll('.reveal').forEach(el => obs.observe(el));

    // ── NAV SHADOW ─────────────────────────────────
    window.addEventListener('scroll', () => {
        document.getElementById('nav').style.boxShadow =
            window.scrollY > 50 ? '0 4px 20px rgba(27,54,93,0.1)' : 'none';
    });
</script>
</body>
</html>
