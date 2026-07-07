<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Sahil Shelar — Frontend Developer</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Fraunces:opsz,wght@9..144,400;9..144,600;9..144,900&family=JetBrains+Mono:wght@400;500;700&family=Inter:wght@400;500;600&display=swap" rel="stylesheet">
<style>
  :root{
    --ink:#0F1420;
    --ink-2:#171E30;
    --paper:#EDEAE1;
    --paper-dim:#B9BAC0;
    --brass:#C9A227;
    --brass-dim:#8a742a;
    --teal:#4FD1C5;
    --slate:#8890A6;
    --line: rgba(233,230,220,0.14);
  }
  *{margin:0;padding:0;box-sizing:border-box;}
  html{scroll-behavior:smooth;}
  body{
    background:var(--ink);
    color:var(--paper);
    font-family:'Inter',sans-serif;
    overflow-x:hidden;
  }
  ::selection{background:var(--brass); color:var(--ink);}

  a{color:inherit; text-decoration:none;}

  .mono{font-family:'JetBrains Mono',monospace;}

  /* ===== Frame counter — fixed corner, signature element ===== */
  #counter{
    position:fixed; top:20px; right:20px;
    font-family:'JetBrains Mono',monospace;
    font-size:11px; letter-spacing:0.08em;
    color:var(--slate);
    z-index:100;
    display:flex; gap:6px; align-items:center;
    pointer-events:none;
  }
  #counter .num{color:var(--brass); font-weight:700;}

  /* corner brackets, camera-focus motif */
  .brackets{position:relative;}
  .brackets::before, .brackets::after,
  .brackets .bl, .brackets .br{
    content:""; position:absolute; width:18px; height:18px;
    border-color:var(--brass); border-style:solid; border-width:0;
    transition:all .35s ease;
    opacity:0.55;
  }
  .brackets::before{top:-10px;left:-10px;border-top-width:2px;border-left-width:2px;}
  .brackets::after{top:-10px;right:-10px;border-top-width:2px;border-right-width:2px;}
  .brackets .bl{bottom:-10px;left:-10px;border-bottom-width:2px;border-left-width:2px;}
  .brackets .br{bottom:-10px;right:-10px;border-bottom-width:2px;border-right-width:2px;}
  .brackets:hover::before, .brackets:hover::after,
  .brackets:hover .bl, .brackets:hover .br{opacity:1; width:24px;height:24px;}

  nav{
    position:fixed; top:0; left:0; right:0; z-index:90;
    display:flex; justify-content:space-between; align-items:center;
    padding:22px 32px;
    backdrop-filter:blur(6px);
    background:linear-gradient(to bottom, rgba(15,20,32,0.85), transparent);
  }
  nav .logo{font-family:'Fraunces',serif; font-weight:600; font-size:18px; letter-spacing:0.02em;}
  nav .logo span{color:var(--brass);}
  nav ul{list-style:none; display:flex; gap:28px;}
  nav ul li a{font-size:12px; letter-spacing:0.12em; text-transform:uppercase; color:var(--slate); transition:color .25s;}
  nav ul li a:hover{color:var(--brass);}
  @media (max-width:640px){ nav ul{display:none;} }

  /* ===== HERO ===== */
  header.hero{
    min-height:100svh;
    display:flex; flex-direction:column; align-items:center; justify-content:center;
    text-align:center;
    padding:120px 24px 60px;
    position:relative;
  }
  header.hero::before{
    content:"";
    position:absolute; inset:0;
    background:
      radial-gradient(ellipse 60% 40% at 50% 20%, rgba(201,162,39,0.08), transparent 60%),
      repeating-linear-gradient(180deg, rgba(255,255,255,0.015) 0px, rgba(255,255,255,0.015) 1px, transparent 1px, transparent 3px);
    pointer-events:none;
  }
  .frame-wrap{
    position:relative;
    width:180px; height:180px;
    margin-bottom:34px;
  }
  .frame-wrap img{
    width:100%; height:100%; object-fit:cover;
    border-radius:2px;
    filter:grayscale(15%) contrast(1.05);
  }
  .aperture-tag{
    position:absolute; bottom:-14px; left:50%; transform:translateX(-50%);
    background:var(--ink); border:1px solid var(--line);
    padding:3px 10px; font-size:10px; letter-spacing:0.14em;
    color:var(--teal); white-space:nowrap;
  }
  .eyebrow{
    font-size:12px; letter-spacing:0.3em; text-transform:uppercase;
    color:var(--teal); margin-bottom:18px;
  }
  h1.name{
    font-family:'Fraunces',serif; font-weight:600;
    font-size:clamp(2.6rem, 8vw, 5rem);
    line-height:1.02;
    letter-spacing:-0.01em;
  }
  h1.name em{font-style:italic; font-weight:400; color:var(--brass);}
  .role-readout{
    margin-top:22px;
    font-size:13px; letter-spacing:0.06em;
    color:var(--slate);
    display:flex; gap:14px; flex-wrap:wrap; justify-content:center;
  }
  .role-readout .sep{color:var(--brass-dim);}
  .hero-desc{
    max-width:520px; margin:30px auto 0;
    font-size:15.5px; line-height:1.7; color:var(--paper-dim);
  }
  .hero-links{
    margin-top:34px; display:flex; gap:16px; flex-wrap:wrap; justify-content:center;
  }
  .btn{
    padding:12px 26px; font-size:12.5px; letter-spacing:0.1em; text-transform:uppercase;
    border:1px solid var(--line); transition:all .3s ease;
  }
  .btn.solid{background:var(--brass); color:var(--ink); border-color:var(--brass); font-weight:600;}
  .btn.solid:hover{background:var(--paper); border-color:var(--paper);}
  .btn.outline:hover{border-color:var(--brass); color:var(--brass);}

  .scroll-cue{
    position:absolute; bottom:30px; left:50%; transform:translateX(-50%);
    font-size:10px; letter-spacing:0.2em; color:var(--slate);
    display:flex; flex-direction:column; align-items:center; gap:8px;
  }
  .scroll-cue .line{width:1px; height:36px; background:var(--line); position:relative; overflow:hidden;}
  .scroll-cue .line::after{
    content:""; position:absolute; top:-40%; left:0; width:100%; height:40%;
    background:var(--brass); animation:reel 1.8s ease-in-out infinite;
  }
  @keyframes reel{ 0%{top:-40%;} 100%{top:100%;} }

  /* ===== SECTION shell ===== */
  section{
    max-width:920px; margin:0 auto; padding:110px 28px;
    position:relative;
  }
  .frame-no{
    font-family:'JetBrains Mono',monospace; font-size:12px; color:var(--brass);
    letter-spacing:0.1em; margin-bottom:10px; display:flex; align-items:center; gap:10px;
  }
  .frame-no::after{content:""; flex:1; height:1px; background:var(--line);}
  h2.section-title{
    font-family:'Fraunces',serif; font-weight:600; font-size:clamp(1.7rem,4vw,2.6rem);
    margin-bottom:44px;
  }

  /* ===== ABOUT ===== */
  .about-body{font-size:16px; line-height:1.85; color:var(--paper-dim); max-width:680px;}
  .about-body strong{color:var(--paper); font-weight:600;}

  /* ===== EDUCATION ===== */
  .edu-card{
    border:1px solid var(--line); padding:30px;
    display:flex; justify-content:space-between; gap:30px; flex-wrap:wrap;
  }
  .edu-card h3{font-family:'Fraunces',serif; font-size:1.3rem; font-weight:600; margin-bottom:6px;}
  .edu-card p{color:var(--slate); font-size:14px; line-height:1.6;}
  .cgpa{
    font-family:'JetBrains Mono',monospace; text-align:right;
  }
  .cgpa .big{font-size:2.2rem; color:var(--brass); font-weight:700; line-height:1;}
  .cgpa .lbl{font-size:10px; letter-spacing:0.15em; color:var(--slate); margin-top:6px;}

  /* ===== SKILLS ===== */
  .skill-grid{display:grid; grid-template-columns:repeat(3,1fr); gap:1px; background:var(--line); border:1px solid var(--line);}
  .skill-col{background:var(--ink); padding:26px 24px;}
  .skill-col h4{
    font-family:'JetBrains Mono',monospace; font-size:11px; letter-spacing:0.14em;
    color:var(--teal); margin-bottom:16px; text-transform:uppercase;
  }
  .skill-col ul{list-style:none;}
  .skill-col li{
    font-size:14.5px; padding:7px 0; color:var(--paper-dim);
    border-bottom:1px solid rgba(255,255,255,0.05);
  }
  .skill-col li:last-child{border-bottom:none;}
  @media (max-width:640px){.skill-grid{grid-template-columns:1fr;}}

  /* ===== PROJECTS ===== */
  .project-card{
    border:1px solid var(--line); padding:36px;
    position:relative; margin-bottom:24px;
    transition:border-color .3s ease;
  }
  .project-card:hover{border-color:var(--brass-dim);}
  .project-head{display:flex; justify-content:space-between; align-items:baseline; gap:20px; flex-wrap:wrap; margin-bottom:14px;}
  .project-head h3{font-family:'Fraunces',serif; font-size:1.5rem; font-weight:600;}
  .project-tag{font-family:'JetBrains Mono',monospace; font-size:11px; color:var(--teal); letter-spacing:0.08em;}
  .project-card p{color:var(--paper-dim); font-size:14.5px; line-height:1.7; margin-bottom:16px;}
  .stack{display:flex; gap:10px; flex-wrap:wrap;}
  .stack span{
    font-family:'JetBrains Mono',monospace; font-size:11px; padding:5px 11px;
    border:1px solid var(--line); color:var(--slate);
  }

  /* ===== CERTS / ACHIEVEMENTS ===== */
  .two-col{display:grid; grid-template-columns:1fr 1fr; gap:50px;}
  @media (max-width:640px){.two-col{grid-template-columns:1fr;}}
  .list-block h4{
    font-family:'JetBrains Mono',monospace; font-size:11px; letter-spacing:0.14em;
    color:var(--brass); margin-bottom:20px; text-transform:uppercase;
  }
  .list-block li{
    list-style:none; padding:14px 0; border-bottom:1px solid var(--line);
    font-size:15px; color:var(--paper-dim); display:flex; gap:12px; align-items:baseline;
  }
  .list-block li .idx{font-family:'JetBrains Mono',monospace; font-size:11px; color:var(--teal);}

  /* ===== CONTACT ===== */
  .contact-wrap{text-align:center;}
  .contact-wrap h2{font-family:'Fraunces',serif; font-weight:600; font-size:clamp(2rem,6vw,3.2rem); margin-bottom:20px;}
  .contact-wrap p{color:var(--paper-dim); max-width:480px; margin:0 auto 40px; line-height:1.7;}
  .contact-links{
    display:flex; flex-direction:column; align-items:stretch; gap:12px;
    max-width:440px; margin:0 auto;
  }
  .contact-row{
    display:flex; align-items:center; justify-content:space-between; gap:16px;
    border:1px solid var(--line); padding:16px 20px;
    transition:border-color .25s ease;
    background:var(--ink-2);
  }
  .contact-row:hover{border-color:var(--brass-dim);}
  .contact-row .field{display:flex; flex-direction:column; align-items:flex-start; gap:4px; text-align:left; min-width:0;}
  .contact-row .field .lbl{font-size:10px; letter-spacing:0.14em; color:var(--slate); text-transform:uppercase;}
  .contact-row .field .val{font-size:14.5px; color:var(--paper); overflow:hidden; text-overflow:ellipsis; white-space:nowrap;}
  .copy-btn{
    font-family:'JetBrains Mono',monospace; font-size:11px; letter-spacing:0.08em;
    color:var(--teal); border:1px solid var(--line); padding:8px 14px;
    background:transparent; cursor:pointer; transition:all .25s ease; white-space:nowrap;
    text-transform:uppercase;
  }
  .copy-btn:hover{border-color:var(--teal); color:var(--ink); background:var(--teal);}
  .copy-btn.copied{border-color:var(--brass); color:var(--ink); background:var(--brass);}
  .contact-row.link-row a.open-link{
    font-family:'JetBrains Mono',monospace; font-size:11px; letter-spacing:0.08em;
    color:var(--brass); border:1px solid var(--line); padding:8px 14px;
    transition:all .25s ease; white-space:nowrap; text-transform:uppercase;
  }
  .contact-row.link-row a.open-link:hover{border-color:var(--brass); background:var(--brass); color:var(--ink);}

  footer{
    text-align:center; padding:40px 20px; color:var(--slate);
    font-family:'JetBrains Mono',monospace; font-size:11px; letter-spacing:0.08em;
    border-top:1px solid var(--line);
  }

  .lang-row{display:flex; gap:14px; justify-content:center; margin-top:36px; flex-wrap:wrap;}
  .lang-row span{
    font-family:'JetBrains Mono',monospace; font-size:11px; letter-spacing:0.1em;
    color:var(--slate); border:1px solid var(--line); padding:6px 14px;
  }

  [data-reveal]{opacity:0; transform:translateY(24px); transition:opacity .7s ease, transform .7s ease;}
  [data-reveal].in{opacity:1; transform:translateY(0);}
</style>
</head>
<body>

<div id="counter"><span class="num">001</span><span>/ 012 FRAMES</span></div>

<nav>
  <div class="logo">S<span>.</span>SHELAR</div>
  <ul>
    <li><a href="#about">About</a></li>
    <li><a href="#education">Education</a></li>
    <li><a href="#skills">Skills</a></li>
    <li><a href="#work">Work</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
</nav>

<header class="hero">
  <div class="eyebrow">Frame 001 — Opening Shot</div>
  <div class="frame-wrap brackets">
    <span class="bl"></span><span class="br"></span>
    <img src="data:image/jpeg;base64,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
