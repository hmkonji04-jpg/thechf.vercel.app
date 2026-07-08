<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>README Generator</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@400;500;700&family=DM+Sans:wght@400;500;700&display=swap" rel="stylesheet">
  <style>
    :root{
      --bg:#f5f1e8;
      --paper:#fffdf8;
      --ink:#171411;
      --muted:#6a6057;
      --line:#d8cfc3;
      --accent:#9a3412;
      --accent-2:#1f6f5f;
      --shadow:0 20px 60px rgba(23,20,17,.12);
      --radius:24px;
    }

    *{box-sizing:border-box}
    html{scroll-behavior:smooth}
    body{
      margin:0;
      font-family:"DM Sans", sans-serif;
      color:var(--ink);
      background:
        radial-gradient(circle at top left, rgba(154,52,18,.08), transparent 30%),
        radial-gradient(circle at bottom right, rgba(31,111,95,.08), transparent 30%),
        linear-gradient(180deg, #f7f3eb 0%, #f2ede3 100%);
      min-height:100vh;
    }

    .grain::before{
      content:"";
      position:fixed;
      inset:0;
      pointer-events:none;
      opacity:.08;
      background-image:
        linear-gradient(transparent 0, rgba(0,0,0,.02) 50%, transparent 100%);
      background-size:100% 4px;
      mix-blend-mode:multiply;
    }

    .wrap{
      width:min(1100px, calc(100% - 32px));
      margin:0 auto;
    }

    header{
      padding:28px 0 18px;
    }

    .nav{
      display:flex;
      justify-content:space-between;
      align-items:center;
      gap:16px;
      padding:14px 18px;
      background:rgba(255,253,248,.72);
      border:1px solid rgba(216,207,195,.9);
      backdrop-filter:blur(14px);
      border-radius:999px;
      box-shadow:var(--shadow);
    }

    .brand{
      font-family:"Space Grotesk", sans-serif;
      font-weight:700;
      letter-spacing:-.04em;
      font-size:1rem;
    }

    .tag{
      color:var(--muted);
      font-size:.95rem;
    }

    main{
      padding:28px 0 60px;
    }

    .hero{
      display:grid;
      grid-template-columns:1.15fr .85fr;
      gap:28px;
      align-items:stretch;
      margin-bottom:28px;
    }

    .hero-copy,
    .panel{
      background:rgba(255,253,248,.78);
      border:1px solid var(--line);
      border-radius:var(--radius);
      box-shadow:var(--shadow);
      backdrop-filter:blur(12px);
    }

    .hero-copy{
      padding:clamp(28px, 5vw, 56px);
      position:relative;
      overflow:hidden;
    }

    .hero-copy::after{
      content:"README";
      position:absolute;
      right:-18px;
      bottom:-18px;
      font-family:"Space Grotesk", sans-serif;
      font-size:clamp(4rem, 12vw, 9rem);
      line-height:.85;
      color:rgba(23,20,17,.04);
      font-weight:700;
      letter-spacing:-.06em;
    }

    .eyebrow{
      display:inline-flex;
      align-items:center;
      gap:10px;
      color:var(--accent-2);
      text-transform:uppercase;
      letter-spacing:.16em;
      font-size:.78rem;
      font-weight:700;
      margin-bottom:16px;
    }

    .eyebrow::before{
      content:"";
      width:34px;
      height:1px;
      background:currentColor;
    }

    h1{
      margin:0 0 16px;
      font-family:"Space Grotesk", sans-serif;
      font-size:clamp(2.5rem, 7vw, 5.5rem);
      line-height:.95;
      letter-spacing:-.06em;
      max-width:10ch;
    }

    .lead{
      margin:0;
      max-width:58ch;
      color:var(--muted);
      font-size:1.05rem;
      line-height:1.7;
    }

    .panel{
      padding:22px;
      display:flex;
      flex-direction:column;
      justify-content:space-between;
      min-height:100%;
    }

    .panel h2{
      margin:0 0 12px;
      font-family:"Space Grotesk", sans-serif;
      font-size:1.15rem;
      letter-spacing:-.03em;
    }

    .panel p{
      margin:0 0 18px;
      color:var(--muted);
      line-height:1.65;
    }

    .mini-list{
      display:grid;
      gap:12px;
      margin-top:14px;
    }

    .mini-item{
      padding:14px 16px;
      border:1px solid var(--line);
      border-radius:18px;
      background:linear-gradient(180deg, rgba(255,255,255,.72), rgba(255,250,243,.9));
      font-size:.95rem;
    }

    .content{
      display:grid;
      grid-template-columns:280px 1fr;
      gap:28px;
      align-items:start;
    }

    .sidebar{
      position:sticky;
      top:20px;
      padding:20px;
      border:1px solid var(--line);
      border-radius:24px;
      background:rgba(255,253,248,.78);
      box-shadow:var(--shadow);
      backdrop-filter:blur(12px);
    }

    .sidebar h3{
      margin:0 0 12px;
      font-family:"Space Grotesk", sans-serif;
      font-size:1rem;
      letter-spacing:-.03em;
    }

    .sidebar nav{
      display:grid;
      gap:10px;
    }

    .sidebar a{
      text-decoration:none;
      color:var(--ink);
      padding:10px 12px;
      border-radius:14px;
      transition:.25s ease;
      border:1px solid transparent;
    }

    .sidebar a:hover{
      transform:translateX(4px);
      background:rgba(154,52,18,.06);
      border-color:rgba(154,52,18,.14);
      color:var(--accent);
    }

    .doc{
      padding:clamp(22px, 4vw, 40px);
      border:1px solid var(--line);
      border-radius:28px;
      background:var(--paper);
      box-shadow:var(--shadow);
      overflow:hidden;
    }

    .doc-head{
      display:flex;
      justify-content:space-between;
      align-items:center;
      gap:16px;
      padding-bottom:20px;
      margin-bottom:24px;
      border-bottom:1px solid var(--line);
    }

    .doc-title{
      font-family:"Space Grotesk", sans-serif;
      font-size:clamp(1.5rem, 3vw, 2.25rem);
      letter-spacing:-.05em;
      margin:0;
    }

    .actions{
      display:flex;
      gap:12px;
      flex-wrap:wrap;
    }

    button{
      appearance:none;
      border:none;
      cursor:pointer;
      font:inherit;
    }

    .btn{
      padding:12px 16px;
      border-radius:999px;
      font-weight:700;
      transition:.25s ease;
    }

    .btn-primary{
      background:var(--ink);
      color:#fffdf8;
      box-shadow:0 10px 30px rgba(23,20,17,.16);
    }

    .btn-primary:hover{
      transform:translateY(-2px) scale(1.02);
      background:var(--accent);
    }

    .btn-secondary{
      background:transparent;
      color:var(--ink);
      border:1px solid var(--line);
    }

    .btn-secondary:hover{
      transform:translateY(-2px);
      border-color:var(--accent-2);
      color:var(--accent-2);
      background:rgba(31,111,95,.05);
    }

    .markdown{
      white-space:pre-wrap;
      line-height:1.75;
      color:#201c18;
      font-size:1rem;
      margin:0;
      font-family:ui-monospace, SFMono-Regular, Menlo, Monaco, Consolas, monospace;
      background:
        linear-gradient(180deg, rgba(154,52,18,.03), transparent 26%),
        linear-gradient(180deg, #fffdfa 0%, #fffaf3 100%);
      border:1px solid rgba(216,207,195,.9);
      border-radius:22px;
      padding:22px;
      overflow:auto;
    }

    .reveal{
      opacity:0;
      transform:translateY(24px);
      animation:rise .8s ease forwards;
    }

    .delay-1{animation-delay:.08s}
    .delay-2{animation-delay:.16s}
    .delay-3{animation-delay:.24s}
    .delay-4{animation-delay:.32s}

    @keyframes rise{
      to{
        opacity:1;
        transform:translateY(0);
      }
    }

    .observe{
      opacity:0;
      transform:translateY(22px);
      transition:opacity .7s ease, transform .7s ease;
    }

    .observe.in{
      opacity:1;
      transform:translateY(0);
    }

    footer{
      padding:26px 0 48px;
      color:var(--muted);
      text-align:center;
      font-size:.95rem;
    }

    @media (max-width: 920px){
      .hero,
      .content{
        grid-template-columns:1fr;
      }

      .sidebar{
        position:relative;
        top:auto;
      }

      .doc-head{
        flex-direction:column;
        align-items:flex-start;
      }
    }

    @media (max-width: 640px){
      .nav{
        border-radius:24px;
        align-items:flex-start;
        flex-direction:column;
      }

      .actions{
        width:100%;
      }

      .btn{
        width:100%;
        text-align:center;
      }
    }
  </style>
</head>
<body class="grain">
  <header class="wrap reveal">
    <div class="nav">
      <div class="brand">hmkonji04-jpg / thechf.vercel.app</div>
      <div class="tag">Ready-to-paste README.md for your GitHub repo</div>
    </div>
  </header>

  <main class="wrap">
    <section class="hero">
      <article class="hero-copy reveal delay-1">
        <div class="eyebrow">GitHub Documentation</div>
        <h1>README prepared for your project.</h1>
        <p class="lead">
          Since you're on the GitHub “new file” page for <strong>README.md</strong>, here is a clean and professional starter document you can paste directly into your repository.
        </p>
      </article>

      <aside class="panel reveal delay-2">
        <div>
          <h2>What this includes</h2>
          <p>A solid starter README with project overview, features, setup, deployment, and contribution notes.</p>
        </div>
        <div class="mini-list">
          <div class="mini-item">Project title and description</div>
          <div class="mini-item">Local setup instructions</div>
          <div class="mini-item">Deployment note for Vercel</div>
          <div class="mini-item">Simple contribution structure</div>
        </div>
      </aside>
    </section>

    <section class="content">
      <aside class="sidebar observe">
        <h3>Quick actions</h3>
        <nav aria-label="README navigation">
          <a href="#readme">View README content</a>
          <a href="#how">How to use it</a>
          <a href="#copy">Copy section</a>
        </nav>
      </aside>

      <section class="doc observe" id="readme">
        <div class="doc-head">
          <h2 class="doc-title">README.md</h2>
          <div class="actions" id="copy">
            <button class="btn btn-primary" id="copyBtn">Copy Markdown</button>
            <button class="btn btn-secondary" id="selectBtn">Select Text</button>
          </div>
        </div>

        <pre class="markdown" id="markdownContent"># thechf.vercel.app

A simple web project for hosting and deploying a website using GitHub and Vercel.

## Overview

This repository contains the source files for the **thechf.vercel.app** website.  
It is intended to be used as a lightweight frontend project, with deployment managed through **Vercel**.

## Features

- Static website structure
- Easy deployment with Vercel
- Version control with GitHub
- Workflow support through GitHub Actions

## Project Structure

```bash
.github/
  workflows/
index.html
README.md
