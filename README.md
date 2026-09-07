<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Brain & Mind | DHANANJAYA 10 - Real Numbers</title>
  
  <!-- MathJax Configuration -->
  <script>
    window.MathJax = {
      tex: {
        inlineMath: [['\\(', '\\)'], ['$', '$']],
        displayMath: [['\\[', '\\]'], ['$$', '$$']],
        processEscapes: true
      },
      options: {
        skipHtmlTags: ['script', 'noscript', 'style', 'textarea', 'pre', 'code']
      },
      startup: {
        pageReady: () => MathJax.startup.defaultPageReady()
      }
    };
  </script>
  <script type="text/javascript" id="MathJax-script" async
    src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
  </script>

  <style>
    :root {
      --primary-blue: #0284c7;
      --primary-dark: #0c4a6e;
      --accent-blue: #0ea5e9;
      --light-blue-bg: #f0f9ff;
      --light-blue-card: #f8fafc;
      --blue-border: #7dd3fc;
      --blue-border-soft: #bae6fd;
      --card-white: #ffffff;
      --correct-green: #059669;
      --correct-green-light: #d1fae5;
      --incorrect-red: #dc2626;
      --incorrect-red-light: #fee2e2;
      --brand-gold: #f59e0b;
      --brand-gold-dark: #d97706;
      --text-main: #0f172a;
      --text-muted: #475569;
      --radius-sm: 8px;
      --radius-md: 14px;
      --radius-lg: 20px;
      --shadow-sm: 0 1px 3px rgba(2, 132, 199, 0.08);
      --shadow-md: 0 4px 8px -1px rgba(2, 132, 199, 0.12);
      --shadow-lg: 0 12px 24px -4px rgba(12, 74, 110, 0.15);
    }

    * { box-sizing: border-box; margin: 0; padding: 0; }
    body {
      font-family: 'Segoe UI', -apple-system, BlinkMacSystemFont, Roboto, sans-serif;
      background: linear-gradient(180deg, #f0f9ff 0%, #ffffff 320px, #f0f9ff 100%);
      color: var(--text-main);
      line-height: 1.6;
      min-height: 100vh;
      display: flex;
      flex-direction: column;
    }

    header {
      background: linear-gradient(135deg, var(--primary-dark) 0%, #0369a1 60%, var(--primary-blue) 100%);
      color: #ffffff; padding: 0.85rem 1.75rem; box-shadow: var(--shadow-md); position: sticky; top: 0; z-index: 100;
    }
    .header-container {
      max-width: 1440px; margin: 0 auto; display: flex; justify-content: space-between; align-items: center; flex-wrap: wrap; gap: 1rem;
    }
    .brand-group { display: flex; align-items: center; gap: 14px; }
    .brand-logo-wrap {
      background: #ffffff; padding: 6px 12px; border-radius: 12px; display: flex; align-items: center; justify-content: center; box-shadow: 0 2px 8px rgba(0,0,0,0.15);
    }
    .brand-logo-svg { width: 48px; height: 48px; display: block; }
    .brand-title h1 { font-size: 1.25rem; font-weight: 800; letter-spacing: -0.02em; }
    .brand-title p { font-size: 0.8rem; color: #bae6fd; font-weight: 600; }

    .timer-widget {
      display: none; align-items: center; gap: 8px; background: rgba(255, 255, 255, 0.18);
      border: 1px solid rgba(255, 255, 255, 0.3); padding: 5px 14px; border-radius: 20px;
    }
    .timer-display {
      font-family: 'Segoe UI', monospace; font-size: 1.05rem; font-weight: 800; color: #ffffff; letter-spacing: 1px; min-width: 54px; text-align: center;
    }
    .timer-btn {
      background: #ffffff; border: none; color: var(--primary-dark); font-size: 0.75rem; font-weight: 700;
      padding: 4px 9px; border-radius: 12px; cursor: pointer; transition: all 0.2s;
    }
    .timer-btn:hover { background: #e0f2fe; color: var(--primary-blue); }

    .toast-reminder {
      display: none; position: fixed; bottom: 25px; right: 25px; background: #0c4a6e; color: #ffffff;
      padding: 14px 22px; border-radius: 14px; box-shadow: 0 10px 25px rgba(0,0,0,0.25); border: 2px solid var(--blue-border);
      z-index: 1000; font-weight: 700; font-size: 0.95rem; animation: slideUp 0.3s ease-out;
    }
    @keyframes slideUp { from { transform: translateY(20px); opacity: 0; } to { transform: translateY(0); opacity: 1; } }

    .nav-tabs { display: none; align-items: center; gap: 8px; flex-wrap: wrap; }
    .tab-btn {
      background: rgba(255, 255, 255, 0.18); border: 1px solid rgba(255, 255, 255, 0.3);
      color: #ffffff; padding: 7px 15px; border-radius: 20px; cursor: pointer; font-size: 0.86rem; font-weight: 600; transition: all 0.2s;
    }
    .tab-btn:hover, .tab-btn.active {
      background: #ffffff; color: var(--primary-blue); box-shadow: 0 2px 8px rgba(0,0,0,0.12);
    }
    .user-actions { display: flex; align-items: center; gap: 10px; flex-wrap: wrap; }
    .user-badge {
      background: rgba(255, 255, 255, 0.18); border: 1px solid rgba(255, 255, 255, 0.3);
      padding: 6px 14px; border-radius: 20px; font-size: 0.85rem; color: #f1f5f9; display: flex; align-items: center; gap: 6px;
    }
    .btn-icon {
      background: rgba(255, 255, 255, 0.22); border: none; color: #ffffff; padding: 8px 14px; border-radius: var(--radius-sm); cursor: pointer; font-size: 0.85rem; font-weight: 600; transition: all 0.2s;
    }
    .btn-icon:hover { background: rgba(255, 255, 255, 0.35); }

    main { max-width: 1440px; width: 100%; margin: 1.5rem auto; padding: 0 1rem; flex: 1; }
    .view-section { display: none; }
    .view-section.active { display: block; animation: fadeIn 0.25s ease-in-out; }
    @keyframes fadeIn { from { opacity: 0; transform: translateY(6px); } to { opacity: 1; transform: translateY(0); } }

    .login-gate-card {
      max-width: 500px; margin: 3rem auto; background: var(--card-white); border-radius: var(--radius-lg);
      padding: 2.75rem 2.25rem; border: 2.5px solid var(--blue-border); box-shadow: var(--shadow-lg); text-align: center;
    }
    .login-lock-icon {
      width: 64px; height: 64px; margin: 0 auto 1.25rem auto; background: #e0f2fe; color: var(--primary-blue);
      border-radius: 50%; display: flex; align-items: center; justify-content: center; font-size: 1.8rem;
    }
    .login-gate-card h2 { color: var(--primary-dark); font-size: 1.5rem; margin-bottom: 0.5rem; font-weight: 800; }
    .login-gate-card p { color: var(--text-muted); font-size: 0.92rem; margin-bottom: 1.75rem; }
    .input-field-group { text-align: left; margin-bottom: 1.25rem; }
    .input-field-group label { display: block; font-size: 0.85rem; font-weight: 700; color: var(--primary-dark); margin-bottom: 6px; }
    .login-input {
      width: 100%; padding: 11px 14px; font-size: 1rem; border: 2px solid var(--blue-border-soft); border-radius: var(--radius-sm);
      outline: none; transition: border-color 0.2s; font-family: inherit;
    }
    .login-input:focus { border-color: var(--primary-blue); box-shadow: 0 0 0 3px rgba(2, 132, 199, 0.15); }
    .login-btn-submit {
      width: 100%; padding: 12px; background: linear-gradient(135deg, var(--primary-blue), var(--accent-blue));
      color: #ffffff; border: none; border-radius: var(--radius-sm); font-size: 1.05rem; font-weight: 700; cursor: pointer; transition: all 0.2s; margin-top: 0.5rem;
    }
    .login-btn-submit:hover { opacity: 0.95; transform: translateY(-1px); }
    .login-error-text {
      color: var(--incorrect-red); background: var(--incorrect-red-light); padding: 10px 14px; border-radius: var(--radius-sm);
      border: 1px solid #fecaca; font-size: 0.88rem; font-weight: 600; margin-top: 14px; display: none; line-height: 1.5; text-align: left;
    }

    .notes-card { max-width: 1100px; margin: 1rem auto 2rem auto; background: var(--card-white); border-radius: var(--radius-lg); padding: 2.5rem; border: 2px solid var(--blue-border-soft); box-shadow: var(--shadow-lg); }
    .notes-header { border-bottom: 2px solid var(--blue-border-soft); padding-bottom: 1.25rem; margin-bottom: 1.5rem; }
    .notes-header h2 { color: var(--primary-dark); font-size: 1.7rem; }
    .notes-body h3 { color: var(--primary-blue); margin: 1.8rem 0 0.6rem 0; font-size: 1.22rem; border-bottom: 1.5px solid var(--blue-border-soft); padding-bottom: 5px; display: flex; align-items: center; gap: 8px; }
    .notes-body p, .notes-body ul, .notes-body ol { color: var(--text-main); font-size: 1.02rem; line-height: 1.8; margin-bottom: 1rem; }
    .notes-body ul, .notes-body ol { padding-left: 1.6rem; }
    .formula-callout { background: #f0f9ff; border: 1px solid var(--blue-border-soft); border-left: 4px solid var(--primary-blue); padding: 14px 18px; border-radius: var(--radius-sm); margin: 14px 0; font-size: 1.05rem; }
    .video-callout { background: #eff6ff; border: 1.5px solid #bfdbfe; border-radius: var(--radius-md); padding: 16px; margin: 16px 0; display: flex; justify-content: space-between; align-items: center; flex-wrap: wrap; gap: 12px; }
    .step-badge { display: inline-block; background: #e0f2fe; color: #0369a1; font-weight: 800; font-size: 0.8rem; padding: 2px 10px; border-radius: 12px; margin-right: 6px; }

    .learning-grid-layout { display: grid; grid-template-columns: 1fr 390px; gap: 1.5rem; align-items: start; }
    @media (max-width: 1080px) { .learning-grid-layout { grid-template-columns: 1fr; } }
    
    .problem-card { background: var(--card-white); border-radius: var(--radius-lg); padding: 2rem; box-shadow: var(--shadow-md); border: 2px solid var(--blue-border-soft); }
    .problem-header { display: flex; justify-content: space-between; align-items: center; margin-bottom: 1.25rem; padding-bottom: 0.75rem; border-bottom: 1.5px solid var(--blue-border-soft); }
    .p-tag { font-size: 1.15rem; font-weight: 800; color: var(--primary-blue); }
    .category-badge { background: #e0f2fe; color: var(--primary-dark); font-weight: 700; font-size: 0.8rem; padding: 3px 10px; border-radius: 6px; border: 1px solid var(--blue-border); margin-left: 8px; }
    .parts-badge { background: #fef3c7; color: #b45309; font-weight: 700; font-size: 0.8rem; padding: 3px 9px; border-radius: 6px; border: 1px solid #fde68a; margin-left: 6px; }
    .status-badge { font-size: 0.8rem; font-weight: 700; padding: 4px 10px; border-radius: 12px; text-transform: uppercase; }
    .badge-unvisited { background: #f8fafc; color: var(--text-muted); border: 1px solid #cbd5e1; }
    .badge-progress { background: #dbeafe; color: #1e40af; }
    .badge-complete { background: var(--correct-green-light); color: var(--correct-green); }
    .badge-skipped { background: #fef3c7; color: #b45309; }

    .problem-context { font-size: 1.15rem; font-weight: 500; margin-bottom: 1.25rem; background: #f0f9ff; border-left: 4px solid var(--accent-blue); padding: 16px 20px; border-radius: var(--radius-sm); line-height: 2.2; border: 1px solid var(--blue-border-soft); border-left-width: 4px; }

    .steps-container { display: flex; flex-direction: column; gap: 1.25rem; }
    .step-card { border: 2px solid var(--blue-border-soft); border-radius: var(--radius-md); padding: 1.25rem 1.5rem; background: #ffffff; transition: all 0.25s ease-in-out; }
    .step-card.active { border-color: var(--accent-blue); box-shadow: 0 4px 12px rgba(2, 132, 199, 0.15); }
    .step-card.completed { border-color: var(--correct-green); background: #fcfdfc; }
    
    .step-header-bar { display: flex; justify-content: space-between; align-items: center; margin-bottom: 0.75rem; }
    .step-title-text { font-weight: 700; font-size: 1rem; color: var(--primary-dark); }
    .step-status-indicator { font-size: 0.8rem; font-weight: 700; padding: 2px 8px; border-radius: 6px; }
    .step-card.completed .step-status-indicator { background: var(--correct-green-light); color: var(--correct-green); }
    .step-card.active .step-status-indicator { background: #e0f2fe; color: var(--primary-dark); }

    .step-prompt { font-size: 1.05rem; font-weight: 500; margin-bottom: 1rem; color: var(--text-main); line-height: 2.4; }

    .step-input {
      display: inline-block; width: 190px; padding: 7px 11px; font-size: 1.05rem; font-weight: 700; font-family: 'Segoe UI', monospace;
      text-align: center; color: var(--primary-blue); background: #ffffff; border: 2px solid #7dd3fc; border-radius: var(--radius-sm); outline: none; margin: 0 4px; vertical-align: middle;
    }
    .step-input:focus { border-color: var(--primary-blue); box-shadow: 0 0 0 3px rgba(2, 132, 199, 0.2); }
    .step-input.input-correct { border-color: var(--correct-green) !important; background: var(--correct-green-light) !important; color: #065f46 !important; }
    .step-input.input-incorrect { border-color: var(--incorrect-red) !important; background: var(--incorrect-red-light) !important; color: #991b1b !important; }

    .step-controls { display: flex; justify-content: space-between; align-items: center; flex-wrap: wrap; gap: 10px; margin-top: 0.75rem; padding-top: 0.75rem; border-top: 1px dashed var(--blue-border-soft); }
    .step-feedback-msg { font-size: 0.88rem; font-weight: 600; }
    .step-feedback-msg.correct { color: #166534; }
    .step-feedback-msg.incorrect { color: #b91c1c; }

    .tools-panel {
      background: #f0f9ff; border: 1.5px solid var(--blue-border); border-radius: var(--radius-md); padding: 1rem; margin-bottom: 1.25rem;
    }
    .tool-tab-header {
      display: flex; gap: 8px; border-bottom: 1.5px solid var(--blue-border-soft); padding-bottom: 8px; margin-bottom: 12px;
    }
    .tool-tab-btn {
      background: none; border: none; font-size: 0.85rem; font-weight: 700; color: var(--text-muted); cursor: pointer; padding: 4px 8px; border-radius: 4px;
    }
    .tool-tab-btn.active { color: var(--primary-blue); background: #e0f2fe; }
    .math-pad-grid { display: grid; grid-template-columns: repeat(7, 1fr); gap: 6px; }
    .math-pad-btn {
      background: #ffffff; border: 1px solid var(--blue-border); padding: 8px 4px; border-radius: var(--radius-sm); font-weight: 700; font-size: 0.95rem; cursor: pointer; text-align: center; color: var(--primary-dark);
    }
    .math-pad-btn:hover { background: var(--primary-blue); color: #ffffff; }

    .calc-box { background: #ffffff; border: 1.5px solid var(--blue-border); border-radius: var(--radius-sm); padding: 10px; }
    .calc-screen { width: 100%; background: #0c4a6e; color: #7dd3fc; font-family: monospace; font-size: 1.1rem; padding: 10px; border-radius: 4px; text-align: right; margin-bottom: 8px; overflow-x: auto; }
    .calc-grid { display: grid; grid-template-columns: repeat(4, 1fr); gap: 6px; }
    .calc-btn { background: #f0f9ff; border: 1px solid var(--blue-border-soft); padding: 8px; border-radius: 4px; font-weight: 700; font-size: 0.9rem; cursor: pointer; text-align: center; color: var(--primary-dark); }
    .calc-btn:hover { background: #e0f2fe; }
    .calc-btn.op { background: #bae6fd; color: #0c4a6e; }
    .calc-btn.eq { background: var(--primary-blue); color: #fff; }

    .palette-card { background: var(--card-white); border-radius: var(--radius-lg); padding: 1.25rem; border: 2px solid var(--blue-border-soft); position: sticky; top: 90px; box-shadow: var(--shadow-md); }
    .palette-grid { display: grid; grid-template-columns: repeat(5, 1fr); gap: 6px; margin: 1rem 0; max-height: 380px; overflow-y: auto; padding-right: 4px; }
    .palette-btn { aspect-ratio: 1; border-radius: var(--radius-sm); border: 1.5px solid var(--blue-border-soft); background: #f8fafc; color: var(--text-muted); font-weight: 700; cursor: pointer; display: flex; align-items: center; justify-content: center; font-size: 0.85rem; }
    .palette-btn.active { border: 2.5px solid var(--primary-blue) !important; background: #e0f2fe !important; color: var(--primary-blue) !important; }
    .palette-btn.completed { background: var(--correct-green) !important; color: #ffffff !important; border-color: var(--correct-green) !important; }
    .palette-btn.progress { background: #93c5fd !important; border-color: #3b82f6 !important; color: #0f172a !important; }
    .palette-btn.skipped { background: #fef3c7 !important; color: #b45309 !important; border-color: #fde68a !important; }

    .problem-action-bar { display: flex; justify-content: space-between; align-items: center; padding-top: 1.25rem; border-top: 1.5px solid var(--blue-border-soft); margin-top: 1.5rem; flex-wrap: wrap; gap: 10px; }
    .btn { padding: 9px 16px; border-radius: var(--radius-sm); font-weight: 700; font-size: 0.92rem; cursor: pointer; border: none; display: inline-flex; align-items: center; gap: 6px; transition: all 0.2s ease; }
    .btn-step-check { background: var(--primary-blue); color: #ffffff; }
    .btn-step-back { background: #f0f9ff; color: var(--primary-dark); border: 1px solid var(--blue-border); }
    .btn-secondary { background: #e2e8f0; color: var(--text-main); }
    .btn-skip { background: #ffffff; color: var(--brand-gold-dark); border: 1.5px solid var(--brand-gold-dark); }

    .score-hero-card { background: linear-gradient(135deg, var(--primary-dark) 0%, var(--primary-blue) 60%, var(--accent-blue) 100%); color: #ffffff; border-radius: var(--radius-lg); padding: 2.5rem 2rem; text-align: center; margin-bottom: 2rem; box-shadow: var(--shadow-lg); }
    .score-circle { width: 115px; height: 115px; border-radius: 50%; background: rgba(255,255,255,0.15); border: 4px solid #7dd3fc; display: flex; flex-direction: column; align-items: center; justify-content: center; margin: 0 auto 1rem auto; }
    .stats-row { display: grid; grid-template-columns: repeat(auto-fit, minmax(120px, 1fr)); gap: 1rem; max-width: 600px; margin: 1.5rem auto 0 auto; }
    .stat-pill { background: rgba(255,255,255,0.12); padding: 10px; border-radius: var(--radius-md); }
    .review-card { background: #ffffff; border: 2px solid var(--blue-border-soft); border-radius: var(--radius-md); padding: 1.5rem; margin-bottom: 1rem; box-shadow: var(--shadow-sm); line-height: 2.2; }
  </style>
</head>
<body>

  <!-- Header -->
  <header>
    <div class="header-container">
      <div class="brand-group">
        <div class="brand-logo-wrap">
          <svg class="brand-logo-svg" viewBox="0 0 160 160" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M45 42 C66 22, 94 22, 115 42" stroke="#f59e0b" stroke-width="8" stroke-linecap="round" fill="none"/>
            <path d="M56 56 C70 42, 90 42, 104 56" stroke="#f59e0b" stroke-width="8" stroke-linecap="round" fill="none"/>
            <path d="M68 70 C75 62, 85 62, 92 70" stroke="#f59e0b" stroke-width="7" stroke-linecap="round" fill="none"/>
            <path d="M25 80 L76 96 L76 136 L25 120 Z" stroke="#334155" stroke-width="7" fill="#ffffff" stroke-linejoin="round"/>
            <path d="M135 80 L84 96 L84 136 L135 120 Z" stroke="#334155" stroke-width="7" fill="#ffffff" stroke-linejoin="round"/>
            <line x1="40" y1="94" x2="68" y2="103" stroke="#334155" stroke-width="5" stroke-linecap="round"/>
            <line x1="40" y1="108" x2="68" y2="117" stroke="#334155" stroke-width="5" stroke-linecap="round"/>
            <line x1="120" y1="94" x2="92" y2="103" stroke="#334155" stroke-width="5" stroke-linecap="round"/>
            <line x1="120" y1="108" x2="92" y2="117" stroke="#334155" stroke-width="5" stroke-linecap="round"/>
          </svg>
        </div>
        <div class="brand-title">
          <h1>Brain &amp; Mind Academy</h1>
          <p>B&amp;M - The Experts • DHANANJAYA 10 (CBSE Class 10: Real Numbers)</p>
        </div>
      </div>

      <div class="timer-widget" id="mainTimerWidget">
        <span style="font-size:0.9rem;">⏱️</span>
        <span class="timer-display" id="timerDisplay">00:00</span>
        <button class="timer-btn" id="timerToggleBtn" onclick="toggleTimer()">Pause</button>
        <button class="timer-btn" onclick="resetTimer()">Reset</button>
        <button class="timer-btn" style="background:#e0f2fe; color:var(--primary-dark);" onclick="playReminderChime()">🔔 Test Sound</button>
      </div>

      <div class="nav-tabs" id="mainHeaderNav">
        <button class="tab-btn active" onclick="switchMainTab('theory')">📖 Theory Notes &amp; Videos</button>
        <button class="tab-btn" onclick="switchMainTab('sheet')">✍️ Board Practice Sheet (28 Items)</button>
        <button class="tab-btn" onclick="switchMainTab('solutions')">📋 Complete Solutions</button>
      </div>
      <div class="user-actions">
        <div class="user-badge"><span id="userEmailSpan">🔒 Locked Portal</span></div>
        <button class="btn-icon" id="soundToggleBtn"><span id="soundIcon">🔊</span></button>
      </div>
    </div>
  </header>

  <div id="reminderToast" class="toast-reminder"></div>

  <main>
    
    <!-- 0. COMPULSORY LOGIN GATE -->
    <section id="loginGateView" class="view-section active">
      <div class="login-gate-card">
        <div class="login-lock-icon">🔒</div>
        <h2>DHANANJAYA 10 Portal</h2>
        <p>CBSE Class 10 Board Series. Each student is allowed <strong>exactly one attempt</strong> unless reset by the administrator.</p>
        
        <form id="studentLoginForm" onsubmit="handlePortalLogin(event)">
          <div class="input-field-group">
            <label for="studentIdInput">Student ID / Roll No</label>
            <input type="text" id="studentIdInput" class="login-input" placeholder="e.g. DHANANJAY-101" required autocomplete="username" />
          </div>
          <div class="input-field-group">
            <label for="studentPasscodeInput">Security Passcode</label>
            <input type="password" id="studentPasscodeInput" class="login-input" placeholder="••••••••" required autocomplete="current-password" />
          </div>
          <button type="submit" class="login-btn-submit" id="loginSubmitBtn">Authenticate &amp; Open Real Numbers</button>
          <div class="login-error-text" id="loginErrorMsg"></div>
        </form>
      </div>
    </section>

    <!-- 1. Theory Notes & Topic Videos -->
    <section id="theoryView" class="view-section">
      <div class="notes-card">
        <div class="notes-header">
          <h2>Chapter 1: Real Numbers — Complete CBSE Board Theory</h2>
          <p style="color: var(--text-muted); font-size: 0.95rem;">Fundamental Theorem of Arithmetic, Divisibility of Integers, and Proofs of Irrationality.</p>
        </div>

        <div class="notes-body">
          <h3><span class="step-badge">TOPIC 1</span> The Fundamental Theorem of Arithmetic</h3>
          <p>Every composite number can be expressed (factorised) as a product of primes, and this factorisation is unique, apart from the order in which the prime factors occur.</p>
          <div class="formula-callout">
            • <strong>General Form:</strong> \( x = p_1^{a_1} \cdot p_2^{a_2} \cdots p_k^{a_k} \), where \( p_1 < p_2 < \dots < p_k \) are prime numbers in ascending order.<br>
            • <strong>HCF &amp; LCM for Two Numbers:</strong><br>
            \( \text{HCF}(a, b) = \) Product of the smallest power of each common prime factor.<br>
            \( \text{LCM}(a, b) = \) Product of the greatest power of each prime factor involved.<br>
            • <strong>Key Property:</strong> \( \text{HCF}(a, b) \times \text{LCM}(a, b) = a \times b \).
          </div>
          <div class="video-callout">
            <div>
              <strong>🎥 Khan Academy Video Lesson:</strong>
              <div style="font-size:0.9rem; color:#1e40af;">Topic 1: The Fundamental Theorem of Arithmetic &amp; Prime Factorisation</div>
            </div>
            <a href="https://www.khanacademy.org/math/ncert-class-10/xd6a17b08edbd2443:real-numbers-ncert-new/xd6a17b08edbd2443:untitled-512/v/the-fundamental-theorem-of-arithmetic-india" target="_blank" class="btn btn-step-check" style="text-decoration:none;">Watch Lesson Video ↗</a>
          </div>

          <h3><span class="step-badge">TOPIC 2</span> Revisiting Irrational Numbers &amp; Proofs by Contradiction</h3>
          <p>A number is irrational if it cannot be expressed in the form \( \frac{p}{q} \), where \( p, q \in \mathbb{Z} \) and \( q \neq 0 \).</p>
          <div class="formula-callout">
            • <strong>Theorem 1.2:</strong> Let \( p \) be a prime number. If \( p \) divides \( a^2 \), then \( p \) divides \( a \) (where \( a \) is a positive integer).<br>
            • <strong>Proof Strategy for \( \sqrt{p} \):</strong> Assume \( \sqrt{p} = \frac{a}{b} \) with \( a, b \) coprime. Show \( p \mid a \) and \( p \mid b \). This contradicts coprimality.<br>
            • <strong>Linear Combinations:</strong> The sum/difference of a rational and irrational is irrational. The product of a non-zero rational and irrational is irrational.
          </div>
          <div class="video-callout">
            <div>
              <strong>🎥 Khan Academy Video Lesson:</strong>
              <div style="font-size:0.9rem; color:#1e40af;">Topic 2: Proof That \(\sqrt{2}\) is Irrational &amp; Contradiction Technique</div>
            </div>
            <a href="https://www.khanacademy.org/math/ncert-class-10/xd6a17b08edbd2443:real-numbers-ncert-new/xd6a17b08edbd2443:revisiting-irrational-numbers-india/v/proof-2-is-irrational-india" target="_blank" class="btn btn-step-check" style="text-decoration:none;">Watch Lesson Video ↗</a>
          </div>
        </div>

        <div style="margin-top:2rem; background:#f0f9ff; border:2px solid var(--blue-border); border-radius:var(--radius-md); padding:1.5rem; display:flex; justify-content:space-between; align-items:center; flex-wrap:wrap; gap:1rem;">
          <div>
            <strong>Ready to practice the complete NCERT question set?</strong>
            <p style="font-size: 0.9rem; color: var(--primary-dark); margin-top:2px;">Work through all 28 examples and exercise questions with step-by-step auto-verification.</p>
          </div>
          <button class="btn btn-primary" onclick="switchMainTab('sheet')" style="background:var(--primary-blue); color:#fff;">
            Start 28-Question Practice Sheet →
          </button>
        </div>
      </div>
    </section>

    <!-- 2. Guided Practice Sheet (Workspace) -->
    <section id="sheetView" class="view-section">
      <div class="learning-grid-layout">
        
        <div class="problem-card">
          <div class="problem-header">
            <div>
              <span class="p-tag" id="pNumberDisplay">Question 1</span>
              <span class="category-badge" id="pCategoryBadge">NCERT Example</span>
              <span class="parts-badge" id="pPartsBadge">2 Steps</span>
            </div>
            <div class="status-badge badge-unvisited" id="pStatusBadge">Unvisited</div>
          </div>
          
          <div class="problem-context" id="pContextDisplay"></div>

          <!-- On-Screen Virtual Tools -->
          <div class="tools-panel">
            <div class="tool-tab-header">
              <button class="tool-tab-btn active" id="tabPadBtn" onclick="switchToolTab('pad')">⌨️ Math Keypad</button>
              <button class="tool-tab-btn" id="tabCalcBtn" onclick="switchToolTab('calc')">🧮 Calculator</button>
            </div>
            
            <div id="mathPadView">
              <div class="math-pad-grid">
                <button class="math-pad-btn" onclick="insertSymbol('√')">√</button>
                <button class="math-pad-btn" onclick="insertSymbol('^')">^</button>
                <button class="math-pad-btn" onclick="insertSymbol('a')">a</button>
                <button class="math-pad-btn" onclick="insertSymbol('b')">b</button>
                <button class="math-pad-btn" onclick="insertSymbol('c')">c</button>
                <button class="math-pad-btn" onclick="insertSymbol('n')">n</button>
                <button class="math-pad-btn" onclick="insertSymbol('0')">0</button>
                <button class="math-pad-btn" onclick="insertSymbol('1')">1</button>
                <button class="math-pad-btn" onclick="insertSymbol('2')">2</button>
                <button class="math-pad-btn" onclick="insertSymbol('3')">3</button>
                <button class="math-pad-btn" onclick="insertSymbol('4')">4</button>
                <button class="math-pad-btn" onclick="insertSymbol('5')">5</button>
                <button class="math-pad-btn" onclick="insertSymbol('7')">7</button>
                <button class="math-pad-btn" onclick="insertSymbol('11')">11</button>
                <button class="math-pad-btn" onclick="insertSymbol('13')">13</button>
                <button class="math-pad-btn" onclick="insertSymbol('17')">17</button>
                <button class="math-pad-btn" onclick="insertSymbol('Yes')">Yes</button>
                <button class="math-pad-btn" onclick="insertSymbol('No')">No</button>
                <button class="math-pad-btn" onclick="insertSymbol('Composite')">Composite</button>
                <button class="math-pad-btn" onclick="insertSymbol('Irrational')">Irrational</button>
                <button class="math-pad-btn" style="background:#fee2e2; color:#dc2626;" onclick="clearActiveField()">Clear</button>
              </div>
            </div>

            <div id="calcView" style="display:none;">
              <div class="calc-box">
                <div class="calc-screen" id="calcScreen">0</div>
                <div class="calc-grid">
                  <button class="calc-btn" onclick="calcAppend('(')">(</button>
                  <button class="calc-btn" onclick="calcAppend(')')">)</button>
                  <button class="calc-btn" onclick="calcClear()">C</button>
                  <button class="calc-btn op" onclick="calcAppend('/')">/</button>
                  <button class="calc-btn" onclick="calcAppend('7')">7</button>
                  <button class="calc-btn" onclick="calcAppend('8')">8</button>
                  <button class="calc-btn" onclick="calcAppend('9')">9</button>
                  <button class="calc-btn op" onclick="calcAppend('*')">*</button>
                  <button class="calc-btn" onclick="calcAppend('4')">4</button>
                  <button class="calc-btn" onclick="calcAppend('5')">5</button>
                  <button class="calc-btn" onclick="calcAppend('6')">6</button>
                  <button class="calc-btn op" onclick="calcAppend('-')">-</button>
                  <button class="calc-btn" onclick="calcAppend('1')">1</button>
                  <button class="calc-btn" onclick="calcAppend('2')">2</button>
                  <button class="calc-btn" onclick="calcAppend('3')">3</button>
                  <button class="calc-btn op" onclick="calcAppend('+')">+</button>
                  <button class="calc-btn" onclick="calcAppend('0')">0</button>
                  <button class="calc-btn" onclick="calcAppend('.')">.</button>
                  <button class="calc-btn op" onclick="calcSqrt()">√</button>
                  <button class="calc-btn eq" onclick="calcEval()">=</button>
                </div>
              </div>
            </div>
          </div>

          <div class="steps-container" id="stepsListContainer"></div>

          <div class="problem-action-bar">
            <div style="display: flex; gap: 8px;">
              <button class="btn btn-secondary" id="prevProblemBtn">← Prev Question</button>
              <button class="btn btn-secondary" id="nextProblemBtn">Next Question →</button>
            </div>
            <button class="btn btn-skip" id="skipProblemBtn">Skip Question</button>
          </div>
        </div>

        <aside class="palette-card">
          <div style="display:flex; justify-content:space-between; align-items:center;">
            <strong style="color:var(--primary-dark); font-size:1.02rem;">28-Item Index</strong>
            <span style="font-size:0.85rem; color:var(--primary-blue); font-weight:700;" id="completionRateText">0/28 Solved</span>
          </div>
          <div class="palette-grid" id="paletteGridContainer"></div>
          <button class="btn btn-primary" id="finishAssessmentBtn" style="margin-top: 1.25rem; width: 100%; background:var(--primary-blue); color:#fff;">Finish &amp; View All Solutions</button>
        </aside>

      </div>
    </section>

    <!-- 3. Final Review & Complete Solutions -->
    <section id="solutionsView" class="view-section">
      <div class="score-hero-card">
        <span style="background:rgba(255,255,255,0.2); color:#bae6fd; padding:4px 10px; border-radius:12px; font-weight:700;">Board Diagnostic Report</span>
        <h2 style="margin: 0.5rem 0; font-size: 1.7rem;">Real Numbers Complete Chapter Performance</h2>
        <div class="score-circle">
          <div id="finalScoreVal" style="font-size:2rem; font-weight:800;">0</div>
          <div style="font-size:0.8rem; color:#bae6fd;">out of 28</div>
        </div>
        <p id="performanceFeedbackDesc" style="color: #bae6fd; font-size:0.95rem; max-width:540px; margin:0 auto;"></p>
        <div class="stats-row">
          <div class="stat-pill"><div style="font-size:0.75rem; color:#bae6fd;">Accuracy</div><div id="accuracyStat" style="font-size:1.2rem; font-weight:700;">0%</div></div>
          <div class="stat-pill"><div style="font-size:0.75rem; color:#bae6fd;">Solved</div><div id="correctCountStat" style="font-size:1.2rem; font-weight:700; color:#86efac;">0</div></div>
          <div class="stat-pill"><div style="font-size:0.75rem; color:#bae6fd;">Skipped</div><div id="skippedCountStat" style="font-size:1.2rem; font-weight:700; color:#fde047;">0</div></div>
        </div>
        <div style="margin-top: 1.5rem; display:flex; justify-content:center; gap:10px;">
          <button class="btn" style="background: rgba(255,255,255,0.25); color:#fff;" id="retakeQuizBtn">🔒 Exit &amp; Lock Session</button>
          <button class="btn" style="background:#fff; color:var(--primary-dark);" onclick="window.print()">🖨️ Print Solutions</button>
        </div>
      </div>
      <h3 style="color: var(--primary-dark); margin-bottom:1rem;">Complete Step-by-Step Solutions (Questions 1 to 28)</h3>
      <div id="reviewListContainer"></div>
    </section>

  </main>

  <script>
    const BACKEND_URL = "https://script.google.com/macros/s/AKfycbwmH_oK_IGRkYPm9DRcdKIdp7nSP2zyftCrnY-wwX45fd9KHfAt26VzOQy1QC7PMsOr/exec";

    let currentAuthUser = {
      studentId: "",
      studentName: ""
    };

    async function handlePortalLogin(e) {
      e.preventDefault();
      const sId = document.getElementById("studentIdInput").value.trim();
      const pass = document.getElementById("studentPasscodeInput").value.trim();
      const errEl = document.getElementById("loginErrorMsg");
      const btn = document.getElementById("loginSubmitBtn");

      errEl.style.display = "none";
      btn.disabled = true;
      btn.textContent = "Verifying with Database...";

      try {
        const response = await fetch(BACKEND_URL, {
          method: "POST",
          body: JSON.stringify({
            action: "verifyStudent",
            studentId: sId,
            accessKey: pass
          })
        });

        const result = await response.json();

        if (result.success) {
          currentAuthUser.studentId = sId;
          currentAuthUser.studentName = result.name || sId;
          sessionStorage.setItem("dhananjaya_auth_id", sId);
          sessionStorage.setItem("dhananjaya_auth_name", currentAuthUser.studentName);

          document.getElementById("userEmailSpan").textContent = `👤 ${currentAuthUser.studentName} (${sId})`;
          document.getElementById("mainTimerWidget").style.display = "flex";
          document.getElementById("mainHeaderNav").style.display = "flex";
          switchMainTab("sheet");
          startTimer();
        } else {
          errEl.textContent = result.error || "Access Denied: Invalid Student ID, Passcode, or Attempt Limit Reached.";
          errEl.style.display = "block";
        }
      } catch (err) {
        errEl.textContent = "Connection error while reaching the server. Please check your network.";
        errEl.style.display = "block";
      } finally {
        btn.disabled = false;
        btn.textContent = "Authenticate & Open Real Numbers";
      }
    }

    function sendReportToSheet(solvedCount, totalCount, totalSecs) {
      if (!currentAuthUser.studentId) return;

      const payload = {
        action: "submitReport",
        studentId: currentAuthUser.studentId,
        studentName: currentAuthUser.studentName,
        score: solvedCount,
        totalQuestions: totalCount,
        accuracy: Math.round((solvedCount / totalCount) * 100),
        timeSpent: formatTime(totalSecs),
        details: {
          assessment: "DHANANJAYA 10 - Real Numbers (NCERT Complete)",
          submittedAt: new Date().toISOString(),
          questionsSolved: solvedCount,
          questionsSkipped: totalCount - solvedCount
        }
      };

      fetch(BACKEND_URL, {
        method: "POST",
        mode: "no-cors",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify(payload)
      }).catch(() => {});
    }

    /* ==========================================================================
       COMPLETE 28 QUESTIONS & EXAMPLES (NCERT CHAPTER 1: REAL NUMBERS)
       ========================================================================== */
    const PROBLEMS_DATA = [
      // 1. Example 1
      {
        id: 1,
        title: "Question 1",
        category: "NCERT Example 1",
        partsInfo: "2 Steps Required",
        context: "Consider the numbers \\( 4^n \\), where \\( n \\) is a natural number. Check whether there is any value of \\( n \\) for which \\( 4^n \\) ends with the digit zero.",
        steps: [
          {
            title: "Step 1: Identify the Required Prime Factor",
            prompt: "If a number ends with 0, its prime factorisation must contain the prime factor: <input class='step-input' style='width:50px;' data-ans='5'>",
            explanation: "Numbers ending with the digit 0 must be divisible by 10, hence divisible by 2 and 5."
          },
          {
            title: "Step 2: Check Uniqueness of Factors for 4^n",
            prompt: "Since \\( 4^n = (2^2)^n = 2^{2n} \\), the only prime factor is 2. Can \\( 4^n \\) ever end with 0? Enter 'Yes' or 'No': <input class='step-input' style='width:60px;' data-ans='No' data-alt='no'>",
            explanation: "By the Fundamental Theorem of Arithmetic, the prime factorisation is unique. 5 is not present, so 4^n never ends with 0."
          }
        ]
      },
      // 2. Example 2
      {
        id: 2,
        title: "Question 2",
        category: "NCERT Example 2",
        partsInfo: "2 Steps Required",
        context: "Find the LCM and HCF of 6 and 20 by the prime factorisation method.",
        steps: [
          {
            title: "Step 1: Find the HCF",
            prompt: "\\( 6 = 2 \\times 3 \\), \\( 20 = 2^2 \\times 5 \\). HCF = \\( 2^1 = \\) <input class='step-input' style='width:50px;' data-ans='2'>",
            explanation: "HCF is the product of the smallest power of each common prime factor = 2."
          },
          {
            title: "Step 2: Find the LCM",
            prompt: "LCM = \\( 2^2 \\times 3 \\times 5 = \\) <input class='step-input' style='width:60px;' data-ans='60'>",
            explanation: "LCM is the product of the highest power of each prime factor = 4 * 3 * 5 = 60."
          }
        ]
      },
      // 3. Example 3
      {
        id: 3,
        title: "Question 3",
        category: "NCERT Example 3",
        partsInfo: "2 Steps Required",
        context: "Find the HCF of 96 and 404 by the prime factorisation method. Hence, find their LCM.",
        steps: [
          {
            title: "Step 1: Compute HCF(96, 404)",
            prompt: "\\( 96 = 2^5 \\times 3 \\) and \\( 404 = 2^2 \\times 101 \\). HCF = \\( 2^2 = \\) <input class='step-input' style='width:50px;' data-ans='4'>",
            explanation: "Common factor is 2^2 = 4."
          },
          {
            title: "Step 2: Compute LCM Using HCF * LCM = a * b",
            prompt: "\\( \\text{LCM} = \\frac{96 \\times 404}{4} = \\) <input class='step-input' style='width:80px;' data-ans='9696'>",
            explanation: "LCM(96, 404) = (96 * 404) / 4 = 9696."
          }
        ]
      },
      // 4. Example 4
      {
        id: 4,
        title: "Question 4",
        category: "NCERT Example 4",
        partsInfo: "3 Steps Required",
        context: "Find the HCF and LCM of 6, 72 and 120, using the prime factorisation method.",
        steps: [
          {
            title: "Step 1: Prime Factorisation",
            prompt: "\\( 6 = 2 \\times 3 \\), \\( 72 = 2^3 \\times 3^2 \\), \\( 120 = 2^3 \\times 3 \\times 5 \\). HCF = \\( 2^1 \\times 3^1 = \\) <input class='step-input' style='width:50px;' data-ans='6'>",
            explanation: "Smallest powers of common prime factors: 2^1 * 3^1 = 6."
          },
          {
            title: "Step 2: Compute LCM",
            prompt: "LCM = \\( 2^3 \\times 3^2 \\times 5^1 = 8 \\times 9 \\times 5 = \\) <input class='step-input' style='width:60px;' data-ans='360'>",
            explanation: "Greatest powers of involved primes: 2^3 * 3^2 * 5^1 = 360."
          },
          {
            title: "Step 3: Three-Number Verification Check",
            prompt: "Does \\( \\text{HCF} \\times \\text{LCM} = 6 \\times 72 \\times 120 \\)? Enter 'Yes' or 'No': <input class='step-input' style='width:60px;' data-ans='No' data-alt='no'>",
            explanation: "No, the product formula HCF * LCM = product of numbers does NOT hold for three numbers."
          }
        ]
      },
      // 5. Ex 1.1, Q1(i)
      {
        id: 5,
        title: "Question 5",
        category: "Exercise 1.1, Q1(i)",
        partsInfo: "2 Steps Required",
        context: "Express 140 as a product of its prime factors.",
        steps: [
          {
            title: "Step 1: Divide by Smallest Primes",
            prompt: "\\( 140 \\div 2 = 70 \\), \\( 70 \\div 2 = 35 \\), \\( 35 \\div 5 = \\) <input class='step-input' style='width:50px;' data-ans='7'>",
            explanation: "140 = 2 * 2 * 5 * 7."
          },
          {
            title: "Step 2: Exponential Form",
            prompt: "Enter as product (e.g. 2^2*5*7): <input class='step-input' style='width:120px;' data-ans='2^2*5*7' data-alt='2^2 * 5 * 7|2^2x5x7'>",
            explanation: "140 = 2^2 * 5 * 7."
          }
        ]
      },
      // 6. Ex 1.1, Q1(ii)
      {
        id: 6,
        title: "Question 6",
        category: "Exercise 1.1, Q1(ii)",
        partsInfo: "2 Steps Required",
        context: "Express 156 as a product of its prime factors.",
        steps: [
          {
            title: "Step 1: Successive Prime Division",
            prompt: "\\( 156 \\div 2 = 78 \\), \\( 78 \\div 2 = 39 \\), \\( 39 \\div 3 = \\) <input class='step-input' style='width:50px;' data-ans='13'>",
            explanation: "156 = 2 * 2 * 3 * 13."
          },
          {
            title: "Step 2: Prime Product Form",
            prompt: "Enter prime factorisation (e.g. 2^2*3*13): <input class='step-input' style='width:120px;' data-ans='2^2*3*13' data-alt='2^2 * 3 * 13'>",
            explanation: "156 = 2^2 * 3 * 13."
          }
        ]
      },
      // 7. Ex 1.1, Q1(iii)
      {
        id: 7,
        title: "Question 7",
        category: "Exercise 1.1, Q1(iii)",
        partsInfo: "2 Steps Required",
        context: "Express 3825 as a product of its prime factors.",
        steps: [
          {
            title: "Step 1: Check Divisibility",
            prompt: "Sum of digits is 18 (divisible by 9). \\( 3825 \\div 9 = 425 \\). \\( 425 \\div 25 = \\) <input class='step-input' style='width:50px;' data-ans='17'>",
            explanation: "3825 = 3^2 * 5^2 * 17."
          },
          {
            title: "Step 2: Prime Product Form",
            prompt: "Enter prime factorisation: <input class='step-input' style='width:130px;' data-ans='3^2*5^2*17' data-alt='3^2 * 5^2 * 17'>",
            explanation: "3825 = 3^2 * 5^2 * 17."
          }
        ]
      },
      // 8. Ex 1.1, Q1(iv)
      {
        id: 8,
        title: "Question 8",
        category: "Exercise 1.1, Q1(iv)",
        partsInfo: "2 Steps Required",
        context: "Express 5005 as a product of its prime factors.",
        steps: [
          {
            title: "Step 1: Sequential Prime Factoring",
            prompt: "\\( 5005 \\div 5 = 1001 \\). Next prime dividing 1001 is 7: \\( 1001 \\div 7 = 143 \\). \\( 143 \\div 11 = \\) <input class='step-input' style='width:50px;' data-ans='13'>",
            explanation: "5005 = 5 * 7 * 11 * 13."
          },
          {
            title: "Step 2: Prime Product Form",
            prompt: "Enter product of primes: <input class='step-input' style='width:130px;' data-ans='5*7*11*13' data-alt='5 * 7 * 11 * 13'>",
            explanation: "5005 = 5 * 7 * 11 * 13."
          }
        ]
      },
      // 9. Ex 1.1, Q1(v)
      {
        id: 9,
        title: "Question 9",
        category: "Exercise 1.1, Q1(v)",
        partsInfo: "2 Steps Required",
        context: "Express 7429 as a product of its prime factors.",
        steps: [
          {
            title: "Step 1: Identify the Smallest Prime Factor",
            prompt: "Testing primes shows no factor below 17. \\( 7429 \\div 17 = 437 \\). \\( 437 \\div 19 = \\) <input class='step-input' style='width:50px;' data-ans='23'>",
            explanation: "7429 = 17 * 19 * 23."
          },
          {
            title: "Step 2: Prime Product Form",
            prompt: "Enter product of primes: <input class='step-input' style='width:120px;' data-ans='17*19*23' data-alt='17 * 19 * 23'>",
            explanation: "7429 = 17 * 19 * 23."
          }
        ]
      },
      // 10. Ex 1.1, Q2(i)
      {
        id: 10,
        title: "Question 10",
        category: "Exercise 1.1, Q2(i)",
        partsInfo: "3 Steps Required",
        context: "Find the LCM and HCF of 26 and 91 and verify that LCM * HCF = product of the two numbers.",
        steps: [
          {
            title: "Step 1: Find HCF and LCM",
            prompt: "\\( 26 = 2 \\times 13 \\), \\( 91 = 7 \\times 13 \\). HCF = <input class='step-input' style='width:50px;' data-ans='13'>, LCM = <input class='step-input' style='width:60px;' data-ans='182'>",
            explanation: "HCF = 13, LCM = 2 * 7 * 13 = 182."
          },
          {
            title: "Step 2: Compute Product of Numbers",
            prompt: "\\( 26 \\times 91 = \\) <input class='step-input' style='width:70px;' data-ans='2366'>",
            explanation: "26 * 91 = 2366."
          },
          {
            title: "Step 3: Verification",
            prompt: "Compute \\( 13 \\times 182 = \\) <input class='step-input' style='width:70px;' data-ans='2366'>. Are they equal? (Yes/No): <input class='step-input' style='width:60px;' data-ans='Yes' data-alt='yes'>",
            explanation: "Verified: HCF * LCM = 2366 = product of numbers."
          }
        ]
      },
      // 11. Ex 1.1, Q2(ii)
      {
        id: 11,
        title: "Question 11",
        category: "Exercise 1.1, Q2(ii)",
        partsInfo: "3 Steps Required",
        context: "Find the LCM and HCF of 510 and 92 and verify that LCM * HCF = product of the two numbers.",
        steps: [
          {
            title: "Step 1: Compute HCF and LCM",
            prompt: "\\( 510 = 2 \\times 3 \\times 5 \\times 17 \\), \\( 92 = 2^2 \\times 23 \\). HCF = <input class='step-input' style='width:50px;' data-ans='2'>, LCM = <input class='step-input' style='width:80px;' data-ans='23460'>",
            explanation: "HCF = 2. LCM = 4 * 3 * 5 * 17 * 23 = 23460."
          },
          {
            title: "Step 2: Product of Numbers",
            prompt: "\\( 510 \\times 92 = \\) <input class='step-input' style='width:80px;' data-ans='46920'>",
            explanation: "510 * 92 = 46920."
          },
          {
            title: "Step 3: Verification",
            prompt: "Compute \\( 2 \\times 23460 = \\) <input class='step-input' style='width:80px;' data-ans='46920'>",
            explanation: "Verified: LCM * HCF = 46920."
          }
        ]
      },
      // 12. Ex 1.1, Q2(iii)
      {
        id: 12,
        title: "Question 12",
        category: "Exercise 1.1, Q2(iii)",
        partsInfo: "3 Steps Required",
        context: "Find the LCM and HCF of 336 and 54 and verify that LCM * HCF = product of the two numbers.",
        steps: [
          {
            title: "Step 1: Compute HCF and LCM",
            prompt: "\\( 336 = 2^4 \\times 3 \\times 7 \\), \\( 54 = 2 \\times 3^3 \\). HCF = <input class='step-input' style='width:50px;' data-ans='6'>, LCM = <input class='step-input' style='width:70px;' data-ans='3024'>",
            explanation: "HCF = 2 * 3 = 6. LCM = 16 * 27 * 7 = 3024."
          },
          {
            title: "Step 2: Product of Numbers",
            prompt: "\\( 336 \\times 54 = \\) <input class='step-input' style='width:80px;' data-ans='18144'>",
            explanation: "336 * 54 = 18144."
          },
          {
            title: "Step 3: Verification",
            prompt: "Compute \\( 6 \\times 3024 = \\) <input class='step-input' style='width:80px;' data-ans='18144'>",
            explanation: "Verified: LCM * HCF = 18144."
          }
        ]
      },
      // 13. Ex 1.1, Q3(i)
      {
        id: 13,
        title: "Question 13",
        category: "Exercise 1.1, Q3(i)",
        partsInfo: "2 Steps Required",
        context: "Find the LCM and HCF of 12, 15 and 21 by applying the prime factorisation method.",
        steps: [
          {
            title: "Step 1: Compute HCF",
            prompt: "\\( 12 = 2^2 \\times 3 \\), \\( 15 = 3 \\times 5 \\), \\( 21 = 3 \\times 7 \\). HCF = <input class='step-input' style='width:50px;' data-ans='3'>",
            explanation: "Common prime factor is 3."
          },
          {
            title: "Step 2: Compute LCM",
            prompt: "LCM = \\( 2^2 \\times 3 \\times 5 \\times 7 = \\) <input class='step-input' style='width:60px;' data-ans='420'>",
            explanation: "LCM = 4 * 3 * 5 * 7 = 420."
          }
        ]
      },
      // 14. Ex 1.1, Q3(ii)
      {
        id: 14,
        title: "Question 14",
        category: "Exercise 1.1, Q3(ii)",
        partsInfo: "2 Steps Required",
        context: "Find the LCM and HCF of 17, 23 and 29 by applying the prime factorisation method.",
        steps: [
          {
            title: "Step 1: Compute HCF of Primes",
            prompt: "Since 17, 23, 29 are all prime numbers, their HCF is: <input class='step-input' style='width:50px;' data-ans='1'>",
            explanation: "Prime numbers share no common factors other than 1."
          },
          {
            title: "Step 2: Compute LCM",
            prompt: "\\( \\text{LCM} = 17 \\times 23 \\times 29 = \\) <input class='step-input' style='width:80px;' data-ans='11339'>",
            explanation: "17 * 23 * 29 = 11339."
          }
        ]
      },
      // 15. Ex 1.1, Q3(iii)
      {
        id: 15,
        title: "Question 15",
        category: "Exercise 1.1, Q3(iii)",
        partsInfo: "2 Steps Required",
        context: "Find the LCM and HCF of 8, 9 and 25 by applying the prime factorisation method.",
        steps: [
          {
            title: "Step 1: Compute HCF",
            prompt: "\\( 8 = 2^3 \\), \\( 9 = 3^2 \\), \\( 25 = 5^2 \\). HCF = <input class='step-input' style='width:50px;' data-ans='1'>",
            explanation: "No common prime factor exists, so HCF = 1."
          },
          {
            title: "Step 2: Compute LCM",
            prompt: "LCM = \\( 8 \\times 9 \\times 25 = \\) <input class='step-input' style='width:70px;' data-ans='1800'>",
            explanation: "LCM = 8 * 9 * 25 = 1800."
          }
        ]
      },
      // 16. Ex 1.1, Q4
      {
        id: 16,
        title: "Question 16",
        category: "Exercise 1.1, Q4",
        partsInfo: "2 Steps Required",
        context: "Given that HCF(306, 657) = 9, find LCM(306, 657).",
        steps: [
          {
            title: "Step 1: Apply Formula",
            prompt: "\\( \\text{LCM} = \\frac{306 \\times 657}{9} \\). First divide: \\( 306 \\div 9 = \\) <input class='step-input' style='width:50px;' data-ans='34'>",
            explanation: "306 / 9 = 34."
          },
          {
            title: "Step 2: Final Multiplication",
            prompt: "\\( 34 \\times 657 = \\) <input class='step-input' style='width:80px;' data-ans='22338'>",
            explanation: "LCM = 22338."
          }
        ]
      },
      // 17. Ex 1.1, Q5
      {
        id: 17,
        title: "Question 17",
        category: "Exercise 1.1, Q5",
        partsInfo: "2 Steps Required",
        context: "Check whether \\( 6^n \\) can end with the digit 0 for any natural number \\( n \\).",
        steps: [
          {
            title: "Step 1: Inspect Prime Factors of 6",
            prompt: "\\( 6^n = (2 \\times 3)^n = 2^n \\times 3^n \\). Does the prime factorisation contain 5? Enter 'Yes' or 'No': <input class='step-input' style='width:60px;' data-ans='No' data-alt='no'>",
            explanation: "Prime factors are only 2 and 3."
          },
          {
            title: "Step 2: Conclude Ending Digit",
            prompt: "Can \\( 6^n \\) end with digit 0? Enter 'Yes' or 'No': <input class='step-input' style='width:60px;' data-ans='No' data-alt='no'>",
            explanation: "Without 5 as a prime factor, it cannot end in 0."
          }
        ]
      },
      // 18. Ex 1.1, Q6
      {
        id: 18,
        title: "Question 18",
        category: "Exercise 1.1, Q6",
        partsInfo: "2 Steps Required",
        context: "Explain why \\( 7 \\times 11 \\times 13 + 13 \\) and \\( 7 \\times 6 \\times 5 \\times 4 \\times 3 \\times 2 \\times 1 + 5 \\) are composite numbers.",
        steps: [
          {
            title: "Step 1: Factor the First Expression",
            prompt: "\\( 13(7 \\times 11 + 1) = 13(77 + 1) = 13 \\times \\) <input class='step-input' style='width:50px;' data-ans='78'>",
            explanation: "Having factors other than 1 and itself makes it composite."
          },
          {
            title: "Step 2: Factor the Second Expression",
            prompt: "\\( 5(7 \\times 6 \\times 4 \\times 3 \\times 2 \\times 1 + 1) = 5(1008 + 1) = 5 \\times \\) <input class='step-input' style='width:60px;' data-ans='1009'>. Are both composite? (Yes/No): <input class='step-input' style='width:60px;' data-ans='Yes' data-alt='yes'>",
            explanation: "Both numbers can be expressed as product of multiple factors > 1, so both are composite."
          }
        ]
      },
      // 19. Ex 1.1, Q7
      {
        id: 19,
        title: "Question 19",
        category: "Exercise 1.1, Q7 (Word Problem)",
        partsInfo: "3 Steps Required",
        context: "There is a circular path around a sports field. Sonia takes 18 minutes to drive one round of the field, while Ravi takes 12 minutes for the same. Suppose they both start at the same point and at the same time, and go in the same direction. After how many minutes will they meet again at the starting point?",
        steps: [
          {
            title: "Step 1: Identify Required Operation",
            prompt: "To find when they next meet at the starting point, we must find the (Enter 'HCF' or 'LCM'): <input class='step-input' style='width:60px;' data-ans='LCM' data-alt='lcm'>",
            explanation: "The meeting time is the Least Common Multiple of both lap times."
          },
          {
            title: "Step 2: Prime Factorise Both Times",
            prompt: "\\( 18 = 2 \\times 3^2 \\) and \\( 12 = 2^2 \\times 3 \\).",
            explanation: "Highest powers: 2^2 and 3^2."
          },
          {
            title: "Step 3: Compute LCM",
            prompt: "\\( \\text{LCM}(18, 12) = 4 \\times 9 = \\) <input class='step-input' style='width:50px;' data-ans='36'> minutes",
            explanation: "They will meet again after 36 minutes."
          }
        ]
      },
      // 20. Theorem 1.3
      {
        id: 20,
        title: "Question 20",
        category: "NCERT Theorem 1.3",
        partsInfo: "3 Steps Required",
        context: "Complete the proof that \\( \\sqrt{2} \\) is irrational using proof by contradiction.",
        steps: [
          {
            title: "Step 1: Initial Assumption",
            prompt: "Assume \\( \\sqrt{2} = \\frac{a}{b} \\) where \\( a, b \\) are coprime integers. Squaring gives \\( 2b^2 = a^2 \\). This proves that 2 divides: <input class='step-input' style='width:50px;' data-ans='a^2' data-alt='a'>",
            explanation: "By Theorem 1.2, 2 divides a^2 and therefore 2 divides a."
          },
          {
            title: "Step 2: Substitute a = 2c",
            prompt: "\\( 2b^2 = (2c)^2 = 4c^2 \\implies b^2 = 2c^2 \\). This proves that 2 divides: <input class='step-input' style='width:50px;' data-ans='b^2' data-alt='b'>",
            explanation: "Therefore 2 divides b^2 and 2 divides b."
          },
          {
            title: "Step 3: Identify Contradiction",
            prompt: "Since 2 divides both \\( a \\) and \\( b \\), this contradicts our assumption that \\( a \\) and \\( b \\) are: <input class='step-input' style='width:90px;' data-ans='coprime' data-alt='co-prime|co prime'>",
            explanation: "Coprime means no common factors other than 1. Hence sqrt(2) is irrational."
          }
        ]
      },
      // 21. Example 5
      {
        id: 21,
        title: "Question 21",
        category: "NCERT Example 5",
        partsInfo: "3 Steps Required",
        context: "Prove that \\( \\sqrt{3} \\) is irrational.",
        steps: [
          {
            title: "Step 1: Set up Coprime Ratio",
            prompt: "Let \\( \\sqrt{3} = \\frac{a}{b} \\implies 3b^2 = a^2 \\). This means \\( a^2 \\) is divisible by: <input class='step-input' style='width:50px;' data-ans='3'>",
            explanation: "3 divides a^2, so 3 divides a."
          },
          {
            title: "Step 2: Substitute a = 3c",
            prompt: "\\( 3b^2 = (3c)^2 = 9c^2 \\implies b^2 = \\) <input class='step-input' style='width:60px;' data-ans='3c^2'>",
            explanation: "3 divides b^2, so 3 divides b."
          },
          {
            title: "Step 3: State Common Factor",
            prompt: "Both \\( a \\) and \\( b \\) share the common factor: <input class='step-input' style='width:50px;' data-ans='3'>",
            explanation: "Common factor 3 contradicts coprimality, proving sqrt(3) is irrational."
          }
        ]
      },
      // 22. Example 6
      {
        id: 22,
        title: "Question 22",
        category: "NCERT Example 6",
        partsInfo: "2 Steps Required",
        context: "Show that \\( 5 - \\sqrt{3} \\) is irrational.",
        steps: [
          {
            title: "Step 1: Isolate the Radical Term",
            prompt: "Assume \\( 5 - \\sqrt{3} = \\frac{a}{b} \\). Rearranging gives \\( \\sqrt{3} = \\frac{5b - a}{k} \\). What is denominator \\( k \\)? <input class='step-input' style='width:50px;' data-ans='b'>",
            explanation: "sqrt(3) = (5b - a) / b."
          },
          {
            title: "Step 2: Deduce Contradiction",
            prompt: "Since \\( a, b \\in \\mathbb{Z} \\), \\( \\frac{5b - a}{b} \\) is rational, meaning \\( \\sqrt{3} \\) would be rational. Does this contradict that \\( \\sqrt{3} \\) is irrational? (Yes/No): <input class='step-input' style='width:60px;' data-ans='Yes' data-alt='yes'>",
            explanation: "Contradiction confirms 5 - sqrt(3) is irrational."
          }
        ]
      },
      // 23. Example 7
      {
        id: 23,
        title: "Question 23",
        category: "NCERT Example 7",
        partsInfo: "2 Steps Required",
        context: "Show that \\( 3\\sqrt{2} \\) is irrational.",
        steps: [
          {
            title: "Step 1: Isolate the Radical",
            prompt: "Let \\( 3\\sqrt{2} = \\frac{a}{b} \\implies \\sqrt{2} = \\frac{a}{k} \\). What is \\( k \\)? <input class='step-input' style='width:50px;' data-ans='3b'>",
            explanation: "sqrt(2) = a / (3b)."
          },
          {
            title: "Step 2: Conclusion",
            prompt: "Since \\( a, 3, b \\) are integers, \\( \\frac{a}{3b} \\) is rational, contradicting the irrationality of: <input class='step-input' style='width:70px;' data-ans='√2' data-alt='sqrt(2)|sqrt 2'>",
            explanation: "Contradicts that sqrt(2) is irrational."
          }
        ]
      },
      // 24. Ex 1.2, Q1
      {
        id: 24,
        title: "Question 24",
        category: "Exercise 1.2, Q1",
        partsInfo: "3 Steps Required",
        context: "Prove that \\( \\sqrt{5} \\) is irrational.",
        steps: [
          {
            title: "Step 1: Square the Ratio",
            prompt: "Assume \\( \\sqrt{5} = \\frac{a}{b} \\) (coprime). \\( a^2 = \\) <input class='step-input' style='width:60px;' data-ans='5b^2'>",
            explanation: "5 divides a^2, hence 5 divides a."
          },
          {
            title: "Step 2: Substitute a = 5c",
            prompt: "\\( 5b^2 = (5c)^2 = 25c^2 \\implies b^2 = \\) <input class='step-input' style='width:60px;' data-ans='5c^2'>",
            explanation: "5 divides b^2, hence 5 divides b."
          },
          {
            title: "Step 3: Conclude Contradiction",
            prompt: "Both \\( a \\) and \\( b \\) have common factor: <input class='step-input' style='width:50px;' data-ans='5'>",
            explanation: "Contradicts that a and b are coprime, proving sqrt(5) is irrational."
          }
        ]
      },
      // 25. Ex 1.2, Q2
      {
        id: 25,
        title: "Question 25",
        category: "Exercise 1.2, Q2",
        partsInfo: "2 Steps Required",
        context: "Prove that \\( 3 + 2\\sqrt{5} \\) is irrational.",
        steps: [
          {
            title: "Step 1: Isolate sqrt(5)",
            prompt: "Let \\( 3 + 2\\sqrt{5} = \\frac{a}{b} \\implies 2\\sqrt{5} = \\frac{a}{b} - 3 = \\frac{a - 3b}{b} \\implies \\sqrt{5} = \\frac{a - 3b}{k} \\). What is \\( k \\)? <input class='step-input' style='width:50px;' data-ans='2b'>",
            explanation: "sqrt(5) = (a - 3b) / (2b)."
          },
          {
            title: "Step 2: Conclusion",
            prompt: "RHS is rational while LHS is irrational. Is \\( 3 + 2\\sqrt{5} \\) irrational? (Yes/No): <input class='step-input' style='width:60px;' data-ans='Yes' data-alt='yes'>",
            explanation: "Yes, 3 + 2*sqrt(5) is irrational."
          }
        ]
      },
      // 26. Ex 1.2, Q3(i)
      {
        id: 26,
        title: "Question 26",
        category: "Exercise 1.2, Q3(i)",
        partsInfo: "2 Steps Required",
        context: "Prove that \\( \\frac{1}{\\sqrt{2}} \\) is irrational.",
        steps: [
          {
            title: "Step 1: Invert the Rational Ratio",
            prompt: "Let \\( \\frac{1}{\\sqrt{2}} = \\frac{a}{b} \\implies \\sqrt{2} = \\) <input class='step-input' style='width:50px;' data-ans='b/a'>",
            explanation: "sqrt(2) = b / a."
          },
          {
            title: "Step 2: Contradiction",
            prompt: "Since \\( a, b \\neq 0 \\) are integers, \\( \\frac{b}{a} \\) is rational, which contradicts that \\( \\sqrt{2} \\) is: <input class='step-input' style='width:90px;' data-ans='irrational'>",
            explanation: "Contradiction proves 1/sqrt(2) is irrational."
          }
        ]
      },
      // 27. Ex 1.2, Q3(ii)
      {
        id: 27,
        title: "Question 27",
        category: "Exercise 1.2, Q3(ii)",
        partsInfo: "2 Steps Required",
        context: "Prove that \\( 7\\sqrt{5} \\) is irrational.",
        steps: [
          {
            title: "Step 1: Isolate sqrt(5)",
            prompt: "Let \\( 7\\sqrt{5} = \\frac{a}{b} \\implies \\sqrt{5} = \\frac{a}{k} \\). What is \\( k \\)? <input class='step-input' style='width:50px;' data-ans='7b'>",
            explanation: "sqrt(5) = a / (7b)."
          },
          {
            title: "Step 2: Conclusion",
            prompt: "Is \\( 7\\sqrt{5} \\) irrational? Enter 'Yes' or 'No': <input class='step-input' style='width:60px;' data-ans='Yes' data-alt='yes'>",
            explanation: "Yes, 7*sqrt(5) is irrational."
          }
        ]
      },
      // 28. Ex 1.2, Q3(iii)
      {
        id: 28,
        title: "Question 28",
        category: "Exercise 1.2, Q3(iii)",
        partsInfo: "2 Steps Required",
        context: "Prove that \\( 6 + \\sqrt{2} \\) is irrational.",
        steps: [
          {
            title: "Step 1: Isolate sqrt(2)",
            prompt: "Let \\( 6 + \\sqrt{2} = \\frac{a}{b} \\implies \\sqrt{2} = \\frac{a - kb}{b} \\). What integer is \\( k \\)? <input class='step-input' style='width:50px;' data-ans='6'>",
            explanation: "sqrt(2) = (a - 6b) / b."
          },
          {
            title: "Step 2: Final Verdict",
            prompt: "RHS is rational, which contradicts the known irrationality of \\( \\sqrt{2} \\). Is \\( 6 + \\sqrt{2} \\) irrational? (Yes/No): <input class='step-input' style='width:60px;' data-ans='Yes' data-alt='yes'>",
            explanation: "Yes, 6 + sqrt(2) is irrational."
          }
        ]
      }
    ];

    /* ==========================================================================
       STOPWATCH ENGINE WITH AUTOMATED MILESTONES
       ========================================================================== */
    let timerSeconds = 0;
    let timerInterval = null;
    let timerRunning = false;

    function formatTime(totalSecs) {
      const mins = Math.floor(totalSecs / 60);
      const secs = totalSecs % 60;
      return `${mins.toString().padStart(2, '0')}:${secs.toString().padStart(2, '0')}`;
    }

    function checkTimerSoundMilestones(secs) {
      if (secs === 1200) {
        playReminderChime();
        showToast("⏰ Milestone Alert: 20 minutes elapsed! Great focus, keep going!");
      } else if (secs > 1200 && (secs - 1200) % 300 === 0) {
        playReminderChime();
        const mins = Math.floor(secs / 60);
        showToast(`⏰ Pace Alert: ${mins} minutes elapsed.`);
      }
    }

    function showToast(msg) {
      const toast = document.getElementById('reminderToast');
      if (toast) {
        toast.textContent = msg;
        toast.style.display = 'block';
        setTimeout(() => { toast.style.display = 'none'; }, 6000);
      }
    }

    function startTimer() {
      if (!timerRunning) {
        timerRunning = true;
        document.getElementById('timerToggleBtn').textContent = 'Pause';
        timerInterval = setInterval(() => {
          timerSeconds++;
          document.getElementById('timerDisplay').textContent = formatTime(timerSeconds);
          checkTimerSoundMilestones(timerSeconds);
        }, 1000);
      }
    }

    function pauseTimer() {
      timerRunning = false;
      document.getElementById('timerToggleBtn').textContent = 'Resume';
      clearInterval(timerInterval);
    }

    function toggleTimer() {
      if (timerRunning) pauseTimer();
      else startTimer();
    }

    function resetTimer() {
      pauseTimer();
      timerSeconds = 0;
      document.getElementById('timerDisplay').textContent = '00:00';
      document.getElementById('timerToggleBtn').textContent = 'Start';
    }

    let soundEnabled = true;
    let audioCtx = null;

    function getAudioContext() {
      if (!audioCtx) {
        const AudioClass = window.AudioContext || window.webkitAudioContext;
        if (AudioClass) audioCtx = new AudioClass();
      }
      if (audioCtx && audioCtx.state === 'suspended') {
        audioCtx.resume().catch(() => {});
      }
      return audioCtx;
    }

    function playSound(type) {
      if (!soundEnabled) return;
      try {
        const ctx = getAudioContext();
        if (!ctx) return;
        const now = ctx.currentTime;
        if (type === 'correct') {
          const osc = ctx.createOscillator();
          const gain = ctx.createGain();
          osc.type = 'sine';
          osc.frequency.setValueAtTime(659.25, now);
          osc.frequency.exponentialRampToValueAtTime(880, now + 0.15);
          gain.gain.setValueAtTime(0.15, now);
          gain.gain.linearRampToValueAtTime(0.001, now + 0.25);
          osc.connect(gain);
          gain.connect(ctx.destination);
          osc.start(now);
          osc.stop(now + 0.26);
        } else if (type === 'incorrect') {
          const osc = ctx.createOscillator();
          const gain = ctx.createGain();
          osc.type = 'triangle';
          osc.frequency.setValueAtTime(196, now);
          osc.frequency.exponentialRampToValueAtTime(146, now + 0.18);
          gain.gain.setValueAtTime(0.15, now);
          gain.gain.linearRampToValueAtTime(0.001, now + 0.22);
          osc.connect(gain);
          gain.connect(ctx.destination);
          osc.start(now);
          osc.stop(now + 0.24);
        }
      } catch(e) {}
    }

    function playReminderChime() {
      if (!soundEnabled) return;
      try {
        const ctx = getAudioContext();
        if (!ctx) return;
        const now = ctx.currentTime;
        const chimeNotes = [523.25, 659.25, 783.99, 1046.50];
        chimeNotes.forEach((freq, idx) => {
          const osc = ctx.createOscillator();
          const gain = ctx.createGain();
          osc.type = 'sine';
          osc.frequency.setValueAtTime(freq, now + idx * 0.14);
          gain.gain.setValueAtTime(0.001, now + idx * 0.14);
          gain.gain.linearRampToValueAtTime(0.22, now + idx * 0.14 + 0.03);
          gain.gain.exponentialRampToValueAtTime(0.0001, now + idx * 0.14 + 0.65);
          osc.connect(gain);
          gain.connect(ctx.destination);
          osc.start(now + idx * 0.14);
          osc.stop(now + idx * 0.14 + 0.7);
        });
      } catch(e) {}
    }

    let state = {
      currentProblemIdx: 0,
      problems: {}
    };

    function getProblemState(idx) {
      if (!state.problems[idx]) {
        state.problems[idx] = { completedSteps: [], inputs: {}, isSolved: false, isSkipped: false };
      }
      return state.problems[idx];
    }

    function cleanString(s) {
      return (s || "").toString().trim().toLowerCase().replace(/\s+/g, '').replace(/−/g, '-');
    }

    function testInputMatching(userStr, targetStr, altStr) {
      const u = cleanString(userStr);
      const t = cleanString(targetStr);
      if (!u) return false;
      if (u === t) return true;
      if (altStr) {
        const alts = altStr.split('|').map(cleanString);
        if (alts.includes(u)) return true;
      }
      const numU = parseFloat(u);
      const numT = parseFloat(t);
      if (!isNaN(numU) && !isNaN(numT)) {
        return Math.abs(numU - numT) < 0.02;
      }
      return false;
    }

    function triggerMathTypeset() {
      if (window.MathJax && typeof window.MathJax.typesetPromise === 'function') {
        window.MathJax.typesetPromise().catch(() => {});
      }
    }

    let activeInputElement = null;
    window.trackActiveField = function(el) { activeInputElement = el; };
    window.insertSymbol = function(sym) {
      if (!activeInputElement) return;
      const start = activeInputElement.selectionStart || 0;
      const end = activeInputElement.selectionEnd || 0;
      const val = activeInputElement.value;
      activeInputElement.value = val.substring(0, start) + sym + val.substring(end);
      activeInputElement.focus();
      activeInputElement.dispatchEvent(new Event('input', { bubbles: true }));
    };
    window.clearActiveField = function() {
      if (!activeInputElement) return;
      activeInputElement.value = '';
      activeInputElement.dispatchEvent(new Event('input', { bubbles: true }));
      activeInputElement.focus();
    };

    window.switchToolTab = function(tab) {
      document.getElementById('tabPadBtn').classList.toggle('active', tab === 'pad');
      document.getElementById('tabCalcBtn').classList.toggle('active', tab === 'calc');
      document.getElementById('mathPadView').style.display = tab === 'pad' ? 'grid' : 'none';
      document.getElementById('calcView').style.display = tab === 'calc' ? 'block' : 'none';
    };

    let calcExpression = "";
    window.calcAppend = function(val) { calcExpression += val; document.getElementById('calcScreen').textContent = calcExpression || "0"; };
    window.calcClear = function() { calcExpression = ""; document.getElementById('calcScreen').textContent = "0"; };
    window.calcSqrt = function() {
      try { calcExpression = String(Math.sqrt(eval(calcExpression || "0"))); document.getElementById('calcScreen').textContent = calcExpression; } catch(e) {}
    };
    window.calcEval = function() {
      try { calcExpression = String(eval(calcExpression || "0")); document.getElementById('calcScreen').textContent = calcExpression; } catch(e) {}
    };

    function switchMainTab(tabId) {
      document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
      const targetBtn = Array.from(document.querySelectorAll('.tab-btn')).find(b => b.getAttribute('onclick') && b.getAttribute('onclick').includes(tabId));
      if (targetBtn) targetBtn.classList.add('active');

      document.querySelectorAll('.view-section').forEach(sec => sec.classList.remove('active'));
      const targetSec = document.getElementById(`${tabId}View`);
      if (targetSec) targetSec.classList.add('active');
      window.scrollTo({ top: 0, behavior: 'smooth' });

      if (tabId === 'sheet') {
        renderProblem(state.currentProblemIdx);
      }
      if (tabId === 'solutions') renderSolutions();
      triggerMathTypeset();
    }

    function renderProblem(idx) {
      if (idx < 0 || idx >= PROBLEMS_DATA.length) return;
      state.currentProblemIdx = idx;
      const prob = PROBLEMS_DATA[idx];
      const pState = getProblemState(idx);

      document.getElementById('pNumberDisplay').textContent = prob.title;
      document.getElementById('pCategoryBadge').textContent = prob.category;
      document.getElementById('pPartsBadge').textContent = prob.partsInfo;
      document.getElementById('pContextDisplay').innerHTML = prob.context;

      const badge = document.getElementById('pStatusBadge');
      if (pState.isSolved) { badge.className = 'status-badge badge-complete'; badge.textContent = 'Completed'; }
      else if (pState.isSkipped) { badge.className = 'status-badge badge-skipped'; badge.textContent = 'Skipped'; }
      else if (pState.completedSteps.length > 0) { badge.className = 'status-badge badge-progress'; badge.textContent = 'In Progress'; }
      else { badge.className = 'status-badge badge-unvisited'; badge.textContent = 'Unvisited'; }

      const container = document.getElementById('stepsListContainer');
      container.innerHTML = '';

      const maxStep = pState.isSolved ? prob.steps.length - 1 : Math.min(pState.completedSteps.length, prob.steps.length - 1);

      for (let sIdx = 0; sIdx <= maxStep; sIdx++) {
        const step = prob.steps[sIdx];
        const isDone = pState.completedSteps.includes(sIdx);

        const card = document.createElement('div');
        card.className = `step-card ${isDone ? 'completed' : 'active'}`;
        card.innerHTML = `
          <div class="step-header-bar">
            <div class="step-title-text">${step.title}</div>
            <span class="step-status-indicator">${isDone ? '✓ Verified' : 'Current Step'}</span>
          </div>
          <div class="step-prompt">${step.prompt}</div>
          <div class="step-controls">
            <div></div>
            <div style="display:flex; align-items:center; gap:8px;">
              <span class="step-feedback-msg" id="step-msg-${idx}-${sIdx}"></span>
              ${!isDone ? `
                <button class="btn btn-step-check" onclick="verifyStepAnswers(${idx}, ${sIdx})">
                  ${sIdx === prob.steps.length - 1 ? 'Verify & Finish Problem ✓' : 'Verify & Continue →'}
                </button>
              ` : '<span style="color:var(--correct-green); font-weight:700;">✓ Correct</span>'}
            </div>
          </div>
        `;
        container.appendChild(card);

        card.querySelectorAll('.step-input').forEach((inp, iIdx) => {
          const inputKey = `p${idx}_s${sIdx}_i${iIdx}`;
          inp.setAttribute('data-key', inputKey);
          inp.setAttribute('onfocus', 'trackActiveField(this)');
          if (pState.inputs[inputKey] !== undefined) inp.value = pState.inputs[inputKey];

          if (isDone) {
            inp.disabled = true;
            inp.classList.add('input-correct');
          } else {
            inp.addEventListener('input', (e) => { pState.inputs[inputKey] = e.target.value; });
            inp.addEventListener('keypress', (e) => { if (e.key === 'Enter') verifyStepAnswers(idx, sIdx); });
          }
        });
      }

      document.getElementById('prevProblemBtn').disabled = idx === 0;
      document.getElementById('nextProblemBtn').disabled = idx === PROBLEMS_DATA.length - 1;
      renderPalette();
      triggerMathTypeset();
    }

    window.verifyStepAnswers = function(pIdx, sIdx) {
      const prob = PROBLEMS_DATA[pIdx];
      const pState = getProblemState(pIdx);
      const card = document.querySelectorAll('.step-card')[sIdx];
      if (!card) return;

      const inputs = card.querySelectorAll('.step-input');
      let ok = true;

      inputs.forEach(inp => {
        const ans = inp.getAttribute('data-ans') || '';
        const alt = inp.getAttribute('data-alt') || '';
        const inputKey = inp.getAttribute('data-key');
        pState.inputs[inputKey] = inp.value;

        if (testInputMatching(inp.value, ans, alt)) {
          inp.classList.remove('input-incorrect');
          inp.classList.add('input-correct');
        } else {
          inp.classList.remove('input-correct');
          inp.classList.add('input-incorrect');
          ok = false;
        }
      });

      const msg = document.getElementById(`step-msg-${pIdx}-${sIdx}`);
      if (ok) {
        playSound('correct');
        if (!pState.completedSteps.includes(sIdx)) pState.completedSteps.push(sIdx);
        pState.isSkipped = false;
        if (msg) {
          msg.className = "step-feedback-msg correct";
          msg.textContent = "✓ Correct!";
        }
        if (pState.completedSteps.length === prob.steps.length) {
          pState.isSolved = true;
          setTimeout(() => renderProblem(pIdx), 350);
        } else {
          setTimeout(() => renderProblem(pIdx), 300);
        }
      } else {
        playSound('incorrect');
        if (msg) {
          msg.className = "step-feedback-msg incorrect";
          msg.textContent = "✗ Check calculation and try again.";
        }
      }
    };

    function renderPalette() {
      const grid = document.getElementById('paletteGridContainer');
      grid.innerHTML = '';
      let solvedCount = 0;

      PROBLEMS_DATA.forEach((p, idx) => {
        const btn = document.createElement('button');
        btn.className = 'palette-btn';
        btn.textContent = p.id;
        const ps = state.problems[idx];
        if (ps) {
          if (ps.isSolved) { btn.classList.add('completed'); solvedCount++; }
          else if (ps.isSkipped) btn.classList.add('skipped');
          else if (ps.completedSteps.length > 0) btn.classList.add('progress');
        }
        if (idx === state.currentProblemIdx) btn.classList.add('active');
        btn.onclick = () => renderProblem(idx);
        grid.appendChild(btn);
      });
      document.getElementById('completionRateText').textContent = `${solvedCount}/${PROBLEMS_DATA.length} Solved`;
    }

    document.getElementById('prevProblemBtn').onclick = () => { if (state.currentProblemIdx > 0) renderProblem(state.currentProblemIdx - 1); };
    document.getElementById('nextProblemBtn').onclick = () => { if (state.currentProblemIdx < PROBLEMS_DATA.length - 1) renderProblem(state.currentProblemIdx + 1); };
    document.getElementById('skipProblemBtn').onclick = () => {
      const ps = getProblemState(state.currentProblemIdx);
      ps.isSkipped = true;
      if (state.currentProblemIdx < PROBLEMS_DATA.length - 1) renderProblem(state.currentProblemIdx + 1);
      else renderProblem(state.currentProblemIdx);
    };

    document.getElementById('finishAssessmentBtn').onclick = () => {
      pauseTimer();
      switchMainTab('solutions');
    };

    function renderSolutions() {
      let solved = 0, skipped = 0;
      PROBLEMS_DATA.forEach((p, idx) => {
        const ps = state.problems[idx];
        if (ps && ps.isSolved) solved++;
        else if (ps && ps.isSkipped) skipped++;
      });
      const total = PROBLEMS_DATA.length;
      document.getElementById('finalScoreVal').textContent = solved;
      document.getElementById('accuracyStat').textContent = `${Math.round((solved/total)*100)}%`;
      document.getElementById('correctCountStat').textContent = solved;
      document.getElementById('skippedCountStat').textContent = skipped;

      const desc = document.getElementById('performanceFeedbackDesc');
      desc.textContent = solved === total 
        ? `🌟 Outstanding mastery! All ${total} NCERT Real Numbers problems solved flawlessly in ${formatTime(timerSeconds)}.` 
        : `Completed in ${formatTime(timerSeconds)}. Review the step rationales below to master Real Numbers for CBSE boards.`;

      const container = document.getElementById('reviewListContainer');
      container.innerHTML = '';

      PROBLEMS_DATA.forEach((prob, idx) => {
        const card = document.createElement('div');
        card.className = 'review-card';
        let stepsHTML = prob.steps.map(st => `
          <div style="margin-top:10px; padding:12px; background:#f0f9ff; border-left:3px solid var(--primary-blue); border-radius:4px; border:1px solid var(--blue-border-soft); border-left-width:3px;">
            <strong style="color:var(--primary-dark); font-size:0.95rem;">${st.title}</strong>
            <p style="margin-top:4px; font-size:0.95rem; color:#0c4a6e;">${st.explanation}</p>
          </div>
        `).join('');
        card.innerHTML = `
          <div style="display:flex; justify-content:space-between; align-items:center; margin-bottom:0.5rem;">
            <strong style="color:var(--primary-dark); font-size:1.1rem;">${prob.title} (${prob.category})</strong>
            <span class="status-badge ${state.problems[idx]?.isSolved ? 'badge-complete' : 'badge-skipped'}">
              ${state.problems[idx]?.isSolved ? 'Solved' : 'Review'}
            </span>
          </div>
          <div style="font-size:1.05rem; margin-bottom:0.5rem;">${prob.context}</div>
          ${stepsHTML}
        `;
        container.appendChild(card);
      });

      sendReportToSheet(solved, total, timerSeconds);
      triggerMathTypeset();
    }

    document.getElementById('retakeQuizBtn').onclick = () => {
      sessionStorage.clear();
      window.location.reload();
    };

    document.getElementById('soundToggleBtn').onclick = () => {
      soundEnabled = !soundEnabled;
      document.getElementById('soundIcon').textContent = soundEnabled ? '🔊' : '🔇';
    };

    window.addEventListener('DOMContentLoaded', () => {
      triggerMathTypeset();
    });
  </script>
</body>
</html>
