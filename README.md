<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Momentum 180 — Pilote 2026</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link href="https://fonts.googleapis.com/css2?family=Lora:ital,wght@0,400;0,500;0,600;0,700;1,400;1,500;1,600;1,700&family=Jost:wght@300;400;500;600&display=swap" rel="stylesheet">
    <style>
        :root {
            --navy:       #1B365D;
            --navy-dark:  #151c3a;
            --coral:      #E07A5F;
            --coral-light:#f4a68e;
            --silver:     #6B6560;
            --silver-on-dark: #c8c2bc;
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
            background-color: #ffffff;
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
            background: radial-gradient(ellipse 70% 80% at 70% 40%,
                rgba(224,122,95,0.06) 0%, transparent 70%);
            pointer-events:none;
        }
        .hero-ornament {
            position:absolute; right:4%; top:50%;
            transform:translateY(-50%);
            font-family: var(--serif);
            font-size: clamp(160px,20vw,280px);
            font-weight:700; font-style:italic;
            color: rgba(27,54,93,0.03);
            line-height:1; pointer-events:none; user-select:none;
        }
        .hero-inner { max-width:760px; position:relative; z-index:1; }

        .eyebrow {
            display:flex; align-items:center; gap:0.8rem;
            margin-bottom:2rem;
            opacity:0; animation: up 0.9s ease 0.2s forwards;
        }
        .eyebrow-line { width:28px; height:1px; background:var(--coral); }
        .eyebrow-text {
            font-size:0.72rem; font-weight:700;
            text-transform:uppercase; letter-spacing:0.2em; color:var(--coral);
        }

        .hero h1 {
            font-family: var(--serif);
            font-size: clamp(2.6rem,5.5vw,4.8rem);
            font-weight:700; line-height:1.08;
            color: var(--navy);
            margin-bottom:2rem;
            opacity:0; animation: up 1s ease 0.35s forwards;
        }
        .hero h1 em { font-style:italic; color:var(--coral); }
        .hero h1 .aside {
            display:block;
            font-size:0.48em; font-weight:400; font-style:italic;
            color:var(--silver); margin-top:0.5em; line-height:1.5;
        }

        .hero-quote {
            font-family:var(--serif); font-style:italic;
            font-size:1.1rem; color:#4a5e7a;
            border-left:2px solid var(--coral);
            padding-left:1.4rem;
            max-width:540px; margin-bottom:1.5rem; line-height:1.8;
            opacity:0; animation: up 1s ease 0.5s forwards;
        }

        .hero-body {
            font-size:0.97rem; color:#3d4f6b;
            max-width:500px; margin-bottom:2.8rem; line-height:1.75;
            opacity:0; animation: up 1s ease 0.65s forwards;
        }
        .hero-body strong { color:var(--navy); font-weight:600; }

        .hero-actions {
            display:flex; align-items:center; gap:1.5rem; flex-wrap:wrap;
            opacity:0; animation: up 1s ease 0.8s forwards;
        }
        .btn-cta {
            display:inline-flex; align-items:center; gap:0.6rem;
            background:var(--coral); color:#fff;
            padding:1rem 2rem; border-radius:4px;
            font-size:0.92rem; font-weight:700;
            text-decoration:none; letter-spacing:0.01em;
            transition:all 0.3s;
        }
        .btn-cta:hover { background:#c9634a; transform:translateY(-2px); box-shadow:0 8px 28px rgba(224,122,95,0.3); }
        .btn-arrow { transition:transform 0.3s; }
        .btn-cta:hover .btn-arrow { transform:translateX(4px); }

        .cta-meta {
            font-size:0.78rem; color:#3d4f6b; line-height:1.5;
        }
        .cta-meta strong { color:var(--navy); font-weight:600; display:block; }

        .spots-row {
            display:flex; align-items:center; gap:0.5rem;
            margin-top:1.8rem;
            opacity:0; animation: up 1s ease 0.95s forwards;
        }
        .spot { width:9px; height:9px; border-radius:50%; }
        .spot.open  { background:var(--coral); }
        .spots-txt { font-size:0.75rem; color:#3d4f6b; margin-left:0.3rem; }
        .spots-txt strong { color:var(--coral); }

        .scroll-down {
            position:absolute; bottom:2.5rem; left:6%;
            display:flex; align-items:center; gap:0.7rem;
            font-size:0.7rem; text-transform:uppercase; letter-spacing:0.15em; color:#3d4f6b;
            opacity:0; animation: fadein 1s ease 1.4s forwards;
        }
        .scroll-line {
            width:30px; height:1px; background:#3d4f6b;
            animation: pulse 2s ease infinite;
        }
        @keyframes pulse { 0%,100%{width:30px;opacity:.4} 50%{width:50px;opacity:.9} }

        /* ── CHIFFRES (dark band) ────────────── */
        .stats-band {
            background: var(--navy-dark);
            padding: 4rem 6%;
            position:relative; overflow:hidden;
        }
        .stats-band::before {
            content:'';
            position:absolute; inset:0;
            background: radial-gradient(ellipse 60% 80% at 85% 50%, rgba(224,122,95,0.07) 0%, transparent 70%);
        }
        .stats-band-inner {
            max-width:1000px; margin:0 auto;
            display:grid; grid-template-columns:1.2fr 2fr;
            gap:3rem; align-items:center; position:relative;
        }
        .stats-intro h2 {
            font-family:var(--serif);
            font-size:clamp(1.6rem,3vw,2.4rem);
            font-weight:600; font-style:italic;
            color:#fff; line-height:1.3;
        }
        .stats-intro h2 em { font-style:normal; color:var(--coral-light); }
        .stats-intro p {
            font-size:0.88rem; color:rgba(255,255,255,0.6);
            margin-top:0.8rem; line-height:1.7;
        }
        .stats-intro .stats-note {
            font-size:0.75rem; color:rgba(255,255,255,0.4);
            margin-top:1.2rem; line-height:1.6;
            border-top:1px solid rgba(255,255,255,0.08);
            padding-top:1rem;
        }
        .stats-grid {
            display:grid; grid-template-columns:repeat(2,1fr); gap:1rem;
        }
        .stat-box {
            background:rgba(255,255,255,0.04);
            border:1px solid rgba(255,255,255,0.08);
            border-radius:10px; padding:1.5rem 1.2rem;
            transition:all 0.3s;
        }
        .stat-box:hover { background:rgba(255,255,255,0.07); transform:translateY(-3px); }
        .stat-num {
            font-family:var(--serif);
            font-size:2.3rem; font-weight:700;
            color:var(--coral-light); line-height:1;
            margin-bottom:0.4rem;
        }
        .stat-label { font-size:0.8rem; color:rgba(255,255,255,0.6); line-height:1.5; }
        .stat-src   { font-size:0.65rem; color:rgba(255,255,255,0.25); margin-top:0.4rem; }

        /* ── CALCULATEUR ─────────────────────── */
        .calculator {
            padding: 6rem 6%;
            background: #f8f7f5;
        }
        .calculator-inner { max-width: 860px; margin: 0 auto; }
        .calculator-header { margin-bottom: 3rem; }
        .calculator-header h2 {
            font-family: var(--serif);
            font-size: clamp(1.8rem, 3.5vw, 3rem);
            font-weight: 700; line-height: 1.15; color: var(--navy);
            margin-bottom: 0.7rem;
        }
        .calculator-header h2 em { font-style: italic; color: var(--coral); }
        .calculator-header p { font-size: 0.97rem; color: #3d4f6b; line-height: 1.7; }

        .calc-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 1.5rem;
            margin-bottom: 1.5rem;
        }
        .calc-field {
            display: flex;
            flex-direction: column;
            gap: 0.5rem;
        }
        .calc-field label {
            font-size: 0.78rem;
            font-weight: 700;
            text-transform: uppercase;
            letter-spacing: 0.1em;
            color: var(--navy);
        }
        .calc-field .field-hint {
            font-size: 0.72rem;
            color: #6b7fa0;
            margin-top: -0.3rem;
        }
        .calc-field input[type="range"] {
            -webkit-appearance: none;
            appearance: none;
            width: 100%;
            height: 4px;
            border-radius: 2px;
            background: #dde3ed;
            outline: none;
            cursor: pointer;
        }
        .calc-field input[type="range"]::-webkit-slider-thumb {
            -webkit-appearance: none;
            appearance: none;
            width: 20px; height: 20px;
            border-radius: 50%;
            background: var(--coral);
            cursor: pointer;
            border: 3px solid white;
            box-shadow: 0 1px 6px rgba(224,122,95,0.4);
            transition: transform 0.15s;
        }
        .calc-field input[type="range"]::-webkit-slider-thumb:hover { transform: scale(1.15); }
        .calc-field input[type="range"]::-moz-range-thumb {
            width: 20px; height: 20px;
            border-radius: 50%;
            background: var(--coral);
            cursor: pointer;
            border: 3px solid white;
        }
        .range-val {
            font-family: var(--serif);
            font-size: 1.9rem;
            font-weight: 700;
            color: var(--navy);
            line-height: 1;
        }
        .range-unit {
            font-size: 0.75rem;
            color: #6b7fa0;
            margin-top: 2px;
        }

        .calc-select {
            padding: 0.7rem 1rem;
            border: 1px solid rgba(27,54,93,0.15);
            border-radius: 6px;
            font-family: var(--sans);
            font-size: 0.9rem;
            color: var(--navy);
            background: white;
            cursor: pointer;
            outline: none;
            appearance: none;
            background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='12' height='8' viewBox='0 0 12 8'%3E%3Cpath d='M1 1l5 5 5-5' stroke='%231B365D' stroke-width='1.5' fill='none' stroke-linecap='round'/%3E%3C/svg%3E");
            background-repeat: no-repeat;
            background-position: right 12px center;
            padding-right: 2rem;
        }

        .calc-loi-banner {
            background: rgba(224,122,95,0.08);
            border: 1px solid rgba(224,122,95,0.25);
            border-radius: 8px;
            padding: 1rem 1.2rem;
            font-size: 0.82rem;
            color: #5a3328;
            line-height: 1.6;
            margin-bottom: 1.5rem;
        }
        .calc-loi-banner strong { color: var(--coral); }

        .calc-result {
            background: var(--navy-dark);
            border-radius: 14px;
            padding: 2.5rem;
            position: relative;
            overflow: hidden;
        }
        .calc-result::before {
            content: '';
            position: absolute; inset: 0;
            background: radial-gradient(ellipse 60% 60% at 90% 10%, rgba(224,122,95,0.1) 0%, transparent 70%);
            pointer-events: none;
        }
        .calc-result-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 1.2rem;
            margin-bottom: 2rem;
        }
        .calc-res-block {
            background: rgba(255,255,255,0.05);
            border: 1px solid rgba(255,255,255,0.07);
            border-radius: 10px;
            padding: 1.2rem 1rem;
        }
        .calc-res-block.highlight {
            background: rgba(224,122,95,0.15);
            border-color: rgba(224,122,95,0.3);
        }
        .calc-res-label {
            font-size: 0.7rem;
            font-weight: 700;
            text-transform: uppercase;
            letter-spacing: 0.08em;
            color: rgba(255,255,255,0.45);
            margin-bottom: 0.5rem;
            line-height: 1.4;
        }
        .calc-res-val {
            font-family: var(--serif);
            font-size: 1.9rem;
            font-weight: 700;
            color: white;
            line-height: 1;
        }
        .calc-res-block.highlight .calc-res-val { color: var(--coral-light); font-size: 2.2rem; }
        .calc-res-sub {
            font-size: 0.72rem;
            color: rgba(255,255,255,0.4);
            margin-top: 0.3rem;
            line-height: 1.4;
        }

        .calc-roi-bar {
            margin-top: 1.5rem;
        }
        .calc-roi-bar-label {
            display: flex;
            justify-content: space-between;
            font-size: 0.75rem;
            color: rgba(255,255,255,0.55);
            margin-bottom: 0.5rem;
        }
        .calc-roi-track {
            background: rgba(255,255,255,0.08);
            border-radius: 4px;
            height: 8px;
            overflow: hidden;
        }
        .calc-roi-fill {
            height: 100%;
            border-radius: 4px;
            background: linear-gradient(90deg, var(--coral), var(--coral-light));
            transition: width 0.6s cubic-bezier(0.4, 0, 0.2, 1);
            width: 0%;
        }

        .calc-verdict {
            margin-top: 1.5rem;
            padding: 1rem 1.2rem;
            background: rgba(255,255,255,0.04);
            border-left: 2px solid var(--coral);
            border-radius: 0 6px 6px 0;
            font-size: 0.88rem;
            color: rgba(255,255,255,0.8);
            line-height: 1.6;
            font-style: italic;
        }
        .calc-cta {
            margin-top: 1.5rem;
            display: flex;
            align-items: center;
            gap: 1.2rem;
            flex-wrap: wrap;
        }
        .calc-cta a {
            display: inline-flex;
            align-items: center;
            gap: 0.5rem;
            background: var(--coral);
            color: white;
            padding: 0.8rem 1.6rem;
            border-radius: 4px;
            text-decoration: none;
            font-size: 0.88rem;
            font-weight: 700;
            transition: all 0.3s;
        }
        .calc-cta a:hover { background: #c9634a; transform: translateY(-1px); }
        .calc-cta-note {
            font-size: 0.75rem;
            color: rgba(255,255,255,0.4);
            line-height: 1.5;
        }

        /* ── PROBLÈME (narrative) ────────────── */
        .problem { padding: 6rem 6%; }
        .problem-inner { max-width:820px; margin:0 auto; }
        .section-label {
            display:flex; align-items:center; gap:0.7rem;
            margin-bottom:1.8rem;
        }
        .section-label-line { width:28px; height:1px; background:var(--coral); }
        .section-label-text {
            font-size:0.72rem; font-weight:700;
            text-transform:uppercase; letter-spacing:0.2em; color:var(--coral);
        }
        .problem h2 {
            font-family:var(--serif);
            font-size:clamp(1.8rem,3.5vw,3rem);
            font-weight:700; line-height:1.15;
            color:var(--navy); margin-bottom:1.5rem;
        }
        .problem h2 em { font-style:italic; color:var(--coral); }
        .problem-story {
            font-family:var(--serif); font-style:italic;
            font-size:1.1rem; color:#4a5e7a;
            border-left:2px solid var(--silver);
            padding-left:1.4rem;
            margin-bottom:2rem; line-height:1.8;
        }
        .problem-body {
            font-size:0.97rem; color:#3d4f6b;
            line-height:1.75; margin-bottom:1rem;
        }
        .problem-body strong { color:var(--navy); font-weight:600; }
        .problem-chains {
            margin-top:2rem; margin-bottom:2rem;
            display:grid; grid-template-columns:1fr 1fr; gap:1rem;
        }
        .chain {
            background:#fff;
            border:1px solid rgba(27,54,93,0.08);
            border-top:2px solid var(--coral);
            border-radius:8px; padding:1.2rem 1.4rem;
        }
        .chain-label {
            font-size:0.68rem; font-weight:700; text-transform:uppercase;
            letter-spacing:0.1em; color:var(--coral); margin-bottom:0.6rem;
        }
        .chain-text { font-size:0.84rem; color:#3d4f6b; line-height:1.7; }
        .chain-text strong { color:var(--navy); }
        .problem-traps {
            display:grid; grid-template-columns:1fr 1fr;
            gap:0.8rem; margin-top:2.5rem;
        }
        .trap {
            display:flex; gap:0.8rem; align-items:flex-start;
            padding:1rem 1.2rem;
            background:#fff;
            border:1px solid rgba(27,54,93,0.08);
            border-radius:8px;
        }
        .trap-x { color:rgba(27,54,93,0.2); font-size:1rem; flex-shrink:0; margin-top:2px; }
        .trap-text { font-size:0.84rem; color:#3d4f6b; line-height:1.5; }
        .trap-text strong { color:var(--navy); }

        /* ── MÉTHODE ─────────────────────────── */
        .method {
            background: var(--navy-dark);
            padding: 6rem 6%;
            position:relative; overflow:hidden;
        }
        .method::before {
            content:'';
            position:absolute; inset:0;
            background: radial-gradient(ellipse 50% 60% at 10% 80%, rgba(224,122,95,0.06) 0%, transparent 70%);
        }
        .method-inner { max-width:1000px; margin:0 auto; position:relative; }
        .method-header { text-align:center; margin-bottom:3.5rem; }
        .method-eyebrow {
            font-size:0.72rem; font-weight:700; text-transform:uppercase;
            letter-spacing:0.2em; color:var(--coral-light); margin-bottom:1rem;
        }
        .method h2 {
            font-family:var(--serif);
            font-size:clamp(1.8rem,3.5vw,3rem);
            font-weight:700; line-height:1.15; color:#fff;
        }
        .method h2 em { font-style:italic; color:var(--coral-light); }
        .method-sub {
            font-size:0.95rem; color:rgba(255,255,255,0.65);
            margin-top:0.8rem;
        }
        .rituals {
            display:grid; grid-template-columns:repeat(2,1fr); gap:1.2rem;
            margin-bottom:3rem;
        }
        .ritual {
            background:rgba(255,255,255,0.04);
            border:1px solid rgba(255,255,255,0.08);
            border-radius:12px; padding:2rem;
            display:flex; gap:1.2rem; align-items:flex-start;
            transition:all 0.3s;
        }
        .ritual:hover { background:rgba(255,255,255,0.07); border-color:rgba(224,122,95,0.25); transform:translateY(-3px); }
        .ritual-icon {
            width:46px; height:46px; min-width:46px;
            background:rgba(255,255,255,0.06);
            border-radius:10px;
            display:flex; align-items:center; justify-content:center;
            font-size:1.3rem;
        }
        .ritual-tag {
            font-size:0.7rem; font-weight:700; text-transform:uppercase;
            letter-spacing:0.08em; color:var(--coral-light); margin-bottom:0.3rem;
        }
        .ritual h4 {
            font-family:var(--serif); font-size:1.2rem; font-weight:700;
            color:#fff; margin-bottom:0.5rem;
        }
        .ritual p { font-size:0.84rem; color:rgba(255,255,255,0.75); line-height:1.6; }

        .phases {
            background:rgba(255,255,255,0.04);
            border:1px solid rgba(255,255,255,0.08);
            border-radius:12px; overflow:hidden;
        }
        .phase {
            display:grid; grid-template-columns:80px 1fr;
            border-bottom:1px solid rgba(255,255,255,0.05);
        }
        .phase:last-child { border-bottom:none; }
        .phase-badge {
            background:rgba(27,54,93,0.6);
            color:var(--coral-light);
            display:flex; align-items:center; justify-content:center;
            font-family:var(--serif); font-size:0.88rem; font-weight:700;
            letter-spacing:0.04em; padding:1.2rem 0.5rem; text-align:center;
        }
        .phase:nth-child(1) .phase-badge { background:rgba(224,122,95,0.2); }
        .phase-content { padding:1.2rem 1.6rem; }
        .phase-when {
            font-size:0.7rem; font-weight:700; text-transform:uppercase;
            letter-spacing:0.08em; color:var(--coral-light); margin-bottom:0.2rem;
        }
        .phase-name { font-weight:700; font-size:0.95rem; color:#fff; margin-bottom:0.2rem; }
        .phase-desc { font-size:0.82rem; color:rgba(255,255,255,0.65); line-height:1.55; }

        /* ── ROI ─────────────────────────────── */
        .roi { padding:6rem 6%; }
        .roi-inner { max-width:900px; margin:0 auto; }
        .roi-header { margin-bottom:3rem; }
        .roi h2 {
            font-family:var(--serif);
            font-size:clamp(1.8rem,3.5vw,3rem);
            font-weight:700; line-height:1.15; color:var(--navy);
        }
        .roi h2 em { font-style:italic; color:var(--coral); }
        .roi-sub { font-size:0.97rem; color:#3d4f6b; margin-top:0.7rem; }

        .roi-calc {
            background:var(--navy-dark);
            border-radius:12px; padding:2.5rem;
            margin-bottom:1.5rem; position:relative; overflow:hidden;
        }
        .roi-calc::before {
            content:'';
            position:absolute; top:0; right:0;
            width:200px; height:200px;
            background:radial-gradient(circle, rgba(224,122,95,0.08) 0%, transparent 70%);
        }
        .roi-calc-tag {
            font-size:0.7rem; font-weight:700; text-transform:uppercase;
            letter-spacing:0.15em; color:rgba(255,255,255,0.55); margin-bottom:1.5rem;
        }
        .roi-equation {
            display:grid; grid-template-columns:1fr auto 1fr auto 1fr;
            gap:0.8rem; align-items:center; margin-bottom:1.5rem;
        }
        .roi-eq-block {
            background:rgba(255,255,255,0.05);
            border:1px solid rgba(255,255,255,0.07);
            border-radius:8px; padding:1.2rem; text-align:center;
        }
        .roi-eq-num {
            font-family:var(--serif); font-size:1.8rem;
            font-weight:700; color:#fff; line-height:1;
        }
        .roi-eq-label { font-size:0.72rem; color:rgba(255,255,255,0.6); margin-top:0.3rem; }
        .roi-eq-op { font-size:1.5rem; color:rgba(255,255,255,0.2); text-align:center; }
        .roi-eq-block.result {
            border-color:rgba(224,122,95,0.3);
            background:rgba(224,122,95,0.1);
        }
        .roi-eq-block.result .roi-eq-num { color:var(--coral-light); font-size:2.1rem; }
        .roi-footnote { font-size:0.68rem; color:rgba(255,255,255,0.45); }

        .roi-extras {
            display:grid; grid-template-columns:repeat(3,1fr); gap:1rem;
        }
        .roi-extra {
            background:#fff;
            border:1px solid rgba(27,54,93,0.08);
            border-radius:10px; padding:1.5rem;
        }
        .roi-extra-num {
            font-family:var(--serif); font-size:2rem;
            font-weight:700; color:var(--navy); line-height:1;
        }
        .roi-extra-text { font-size:0.8rem; color:#3d4f6b; margin-top:0.3rem; line-height:1.5; }
        .roi-extra-src  { font-size:0.65rem; color:#8a9ab5; margin-top:0.4rem; }

        /* ── TABLEAU COMPARATIF ──────────────── */
        .compare { padding:6rem 6%; background:var(--navy-dark); }
        .compare-inner { max-width:880px; margin:0 auto; }
        .compare-header { text-align:center; margin-bottom:3rem; }
        .compare-eyebrow {
            font-size:0.72rem; font-weight:700; text-transform:uppercase;
            letter-spacing:0.2em; color:var(--coral-light); margin-bottom:1rem;
        }
        .compare h2 {
            font-family:var(--serif);
            font-size:clamp(1.8rem,3.5vw,3rem);
            font-weight:700; line-height:1.15; color:#fff;
        }
        .compare h2 em { font-style:italic; color:var(--coral-light); }
        .compare-intro { font-size:0.95rem; color:rgba(255,255,255,0.6); margin-top:0.7rem; }

        .compare-wrap {
            border-radius:12px; overflow:hidden;
            box-shadow:0 8px 40px rgba(0,0,0,0.3);
        }
        table { width:100%; border-collapse:collapse; background:#fff; }
        thead th {
            padding:1rem 1.3rem;
            font-size:0.72rem; font-weight:700;
            text-transform:uppercase; letter-spacing:0.1em;
            text-align:left;
        }
        thead th:first-child  { background:rgba(27,54,93,0.05); color:#4a5570; width:34%; }
        thead th:nth-child(2) { background:rgba(27,54,93,0.08); color:#4a5570; text-align:center; }
        thead th:nth-child(3) { background:var(--navy); color:#fff; text-align:center; position:relative; }
        thead th:nth-child(3)::after {
            content:''; position:absolute; bottom:0; left:0; right:0;
            height:2px; background:var(--coral);
        }
        tbody tr { border-bottom:1px solid rgba(27,54,93,0.06); transition:background 0.2s; }
        tbody tr:last-child { border-bottom:none; }
        tbody tr:hover { background:rgba(27,54,93,0.02); }
        td { padding:1rem 1.3rem; font-size:0.87rem; vertical-align:middle; }
        td:first-child { font-weight:600; color:var(--navy); background:rgba(27,54,93,0.02); }
        td:nth-child(2){ color:#4a5570; text-align:center; }
        td:nth-child(3){ font-weight:600; color:var(--navy); text-align:center; background:rgba(27,54,93,0.02); }

        .badge {
            display:inline-flex; align-items:center; gap:0.3rem;
            padding:0.28rem 0.75rem; border-radius:100px;
            font-size:0.77rem; font-weight:600;
        }
        .badge-no  { background:rgba(0,0,0,0.04); color:#bbb; }
        .badge-no::before { content:'—'; }
        .badge-yes { background:rgba(224,122,95,0.12); color:var(--coral); border:1px solid rgba(224,122,95,0.25); }
        .badge-yes::before { content:'✓'; font-weight:700; }

        /* ── TARIF ───────────────────────────── */
        .pricing { padding:6rem 6%; }
        .pricing-inner { max-width:680px; margin:0 auto; text-align:center; }
        .pricing-eyebrow {
            font-size:0.72rem; font-weight:700; text-transform:uppercase;
            letter-spacing:0.2em; color:var(--coral); margin-bottom:1rem;
        }
        .pricing h2 {
            font-family:var(--serif);
            font-size:clamp(1.8rem,3.5vw,3rem);
            font-weight:700; color:var(--navy); margin-bottom:0.7rem;
        }
        .pricing h2 em { font-style:italic; color:var(--coral); }
        .pricing-sub { font-size:0.95rem; color:#3d4f6b; margin-bottom:2.5rem; }

        .pricing-card {
            background:#fff;
            border:1px solid rgba(27,54,93,0.1);
            border-radius:16px; padding:3rem 2.5rem;
            box-shadow:0 20px 60px rgba(27,54,93,0.08);
            position:relative; overflow:hidden;
        }
        .pricing-card::before {
            content:''; position:absolute; top:0; left:0; right:0;
            height:3px; background:linear-gradient(90deg, var(--coral), var(--coral-light));
        }
        .pricing-badge {
            display:inline-block;
            background:rgba(224,122,95,0.1);
            border:1px solid rgba(224,122,95,0.25);
            color:var(--coral); font-size:0.72rem; font-weight:700;
            text-transform:uppercase; letter-spacing:0.1em;
            padding:0.3rem 0.9rem; border-radius:4px; margin-bottom:1.5rem;
        }
        .price {
            font-family:var(--serif); font-size:5.5rem;
            font-weight:700; line-height:1; color:var(--navy);
        }
        .price sup { font-size:0.35em; vertical-align:super; opacity:0.5; font-weight:400; }
        .price-anchor {
            font-size:0.8rem;
            color:#8a9ab5;
            text-decoration:line-through;
            margin-bottom:0.1rem;
        }
        .price-detail { font-size:0.8rem; color:#3d4f6b; margin-top:0.3rem; margin-bottom:2rem; }
        .price-items {
            display:grid; grid-template-columns:1fr 1fr;
            gap:0.5rem 1.5rem; text-align:left; margin-bottom:2rem;
        }
        .price-item {
            display:flex; gap:0.5rem; align-items:flex-start;
            font-size:0.84rem; color:#4a5e7a; padding:0.25rem 0;
        }
        .price-check { color:var(--coral); font-weight:700; flex-shrink:0; }

        .btn-book {
            display:block;
            background:var(--coral); color:#fff;
            padding:1.1rem 2rem; border-radius:6px;
            text-decoration:none; font-size:0.97rem; font-weight:700;
            letter-spacing:0.02em; transition:all 0.3s;
            margin-bottom:0.8rem;
        }
        .btn-book:hover { background:#c9634a; transform:translateY(-2px); box-shadow:0 10px 30px rgba(224,122,95,0.35); }
        .book-note { font-size:0.75rem; color:#3d4f6b; }

        .counterparts {
            margin-top:1.8rem;
            padding:1.4rem 1.6rem;
            background:rgba(27,54,93,0.03);
            border:1px solid rgba(27,54,93,0.08);
            border-radius:8px;
            text-align:left;
        }
        .counterparts-title { font-weight:700; font-size:0.88rem; color:var(--navy); margin-bottom:0.6rem; }
        .counterparts-text  { font-size:0.8rem; color:#3d4f6b; line-height:1.7; }

        /* ── À PROPOS ────────────────────────── */
        .about { padding:6rem 6%; background:var(--navy-dark); }
        .about-inner {
            max-width:860px; margin:0 auto;
            display:grid; grid-template-columns:auto 1fr;
            gap:3.5rem; align-items:center;
        }
        .about-avatar {
            width:150px; height:150px; min-width:150px;
            border-radius:50%;
            background:rgba(255,255,255,0.05);
            border:2px solid rgba(184,176,164,0.3);
            display:flex; align-items:center; justify-content:center;
            font-family:var(--serif); font-style:italic;
            font-size:3rem; font-weight:300; color:var(--silver);
        }
        .about-eyebrow {
            font-size:0.72rem; font-weight:700; text-transform:uppercase;
            letter-spacing:0.2em; color:var(--coral-light); margin-bottom:1rem;
        }
        .about h3 {
            font-family:var(--serif);
            font-size:clamp(1.6rem,3vw,2.4rem);
            font-weight:700; line-height:1.2; color:#fff; margin-bottom:1rem;
        }
        .about h3 em { font-style:italic; color:var(--coral-light); }
        .about p { font-size:0.92rem; color:rgba(255,255,255,0.75); line-height:1.75; margin-bottom:0.8rem; }
        .about-tags {
            display:flex; flex-wrap:wrap; gap:0.5rem; margin-top:1.2rem;
        }
        .about-tag {
            background:rgba(255,255,255,0.05);
            border:1px solid rgba(255,255,255,0.1);
            padding:0.3rem 0.8rem; border-radius:4px;
            font-size:0.75rem; color:rgba(255,255,255,0.65);
        }
        .about-link {
            display:inline-flex; align-items:center; gap:0.4rem;
            color:var(--coral-light); font-size:0.85rem; font-weight:600;
            text-decoration:none; border-bottom:1px solid rgba(244,166,142,0.3);
            padding-bottom:2px; margin-top:1rem;
            transition:all 0.3s;
        }
        .about-link:hover { border-color:var(--coral-light); }

        /* ── OBJECTIONS ──────────────────────── */
        .objections { padding:6rem 6%; }
        .objections-inner { max-width:780px; margin:0 auto; }
        .objections h2 {
            font-family:var(--serif);
            font-size:clamp(1.6rem,3vw,2.4rem);
            font-weight:700; color:var(--navy);
            margin-bottom:2.5rem; line-height:1.2;
        }
        .objection { margin-bottom:2rem; padding-bottom:2rem; border-bottom:1px solid rgba(27,54,93,0.07); }
        .objection:last-child { border-bottom:none; margin-bottom:0; padding-bottom:0; }
        .objection-q {
            font-family:var(--serif); font-style:italic;
            font-size:1.05rem; color:var(--navy);
            margin-bottom:0.6rem; font-weight:600;
        }
        .objection-a { font-size:0.92rem; color:#3d4f6b; line-height:1.75; }
        .objection-a strong { color:var(--navy); }

        /* ── FINALE ──────────────────────────── */
        .finale {
            padding:7rem 6%;
            text-align:center;
            position:relative; overflow:hidden;
        }
        .finale::before {
            content:'';
            position:absolute; inset:0;
            background:radial-gradient(ellipse 50% 60% at 50% 50%, rgba(224,122,95,0.05) 0%, transparent 70%);
        }
        .finale-inner { max-width:660px; margin:0 auto; position:relative; }
        .finale-ornament {
            font-family:var(--serif); font-size:7rem; line-height:0.6;
            color:rgba(224,122,95,0.12); display:block; margin-bottom:1.5rem;
        }
        .finale h2 {
            font-family:var(--serif);
            font-size:clamp(1.8rem,4vw,3.2rem);
            font-weight:700; font-style:italic;
            color:var(--navy); line-height:1.2; margin-bottom:1.2rem;
        }
        .finale h2 em { font-style:normal; color:var(--coral); }
        .finale-sub {
            font-size:1rem; color:#3d4f6b;
            margin-bottom:2.5rem; line-height:1.8;
        }
        .finale-sep { width:40px; height:1px; background:rgba(27,54,93,0.15); margin:2rem auto; }
        .finale-spots {
            display:flex; justify-content:center; gap:0.5rem; margin-bottom:0.6rem;
        }
        .f-spot { width:10px; height:10px; border-radius:50%; }
        .f-spot.open { background:var(--coral); }
        .finale-spots-txt { font-size:0.75rem; color:#3d4f6b; margin-bottom:2rem; }
        .finale-spots-txt strong { color:var(--coral); }
        .btn-finale {
            display:block; max-width:380px; margin:0 auto 1rem;
            background:var(--coral); color:#fff;
            padding:1.15rem 2rem; border-radius:6px;
            text-decoration:none; font-size:0.97rem; font-weight:700;
            text-align:center; transition:all 0.3s;
        }
        .btn-finale:hover { background:#c9634a; transform:translateY(-2px); box-shadow:0 10px 32px rgba(224,122,95,0.3); }
        .finale-note { font-size:0.75rem; color:#3d4f6b; }

        /* ── FOOTER ──────────────────────────── */
        footer {
            background:var(--navy-dark);
            padding:2rem 6%;
            display:flex; justify-content:space-between; align-items:center;
            flex-wrap:wrap; gap:1rem;
            border-top:1px solid rgba(255,255,255,0.05);
        }
        .footer-brand {
            font-family:var(--serif); font-style:italic;
            font-size:0.88rem; color:rgba(255,255,255,0.35);
        }
        .footer-contact { font-size:0.75rem; color:rgba(255,255,255,0.25); }
        .footer-contact a { color:rgba(255,255,255,0.4); text-decoration:none; }

        /* ── ANIMATIONS ──────────────────────── */
        @keyframes up   { from{opacity:0;transform:translateY(24px)} to{opacity:1;transform:translateY(0)} }
        @keyframes fadein { from{opacity:0} to{opacity:1} }
        .reveal { opacity:0; transform:translateY(24px); transition:opacity .8s ease, transform .8s ease; }
        .reveal.visible { opacity:1; transform:translateY(0); }
        .d1 { transition-delay:.1s; }
        .d2 { transition-delay:.2s; }
        .d3 { transition-delay:.3s; }

        /* ── RESPONSIVE ──────────────────────── */
        @media (max-width:900px) {
            .stats-band-inner { grid-template-columns:1fr; gap:2rem; }
            .stats-grid { grid-template-columns:1fr 1fr; }
            .rituals { grid-template-columns:1fr; }
            .problem-traps { grid-template-columns:1fr; }
            .problem-chains { grid-template-columns:1fr; }
            .roi-equation { grid-template-columns:1fr; }
            .roi-eq-op { display:none; }
            .roi-extras { grid-template-columns:1fr; }
            .about-inner { grid-template-columns:1fr; text-align:center; }
            .about-tags { justify-content:center; }
            .about-avatar { margin:0 auto; }
            .calc-grid { grid-template-columns:1fr; }
            .calc-result-grid { grid-template-columns:1fr; }
        }
        @media (max-width:680px) {
            .hero h1 { font-size:2.2rem; }
            .hero-ornament { display:none; }
            .price-items { grid-template-columns:1fr; }
            thead th:nth-child(2), td:nth-child(2) { display:none; }
            footer { flex-direction:column; text-align:center; }
            .roi-extras { grid-template-columns:1fr 1fr; }
        }
        @media (max-width:420px) {
            .stats-grid { grid-template-columns:1fr; }
            .roi-extras { grid-template-columns:1fr; }
        }
    </style>
</head>
<body>

<!-- ═══ NAV ═══════════════════════════════════════ -->
<nav id="nav">
    <div class="nav-logo">Momentum 180</div>
    <a href="https://calendly.com/equilibre_performance/equilibreperformance" target="_blank" class="nav-cta">Diagnostic — 15 min →</a>
</nav>

<!-- ═══ HERO ══════════════════════════════════════ -->
<section class="hero">
    <div class="hero-ornament">180</div>
    <div class="hero-inner">

        <div class="eyebrow">
            <div class="eyebrow-line"></div>
            <div class="eyebrow-text">Programme pilote · Organisations 50–200 collaborateurs · Hainaut &amp; Wallonie</div>
        </div>

        <h1>
            Personne n'a conçu<br>
            <em>la journée de travail</em><br>
            dans votre entreprise.
            <span class="aside">Elle s'est juste imposée. Et chaque mois, vos équipes accumulent de la fatigue que personne ne voit — jusqu'au jour où l'arrêt maladie tombe.</span>
        </h1>

        <p class="hero-quote">
            Ce programme ne traite pas les absences. Il prévient les causes qui transforment la fatigue quotidienne en arrêt longue durée — le poste qui explose depuis 5 ans.
        </p>

        <p class="hero-body">
            4 routines opérationnelles intégrées dans vos workflows existants. 4 semaines sur site. 6 mois de consolidation. <strong>Résultats mesurés à J+180.</strong> La méthode reste quand je pars — zéro dépendance consultante.
        </p>

        <div class="hero-actions">
            <a href="https://calendly.com/equilibre_performance/equilibreperformance" target="_blank" class="btn-cta">
                15 minutes pour voir si ça correspond
                <span class="btn-arrow">→</span>
            </a>
            <div class="cta-meta">
                <strong>Pas un pitch. Un diagnostic honnête.</strong>
                Je vous dis franchement si votre organisation correspond au profil — ou pas.
            </div>
        </div>

        <div class="spots-row">
            <div class="spot open"></div>
            <div class="spot open"></div>
            <span class="spots-txt">Pilote 2026 — <strong>2 organisations partenaires</strong></span>
        </div>
    </div>

    <div class="scroll-down">
        <div class="scroll-line"></div>
        Voir les chiffres
    </div>
</section>

<!-- ═══ CHIFFRES ══════════════════════════════════ -->
<section class="stats-band">
    <div class="stats-band-inner">
        <div class="stats-intro reveal">
            <h2>Ce que coûtent les absences longue durée <em>dans votre bilan.</em></h2>
            <p>Ces chiffres concernent des organisations belges ordinaires. Peut-être la vôtre.</p>
            <p class="stats-note">Depuis janvier 2026 : les employeurs de 50+ travailleurs paient 30% des indemnités maladie des 2e et 3e mois d'incapacité. Le coût d'un arrêt longue durée ne se limite plus au salaire garanti.<br><em>Loi fédérale 1er janvier 2026 · SD Worx · Le Soir</em></p>
        </div>
        <div class="stats-grid">
            <div class="stat-box reveal d1">
                <div class="stat-num">165 425€</div>
                <div class="stat-label">Coût de l'absentéisme pour 100 ETP en Hainaut</div>
                <div class="stat-src">SD Worx 2025</div>
            </div>
            <div class="stat-box reveal d2">
                <div class="stat-num">+94%</div>
                <div class="stat-label">De burn-out en 6 ans en Belgique</div>
                <div class="stat-src">Mutualités Libres 2024</div>
            </div>
            <div class="stat-box reveal d1">
                <div class="stat-num">+44%</div>
                <div class="stat-label">D'arrêts longue durée en 5 ans (2018–2023)</div>
                <div class="stat-src">INAMI / VRT News 2025</div>
            </div>
            <div class="stat-box reveal d2">
                <div class="stat-num">40%</div>
                <div class="stat-label">Des travailleurs belges concernés par le risque de burn-out</div>
                <div class="stat-src">AG Insurance 2024</div>
            </div>
        </div>
    </div>
</section>

<!-- ═══ CALCULATEUR ROI ═══════════════════════════ -->
<section class="calculator" id="calculateur">
    <div class="calculator-inner">
        <div class="calculator-header reveal">
            <div class="section-label">
                <div class="section-label-line"></div>
                <div class="section-label-text">Calculateur de coût réel</div>
            </div>
            <h2>Combien vous coûte<br><em>l'absentéisme aujourd'hui ?</em></h2>
            <p>Ajustez les curseurs selon votre situation réelle. Les chiffres s'adaptent instantanément — basés sur les données SD Worx 2025 et la loi fédérale belge de janvier 2026.</p>
        </div>

        <div class="calc-loi-banner reveal d1">
            <strong>⚠ Loi fédérale du 1er janvier 2026 :</strong> Les employeurs de 50+ travailleurs paient désormais 30% des indemnités maladie des 2e et 3e mois d'incapacité. Ce calculateur intègre ce surcoût dans le total.
        </div>

        <div class="calc-grid reveal d2">
            <div class="calc-field">
                <label>Nombre de collaborateurs</label>
                <div class="field-hint">Effectif total de votre organisation</div>
                <div class="range-val" id="etp-val">75</div>
                <div class="range-unit">collaborateurs (ETP)</div>
                <input type="range" id="etp" min="10" max="300" step="5" value="75" oninput="updateCalc()">
            </div>
            <div class="calc-field">
                <label>Taux d'absentéisme actuel</label>
                <div class="field-hint">Moyenne belge : 6,9% (SD Worx 2025)</div>
                <div class="range-val" id="taux-val">6.9<span style="font-size:1.2rem">%</span></div>
                <div class="range-unit">du temps de travail</div>
                <input type="range" id="taux" min="2" max="18" step="0.1" value="6.9" oninput="updateCalc()">
            </div>
            <div class="calc-field">
                <label>Salaire brut mensuel moyen</label>
                <div class="field-hint">Moyenne belge : 3 650€ brut/mois</div>
                <div class="range-val" id="sal-val">3 650<span style="font-size:1.2rem">€</span></div>
                <div class="range-unit">brut / collaborateur / mois</div>
                <input type="range" id="sal" min="2000" max="7000" step="50" value="3650" oninput="updateCalc()">
            </div>
            <div class="calc-field">
                <label>Part d'arrêts longs (&gt;30 jours)</label>
                <div class="field-hint">Proportion des absences de longue durée</div>
                <div class="range-val" id="long-val">35<span style="font-size:1.2rem">%</span></div>
                <div class="range-unit">des absences sont des arrêts longs</div>
                <input type="range" id="long" min="10" max="70" step="5" value="35" oninput="updateCalc()">
            </div>
        </div>

        <div class="calc-result reveal d3">
            <div class="calc-result-grid">
                <div class="calc-res-block">
                    <div class="calc-res-label">Coût direct estimé / an</div>
                    <div class="calc-res-val" id="res-direct">—</div>
                    <div class="calc-res-sub">Salaires maintenus + remplacements</div>
                </div>
                <div class="calc-res-block">
                    <div class="calc-res-label">Surcoût loi 2026 / an</div>
                    <div class="calc-res-val" id="res-loi">—</div>
                    <div class="calc-res-sub">30% indemnités mois 2 et 3 (arrêts &gt;30j)</div>
                </div>
                <div class="calc-res-block highlight">
                    <div class="calc-res-label">Coût total estimé / an</div>
                    <div class="calc-res-val" id="res-total">—</div>
                    <div class="calc-res-sub">Impact réel sur votre bilan</div>
                </div>
            </div>

            <div class="calc-roi-bar">
                <div class="calc-roi-bar-label">
                    <span>Investissement Momentum 180 (3 000€)</span>
                    <span id="res-roi-pct">—</span>
                </div>
                <div class="calc-roi-track">
                    <div class="calc-roi-fill" id="roi-fill"></div>
                </div>
            </div>

            <div class="calc-verdict" id="res-verdict">
                Ajustez les curseurs pour voir votre situation.
            </div>

            <div class="calc-cta">
                <a href="https://calendly.com/equilibre_performance/equilibreperformance" target="_blank">
                    → Discuter de ces chiffres — 15 min
                </a>
                <div class="calc-cta-note">
                    Je vous dis si une réduction de 20% est réaliste pour votre organisation.<br>
                    Pas un pitch — un diagnostic honnête.
                </div>
            </div>
        </div>
    </div>
</section>

<!-- ═══ PROBLÈME ══════════════════════════════════ -->
<section class="problem">
    <div class="problem-inner">
        <div class="section-label reveal">
            <div class="section-label-line"></div>
            <div class="section-label-text">Le mécanisme que personne ne voit</div>
        </div>
        <h2 class="reveal d1">
            La fatigue quotidienne ne disparaît pas.<br>Elle <em>s'accumule — jusqu'à l'arrêt.</em>
        </h2>
        <p class="problem-story reveal d1">
            Les équipes sédentaires savent ce qu'elles devraient faire. Faire des pauses. Structurer leur journée. Bouger. Le problème, ce n'est pas la connaissance — c'est que le cadre de travail les empêche de l'appliquer.
        </p>
        <p class="problem-body reveal d2">
            Un arrêt longue durée ne tombe pas du ciel. Il se construit en silence, par deux chaînes que le quotidien entretient sans que personne ne les voit.
        </p>

        <div class="problem-chains reveal d2">
            <div class="chain">
                <div class="chain-label">Chaîne 1 — Corps</div>
                <div class="chain-text"><strong>Sédentarité prolongée</strong> → tensions chroniques (dos, nuque, poignets) → douleurs → arrêts courts qui s'allongent.</div>
            </div>
            <div class="chain">
                <div class="chain-label">Chaîne 2 — Cognition</div>
                <div class="chain-text"><strong>Surcharge cognitive sans récupération</strong> → épuisement cumulé → désengagement → burn-out → arrêt longue durée.</div>
            </div>
        </div>

        <p class="problem-body reveal d2">
            Les approches classiques ne cassent aucune des deux chaînes — parce qu'elles se déroulent <strong>en dehors du travail réel.</strong>
        </p>

        <div class="problem-traps reveal d3">
            <div class="trap">
                <div class="trap-x">✗</div>
                <div class="trap-text"><strong>Team buildings événementiels</strong> — bonne humeur 48h, zéro changement dans les routines quotidiennes</div>
            </div>
            <div class="trap">
                <div class="trap-x">✗</div>
                <div class="trap-text"><strong>Séminaires ponctuels</strong> — le consultant part, les habitudes restent identiques</div>
            </div>
            <div class="trap">
                <div class="trap-x">✗</div>
                <div class="trap-text"><strong>Avantages en nature</strong> — babyfoot, corbeille de fruits : visible, mais cosmétique</div>
            </div>
            <div class="trap">
                <div class="trap-x">✗</div>
                <div class="trap-text"><strong>Formations ponctuelles</strong> — sans ancrage dans les outils et workflows existants</div>
            </div>
        </div>
    </div>
</section>

<!-- ═══ MÉTHODE ═══════════════════════════════════ -->
<section class="method">
    <div class="method-inner">
        <div class="method-header reveal">
            <div class="method-eyebrow">Momentum 180</div>
            <h2>4 routines. <em>Dans vos workflows.</em><br>Pas en dehors.</h2>
            <p class="method-sub">40 minutes par jour. 5% du temps de travail. Dans vos agendas — pas en dehors.</p>
        </div>

        <div class="rituals">
            <div class="ritual reveal">
                <div class="ritual-icon">🏋️</div>
                <div>
                    <div class="ritual-tag">10 min · Chaque matin</div>
                    <h4>Démarrage synchronisé</h4>
                    <p>Casse la sédentarité dès 9h. Mobilisation adaptée bureau — pas de tenue de sport, pas de performance. Crée un moment de cohésion quotidien. Inspiré du Radio Taiso pratiqué chez Toyota depuis +70 ans : <strong>27 millions de Japonais 2×/semaine.</strong> Zéro organisation belge ne l'utilise encore.</p>
                </div>
            </div>
            <div class="ritual reveal d1">
                <div class="ritual-icon">⏸️</div>
                <div>
                    <div class="ritual-tag">10 min · 4× par jour</div>
                    <h4>Pauses de concentration</h4>
                    <p>Le cerveau fonctionne par cycles ultradiens de 90 minutes. Le forcer au-delà détruit la productivité. Mobilisation ciblée pour les tensions posturales et récupération cognitive : <strong>+15 à 18% de concentration mesurée.</strong></p>
                    <p style="margin-top:0.5rem; font-size:0.78rem; opacity:0.6;">Kleitman / INRS — cycles ultradiens</p>
                </div>
            </div>
            <div class="ritual reveal d2">
                <div class="ritual-icon">📅</div>
                <div>
                    <div class="ritual-tag">Formation 2h par service · Max 20 personnes</div>
                    <h4>Time Blocking</h4>
                    <p>Casse la fragmentation des tâches — première source de fatigue mentale en bureau. Intégration directe dans Outlook, Teams ou Google. <strong>4 à 5h de productivité réelle récupérées par collaborateur par semaine.</strong></p>
                    <p style="margin-top:0.5rem; font-size:0.78rem; opacity:0.6;">Résultat observé en environnement corporate</p>
                </div>
            </div>
            <div class="ritual reveal d3">
                <div class="ritual-icon">🤝</div>
                <div>
                    <div class="ritual-tag">Min. 2 par service · Autonomie à J+180</div>
                    <h4>Ambassadeurs internes</h4>
                    <p>Casse la dépendance au consultant. Vos propres équipes pilotent le système après mon départ. La méthode reste — pas de rechute à 6 semaines. <strong>Autonomie mesurée à J+180.</strong></p>
                </div>
            </div>
        </div>

        <div class="phases reveal">
            <div class="phase">
                <div class="phase-badge">S0</div>
                <div class="phase-content">
                    <div class="phase-when">1 journée sur site</div>
                    <div class="phase-name">Cadrage</div>
                    <div class="phase-desc">Rencontre avec dirigeants, managers et décideurs. Définition de la marche à suivre. Identification des ambassadeurs (minimum 2 par service). Co-construction des routines adaptées à votre culture.</div>
                </div>
            </div>
            <div class="phase">
                <div class="phase-badge">S1</div>
                <div class="phase-content">
                    <div class="phase-when">Journées complètes sur site</div>
                    <div class="phase-name">Immersion</div>
                    <div class="phase-desc">Présence sur site toute la journée. Les équipes s'habituent à Marjorie. Implémentation progressive des routines dans les workflows. Conseil et ajustements en temps réel.</div>
                </div>
            </div>
            <div class="phase">
                <div class="phase-badge">S2</div>
                <div class="phase-content">
                    <div class="phase-when">Min. 4h/jour sur site</div>
                    <div class="phase-name">Formation</div>
                    <div class="phase-desc">Time blocking : 2h par service, max 20 personnes, réparti sur la semaine. Maintien des routines quotidiennes. Accompagnement terrain.</div>
                </div>
            </div>
            <div class="phase">
                <div class="phase-badge">S3</div>
                <div class="phase-content">
                    <div class="phase-when">4h/jour sur site</div>
                    <div class="phase-name">Finalisation</div>
                    <div class="phase-desc">Vérification de l'implémentation. Passage de relais complet aux ambassadeurs. Organisation du suivi sur 6 mois.</div>
                </div>
            </div>
            <div class="phase">
                <div class="phase-badge">M1–6</div>
                <div class="phase-content">
                    <div class="phase-when">6 mois · À distance (+ sur site si nécessaire)</div>
                    <div class="phase-name">Autonomie &amp; consolidation</div>
                    <div class="phase-desc">Rapport succinct des ambassadeurs 1×/mois. Recadrage à distance. Récolte des métriques et témoignages à J+180. Le rapport d'impact est un document de pilotage partageable en interne — pas une impression.</div>
                </div>
            </div>
        </div>
    </div>
</section>

<!-- ═══ ROI ════════════════════════════════════════ -->
<section class="roi">
    <div class="roi-inner">
        <div class="roi-header reveal">
            <div class="section-label">
                <div class="section-label-line"></div>
                <div class="section-label-text">Impact financier</div>
            </div>
            <h2>3 000€ investis.<br><em>Retour potentiel ×5 à ×10 en 6 mois.</em></h2>
            <p class="roi-sub">Calcul basé sur une cible de réduction de 20% de l'absentéisme — objectif réaliste sur 6 mois. Pas une promesse contractuelle.</p>
        </div>

        <div class="roi-calc reveal d1">
            <div class="roi-calc-tag">Pour une organisation de 50 collaborateurs en Hainaut · SD Worx 2025 · 165 425€/100 ETP</div>
            <div class="roi-equation">
                <div class="roi-eq-block">
                    <div class="roi-eq-num">82 700€</div>
                    <div class="roi-eq-label">Coût absentéisme estimé/an</div>
                </div>
                <div class="roi-eq-op">×</div>
                <div class="roi-eq-block">
                    <div class="roi-eq-num">−20%</div>
                    <div class="roi-eq-label">Cible de réduction à J+180</div>
                </div>
                <div class="roi-eq-op">=</div>
                <div class="roi-eq-block result">
                    <div class="roi-eq-num">~16 500€</div>
                    <div class="roi-eq-label">Économies potentielles/an</div>
                </div>
            </div>
            <div class="roi-footnote">Investissement pilote : 3 000€ HTVA — retour potentiel ×5 à ×10. Ces cibles seront mesurées et documentées dans le rapport J+180. Utilisez le calculateur ci-dessus pour estimer votre situation précise.</div>
        </div>

        <div class="roi-extras reveal d2">
            <div class="roi-extra">
                <div class="roi-extra-num">1 580€</div>
                <div class="roi-extra-text">Coût direct de l'absentéisme par collaborateur par an</div>
                <div class="roi-extra-src">SD Worx 2024</div>
            </div>
            <div class="roi-extra">
                <div class="roi-extra-num">+4–5h</div>
                <div class="roi-extra-text">De productivité réelle récupérées par semaine via time blocking</div>
                <div class="roi-extra-src">Résultat observé · environnement corporate</div>
            </div>
            <div class="roi-extra">
                <div class="roi-extra-num">+15–18%</div>
                <div class="roi-extra-text">De concentration mesurée avec les pauses de récupération cognitive</div>
                <div class="roi-extra-src">INRS · cycles ultradiens (Kleitman)</div>
            </div>
        </div>
    </div>
</section>

<!-- ═══ COMPARATIF ════════════════════════════════ -->
<section class="compare">
    <div class="compare-inner">
        <div class="compare-header reveal">
            <div class="compare-eyebrow">La différence</div>
            <h2>Ce que les autres font.<br><em>Ce que je fais, moi.</em></h2>
            <p class="compare-intro">Pas pour critiquer — pour être honnête sur pourquoi certaines approches ne tiennent pas dans le temps.</p>
        </div>
        <div class="compare-wrap reveal d1">
            <table>
                <thead>
                    <tr>
                        <th>Critère</th>
                        <th>Approches classiques</th>
                        <th>Momentum 180</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>Durée réelle</td>
                        <td><span class="badge badge-no">1 à 2 jours</span></td>
                        <td><span class="badge badge-yes">4 semaines + 6 mois suivi</span></td>
                    </tr>
                    <tr>
                        <td>Ancrage après départ</td>
                        <td><span class="badge badge-no">Aucun</span></td>
                        <td><span class="badge badge-yes">Ambassadeurs formés par service</span></td>
                    </tr>
                    <tr>
                        <td>Intégration workflows</td>
                        <td><span class="badge badge-no">En dehors du travail</span></td>
                        <td><span class="badge badge-yes">Dans le quotidien réel</span></td>
                    </tr>
                    <tr>
                        <td>Mesure avant / après</td>
                        <td><span class="badge badge-no">Rarement</span></td>
                        <td><span class="badge badge-yes">Rapport J+21 et J+180</span></td>
                    </tr>
                    <tr>
                        <td>Effet dans le temps</td>
                        <td><span class="badge badge-no">Éphémère (6–8 semaines)</span></td>
                        <td><span class="badge badge-yes">Culture auto-entretenue</span></td>
                    </tr>
                    <tr>
                        <td>Dépendance consultante</td>
                        <td><span class="badge badge-no">Souvent, pour renouveler</span></td>
                        <td><span class="badge badge-yes">Zéro — vos équipes pilotent</span></td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
</section>

<!-- ═══ TARIF ═════════════════════════════════════ -->
<section class="pricing">
    <div class="pricing-inner">
        <div class="pricing-eyebrow reveal">Offre pilote 2026</div>
        <h2 class="reveal d1">Tout inclus.<br><em>2 organisations partenaires.</em></h2>
        <p class="pricing-sub reveal d2">Je sélectionne les structures où la méthode a le plus de chances de produire des résultats mesurables. On le voit ensemble en 15 minutes.</p>

        <div class="pricing-card reveal d2">
            <div class="pricing-badge">Pilote · 2 places · 2026</div>
            <div class="price-anchor">Tarif standard post-pilote : à partir de 6 000€</div>
            <div class="price"><sup>€</sup>3 000</div>
            <div class="price-detail">HTVA · Par organisation · Tout inclus · Aucun frais caché</div>
            <div class="price-items">
                <div class="price-item"><span class="price-check">✓</span> Cadrage avec dirigeants et managers (1 journée)</div>
                <div class="price-item"><span class="price-check">✓</span> 4 semaines sur site (immersion, formation, finalisation)</div>
                <div class="price-item"><span class="price-check">✓</span> Formations time blocking par service (max 20 pers.)</div>
                <div class="price-item"><span class="price-check">✓</span> Formation ambassadeurs internes (min. 2 par service)</div>
                <div class="price-item"><span class="price-check">✓</span> Tous outils, templates &amp; supports</div>
                <div class="price-item"><span class="price-check">✓</span> 6 mois de suivi + rapports J+21 et J+180</div>
            </div>
            <a href="https://calendly.com/equilibre_performance/equilibreperformance" target="_blank" class="btn-book">
                → Réserver un diagnostic — 15 minutes
            </a>
            <p class="book-note">Zéro engagement · Garantie Jour 3 : 50% remboursé si ça ne correspond pas — vous gardez tous les outils</p>
            <div class="counterparts">
                <div class="counterparts-title">Ce que je demande en contrepartie</div>
                <div class="counterparts-text">Accès direct aux équipes · Participation active de la direction · Feedback structuré au fil du programme · Accès aux métriques pour les rapports J+21 et J+180 · Témoignage écrit ou vidéo en fin de mission.</div>
            </div>
        </div>
    </div>
</section>

<!-- ═══ À PROPOS ══════════════════════════════════ -->
<section class="about">
    <div class="about-inner">
        <div class="about-avatar reveal">MM</div>
        <div class="reveal d1">
            <div class="about-eyebrow">Marjorie Mathieu</div>
            <h3>Je ne théorise pas.<br>Je <em>m'immerge.</em></h3>
            <p>15 ans dans des environnements corporate sédentaires — BNP Paribas, Serco Europe, CEPI Brussels, KONE, STIB. J'ai observé de l'intérieur comment l'absence de routines quotidiennes détruit l'engagement des équipes. Les séminaires s'oublient. Les habitudes restent.</p>
            <p>14 ans de pratique et d'enseignement des techniques de régulation physique et cognitive — appliquées comme outils opérationnels, pas comme philosophie personnelle. Créatrice de Momentum 180 (2026). Approche 100% data-driven : les rapports J+21 et J+180 sont des documents de pilotage, pas des impressions.</p>
            <div class="about-tags">
                <span class="about-tag">BNP Paribas · Serco · CEPI Brussels · KONE · STIB</span>
                <span class="about-tag">15 ans corporate</span>
                <span class="about-tag">14 ans de pratique des routines opérationnelles</span>
                <span class="about-tag">Smart Coop · Ath, Hainaut</span>
            </div>
            <a href="https://www.linkedin.com/in/momentum180/" target="_blank" class="about-link">
                Mon parcours complet sur LinkedIn →
            </a>
        </div>
    </div>
</section>

<!-- ═══ OBJECTIONS ════════════════════════════════ -->
<section class="objections">
    <div class="objections-inner">
        <h2 class="reveal">Vos questions légitimes.</h2>

        <div class="objection reveal d1">
            <div class="objection-q">« Mes équipes vont résister. »</div>
            <div class="objection-a">Pas de tenue de sport, pas de performance physique. La Semaine 0 calibre tout à votre culture. Le démarrage synchronisé reprend un principe utilisé dans les bureaux de Toyota depuis 70 ans — <strong>pas de la gym.</strong></div>
        </div>

        <div class="objection reveal d1">
            <div class="objection-q">« On a déjà investi dans du team building, ça n'a rien changé. »</div>
            <div class="objection-a">Normal : un événement ponctuel ne crée pas d'habitude. Ici, c'est <strong>4 semaines dans vos workflows quotidiens</strong> + des ambassadeurs formés dans chaque service pour maintenir le système après mon départ.</div>
        </div>

        <div class="objection reveal d2">
            <div class="objection-q">« Il n'y a pas de preuve que ça marche chez nous. »</div>
            <div class="objection-a">C'est le principe du pilote. <strong>3 000€ pour co-construire les premiers résultats belges.</strong> Les chiffres J+180 parleront — c'est pour ça que les métriques font partie des contreparties attendues. Et si après 3 jours ça ne colle pas : 50% remboursé, vous gardez tous les outils.</div>
        </div>

        <div class="objection reveal d2">
            <div class="objection-q">« Qu'est-ce qui se passe quand vous partez ? »</div>
            <div class="objection-a">Rien ne s'évapore — c'est le point central. Les ambassadeurs internes pilotent le système. Les routines sont dans les agendas. Les outils sont dans vos fichiers. <strong>La méthode reste parce qu'elle est dans vos workflows, pas dans ma tête.</strong></div>
        </div>
    </div>
</section>

<!-- ═══ FINALE ════════════════════════════════════ -->
<section class="finale">
    <div class="finale-inner">
        <span class="finale-ornament reveal">"</span>
        <h2 class="reveal d1">
            Personne n'a conçu la journée de travail.<br>
            <em>Il suffit de peu pour que tout change.</em>
        </h2>
        <p class="finale-sub reveal d2">
            15 minutes pour voir si votre organisation correspond au profil. Pas un pitch. Un diagnostic honnête — je vous dis ce que j'observe et si le pilote a du sens pour vous.
        </p>
        <div class="finale-sep reveal"></div>
        <div class="finale-spots reveal">
            <div class="f-spot open"></div>
            <div class="f-spot open"></div>
        </div>
        <p class="finale-spots-txt reveal"><strong>2 places partenaires</strong> — Pilote 2026 · 3 000€ HTVA</p>
        <a href="https://calendly.com/equilibre_performance/equilibreperformance" target="_blank" class="btn-finale reveal d2">
            → 15 minutes pour voir si ça correspond
        </a>
        <p class="finale-note reveal d3">hello@marjoriemathieu.be · +32 477 09 18 03</p>
    </div>
</section>

<!-- ═══ FOOTER ════════════════════════════════════ -->
<footer>
    <div class="footer-brand">Marjorie Mathieu — Momentum 180</div>
    <div class="footer-contact">
        <a href="mailto:hello@marjoriemathieu.be">hello@marjoriemathieu.be</a> · +32 477 09 18 03 · Ath, Hainaut — Belgique
    </div>
</footer>

<script>
    /* ── SCROLL REVEAL ── */
    const obs = new IntersectionObserver(entries => {
        entries.forEach(e => { if (e.isIntersecting) e.target.classList.add('visible'); });
    }, { threshold: 0.08, rootMargin: '0px 0px -30px 0px' });
    document.querySelectorAll('.reveal').forEach(el => obs.observe(el));

    window.addEventListener('scroll', () => {
        document.getElementById('nav').style.boxShadow =
            window.scrollY > 50 ? '0 4px 20px rgba(27,54,93,0.1)' : 'none';
    });

    /* ── CALCULATEUR ROI ── */
    const PROGRAMME_COST = 3000;
    const COUT_PAR_ETP_HAINAUT = 1654.25; // 165425 / 100

    function fmt(n) {
        return Math.round(n).toLocaleString('fr-BE') + '€';
    }

    function updateCalc() {
        const etp   = parseFloat(document.getElementById('etp').value);
        const taux  = parseFloat(document.getElementById('taux').value);
        const sal   = parseFloat(document.getElementById('sal').value);
        const longP = parseFloat(document.getElementById('long').value) / 100;

        document.getElementById('etp-val').textContent  = Math.round(etp);
        document.getElementById('taux-val').innerHTML   = taux.toFixed(1) + '<span style="font-size:1.2rem">%</span>';
        document.getElementById('sal-val').innerHTML    = Math.round(sal).toLocaleString('fr-BE') + '<span style="font-size:1.2rem">€</span>';
        document.getElementById('long-val').innerHTML   = Math.round(longP * 100) + '<span style="font-size:1.2rem">%</span>';

        // Coût direct : base SD Worx ajustée à l'effectif et au taux réel vs moyenne belge (6.9%)
        const tauxMoy = 6.9;
        const coutBase = etp * COUT_PAR_ETP_HAINAUT;
        const coutAjuste = coutBase * (taux / tauxMoy);

        // Surcoût loi 2026 : arrêts longs (>30j) → employeur paie 30% indemnités mois 2 et 3
        // Estimation : durée moyenne arrêt long = 90j → 2 mois indemnisés à 60% salaire brut
        const nbArretLong = etp * (taux / 100) * longP;
        const indemnitesMensuelle = sal * 0.60;
        const surcoutLoi = nbArretLong * (indemnitesMensuelle * 2) * 0.30;

        const total = coutAjuste + surcoutLoi;
        const savings20 = total * 0.20;
        const roi = savings20 / PROGRAMME_COST;
        const roiPct = Math.min((PROGRAMME_COST / savings20) * 100, 100);

        document.getElementById('res-direct').textContent = fmt(coutAjuste);
        document.getElementById('res-loi').textContent    = fmt(surcoutLoi);
        document.getElementById('res-total').textContent  = fmt(total);

        const roiFill = document.getElementById('roi-fill');
        const barPct  = Math.min((PROGRAMME_COST / savings20) * 100, 100);
        roiFill.style.width = barPct.toFixed(1) + '%';

        const roiX = (savings20 / PROGRAMME_COST).toFixed(1);
        document.getElementById('res-roi-pct').textContent =
            '= ' + barPct.toFixed(0) + "% de l\u2019\u00e9conomie \u00e0 J+180 si \u221220%";

        let verdict = '';
        if (savings20 <= 0 || !isFinite(savings20)) {
            verdict = 'Ajustez les curseurs pour voir votre situation.';
        } else if (roi >= 5) {
            verdict = `Sur la base de vos paramètres, une réduction de 20% de l'absentéisme représente ${fmt(savings20)}/an — soit un retour de ×${roiX} sur l'investissement de ${fmt(PROGRAMME_COST)}. Pour ${Math.round(etp)} collaborateurs, le programme se rentabilise en moins de 3 mois.`;
        } else if (roi >= 2) {
            verdict = `Une réduction de 20% représente ${fmt(savings20)}/an pour votre organisation — soit ×${roiX} l'investissement. Le surcoût loi 2026 seul (${fmt(surcoutLoi)}/an) justifie une action préventive.`;
        } else {
            verdict = `Votre coût d'absentéisme estimé est de ${fmt(total)}/an. Une réduction de 20% = ${fmt(savings20)}/an. Discutons ensemble si Momentum 180 est le levier le plus adapté à votre situation.`;
        }
        document.getElementById('res-verdict').textContent = verdict;
    }

    // Init on load
    updateCalc();
</script>
</body>
</html>
