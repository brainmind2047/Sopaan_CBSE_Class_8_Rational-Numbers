<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Sopaan · Rational Numbers</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Fraunces:opsz,wght@9..144,500;9..144,700&family=Source+Sans+3:wght@400;600;700&family=IBM+Plex+Mono:wght@500;600&display=swap">
<style>
  html,body{margin:0;} img{max-width:100%;} [hidden]{display:none !important;}
  :root{
    --navy:#16264A; --navy-2:#1F3B6B; --gold:#C79A3E; --gold-soft:#F3E7C9;
    --paper:#FBF9F4; --paper-2:#F1EAD8; --card:#FFFFFF;
    --ink:#211E1A; --ink-soft:#655D4C; --rule:#E4DCC8;
    --success:#2E8B57; --success-soft:#E1F2E7;
    --danger:#BF4B45; --danger-soft:#FAE3E1;
    --locked:#C7BEA9;
    --focus:#1F3B6B;
    --accent-text:#1F3B6B; --retry-text:#8A661F;
    color-scheme:light;
  }
  @media (prefers-color-scheme: dark){
    :root:not([data-theme="light"]){
      --navy:#0E1830; --navy-2:#16264A; --gold:#E0B75B; --gold-soft:#3A2F16;
      --paper:#141210; --paper-2:#1C1914; --card:#1C1914;
      --ink:#EDE7DA; --ink-soft:#B2A996; --rule:#3A342A;
      --success:#7BC79A; --success-soft:#1B2E22;
      --danger:#E38884; --danger-soft:#331D1B;
      --locked:#4A4436;
      --focus:#E0B75B;
      --accent-text:#E0B75B; --retry-text:#E0B75B;
      color-scheme:dark;
    }
  }
  :root[data-theme="dark"]{
    --navy:#0E1830; --navy-2:#16264A; --gold:#E0B75B; --gold-soft:#3A2F16;
    --paper:#141210; --paper-2:#1C1914; --card:#1C1914;
    --ink:#EDE7DA; --ink-soft:#B2A996; --rule:#3A342A;
    --success:#7BC79A; --success-soft:#1B2E22;
    --danger:#E38884; --danger-soft:#331D1B;
    --locked:#4A4436;
    --focus:#E0B75B;
    --accent-text:#E0B75B; --retry-text:#E0B75B;
    color-scheme:dark;
  }

  *{box-sizing:border-box;}
  body{background:var(--paper); color:var(--ink); font-family:'Source Sans 3',-apple-system,'Segoe UI',sans-serif; padding-inline:0; padding-block:0;}
  h1,h2,h3{font-family:'Fraunces',Georgia,serif; text-wrap:balance; margin:0;}
  .num{font-family:'IBM Plex Mono',ui-monospace,monospace; font-variant-numeric:tabular-nums;}

  header.brand{
    background:linear-gradient(155deg,var(--navy) 0%, var(--navy-2) 100%);
    color:#F4EFDF; padding-block:calc(20px + env(safe-area-inset-top,0px)) 18px; padding-inline:20px;
  }
  .brand-row{display:flex; align-items:center; gap:12px; max-width:900px; margin:0 auto;}
  .crest{
    width:42px; height:42px; border-radius:10px; background:var(--gold); color:var(--navy);
    display:flex; align-items:center; justify-content:center; font-family:'Fraunces',serif; font-weight:700; font-size:18px; flex-shrink:0;
  }
  .brand-name{font-size:12px; letter-spacing:.08em; text-transform:uppercase; color:var(--gold); font-weight:700;}
  .series-name{font-size:19px; font-weight:700; font-family:'Fraunces',serif;}
  .chapter-eyebrow{max-width:900px; margin:14px auto 0; font-size:12px; letter-spacing:.06em; text-transform:uppercase; color:#AEB9D6;}
  .chapter-title{font-size:28px; max-width:900px; margin:2px auto 0;}
  .chapter-sub{font-size:14.5px; color:var(--gold); font-weight:700; max-width:900px; margin:3px auto 0;}

  .chapter-progress{max-width:900px; margin:14px auto 0; display:flex; align-items:center; gap:10px;}
  .cp-track{flex:1; height:6px; border-radius:99px; background:rgba(255,255,255,.18); overflow:hidden;}
  .cp-fill{height:100%; background:var(--gold); border-radius:99px; transition:width .3s ease;}
  .cp-label{font-size:11.5px; color:#CFD7EA; white-space:nowrap;}

  .tabbar{position:sticky; top:env(safe-area-inset-top,0px); z-index:15; background:var(--paper); border-bottom:1px solid var(--rule); overflow-x:auto; white-space:nowrap;}
  .tabbar-inner{max-width:900px; margin:0 auto; display:flex; padding-inline:16px;}
  .tab-btn{font-family:inherit; font-size:14px; font-weight:600; color:var(--ink-soft); background:none; border:none; padding:13px 16px; cursor:pointer; position:relative; flex-shrink:0;}
  .tab-btn.active{color:var(--accent-text);}
  .tab-btn.active::after{content:''; position:absolute; left:12px; right:12px; bottom:0; height:3px; background:var(--gold); border-radius:3px 3px 0 0;}
  .tab-count{font-size:11px; color:var(--ink-soft); margin-left:5px;}

  .slide-progress{max-width:900px; margin:0 auto; padding:10px 16px 0; display:flex; align-items:center; gap:10px;}
  .sp-track{flex:1; height:5px; border-radius:99px; background:var(--rule); overflow:hidden;}
  .sp-fill{height:100%; background:var(--accent-text); border-radius:99px; transition:width .3s ease;}
  .sp-label{font-size:12px; color:var(--ink-soft); white-space:nowrap; font-weight:600;}

  .wrap{max-width:900px; margin:0 auto; padding:16px 16px calc(110px + env(safe-area-inset-bottom,0px));}

  .qcard{background:var(--card); border:1px solid var(--rule); border-radius:14px; padding:18px;}
  .qhead{display:flex; align-items:flex-start; gap:10px; margin-bottom:10px;}
  .qnum{width:32px; height:32px; border-radius:8px; background:var(--gold-soft); color:var(--accent-text); display:flex; align-items:center; justify-content:center; font-weight:700; font-family:'Fraunces',serif; flex-shrink:0; font-size:14px;}
  .qtext{font-size:16px; line-height:1.55; flex:1;}
  .qtag{font-size:10.5px; color:var(--gold); background:var(--gold-soft); padding:2px 7px; border-radius:99px; font-weight:700; margin-left:6px; white-space:nowrap;}
  .marks-pill{font-size:11px; font-weight:700; color:var(--ink-soft); border:1px solid var(--rule); padding:3px 9px; border-radius:99px; margin-left:auto; flex-shrink:0; white-space:nowrap;}
  .step-badge{font-size:11px; font-weight:700; color:var(--accent-text); background:var(--paper-2); border:1px solid var(--rule); padding:3px 9px; border-radius:99px; display:inline-block; margin-bottom:12px;}

  .options{display:flex; flex-direction:column; gap:8px; margin-top:10px;}
  .opt{display:flex; align-items:center; gap:10px; padding:11px 12px; border:1.5px solid var(--rule); border-radius:10px; cursor:pointer; font-size:15px; background:var(--paper);}
  .opt input{accent-color:var(--navy-2);}
  .opt.is-correct{border-color:var(--success); background:var(--success-soft);}
  .opt.is-wrong{border-color:var(--danger); background:var(--danger-soft);}
  .opt.locked{cursor:not-allowed;}

  .subpart-label{font-weight:700; font-size:12.5px; color:var(--accent-text); text-transform:uppercase; letter-spacing:.03em; margin:14px 0 6px;}
  .or-divider{text-align:center; font-size:11px; font-weight:700; letter-spacing:.08em; color:var(--ink-soft); margin:8px 0;}

  .steps{display:flex; flex-direction:column; gap:10px;}
  .step-line{font-size:14.5px; line-height:1.9; background:var(--paper); border:1px dashed var(--rule); border-radius:10px; padding:9px 12px;}
  .step-line.resolved{opacity:.9;}
  .blank-input{font-family:'IBM Plex Mono',monospace; font-size:14px; border:1.5px solid var(--rule); border-radius:6px; padding:3px 8px; width:120px; background:var(--card); color:var(--ink); margin:0 2px;}
  .blank-input:focus{outline:none; border-color:var(--focus); box-shadow:0 0 0 3px var(--gold-soft);}
  .blank-input.is-correct{border-color:var(--success); background:var(--success-soft);}
  .blank-input.is-wrong{border-color:var(--danger); background:var(--danger-soft);}
  .blank-input[disabled]{opacity:.85;}
  .reveal-note{font-size:12px; color:var(--danger); padding-left:2px; margin-top:-2px;}

  .feedback{font-size:13.5px; padding:10px 12px; border-radius:9px; margin-top:14px; display:none;}
  .feedback.show{display:block;}
  .feedback.ok{background:var(--success-soft); color:var(--success);}
  .feedback.retry{background:var(--gold-soft); color:var(--retry-text);}
  .feedback.reveal{background:var(--danger-soft); color:var(--danger);}
  .feedback.err{background:var(--danger-soft); color:var(--danger);}
  .attempts-dots{display:inline-flex; gap:4px; margin-left:2px;}
  .attempts-dots span{width:6px; height:6px; border-radius:50%; background:var(--ink-soft); opacity:.3; display:inline-block;}
  .attempts-dots span.used{opacity:1; background:var(--danger);}

  .ar-box{background:var(--paper-2); border-radius:10px; padding:10px 12px; margin-bottom:12px; font-size:13px; color:var(--ink-soft);}

  .navbar{
    position:fixed; left:0; right:0; bottom:0; z-index:30; background:var(--paper);
    border-top:1px solid var(--rule); padding:10px 16px calc(10px + env(safe-area-inset-bottom,0px));
  }
  .navbar-inner{max-width:900px; margin:0 auto; display:flex; gap:8px; flex-wrap:wrap; align-items:center;}
  .btn{font-family:inherit; font-size:13.5px; font-weight:700; padding:10px 14px; border-radius:9px; border:1.5px solid var(--rule); background:var(--card); color:var(--ink); cursor:pointer;}
  .btn:hover{border-color:var(--navy-2);}
  .btn:disabled{opacity:.4; cursor:not-allowed;}
  .btn-primary{background:var(--navy-2); color:#fff; border-color:var(--navy-2);}
  .navbar .spacer{flex:1;}

  .fab{position:fixed; right:16px; bottom:calc(74px + env(safe-area-inset-bottom,0px)); background:var(--gold); color:var(--navy); border:none; border-radius:999px; padding:11px 16px; font-family:inherit; font-weight:700; font-size:13px; display:flex; align-items:center; gap:7px; cursor:pointer; box-shadow:0 6px 16px rgba(0,0,0,.18); z-index:35;}
  .fab-badge{background:rgba(255,255,255,.55); border-radius:99px; padding:1px 7px; font-size:11px;}

  .overlay{position:fixed; inset:0; background:rgba(20,18,14,.45); z-index:50; display:none; align-items:flex-end; justify-content:center;}
  .overlay.show{display:flex;}
  .palette{background:var(--card); width:min(480px,100%); max-height:78vh; overflow-y:auto; border-radius:18px 18px 0 0; padding:18px 18px calc(18px + env(safe-area-inset-bottom,0px)); border:1px solid var(--rule); border-bottom:none;}
  @media (min-width:640px){ .overlay{align-items:center;} .palette{border-radius:18px; border-bottom:1px solid var(--rule); max-height:74vh;} }
  .palette-head{display:flex; align-items:center; justify-content:space-between; margin-bottom:6px;}
  .palette-head h2{font-size:16px;}
  .palette-close{background:none; border:none; font-size:20px; color:var(--ink-soft); cursor:pointer; padding:4px;}
  .palette-legend{display:flex; gap:12px; flex-wrap:wrap; font-size:11px; color:var(--ink-soft); margin:10px 0 14px;}
  .palette-legend span{display:inline-flex; align-items:center; gap:5px;}
  .dot{width:9px; height:9px; border-radius:50%; display:inline-block;}
  .dot.correct{background:var(--success);} .dot.revealed{background:var(--danger);}
  .dot.skipped{background:var(--gold);} .dot.locked{background:var(--locked);}
  .dot.current{background:var(--navy-2);}
  .chip-grid{display:grid; grid-template-columns:repeat(auto-fill,minmax(48px,1fr)); gap:8px;}
  .chip{border:1.5px solid var(--rule); border-radius:9px; padding:8px 4px; text-align:center; font-family:'IBM Plex Mono',monospace; font-size:12.5px; font-weight:600; cursor:pointer; background:var(--paper); color:var(--ink);}
  .chip[data-status="correct"]{border-color:var(--success); background:var(--success-soft); color:var(--success);}
  .chip[data-status="revealed"]{border-color:var(--danger); background:var(--danger-soft); color:var(--danger);}
  .chip[data-status="skipped"]{border-color:var(--gold); background:var(--gold-soft); color:var(--retry-text);}
  .chip[data-status="locked"]{border-color:var(--rule); color:var(--locked); cursor:not-allowed; background:var(--paper-2);}
  .chip[data-status="current"]{outline:2px solid var(--navy-2); outline-offset:1px;}

  .toast{position:fixed; left:50%; bottom:calc(140px + env(safe-area-inset-bottom,0px)); transform:translateX(-50%); background:var(--ink); color:var(--paper); padding:9px 16px; border-radius:99px; font-size:13px; opacity:0; pointer-events:none; transition:opacity .25s ease; z-index:60;}
  .toast.show{opacity:1;}

  .done-card{text-align:center; padding:36px 20px;}
  .done-card .big{font-size:38px; margin-bottom:6px;}
  .score-pills{display:flex; gap:10px; justify-content:center; flex-wrap:wrap; margin:16px 0;}
  .score-pill{padding:8px 16px; border-radius:99px; font-size:13px; font-weight:700;}

  footer.brandfoot{max-width:900px; margin:14px auto 0; padding:0 16px calc(110px + env(safe-area-inset-bottom,0px)); text-align:center; font-size:12px; color:var(--ink-soft);}

  .mode-pill{font-family:inherit; font-size:12.5px; font-weight:700; color:var(--navy); background:var(--gold); border:none; border-radius:99px; padding:6px 14px; cursor:pointer; margin-top:12px; display:inline-flex; align-items:center; gap:6px;}
  .mode-pick{display:flex; flex-direction:column; gap:14px; padding:8px 0 24px;}
  .mode-card{background:var(--card); border:1.5px solid var(--rule); border-radius:16px; padding:22px; cursor:pointer; text-align:left;}
  .mode-card:hover{border-color:var(--navy-2);}
  .mode-card .mode-icon{font-size:26px; margin-bottom:8px;}
  .mode-card h3{font-size:18px; margin-bottom:6px;}
  .mode-card p{font-size:13.5px; color:var(--ink-soft); line-height:1.5; margin:0;}
  .quiz-hint{font-size:12.5px; color:var(--ink-soft); background:var(--paper-2); border-radius:9px; padding:8px 12px; margin-bottom:14px;}
  .review-row{border:1px solid var(--rule); border-radius:10px; padding:11px 13px; margin-bottom:10px;}
  .review-tag{font-size:11.5px; font-weight:700; margin-bottom:4px; display:block;}
  .review-tag.ok{color:var(--success);} .review-tag.bad{color:var(--danger);} .review-tag.na{color:var(--ink-soft);}
  .review-q{font-size:13.5px; margin-bottom:6px; color:var(--ink-soft);}
  .review-ans{font-size:13px; margin-bottom:2px;}

  .who-row{max-width:900px; margin:12px auto 0; display:flex; flex-wrap:wrap; gap:8px; align-items:center;}
  .who-row .mode-pill{margin-top:0;}
  .who{display:inline-flex; flex-wrap:wrap; align-items:center; gap:6px; font-size:12.5px; color:#CFD7EA;}
  .who b{color:#F4EFDF;}
  .who button{font-family:inherit; font-size:12px; font-weight:700; color:#F4EFDF; background:rgba(255,255,255,.12); border:1px solid rgba(255,255,255,.22); border-radius:99px; padding:5px 11px; cursor:pointer;}
  .who button:hover{background:rgba(255,255,255,.2);}
  .login-card{max-width:460px; margin:8px auto 0; background:var(--card); border:1px solid var(--rule); border-radius:16px; padding:22px;}
  .login-card h2{font-size:21px; margin-bottom:4px;}
  .login-card p.lead{font-size:13.5px; color:var(--ink-soft); margin:0 0 16px; line-height:1.5;}
  .fld{display:flex; flex-direction:column; gap:5px; margin-bottom:12px;}
  .fld label{font-size:12px; font-weight:700; letter-spacing:.04em; text-transform:uppercase; color:var(--ink-soft);}
  .fld input{font-family:inherit; font-size:15px; padding:10px 12px; border:1.5px solid var(--rule); border-radius:9px; background:var(--paper); color:var(--ink);}
  .fld input:focus{outline:none; border-color:var(--focus); box-shadow:0 0 0 3px var(--gold-soft);}
  .fld-row{display:grid; grid-template-columns:1fr 1fr; gap:10px;}
  .login-err{font-size:13px; color:var(--danger); background:var(--danger-soft); border-radius:8px; padding:8px 10px; margin-bottom:12px;}
  .login-note{font-size:12px; color:var(--ink-soft); margin-top:12px; line-height:1.5;}
  .known{margin:0 0 16px; display:flex; flex-direction:column; gap:6px;}
  .known-label{font-size:12px; font-weight:700; letter-spacing:.04em; text-transform:uppercase; color:var(--ink-soft);}
  .known-btn{display:flex; justify-content:space-between; align-items:center; gap:10px; text-align:left; font-family:inherit; font-size:14.5px; padding:10px 12px; border:1.5px solid var(--rule); border-radius:10px; background:var(--paper); color:var(--ink); cursor:pointer;}
  .known-btn:hover{border-color:var(--navy-2);}
  .known-btn small{font-size:12px; color:var(--ink-soft);}
  .rec-card{background:var(--card); border:1px solid var(--rule); border-radius:14px; padding:18px; margin-bottom:14px;}
  .rec-card h2{font-size:19px; margin-bottom:10px;}
  .rec-card h3{font-size:15px; margin:4px 0 8px;}
  .rec-table-wrap{overflow-x:auto;}
  .rec-table{width:100%; border-collapse:collapse; font-size:13.5px; font-variant-numeric:tabular-nums;}
  .rec-table th{text-align:left; font-size:11.5px; text-transform:uppercase; letter-spacing:.04em; color:var(--ink-soft); padding:6px 8px; border-bottom:1px solid var(--rule); white-space:nowrap;}
  .rec-table td{padding:8px; border-bottom:1px solid var(--rule); white-space:nowrap;}
  .rec-bar{display:inline-block; width:70px; height:6px; border-radius:99px; background:var(--rule); overflow:hidden; vertical-align:middle; margin-right:6px;}
  .rec-bar i{display:block; height:100%; background:var(--success);}
  .rec-empty{font-size:13.5px; color:var(--ink-soft);}
  .sec-sub{max-width:900px; margin:0 auto; padding:10px 16px 0; font-size:12.5px; font-weight:700; color:var(--accent-text); letter-spacing:.02em;}
  .opt{flex-wrap:wrap;}
  .opt-l{font-family:'IBM Plex Mono',monospace; font-size:13px; font-weight:600; color:var(--ink-soft);}
  .opt-t{flex:1; min-width:0;}
  .opt.is-chosen:not(.is-correct):not(.is-wrong){border-color:var(--navy-2); background:var(--gold-soft);}
  .opt-tag{font-size:11px; font-weight:700; padding:2px 8px; border-radius:99px; background:var(--card); border:1px solid currentColor; white-space:nowrap;}
  .opt.is-correct .opt-tag{color:var(--success);} .opt.is-wrong .opt-tag{color:var(--danger);} .opt.is-chosen:not(.is-correct):not(.is-wrong) .opt-tag{color:var(--accent-text);}
  .chosen{font-size:13.5px; margin-top:10px; padding:8px 12px; border-radius:9px;}
  .chosen.ok{background:var(--success-soft); color:var(--success);} .chosen.bad{background:var(--danger-soft); color:var(--danger);}
  .chosen + .chosen{margin-top:6px;}
  .solution{margin-top:14px; border:1px solid var(--rule); border-left:4px solid var(--gold); background:var(--paper-2); border-radius:10px; padding:12px 14px;}
  .sol-h{font-family:'Fraunces',Georgia,serif; font-weight:700; font-size:14px; color:var(--accent-text); margin-bottom:6px;}
  .sol-line{font-size:14.5px; line-height:1.7;}
  .rev-sol summary{cursor:pointer; font-size:12.5px; font-weight:700; color:var(--accent-text); margin-top:6px;}
  .rev-sol .solution{margin-top:8px;}
  .chapter-credit{max-width:900px; margin:4px auto 0; font-size:12px; color:#CFD7EA;}
  footer.brandfoot a{color:inherit;}
  .blank-input.wide{width:260px; max-width:100%; font-family:'Source Sans 3',sans-serif;}
  .blank-input.expr{width:170px; max-width:100%;}
  /*fix-layout*/ .cp-fill,.sp-fill{width:0;} .fld{min-width:0;} .fld input{width:100%; min-width:0; box-sizing:border-box;}
  .fig{margin:6px 0 10px; display:flex; justify-content:center;}
  .figsvg{width:100%; max-width:340px; height:auto; overflow:visible;}
  .figsvg .ln,.figsvg .arm{stroke:var(--ink); stroke-width:1.6; fill:none;}
  .figsvg .arm{stroke:var(--accent-text); stroke-width:2;}
  .figsvg .pt{fill:var(--ink);}
  .figsvg .lb{fill:var(--ink); font:600 13px 'Source Sans 3',sans-serif;}
  .figsvg .al{fill:var(--accent-text); font:700 12px 'Source Sans 3',sans-serif;}
  .figsvg .wg{fill:var(--gold-soft); stroke:var(--gold); stroke-width:1.2;}
  .figsvg .wg2{fill:rgba(199,154,62,.35); stroke:var(--gold); stroke-width:1.2;}
  .figsvg .ra{fill:none; stroke:var(--ink); stroke-width:1.2;}
  .figsvg .ahd{fill:var(--ink);}
  .figsvg .pr{fill:var(--paper-2); stroke:var(--ink-soft); stroke-width:1.2;}
  .figsvg .tk{stroke:var(--ink-soft); stroke-width:.8;}
  .figsvg .po{fill:var(--ink); font:600 8.5px 'IBM Plex Mono',monospace;}
  .figsvg .pi{fill:var(--danger); font:600 7.5px 'IBM Plex Mono',monospace;}
  .figsvg .sh{fill:var(--gold-soft); stroke:var(--ink); stroke-width:1.5; stroke-linejoin:round;}
  .figsvg .sh2{fill:rgba(199,154,62,.38); stroke:var(--ink); stroke-width:1.5; stroke-linejoin:round;}
  .figsvg .sh3{fill:rgba(199,154,62,.22); stroke:var(--ink); stroke-width:1.5; stroke-linejoin:round;}
  .figsvg .none{fill:none;}
  .figsvg .hid{stroke-dasharray:5 4; fill:none;}
  .figsvg .tick{stroke:var(--ink); stroke-width:1.4; fill:none;}
  .figsvg .shd{fill:var(--accent-text); fill-opacity:.55;}
  .figsvg .cell{fill:var(--card); stroke:var(--ink); stroke-width:1.1;}
  .figsvg .dr{fill:var(--danger);} .figsvg .dw{fill:var(--card); stroke:var(--ink); stroke-width:1.2;}
  .figsvg .dotfill{fill:var(--danger);}
  .tt{border-collapse:collapse; font-size:13.5px; margin:4px auto; font-variant-numeric:tabular-nums;} .tt th,.tt td{border:1px solid var(--rule); padding:4px 9px; text-align:left;} .tt th{background:var(--paper-2); font-weight:700;} .ttw{overflow-x:auto; max-width:100%;}
  .fq{display:inline-flex; flex-direction:column; vertical-align:middle; text-align:center; font-size:.82em; line-height:1.12; margin:0 2px;}
  .fq>span:first-child{border-bottom:1.5px solid currentColor; padding:0 2px;}
  .fq>span:last-child{padding:0 2px;}
  .mx{white-space:nowrap;}
  .blank-input.fr{width:110px;}
  @media (prefers-reduced-motion:reduce){ *{transition:none !important;} }
.datline{display:block;margin-top:8px;padding:8px 10px;border-radius:8px;background:var(--paper-2);font:500 14px/1.7 'IBM Plex Mono',monospace;word-spacing:2px;overflow-wrap:anywhere;}

  .theory{display:flex;flex-direction:column;gap:16px;padding-bottom:40px;}
  .hub{display:grid;grid-template-columns:1fr;gap:12px;}
  @media (min-width:640px){ .hub{grid-template-columns:repeat(3,1fr);} }
  .hub-card{background:var(--card);border:1px solid var(--rule);border-radius:14px;padding:16px;display:flex;flex-direction:column;gap:8px;}
  .hub-card h3{font-family:'Fraunces',serif;font-size:18px;margin:0;color:var(--accent-text);}
  .hub-card p{margin:0;font-size:14px;color:var(--ink-soft);line-height:1.5;}
  .hub-btns{display:flex;flex-wrap:wrap;gap:8px;margin-top:auto;}
  .hub-btn{min-height:40px;border:1.5px solid var(--rule);background:var(--paper-2);color:var(--ink);border-radius:10px;padding:8px 12px;font:600 14px 'Source Sans 3',sans-serif;cursor:pointer;text-align:left;}
  .hub-btn:hover{border-color:var(--gold);}
  .hub-btn.primary{background:var(--navy);color:#F4EFDF;border-color:var(--navy);}
  .note{background:var(--card);border:1px solid var(--rule);border-radius:14px;padding:18px;scroll-margin-top:120px;}
  .note h2{font-family:'Fraunces',serif;font-size:22px;margin:0 0 4px;color:var(--ink);}
  .note .lt{font-size:13.5px;color:var(--ink-soft);margin:0 0 12px;}
  .note .lt b{color:var(--accent-text);}
  .note h4{font:700 15px 'Source Sans 3',sans-serif;margin:16px 0 6px;color:var(--accent-text);}
  .note p,.note li{font-size:15.5px;line-height:1.6;}
  .note ul{padding-left:20px;margin:6px 0;}
  .keybox{background:var(--gold-soft);border-left:4px solid var(--gold);border-radius:8px;padding:10px 12px;margin:10px 0;font-size:15px;line-height:1.6;}
  .keybox b{color:var(--ink);}
  .ex{background:var(--paper-2);border-radius:10px;padding:12px;margin:10px 0;}
  .ex .exh{font-family:'Fraunces',serif;font-weight:700;color:var(--accent-text);margin-bottom:4px;}
  .ex .exl{font-size:15px;line-height:1.7;}
  .ttab{width:100%;border-collapse:collapse;font-size:14.5px;margin:8px 0;}
  .ttab th,.ttab td{border:1px solid var(--rule);padding:7px 8px;text-align:left;vertical-align:top;}
  .ttab th{background:var(--paper-2);}
  .tscroll{overflow-x:auto;}
  .mono{font-family:'IBM Plex Mono',monospace;font-size:.92em;}
  @media (max-width:480px){ .ttab{font-size:13.5px;} .ttab th,.ttab td{padding:6px;} }
  .note .figsvg{max-width:100%;height:auto;display:block;margin:8px auto;}


  .rep-top{display:flex;flex-wrap:wrap;gap:18px;align-items:center;justify-content:center;margin-top:8px;}
  .rep-legend{flex:1;min-width:220px;display:flex;flex-direction:column;gap:8px;}
  .rep-cap{font:700 13px 'Source Sans 3',sans-serif;color:var(--ink-soft);text-transform:uppercase;letter-spacing:.05em;}
  .rep-li{display:flex;align-items:center;gap:6px;font-size:15px;}
  .rep-n{margin-left:auto;white-space:nowrap;padding-left:8px;font-family:'IBM Plex Mono',monospace;font-weight:600;}
  .sw{display:inline-block;width:12px;height:12px;border-radius:3px;flex:none;}
  .rep-grid{display:grid;grid-template-columns:1fr;gap:12px;}
  @media (min-width:640px){ .rep-grid{grid-template-columns:1fr 1fr;} }
  .rep-card{background:var(--card);border:1px solid var(--rule);border-radius:14px;padding:14px;display:flex;flex-direction:column;gap:10px;}
  .rep-h{display:flex;align-items:center;gap:8px;font:700 16px 'Source Sans 3',sans-serif;}
  .crit{display:inline-grid;place-items:center;width:28px;height:28px;border-radius:50%;color:var(--card);font:700 15px Fraunces,serif;flex:none;}
  .rep-row{display:flex;gap:14px;align-items:center;}
  .rep-stats{display:flex;flex-direction:column;gap:5px;font-size:14.5px;}
  .rep-stats div{display:flex;align-items:center;gap:6px;}
  .rep-lvl{margin-top:4px;color:var(--accent-text);} .rep-lvl span{color:var(--ink-soft);font-size:13px;}
  .rep-note{font-size:13px;color:var(--ink-soft);}


  .skip-chips{display:flex;flex-wrap:wrap;gap:8px;justify-content:center;margin:12px 0;}
  .skip-chips .chip{min-width:48px;min-height:40px;cursor:pointer;border:1.5px solid var(--gold);background:var(--gold-soft);color:var(--retry-text);border-radius:10px;font:600 14px 'IBM Plex Mono',monospace;}
  .skip-btns{display:flex;flex-wrap:wrap;gap:10px;justify-content:center;margin-top:12px;}


  .kb-toggle{border:none;background:transparent;font-size:15px;cursor:pointer;padding:0 2px;vertical-align:middle;opacity:.7;}
  .vkb{position:fixed;left:0;right:0;bottom:0;z-index:80;background:var(--paper-2);border-top:1px solid var(--rule);box-shadow:0 -6px 20px rgba(0,0,0,.12);padding:6px 6px 8px;display:none;}
  .vkb.show{display:block;}
  .vkb-top{display:flex;justify-content:space-between;align-items:center;max-width:640px;margin:0 auto 4px;font:600 12px 'Source Sans 3',sans-serif;color:var(--ink-soft);}
  .vkb-link{border:none;background:none;color:var(--accent-text);font:600 12px 'Source Sans 3',sans-serif;cursor:pointer;text-decoration:underline;}
  .vkb-row{display:flex;gap:5px;max-width:640px;margin:0 auto 5px;}
  .vkb-k{flex:1;min-height:42px;border:1px solid var(--rule);border-radius:8px;background:var(--card);color:var(--ink);font:600 17px 'IBM Plex Mono',monospace;cursor:pointer;padding:0;}
  .vkb-k.fn{font:600 13px 'Source Sans 3',sans-serif;background:var(--gold-soft);}
  .vkb-k.done{background:var(--navy);color:#F4EFDF;border-color:var(--navy);}
  .vkb-k:active{transform:scale(.96);}
  body.kb-open .wrap{padding-bottom:360px;}
  body.kb-open .fab{display:none;}
  .tool-bar{display:flex;gap:8px;flex-wrap:wrap;margin:-4px 0 10px;}
  .tool-btn{min-height:36px;border:1.5px solid var(--gold);background:var(--gold-soft);color:var(--ink);border-radius:18px;padding:4px 12px;font:600 13.5px 'Source Sans 3',sans-serif;cursor:pointer;}
  .tool-panel{position:fixed;z-index:85;background:var(--card);border:1px solid var(--rule);border-radius:14px;box-shadow:0 10px 30px rgba(0,0,0,.25);display:none;}
  .tool-panel.show{display:block;}
  .tp-head{display:flex;align-items:center;gap:8px;padding:8px 10px;border-bottom:1px solid var(--rule);font:600 14px 'Source Sans 3',sans-serif;}
  .tp-note{font-size:12px;color:var(--ink-soft);font-weight:500;}
  .tp-x{margin-left:auto;border:1px solid var(--rule);background:var(--paper-2);color:var(--ink);border-radius:8px;min-height:32px;padding:2px 10px;cursor:pointer;font:600 13px 'Source Sans 3',sans-serif;}
  .tp-x + .tp-x{margin-left:0;}
  .calc{right:12px;bottom:84px;width:min(330px,calc(100vw - 24px));}
  body.calc-open .wrap{padding-bottom:440px;}
  body.calc-open .fab{display:none;}
  @media (max-width:640px){ .calc{left:6px;right:6px;width:auto;} .calc-keys button{min-height:36px;} }
  .calc-disp{padding:8px 12px;text-align:right;background:var(--paper-2);}
  .calc-expr{font:500 13px 'IBM Plex Mono',monospace;color:var(--ink-soft);min-height:18px;word-break:break-all;}
  .calc-res{font:600 24px 'IBM Plex Mono',monospace;color:var(--ink);word-break:break-all;}
  .calc-keys{display:grid;grid-template-columns:repeat(6,1fr);gap:5px;padding:8px;}
  .calc-keys button{min-height:40px;border:1px solid var(--rule);border-radius:8px;background:var(--card);color:var(--ink);font:600 14px 'IBM Plex Mono',monospace;cursor:pointer;padding:0;}
  .calc-keys button.fn{background:var(--gold-soft);font-family:'Source Sans 3',sans-serif;font-size:13px;}
  .calc-keys button.eq{grid-column:span 2;background:var(--navy);color:#F4EFDF;border-color:var(--navy);}
  .desmos{left:50%;top:50%;transform:translate(-50%,-50%);width:min(760px,calc(100vw - 16px));height:min(560px,calc(100vh - 90px));flex-direction:column;}
  .desmos.show{display:flex;}
  #desmosBox{flex:1;min-height:0;border-radius:0 0 14px 14px;overflow:hidden;}
  .desmos-msg{padding:24px;text-align:center;color:var(--ink-soft);}
  .chip[data-status="skipped"]{cursor:pointer;}
  .chip[data-status="answered"]{border-color:var(--accent-text);color:var(--accent-text);}


  button.crest-home{border:none;padding:0;position:relative;cursor:pointer;transition:transform .15s ease;}
  button.crest-home:hover,button.crest-home:focus-visible{transform:scale(1.06);outline:2px solid var(--gold);outline-offset:2px;}
  .crest-h{position:absolute;right:-7px;bottom:-7px;width:18px;height:18px;border-radius:50%;background:#F4EFDF;color:var(--navy);font:700 12px/18px 'Source Sans 3',sans-serif;text-align:center;box-shadow:0 1px 3px rgba(0,0,0,.3);}
  .brand .brand-row{position:relative;}
  .bmasw{position:absolute;left:50%;top:50%;transform:translate(-50%,-50%);display:flex;flex-shrink:0;white-space:nowrap;align-items:center;gap:6px;background:rgba(255,255,255,.12);border:1px solid rgba(255,255,255,.25);border-radius:99px;padding:5px 14px;color:#F4EFDF;}
  .bmasw-ic{font-size:16px;} .bmasw-t{font:600 20px 'IBM Plex Mono',monospace;letter-spacing:.02em;min-width:62px;text-align:center;}
  .bmasw-b{border:none;background:rgba(255,255,255,.18);color:#F4EFDF;border-radius:50%;width:30px;height:30px;cursor:pointer;font-size:13px;}
  .bmasw.off{display:none;}
  @media (max-width:560px){ .bmasw{position:static;transform:none;margin-left:auto;padding:4px 5px 4px 8px;gap:4px;} .bmasw-ic{display:none;} .bmasw-t{font-size:16px;min-width:48px;} .bmasw-b{width:26px;height:26px;} .brand .series-name{font-size:15px;} .brand .brand-name{font-size:10.5px;} .brand .brand-row>div:not(.bmasw){min-width:0;} }
  .bmasw-done{font:600 15px 'IBM Plex Mono',monospace;color:var(--accent-text);margin:4px 0 8px;}
  .sp-fab{position:fixed;left:14px;bottom:84px;z-index:60;border:1.5px solid var(--navy-2);background:var(--card);color:var(--ink);border-radius:99px;padding:9px 14px;font:700 14px 'Source Sans 3',sans-serif;box-shadow:0 4px 14px rgba(0,0,0,.15);cursor:pointer;}
  .sp-fab.on{background:var(--navy);color:#F4EFDF;}
  body.kb-open .sp-fab{display:none;}
  .sp-canvas{position:absolute;z-index:55;display:none;touch-action:none;cursor:crosshair;}
  .sp-canvas.passive{pointer-events:none;cursor:default;}
  .sp-bar{position:fixed;top:8px;left:8px;right:8px;margin:0 auto;width:max-content;z-index:90;display:none;align-items:center;gap:6px;background:var(--card);border:1px solid var(--rule);border-radius:14px;padding:6px 8px;box-shadow:0 6px 20px rgba(0,0,0,.2);max-width:calc(100vw - 16px);flex-wrap:wrap;justify-content:center;}
  .sp-lbl{font:700 13px 'Source Sans 3',sans-serif;color:var(--ink-soft);margin-right:2px;}
  .sp-pen,.sp-tool{width:38px;height:38px;border-radius:10px;border:1.5px solid var(--rule);background:var(--paper);cursor:pointer;display:inline-flex;align-items:center;justify-content:center;font-size:17px;padding:0;color:var(--ink);}
  .sp-pen i{width:20px;height:20px;border-radius:50%;display:block;}
  .sp-pen.on,.sp-tool.on{border-color:var(--navy-2);box-shadow:0 0 0 3px var(--gold-soft);}
  @media (max-width:560px){ .sp-lbl{display:none;} .sp-pen,.sp-tool{width:34px;height:34px;} .sp-fab span{display:none;} }

  /* larger reading sizes */
  .chapter-eyebrow{font-size:13.5px;}
  .chapter-title{font-size:36px;line-height:1.15;}
  .chapter-sub{font-size:16.5px;}
  .tab-btn{font-size:15.5px;}
  .sec-sub{font-size:15px;}
  .qtext{font-size:19px;line-height:1.55;}
  .qnum{width:36px;height:36px;font-size:16px;}
  .opt{font-size:17.5px;padding:12px 14px;}
  .step-line{font-size:17.5px;line-height:2;}
  .blank-input{font-size:16px;}
  .sol-line{font-size:16.5px;}
  .feedback{font-size:15px;}
  .note h2{font-size:28px;}
  .note h4{font-size:19px;}
  .note p,.note li{font-size:17.5px;line-height:1.65;}
  .note .lt{font-size:15.5px;}
  .ex .exh{font-size:18px;} .ex .exl{font-size:16.5px;}
  .keybox{font-size:16.5px;}
  .ttab{font-size:15.5px;}
  .hub-card h3{font-size:21px;} .hub-card p{font-size:15.5px;} .hub-btn{font-size:15px;}
  @media (max-width:480px){ .chapter-title{font-size:30px;} .qtext{font-size:18px;} .opt,.step-line{font-size:16.5px;} .note h2{font-size:24px;} .note p,.note li{font-size:16.5px;} }
</style>
</head>
<body>
<header class="brand">
  <div class="brand-row">
    <div class="crest">BM</div>
    <div>
      <div class="brand-name">Brain &amp; Mind Academy</div>
      <div class="series-name">Sopaan <span style="font-weight:400;font-size:14px;color:#CFD7EA;">Practice Series</span></div>
    </div>
  </div>
  <div class="chapter-eyebrow">Class 8 Mathematics · Chapter 1</div>
  <div class="chapter-title">Rational Numbers</div>
  <div class="chapter-sub">Theory Notes · Practice by Learning Objective · Learning Assessment</div><div class="chapter-credit">Mixed multiple-choice and fill-in-the-blank practice · Chapter 1</div>
  <div class="chapter-progress">
    <div class="cp-track"><div class="cp-fill" id="cpFill"></div></div>
    <div class="cp-label" id="cpLabel">0% complete</div>
  </div>
  <div class="who-row"><button class="mode-pill" id="modePill" hidden>Choose a mode</button><span class="who" id="whoBar" hidden></span></div>
</header>

<nav class="tabbar"><div class="tabbar-inner" id="tabbar"></div></nav>
<div class="sec-sub" id="secSub"></div><div class="slide-progress"><div class="sp-track"><div class="sp-fill" id="spFill"></div></div><div class="sp-label" id="spLabel">Question 1 of 49</div></div>
<div class="wrap" id="wrap"></div>
<footer class="brandfoot">Brain &amp; Mind Academy · Sopaan Practice Series · Class 8 Mathematics · Chapter 1<br>Chapter follows the Class 8 mathematics syllabus (New Enjoying Mathematics, Class 8). Theory notes, questions, learning assessments and worked solutions are written by Brain &amp; Mind Academy.</footer>

<div class="navbar"><div class="navbar-inner" id="navbarInner"></div></div>
<button class="fab" id="paletteFab"><span>Questions</span><span class="fab-badge" id="fabBadge">0/49</span></button>

<div class="overlay" id="overlay">
  <div class="palette" role="dialog" aria-label="Question palette">
    <div class="palette-head"><h2 id="paletteTitle">Question palette</h2><button class="palette-close" id="paletteClose">&times;</button></div>
    <div class="palette-legend">
      <span><i class="dot current"></i>Current</span><span><i class="dot correct"></i>Correct</span>
      <span><i class="dot revealed"></i>Revealed</span><span><i class="dot skipped"></i>Skipped</span>
      <span><i class="dot locked"></i>Locked</span>
    </div>
    <div class="chip-grid" id="paletteBody"></div>
  </div>
</div>
<div class="toast" id="toast"></div>

<script>
(function(){
"use strict";

/* ================= audio ================= */
var audioCtx=null;
function ensureAudio(){ if(!audioCtx){ try{ audioCtx=new (window.AudioContext||window.webkitAudioContext)(); }catch(e){} } return audioCtx; }
function playTone(freqs,dur,type){
  var ctx=ensureAudio(); if(!ctx) return;
  try{
    var t0=ctx.currentTime;
    freqs.forEach(function(f,i){
      var o=ctx.createOscillator(), g=ctx.createGain();
      o.type=type||'sine'; o.frequency.value=f;
      var start=t0+i*dur;
      g.gain.setValueAtTime(0.0001,start);
      g.gain.exponentialRampToValueAtTime(0.16,start+0.02);
      g.gain.exponentialRampToValueAtTime(0.0001,start+dur);
      o.connect(g); g.connect(ctx.destination);
      o.start(start); o.stop(start+dur+0.02);
    });
  }catch(e){}
}
function playSuccess(){ playTone([523.25,659.25,783.99],0.11,'sine'); }
function playWrong(){ playTone([220,185],0.14,'square'); }
function playReveal(){ playTone([300,220],0.16,'triangle'); }

/* ================= helpers ================= */
function norm(s){
  return String(s===undefined||s===null?'':s).trim().toLowerCase().replace(/\s+/g,'')
    .replace(/[×∗*·]/g,'x').replace(/÷/g,'/').replace(/–|—|−/g,'-')
    .replace(/[²]/g,'^2').replace(/[³]/g,'^3').replace(/[⁴]/g,'^4').replace(/[⁵]/g,'^5')
    .replace(/[⁶]/g,'^6').replace(/[⁷]/g,'^7').replace(/[⁸]/g,'^8').replace(/[⁹]/g,'^9')
    .replace(/\^/g,'');
}
function parseNum(s){
  if(s===undefined||s===null) return null;
  var t=String(s).trim().replace(/,/g,'').replace(/[−–—]/g,'-').replace(/\s+/g,''); if(t==='') return null;
  var neg=false; if(t[0]==='-'){neg=true;t=t.slice(1);}
  var m=t.match(/^(\d+)\/(\d+)$/);
  if(m){ var v=parseInt(m[1],10)/parseInt(m[2],10); return neg?-v:v; }
  if(/^\d+(\.\d+)?$/.test(t)){ var v2=parseFloat(t); return neg?-v2:v2; }
  return null;
}
/* ---- expression checker: compares answers like (P-2w)/2 and P/2-w at random values ---- */
function exprPrep(s){
  return String(s).toLowerCase().replace(/\s+/g,'').replace(/^[a-z]\(x\)=/i,'').replace(/^y=/i,'').replace(/[×∗·]/g,'*').replace(/÷/g,'/').replace(/[−–—]/g,'-')
    .replace(/²/g,'^2').replace(/³/g,'^3').replace(/⁴/g,'^4').replace(/⁵/g,'^5').replace(/⁶/g,'^6').replace(/⁷/g,'^7').replace(/⁸/g,'^8').replace(/⁹/g,'^9').replace(/π/g,'#').replace(/pi/gi,'#').replace(/½/g,'(1/2)');
}
function exprCompile(src){
  var s=exprPrep(src), i=0, toks=[], absDepth=0;
  while(i<s.length){
    var ch=s[i];
    if(/[0-9.]/.test(ch)){ var j=i; while(j<s.length && /[0-9.]/.test(s[j])) j++; toks.push({k:'n',v:parseFloat(s.slice(i,j))}); i=j; continue; }
    if(/[a-zA-Z#]/.test(ch)){ toks.push({k:'v',v:ch}); i++; continue; }
    if(ch==='|'){ var pv=toks[toks.length-1]; var opn=(absDepth===0)||!pv||('+-*/^(['.indexOf(pv.k)>=0); if(opn){ absDepth++; toks.push({k:'['}); } else { absDepth--; toks.push({k:']'}); } i++; continue; }
    if('+-*/^()'.indexOf(ch)>=0){ toks.push({k:ch}); i++; continue; }
    return null;
  }
  var out=[];
  for(var t=0;t<toks.length;t++){
    var a=toks[t], b=out[out.length-1];
    if(b && (b.k==='n'||b.k==='v'||b.k===')'||b.k===']') && (a.k==='n'||a.k==='v'||a.k==='('||a.k==='[')) out.push({k:'&'});
    out.push(a);
  }
  var p=0;
  function peek(){ return out[p]; }
  function parseE(){ var n=parseT(); while(peek() && (peek().k==='+'||peek().k==='-')){ var o=out[p++].k, r=parseT(); n=(function(l,r,o){return function(e){ return o==='+'?l(e)+r(e):l(e)-r(e); };})(n,r,o); } return n; }
  function parseI(){ var n=parseU(); while(peek() && peek().k==='&'){ p++; var r=parseP(); n=(function(l,r){return function(e){ return l(e)*r(e); };})(n,r); } return n; }
  function parseT(){ var n=parseI(); while(peek() && (peek().k==='*'||peek().k==='/')){ var o=out[p++].k, r=parseI(); n=(function(l,r,o){return function(e){ return o==='*'?l(e)*r(e):l(e)/r(e); };})(n,r,o); } return n; }
  function parseU(){ if(peek() && peek().k==='-'){ p++; var u=parseU(); return function(e){ return -u(e); }; } if(peek() && peek().k==='+'){ p++; return parseU(); } return parseP(); }
  function parseP(){ var b=parseA(); if(peek() && peek().k==='^'){ p++; var x=parseU(); return function(e){ return Math.pow(b(e),x(e)); }; } return b; }
  function parseA(){
    var t=out[p++]; if(!t) throw 0;
    if(t.k==='n') return function(){ return t.v; };
    if(t.k==='v') return t.v==='#' ? function(){ return Math.PI; } : function(e){ return e[t.v]; };
    if(t.k==='('){ var n=parseE(); if(!peek()||peek().k!==')') throw 0; p++; return n; }
    if(t.k==='['){ var m=parseE(); if(!peek()||peek().k!==']') throw 0; p++; return function(e){ return Math.abs(m(e)); }; }
    throw 0;
  }
  try{ var f=parseE(); if(p!==out.length) return null; return f; }catch(e){ return null; }
}
function exprEqual(input,answer){
  var f=exprCompile(input), g=exprCompile(answer); if(!f||!g) return false;
  var hits=0;
  for(var trial=0;trial<8;trial++){
    var env={}; 'abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ'.split('').forEach(function(c){ env[c]=1.3+Math.random()*4.1; });
    var x=f(env), y=g(env);
    if(!isFinite(x)||!isFinite(y)) continue;
    if(Math.abs(x-y)>1e-7*Math.max(1,Math.abs(x),Math.abs(y))) return false;
    hits++;
  }
  return hits>=3;
}
function wordsNorm(s){ return String(s||'').toLowerCase().replace(/\band\b/g,' ').replace(/[^a-z]/g,''); }
function listNorm(s){ return (String(s||'').replace(/[−–—]/g,'-').replace(/(\d) (?=\d{3}\b)/g,'$1').match(/-?\d+(\.\d+)?/g)||[]).join(','); }
function powNorm(s){ return String(s||'').toLowerCase().replace(/\s+/g,'').replace(/[×∗*·.]/g,'x').replace(/[⁰¹²³⁴⁵⁶⁷⁸⁹]+/g,function(m){ return '^'+m.split('').map(function(c){ return '⁰¹²³⁴⁵⁶⁷⁸⁹'.indexOf(c); }).join(''); }).replace(/\^1(?!\d)/g,''); }
function fr(s){ return String(s).replace(/\{(\d+) (\d+)\/(\d+)\}/g,'<span class="mx">$1<span class="fq"><span>$2</span><span>$3</span></span></span>').replace(/\{(\d+)\/(\d+)\}/g,'<span class="fq"><span>$1</span><span>$2</span></span>'); }
function gcdI(a,b){ a=Math.abs(a); b=Math.abs(b); while(b){ var t=a%b; a=b; b=t; } return a; }
function fracParse(s){ s=String(s===undefined||s===null?'':s).trim().replace(/[\u2044\u2215\u00f7]/g,'/').replace(/\s+/g,' ').replace(/\s*\/\s*/g,'/'); var m;
  if((m=s.match(/^(-?\d+)$/))) return {v:+m[1],form:'int',n:+m[1],d:1};
  if((m=s.match(/^(-?\d+)\/(\d+)$/))){ if(+m[2]===0) return null; return {v:m[1]/m[2],form:'frac',n:+m[1],d:+m[2]}; }
  if((m=s.match(/^(-?)(\d+)(?: |\+)(\d+)\/(\d+)$/))){ if(+m[4]===0) return null; var sg=m[1]?-1:1; return {v:sg*(+m[2]+m[3]/m[4]),form:'mixed',w:sg*m[2],n:+m[3],d:+m[4]}; }
  if((m=s.match(/^-?\d*\.\d+$/))) return {v:parseFloat(s),form:'dec'};
  return null; }
function fracOK(mode,input,answer){
  if(mode==='flist'){ var A=String(input).split(/[,;]/).map(function(x){return x.trim();}).filter(Boolean), K=String(answer).split(/[,;]/).map(function(x){return x.trim();});
    if(A.length!==K.length) return false; return A.every(function(x,i){ var a=fracParse(x), k=fracParse(K[i]); return a&&k&&Math.abs(a.v-k.v)<1e-9; }); }
  var a=fracParse(input), k=fracParse(answer); if(!a||!k) return false;
  var same=Math.abs(a.v-k.v)<1e-9; if(!same) return false;
  if(mode==='fv') return true;
  if(mode==='dec') return a.form==='dec'||a.form==='int';
  if(mode==='fe') return (a.form==='frac'&&k.form==='frac'&&a.n===k.n&&a.d===k.d)||(a.form==='int'&&k.form==='int');
  if(mode==='fi') return a.form==='frac'||(a.form==='int'&&k.form==='int');
  if(mode==='fl') return a.form==='int'||(a.form==='frac'&&gcdI(a.n,a.d)===1)||(a.form==='mixed'&&a.n<a.d&&gcdI(a.n,a.d)===1);
  if(mode==='fm') return a.form==='int'||(a.form==='mixed'&&a.n>0&&a.n<a.d&&gcdI(a.n,a.d)===1);
  return false; }
function answerMatches(input,answer,accept,expr){
  if(expr==='dec'||expr==='fv'||expr==='fe'||expr==='fl'||expr==='fm'||expr==='fi'||expr==='flist'){ if(input===undefined||input===null||String(input).trim()==='') return false; return fracOK(expr,input,answer); }
  if(input===undefined||input===null||String(input).trim()==='') return false;
  if(expr==='words'){ return [answer].concat(accept||[]).some(function(a){ if(/\d/.test(a)) return norm(a)===norm(input); var w=wordsNorm(a); return w!=='' && w===wordsNorm(input); }); }
  if(expr==='list'){ return [answer].concat(accept||[]).some(function(a){ return listNorm(a)===listNorm(input); }); }
  if(expr==='pow'){ return [answer].concat(accept||[]).some(function(a){ return powNorm(a)===powNorm(input); }); }
  if(expr==='time'){ var tn=function(x){ var t=String(x).toLowerCase().replace(/[\s.]/g,'').replace(/[:h]/g,''); if(/^\d{3}(am|pm)?$/.test(t)) t='0'+t; return t; }; return [answer].concat(accept||[]).some(function(a){ return tn(a)===tn(input); }); }
  if(expr==='glist'){ var gn=function(x){ return String(x).toUpperCase().split(/[\s,;]+/).filter(Boolean).sort().join(','); }; return [answer].concat(accept||[]).some(function(a){ return gn(a)===gn(input); }); }
  if(expr==='coord'){ var cn=function(x){ return String(x).replace(/[\u2212\u2013\u2014]/g,'-').replace(/[\s()\[\]]/g,''); }; return [answer].concat(accept||[]).some(function(a){ return cn(a)===cn(input); }); }
  if(expr==='dlist'){ var dn=function(x){ return (String(x).replace(/[−–—]/g,'-').match(/-?\d*\.?\d+/g)||[]).map(Number).join(','); }; return [answer].concat(accept||[]).some(function(a){ return dn(a)===dn(input); }); }
  if(expr==='set'){ var sn=function(x){ return (String(x).match(/-?\d+/g)||[]).map(Number).sort(function(a,b){return a-b;}).join(','); }; return [answer].concat(accept||[]).some(function(a){ return sn(a)===sn(input); }); }
  if(expr==='primes'){ var pn=function(x){ var t=powNorm(x).replace(/[^0-9x^]/g,''); var out=[]; t.split('x').forEach(function(tok){ if(!tok) return; var m=tok.split('^'); var b=+m[0], e=m[1]?+m[1]:1; for(var i=0;i<e;i++) out.push(b); }); return out.sort(function(a,b){return a-b;}).join(','); }; return [answer].concat(accept||[]).some(function(a){ return pn(a)===pn(input); }); }
  if(expr==='angle'){ var an=function(x){ return String(x).toUpperCase().replace(/[^A-Z]/g,''); }; var k=an(answer), v=an(input); return v===k || v===k.split('').reverse().join(''); }
  if(expr==='trans'){ var tv=function(x){ var s=String(x).toLowerCase().replace(/[−–—]/g,'-').replace(/\b(units?|squares?|and|then|steps?|to|the|a)\b/g,' ').replace(/[,;.]/g,' '); var re=/(\d+)\s*(right|left|up|down|r|l|u|d)\b/g, m, dx=0, dy=0, n=0; while((m=re.exec(s))){ var v=+m[1], d=m[2][0]; if(d==='r')dx+=v; else if(d==='l')dx-=v; else if(d==='u')dy+=v; else dy-=v; n++; } if(!n||s.replace(re,'').replace(/\s+/g,'')!=='') return null; return dx+','+dy; }; var ti=tv(input); return ti!==null && [answer].concat(accept||[]).some(function(a){ return tv(a)===ti; }); }
  if(expr==='rot'){ var rv=function(x){ var s=String(x).toLowerCase().replace(/quarter[\s-]*turn/g,'90').replace(/half[\s-]*turn/g,'180').replace(/three[\s-]*quarter[\s-]*turn/g,'270'); var m=s.match(/\b(90|180|270)\b/); if(!m) return null; var a=+m[1]; if(a===180) return '180'; var dir=/anti|counter|acw|ccw/.test(s)?-1:(/clockwise|\bcw\b/.test(s)?1:0); if(!dir) return null; return String(((a*dir)%360+360)%360); }; var ri=rv(input); return ri!==null && ri===rv(answer); }
  if(expr==='expanded'){ var f=function(x){ return String(x).replace(/\s+/g,'').replace(/,/g,''); }; return [answer].concat(accept||[]).some(function(a){ return f(a)===f(input); }); }
  if(expr===true && input!==undefined && input!==null && String(input).trim()!==''){
    if(exprEqual(input,answer)) return true;
    var alt=String(input).replace(/\/\s*(\d+(?:\.\d+)?)\s*([a-zA-Z(])/g,'/$1*$2'); if(alt!==String(input) && exprEqual(alt,answer)) return true;
    return (accept||[]).some(function(a){ return exprEqual(input,a); });
  }
  if(input===undefined||input===null||String(input).trim()==='') return false;
  var n1=parseNum(input), n2=parseNum(answer);
  if(n1!==null && n2!==null){ if(Math.abs(n1-n2)<1e-3) return true; return (accept||[]).some(function(a){ var n3=parseNum(a); return n3!==null && Math.abs(n1-n3)<1e-3; }); }
  var cands=[answer].concat(accept||[]); var ni=norm(input);
  for(var i=0;i<cands.length;i++){ if(norm(cands[i])===ni) return true; }
  return false;
}
function esc(s){ return String(s).replace(/&/g,'&amp;').replace(/</g,'&lt;'); }

/* ================= DATA ================= */
var AR_OPTIONS = ["Both A and R are true, and R is the correct explanation of A","Both A and R are true, but R is NOT the correct explanation of A","A is true but R is false","A is false but R is true"];
var THEORY = "<div class=\"hub\"><div class=\"hub-card\"><h3>📖 Theory notes</h3><p>Explained notes for every part of the chapter, following the book, with rules, number lines and solved examples.</p><div class=\"hub-btns\"><button class=\"hub-btn\" data-jump=\"n11\">1.1 notes</button><button class=\"hub-btn\" data-jump=\"n12\">1.2 notes</button><button class=\"hub-btn\" data-jump=\"n13\">1.3 notes</button><button class=\"hub-btn\" data-jump=\"n14\">1.4 notes</button><button class=\"hub-btn\" data-jump=\"n15\">1.5 notes</button><button class=\"hub-btn\" data-jump=\"n16\">1.6 notes</button><button class=\"hub-btn\" data-jump=\"n17\">1.7 notes</button></div></div><div class=\"hub-card\"><h3>🎯 Practice by learning objective</h3><p>Every Example, Try This and Exercise question of the chapter, one sheet per objective, mixing multiple-choice and fill-in-the-blank questions. The bold tag shows where each question is in the book.</p><div class=\"hub-btns\"><button class=\"hub-btn\" data-go=\"s1\">1.1 · Rational numbers and standard form</button><button class=\"hub-btn\" data-go=\"s2\">1.2 · Number line, comparison and absolute value</button><button class=\"hub-btn\" data-go=\"s3\">1.3 · Addition and its properties</button><button class=\"hub-btn\" data-go=\"s4\">1.4 · Subtraction and its properties</button><button class=\"hub-btn\" data-go=\"s5\">1.5 · Multiplication and its properties</button><button class=\"hub-btn\" data-go=\"s6\">1.6 · Division and real-life problems</button><button class=\"hub-btn\" data-go=\"s7\">1.7 · Density of rational numbers</button></div></div><div class=\"hub-card\"><h3>📝 Learning assessment</h3><p>Four short assessments built from the Chapter Check-up, one per skill area. Take them in Quiz mode and open the report to see your results as pie charts.</p><div class=\"hub-btns\"><button class=\"hub-btn\" data-go=\"s8\">A · Knowing and understanding</button><button class=\"hub-btn\" data-go=\"s9\">B · Investigating patterns</button><button class=\"hub-btn\" data-go=\"s10\">C · Communicating</button><button class=\"hub-btn\" data-go=\"s11\">D · Applying mathematics in real-life contexts</button><button class=\"hub-btn primary\" data-go=\"report\">📊 View my report</button></div></div></div><section class=\"note\" id=\"nintro\"><h2>About this chapter</h2><p>A <b>rational number</b> is any number that can be written as {p/q}, where p and q are integers and q ≠ 0. Natural numbers, whole numbers, integers and fractions are all rational numbers.</p><p>The practice sheets contain <b>all</b> the questions of the chapter in book order. Each question starts with a tag such as <b>Example 7</b>, <b>Try This</b>, <b>Ex 1A · Q3(b)</b> or <b>Check-up · MCQ 2</b>.</p><div class=\"tscroll\"><table class=\"ttab\"><tr><th>Assessment</th><th>Skill area</th><th>What it checks</th></tr><tr><td>A</td><td>Knowing and understanding</td><td>Using the rules of the chapter correctly.</td></tr><tr><td>B</td><td>Investigating patterns</td><td>Spotting patterns and using properties to simplify.</td></tr><tr><td>C</td><td>Communicating</td><td>Naming properties, correct notation, spotting errors.</td></tr><tr><td>D</td><td>Applying mathematics in real-life contexts</td><td>Money, measurement and sharing problems.</td></tr></table></div><p><b>Tools:</b> ⏱ at the top times each tab (pause or reset it). ✏️ opens a scratchpad with four pens for rough work. Tap the BM badge to go back to the home page.</p><p><b>Typing answers:</b> type fractions as <span class=\"mono\">-3/4</span> (use the − key for negative, and keep the denominator positive). Give answers in lowest terms when asked; improper fractions such as <span class=\"mono\">13/6</span> are fine.</p></section><section class=\"note\" id=\"n11\"><h2>1.1 Rational numbers and standard form</h2><p class=\"lt\"><b>Objective:</b> Recognise rational numbers, find equivalent rational numbers and write rational numbers in standard form.</p><p>A number that can be written as {a/b}, where a and b are integers and b ≠ 0, is a <b>rational number</b>. The denominator cannot be 0 because division by zero is not defined. Examples: {4/5}, {−10/9}, 2 (= {2/1}), 0 (= {0/15}).</p><div class=\"ex\"><div class=\"exh\">Book Example 1 · Which are rational?</div><div class=\"exl\">{3/4}, {−7/8} and {0/6} are rational (integers on top and bottom, denominator not zero).<br>10 = {10/1} and −7 = {−7/1} are rational.<br>{8/0} is <b>not</b> rational: the denominator is zero.</div></div><h4>Equivalent rational numbers</h4><p>Rational numbers of equal value are <b>equivalent</b>: {1/2} = {2/4} = {4/8}. Multiply or divide the numerator and the denominator by the same non-zero number.</p><div class=\"ex\"><div class=\"exh\">Book Example 2 · Missing terms</div><div class=\"exl\">{3/5} = {12/x}: 12 ÷ 3 = 4, so x = 5 × 4 = <b>20</b>.<br>{40/90} = {x/9}: 90 ÷ 9 = 10, so x = 40 ÷ 10 = <b>4</b>.</div></div><h4>Standard form</h4><p>A rational number is in <b>standard form</b> when (1) the numerator and denominator are co-prime (no common factor other than 1) and (2) the denominator is positive.</p><ul><li>If the denominator is negative, multiply numerator and denominator by −1: {4/−9} = {−4/9}.</li><li><b>Method 1:</b> keep dividing by common factors: {48/72} = {24/36} = {12/18} = {6/9} = {2/3}.</li><li><b>Method 2:</b> divide once by the HCF: HCF(12, 16) = 4, so {12/16} = {3/4}.</li></ul><div class=\"ex\"><div class=\"exh\">Book Example 3 · Standard form</div><div class=\"exl\">{7/8} is already in standard form.<br>{6/−35} → multiply by −1 → <b>{−6/35}</b>.<br>{8/12} → divide by 4 → <b>{2/3}</b>.  {39/91} → divide by 13 → <b>{3/7}</b>.</div></div><div class=\"keybox\"><b>A negative sign may sit in three places:</b> {−3/4}, −{3/4} and {3/−4} are the same number. Standard form keeps the sign on the numerator.</div><div class=\"hub-btns\" style=\"margin-top:12px\"><button class=\"hub-btn primary\" data-go=\"s1\">Practise 1.1 →</button></div></section><section class=\"note\" id=\"n12\"><h2>1.2 Number line, comparison and absolute value</h2><p class=\"lt\"><b>Objective:</b> Represent rational numbers on the number line, compare and order them, and find absolute values.</p><p>To show a rational number on a number line, divide each unit length into as many equal parts as the denominator, then count the numerator from 0 (right for positive, left for negative).</p><svg class=\"figsvg\" viewBox=\"0 0 330 92\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><text class=\"lb\" x=\"165.0\" y=\"10.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">Book Example 4 · each unit divided into 3 parts</text><line class=\"ln\" x1=\"14.0\" y1=\"46.0\" x2=\"316.0\" y2=\"46.0\" marker-end=\"url(#ah)\" marker-start=\"url(#ahs)\"/><line x1=\"22.0\" y1=\"37\" x2=\"22.0\" y2=\"55\" style=\"stroke:var(--ink);stroke-width:1.6\"/><text class=\"lb\" x=\"22.0\" y=\"66.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−1</text><line x1=\"53.8\" y1=\"41\" x2=\"53.8\" y2=\"51\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"85.6\" y1=\"41\" x2=\"85.6\" y2=\"51\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"117.3\" y1=\"37\" x2=\"117.3\" y2=\"55\" style=\"stroke:var(--ink);stroke-width:1.6\"/><text class=\"lb\" x=\"117.3\" y=\"66.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">0</text><line x1=\"149.1\" y1=\"41\" x2=\"149.1\" y2=\"51\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"180.9\" y1=\"41\" x2=\"180.9\" y2=\"51\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"212.7\" y1=\"37\" x2=\"212.7\" y2=\"55\" style=\"stroke:var(--ink);stroke-width:1.6\"/><text class=\"lb\" x=\"212.7\" y=\"66.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">1</text><line x1=\"244.4\" y1=\"41\" x2=\"244.4\" y2=\"51\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"276.2\" y1=\"41\" x2=\"276.2\" y2=\"51\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"308.0\" y1=\"37\" x2=\"308.0\" y2=\"55\" style=\"stroke:var(--ink);stroke-width:1.6\"/><text class=\"lb\" x=\"308.0\" y=\"66.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2</text><circle cx=\"85.6\" cy=\"46\" r=\"5\" style=\"fill:var(--danger)\"/><text class=\"al\" x=\"85.6\" y=\"29.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−1/3</text><circle cx=\"180.9\" cy=\"46\" r=\"5\" style=\"fill:var(--danger)\"/><text class=\"al\" x=\"180.9\" y=\"29.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2/3</text><circle cx=\"276.2\" cy=\"46\" r=\"5\" style=\"fill:var(--danger)\"/><text class=\"al\" x=\"276.2\" y=\"29.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">5/3</text></svg><h4>Comparing</h4><ul><li>On a number line, the number on the <b>left is smaller</b>.</li><li><b>Same denominators:</b> compare the numerators.</li><li><b>Different denominators:</b> make the denominators positive, rewrite with the LCM and compare numerators.</li><li><b>Same positive numerators:</b> the smaller denominator gives the greater number: {4/7} > {4/11}.</li></ul><div class=\"ex\"><div class=\"exh\">Book Example 6 · Compare {−1/8} and {5/−4}</div><div class=\"exl\">Positive denominators: {−1/8} and {−5/4}.<br>LCM of 8 and 4 = 8: {−5/4} = {−10/8}.<br>−1 > −10, so <b>{−1/8} > {5/−4}</b>.</div></div><div class=\"ex\"><div class=\"exh\">Book Example 8 · Ascending order of {3/8}, {4/12}, {−7/16}, {−2/3}</div><div class=\"exl\">LCM of 8, 12, 16, 3 = 48: {18/48}, {16/48}, {−21/48}, {−32/48}.<br>Numerators in order: −32 < −21 < 16 < 18.<br>So <b>{−2/3} < {−7/16} < {4/12} < {3/8}</b>.</div></div><h4>Absolute value</h4><p>The <b>absolute value</b> |x| is the distance of x from 0 on the number line, whatever the direction: |{−3/4}| = {3/4} and |{3/4}| = {3/4}.</p><div class=\"ex\"><div class=\"exh\">Book Example 9</div><div class=\"exl\">|{−2/3}| = <b>{2/3}</b>.</div></div><div class=\"keybox\"><b>Common mistake:</b> {5/8} is greater than {5/20} (bigger parts), and −{6/7} is less than {2/7} (every negative number is less than every positive one).</div><div class=\"hub-btns\" style=\"margin-top:12px\"><button class=\"hub-btn primary\" data-go=\"s2\">Practise 1.2 →</button></div></section><section class=\"note\" id=\"n13\"><h2>1.3 Addition and its properties</h2><p class=\"lt\"><b>Objective:</b> Add rational numbers and use closure, commutativity, associativity, the additive identity and additive inverses.</p><p>To add rational numbers, make the denominators the same (use the LCM) and add the numerators. There are four cases: the denominators are the same, one is a multiple of the other, they are co-prime, or they have common factors.</p><div class=\"ex\"><div class=\"exh\">Book Example 12 · One denominator a multiple of the other</div><div class=\"exl\">{4/3} + {5/6}: LCM = 6, {4/3} = {8/6}.<br>{8/6} + {5/6} = <b>{13/6}</b> = {2 1/6}.</div></div><div class=\"ex\"><div class=\"exh\">Book Example 14 · Co-prime denominators</div><div class=\"exl\">{4/5} + ({−6/7}): LCM = 5 × 7 = 35.<br>{28/35} + {−30/35} = <b>{−2/35}</b>.</div></div><h4>Properties of addition</h4><div class=\"tscroll\"><table class=\"ttab\"><tr><th>Property</th><th>Statement</th></tr><tr><td>Closure</td><td>{a/b} + {c/d} is always rational</td></tr><tr><td>Commutative</td><td>{a/b} + {c/d} = {c/d} + {a/b}</td></tr><tr><td>Associative</td><td>({a/b} + {c/d}) + {e/f} = {a/b} + ({c/d} + {e/f})</td></tr><tr><td>Additive identity</td><td>{a/b} + 0 = {a/b}</td></tr><tr><td>Additive inverse</td><td>{a/b} + ({−a/b}) = 0</td></tr></table></div><div class=\"keybox\"><b>Add fast:</b> group numbers that make whole numbers first: 76 + 598 + 224 = (76 + 224) + 598 = 898.</div><div class=\"hub-btns\" style=\"margin-top:12px\"><button class=\"hub-btn primary\" data-go=\"s3\">Practise 1.3 →</button></div></section><section class=\"note\" id=\"n14\"><h2>1.4 Subtraction and its properties</h2><p class=\"lt\"><b>Objective:</b> Subtract rational numbers by adding the additive inverse and test the properties of subtraction.</p><p><b>Subtraction is addition of the additive inverse:</b> {a/b} − {c/d} = {a/b} + ({−c/d}). So 5 − (−7) = 5 + 7 = 12, and {4/9} − ({−2/8}) = {4/9} + {2/8}.</p><div class=\"ex\"><div class=\"exh\">Book Example 17 · Subtract {−3/7} from {4/11}</div><div class=\"exl\">{4/11} − ({−3/7}) = {4/11} + {3/7}.<br>LCM 77: {28/77} + {33/77} = <b>{61/77}</b>.</div></div><h4>Properties of subtraction</h4><ul><li><b>Closure:</b> the difference of two rational numbers is rational.</li><li><b>Not commutative:</b> {3/4} − {1/4} = {1/2} but {1/4} − {3/4} = −{1/2}.</li><li><b>Not associative:</b> ({3/8} − {2/4}) − {1/16} = −{3/16} but {3/8} − ({2/4} − {1/16}) = −{1/16}.</li></ul><div class=\"keybox\"><b>Watch the signs:</b> “− (−b)” becomes “+ b” before you do anything else.</div><div class=\"hub-btns\" style=\"margin-top:12px\"><button class=\"hub-btn primary\" data-go=\"s4\">Practise 1.4 →</button></div></section><section class=\"note\" id=\"n15\"><h2>1.5 Multiplication and its properties</h2><p class=\"lt\"><b>Objective:</b> Multiply rational numbers, find reciprocals and use the properties of multiplication, including distributivity.</p><p>Multiply the numerators to get the new numerator and the denominators to get the new denominator: {−2/11} × {3/5} = {−6/55}. Cancel common factors first to keep the numbers small.</p><div class=\"ex\"><div class=\"exh\">Book Example 25 · Cancel first</div><div class=\"exl\">{45/84} × {21/27}: cancel 45 and 27 by 9 → {5/84} × {21/3}.<br>Cancel 21 and 84 by 21 → {5/4} × {1/3} = <b>{5/12}</b>.</div></div><h4>Properties of multiplication</h4><ul><li><b>Closure, commutative, associative</b> all hold.</li><li><b>Multiplicative identity</b> 1: {a/b} × 1 = {a/b}.</li><li><b>Multiplicative inverse (reciprocal):</b> {a/b} × {b/a} = 1 for every non-zero {a/b}. The reciprocal of {−5/8} is {−8/5}. <b>0 has no reciprocal.</b></li><li><b>Distributive property:</b> {a/b} × ({c/d} + {e/f}) = {a/b} × {c/d} + {a/b} × {e/f}.</li><li><b>Multiplication by 0:</b> {a/b} × 0 = 0.</li></ul><div class=\"ex\"><div class=\"exh\">Book Example 32 · Distributive property</div><div class=\"exl\">LHS = {−3/5} × ({3/4} + {−8/9}) = {−3/5} × {−5/36} = {15/180}.<br>RHS = {−9/20} + {24/45} = {−81/180} + {96/180} = {15/180}.<br>Both equal <b>{1/12}</b>.</div></div><div class=\"keybox\"><b>Sign rules</b> are the same as for integers: same signs → positive product, different signs → negative product.</div><div class=\"hub-btns\" style=\"margin-top:12px\"><button class=\"hub-btn primary\" data-go=\"s5\">Practise 1.5 →</button></div></section><section class=\"note\" id=\"n16\"><h2>1.6 Division and real-life problems</h2><p class=\"lt\"><b>Objective:</b> Divide rational numbers using reciprocals, test the properties of division and solve real-life problems.</p><p>Division is multiplication by the <b>multiplicative inverse</b> of the divisor: {a/b} ÷ {c/d} = {a/b} × {d/c} ({c/d} ≠ 0). For example 6 ÷ {1/2} = 6 × 2 = 12 (there are 12 halves in 6).</p><div class=\"ex\"><div class=\"exh\">Book Example 37 · Divide {3/8} by {−4/9}</div><div class=\"exl\">Reciprocal of {−4/9} is {−9/4}.<br>{3/8} × {−9/4} = <b>{−27/32}</b>.</div></div><h4>Properties of division</h4><div class=\"tscroll\"><table class=\"ttab\"><tr><th>Property</th><th>+</th><th>−</th><th>×</th><th>÷</th></tr><tr><td>Closure</td><td>yes</td><td>yes</td><td>yes</td><td>no (÷ 0)</td></tr><tr><td>Commutative</td><td>yes</td><td>no</td><td>yes</td><td>no</td></tr><tr><td>Associative</td><td>yes</td><td>no</td><td>yes</td><td>no</td></tr></table></div><h4>Real-life problems</h4><p>Change mixed numbers to improper fractions, decide which operation the story needs, then simplify.</p><div class=\"ex\"><div class=\"exh\">Book Example 41 · Tiles</div><div class=\"exl\">Hall = {21 3/4} m × {11 1/4} m = {87/4} × {45/4} = {3915/16} m².<br>One tile = {3/4} × {3/4} = {9/16} m².<br>Tiles = {3915/16} ÷ {9/16} = {3915/16} × {16/9} = <b>435</b>.</div></div><div class=\"keybox\"><b>Profit of {−2/15}</b> means a loss of {2/15} of the investment.</div><div class=\"hub-btns\" style=\"margin-top:12px\"><button class=\"hub-btn primary\" data-go=\"s6\">Practise 1.6 →</button></div></section><section class=\"note\" id=\"n17\"><h2>1.7 Density of rational numbers</h2><p class=\"lt\"><b>Objective:</b> Find one or more rational numbers between two given rational numbers.</p><p>Between two integers there are only a limited number of integers, but between any two rational numbers there are <b>countless</b> rational numbers. Magnify the number line: between 0 and 1 are {1/10}, …, {9/10}; between {5/10} and {6/10} are {51/100}, …, {59/100}; and so on.</p><svg class=\"figsvg\" viewBox=\"0 0 330 92\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><text class=\"lb\" x=\"165.0\" y=\"10.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">Between 0 and 1: nine tenths … and each gap holds nine hundredths</text><line class=\"ln\" x1=\"14.0\" y1=\"46.0\" x2=\"316.0\" y2=\"46.0\" marker-end=\"url(#ah)\" marker-start=\"url(#ahs)\"/><line x1=\"22.0\" y1=\"37\" x2=\"22.0\" y2=\"55\" style=\"stroke:var(--ink);stroke-width:1.6\"/><text class=\"lb\" x=\"22.0\" y=\"66.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">0</text><line x1=\"50.6\" y1=\"41\" x2=\"50.6\" y2=\"51\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"79.2\" y1=\"41\" x2=\"79.2\" y2=\"51\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"107.8\" y1=\"41\" x2=\"107.8\" y2=\"51\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"136.4\" y1=\"41\" x2=\"136.4\" y2=\"51\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"165.0\" y1=\"41\" x2=\"165.0\" y2=\"51\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"193.6\" y1=\"41\" x2=\"193.6\" y2=\"51\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"222.2\" y1=\"41\" x2=\"222.2\" y2=\"51\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"250.8\" y1=\"41\" x2=\"250.8\" y2=\"51\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"279.4\" y1=\"41\" x2=\"279.4\" y2=\"51\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"308.0\" y1=\"37\" x2=\"308.0\" y2=\"55\" style=\"stroke:var(--ink);stroke-width:1.6\"/><text class=\"lb\" x=\"308.0\" y=\"66.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">1</text></svg><h4>Method 1 · The mean</h4><p>Add the two numbers and divide by 2.</p><div class=\"ex\"><div class=\"exh\">Book Example 43</div><div class=\"exl\">A rational number between {1/3} and {1/2}: {1/3} + {1/2} = {5/6}; {5/6} ÷ 2 = <b>{5/12}</b>.</div></div><h4>Method 2 · Same denominators</h4><p>Write both with the same denominator. If there are not enough whole numbers between the numerators, multiply numerator and denominator by 10, 100, …</p><div class=\"ex\"><div class=\"exh\">Book Example 45 · Five numbers between {3/4} and {5/6}</div><div class=\"exl\">LCM 12: {9/12} and {10/12}; nothing in between yet.<br>× 10: {90/120} and {100/120}. Any five of {91/120}, {92/120}, …, {99/120}.</div></div><div class=\"keybox\"><b>“Between” means strictly between:</b> the two given numbers themselves are not counted.</div><div class=\"hub-btns\" style=\"margin-top:12px\"><button class=\"hub-btn primary\" data-go=\"s7\">Practise 1.7 →</button></div></section><section class=\"note\" id=\"nsum\"><h2>Chapter checklist</h2><ul><li>Recognise rational numbers, find equivalent rational numbers and write rational numbers in standard form.</li><li>Represent rational numbers on the number line, compare and order them, and find absolute values.</li><li>Add rational numbers and use closure, commutativity, associativity, the additive identity and additive inverses.</li><li>Subtract rational numbers by adding the additive inverse and test the properties of subtraction.</li><li>Multiply rational numbers, find reciprocals and use the properties of multiplication, including distributivity.</li><li>Divide rational numbers using reciprocals, test the properties of division and solve real-life problems.</li><li>Find one or more rational numbers between two given rational numbers.</li></ul><div class=\"hub-btns\" style=\"margin-top:10px\"><button class=\"hub-btn\" data-go=\"s8\">Assessment A</button><button class=\"hub-btn\" data-go=\"s9\">Assessment B</button><button class=\"hub-btn\" data-go=\"s10\">Assessment C</button><button class=\"hub-btn\" data-go=\"s11\">Assessment D</button><button class=\"hub-btn primary\" data-go=\"report\">📊 Report</button></div></section>";
var REPORT = [["s8", "A", "Knowing and understanding"], ["s9", "B", "Investigating patterns"], ["s10", "C", "Communicating"], ["s11", "D", "Applying mathematics in real-life contexts"]];
var SECTIONS = [{"id": "s1", "label": "1.1 Standard form", "sub": "Rational numbers, equivalent rational numbers and standard form", "slides": [{"kind": "mcq", "text": "<b>Example 1</b> · State which of the following are rational numbers: a) {3/4}  b) {−7/8}  c) {0/6}  d) {8/0}  e) 10  f) −7", "opts": ["All six are rational", "Only a, b and e", "All of them except c and d", "All of them except d"], "correct": 3, "tag": "", "sol": "a) {3/4}, b) {−7/8}, c) {0/6}: integers on top and bottom and the denominator is not zero, so they are rational. d) {8/0} is not rational: the denominator is zero and division by zero is not defined. e) 10 = {10/1} and f) −7 = {−7/1} are rational."}, {"kind": "mcq", "text": "<b>Try This · Q1</b> · Which of the following are rational numbers? a) {−1/0}  b) {0/−1}  c) {1/−1}", "opts": ["b and c only", "a only", "c only", "a, b and c"], "correct": 0, "tag": "", "sol": "a) {−1/0} has denominator 0, so it is not rational. b) {0/−1} = 0 and c) {1/−1} = −1 have non-zero denominators, so they are rational."}, {"kind": "mcq", "text": "<b>Try This · Q2</b> · List any 5 rational numbers. Which of these lists contains five rational numbers?", "opts": ["{1/2}, −3, 0, {−4/5}, {7/9}", "{1/2}, −3, {5/0}, {−4/5}, {7/9}", "{2/0}, {3/0}, {4/0}, {5/0}, {6/0}", "{0/0}, 1, 2, 3, 4"], "correct": 0, "tag": "", "sol": "Every number in the first list can be written as {p/q} with q ≠ 0 (−3 = {−3/1}, 0 = {0/1}). The other lists contain numbers with denominator 0, which are not rational. Any five such numbers, e.g. {2/3}, 5, {−1/4}, 0, {9/7}, would do."}, {"kind": "blank", "p": "<b>Example 2</b> · Convert the rational number into an equivalent rational number with the given numerator or denominator.", "tag": "", "marks": "", "flat": [{"t": "a) {3/5} = {12/x}: x = __B1__", "a": {"B1": "20"}}, {"t": "b) {7/12} = {35/x}: x = __B1__", "a": {"B1": "60"}}, {"t": "c) {36/96} = {3/x}: x = __B1__", "a": {"B1": "8"}}, {"t": "d) {40/90} = {x/9}: x = __B1__", "a": {"B1": "4"}}], "sol": "12 ÷ 3 = 4, so {3/5} = (3 × 4)/(5 × 4) = {12/20}.\n35 ÷ 7 = 5, so {7/12} = (7 × 5)/(12 × 5) = {35/60}.\n36 ÷ 3 = 12, so {36/96} = (36 ÷ 12)/(96 ÷ 12) = {3/8}.\n90 ÷ 9 = 10, so {40/90} = (40 ÷ 10)/(90 ÷ 10) = {4/9}."}, {"kind": "mcq", "text": "<b>Example 3</b> · Which of the following rational numbers are in standard form?  a) {7/8}  b) {6/−35}  c) {8/12}  d) {39/91}", "opts": ["a and d", "a only", "All four", "a and b"], "correct": 1, "tag": "", "sol": "a) 7 and 8 are co-prime and the denominator is positive: standard form. b) the denominator is negative. c) 8 and 12 have the common factor 4. d) 39 and 91 have the common factor 13."}, {"kind": "blank", "p": "<b>Example 3</b> · Convert the other rational numbers into standard form.", "tag": "", "marks": "", "flat": [{"t": "b) {6/−35} = __B1__", "a": {"B1": "-6/35"}, "expr": "fl"}, {"t": "c) {8/12} = __B1__", "a": {"B1": "2/3"}, "expr": "fl"}, {"t": "d) {39/91} = __B1__", "a": {"B1": "3/7"}, "expr": "fl"}], "sol": "Multiply numerator and denominator by −1: (6 × (−1))/(−35 × (−1)) = {−6/35}.\n(8 ÷ 4)/(12 ÷ 4) = {2/3}.\n(39 ÷ 13)/(91 ÷ 13) = {3/7}."}, {"kind": "blank", "p": "<b>Try This · Q1</b> · Express in standard form.", "tag": "", "marks": "", "flat": [{"t": "a) {60/130} = __B1__", "a": {"B1": "6/13"}, "expr": "fl"}, {"t": "b) {35/70} = __B1__", "a": {"B1": "1/2"}, "expr": "fl"}, {"t": "c) {300/550} = __B1__", "a": {"B1": "6/11"}, "expr": "fl"}, {"t": "d) {85/102} = __B1__", "a": {"B1": "5/6"}, "expr": "fl"}], "sol": "HCF(60, 130) = 10: {6/13}.\nHCF(35, 70) = 35: {1/2}.\nHCF(300, 550) = 50: {6/11}.\nHCF(85, 102) = 17: {5/6}."}, {"kind": "mcq", "text": "<b>Ex 1A · Q1</b> · State which of the following are NOT rational numbers.  a) {3/7}  b) {123/478}  c) {1/1000}  d) {0/68}  e) {893/0}  f) {−8/9}  g) {−6/−25}  h) {18/−25}", "opts": ["e only", "d and e", "g and h", "d, e and h"], "correct": 0, "tag": "", "sol": "Only e) {893/0} is not rational, because its denominator is 0 and division by zero is not defined. All the others have integer numerators and non-zero integer denominators (d) {0/68} = 0 is rational)."}, {"kind": "mcq", "text": "<b>Ex 1A · Q2</b> · Which of the following are in standard form?  a) {4/6}  b) {4/−9}  c) {−11/−13}  d) {−21/−28}  e) {−42/48}  f) {18/15}  g) {−346/692}  h) {12/6}", "opts": ["a and f only", "b and c only", "c, e and g", "None of them"], "correct": 3, "tag": "", "sol": "a) common factor 2. b), c), d) have negative denominators. e) common factor 6. f) common factor 3. g) common factor 346. h) common factor 6. So none is in standard form."}, {"kind": "blank", "p": "<b>Ex 1A · Q2(a–d)</b> · Convert into standard form.", "tag": "", "marks": "", "flat": [{"t": "a) {4/6} = __B1__", "a": {"B1": "2/3"}, "expr": "fl"}, {"t": "b) {4/−9} = __B1__", "a": {"B1": "-4/9"}, "expr": "fl"}, {"t": "c) {−11/−13} = __B1__", "a": {"B1": "11/13"}, "expr": "fl"}, {"t": "d) {−21/−28} = __B1__", "a": {"B1": "3/4"}, "expr": "fl"}], "sol": "Divide by 2: {2/3}.\nMultiply by −1: {−4/9}.\nMultiply by −1: {11/13}.\nMultiply by −1: {21/28}; divide by 7: {3/4}."}, {"kind": "blank", "p": "<b>Ex 1A · Q2(e–h)</b> · Convert into standard form.", "tag": "", "marks": "", "flat": [{"t": "e) {−42/48} = __B1__", "a": {"B1": "-7/8"}, "expr": "fl"}, {"t": "f) {18/15} = __B1__", "a": {"B1": "6/5"}, "expr": "fl"}, {"t": "g) {−346/692} = __B1__", "a": {"B1": "-1/2"}, "expr": "fl"}, {"t": "h) {12/6} = __B1__", "a": {"B1": "2"}, "expr": "fl"}], "sol": "HCF 6: {−7/8}.\nHCF 3: {6/5}.\n692 = 2 × 346, so {−1/2}.\n{12/6} = {2/1} = 2."}, {"kind": "blank", "p": "<b>Ex 1A · Q3(a, b, d)</b> · Fill in the boxes (written here as x and y).", "tag": "", "marks": "", "flat": [{"t": "a) {4/5} = {−12/x} = {20/y}: x = __B1__, y = __B2__", "a": {"B1": "-15", "B2": "25"}}, {"t": "b) {−5/7} = {−15/x} = {−35/y}: x = __B1__, y = __B2__", "a": {"B1": "21", "B2": "49"}}, {"t": "d) {16/24} = {8/x} = {−32/y}: x = __B1__, y = __B2__", "a": {"B1": "12", "B2": "-48"}}], "sol": "−12 = 4 × (−3), so x = 5 × (−3) = −15; 20 = 4 × 5, so y = 5 × 5 = 25.\n−15 = −5 × 3, so x = 21; −35 = −5 × 7, so y = 49.\n8 = 16 ÷ 2, so x = 24 ÷ 2 = 12; −32 = 16 × (−2), so y = 24 × (−2) = −48."}, {"kind": "mcq", "text": "<b>Ex 1A · Q3(c)</b> · Fill in the boxes: {−3/x} = {6/−16} = {y/24}. The values of x and y are", "opts": ["x = 8, y = −9", "x = −8, y = 9", "x = 8, y = 9", "x = −8, y = −9"], "correct": 0, "tag": "", "sol": "{6/−16} = {−6/16} = {−3/8}, so x = 8. {−3/8} = (−3 × 3)/(8 × 3) = {−9/24}, so y = −9."}, {"kind": "blank", "p": "<b>Ex 1A · Q4</b> · Express as rational numbers with positive denominators.", "tag": "", "marks": "", "flat": [{"t": "a) {12/−29} = __B1__", "a": {"B1": "-12/29"}, "expr": "fv"}, {"t": "b) {3/−8} = __B1__", "a": {"B1": "-3/8"}, "expr": "fv"}, {"t": "c) {−16/−24} = __B1__", "a": {"B1": "2/3"}, "expr": "fv"}, {"t": "d) {−6/−19} = __B1__", "a": {"B1": "6/19"}, "expr": "fv"}], "sol": "Multiply by −1: {−12/29}.\nMultiply by −1: {−3/8}.\nMultiply by −1: {16/24} (= {2/3}).\nMultiply by −1: {6/19}."}, {"kind": "blank", "p": "<b>Ex 1A · Q5</b> · Convert {4/9} into equivalent rational numbers with the given numerators. Write the new denominator.", "tag": "", "marks": "", "flat": [{"t": "a) numerator 20: {4/9} = {20/x}, x = __B1__", "a": {"B1": "45"}}, {"t": "b) numerator −16: {4/9} = {−16/x}, x = __B1__", "a": {"B1": "-36"}}, {"t": "c) numerator 12: {4/9} = {12/x}, x = __B1__", "a": {"B1": "27"}}, {"t": "d) numerator −24: {4/9} = {−24/x}, x = __B1__", "a": {"B1": "-54"}}], "sol": "20 = 4 × 5, so x = 9 × 5 = 45: {20/45}.\n−16 = 4 × (−4), so x = 9 × (−4) = −36: {−16/−36}.\n12 = 4 × 3, so x = 27: {12/27}.\n−24 = 4 × (−6), so x = −54: {−24/−54}."}]}, {"id": "s2", "label": "1.2 Number line & compare", "sub": "Number line, comparison, ordering and absolute value", "slides": [{"kind": "blank", "p": "<b>Example 4</b> · Represent {5/3}, {−1/3} and {2/3} on a number line.", "tag": "", "marks": "", "flat": [{"t": "Divide each unit length into __B1__ equal parts.", "a": {"B1": "3"}}, {"t": "{5/3} is __B1__ parts to the right of 0.", "a": {"B1": "5"}}, {"t": "{−1/3} is __B1__ part(s) to the left of 0.", "a": {"B1": "1"}}, {"t": "{2/3} is __B1__ parts to the right of 0.", "a": {"B1": "2"}}], "sol": "The denominator is 3, so each unit is split into 3 parts (thirds).\nCount 5 thirds to the right: {5/3} lies between 1 and 2.\nCount 1 third to the left of 0.\nCount 2 thirds to the right: {2/3} lies between 0 and 1.", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 330 76\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><line class=\"ln\" x1=\"14.0\" y1=\"30.0\" x2=\"316.0\" y2=\"30.0\" marker-end=\"url(#ah)\" marker-start=\"url(#ahs)\"/><line x1=\"22.0\" y1=\"21\" x2=\"22.0\" y2=\"39\" style=\"stroke:var(--ink);stroke-width:1.6\"/><text class=\"lb\" x=\"22.0\" y=\"50.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−1</text><line x1=\"53.8\" y1=\"25\" x2=\"53.8\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"85.6\" y1=\"25\" x2=\"85.6\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"117.3\" y1=\"21\" x2=\"117.3\" y2=\"39\" style=\"stroke:var(--ink);stroke-width:1.6\"/><text class=\"lb\" x=\"117.3\" y=\"50.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">0</text><line x1=\"149.1\" y1=\"25\" x2=\"149.1\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"180.9\" y1=\"25\" x2=\"180.9\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"212.7\" y1=\"21\" x2=\"212.7\" y2=\"39\" style=\"stroke:var(--ink);stroke-width:1.6\"/><text class=\"lb\" x=\"212.7\" y=\"50.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">1</text><line x1=\"244.4\" y1=\"25\" x2=\"244.4\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"276.2\" y1=\"25\" x2=\"276.2\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"308.0\" y1=\"21\" x2=\"308.0\" y2=\"39\" style=\"stroke:var(--ink);stroke-width:1.6\"/><text class=\"lb\" x=\"308.0\" y=\"50.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2</text></svg>"}, {"kind": "mcq", "text": "<b>Try This · Q2</b> · Represent {−3/4}, {−6/4}, {2/4} and {5/4} on a number line. The points P, Q, R, S show these numbers. Which labelling is correct?", "opts": ["P = {−6/4}, Q = {−3/4}, R = {2/4}, S = {5/4}", "P = {−3/4}, Q = {−6/4}, R = {5/4}, S = {2/4}", "P = {−6/4}, Q = {−3/4}, R = {5/4}, S = {2/4}", "P = {−3/4}, Q = {−6/4}, R = {2/4}, S = {5/4}"], "correct": 0, "tag": "", "sol": "Each unit is divided into 4 parts. {−6/4} is 6 quarters left of 0 (P), {−3/4} is 3 quarters left (Q), {2/4} is 2 quarters right (R) and {5/4} is 5 quarters right (S).", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 330 76\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><line class=\"ln\" x1=\"14.0\" y1=\"30.0\" x2=\"316.0\" y2=\"30.0\" marker-end=\"url(#ah)\" marker-start=\"url(#ahs)\"/><line x1=\"22.0\" y1=\"21\" x2=\"22.0\" y2=\"39\" style=\"stroke:var(--ink);stroke-width:1.6\"/><text class=\"lb\" x=\"22.0\" y=\"50.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−2</text><line x1=\"39.9\" y1=\"25\" x2=\"39.9\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"57.8\" y1=\"25\" x2=\"57.8\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"75.6\" y1=\"25\" x2=\"75.6\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"93.5\" y1=\"21\" x2=\"93.5\" y2=\"39\" style=\"stroke:var(--ink);stroke-width:1.6\"/><text class=\"lb\" x=\"93.5\" y=\"50.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−1</text><line x1=\"111.4\" y1=\"25\" x2=\"111.4\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"129.2\" y1=\"25\" x2=\"129.2\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"147.1\" y1=\"25\" x2=\"147.1\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"165.0\" y1=\"21\" x2=\"165.0\" y2=\"39\" style=\"stroke:var(--ink);stroke-width:1.6\"/><text class=\"lb\" x=\"165.0\" y=\"50.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">0</text><line x1=\"182.9\" y1=\"25\" x2=\"182.9\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"200.8\" y1=\"25\" x2=\"200.8\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"218.6\" y1=\"25\" x2=\"218.6\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"236.5\" y1=\"21\" x2=\"236.5\" y2=\"39\" style=\"stroke:var(--ink);stroke-width:1.6\"/><text class=\"lb\" x=\"236.5\" y=\"50.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">1</text><line x1=\"254.4\" y1=\"25\" x2=\"254.4\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"272.2\" y1=\"25\" x2=\"272.2\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"290.1\" y1=\"25\" x2=\"290.1\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"308.0\" y1=\"21\" x2=\"308.0\" y2=\"39\" style=\"stroke:var(--ink);stroke-width:1.6\"/><text class=\"lb\" x=\"308.0\" y=\"50.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2</text><circle cx=\"57.8\" cy=\"30\" r=\"5\" style=\"fill:var(--danger)\"/><text class=\"al\" x=\"57.8\" y=\"13.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">P</text><circle cx=\"111.4\" cy=\"30\" r=\"5\" style=\"fill:var(--danger)\"/><text class=\"al\" x=\"111.4\" y=\"13.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">Q</text><circle cx=\"200.8\" cy=\"30\" r=\"5\" style=\"fill:var(--danger)\"/><text class=\"al\" x=\"200.8\" y=\"13.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">R</text><circle cx=\"254.4\" cy=\"30\" r=\"5\" style=\"fill:var(--danger)\"/><text class=\"al\" x=\"254.4\" y=\"13.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">S</text></svg>"}, {"kind": "mcq", "text": "<b>Example 5</b> · Compare using the number line: a) 0 and {2/3}   b) {−4/3} and {−1/3}", "opts": ["0 > {2/3} and {−4/3} < {−1/3}", "0 > {2/3} and {−4/3} > {−1/3}", "0 < {2/3} and {−4/3} < {−1/3}", "0 < {2/3} and {−4/3} > {−1/3}"], "correct": 2, "tag": "", "sol": "a) 0 is on the left of {2/3}, so 0 < {2/3}. b) {−4/3} is on the left of {−1/3}, so {−4/3} < {−1/3} (i.e. {−1/3} > {−4/3}).", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 330 76\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><line class=\"ln\" x1=\"14.0\" y1=\"30.0\" x2=\"316.0\" y2=\"30.0\" marker-end=\"url(#ah)\" marker-start=\"url(#ahs)\"/><line x1=\"22.0\" y1=\"21\" x2=\"22.0\" y2=\"39\" style=\"stroke:var(--ink);stroke-width:1.6\"/><text class=\"lb\" x=\"22.0\" y=\"50.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−2</text><line x1=\"45.8\" y1=\"25\" x2=\"45.8\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"69.7\" y1=\"25\" x2=\"69.7\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"93.5\" y1=\"21\" x2=\"93.5\" y2=\"39\" style=\"stroke:var(--ink);stroke-width:1.6\"/><text class=\"lb\" x=\"93.5\" y=\"50.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−1</text><line x1=\"117.3\" y1=\"25\" x2=\"117.3\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"141.2\" y1=\"25\" x2=\"141.2\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"165.0\" y1=\"21\" x2=\"165.0\" y2=\"39\" style=\"stroke:var(--ink);stroke-width:1.6\"/><text class=\"lb\" x=\"165.0\" y=\"50.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">0</text><line x1=\"188.8\" y1=\"25\" x2=\"188.8\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"212.7\" y1=\"25\" x2=\"212.7\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"236.5\" y1=\"21\" x2=\"236.5\" y2=\"39\" style=\"stroke:var(--ink);stroke-width:1.6\"/><text class=\"lb\" x=\"236.5\" y=\"50.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">1</text><line x1=\"260.3\" y1=\"25\" x2=\"260.3\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"284.2\" y1=\"25\" x2=\"284.2\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"308.0\" y1=\"21\" x2=\"308.0\" y2=\"39\" style=\"stroke:var(--ink);stroke-width:1.6\"/><text class=\"lb\" x=\"308.0\" y=\"50.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2</text></svg>"}, {"kind": "blank", "p": "<b>Example 6</b> · Compare the two rational numbers {−1/8} and {5/−4}. Which is greater?", "tag": "", "marks": "", "flat": [{"t": "Step 1: write with positive denominators: {5/−4} = {x/4}, x = __B1__", "a": {"B1": "-5"}}, {"t": "Step 2: LCM of 8 and 4 = __B1__", "a": {"B1": "8"}}, {"t": "Step 3: {−5/4} = {y/8}, y = __B1__", "a": {"B1": "-10"}}, {"t": "Step 4: the greater number is __B1__", "a": {"B1": "-1/8"}, "expr": "fl"}], "sol": "Multiply by −1: {5/−4} = {−5/4}.\n8 is a multiple of 4, so the LCM is 8.\n(−5 × 2)/(4 × 2) = {−10/8}.\n−1 > −10, so {−1/8} > {−10/8}, i.e. {−1/8} > {5/−4}."}, {"kind": "mcq", "text": "<b>Example 7</b> · Compare the two rational numbers {2/9} and {5/6}. Which is smaller?", "opts": ["{2/9}, because {4/18} < {15/18}", "{2/9}, because 2 < 5 and 9 > 6 so it is the same as {5/6}", "{5/6}, because {5/6} = {15/18} < {2/9} = {4/18}", "{5/6}, because 6 < 9 so sixths are smaller"], "correct": 0, "tag": "", "sol": "LCM of 9 and 6 = 18. {2/9} = {4/18} and {5/6} = {15/18}. 4 < 15, so {2/9} < {5/6}: {2/9} is smaller."}, {"kind": "mcq", "text": "<b>Try This</b> · Circle the greater rational number:  a) {3/8}, {7/8}   b) {7/12}, {5/6}   c) {5/8}, {5/9}   d) {8/10}, {8/15}", "opts": ["a) {3/8}  b) {5/6}  c) {5/9}  d) {8/10}", "a) {7/8}  b) {5/6}  c) {5/9}  d) {8/15}", "a) {7/8}  b) {7/12}  c) {5/8}  d) {8/10}", "a) {7/8}  b) {5/6}  c) {5/8}  d) {8/10}"], "correct": 3, "tag": "", "sol": "a) same denominator: 7 > 3, so {7/8}. b) {5/6} = {10/12} > {7/12}. c) same numerator: the smaller denominator gives the greater number, {5/8}. d) likewise {8/10} > {8/15}."}, {"kind": "blank", "p": "<b>Example 8</b> · Arrange the following rational numbers in ascending order: {3/8}, {4/12}, {−7/16}, {−2/3}.", "tag": "", "marks": "", "flat": [{"t": "Step 1: LCM of 8, 12, 16 and 3 = __B1__", "a": {"B1": "48"}}, {"t": "Step 2: numerators over 48, in the order given: __B1__", "a": {"B1": "18, 16, -21, -32"}, "expr": "dlist"}, {"t": "Step 3: the numerators in ascending order: __B1__", "a": {"B1": "-32, -21, 16, 18"}, "expr": "dlist"}, {"t": "So the smallest number is __B1__", "a": {"B1": "-2/3"}, "expr": "fl"}], "sol": "LCM = 2 × 2 × 2 × 2 × 3 = 48.\n{3/8} = {18/48}, {4/12} = {16/48}, {−7/16} = {−21/48}, {−2/3} = {−32/48}.\n−32 < −21 < 16 < 18.\nAscending order: {−2/3} < {−7/16} < {4/12} < {3/8}."}, {"kind": "mcq", "text": "<b>Example 9</b> · Find the absolute value of {−2/3}.", "opts": ["{3/2}", "0", "{2/3}", "{−2/3}"], "correct": 2, "tag": "", "sol": "The distance of {−2/3} from 0 is {2/3}: |{−2/3}| = {2/3}."}, {"kind": "blank", "p": "<b>Try This</b> · Find the absolute value of each of the following.", "tag": "", "marks": "", "flat": [{"t": "a) |{3/7}| = __B1__", "a": {"B1": "3/7"}, "expr": "fl"}, {"t": "b) |{−8/13}| = __B1__", "a": {"B1": "8/13"}, "expr": "fl"}, {"t": "c) |{18/−25}| = __B1__", "a": {"B1": "18/25"}, "expr": "fl"}, {"t": "d) |{−12/−13}| = __B1__", "a": {"B1": "12/13"}, "expr": "fl"}], "sol": "{3/7} is positive, so its absolute value is {3/7}.\nDistance from 0 is {8/13}.\n{18/−25} = {−18/25}; absolute value {18/25}.\n{−12/−13} = {12/13}, which is positive."}, {"kind": "blank", "p": "<b>Ex 1A · Q6</b> · Locate the points on a number line. Type the letter of the point that shows each number.", "tag": "", "marks": "", "flat": [{"t": "a) {3/7} → __B1__, {−2/7} → __B2__, 1 → __B3__, {−8/7} → __B4__, 0 → __B5__", "a": {"B1": "S", "B2": "Q", "B3": "T", "B4": "P", "B5": "R"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 330 76\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><line class=\"ln\" x1=\"14.0\" y1=\"30.0\" x2=\"316.0\" y2=\"30.0\" marker-end=\"url(#ah)\" marker-start=\"url(#ahs)\"/><line x1=\"22.0\" y1=\"21\" x2=\"22.0\" y2=\"39\" style=\"stroke:var(--ink);stroke-width:1.6\"/><text class=\"lb\" x=\"22.0\" y=\"50.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−2</text><line x1=\"32.2\" y1=\"25\" x2=\"32.2\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"42.4\" y1=\"25\" x2=\"42.4\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"52.6\" y1=\"25\" x2=\"52.6\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"62.9\" y1=\"25\" x2=\"62.9\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"73.1\" y1=\"25\" x2=\"73.1\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"83.3\" y1=\"25\" x2=\"83.3\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"93.5\" y1=\"21\" x2=\"93.5\" y2=\"39\" style=\"stroke:var(--ink);stroke-width:1.6\"/><text class=\"lb\" x=\"93.5\" y=\"50.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−1</text><line x1=\"103.7\" y1=\"25\" x2=\"103.7\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"113.9\" y1=\"25\" x2=\"113.9\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"124.1\" y1=\"25\" x2=\"124.1\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"134.4\" y1=\"25\" x2=\"134.4\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"144.6\" y1=\"25\" x2=\"144.6\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"154.8\" y1=\"25\" x2=\"154.8\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"165.0\" y1=\"21\" x2=\"165.0\" y2=\"39\" style=\"stroke:var(--ink);stroke-width:1.6\"/><text class=\"lb\" x=\"165.0\" y=\"50.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">0</text><line x1=\"175.2\" y1=\"25\" x2=\"175.2\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"185.4\" y1=\"25\" x2=\"185.4\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"195.6\" y1=\"25\" x2=\"195.6\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"205.9\" y1=\"25\" x2=\"205.9\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"216.1\" y1=\"25\" x2=\"216.1\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"226.3\" y1=\"25\" x2=\"226.3\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"236.5\" y1=\"21\" x2=\"236.5\" y2=\"39\" style=\"stroke:var(--ink);stroke-width:1.6\"/><text class=\"lb\" x=\"236.5\" y=\"50.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">1</text><line x1=\"246.7\" y1=\"25\" x2=\"246.7\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"256.9\" y1=\"25\" x2=\"256.9\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"267.1\" y1=\"25\" x2=\"267.1\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"277.4\" y1=\"25\" x2=\"277.4\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"287.6\" y1=\"25\" x2=\"287.6\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"297.8\" y1=\"25\" x2=\"297.8\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"308.0\" y1=\"21\" x2=\"308.0\" y2=\"39\" style=\"stroke:var(--ink);stroke-width:1.6\"/><text class=\"lb\" x=\"308.0\" y=\"50.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2</text><circle cx=\"83.3\" cy=\"30\" r=\"5\" style=\"fill:var(--danger)\"/><text class=\"al\" x=\"83.3\" y=\"13.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">P</text><circle cx=\"144.6\" cy=\"30\" r=\"5\" style=\"fill:var(--danger)\"/><text class=\"al\" x=\"144.6\" y=\"13.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">Q</text><circle cx=\"165.0\" cy=\"30\" r=\"5\" style=\"fill:var(--danger)\"/><text class=\"al\" x=\"165.0\" y=\"13.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">R</text><circle cx=\"195.6\" cy=\"30\" r=\"5\" style=\"fill:var(--danger)\"/><text class=\"al\" x=\"195.6\" y=\"13.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">S</text><circle cx=\"236.5\" cy=\"30\" r=\"5\" style=\"fill:var(--danger)\"/><text class=\"al\" x=\"236.5\" y=\"13.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">T</text></svg>"}, {"t": "b) {−4/3} → __B1__, {1/3} → __B2__, {7/3} → __B3__, 0 → __B4__, 2 → __B5__", "a": {"B1": "P", "B2": "R", "B3": "T", "B4": "Q", "B5": "S"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 330 76\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><line class=\"ln\" x1=\"14.0\" y1=\"30.0\" x2=\"316.0\" y2=\"30.0\" marker-end=\"url(#ah)\" marker-start=\"url(#ahs)\"/><line x1=\"22.0\" y1=\"21\" x2=\"22.0\" y2=\"39\" style=\"stroke:var(--ink);stroke-width:1.6\"/><text class=\"lb\" x=\"22.0\" y=\"50.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−2</text><line x1=\"41.1\" y1=\"25\" x2=\"41.1\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"60.1\" y1=\"25\" x2=\"60.1\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"79.2\" y1=\"21\" x2=\"79.2\" y2=\"39\" style=\"stroke:var(--ink);stroke-width:1.6\"/><text class=\"lb\" x=\"79.2\" y=\"50.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−1</text><line x1=\"98.3\" y1=\"25\" x2=\"98.3\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"117.3\" y1=\"25\" x2=\"117.3\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"136.4\" y1=\"21\" x2=\"136.4\" y2=\"39\" style=\"stroke:var(--ink);stroke-width:1.6\"/><text class=\"lb\" x=\"136.4\" y=\"50.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">0</text><line x1=\"155.5\" y1=\"25\" x2=\"155.5\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"174.5\" y1=\"25\" x2=\"174.5\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"193.6\" y1=\"21\" x2=\"193.6\" y2=\"39\" style=\"stroke:var(--ink);stroke-width:1.6\"/><text class=\"lb\" x=\"193.6\" y=\"50.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">1</text><line x1=\"212.7\" y1=\"25\" x2=\"212.7\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"231.7\" y1=\"25\" x2=\"231.7\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"250.8\" y1=\"21\" x2=\"250.8\" y2=\"39\" style=\"stroke:var(--ink);stroke-width:1.6\"/><text class=\"lb\" x=\"250.8\" y=\"50.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2</text><line x1=\"269.9\" y1=\"25\" x2=\"269.9\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"288.9\" y1=\"25\" x2=\"288.9\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"308.0\" y1=\"21\" x2=\"308.0\" y2=\"39\" style=\"stroke:var(--ink);stroke-width:1.6\"/><text class=\"lb\" x=\"308.0\" y=\"50.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">3</text><circle cx=\"60.1\" cy=\"30\" r=\"5\" style=\"fill:var(--danger)\"/><text class=\"al\" x=\"60.1\" y=\"13.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">P</text><circle cx=\"136.4\" cy=\"30\" r=\"5\" style=\"fill:var(--danger)\"/><text class=\"al\" x=\"136.4\" y=\"13.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">Q</text><circle cx=\"155.5\" cy=\"30\" r=\"5\" style=\"fill:var(--danger)\"/><text class=\"al\" x=\"155.5\" y=\"13.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">R</text><circle cx=\"250.8\" cy=\"30\" r=\"5\" style=\"fill:var(--danger)\"/><text class=\"al\" x=\"250.8\" y=\"13.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">S</text><circle cx=\"269.9\" cy=\"30\" r=\"5\" style=\"fill:var(--danger)\"/><text class=\"al\" x=\"269.9\" y=\"13.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">T</text></svg>"}, {"t": "c) {4/5} → __B1__, {10/5} → __B2__, {−3/5} → __B3__, {−7/5} → __B4__, 1 → __B5__", "a": {"B1": "R", "B2": "T", "B3": "Q", "B4": "P", "B5": "S"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 330 76\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><line class=\"ln\" x1=\"14.0\" y1=\"30.0\" x2=\"316.0\" y2=\"30.0\" marker-end=\"url(#ah)\" marker-start=\"url(#ahs)\"/><line x1=\"22.0\" y1=\"21\" x2=\"22.0\" y2=\"39\" style=\"stroke:var(--ink);stroke-width:1.6\"/><text class=\"lb\" x=\"22.0\" y=\"50.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−2</text><line x1=\"36.3\" y1=\"25\" x2=\"36.3\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"50.6\" y1=\"25\" x2=\"50.6\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"64.9\" y1=\"25\" x2=\"64.9\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"79.2\" y1=\"25\" x2=\"79.2\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"93.5\" y1=\"21\" x2=\"93.5\" y2=\"39\" style=\"stroke:var(--ink);stroke-width:1.6\"/><text class=\"lb\" x=\"93.5\" y=\"50.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−1</text><line x1=\"107.8\" y1=\"25\" x2=\"107.8\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"122.1\" y1=\"25\" x2=\"122.1\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"136.4\" y1=\"25\" x2=\"136.4\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"150.7\" y1=\"25\" x2=\"150.7\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"165.0\" y1=\"21\" x2=\"165.0\" y2=\"39\" style=\"stroke:var(--ink);stroke-width:1.6\"/><text class=\"lb\" x=\"165.0\" y=\"50.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">0</text><line x1=\"179.3\" y1=\"25\" x2=\"179.3\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"193.6\" y1=\"25\" x2=\"193.6\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"207.9\" y1=\"25\" x2=\"207.9\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"222.2\" y1=\"25\" x2=\"222.2\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"236.5\" y1=\"21\" x2=\"236.5\" y2=\"39\" style=\"stroke:var(--ink);stroke-width:1.6\"/><text class=\"lb\" x=\"236.5\" y=\"50.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">1</text><line x1=\"250.8\" y1=\"25\" x2=\"250.8\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"265.1\" y1=\"25\" x2=\"265.1\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"279.4\" y1=\"25\" x2=\"279.4\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"293.7\" y1=\"25\" x2=\"293.7\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"308.0\" y1=\"21\" x2=\"308.0\" y2=\"39\" style=\"stroke:var(--ink);stroke-width:1.6\"/><text class=\"lb\" x=\"308.0\" y=\"50.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2</text><circle cx=\"64.9\" cy=\"30\" r=\"5\" style=\"fill:var(--danger)\"/><text class=\"al\" x=\"64.9\" y=\"13.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">P</text><circle cx=\"122.1\" cy=\"30\" r=\"5\" style=\"fill:var(--danger)\"/><text class=\"al\" x=\"122.1\" y=\"13.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">Q</text><circle cx=\"222.2\" cy=\"30\" r=\"5\" style=\"fill:var(--danger)\"/><text class=\"al\" x=\"222.2\" y=\"13.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">R</text><circle cx=\"236.5\" cy=\"30\" r=\"5\" style=\"fill:var(--danger)\"/><text class=\"al\" x=\"236.5\" y=\"13.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">S</text><circle cx=\"308.0\" cy=\"30\" r=\"5\" style=\"fill:var(--danger)\"/><text class=\"al\" x=\"308.0\" y=\"13.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">T</text></svg>"}], "sol": "Sevenths: {−8/7} is 8 parts left of 0 (P), {−2/7} is 2 parts left (Q), 0 (R), {3/7} is 3 parts right (S), 1 = {7/7} (T).\nThirds: {−4/3} (P), 0 (Q), {1/3} (R), 2 = {6/3} (S), {7/3} (T).\nFifths: {−7/5} (P), {−3/5} (Q), {4/5} (R), 1 = {5/5} (S), {10/5} = 2 (T)."}, {"kind": "mcq", "text": "<b>Ex 1A · Q7(a–d)</b> · Fill in the boxes using =, > or <:  a) {−11/3} □ {−2/3}   b) {−7/3} □ {−12/3}   c) {3/3} □ {−5/−5}   d) {−9/3} □ {0/3}", "opts": ["<, >, =, <", ">, <, =, <", "<, <, =, >", "<, >, >, <"], "correct": 0, "tag": "", "sol": "Same denominators, so compare numerators: a) −11 < −2. b) −7 > −12. c) {3/3} = 1 and {−5/−5} = 1, so =. d) −9 < 0."}, {"kind": "mcq", "text": "<b>Ex 1A · Q7(e–h)</b> · Fill in the boxes using =, > or <:  e) {−10/3} □ {−5/3}   f) {8/3} □ {2/3}   g) {6/3} □ {−6/3}   h) {12/3} □ {−1/3}", "opts": ["<, <, >, >", "<, >, >, >", ">, >, >, >", "<, >, <, >"], "correct": 1, "tag": "", "sol": "e) −10 < −5. f) 8 > 2. g) 6 > −6. h) 12 > −1."}, {"kind": "blank", "p": "<b>Ex 1A · Q8</b> · Determine which of the two rational numbers is greater in each case (use a positive denominator).", "tag": "", "marks": "", "flat": [{"t": "a) {−3/7}, {2/7}: __B1__", "a": {"B1": "2/7"}, "expr": "fv"}, {"t": "b) {−4/9}, {−5/6}: __B1__", "a": {"B1": "-4/9"}, "expr": "fv"}, {"t": "c) {1/2}, {4/7}: __B1__", "a": {"B1": "4/7"}, "expr": "fv"}, {"t": "d) {−7/11}, {5/8}: __B1__", "a": {"B1": "5/8"}, "expr": "fv"}, {"t": "e) {−3/−13}, {−5/−21}: __B1__", "a": {"B1": "5/21"}, "expr": "fv"}], "sol": "Same denominator: 2 > −3, so {2/7}.\nLCM 18: {−8/18} and {−15/18}; −8 > −15, so {−4/9}.\nLCM 14: {7/14} and {8/14}, so {4/7}.\nA positive number is greater than a negative one: {5/8}.\n{3/13} and {5/21}; LCM 273: {63/273} and {65/273}, so {−5/−21} = {5/21} is greater."}, {"kind": "mcq", "text": "<b>Ex 1A · Q9(a–d)</b> · Fill in the boxes using <, = or >:  a) {−7/12} □ {−5/−8}   b) {−4/9} □ {−3/7}   c) {−7/8} □ {14/17}   d) {−2/9} □ {8/−36}", "opts": ["<, <, >, =", ">, <, <, =", "<, <, <, =", "<, >, <, ="], "correct": 2, "tag": "", "sol": "a) {−5/−8} = {5/8} is positive, so {−7/12} < {5/8}. b) LCM 63: {−28/63} < {−27/63}. c) negative < positive. d) {8/−36} = {−2/9}, so they are equal."}, {"kind": "mcq", "text": "<b>Ex 1A · Q9(e–h)</b> · Fill in the boxes using <, = or >:  e) {5/8} □ {25/45}   f) {4/6} □ {1/12}   g) {8/9} □ {8/19}   h) {19/35} □ {19/20}", "opts": [">, >, >, <", "<, >, >, <", ">, <, >, <", ">, >, <, >"], "correct": 0, "tag": "", "sol": "e) {25/45} = {5/9}; same numerator, smaller denominator 8 gives the greater number: {5/8} > {5/9}. f) {8/12} > {1/12}. g) same numerator: {8/9} > {8/19}. h) same numerator: {19/35} < {19/20}."}, {"kind": "blank", "p": "<b>Ex 1A · Q10</b> · Arrange in ascending order: {2/5}, {−1/2}, {8/−15}, {−3/−10}.", "tag": "", "marks": "", "flat": [{"t": "LCM of 5, 2, 15 and 10 = __B1__", "a": {"B1": "30"}}, {"t": "Numerators over 30 (positive denominators), in the order given: __B1__", "a": {"B1": "12, -15, -16, 9"}, "expr": "dlist"}, {"t": "Numerators in ascending order: __B1__", "a": {"B1": "-16, -15, 9, 12"}, "expr": "dlist"}, {"t": "Smallest number = __B1__", "a": {"B1": "-8/15"}, "expr": "fl"}, {"t": "Greatest number = __B1__", "a": {"B1": "2/5"}, "expr": "fl"}], "sol": "LCM = 30.\n{12/30}, {−15/30}, {−16/30}, {9/30}.\n−16 < −15 < 9 < 12.\n{8/−15} = {−8/15} is the smallest.\nAscending: {8/−15}, {−1/2}, {−3/−10}, {2/5}; the greatest is {2/5}."}, {"kind": "blank", "p": "<b>Ex 1A · Q11</b> · Arrange in descending order: {−7/10}, {8/−15}, {19/30}, {−2/−5}.", "tag": "", "marks": "", "flat": [{"t": "LCM of 10, 15, 30 and 5 = __B1__", "a": {"B1": "30"}}, {"t": "Numerators over 30 (positive denominators), in the order given: __B1__", "a": {"B1": "-21, -16, 19, 12"}, "expr": "dlist"}, {"t": "Numerators in descending order: __B1__", "a": {"B1": "19, 12, -16, -21"}, "expr": "dlist"}, {"t": "Greatest number = __B1__", "a": {"B1": "19/30"}, "expr": "fl"}, {"t": "Smallest number = __B1__", "a": {"B1": "-7/10"}, "expr": "fl"}], "sol": "LCM = 30.\n{−21/30}, {−16/30}, {19/30}, {12/30}.\n19 > 12 > −16 > −21.\n{19/30} is the greatest.\nDescending: {19/30}, {−2/−5}, {8/−15}, {−7/10}; the smallest is {−7/10}."}]}, {"id": "s3", "label": "1.3 Addition", "sub": "Adding rational numbers and the properties of addition", "slides": [{"kind": "mcq", "text": "<b>Example 10</b> · Add {5/6} and {7/6}.", "opts": ["2", "{2/6}", "{12/36}", "{35/36}"], "correct": 0, "tag": "", "sol": "Same denominators: (5 + 7)/6 = {12/6} = 2."}, {"kind": "blank", "p": "<b>Example 11</b> · Add {7/5} and {−13/5}.", "tag": "", "marks": "", "flat": [{"t": "{7/5} + ({−13/5}) = __B1__", "a": {"B1": "-6/5"}, "expr": "fl"}], "sol": "Same denominators: (7 − 13)/5 = {−6/5}."}, {"kind": "blank", "p": "<b>Example 12</b> · Find the sum {4/3} + {5/6}.", "tag": "", "marks": "", "flat": [{"t": "LCM of 3 and 6 = __B1__", "a": {"B1": "6"}}, {"t": "{4/3} = {x/6}: x = __B1__", "a": {"B1": "8"}}, {"t": "{4/3} + {5/6} = __B1__", "a": {"B1": "13/6"}, "expr": "fl"}], "sol": "3 is a factor of 6, so the LCM is 6.\n(4 × 2)/(3 × 2) = {8/6}.\n{8/6} + {5/6} = {13/6} = {2 1/6}."}, {"kind": "mcq", "text": "<b>Example 13</b> · Add: {−3/7} + ({−5/21})", "opts": ["{−8/21}", "{−2/3}", "{−8/28}", "{2/3}"], "correct": 1, "tag": "", "sol": "{−3/7} = {−9/21}. {−9/21} + {−5/21} = {−14/21} = {−2/3}."}, {"kind": "blank", "p": "<b>Example 14</b> · Find the sum of {4/5} and {−6/7}.", "tag": "", "marks": "", "flat": [{"t": "5 and 7 are co-prime, so the LCM = __B1__", "a": {"B1": "35"}}, {"t": "{4/5} = {x/35} and {−6/7} = {y/35}: x = __B1__, y = __B2__", "a": {"B1": "28", "B2": "-30"}}, {"t": "Sum = __B1__", "a": {"B1": "-2/35"}, "expr": "fl"}], "sol": "LCM = 5 × 7 = 35.\n4 × 7 = 28; −6 × 5 = −30.\n(28 − 30)/35 = {−2/35}."}, {"kind": "mcq", "text": "<b>Example 15</b> · Find the sum: {5/12} + {7/8}", "opts": ["{31/24}", "{31/48}", "{12/20}", "{35/96}"], "correct": 0, "tag": "", "sol": "12 and 8 have common factors; LCM = 24. {5/12} = {10/24}, {7/8} = {21/24}. (10 + 21)/24 = {31/24} = {1 7/24}."}, {"kind": "mcq", "text": "<b>Try This</b> · Find the sum of each:  a) {4/6} + ({−5/6})   b) {1/2} + {3/8}   c) {4/5} + ({−2/7})   d) {4/10} + {7/15}", "opts": ["a) {1/6}  b) {7/8}  c) {18/35}  d) {13/15}", "a) {−1/6}  b) {4/10}  c) {2/35}  d) {11/25}", "a) {−1/6}  b) {7/8}  c) {−18/35}  d) {11/15}", "a) {−1/6}  b) {7/8}  c) {18/35}  d) {13/15}"], "correct": 3, "tag": "", "sol": "a) (4 − 5)/6 = {−1/6}. b) {4/8} + {3/8} = {7/8}. c) LCM 35: {28/35} − {10/35} = {18/35}. d) LCM 30: {12/30} + {14/30} = {26/30} = {13/15}."}, {"kind": "blank", "p": "<b>Ex 1B · Q1</b> · Add the following (answers in lowest terms).", "tag": "", "marks": "", "flat": [{"t": "a) {2/9} + {5/9} = __B1__", "a": {"B1": "7/9"}, "expr": "fl"}, {"t": "b) {11/15} + ({−7/15}) = __B1__", "a": {"B1": "4/15"}, "expr": "fl"}, {"t": "c) {−5/12} + ({−8/12}) = __B1__", "a": {"B1": "-13/12"}, "expr": "fl"}, {"t": "d) {7/40} + ({−23/40}) = __B1__", "a": {"B1": "-2/5"}, "expr": "fl"}, {"t": "e) {−8/25} + {4/25} = __B1__", "a": {"B1": "-4/25"}, "expr": "fl"}, {"t": "f) {22/35} + ({−15/35}) = __B1__", "a": {"B1": "1/5"}, "expr": "fl"}], "sol": "(2 + 5)/9 = {7/9}.\n(11 − 7)/15 = {4/15}.\n(−5 − 8)/12 = {−13/12}.\n(7 − 23)/40 = {−16/40} = {−2/5}.\n(−8 + 4)/25 = {−4/25}.\n(22 − 15)/35 = {7/35} = {1/5}."}, {"kind": "blank", "p": "<b>Ex 1B · Q2(a–e)</b> · Simplify.", "tag": "", "marks": "", "flat": [{"t": "a) {−7/11} + {1/6} = __B1__", "a": {"B1": "-31/66"}, "expr": "fl"}, {"t": "b) {−3/7} + {2/5} = __B1__", "a": {"B1": "-1/35"}, "expr": "fl"}, {"t": "c) {−7/9} + {2/7} = __B1__", "a": {"B1": "-31/63"}, "expr": "fl"}, {"t": "d) {3/4} + ({−2/5}) = __B1__", "a": {"B1": "7/20"}, "expr": "fl"}, {"t": "e) {3/5} + {1/6} = __B1__", "a": {"B1": "23/30"}, "expr": "fl"}], "sol": "LCM 66: {−42/66} + {11/66} = {−31/66}.\nLCM 35: {−15/35} + {14/35} = {−1/35}.\nLCM 63: {−49/63} + {18/63} = {−31/63}.\nLCM 20: {15/20} − {8/20} = {7/20}.\nLCM 30: {18/30} + {5/30} = {23/30}."}, {"kind": "blank", "p": "<b>Ex 1B · Q2(f–j)</b> · Simplify.", "tag": "", "marks": "", "flat": [{"t": "f) {−18/20} + {6/11} = __B1__", "a": {"B1": "-39/110"}, "expr": "fl"}, {"t": "g) {13/60} + ({−3/36}) = __B1__", "a": {"B1": "2/15"}, "expr": "fl"}, {"t": "h) {6/40} + {1/25} = __B1__", "a": {"B1": "19/100"}, "expr": "fl"}, {"t": "i) {16/18} + ({−16/27}) = __B1__", "a": {"B1": "8/27"}, "expr": "fl"}, {"t": "j) {−21/81} + {5/18} = __B1__", "a": {"B1": "1/54"}, "expr": "fl"}], "sol": "{−18/20} = {−9/10}; LCM 110: {−99/110} + {60/110} = {−39/110}.\n{−3/36} = {−1/12}; LCM 60: {13/60} − {5/60} = {8/60} = {2/15}.\n{3/20} + {1/25}; LCM 100: {15/100} + {4/100} = {19/100}.\n{8/9} − {16/27} = {24/27} − {16/27} = {8/27}.\n{−7/27} + {5/18}; LCM 54: {−14/54} + {15/54} = {1/54}."}, {"kind": "mcq", "text": "<b>Ex 1B · Q3</b> · Name the property used in each:  a) {3/7} + {4/9} = {4/9} + □   b) {6/13} + ({4/9} + {7/8}) = ({6/13} + {4/9}) + □   c) {−7/13} + {−2/9} = {−2/9} + □   d) {−4/11} + ({−2/9} + {−8/13}) = ({−4/11} + □) + {−8/13}   e) {−7/18} + □ = {−7/18}   f) {−7/26} + □ = 0", "opts": ["a) commutative  b) associative  c) commutative  d) associative  e) additive identity  f) additive inverse", "a) commutative  b) commutative  c) commutative  d) associative  e) additive identity  f) closure", "a) commutative  b) associative  c) associative  d) commutative  e) additive identity  f) additive inverse", "a) associative  b) commutative  c) commutative  d) associative  e) additive inverse  f) additive identity"], "correct": 0, "tag": "", "sol": "a), c): the order of the two numbers is changed (commutative). b), d): the grouping is changed (associative). e) adding 0 leaves the number unchanged (additive identity). f) a number plus its opposite is 0 (additive inverse)."}, {"kind": "blank", "p": "<b>Ex 1B · Q3</b> · Fill in the boxes (□).", "tag": "", "marks": "", "flat": [{"t": "a) {3/7} + {4/9} = {4/9} + □: □ = __B1__", "a": {"B1": "3/7"}, "expr": "fl"}, {"t": "b) {6/13} + ({4/9} + {7/8}) = ({6/13} + {4/9}) + □: □ = __B1__", "a": {"B1": "7/8"}, "expr": "fl"}, {"t": "c) {−7/13} + {−2/9} = {−2/9} + □: □ = __B1__", "a": {"B1": "-7/13"}, "expr": "fl"}, {"t": "d) {−4/11} + ({−2/9} + {−8/13}) = ({−4/11} + □) + {−8/13}: □ = __B1__", "a": {"B1": "-2/9"}, "expr": "fl"}, {"t": "e) {−7/18} + □ = {−7/18}: □ = __B1__", "a": {"B1": "0"}}, {"t": "f) {−7/26} + □ = 0: □ = __B1__", "a": {"B1": "7/26"}, "expr": "fl"}], "sol": "Commutative property: {3/7}.\nAssociative property: {7/8}.\nCommutative property: {−7/13}.\nAssociative property: {−2/9}.\nAdditive identity: 0.\nAdditive inverse of {−7/26}: {7/26}."}, {"kind": "mcq", "text": "<b>Ex 1B · Q4</b> · Show that ({−2/5} + {4/9}) + ({−3/4}) = {−2/5} + [{4/9} + ({−3/4})]. Both sides are equal to", "opts": ["{−11/36}", "{2/45}", "{127/180}", "{−127/180}"], "correct": 3, "tag": "", "sol": "LHS: {−2/5} + {4/9} = (−18 + 20)/45 = {2/45}; {2/45} − {3/4} = (8 − 135)/180 = {−127/180}. RHS: {4/9} − {3/4} = (16 − 27)/36 = {−11/36}; {−2/5} − {11/36} = (−72 − 55)/180 = {−127/180}. LHS = RHS."}, {"kind": "blank", "p": "<b>Ex 1B · Q5</b> · Verify that a + (b + c) = (a + b) + c by taking a = {−4/5}, b = {7/8} and c = {3/4}.", "tag": "", "marks": "", "flat": [{"t": "b + c = __B1__", "a": {"B1": "13/8"}, "expr": "fl"}, {"t": "a + (b + c) = __B1__", "a": {"B1": "33/40"}, "expr": "fl"}, {"t": "a + b = __B1__", "a": {"B1": "3/40"}, "expr": "fl"}, {"t": "(a + b) + c = __B1__", "a": {"B1": "33/40"}, "expr": "fl"}], "sol": "{7/8} + {6/8} = {13/8}.\n{−32/40} + {65/40} = {33/40}.\n{−32/40} + {35/40} = {3/40}.\n{3/40} + {30/40} = {33/40}. Both sides are {33/40}, so the associative property is verified."}, {"kind": "blank", "p": "<b>Ex 1B · Q6</b> · Add as fast as possible using the associative and commutative properties.", "tag": "", "marks": "", "flat": [{"t": "a) 76 + 598 + 224 = __B1__", "a": {"B1": "898"}}, {"t": "b) {7/38} + {17/20} + {31/38} = __B1__", "a": {"B1": "37/20"}, "expr": "fl"}, {"t": "c) 782 + 890 + 218 = __B1__", "a": {"B1": "1890"}}], "sol": "(76 + 224) + 598 = 300 + 598 = 898.\n({7/38} + {31/38}) + {17/20} = 1 + {17/20} = {37/20} = {1 17/20}.\n(782 + 218) + 890 = 1000 + 890 = 1890."}]}, {"id": "s4", "label": "1.4 Subtraction", "sub": "Subtracting rational numbers and the properties of subtraction", "slides": [{"kind": "mcq", "text": "<b>Example 16</b> · Find {8/9} − {5/9}.", "opts": ["{1/3}", "{−1/3}", "{13/9}", "{3/18}"], "correct": 0, "tag": "", "sol": "Add the additive inverse of {5/9}: {8/9} + ({−5/9}) = {3/9} = {1/3}."}, {"kind": "blank", "p": "<b>Example 17</b> · Subtract {−3/7} from {4/11}.", "tag": "", "marks": "", "flat": [{"t": "{4/11} − ({−3/7}) = {4/11} + __B1__", "a": {"B1": "3/7"}, "expr": "fl"}, {"t": "LCM of 11 and 7 = __B1__", "a": {"B1": "77"}}, {"t": "Answer = __B1__", "a": {"B1": "61/77"}, "expr": "fl"}], "sol": "Subtracting {−3/7} means adding its additive inverse {3/7}.\n11 and 7 are co-prime: 77.\n{28/77} + {33/77} = {61/77}."}, {"kind": "blank", "p": "<b>Example 18</b> · Find {3/11} − {7/8}.", "tag": "", "marks": "", "flat": [{"t": "LCM of 11 and 8 = __B1__", "a": {"B1": "88"}}, {"t": "{3/11} − {7/8} = __B1__", "a": {"B1": "-53/88"}, "expr": "fl"}], "sol": "11 × 8 = 88.\n{24/88} − {77/88} = {−53/88}. The answer is a rational number (closure)."}, {"kind": "mcq", "text": "<b>Example 19</b> · Find {4/9} − ({−2/8}).", "opts": ["{−7/36}", "{25/36}", "{7/36}", "{6/17}"], "correct": 1, "tag": "", "sol": "{4/9} + {2/8} = {32/72} + {18/72} = {50/72} = {25/36}."}, {"kind": "mcq", "text": "<b>Example 20</b> · Check if {3/4} − {1/4} = {1/4} − {3/4}.", "opts": ["Yes: both are {−1/2}", "No: {1/2} ≠ {−1/2}", "Yes: both are {1/2}", "No: {1/2} ≠ 0"], "correct": 1, "tag": "", "sol": "{3/4} − {1/4} = {2/4} = {1/2} and {1/4} − {3/4} = {−2/4} = {−1/2}. Since {1/2} ≠ {−1/2}, the two sides are not equal."}, {"kind": "blank", "p": "<b>Example 21</b> · Check if {7/18} − {10/27} = {10/27} − {7/18}.", "tag": "", "marks": "", "flat": [{"t": "{7/18} − {10/27} = __B1__", "a": {"B1": "1/54"}, "expr": "fl"}, {"t": "{10/27} − {7/18} = __B1__", "a": {"B1": "-1/54"}, "expr": "fl"}, {"t": "Is subtraction of rational numbers commutative? __B1__ (yes / no)", "a": {"B1": "no"}, "expr": "words", "accept": ["n"]}], "sol": "LCM 54: (21 − 20)/54 = {1/54}.\n(20 − 21)/54 = {−1/54}.\n{1/54} ≠ {−1/54}, so subtraction is not commutative."}, {"kind": "blank", "p": "<b>Example 22</b> · Check if ({3/8} − {2/4}) − {1/16} = {3/8} − ({2/4} − {1/16}).", "tag": "", "marks": "", "flat": [{"t": "LHS = __B1__", "a": {"B1": "-3/16"}, "expr": "fl"}, {"t": "RHS = __B1__", "a": {"B1": "-1/16"}, "expr": "fl"}], "sol": "(3 − 4)/8 − {1/16} = {−1/8} − {1/16} = (−2 − 1)/16 = {−3/16}.\n{3/8} − (8 − 1)/16 = {3/8} − {7/16} = (6 − 7)/16 = {−1/16}. LHS ≠ RHS."}, {"kind": "mcq", "text": "<b>Example 23</b> · Check if ({5/8} − {2/7}) − {1/4} = {5/8} − ({2/7} − {1/4}).", "opts": ["Yes: both sides are {5/56}", "No: LHS = {33/56}, RHS = {5/56}", "No: LHS = {5/56}, RHS = {33/56}", "Yes: both sides are {33/56}"], "correct": 2, "tag": "", "sol": "LHS = (35 − 16)/56 − {1/4} = {19/56} − {14/56} = {5/56}. RHS = {5/8} − (8 − 7)/28 = {5/8} − {1/28} = (35 − 2)/56 = {33/56}. So subtraction is not associative."}, {"kind": "blank", "p": "<b>Ex 1C · Q1(a–e)</b> · Subtract the following (answers in lowest terms).", "tag": "", "marks": "", "flat": [{"t": "a) {9/20} − {3/20} = __B1__", "a": {"B1": "3/10"}, "expr": "fl"}, {"t": "b) {−40/111} − ({−60/111}) = __B1__", "a": {"B1": "20/111"}, "expr": "fl"}, {"t": "c) −{14/31} − {15/31} = __B1__", "a": {"B1": "-29/31"}, "expr": "fl"}, {"t": "d) +{70/89} − ({−19/89}) = __B1__", "a": {"B1": "1"}, "expr": "fl"}, {"t": "e) −{47/90} − {30/90} = __B1__", "a": {"B1": "-77/90"}, "expr": "fl"}], "sol": "{6/20} = {3/10}.\n(−40 + 60)/111 = {20/111}.\n(−14 − 15)/31 = {−29/31}.\n(70 + 19)/89 = {89/89} = 1.\n(−47 − 30)/90 = {−77/90}."}, {"kind": "blank", "p": "<b>Ex 1C · Q1(f–j)</b> · Subtract the following (answers in lowest terms).", "tag": "", "marks": "", "flat": [{"t": "f) {5/18} − {2/3} = __B1__", "a": {"B1": "-7/18"}, "expr": "fl"}, {"t": "g) −{16/25} − (−{1/5}) = __B1__", "a": {"B1": "-11/25"}, "expr": "fl"}, {"t": "h) −{7/60} − {3/20} = __B1__", "a": {"B1": "-4/15"}, "expr": "fl"}, {"t": "i) −{4/7} − {1/4} = __B1__", "a": {"B1": "-23/28"}, "expr": "fl"}, {"t": "j) {12/25} − (−{7/35}) = __B1__", "a": {"B1": "17/25"}, "expr": "fl"}], "sol": "{5/18} − {12/18} = {−7/18}.\n{−16/25} + {5/25} = {−11/25}.\n{−7/60} − {9/60} = {−16/60} = {−4/15}.\n{−16/28} − {7/28} = {−23/28}.\n{7/35} = {1/5}; {12/25} + {5/25} = {17/25}."}, {"kind": "mcq", "text": "<b>Ex 1C · Q2(a–c)</b> · State whether the statements are true or false.  a) {3/8} − {2/7} = {2/7} − {3/8}   b) ({2/7} − {4/9}) − {1/8} = {2/7} − ({4/9} − {1/8})   c) {3/8} + 0 = {3/8}", "opts": ["a) True  b) False  c) True", "a) True  b) True  c) True", "a) False  b) True  c) True", "a) False  b) False  c) True"], "correct": 3, "tag": "", "sol": "a) {5/56} ≠ {−5/56}: subtraction is not commutative. b) LHS = {−10/63} − {1/8} = {−143/504}, RHS = {2/7} − {23/72} = {−17/504}: not associative. c) 0 is the additive identity: true."}, {"kind": "mcq", "text": "<b>Ex 1C · Q2(d–f)</b> · State whether the statements are true or false.  d) {7/9} − ({−7/9}) = 0   e) {6/7} + ({−6/7}) = 0   f) {4/9} − 0 = 0", "opts": ["d) True  e) True  f) False", "d) False  e) False  f) False", "d) True  e) True  f) True", "d) False  e) True  f) False"], "correct": 3, "tag": "", "sol": "d) {7/9} + {7/9} = {14/9}, not 0: false. e) a number plus its additive inverse is 0: true. f) {4/9} − 0 = {4/9}, not 0: false."}, {"kind": "blank", "p": "<b>Ex 1C · Q3</b> · Solve the following.", "tag": "", "marks": "", "flat": [{"t": "a) {−6/9} − ({−2/7}) = __B1__", "a": {"B1": "-8/21"}, "expr": "fl"}, {"t": "b) {7/24} − {11/16} = __B1__", "a": {"B1": "-19/48"}, "expr": "fl"}, {"t": "c) {10/63} − ({−6/7}) = __B1__", "a": {"B1": "64/63"}, "expr": "fl"}, {"t": "d) −{11/13} − ({−5/26}) = __B1__", "a": {"B1": "-17/26"}, "expr": "fl"}], "sol": "{−2/3} + {2/7} = (−14 + 6)/21 = {−8/21}.\nLCM 48: {14/48} − {33/48} = {−19/48}.\n{10/63} + {54/63} = {64/63}.\n{−22/26} + {5/26} = {−17/26}."}, {"kind": "blank", "p": "<b>Ex 1C · Q4</b> · Simplify.", "tag": "", "marks": "", "flat": [{"t": "a) {3/7} + {5/9} − ({−2/3}) = __B1__", "a": {"B1": "104/63"}, "expr": "fl"}, {"t": "b) {−4/11} + {−2/3} − ({−5/9}) = __B1__", "a": {"B1": "-47/99"}, "expr": "fl"}, {"t": "c) −{1/6} + ({−2/3}) − {1/3} = __B1__", "a": {"B1": "-7/6"}, "expr": "fl"}], "sol": "LCM 63: {27/63} + {35/63} + {42/63} = {104/63} = {1 41/63}.\nLCM 99: {−36/99} − {66/99} + {55/99} = {−47/99}.\n{−1/6} − {4/6} − {2/6} = {−7/6}."}]}, {"id": "s5", "label": "1.5 Multiplication", "sub": "Multiplying rational numbers and the properties of multiplication", "slides": [{"kind": "blank", "p": "<b>Example 24</b> · Multiply the following.", "tag": "", "marks": "", "flat": [{"t": "a) 3 × 7 = __B1__", "a": {"B1": "21"}}, {"t": "b) −3 × 8 = __B1__", "a": {"B1": "-24"}}, {"t": "c) {1/3} × {1/4} = __B1__", "a": {"B1": "1/12"}, "expr": "fl"}, {"t": "d) {−3/8} × 4 = __B1__", "a": {"B1": "-3/2"}, "expr": "fl"}, {"t": "e) {−7/8} × {3/4} = __B1__", "a": {"B1": "-21/32"}, "expr": "fl"}, {"t": "f) {−4/9} × {−3/4} = __B1__", "a": {"B1": "1/3"}, "expr": "fl"}], "sol": "{3/1} × {7/1} = {21/1} = 21.\n(−3 × 8)/(1 × 1) = −24.\n(1 × 1)/(3 × 4) = {1/12}.\n(−3 × 4)/(8 × 1) = {−12/8} = {−3/2}.\n(−7 × 3)/(8 × 4) = {−21/32}.\n((−4) × (−3))/(9 × 4) = {12/36} = {1/3}."}, {"kind": "mcq", "text": "<b>Example 25</b> · Simplify: {45/84} × {21/27}", "opts": ["{7/12}", "{5/12}", "{15/28}", "{5/4}"], "correct": 1, "tag": "", "sol": "45 and 27 have the common factor 9: {5/84} × {21/3}. 21 and 84 have the common factor 21: {5/4} × {1/3} = {5/12}."}, {"kind": "blank", "p": "<b>Try This</b> · Multiply.", "tag": "", "marks": "", "flat": [{"t": "a) {−2/5} × {−4/7} = __B1__", "a": {"B1": "8/35"}, "expr": "fl"}, {"t": "b) {−56/45} × {36/−64} = __B1__", "a": {"B1": "7/10"}, "expr": "fl"}], "sol": "((−2) × (−4))/(5 × 7) = {8/35}.\nBoth factors are negative, so the product is positive. Cancel 56 with 64 (by 8) and 36 with 45 (by 9): {7/5} × {4/8} = {28/40} = {7/10}."}, {"kind": "mcq", "text": "<b>Example 26</b> · Multiply: {−3/7} × {5/8}", "opts": ["{−8/15}", "{15/56}", "{−15/56}", "{2/56}"], "correct": 2, "tag": "", "sol": "(−3 × 5)/(7 × 8) = {−15/56}, which is again a rational number: rational numbers are closed under multiplication."}, {"kind": "blank", "p": "<b>Example 27</b> · Compare {7/9} × {3/8} and {3/8} × {7/9}.", "tag": "", "marks": "", "flat": [{"t": "{7/9} × {3/8} = __B1__", "a": {"B1": "7/24"}, "expr": "fl"}, {"t": "{3/8} × {7/9} = __B1__", "a": {"B1": "7/24"}, "expr": "fl"}, {"t": "This shows the __B1__ property of multiplication.", "a": {"B1": "commutative"}, "expr": "words"}], "sol": "{21/72} = {7/24}.\n{21/72} = {7/24}.\nChanging the order does not change the product: commutative property."}, {"kind": "mcq", "text": "<b>Example 28</b> · Check if ({3/7} × {4/9}) × {7/12} = {3/7} × ({4/9} × {7/12}).", "opts": ["No: LHS = {1/9}, RHS = {1/3}", "No: LHS = {12/63}, RHS = {28/108}", "Yes: both sides are {1/9}", "Yes: both sides are {1/3}"], "correct": 2, "tag": "", "sol": "LHS = {12/63} × {7/12} = {84/756} = {1/9}. RHS = {3/7} × {28/108} = {84/756} = {1/9}. The associative property holds."}, {"kind": "blank", "p": "<b>Example 29</b> · Check if [({−2/5}) × {3/4}] × ({−1/2}) = ({−2/5}) × [{3/4} × ({−1/2})].", "tag": "", "marks": "", "flat": [{"t": "LHS = __B1__", "a": {"B1": "3/20"}, "expr": "fl"}, {"t": "RHS = __B1__", "a": {"B1": "3/20"}, "expr": "fl"}], "sol": "{−6/20} × {−1/2} = {6/40} = {3/20}.\n{−2/5} × {−3/8} = {6/40} = {3/20}. LHS = RHS: multiplication is associative."}, {"kind": "blank", "p": "<b>Try This</b> · Find the multiplicative inverse of:", "tag": "", "marks": "", "flat": [{"t": "a) {−7/13}: __B1__", "a": {"B1": "-13/7"}, "expr": "fl"}], "sol": "{−7/13} × {−13/7} = 1, so the reciprocal is {−13/7}."}, {"kind": "mcq", "text": "<b>Try This</b> · Find the multiplicative inverse of: b) {0/2}", "opts": ["It does not exist", "2", "0", "{2/0}"], "correct": 0, "tag": "", "sol": "{0/2} = 0, and 0 × any number = 0 ≠ 1. So 0 has no multiplicative inverse ({2/0} is not defined)."}, {"kind": "mcq", "text": "<b>Example 30</b> · Check that 3 × (4 + 5) = 3 × 4 + 3 × 5. Each side equals", "opts": ["32", "12", "17", "27"], "correct": 3, "tag": "", "sol": "LHS = 3 × 9 = 27; RHS = 12 + 15 = 27. Multiplication is distributed over addition."}, {"kind": "blank", "p": "<b>Example 31</b> · Is {4/7}({2/3} + {3/4}) = {4/7} × {2/3} + {4/7} × {3/4}?", "tag": "", "marks": "", "flat": [{"t": "LHS = __B1__", "a": {"B1": "17/21"}, "expr": "fv"}, {"t": "RHS = __B1__", "a": {"B1": "17/21"}, "expr": "fv"}, {"t": "Are they equal? __B1__ (yes / no)", "a": {"B1": "yes"}, "expr": "words", "accept": ["y"]}], "sol": "{4/7} × (8 + 9)/12 = {4/7} × {17/12} = {68/84} (= {17/21}).\n{8/21} + {12/28} = (32 + 36)/84 = {68/84}.\nYes: multiplication by {4/7} is distributed over addition."}, {"kind": "mcq", "text": "<b>Example 32</b> · Check if {−3/5}({3/4} + {−8/9}) = {−3/5} × {3/4} + {−3/5} × {−8/9}. Both sides equal", "opts": ["{−1/12}", "{3/20}", "{1/12}", "{15/36}"], "correct": 2, "tag": "", "sol": "LHS = {−3/5} × (27 − 32)/36 = {−3/5} × {−5/36} = {15/180}. RHS = {−9/20} + {24/45} = (−81 + 96)/180 = {15/180}. Both = {1/12}."}, {"kind": "blank", "p": "<b>Ex 1D · Q1</b> · Multiply (answers in lowest terms).", "tag": "", "marks": "", "flat": [{"t": "a) {4/15} × {3/8} = __B1__", "a": {"B1": "1/10"}, "expr": "fl"}, {"t": "b) {4/11} × (−{2/9}) = __B1__", "a": {"B1": "-8/99"}, "expr": "fl"}, {"t": "c) −{5/7} × {14/15} = __B1__", "a": {"B1": "-2/3"}, "expr": "fl"}, {"t": "d) {−16/25} × {5/8} = __B1__", "a": {"B1": "-2/5"}, "expr": "fl"}, {"t": "e) {13/40} × ({−25/39}) = __B1__", "a": {"B1": "-5/24"}, "expr": "fl"}, {"t": "f) {81/100} × {25/27} = __B1__", "a": {"B1": "3/4"}, "expr": "fl"}], "sol": "{12/120} = {1/10}.\n{−8/99}.\nCancel 7 and 14, 5 and 15: (−1 × 2)/(1 × 3) = {−2/3}.\nCancel 16 and 8, 5 and 25: {−2/5}.\nCancel 13 and 39, 25 and 40: {−5/24}.\nCancel 81 and 27, 25 and 100: {3/4}."}, {"kind": "blank", "p": "<b>Ex 1D · Q2</b> · Simplify.", "tag": "", "marks": "", "flat": [{"t": "a) (−{8/5} × {3/4}) + ({7/8} × {−16/25}) = __B1__", "a": {"B1": "-44/25"}, "expr": "fl"}, {"t": "b) ({7/25} × {−15/18}) + (−{3/5} × {4/9}) = __B1__", "a": {"B1": "-1/2"}, "expr": "fl"}, {"t": "c) (−{3/4} × {8/15}) − ({2/3} × {−3/8}) − (−{4/7} × {−14/15}) = __B1__", "a": {"B1": "-41/60"}, "expr": "fl"}], "sol": "{−6/5} + {−14/25} = {−30/25} − {14/25} = {−44/25}.\n{−7/30} + {−4/15} = {−7/30} − {8/30} = {−15/30} = {−1/2}.\n{−2/5} − ({−1/4}) − {8/15} = {−24/60} + {15/60} − {32/60} = {−41/60}."}, {"kind": "mcq", "text": "<b>Ex 1D · Q3(a)</b> · Show that (−{5/8} × {4/15}) × {−3/4} = {−5/8} × ({4/15} × {−3/4}). Both sides equal", "opts": ["{1/6}", "{1/8}", "{−1/5}", "{−1/8}"], "correct": 1, "tag": "", "sol": "LHS = {−20/120} × {−3/4} = {−1/6} × {−3/4} = {3/24} = {1/8}. RHS = {−5/8} × {−12/60} = {−5/8} × {−1/5} = {5/40} = {1/8}."}, {"kind": "blank", "p": "<b>Ex 1D · Q3(b)</b> · Show that {−2/3}({4/5} + {−8/15}) = ({−2/3} × {4/5}) + ({−2/3} × {−8/15}).", "tag": "", "marks": "", "flat": [{"t": "LHS = __B1__", "a": {"B1": "-8/45"}, "expr": "fl"}, {"t": "RHS = __B1__", "a": {"B1": "-8/45"}, "expr": "fl"}], "sol": "{4/5} + {−8/15} = (12 − 8)/15 = {4/15}; {−2/3} × {4/15} = {−8/45}.\n{−8/15} + {16/45} = (−24 + 16)/45 = {−8/45}. LHS = RHS."}, {"kind": "blank", "p": "<b>Ex 1D · Q4</b> · Verify a × (b × c) = (a × b) × c by taking a = −{4/7}, b = {14/15} and c = −{3/4}.", "tag": "", "marks": "", "flat": [{"t": "b × c = __B1__", "a": {"B1": "-7/10"}, "expr": "fl"}, {"t": "a × (b × c) = __B1__", "a": {"B1": "2/5"}, "expr": "fl"}, {"t": "a × b = __B1__", "a": {"B1": "-8/15"}, "expr": "fl"}, {"t": "(a × b) × c = __B1__", "a": {"B1": "2/5"}, "expr": "fl"}], "sol": "{−42/60} = {−7/10}.\n{28/70} = {2/5}.\n{−56/105} = {−8/15}.\n{24/60} = {2/5}. Both sides are {2/5}: verified."}, {"kind": "mcq", "text": "<b>Ex 1D · Q5</b> · State the properties illustrated:  a) {−2/3} × ({3/7} × {−5/8}) = ({−2/3} × {3/7}) × {−5/8}   b) {−4/7} × {−5/8} = {−5/8} × {−4/7}   c) {−4/5} × ({2/3} + {−4/9}) = ({−4/5} × {2/3}) + ({−4/5} × {−4/9})", "opts": ["a) associative  b) commutative  c) closure", "a) commutative  b) associative  c) distributive property of multiplication over addition", "a) associative  b) commutative  c) distributive property of multiplication over addition", "a) distributive  b) commutative  c) associative"], "correct": 2, "tag": "", "sol": "a) The grouping changes: associative property of multiplication. b) The order changes: commutative property. c) Multiplication is spread over the sum: distributive property."}, {"kind": "blank", "p": "<b>Ex 1D · Q6</b> · Simplify using the distributive property of multiplication over addition.", "tag": "", "marks": "", "flat": [{"t": "a) {7/20} × {6/17} + {11/17} × {7/20} = __B1__", "a": {"B1": "7/20"}, "expr": "fl"}, {"t": "b) {3/4} × {18/31} + {3/4} × {13/31} = __B1__", "a": {"B1": "3/4"}, "expr": "fl"}, {"t": "c) 273 × 43 + 273 × 57 = __B1__", "a": {"B1": "27300"}}], "sol": "{7/20} × ({6/17} + {11/17}) = {7/20} × 1 = {7/20}.\n{3/4} × ({18/31} + {13/31}) = {3/4} × 1 = {3/4}.\n273 × (43 + 57) = 273 × 100 = 27300."}]}, {"id": "s6", "label": "1.6 Division & real life", "sub": "Dividing rational numbers, properties of division and real-life problems", "slides": [{"kind": "mcq", "text": "<b>Example 33</b> · We know that 6 ÷ 2 = 3. Dividing by 2 is the same as multiplying by", "opts": ["{1/2}", "2", "{−1/2}", "−2"], "correct": 0, "tag": "", "sol": "6 ÷ 2 = 6 × {1/2} = {6/2} = 3: multiply by the reciprocal of 2."}, {"kind": "blank", "p": "<b>Example 34</b> · 49 ÷ (−7) = −7 because (−7) × (−7) = 49. Write it as a multiplication.", "tag": "", "marks": "", "flat": [{"t": "Multiplicative inverse of −7 = __B1__", "a": {"B1": "-1/7"}, "expr": "fl"}, {"t": "49 × ({−1/7}) = __B1__", "a": {"B1": "-7"}}], "sol": "−7 × ({−1/7}) = 1, so the inverse is {−1/7}.\n49 × ({−1/7}) = {49/−7} = −7."}, {"kind": "mcq", "text": "<b>Example 35</b> · How many halves are there in 6? That is, 6 ÷ {1/2} =", "opts": ["3", "{6 1/2}", "{1/3}", "12"], "correct": 3, "tag": "", "sol": "1 has 2 halves, so 6 has 12 halves: 6 ÷ {1/2} = 6 × 2 = 12."}, {"kind": "blank", "p": "<b>Example 36</b> · Divide: {7/2} ÷ {5/9}.", "tag": "", "marks": "", "flat": [{"t": "Reciprocal of {5/9} = __B1__", "a": {"B1": "9/5"}, "expr": "fl"}, {"t": "{7/2} ÷ {5/9} = __B1__", "a": {"B1": "63/10"}, "expr": "fl"}], "sol": "Flip {5/9}: {9/5}.\n{7/2} × {9/5} = {63/10} = {6 3/10}."}, {"kind": "mcq", "text": "<b>Example 37</b> · Divide: {3/8} ÷ {−4/9}", "opts": ["{−27/32}", "{−1/6}", "{−32/27}", "{27/32}"], "correct": 0, "tag": "", "sol": "Reciprocal of {−4/9} is {−9/4}. {3/8} × {−9/4} = {−27/32}."}, {"kind": "blank", "p": "<b>Example 38</b> · Divide: {3/7} ÷ {2/3}.", "tag": "", "marks": "", "flat": [{"t": "{3/7} ÷ {2/3} = __B1__", "a": {"B1": "9/14"}, "expr": "fl"}], "sol": "{3/7} × {3/2} = {9/14}, a rational number. But {a/b} ÷ 0 is not defined, so rational numbers are not closed under division."}, {"kind": "blank", "p": "<b>Example 39</b> · Check if {1/4} ÷ {1/2} = {1/2} ÷ {1/4}.", "tag": "", "marks": "", "flat": [{"t": "LHS = __B1__", "a": {"B1": "1/2"}, "expr": "fl"}, {"t": "RHS = __B1__", "a": {"B1": "2"}}], "sol": "{1/4} × {2/1} = {2/4} = {1/2}.\n{1/2} × {4/1} = {4/2} = 2. LHS ≠ RHS, so division is not commutative."}, {"kind": "mcq", "text": "<b>Example 40</b> · Check if ({3/4} ÷ {1/2}) ÷ {1/8} = {3/4} ÷ ({1/2} ÷ {1/8}).", "opts": ["No: LHS = 12, RHS = {3/16}", "Yes: both sides are {3/16}", "Yes: both sides are 12", "No: LHS = {3/16}, RHS = 12"], "correct": 0, "tag": "", "sol": "LHS = ({3/4} × 2) ÷ {1/8} = {6/4} × 8 = 12. RHS = {3/4} ÷ ({1/2} × 8) = {3/4} ÷ 4 = {3/16}. So division is not associative."}, {"kind": "blank", "p": "<b>Ex 1E · Q1(a–e)</b> · Divide (answers in lowest terms).", "tag": "", "marks": "", "flat": [{"t": "a) {12/19} ÷ {2/3} = __B1__", "a": {"B1": "18/19"}, "expr": "fl"}, {"t": "b) {7/8} ÷ {1/2} = __B1__", "a": {"B1": "7/4"}, "expr": "fl"}, {"t": "c) {6/13} ÷ {−3/2} = __B1__", "a": {"B1": "-4/13"}, "expr": "fl"}, {"t": "d) {18/34} ÷ {−9/40} = __B1__", "a": {"B1": "-40/17"}, "expr": "fl"}, {"t": "e) {−6/11} ÷ {−18/44} = __B1__", "a": {"B1": "4/3"}, "expr": "fl"}], "sol": "{12/19} × {3/2} = {36/38} = {18/19}.\n{7/8} × 2 = {7/4}.\n{6/13} × {−2/3} = {−12/39} = {−4/13}.\n{18/34} × {−40/9} = {−720/306} = {−40/17}.\n{−6/11} × {−44/18} = {264/198} = {4/3}."}, {"kind": "blank", "p": "<b>Ex 1E · Q1(f–j)</b> · Divide (answers in lowest terms).", "tag": "", "marks": "", "flat": [{"t": "f) {4/9} ÷ {2/3} = __B1__", "a": {"B1": "2/3"}, "expr": "fl"}, {"t": "g) {18/25} ÷ ({−9/35}) = __B1__", "a": {"B1": "-14/5"}, "expr": "fl"}, {"t": "h) {11/10} ÷ ({−11/2}) = __B1__", "a": {"B1": "-1/5"}, "expr": "fl"}, {"t": "i) −{5/2} ÷ {1/4} = __B1__", "a": {"B1": "-10"}, "expr": "fl"}, {"t": "j) {1 7/9} ÷ {1 1/3} = __B1__", "a": {"B1": "4/3"}, "expr": "fl"}], "sol": "{4/9} × {3/2} = {12/18} = {2/3}.\n{18/25} × {−35/9} = {−630/225} = {−14/5}.\n{11/10} × {−2/11} = {−2/10} = {−1/5}.\n{−5/2} × 4 = −10.\n{16/9} ÷ {4/3} = {16/9} × {3/4} = {48/36} = {4/3}."}, {"kind": "blank", "p": "<b>Ex 1E · Q2</b> · Simplify (work from left to right).", "tag": "", "marks": "", "flat": [{"t": "a) −4 ÷ ({−2/5}) × {3/4} = __B1__", "a": {"B1": "15/2"}, "expr": "fl"}, {"t": "b) {8/15} ÷ {4/5} × {2/3} = __B1__", "a": {"B1": "4/9"}, "expr": "fl"}], "sol": "−4 × {−5/2} = 10; 10 × {3/4} = {30/4} = {15/2}.\n{8/15} × {5/4} = {40/60} = {2/3}; {2/3} × {2/3} = {4/9}."}, {"kind": "mcq", "text": "<b>Example 41</b> · The length and breadth of a hall are {21 3/4} m and {11 1/4} m. How many square tiles of side {3/4} m are required to pave the floor?", "opts": ["3915", "580", "348", "435"], "correct": 3, "tag": "", "sol": "Area of hall = {87/4} × {45/4} = {3915/16} m². Area of one tile = {3/4} × {3/4} = {9/16} m². Number of tiles = {3915/16} ÷ {9/16} = {3915/16} × {16/9} = 435."}, {"kind": "blank", "p": "<b>Example 42</b> · Mariam invested ₹{7 1/2} lakhs in a business. After one year her profit was {−2/15} of the investment. How much money is left in her business?", "tag": "", "marks": "", "flat": [{"t": "Investment = ₹__B1__", "a": {"B1": "750000"}}, {"t": "Loss = ₹__B1__", "a": {"B1": "100000"}}, {"t": "Money left = ₹__B1__", "a": {"B1": "650000"}}], "sol": "₹{7 1/2} lakhs = ₹7,50,000.\nA profit of {−2/15} is a loss of {2/15}: ₹7,50,000 × {2/15} = ₹1,00,000.\n₹7,50,000 − ₹1,00,000 = ₹6,50,000."}, {"kind": "blank", "p": "<b>Ex 1F · Q1</b> · A gold chain packed in a gift box weighs {80 1/6} g. The chain weighs {26 7/12} g. What is the weight of the box?", "tag": "", "marks": "", "flat": [{"t": "Weight of the box = __B1__ g", "a": {"B1": "643/12"}, "expr": "fl"}], "sol": "{481/6} − {319/12} = {962/12} − {319/12} = {643/12} = {53 7/12} g."}, {"kind": "mcq", "text": "<b>Ex 1F · Q2</b> · A fruit basket containing apples, oranges and pears weighs {19 1/3} kg. There are {8 1/9} kg of pears and {3 1/9} kg of oranges, and the basket itself weighs {1 1/9} kg. How many kilograms of apples are there?", "opts": ["7 kg", "{8 1/9} kg", "{9 1/3} kg", "{6 8/9} kg"], "correct": 0, "tag": "", "sol": "Apples = {19 1/3} − ({8 1/9} + {3 1/9} + {1 1/9}) = {174/9} − {111/9} = {63/9} = 7 kg."}, {"kind": "blank", "p": "<b>Ex 1F · Q3</b> · A corridor is {66/7} m long and {56/55} m broad. What is the area of carpet needed to cover it fully?", "tag": "", "marks": "", "flat": [{"t": "Area = __B1__ m²", "a": {"B1": "48/5"}, "expr": "fl"}], "sol": "{66/7} × {56/55}: cancel 66 and 55 by 11, 56 and 7 by 7: (6 × 8)/(1 × 5) = {48/5} = {9 3/5} m²."}, {"kind": "mcq", "text": "<b>Ex 1F · Q4</b> · A roll of ribbon was cut into 26 pieces, each {2 3/4} m long. What was the length of the original roll?", "opts": ["{71 1/2} m", "{28 3/4} m", "{52 3/4} m", "{9 5/11} m"], "correct": 0, "tag": "", "sol": "26 × {11/4} = {286/4} = {143/2} = {71 1/2} m."}, {"kind": "blank", "p": "<b>Ex 1F · Q5</b> · Find the area of a square paper of side {25/2} cm.", "tag": "", "marks": "", "flat": [{"t": "Area = __B1__ cm²", "a": {"B1": "625/4"}, "expr": "fl"}], "sol": "{25/2} × {25/2} = {625/4} = {156 1/4} cm²."}, {"kind": "mcq", "text": "<b>Ex 1F · Q6</b> · A train moves at an average speed of {425/4} km/h. How far will it travel in {16/5} hours?", "opts": ["{425/16} km", "{2125/64} km", "340 km", "136 km"], "correct": 2, "tag": "", "sol": "Distance = speed × time = {425/4} × {16/5} = 85 × 4 = 340 km."}, {"kind": "blank", "p": "<b>Ex 1F · Q7</b> · In a school, {5/8} of the students are girls. The number of girls is 120 more than the number of boys. What is the strength of the school? How many boys are there?", "tag": "", "marks": "", "flat": [{"t": "Fraction of boys = __B1__", "a": {"B1": "3/8"}, "expr": "fl"}, {"t": "Strength of the school = __B1__", "a": {"B1": "480"}}, {"t": "Number of boys = __B1__", "a": {"B1": "180"}}], "sol": "1 − {5/8} = {3/8}.\nGirls − boys = {5/8} − {3/8} = {2/8} = {1/4} of the school = 120, so the strength is 120 × 4 = 480.\n{3/8} × 480 = 180 boys (and 300 girls)."}, {"kind": "blank", "p": "<b>Ex 1F · Q8</b> · The length and breadth of a garden are {45 1/2} m and {23 1/2} m. Find the length of barbed wire needed for a three-layer fence around it.", "tag": "", "marks": "", "flat": [{"t": "Perimeter = __B1__ m", "a": {"B1": "138"}}, {"t": "Barbed wire = __B1__ m", "a": {"B1": "414"}}], "sol": "2 × ({91/2} + {47/2}) = 2 × {138/2} = 138 m.\nThree layers: 3 × 138 = 414 m."}, {"kind": "mcq", "text": "<b>Ex 1F · Q9</b> · Rohan filled his car with 20 L of petrol and paid ₹2620. What is the cost of one litre of petrol?", "opts": ["₹121", "₹1310", "₹262", "₹131"], "correct": 3, "tag": "", "sol": "₹2620 ÷ 20 = ₹131."}]}, {"id": "s7", "label": "1.7 Density", "sub": "Rational numbers between two given rational numbers", "slides": [{"kind": "blank", "p": "<b>Example 43</b> · Find a rational number between {1/3} and {1/2} (Method 1: the average).", "tag": "", "marks": "", "flat": [{"t": "Sum = __B1__", "a": {"B1": "5/6"}, "expr": "fl"}, {"t": "Average = __B1__", "a": {"B1": "5/12"}, "expr": "fl"}], "sol": "(2 + 3)/6 = {5/6}.\n{5/6} ÷ 2 = {5/12}, so {1/3} < {5/12} < {1/2}."}, {"kind": "mcq", "text": "<b>Example 44</b> · Find a rational number between {7/8} and {8/9} by finding the average.", "opts": ["{63/64}", "{127/72}", "{127/144}", "{15/16}"], "correct": 2, "tag": "", "sol": "{1/2} × ({7/8} + {8/9}) = {1/2} × (63 + 64)/72 = {1/2} × {127/72} = {127/144}."}, {"kind": "blank", "p": "<b>Example 45</b> · Find five rational numbers between {3/4} and {5/6} (Method 2).", "tag": "", "marks": "", "flat": [{"t": "LCM 12: {3/4} = {x/12} and {5/6} = {y/12}: x = __B1__, y = __B2__", "a": {"B1": "9", "B2": "10"}}, {"t": "Multiply by 10: {3/4} = {x/120}, {5/6} = {y/120}: x = __B1__, y = __B2__", "a": {"B1": "90", "B2": "100"}}, {"t": "How many rational numbers with denominator 120 lie between them? __B1__", "a": {"B1": "9"}}], "sol": "{9/12} and {10/12}: no whole number between 9 and 10.\n{90/120} and {100/120}.\n{91/120}, {92/120}, …, {99/120}: 9 numbers. Take any five of them."}, {"kind": "mcq", "text": "<b>Example 46</b> · Find 20 rational numbers between 0.5 and 0.6. Written with denominator 1000, how many rational numbers lie between {500/1000} and {600/1000}?", "opts": ["20", "99", "100", "9"], "correct": 1, "tag": "", "sol": "0.5 = {5/10} = {50/100} = {500/1000} and 0.6 = {600/1000}. The numerators 501, 502, …, 599 give 99 rational numbers; take any 20 of them."}, {"kind": "blank", "p": "<b>Ex 1G · Q1</b> · Find a rational number between the two numbers using the average (mean) method.", "tag": "", "marks": "", "flat": [{"t": "a) −5 and −6: __B1__", "a": {"B1": "-11/2"}, "expr": "fl"}, {"t": "b) {−8/11} and {−7/11}: __B1__", "a": {"B1": "-15/22"}, "expr": "fl"}, {"t": "c) {−4/5} and {4/5}: __B1__", "a": {"B1": "0"}, "expr": "fl"}, {"t": "d) {5/14} and {9/14}: __B1__", "a": {"B1": "1/2"}, "expr": "fl"}], "sol": "(−5 − 6) ÷ 2 = {−11/2}.\n{−15/11} ÷ 2 = {−15/22}.\n({−4/5} + {4/5}) ÷ 2 = 0.\n{14/14} ÷ 2 = {1/2}."}, {"kind": "blank", "p": "<b>Ex 1G · Q2(a)</b> · Find three rational numbers between {1/8} and {1/12}.", "tag": "", "marks": "", "flat": [{"t": "With denominator 96: {1/12} = {x/96} and {1/8} = {y/96}: x = __B1__, y = __B2__", "a": {"B1": "8", "B2": "12"}}, {"t": "The three numerators in between, in increasing order: __B1__", "a": {"B1": "9, 10, 11"}, "expr": "dlist"}], "sol": "LCM 24 gives {2/24} and {3/24} (nothing between), so use 96: {8/96} and {12/96}.\n{9/96}, {10/96}, {11/96} (i.e. {3/32}, {5/48}, {11/96})."}, {"kind": "mcq", "text": "<b>Ex 1G · Q2(b)</b> · Find three rational numbers between {7/10} and {6/9}.", "opts": ["{2/3}, {17/25}, {7/10}", "{121/180}, {122/180}, {123/180}", "{3/5}, {5/8}, {13/20}", "{61/90}, {71/90}, {62/90}"], "correct": 1, "tag": "", "sol": "{6/9} = {2/3}. LCM 90: {60/90} and {63/90}; × 2: {120/180} and {126/180}. So {121/180}, {122/180}, {123/180} (also 124, 125) lie between. {71/90} is too big, and the endpoints themselves do not count."}, {"kind": "blank", "p": "<b>Ex 1G · Q2(c)</b> · Find three rational numbers between {2/13} and {3/11}.", "tag": "", "marks": "", "flat": [{"t": "LCM of 13 and 11 = __B1__", "a": {"B1": "143"}}, {"t": "{2/13} = {x/143} and {3/11} = {y/143}: x = __B1__, y = __B2__", "a": {"B1": "22", "B2": "39"}}, {"t": "How many rational numbers with denominator 143 lie strictly between them? __B1__", "a": {"B1": "16"}}], "sol": "13 × 11 = 143.\n2 × 11 = 22; 3 × 13 = 39.\n23, 24, …, 38: 16 numerators. Any three, e.g. {23/143}, {24/143}, {25/143}."}, {"kind": "mcq", "text": "<b>Ex 1G · Q2(d)</b> · Find three rational numbers between {7/10} and {9/11}.", "opts": ["{78/110}, {79/110}, {80/110}", "{7/11}, {8/11}, {9/10}", "{76/110}, {77/110}, {78/110}", "{91/110}, {92/110}, {93/110}"], "correct": 0, "tag": "", "sol": "LCM 110: {7/10} = {77/110} and {9/11} = {90/110}. Numerators 78 to 89 lie between; {78/110}, {79/110}, {80/110} work. {7/11} < {7/10} and {9/10} > {9/11}."}, {"kind": "blank", "p": "<b>Ex 1G · Q3(a)</b> · Find five rational numbers between {4/15} and {7/15}.", "tag": "", "marks": "", "flat": [{"t": "With denominator 30: {4/15} = {x/30} and {7/15} = {y/30}: x = __B1__, y = __B2__", "a": {"B1": "8", "B2": "14"}}, {"t": "Five numerators in between, in increasing order: __B1__", "a": {"B1": "9, 10, 11, 12, 13"}, "expr": "dlist"}], "sol": "Only {5/15} and {6/15} lie between with denominator 15, so multiply by 2: {8/30} and {14/30}.\n{9/30}, {10/30}, {11/30}, {12/30}, {13/30}."}, {"kind": "mcq", "text": "<b>Ex 1G · Q3(b)</b> · Find five rational numbers between {−16/21} and {18/25}. Which set works?", "opts": ["0, {1/2}, {3/4}, {4/5}, 1", "{−1/2}, 0, {1/5}, {1/3}, {1/2}", "−1, {−1/2}, 0, {1/2}, 1", "{−4/5}, {−1/2}, 0, {1/3}, {1/2}"], "correct": 1, "tag": "", "sol": "{−16/21} ≈ −0.76 and {18/25} = 0.72. Every number in the set {−1/2}, 0, {1/5}, {1/3}, {1/2} lies between them. −1 and 1, {3/4} and {4/5}, and {−4/5} are outside. (With LCM 525: {−400/525} and {378/525}, so there are many more.)"}]}, {"id": "s8", "label": "Assessment A", "sub": "Knowing and understanding", "slides": [{"kind": "mcq", "text": "<b>Check-up · MCQ 1</b> · Which of the following is the additive inverse of −{5/6}?", "opts": ["−{6/5}", "{6/5}", "{5/6}", "0"], "correct": 2, "tag": "", "sol": "−{5/6} + {5/6} = 0, so the additive inverse is {5/6}."}, {"kind": "mcq", "text": "<b>Check-up · MCQ 2</b> · The multiplicative inverse of a negative rational number is", "opts": ["0", "a negative rational number", "1", "a positive rational number"], "correct": 1, "tag": "", "sol": "The product must be 1 (positive), so the inverse has the same sign: e.g. −{2/3} × −{3/2} = 1. It is negative."}, {"kind": "mcq", "text": "<b>Check-up · Q3</b> · Circle the rational numbers and cross the ones which are not rational (give reasons): a) {7/9}  b) {8/19}  c) {6/12}  d) {0/7}  e) {16/0}. Which one is NOT rational?", "opts": ["{8/19}", "{0/7}", "{6/12}", "{16/0}", "{7/9}"], "correct": 3, "tag": "", "sol": "{7/9}, {8/19}, {6/12} and {0/7} have non-zero denominators, so they are rational. {16/0} has denominator 0 and is not defined."}, {"kind": "blank", "p": "<b>Check-up · Q4</b> · Express the rational numbers in standard form.", "tag": "", "marks": "", "flat": [{"t": "a) {32/40} = __B1__", "a": {"B1": "4/5"}, "expr": "fl"}, {"t": "b) {−8/60} = __B1__", "a": {"B1": "-2/15"}, "expr": "fl"}, {"t": "c) {3/−4} = __B1__", "a": {"B1": "-3/4"}, "expr": "fl"}, {"t": "d) {−2/−8} = __B1__", "a": {"B1": "1/4"}, "expr": "fl"}], "sol": "HCF 8: {4/5}.\nHCF 4: {−2/15}.\nMultiply by −1: {−3/4}.\nMultiply by −1: {2/8} = {1/4}."}, {"kind": "mcq", "text": "<b>Check-up · Q6</b> · Fill in the boxes using > or <:  a) {−8/19} □ {−7/19}   b) {−13/20} □ {3/20}   c) {7/8} □ {−3/8}   d) {3/4} □ {−2/3}   e) {7/8} □ {6/7}", "opts": ["<, <, >, >, >", "<, <, >, >, <", ">, <, >, >, >", "<, >, >, <, >"], "correct": 0, "tag": "", "sol": "a) −8 < −7. b) −13 < 3. c) positive > negative. d) positive > negative. e) LCM 56: {49/56} > {48/56}."}, {"kind": "blank", "p": "<b>Check-up · Q7</b> · Solve.", "tag": "", "marks": "", "flat": [{"t": "a) {7/16} + {3/8} = __B1__", "a": {"B1": "13/16"}, "expr": "fl"}, {"t": "b) {8/15} + (−{3/25}) = __B1__", "a": {"B1": "31/75"}, "expr": "fl"}, {"t": "c) {5/4} − (−{3/7}) = __B1__", "a": {"B1": "47/28"}, "expr": "fl"}, {"t": "d) −3 ÷ {1/6} = __B1__", "a": {"B1": "-18"}}, {"t": "e) {2 1/3} ÷ ({−35/18}) = __B1__", "a": {"B1": "-6/5"}, "expr": "fl"}], "sol": "{7/16} + {6/16} = {13/16}.\nLCM 75: {40/75} − {9/75} = {31/75}.\n{35/28} + {12/28} = {47/28}.\n−3 × 6 = −18.\n{7/3} × {−18/35} = {−126/105} = {−6/5}."}, {"kind": "blank", "p": "<b>Check-up · Mental Maths 3</b> · Find the value of ({−9/11}) − ({−3/11}).", "tag": "", "marks": "", "flat": [{"t": "Answer = __B1__", "a": {"B1": "-6/11"}, "expr": "fl"}], "sol": "{−9/11} + {3/11} = {−6/11}."}]}, {"id": "s9", "label": "Assessment B", "sub": "Investigating patterns", "slides": [{"kind": "blank", "p": "<b>Check-up · Q5</b> · Plot {1/10}, {3/10}, {−6/10}, {18/10} and {−12/10} on the number line (each unit is divided into 10 parts). Type the letter of the point for each number.", "tag": "", "marks": "", "flat": [{"t": "{1/10} → __B1__, {3/10} → __B2__, {−6/10} → __B3__, {18/10} → __B4__, {−12/10} → __B5__", "a": {"B1": "R", "B2": "S", "B3": "Q", "B4": "T", "B5": "P"}}], "sol": "Count tenths from 0: {−12/10} is 12 parts left (P), {−6/10} 6 parts left (Q), {1/10} 1 part right (R), {3/10} 3 parts right (S), {18/10} 18 parts right (T).", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 330 76\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><line class=\"ln\" x1=\"14.0\" y1=\"30.0\" x2=\"316.0\" y2=\"30.0\" marker-end=\"url(#ah)\" marker-start=\"url(#ahs)\"/><line x1=\"22.0\" y1=\"21\" x2=\"22.0\" y2=\"39\" style=\"stroke:var(--ink);stroke-width:1.6\"/><text class=\"lb\" x=\"22.0\" y=\"50.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−2</text><line x1=\"29.2\" y1=\"25\" x2=\"29.2\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"36.3\" y1=\"25\" x2=\"36.3\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"43.5\" y1=\"25\" x2=\"43.5\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"50.6\" y1=\"25\" x2=\"50.6\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"57.8\" y1=\"25\" x2=\"57.8\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"64.9\" y1=\"25\" x2=\"64.9\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"72.0\" y1=\"25\" x2=\"72.0\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"79.2\" y1=\"25\" x2=\"79.2\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"86.3\" y1=\"25\" x2=\"86.3\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"93.5\" y1=\"21\" x2=\"93.5\" y2=\"39\" style=\"stroke:var(--ink);stroke-width:1.6\"/><text class=\"lb\" x=\"93.5\" y=\"50.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−1</text><line x1=\"100.7\" y1=\"25\" x2=\"100.7\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"107.8\" y1=\"25\" x2=\"107.8\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"115.0\" y1=\"25\" x2=\"115.0\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"122.1\" y1=\"25\" x2=\"122.1\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"129.2\" y1=\"25\" x2=\"129.2\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"136.4\" y1=\"25\" x2=\"136.4\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"143.6\" y1=\"25\" x2=\"143.6\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"150.7\" y1=\"25\" x2=\"150.7\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"157.8\" y1=\"25\" x2=\"157.8\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"165.0\" y1=\"21\" x2=\"165.0\" y2=\"39\" style=\"stroke:var(--ink);stroke-width:1.6\"/><text class=\"lb\" x=\"165.0\" y=\"50.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">0</text><line x1=\"172.2\" y1=\"25\" x2=\"172.2\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"179.3\" y1=\"25\" x2=\"179.3\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"186.4\" y1=\"25\" x2=\"186.4\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"193.6\" y1=\"25\" x2=\"193.6\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"200.8\" y1=\"25\" x2=\"200.8\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"207.9\" y1=\"25\" x2=\"207.9\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"215.1\" y1=\"25\" x2=\"215.1\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"222.2\" y1=\"25\" x2=\"222.2\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"229.3\" y1=\"25\" x2=\"229.3\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"236.5\" y1=\"21\" x2=\"236.5\" y2=\"39\" style=\"stroke:var(--ink);stroke-width:1.6\"/><text class=\"lb\" x=\"236.5\" y=\"50.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">1</text><line x1=\"243.7\" y1=\"25\" x2=\"243.7\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"250.8\" y1=\"25\" x2=\"250.8\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"257.9\" y1=\"25\" x2=\"257.9\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"265.1\" y1=\"25\" x2=\"265.1\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"272.2\" y1=\"25\" x2=\"272.2\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"279.4\" y1=\"25\" x2=\"279.4\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"286.6\" y1=\"25\" x2=\"286.6\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"293.7\" y1=\"25\" x2=\"293.7\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"300.8\" y1=\"25\" x2=\"300.8\" y2=\"35\" style=\"stroke:var(--ink);stroke-width:1\"/><line x1=\"308.0\" y1=\"21\" x2=\"308.0\" y2=\"39\" style=\"stroke:var(--ink);stroke-width:1.6\"/><text class=\"lb\" x=\"308.0\" y=\"50.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2</text><circle cx=\"79.2\" cy=\"30\" r=\"5\" style=\"fill:var(--danger)\"/><text class=\"al\" x=\"79.2\" y=\"13.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">P</text><circle cx=\"122.1\" cy=\"30\" r=\"5\" style=\"fill:var(--danger)\"/><text class=\"al\" x=\"122.1\" y=\"13.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">Q</text><circle cx=\"172.2\" cy=\"30\" r=\"5\" style=\"fill:var(--danger)\"/><text class=\"al\" x=\"172.2\" y=\"13.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">R</text><circle cx=\"186.4\" cy=\"30\" r=\"5\" style=\"fill:var(--danger)\"/><text class=\"al\" x=\"186.4\" y=\"13.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">S</text><circle cx=\"293.7\" cy=\"30\" r=\"5\" style=\"fill:var(--danger)\"/><text class=\"al\" x=\"293.7\" y=\"13.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">T</text></svg>"}, {"kind": "blank", "p": "<b>Check-up · Mental Maths 1</b> · Find 872 + 479 + 228 + 121 by grouping cleverly.", "tag": "", "marks": "", "flat": [{"t": "(872 + 228) = __B1__", "a": {"B1": "1100"}}, {"t": "Total = __B1__", "a": {"B1": "1700"}}], "sol": "872 + 228 = 1100.\n479 + 121 = 600; 1100 + 600 = 1700."}, {"kind": "mcq", "text": "<b>Check-up · Mental Maths 2</b> · Solve: {7/8} × {22/35} + {13/35} × {7/8}", "opts": ["{7/35}", "{35/35}", "{7/8}", "{91/280}"], "correct": 2, "tag": "", "sol": "Distributive property: {7/8} × ({22/35} + {13/35}) = {7/8} × 1 = {7/8}."}, {"kind": "blank", "p": "<b>Check-up · Q9</b> · Simplify using an appropriate property: {3/20} × {2/3} + {3/20} × {1/3}.", "tag": "", "marks": "", "flat": [{"t": "{2/3} + {1/3} = __B1__", "a": {"B1": "1"}, "expr": "fl"}, {"t": "Answer = __B1__", "a": {"B1": "3/20"}, "expr": "fl"}], "sol": "The common factor is {3/20}: {3/20} × ({2/3} + {1/3}).\n{3/20} × 1 = {3/20} (distributive property)."}, {"kind": "mcq", "text": "<b>Check-up · Brain Teaser</b> · In a 3 × 3 magic square every row, column and diagonal has the same sum. The rows are: (a − b, a + b − c, a + c), (a + b + c, ?, a − b − c), (a − c, a − b + c, a + b). Can it be a magic square for any rational a, b, c? If yes, find ‘?’.", "opts": ["Yes, ? = b", "No, it can never be magic", "Yes, ? = a + b + c", "Yes, ? = a"], "correct": 3, "tag": "", "sol": "Row 1 sum = 3a. Row 2: (a + b + c) + ? + (a − b − c) = 2a + ? = 3a, so ? = a. Check: middle column (a + b − c) + a + (a − b + c) = 3a, diagonal (a − b) + a + (a + b) = 3a. So it is magic with ? = a."}, {"kind": "blank", "p": "Work out each product and look for a pattern.", "tag": "", "marks": "", "flat": [{"t": "{1/2} × {2/3} = __B1__", "a": {"B1": "1/3"}, "expr": "fl"}, {"t": "{1/2} × {2/3} × {3/4} = __B1__", "a": {"B1": "1/4"}, "expr": "fl"}, {"t": "{1/2} × {2/3} × {3/4} × {4/5} = __B1__", "a": {"B1": "1/5"}, "expr": "fl"}, {"t": "Continue up to × {99/100}: product = __B1__", "a": {"B1": "1/100"}, "expr": "fl"}], "sol": "{2/6} = {1/3}.\n{1/4}.\n{1/5}.\nEach numerator cancels the previous denominator, leaving {1/100}."}, {"kind": "blank", "p": "Differences of the form 1/n − 1/(n + 1).", "tag": "", "marks": "", "flat": [{"t": "{1/1} − {1/2} = __B1__", "a": {"B1": "1/2"}, "expr": "fl"}, {"t": "{1/2} − {1/3} = __B1__", "a": {"B1": "1/6"}, "expr": "fl"}, {"t": "{1/3} − {1/4} = __B1__", "a": {"B1": "1/12"}, "expr": "fl"}, {"t": "Rule: 1/n − 1/(n + 1) = 1/(__B1__)", "a": {"B1": "n(n+1)"}, "expr": true, "accept": ["n^2+n"]}], "sol": "{1/2}.\n{1/6}.\n{1/12}.\nThe denominators 2, 6, 12 are 1 × 2, 2 × 3, 3 × 4: n(n + 1)."}, {"kind": "mcq", "text": "Using the pattern above, 1/(1×2) + 1/(2×3) + … + 1/(9×10) equals", "opts": ["{10/11}", "{1/10}", "{9/10}", "1"], "correct": 2, "tag": "", "sol": "Each term is 1/n − 1/(n + 1); everything cancels except 1 − {1/10} = {9/10}."}]}, {"id": "s10", "label": "Assessment C", "sub": "Communicating", "slides": [{"kind": "mcq", "text": "<b>Check-up · Q8(a–d)</b> · State the properties involved:  a) {3/4} + {4/7} = {4/7} + {3/4}   b) {7/8} + ({3/4} + {1/9}) = ({7/8} + {3/4}) + {1/9}   c) {7/20} × {3/10} = {3/10} × {7/20}   d) {18/23} × ({4/9} × {6/7}) = ({18/23} × {4/9}) × {6/7}", "opts": ["a) associative (addition)  b) commutative (addition)  c) commutative (multiplication)  d) associative (multiplication)", "a) commutative (addition)  b) associative (addition)  c) associative (multiplication)  d) commutative (multiplication)", "a) commutative (addition)  b) distributive  c) commutative (multiplication)  d) distributive", "a) commutative (addition)  b) associative (addition)  c) commutative (multiplication)  d) associative (multiplication)"], "correct": 3, "tag": "", "sol": "Changing the order is the commutative property; changing the grouping is the associative property."}, {"kind": "mcq", "text": "<b>Check-up · Q8(e–h)</b> · State the properties involved:  e) {3/4} × 0 = 0 × {3/4} = 0   f) {7/8} + 0 = 0 + {7/8} = {7/8}   g) {15/19} × 1 = 1 × {15/19} = {15/19}   h) {16/17} × {3/4} + {20/31} × {3/4} = {3/4}({16/17} + {20/31})", "opts": ["e) additive identity  f) multiplication by zero  g) multiplicative identity  h) distributive", "e) multiplication by zero  f) additive identity  g) multiplicative identity  h) distributive", "e) multiplication by zero  f) additive identity  g) multiplicative inverse  h) distributive", "e) multiplication by zero  f) additive inverse  g) multiplicative inverse  h) associative"], "correct": 1, "tag": "", "sol": "e) any number × 0 = 0. f) 0 is the additive identity. g) 1 is the multiplicative identity. h) multiplication distributes over addition."}, {"kind": "blank", "p": "Neha marked {−3/4} on a number line by dividing each unit into 3 parts and counting 4 to the left. Correct her method.", "tag": "", "marks": "", "flat": [{"t": "She should divide each unit into __B1__ parts", "a": {"B1": "4"}}, {"t": "and count __B1__ parts", "a": {"B1": "3"}}, {"t": "to the __B1__ of 0 (left / right).", "a": {"B1": "left"}, "expr": "words"}], "sol": "The denominator gives the number of parts.\nThe numerator gives how many to count.\nNegative numbers are to the left."}, {"kind": "mcq", "text": "Aman writes: “{3/−7} is in standard form.” Which correction is best?", "opts": ["Yes — 3 and 7 are co-prime, so it is in standard form", "No — the denominator must be positive, so it is {−3/7}", "No — the sign must be removed, so it is {3/7}", "No — both signs change, so it is {−3/−7}"], "correct": 1, "tag": "", "sol": "Standard form needs a positive denominator; the sign moves to the numerator."}, {"kind": "blank", "p": "Complete the explanation of how to divide {−5/8} by {15/4}.", "tag": "", "marks": "", "flat": [{"t": "Multiply {−5/8} by the __B1__ of {15/4}.", "a": {"B1": "reciprocal"}, "expr": "words", "accept": ["multiplicative inverse", "inverse"]}, {"t": "That is {−5/8} × __B1__", "a": {"B1": "4/15"}, "expr": "fl"}, {"t": "The answer in lowest terms is __B1__", "a": {"B1": "-1/6"}, "expr": "fl"}], "sol": "Divide by multiplying by the reciprocal.\n{4/15}.\n{−20/120} = {−1/6}."}, {"kind": "mcq", "text": "Priya works out {2/3} − ({−1/6}) as {4/6} − {1/6} = {3/6}. What is her mistake?", "opts": ["Subtracting {−1/6} means adding {1/6}, so the answer is {5/6}", "She should subtract the denominators too, so the answer is {3/0}", "There is no mistake, {3/6} = {1/2} is correct", "She should use LCM 18, so the answer is {9/18}"], "correct": 0, "tag": "", "sol": "a − (−b) = a + b: {4/6} + {1/6} = {5/6}."}, {"kind": "mcq", "text": "Rahul says “0 is its own additive inverse and its own multiplicative inverse.” Which reply is correct?", "opts": ["Only the first part is true: 0 has no multiplicative inverse", "Both parts are true", "Only the second part is true", "Neither part is true"], "correct": 0, "tag": "", "sol": "0 + 0 = 0, but 0 × anything = 0 ≠ 1."}, {"kind": "mcq", "text": "<b>Check-up · Being Indian (c)</b> · Anuran's office is 12 km from his house. He takes an auto for part of the way, a bus for more, and walks the rest. Why do you think he walks some distance daily?", "opts": ["To stay physically active, which gives energy, mood, sleep and brain benefits", "To save money, because the auto and bus fares are too high", "Because the bus route does not go all the way to his office", "To save time, because walking is faster than the bus for short trips"], "correct": 0, "tag": "", "sol": "The passage explains that regular exercise gives more energy, improves mood, helps sleep and boosts brain health. Walking part of the way is an easy daily exercise."}]}, {"id": "s11", "label": "Assessment D", "sub": "Applying mathematics in real-life contexts", "slides": [{"kind": "blank", "p": "<b>Check-up · Q10</b> · Seema has a roll of ribbon 30 m long. She cuts strips of length {1 1/4} m. How many strips can she get? How much of the roll will be left?", "tag": "", "marks": "", "flat": [{"t": "Number of strips = __B1__", "a": {"B1": "24"}}, {"t": "Ribbon left = __B1__ m", "a": {"B1": "0"}}], "sol": "30 ÷ {5/4} = 30 × {4/5} = 24 strips.\n24 × {5/4} = 30 m, so 0 m is left."}, {"kind": "mcq", "text": "<b>Check-up · Q11(a)</b> · Priya and Sumit each earn ₹37,800 a month. Priya spends {1/7} on travel, {3/5} on household expenses and {1/18} on miscellaneous; Sumit spends {1/9}, {5/8} and {3/14}. The rest is deposited in the bank. Priya spends ______ on travel.", "opts": ["₹5600", "₹6000", "₹5000", "₹5400"], "correct": 3, "tag": "", "sol": "{1/7} × 37800 = ₹5400."}, {"kind": "mcq", "text": "<b>Check-up · Q11(b)</b> · (Same table.) Which statement is true about the household expenses? (Priya {3/5}, Sumit {5/8} of ₹37,800)", "opts": ["Priya and Sumit spend equal amounts", "None of these", "Sumit spends more", "Priya spends more"], "correct": 2, "tag": "", "sol": "Priya: {3/5} × 37800 = ₹22,680. Sumit: {5/8} × 37800 = ₹23,625. Also {5/8} > {3/5} ({25/40} > {24/40}). Sumit spends more."}, {"kind": "mcq", "text": "<b>Check-up · Q11(c)</b> · (Same table.) Sumit deposits ______ in his savings account. (He spends {1/9}, {5/8} and {3/14} of ₹37,800.)", "opts": ["₹1875", "₹1500", "₹2056", "₹2490"], "correct": 0, "tag": "", "sol": "Fraction spent = {1/9} + {5/8} + {3/14} = (56 + 315 + 108)/504 = {479/504}. Saved = {25/504} × 37800 = ₹1875."}, {"kind": "blank", "p": "<b>Check-up · Creative Thinking</b> · A submarine travels 100 km from the shore, then descends {1 1/10} km below sea level. It then ascends {3/5} km. The next day it descends {9/10} km more.", "tag": "", "marks": "", "flat": [{"t": "Position relative to sea level = __B1__ km (negative = below; type an improper fraction)", "a": {"B1": "-7/5"}, "expr": "fl"}, {"t": "Horizontal distance from the shore = __B1__ km", "a": {"B1": "100"}}], "sol": "−{11/10} + {6/10} − {9/10} = {−14/10} = {−7/5} km, i.e. {1 2/5} km below sea level.\nMoving up and down does not change the horizontal distance: 100 km."}, {"kind": "blank", "p": "<b>Check-up · Everyday Maths 1</b> · A train travels {722 1/2} km in {8 1/2} hours. Find its speed in km/h.", "tag": "", "marks": "", "flat": [{"t": "Speed = __B1__ km/h", "a": {"B1": "85"}, "expr": "fl"}], "sol": "{1445/2} ÷ {17/2} = {1445/2} × {2/17} = 85 km/h."}, {"kind": "mcq", "text": "<b>Check-up · Everyday Maths 2</b> · A shirt can be stitched using {2 1/4} m of cloth. How much cloth is needed for 9 shirts?", "opts": ["{20 1/4} m", "{81/36} m", "{11 1/4} m", "{18 1/4} m"], "correct": 0, "tag": "", "sol": "9 × {9/4} = {81/4} = {20 1/4} m."}, {"kind": "blank", "p": "<b>Check-up · Cross-Curricular (a)</b> · Long jump: Shruti {5 3/5} m, Mehak {5 1/2} m, Arti {5 3/4} m, Ruchi {5 9/10} m. How much farther did Shruti jump than Mehak?", "tag": "", "marks": "", "flat": [{"t": "Difference = __B1__ m", "a": {"B1": "1/10"}, "expr": "fl"}], "sol": "{5 3/5} − {5 1/2} = {3/5} − {1/2} = {6/10} − {5/10} = {1/10} m."}, {"kind": "mcq", "text": "<b>Check-up · Cross-Curricular (b)</b> · (Same table: Shruti {5 3/5} m, Mehak {5 1/2} m, Arti {5 3/4} m, Ruchi {5 9/10} m.) Who covered the longest distance?", "opts": ["Arti", "Mehak", "Ruchi", "Shruti"], "correct": 2, "tag": "", "sol": "Compare the fractions with denominator 20: {12/20}, {10/20}, {15/20}, {18/20}. Ruchi's {5 9/10} m is the longest."}, {"kind": "blank", "p": "<b>Check-up · Being Indian (a, b)</b> · Anuran's office is 12 km from his house. He takes an auto for {1/6} of the distance, covers {4/5} of the remaining by bus and walks the rest.", "tag": "", "marks": "", "flat": [{"t": "Distance walked one way = __B1__ km", "a": {"B1": "2"}}, {"t": "a) He repeats this on the way back. Distance walked every day = __B1__ km", "a": {"B1": "4"}}, {"t": "b) He goes to office 5 days a week. Distance walked every week = __B1__ km", "a": {"B1": "20"}}], "sol": "Auto: {1/6} × 12 = 2 km; remaining 10 km; bus {4/5} × 10 = 8 km; walks 10 − 8 = 2 km.\n2 km each way: 4 km a day.\n5 × 4 = 20 km a week."}]}];
/* ================= build slide lists ================= */
var SLIDES = {}; SECTIONS.forEach(function(sec){ SLIDES[sec.id]=sec.slides; });
var TAB_DEFS = SECTIONS.map(function(sec){ return {id:sec.id, label:sec.label, sub:sec.sub}; });

/* ================= state ================= */
function blankItem(slide){
  if(slide.kind==='mcq'||slide.kind==='ar'){
    return {status:'unanswered', attempts:0, choice:undefined};
  }
  return {status:'unanswered', curStep:0, stepStates: slide.flat.map(function(){ return {status:'unanswered', attempts:0, inputs:{}}; })};
}
function defaultState(){
  var s={tabs:{}};
  TAB_DEFS.forEach(function(td){
    s.tabs[td.id] = { idx:0, maxReached:0, items: SLIDES[td.id].map(function(sl){ return blankItem(sl); }) };
  });
  return s;
}
var appState = {mode:null, learning:null, quiz:null};
var state = null;      // alias for appState[appState.mode]
var MODE = null;
var activeTab=TAB_DEFS[0].id;

function setMode(m){
  appState.mode = m;
  if(!appState[m]) appState[m] = defaultState();
  state = appState[m];
  MODE = m;
}
/* ================= student accounts (saved on this device) ================= */
var SHEET_KEY='sopaan-c8-ch1';
var ACC_KEY='sopaan-students-v1';
var storageOK=true;
var MEM={};
function lsGet(k){ var r=null; try{ r=localStorage.getItem(k); }catch(e){ storageOK=false; }
  if(r===null||r===undefined) r=MEM[k]||null; try{ return r?JSON.parse(r):null; }catch(e){ return null; } }
function lsSet(k,v){ var j=JSON.stringify(v); MEM[k]=j; try{ localStorage.setItem(k,j); return true; }catch(e){ storageOK=false; return false; } }
try{ localStorage.setItem('sopaan-probe','1'); localStorage.removeItem('sopaan-probe'); }catch(e){ storageOK=false; }
function hashPin(pin,salt){ var h=2166136261, str=salt+'|'+pin; for(var i=0;i<str.length;i++){ h^=str.charCodeAt(i); h=Math.imul(h,16777619)>>>0; } return h.toString(36); }
function accKey(name,roll){ return (name.trim().toLowerCase().replace(/\s+/g,' ')+'#'+roll.trim().toLowerCase()); }
function accounts(){ return lsGet(ACC_KEY)||{students:{}}; }
var student=null; // {key,name,roll}
var records=[];   // finished-tab history for this student on this sheet
function progKey(){ return SHEET_KEY+'::'+student.key; }

function loadState(){
  appState = {mode:null, learning:null, quiz:null}; records=[]; activeTab=TAB_DEFS[0].id;
  var saved=lsGet(progKey());
  if(!saved) return;
  try{
    ['learning','quiz'].forEach(function(m){
      if(saved[m] && saved[m].tabs){
        var fresh = defaultState();
        TAB_DEFS.forEach(function(td){
          if(saved[m].tabs[td.id] && saved[m].tabs[td.id].items && saved[m].tabs[td.id].items.length===SLIDES[td.id].length){
            fresh.tabs[td.id] = saved[m].tabs[td.id];
          }
        });
        appState[m] = fresh;
      }
    });
    if(saved.mode==='learning' || saved.mode==='quiz') appState.mode = saved.mode;
    if(saved.activeTab && TAB_DEFS.some(function(t){ return t.id===saved.activeTab; })) activeTab = saved.activeTab;
    if(Array.isArray(saved.records)) records = saved.records;
  }catch(e){}
}
function saveState(){
  if(!student) return;
  lsSet(progKey(), {mode:appState.mode, learning:appState.learning, quiz:appState.quiz, activeTab:activeTab, records:records, updated:Date.now()});
  var acc=accounts(); if(acc.students[student.key]){ acc.students[student.key].last=Date.now(); lsSet(ACC_KEY,acc); }
}
function addRecord(mode, tabId, correct, revealed, skipped, total){
  records.unshift({at:Date.now(), mode:mode, tab:tabId, correct:correct, revealed:revealed, skipped:skipped, total:total});
  if(records.length>60) records.length=60;
  saveState();
}
function fmtDate(ms){ try{ return new Date(ms).toLocaleString(undefined,{day:'numeric',month:'short',hour:'2-digit',minute:'2-digit'}); }catch(e){ return ''; } }

function renderWho(){
  var el=document.getElementById('whoBar');
  if(!student){ el.hidden=true; el.innerHTML=''; return; }
  el.hidden=false;
  el.innerHTML='Signed in as <b>'+esc(student.name)+'</b> · Roll '+esc(student.roll)+
    ' <button id="btnRecord">My record</button> <button id="btnSignOut">Sign out</button>';
  document.getElementById('btnRecord').addEventListener('click', renderRecord);
  document.getElementById('btnSignOut').addEventListener('click', signOut);
}
function signOut(){
  saveState(); student=null; state=null; MODE=null;
  var acc=accounts(); delete acc.current; lsSet(ACC_KEY,acc);
  document.getElementById('modePill').hidden=true;
  renderWho(); renderLogin();
}
function signIn(key){
  var acc=accounts(); var st=acc.students[key]; if(!st) return;
  student={key:key, name:st.name, roll:st.roll};
  acc.current=key; st.last=Date.now(); lsSet(ACC_KEY,acc);
  loadState(); renderWho();
  if(appState.mode==='learning' || appState.mode==='quiz'){
    setMode(appState.mode); document.getElementById('modePill').hidden=false; updateModePill();
    showChrome(true); buildTabbar(); renderSlide();
    showToast('Welcome back, '+st.name.split(' ')[0]+'. Picking up where you left off.');
  } else {
    renderModePicker();
  }
}
function renderLogin(msg){
  showChrome(false);
  var acc=accounts(); var keys=Object.keys(acc.students).sort(function(a,b){ return (acc.students[b].last||0)-(acc.students[a].last||0); });
  var h='<div class="login-card"><h2>Student sign-in</h2>'+
    '<p class="lead">Sign in to save your answers, see your record and continue where you left off next time.</p>';
  if(!storageOK) h+='<div class="login-err">This browser is blocking saved data (for example, a private window). You can still practise, but progress will not be kept after you close the page.</div>';
  if(msg) h+='<div class="login-err">'+esc(msg)+'</div>';
  if(keys.length){
    h+='<div class="known"><span class="known-label">Continue as</span>';
    keys.slice(0,6).forEach(function(k){ var st=acc.students[k];
      h+='<button class="known-btn" data-k="'+esc(k)+'"><span>'+esc(st.name)+' <small>· Roll '+esc(st.roll)+'</small></span><small>'+(st.last?'Last active '+fmtDate(st.last):'')+'</small></button>'; });
    h+='</div>';
  }
  h+='<form id="loginForm" novalidate>'+
    '<div class="fld"><label for="lgName">Full name</label><input id="lgName" autocomplete="name" required></div>'+
    '<div class="fld-row"><div class="fld"><label for="lgRoll">Roll no.</label><input id="lgRoll" required></div>'+
    '<div class="fld"><label for="lgPin">4-digit PIN</label><input id="lgPin" type="password" inputmode="numeric" maxlength="4" autocomplete="off" required></div></div>'+
    '<button class="btn btn-primary" type="submit" style="width:100%;">Sign in</button>'+
    '<p class="login-note">New here? Enter your name, roll no. and a PIN you will remember, and your profile is created. Progress is saved on this device, so use the same device and browser to continue.</p>'+
    '</form></div>';
  var wrap=document.getElementById('wrap'); wrap.innerHTML=h;
  wrap.querySelectorAll('.known-btn').forEach(function(b){
    b.addEventListener('click', function(){
      var st=accounts().students[b.dataset.k];
      document.getElementById('lgName').value=st.name; document.getElementById('lgRoll').value=st.roll;
      document.getElementById('lgPin').focus();
    });
  });
  document.getElementById('loginForm').addEventListener('submit', function(e){
    e.preventDefault();
    var name=document.getElementById('lgName').value.trim(), roll=document.getElementById('lgRoll').value.trim(), pin=document.getElementById('lgPin').value.trim();
    if(!name||!roll){ renderLoginErr('Enter your name and roll no.'); return; }
    if(!/^\d{4}$/.test(pin)){ renderLoginErr('Your PIN must be exactly 4 digits.'); return; }
    var k=accKey(name,roll); var acc=accounts();
    if(acc.students[k]){
      if(acc.students[k].pin!==hashPin(pin,k)){ renderLoginErr('That PIN does not match this name and roll no. Try again.'); return; }
    } else {
      acc.students[k]={name:name.replace(/\s+/g,' '), roll:roll, pin:hashPin(pin,k), created:Date.now()};
      lsSet(ACC_KEY,acc);
    }
    signIn(k);
  });
}
function renderLoginErr(m){
  var n=document.getElementById('lgName').value, r=document.getElementById('lgRoll').value;
  renderLogin(m); document.getElementById('lgName').value=n; document.getElementById('lgRoll').value=r; document.getElementById('lgPin').focus();
}
function tabSummary(m){
  var st=appState[m]; if(!st) return null;
  return TAB_DEFS.map(function(td){
    var items=st.tabs[td.id].items, n=items.length;
    var c=items.filter(function(i){return i.status==='correct';}).length;
    var done=items.filter(function(i){return i.status!=='unanswered';}).length;
    return {label:td.label, n:n, done:done, correct:c};
  });
}
function renderRecord(){
  showChrome(false);
  var tabLabel=function(id){ var t=TAB_DEFS.find(function(x){return x.id===id;}); return t?t.label:id; };
  var h='<div class="rec-card"><h2>'+esc(student.name)+'’s record</h2><p class="rec-empty" style="margin:0 0 12px;">Roll '+esc(student.roll)+' · Rational Numbers</p>';
  ['learning','quiz'].forEach(function(m){
    var sum=tabSummary(m);
    h+='<h3>'+(m==='learning'?'📘 Learning Sheet':'📝 Quiz Mode')+'</h3>';
    if(!sum){ h+='<p class="rec-empty">Not started yet.</p>'; return; }
    h+='<div class="rec-table-wrap"><table class="rec-table"><thead><tr><th>Section</th><th>Progress</th><th>Correct first time</th></tr></thead><tbody>';
    sum.forEach(function(r){ var pct=Math.round(r.done/r.n*100);
      h+='<tr><td>'+r.label+'</td><td><span class="rec-bar"><i style="width:'+pct+'%"></i></span>'+r.done+' / '+r.n+'</td><td>'+(m==='quiz'?'—':r.correct+' / '+r.n)+'</td></tr>'; });
    h+='</tbody></table></div>';
  });
  h+='</div><div class="rec-card"><h3>Finished sections</h3>';
  if(!records.length){ h+='<p class="rec-empty">No sections finished yet. Each time you finish a tab, your score is recorded here.</p>'; }
  else {
    h+='<div class="rec-table-wrap"><table class="rec-table"><thead><tr><th>When</th><th>Mode</th><th>Section</th><th>Score</th></tr></thead><tbody>';
    records.forEach(function(r){ h+='<tr><td>'+fmtDate(r.at)+'</td><td>'+(r.mode==='quiz'?'Quiz':'Learning')+'</td><td>'+tabLabel(r.tab)+'</td><td>'+r.correct+' / '+r.total+(r.mode==='learning'?' <span class="rec-empty">('+r.revealed+' revealed, '+r.skipped+' skipped)</span>':'')+'</td></tr>'; });
    h+='</tbody></table></div>';
  }
  h+='</div><button class="btn btn-primary" id="btnBack">'+(MODE?'Back to practice':'Choose a mode')+'</button>';
  document.getElementById('wrap').innerHTML=h;
  document.getElementById('btnBack').addEventListener('click', function(){
    if(MODE){ showChrome(true); buildTabbar(); renderSlide(); } else renderModePicker();
  });
  window.scrollTo({top:0});
}

/* ================= tab bar ================= */
function buildTabbar(){
  var el=document.getElementById('tabbar');
  el.innerHTML = '<button class="tab-btn'+(activeTab==='theory'?' active':'')+'" data-tab="theory">Theory<span class="tab-count">notes</span></button>' + TAB_DEFS.map(function(t){
    return '<button class="tab-btn'+(t.id===activeTab?' active':'')+'" data-tab="'+t.id+'">'+t.label+'<span class="tab-count">'+SLIDES[t.id].length+'</span></button>';
  }).join('') + '<button class="tab-btn'+(activeTab==='report'?' active':'')+'" data-tab="report">📊 Report<span class="tab-count">pie</span></button>';
  el.querySelectorAll('.tab-btn').forEach(function(btn){
    btn.addEventListener('click', function(){ activeTab=btn.dataset.tab; buildTabbar(); renderSlide(); window.scrollTo({top:0,behavior:'smooth'}); });
  });
}

/* ================= rendering ================= */
function canProceed(item){ return item.status==='correct'||item.status==='revealed'||item.status==='skipped'; }

function renderSlide(){
  if(!state.tabs[activeTab]){ activeTab=TAB_DEFS[0].id; }
  var ts = state.tabs[activeTab];
  var slides = SLIDES[activeTab];
  if(ts.idx>=slides.length||ts.idx<0) ts.idx=0;
  var idx = ts.idx;
  var slide = slides[idx];
  var item = ts.items[idx];

  var tdef=TAB_DEFS.find(function(t){return t.id===activeTab;});
  document.getElementById('spLabel').textContent = tdef.label+' · Question '+(idx+1)+' of '+slides.length;
  document.getElementById('secSub').textContent = tdef.label+' — '+tdef.sub;
  document.getElementById('spFill').style.width = Math.round(((idx)/(Math.max(slides.length-1,1)))*100)+'%';

  var h='<div class="qcard">';
  if(slide.kind==='mcq' || slide.kind==='ar'){
    h += renderChoiceBody(slide, item, idx);
  } else {
    h += renderBlankBody(slide, item, idx);
  }
  h += '<div class="feedback" id="feedbackBox"></div>';
  if(MODE==='learning' && (item.status==='correct'||item.status==='revealed')) h += solutionHTML(slide);
  h += '</div>';

  document.getElementById('wrap').innerHTML = h;
  wireSlideEvents(slide, item, idx);
  restoreFeedback(item);
  renderNavbar(item);
  updateFab();
  saveState();
}

function solutionHTML(slide){
  if(!slide.sol) return '';
  return '<div class="solution"><div class="sol-h">Solution</div>'+slide.sol.split('\n').map(function(l){ return '<div class="sol-line">'+fr(esc(l))+'</div>'; }).join('')+'</div>';
}
var LETTERS=['a','b','c','d','e','f'];
function chosenHTML(slide,item){
  var opts = slide.kind==='mcq' ? slide.opts : AR_OPTIONS;
  if(item.choice===undefined) return '';
  var ok=item.choice===slide.correct;
  var h='<div class="chosen '+(ok?'ok':'bad')+'"><b>Your answer:</b> ('+LETTERS[item.choice]+') '+fr(esc(opts[item.choice]))+(ok?' ✓':' ✗')+'</div>';
  if(!ok) h+='<div class="chosen ok"><b>Correct answer:</b> ('+LETTERS[slide.correct]+') '+fr(esc(opts[slide.correct]))+'</div>';
  return h;
}
function renderChoiceBody(slide, item, idx){
  var h='<div class="qhead"><div class="qnum">'+(idx+1)+'</div>';
  if(slide.kind==='mcq'){
    h += '<div class="qtext">'+fr(esc(slide.text))+(slide.tag?'<span class="qtag">'+esc(slide.tag)+'</span>':'')+'</div>';
  } else {
    h += '<div class="qtext"><span class="qtag" style="margin-left:0;margin-right:6px;">A / R</span>Assertion (A): '+fr(esc(slide.a))+'<br>Reason (R): '+fr(esc(slide.r))+(slide.tag?'<span class="qtag">'+esc(slide.tag)+'</span>':'')+'</div>';
  }
  h += '</div>';
  if(slide.fig) h += '<div class="fig">'+slide.fig+'</div>';
  var opts = slide.kind==='mcq' ? slide.opts : AR_OPTIONS;
  if(MODE==='quiz') h += '<div class="quiz-hint">Quiz mode — pick an option. The correct answer is revealed once you finish this tab.</div>';
  var locked = MODE==='learning' && (item.status==='correct' || item.status==='revealed');
  h += '<div class="options">';
  opts.forEach(function(opt,i){
    var cls='opt';
    if(locked){
      if(i===slide.correct) cls+=' is-correct';
      else if(item.choice===i) cls+=' is-wrong';
      cls+=' locked';
    }
    if(item.choice===i) cls+=' is-chosen';
    h += '<label class="'+cls+'"><input type="radio" name="choice" value="'+i+'" '+(item.choice===i?'checked':'')+' '+(locked?'disabled':'')+'> <span class="opt-l">('+LETTERS[i]+')</span> <span class="opt-t">'+fr(esc(opt))+'</span>'+(item.choice===i?'<span class="opt-tag">'+(locked?(i===slide.correct?'Your answer ✓':'Your answer ✗'):'Selected')+'</span>':'')+'</label>';
  });
  h += '</div>';
  if(locked) h += chosenHTML(slide,item);
  return h;
}

function renderBlankBody(slide, item, idx){
  var h='<div class="qhead"><div class="qnum">'+(idx+1)+'</div><div class="qtext">';
  if(slide.kind==='case'){ h += '<b>'+esc(slide.title)+'.</b> '+esc(slide.body); }
  else { var pp=fr(esc(slide.p)).split('\n'); h += pp[0]+pp.slice(1).map(function(x){return '<span class="datline">'+x+'</span>';}).join(''); }
  h += (slide.tag?'<span class="qtag">'+esc(slide.tag)+'</span>':'')+'</div>';
  if(slide.marks) h += '<div class="marks-pill">'+slide.marks+'</div>';
  h += '</div>';
  if(slide.fig) h += '<div class="fig">'+slide.fig+'</div>';

  var total = slide.flat.length;
  var hasExpr = slide.flat.some(function(s){ return s.expr===true; });
  var hasFrac = slide.flat.some(function(s){ return ['fv','fe','fl','fm','fi','flist'].indexOf(s.expr)>=0; });
  var blankCount=0; slide.flat.forEach(function(s){ blankCount+=Object.keys(s.a).length; });

  if(MODE==='quiz'){
    h += '<div class="step-badge">'+blankCount+' blank'+(blankCount===1?'':'s')+' in this question</div>';
    h += '<div class="quiz-hint">Quiz mode — fill in what you can. Correct answers are revealed once you finish this tab.</div>';
    if(hasFrac) h += '<div class="quiz-hint">Type fractions like <b>3/4</b> and mixed numbers like <b>2 3/4</b> (whole number, space, fraction).</div>';
    if(hasExpr) h += '<div class="quiz-hint">Type answers like <b>2x-5</b>, <b>x^2-4</b> or <b>3+2i</b>. Use ^ for powers, | | for absolute value and pi for π. Any equivalent form is accepted.</div>';
    h += '<div class="steps">';
    for(var qi=0; qi<total; qi++){
      var qstep = slide.flat[qi];
      var qss = item.stepStates[qi];
      if(qstep.partLabel) h += '<div class="subpart-label">'+esc(qstep.partLabel)+'</div>';
      if(qstep.orDivider) h += '<div class="or-divider">OR</div>';
      var qline = fr(qstep.t);
      Object.keys(qstep.a).forEach(function(bkey){
        var val = qss.inputs[bkey]||'';
        var inp='<input class="blank-input'+(['fv','fe','fl','fm','fi','dec'].indexOf(qstep.expr)>=0?' fr':(qstep.expr==='flist'||qstep.expr==='dlist'||qstep.expr==='glist')?' wide':qstep.expr===true?' expr':(qstep.expr==='words'||qstep.expr==='list'||qstep.expr==='expanded'||qstep.expr==='set'||qstep.expr==='primes'||qstep.expr==='trans'||qstep.expr==='rot'?' wide':''))+'" data-step="'+qi+'" data-bkey="'+bkey+'" value="'+esc(val)+'">';
        qline = qline.replace('__'+bkey+'__', inp);
      });
      if(qstep.fig) h += '<div class="fig">'+qstep.fig+'</div>';
      h += '<div class="step-line">'+qline+'</div>';
    }
    h += '</div>';
    return h;
  }

  if(hasFrac) h += '<div class="quiz-hint">Type fractions like <b>3/4</b> and mixed numbers like <b>2 3/4</b> (whole number, space, fraction).</div>';
  if(hasExpr) h += '<div class="quiz-hint">Type answers like <b>2x-5</b>, <b>x^2-4</b> or <b>3+2i</b>. Use ^ for powers, | | for absolute value and pi for π. Any equivalent form is accepted.</div>';
  var locked = item.status==='correct' || item.status==='revealed';
  var upto = locked ? total-1 : item.curStep;
  h += '<div class="step-badge">Step '+(Math.min(item.curStep,total-1)+1)+' of '+total+'</div>';
  h += '<div class="steps">';
  for(var i=0;i<=upto;i++){
    var step = slide.flat[i];
    var ss = item.stepStates[i];
    if(step.partLabel) h += '<div class="subpart-label">'+esc(step.partLabel)+'</div>';
    if(step.orDivider) h += '<div class="or-divider">OR</div>';
    var resolved = ss.status==='correct' || ss.status==='revealed';
    var line = fr(step.t);
    Object.keys(step.a).forEach(function(bkey){
      var fs = ss.inputs['fs_'+bkey];
      var cls = fs==='correct'?'is-correct':(fs==='wrong'?'is-wrong':'');
      var val = ss.inputs[bkey]||'';
      var dis = resolved ? 'disabled':'';
      var inp='<input class="blank-input '+cls+(['fv','fe','fl','fm','fi','dec'].indexOf(step.expr)>=0?' fr':(step.expr==='flist'||step.expr==='dlist'||step.expr==='glist')?' wide':step.expr===true?' expr':(step.expr==='words'||step.expr==='list'||step.expr==='expanded'||step.expr==='set'||step.expr==='primes'||step.expr==='trans'||step.expr==='rot'?' wide':''))+'" data-step="'+i+'" data-bkey="'+bkey+'" value="'+esc(val)+'" '+dis+'>';
      line = line.replace('__'+bkey+'__', inp);
    });
    if(step.fig) h += '<div class="fig">'+step.fig+'</div>';
    h += '<div class="step-line'+(resolved?' resolved':'')+'">'+line+'</div>';
    if(ss.status==='revealed'){
      var reveals=[];
      Object.keys(step.a).forEach(function(bkey){ reveals.push(bkey+' = '+esc(step.a[bkey])); });
      h += '<div class="reveal-note">correct: '+reveals.join(', ')+'</div>';
    }
  }
  h += '</div>';
  return h;
}

var __flash=null;
function restoreFeedback(item){
  var fb=document.getElementById('feedbackBox'); if(!fb) return;
  if(__flash){ fb.className='feedback show '+__flash.c; fb.innerHTML=__flash.h; __flash=null; return; }
  if(MODE==='quiz'){ fb.className='feedback'; fb.innerHTML=''; return; }
  if(item.status==='correct'){ fb.className='feedback show ok'; fb.innerHTML='<b>All done — correct!</b>'; }
  else if(item.status==='revealed'){ fb.className='feedback show reveal'; fb.innerHTML='<b>Answer revealed above.</b> Move on whenever you’re ready.'; }
  else if(item.status==='skipped'){ fb.className='feedback show retry'; fb.innerHTML='Skipped — you can answer it now and press <b>Check</b>, or come back later from the Question Palette.'; }
  else { fb.className='feedback'; fb.innerHTML=''; }
}

function slideIsAnswered(slide,item){
  if(slide.kind==='mcq'||slide.kind==='ar') return item.choice!==undefined;
  return item.stepStates.some(function(ss){ return Object.keys(ss.inputs).some(function(k){ return k.indexOf('fs_')!==0 && ss.inputs[k] && String(ss.inputs[k]).trim()!==''; }); });
}
function renderNavbar(item){
  var ts = state.tabs[activeTab];
  var slides = SLIDES[activeTab];
  var slide = slides[ts.idx];
  var isLast = ts.idx === slides.length-1;
  var h='';
  h += '<button class="btn" id="btnPrev" '+(ts.idx===0?'disabled':'')+'>&larr; Previous</button>';

  if(MODE==='quiz'){
    h += '<button class="btn" id="btnSkip">Skip</button>';
    h += '<span class="spacer"></span>';
    h += '<button class="btn btn-primary" id="btnNext">'+(isLast?'Finish':'Next →')+'</button>';
  } else {
    h += '<button class="btn" id="btnSkip" '+(item.status!=='unanswered'?'disabled':'')+'>Skip</button>';
    h += '<span class="spacer"></span>';
    h += '<button class="btn btn-primary" id="btnCheck" '+((item.status!=='unanswered'&&item.status!=='skipped')?'disabled':'')+'>Check</button>';
    h += '<button class="btn btn-primary" id="btnNext" '+(canProceed(item)?'':'disabled')+'>'+(isLast?'Finish':'Next →')+'</button>';
  }
  document.getElementById('navbarInner').innerHTML = h;

  document.getElementById('btnPrev').addEventListener('click', function(){ if(ts.idx>0){ ts.idx--; renderSlide(); } });

  if(MODE==='quiz'){
    document.getElementById('btnSkip').addEventListener('click', function(){
      item.status='skipped';
      advanceQuiz(ts, slides);
    });
    document.getElementById('btnNext').addEventListener('click', function(){
      item.status = slideIsAnswered(slide,item) ? 'answered' : 'unanswered';
      advanceQuiz(ts, slides);
    });
  } else {
    document.getElementById('btnSkip').addEventListener('click', function(){
      if(item.status==='unanswered'){ item.status='skipped'; renderSlide(); }
    });
    document.getElementById('btnNext').addEventListener('click', function(){
      if(!canProceed(item)) return;
      if(ts.idx < slides.length-1){ ts.idx++; ts.maxReached=Math.max(ts.maxReached, ts.idx); renderSlide(); }
      else { renderFinished(); }
    });
    document.getElementById('btnCheck').addEventListener('click', function(){ handleCheck(); });
  }
}
function advanceQuiz(ts, slides){
  if(ts.idx < slides.length-1){ ts.idx++; ts.maxReached=Math.max(ts.maxReached, ts.idx); renderSlide(); }
  else { renderFinished(); }
}

function wireSlideEvents(slide, item, idx){
  document.querySelectorAll('input[type="radio"][name="choice"]').forEach(function(r){
    r.addEventListener('change', function(){ item.choice=parseInt(r.value,10); saveState();
      document.querySelectorAll('.opt').forEach(function(l){ l.classList.remove('is-chosen'); var t=l.querySelector('.opt-tag'); if(t) t.remove(); });
      var lab=r.closest('.opt'); lab.classList.add('is-chosen'); var tg=document.createElement('span'); tg.className='opt-tag'; tg.textContent='Selected'; lab.appendChild(tg); });
  });
  document.querySelectorAll('.blank-input').forEach(function(inp){
    inp.addEventListener('input', function(){
      var si=parseInt(inp.dataset.step,10), bk=inp.dataset.bkey;
      item.stepStates[si].inputs[bk]=inp.value;
      saveState();
    });
  });
}

function handleCheck(){
  var ts = state.tabs[activeTab];
  var slide = SLIDES[activeTab][ts.idx];
  var item = ts.items[ts.idx];
  if(item.status==='skipped') item.status='unanswered';
  var fb = document.getElementById('feedbackBox');

  if(slide.kind==='mcq' || slide.kind==='ar'){
    if(item.choice===undefined){ fb.className='feedback show err'; fb.innerHTML='Please choose an option first.'; return; }
    var ok = item.choice===slide.correct;
    if(ok){
      item.status='correct'; playSuccess();
      fb.className='feedback show ok'; fb.innerHTML='<b>Correct!</b>';
    } else {
      item.attempts=(item.attempts||0)+1;
      if(item.attempts>=2){ item.status='revealed'; playReveal(); }
      else { playWrong(); fb.className='feedback show retry'; fb.innerHTML='<b>Not quite — try again</b> (attempt 1 of 2) <span class="attempts-dots"><span class="used"></span><span></span></span>'; __flash={c:'retry',h:'<b>Not quite — try again</b> (attempt 1 of 2) <span class="attempts-dots"><span class="used"></span><span></span></span>'}; }
    }
    renderSlide();
    return;
  }

  // blank / case
  var step = slide.flat[item.curStep];
  var ss = item.stepStates[item.curStep];
  var blanks = Object.keys(step.a);
  var missing = blanks.some(function(k){ return !ss.inputs[k] || String(ss.inputs[k]).trim()===''; });
  if(missing){ fb.className='feedback show err'; fb.innerHTML='Fill in every blank in this step before checking.'; return; }

  var allGood=true;
  blanks.forEach(function(k){
    var good=answerMatches(ss.inputs[k], step.a[k], step.accept, step.expr);
    ss.inputs['fs_'+k]=good?'correct':'wrong';
    if(!good) allGood=false;
  });

  if(allGood){
    ss.status='correct'; playSuccess();
    advanceStepOrFinish(item, slide);
  } else {
    ss.attempts=(ss.attempts||0)+1;
    if(ss.attempts>=2){
      ss.status='revealed'; playReveal();
      advanceStepOrFinish(item, slide);
    } else {
      playWrong();
      fb.className='feedback show retry';
      fb.innerHTML='<b>Not quite — try again</b> (attempt 1 of 2) <span class="attempts-dots"><span class="used"></span><span></span></span>'; __flash={c:'retry',h:'<b>Not quite — try again</b> (attempt 1 of 2) <span class="attempts-dots"><span class="used"></span><span></span></span>'};
      renderSlide();
      return;
    }
  }
  renderSlide();
}

function advanceStepOrFinish(item, slide){
  var total = slide.flat.length;
  var hasExpr = slide.flat.some(function(s){ return s.expr===true; });
  var hasFrac = slide.flat.some(function(s){ return ['fv','fe','fl','fm','fi','flist'].indexOf(s.expr)>=0; });
  if(item.curStep < total-1){
    item.curStep++;
  } else {
    var anyRevealed = item.stepStates.some(function(ss){ return ss.status==='revealed'; });
    item.status = anyRevealed ? 'revealed' : 'correct';
  }
}

/* ================= palette ================= */
var overlay=document.getElementById('overlay');
function statusOf(tabId,i){
  var ts=state.tabs[tabId];
  if(i>ts.maxReached) return 'locked';
  if(i===ts.idx) return 'current';
  return ts.items[i].status==='unanswered' ? 'locked' : ts.items[i].status;
}
function buildPalette(){
  var slides=SLIDES[activeTab];
  document.getElementById('paletteTitle').textContent = TAB_DEFS.find(function(t){return t.id===activeTab;}).label+' · Question palette';
  var body=document.getElementById('paletteBody');
  var html='';
  for(var i=0;i<slides.length;i++){
    html += '<div class="chip" data-status="'+statusOf(activeTab,i)+'" data-idx="'+i+'">'+(i+1)+'</div>';
  }
  body.innerHTML = html;
  body.querySelectorAll('.chip').forEach(function(chip){
    chip.addEventListener('click', function(){
      var i=parseInt(chip.dataset.idx,10);
      var ts=state.tabs[activeTab];
      if(i>ts.maxReached){ showToast('Finish the earlier questions to unlock this one.'); return; }
      ts.idx=i; closePalette(); renderSlide();
    });
  });
}
function openPalette(){ buildPalette(); overlay.classList.add('show'); }
function closePalette(){ overlay.classList.remove('show'); }
var toastTimer;
function showToast(msg){
  var t=document.getElementById('toast'); t.textContent=msg; t.classList.add('show');
  clearTimeout(toastTimer); toastTimer=setTimeout(function(){ t.classList.remove('show'); },2200);
}
document.getElementById('paletteFab').addEventListener('click', openPalette);
document.getElementById('paletteClose').addEventListener('click', closePalette);
overlay.addEventListener('click', function(e){ if(e.target===overlay) closePalette(); });

function updateFab(){
  var slides=SLIDES[activeTab];
  var done=state.tabs[activeTab].items.filter(function(it){ return it.status==='correct'||it.status==='revealed'||it.status==='skipped'; }).length;
  document.getElementById('fabBadge').textContent = done+'/'+slides.length;
}

/* ================= overall progress + finish ================= */
function updateChapterProgress(){
  var total=0, done=0;
  TAB_DEFS.forEach(function(td){
    state.tabs[td.id].items.forEach(function(it){
      total++;
      if(it.status==='correct'||it.status==='revealed'||it.status==='skipped') done++;
    });
  });
  var pct = total>0 ? Math.round((done/total)*100) : 0;
  document.getElementById('cpFill').style.width=pct+'%';
  document.getElementById('cpLabel').textContent=pct+'% complete';
}
function isSlideCorrect(tabId,i){
  var slide=SLIDES[tabId][i], item=state.tabs[tabId].items[i];
  if(slide.kind==='mcq'||slide.kind==='ar') return item.choice===slide.correct;
  return slide.flat.every(function(step,si){
    var ss=item.stepStates[si];
    return Object.keys(step.a).every(function(k){ return answerMatches(ss.inputs[k], step.a[k], step.accept, step.expr); });
  });
}
function isSlideAttempted(tabId,i){
  var slide=SLIDES[tabId][i], item=state.tabs[tabId].items[i];
  if(slide.kind==='mcq'||slide.kind==='ar') return item.choice!==undefined;
  return slide.flat.some(function(step,si){
    var ss=item.stepStates[si];
    return Object.keys(step.a).some(function(k){ return ss.inputs[k] && String(ss.inputs[k]).trim()!==''; });
  });
}
function slideLabel(slide){
  var t = slide.kind==='case' ? slide.title : (slide.kind==='ar' ? slide.a : (slide.p||slide.text||''));
  t = String(t);
  return t.length>90 ? t.slice(0,90)+'…' : t;
}
function slideAnswerText(slide, item, correctSide){
  if(slide.kind==='mcq'||slide.kind==='ar'){
    var opts = slide.kind==='mcq' ? slide.opts : AR_OPTIONS;
    if(correctSide) return '('+LETTERS[slide.correct]+') '+opts[slide.correct];
    return item.choice!==undefined ? '('+LETTERS[item.choice]+') '+opts[item.choice] : '— not attempted —';
  }
  return slide.flat.map(function(step,si){
    var ss=item.stepStates[si];
    return Object.keys(step.a).map(function(k){
      return correctSide ? step.a[k] : (ss.inputs[k] || '—');
    }).join(', ');
  }).join('  |  ');
}

function renderFinished(){
  if(MODE==='quiz'){ renderQuizResults(); return; }
  var ts=state.tabs[activeTab];
  var correct=ts.items.filter(function(i){return i.status==='correct';}).length;
  var revealed=ts.items.filter(function(i){return i.status==='revealed';}).length;
  var skipped=ts.items.filter(function(i){return i.status==='skipped';}).length;
  var h='<div class="qcard done-card"><div class="big">✨</div><h2>Tab complete</h2>';
  h+='<p style="color:var(--ink-soft);font-size:14px;">You worked through all '+ts.items.length+' questions in this tab.</p>';
  if(!ts.recorded){ ts.recorded=true; addRecord('learning', activeTab, correct, revealed, skipped, ts.items.length); }
  h+='<div class="score-pills">'+
     '<span class="score-pill" style="background:var(--success-soft);color:var(--success);">'+correct+' correct</span>'+
     '<span class="score-pill" style="background:var(--danger-soft);color:var(--danger);">'+revealed+' revealed</span>'+
     '<span class="score-pill" style="background:var(--gold-soft);color:var(--retry-text);">'+skipped+' skipped</span></div>'+
     '<button class="btn btn-primary" id="btnReview">Review from question 1</button></div>';
  document.getElementById('wrap').innerHTML=h;
  document.getElementById('navbarInner').innerHTML='';
  document.getElementById('btnReview').addEventListener('click', function(){ ts.idx=0; ts.recorded=false; renderSlide(); });
  updateChapterProgress(); saveState();
}

function renderQuizResults(){
  var ts=state.tabs[activeTab];
  var slides=SLIDES[activeTab];
  var correctCount=0, attemptedCount=0;
  var rowsHtml = slides.map(function(slide,i){
    var item=ts.items[i];
    var ok=isSlideCorrect(activeTab,i);
    var att=isSlideAttempted(activeTab,i);
    if(ok) correctCount++;
    if(att) attemptedCount++;
    var tagCls = ok?'ok':(att?'bad':'na');
    var tagText = ok?'Correct':(att?'Incorrect':'Not attempted');
    var row='<div class="review-row">';
    row+='<span class="review-tag '+tagCls+'">Q'+(i+1)+' · '+tagText+'</span>';
    row+='<div class="review-q">'+fr(esc(slideLabel(slide)))+'</div>';
    row+='<div class="review-ans"><b>Your answer:</b> '+fr(esc(slideAnswerText(slide,item,false)))+'</div>';
    if(!ok) row+='<div class="review-ans" style="color:var(--success);"><b>Correct answer:</b> '+fr(esc(slideAnswerText(slide,item,true)))+'</div>';
    if(slide.sol) row+='<details class="rev-sol"><summary>Show solution</summary>'+solutionHTML(slide)+'</details>';
    row+='</div>';
    return row;
  }).join('');

  addRecord('quiz', activeTab, correctCount, 0, 0, slides.length);
  var h='<div class="qcard done-card" style="text-align:left;">';
  h+='<div style="text-align:center;"><div class="big">🏁</div><h2>Quiz complete</h2>';
  h+='<p style="color:var(--ink-soft);font-size:14px;">'+correctCount+' / '+slides.length+' correct · '+attemptedCount+' attempted</p></div>';
  h+='<div style="margin-top:16px;">'+rowsHtml+'</div>';
  h+='<div style="text-align:center;margin-top:6px;"><button class="btn btn-primary" id="btnReview">Review from question 1</button></div>';
  h+='</div>';
  document.getElementById('wrap').innerHTML=h;
  document.getElementById('navbarInner').innerHTML='';
  document.getElementById('btnReview').addEventListener('click', function(){ ts.idx=0; renderSlide(); });
  playSuccess();
  updateChapterProgress(); saveState();
}

/* ================= mode picker ================= */
function updateModePill(){
  var btn=document.getElementById('modePill');
  if(!btn) return;
  btn.textContent = MODE==='quiz' ? '📝 Quiz Mode · switch' : '📘 Learning Sheet · switch';
}
function showChrome(show){
  document.querySelector('.tabbar').style.display = show?'':'none';
  document.querySelector('.slide-progress').style.display = show?'':'none';
  document.querySelector('.navbar').style.display = show?'':'none';
  document.getElementById('paletteFab').style.display = show?'':'none';
}
function renderModePicker(){
  showChrome(false);
  var wrap=document.getElementById('wrap');
  wrap.innerHTML =
    '<div class="mode-pick">'+
      '<div class="mode-card" data-pick="learning"><div class="mode-icon">📘</div><h3>Learning Sheet</h3>'+
      '<p>Work through each question step by step with instant feedback — two tries, then the correct value is revealed right there so you can keep moving.</p></div>'+
      '<div class="mode-card" data-pick="quiz"><div class="mode-icon">📝</div><h3>Quiz Mode</h3>'+
      '<p>Attempt every question with no hints along the way. Your score and the full answer key are shown together once you finish the tab — just like the real exam.</p></div>'+
    '</div>';
  wrap.querySelectorAll('[data-pick]').forEach(function(card){
    card.addEventListener('click', function(){
      setMode(card.dataset.pick); activeTab='theory';
      document.getElementById('modePill').hidden=false;
      updateModePill();
      showChrome(true);
      buildTabbar();
      renderSlide();
    });
  });
}
document.getElementById('modePill').addEventListener('click', function(){
  if(!appState.mode){ return; }
  setMode(appState.mode==='quiz' ? 'learning' : 'quiz');
  updateModePill();
  showChrome(true);
  buildTabbar();
  renderSlide();
});

/* ================= boot ================= */
var _origRenderSlide = renderSlide;
renderSlide = function(){ _origRenderSlide(); updateChapterProgress(); updateModePill(); };


/* ================= theory tab ================= */
function renderTheory(){
  var wrap=document.getElementById('wrap');
  wrap.innerHTML='<div class="theory">'+fr(THEORY)+'</div>';
  document.querySelector('.slide-progress').style.display='none';
  document.querySelector('.navbar').style.display='none';
  document.getElementById('paletteFab').style.display='none';
  document.getElementById('secSub').textContent='Theory — notes, key ideas and worked examples';
  wrap.querySelectorAll('[data-go]').forEach(function(b){ b.addEventListener('click',function(){ activeTab=b.dataset.go; buildTabbar(); renderSlide(); window.scrollTo({top:0,behavior:'smooth'}); }); });
  wrap.querySelectorAll('[data-jump]').forEach(function(b){ b.addEventListener('click',function(){ var t=document.getElementById(b.dataset.jump); if(t) t.scrollIntoView({behavior:'smooth',block:'start'}); }); });
}
var _rsTheory = renderSlide;
renderSlide = function(){
  if(activeTab==='theory'){ renderTheory(); buildTabbar(); updateChapterProgress(); updateModePill(); saveState(); return; }
  document.querySelector('.slide-progress').style.display='';
  document.querySelector('.navbar').style.display='';
  document.getElementById('paletteFab').style.display='';
  _rsTheory();
};


/* ================= MYP criterion report ================= */
var CRIT_COL={A:'var(--accent-text)',B:'var(--gold)',C:'#8A6FC4',D:'#2F9AA0'};
function critStats(){
  return REPORT.map(function(r){
    var tabId=r[0], slides=SLIDES[tabId], ts=state&&state.tabs[tabId];
    var c=0,w=0,n=0;
    slides.forEach(function(sl,i){
      if(!ts||!ts.items[i]){ n++; return; }
      var it=ts.items[i];
      if(MODE==='learning'){
        if(it.status==='correct') c++; else if(it.status==='revealed') w++; else n++;
      } else {
        if(isSlideCorrect(tabId,i)) c++; else if(isSlideAttempted(tabId,i)) w++; else n++;
      }
    });
    var tot=slides.length, pct=tot?Math.round(c/tot*100):0;
    var lvl=Math.round(c/Math.max(tot,1)*8);
    return {tab:tabId,letter:r[1],name:r[2],c:c,w:w,n:n,tot:tot,pct:pct,lvl:lvl};
  });
}
function arcPath(cx,cy,r,a0,a1){
  if(a1-a0>=Math.PI*2-1e-6){ return 'M'+(cx-r)+','+cy+' a'+r+','+r+' 0 1,0 '+(2*r)+',0 a'+r+','+r+' 0 1,0 '+(-2*r)+',0 Z'; }
  var x0=cx+r*Math.sin(a0), y0=cy-r*Math.cos(a0), x1=cx+r*Math.sin(a1), y1=cy-r*Math.cos(a1);
  return 'M'+cx+','+cy+' L'+x0.toFixed(2)+','+y0.toFixed(2)+' A'+r+','+r+' 0 '+((a1-a0)>Math.PI?1:0)+',1 '+x1.toFixed(2)+','+y1.toFixed(2)+' Z';
}
function pieSVG(parts,size,hole,center,sub){
  var tot=parts.reduce(function(s,p){return s+p.v;},0), cx=size/2, cy=size/2, r=size/2-4, a=0, h='';
  if(!tot){ h+='<circle cx="'+cx+'" cy="'+cy+'" r="'+r+'" style="fill:var(--paper-2);stroke:var(--rule)"/>'; }
  parts.forEach(function(p){ if(!p.v) return; var b=a+p.v/tot*Math.PI*2; h+='<path d="'+arcPath(cx,cy,r,a,b)+'" style="fill:'+p.col+';stroke:var(--card);stroke-width:2"><title>'+esc(p.label)+': '+p.v+'</title></path>'; a=b; });
  if(hole) h+='<circle cx="'+cx+'" cy="'+cy+'" r="'+(r*hole)+'" style="fill:var(--card)"/>';
  if(center) h+='<text x="'+cx+'" y="'+(cy-(sub?4:0))+'" text-anchor="middle" dominant-baseline="middle" style="fill:var(--ink);font:700 '+(size>150?22:15)+'px Fraunces,serif">'+center+'</text>';
  if(sub) h+='<text x="'+cx+'" y="'+(cy+16)+'" text-anchor="middle" style="fill:var(--ink-soft);font:600 11px \'Source Sans 3\',sans-serif">'+sub+'</text>';
  return '<svg viewBox="0 0 '+size+' '+size+'" width="'+size+'" height="'+size+'" role="img">'+h+'</svg>';
}
function band(l){ return l===0?'0':(l<=2?'1–2':(l<=4?'3–4':(l<=6?'5–6':'7–8'))); }
function renderReport(){
  var st=critStats(), totC=0, totQ=0;
  st.forEach(function(s){ totC+=s.c; totQ+=s.tot; });
  var h='<div class="theory">';
  h+='<section class="note"><h2>Chapter test report</h2><p class="lt">'+(MODE==='quiz'?'<b>Quiz mode</b> results: answers are marked when you finish each test tab.':'<b>Learning mode</b> results: a question counts as correct only if you got it without the answer being revealed. Switch to Quiz mode for an exam-style score.')+'</p>';
  h+='<div class="rep-top"><div class="rep-pie">'+pieSVG(st.map(function(s){return {v:s.c,col:CRIT_COL[s.letter],label:'Criterion '+s.letter};}),200,0.55,totC+'/'+totQ,'correct')+'</div>';
  h+='<div class="rep-legend"><div class="rep-cap">Marks earned, by criterion</div>'+st.map(function(s){ return '<div class="rep-li"><span class="sw" style="background:'+CRIT_COL[s.letter]+'"></span><b>'+s.letter+'</b>&nbsp;'+esc(s.name)+'<span class="rep-n">'+s.c+' / '+s.tot+'</span></div>'; }).join('')+'</div></div></section>';
  h+='<div class="rep-grid">'+st.map(function(s){
    return '<div class="rep-card"><div class="rep-h"><span class="crit" style="background:'+CRIT_COL[s.letter]+'">'+s.letter+'</span>'+esc(s.name)+'</div>'+
      '<div class="rep-row">'+pieSVG([{v:s.c,col:'var(--success)',label:'Correct'},{v:s.w,col:'var(--danger)',label:'Incorrect'},{v:s.n,col:'var(--locked)',label:'Not attempted'}],120,0.5,s.pct+'%')+
      '<div class="rep-stats"><div><span class="sw" style="background:var(--success)"></span>Correct <b>'+s.c+'</b></div><div><span class="sw" style="background:var(--danger)"></span>Incorrect <b>'+s.w+'</b></div><div><span class="sw" style="background:var(--locked)"></span>Not attempted <b>'+s.n+'</b></div>'+
      '<div class="rep-lvl">Indicative level <b>'+s.lvl+'</b> / 8 <span>(band '+band(s.lvl)+')</span></div></div></div>'+
      '<button class="hub-btn" data-go="'+s.tab+'">Open Test '+s.letter+' →</button></div>';
  }).join('')+'</div>';
  h+='<p class="rep-note">Indicative level = fraction of questions correct × 8, rounded. It is a practice guide only; your teacher awards the real MYP criterion levels.</p></div>';
  var wrap=document.getElementById('wrap'); wrap.innerHTML=h;
  document.querySelector('.slide-progress').style.display='none';
  document.querySelector('.navbar').style.display='none';
  document.getElementById('paletteFab').style.display='none';
  document.getElementById('secSub').textContent='Report — chapter test results by MYP criterion';
  wrap.querySelectorAll('[data-go]').forEach(function(b){ b.addEventListener('click',function(){ activeTab=b.dataset.go; buildTabbar(); renderSlide(); window.scrollTo({top:0,behavior:'smooth'}); }); });
}
var _rsReport = renderSlide;
renderSlide = function(){
  if(activeTab==='report'){ renderReport(); buildTabbar(); updateChapterProgress(); updateModePill(); saveState(); return; }
  _rsReport();
};


/* ================= skipped-question return ================= */
function firstSkippedIdx(ts){
  for(var i=0;i<ts.items.length;i++){
    var it=ts.items[i];
    if(MODE==='quiz'){ if(!isSlideAttempted(activeTab,i)) return i; }
    else if(it.status==='skipped'||it.status==='unanswered') return i;
  }
  return -1;
}
function skippedList(ts){
  var out=[]; for(var i=0;i<ts.items.length;i++){ var it=ts.items[i];
    if(MODE==='quiz' ? !isSlideAttempted(activeTab,i) : (it.status==='skipped'||it.status==='unanswered')) out.push(i); }
  return out;
}
function renderSkipGate(ts){
  var list=skippedList(ts);
  var h='<div class="qcard done-card"><div class="big">⏭️</div><h2>You skipped '+list.length+' question'+(list.length>1?'s':'')+'</h2>'+
    '<p style="color:var(--ink-soft);font-size:14px;">Answer them now, or submit the tab as it is. Answers are marked only when you submit.</p>'+
    '<div class="skip-chips">'+list.map(function(i){ return '<button class="chip skip-go" data-i="'+i+'">Q'+(i+1)+'</button>'; }).join('')+'</div>'+
    '<div class="skip-btns"><button class="btn btn-primary" id="btnGoSkipped">Answer skipped questions</button><button class="btn" id="btnSubmitAnyway">Submit anyway</button></div></div>';
  document.getElementById('wrap').innerHTML=h;
  document.getElementById('navbarInner').innerHTML='';
  var go=function(i){ ts.idx=i; ts.maxReached=Math.max(ts.maxReached,i); renderSlide(); window.scrollTo({top:0,behavior:'smooth'}); };
  document.getElementById('btnGoSkipped').addEventListener('click',function(){ go(list[0]); });
  document.querySelectorAll('.skip-go').forEach(function(b){ b.addEventListener('click',function(){ go(parseInt(b.dataset.i,10)); }); });
  document.getElementById('btnSubmitAnyway').addEventListener('click',function(){ ts.submitOK=true; renderFinished(); ts.submitOK=false; });
  saveState();
}
var _rfSkip = renderFinished;
renderFinished = function(){
  var ts=state.tabs[activeTab];
  if(MODE==='quiz' && !ts.submitOK && skippedList(ts).length){ renderSkipGate(ts); return; }
  _rfSkip();
  if(MODE==='learning'){
    var list=skippedList(ts);
    if(list.length){
      var card=document.querySelector('.done-card');
      if(card){ var d=document.createElement('div'); d.className='skip-btns';
        d.innerHTML='<button class="btn btn-primary" id="btnGoSkipped">Attempt skipped questions ('+list.length+')</button>';
        card.appendChild(d);
        document.getElementById('btnGoSkipped').addEventListener('click',function(){ ts.idx=list[0]; ts.recorded=false; renderSlide(); window.scrollTo({top:0,behavior:'smooth'}); }); }
    }
  }
};


/* ================= approx answers (physics: within 1%) ================= */
var _amTools = answerMatches;
answerMatches = function(input,answer,accept,expr){
  if(expr==='approx'){
    var n1=parseNum(input); if(n1===null) return false;
    return [answer].concat(accept||[]).some(function(a){ var n2=parseNum(a); if(n2===null) return false; return Math.abs(n1-n2) <= Math.max(0.011*Math.abs(n2), 1e-9); });
  }
  return _amTools(input,answer,accept,expr);
};

/* ================= palette: every question already reached can be opened ================= */
statusOf = function(tabId,i){
  var ts=state.tabs[tabId];
  if(i>ts.maxReached) return 'locked';
  if(i===ts.idx) return 'current';
  var s=ts.items[i].status;
  if(s==='unanswered') return 'skipped';
  return s;
};

/* ================= on-screen keyboard ================= */
var KB={on:true, page:'num', target:null};
try{ var kbp=localStorage.getItem('sopaan-kb-pref'); if(kbp==='off') KB.on=false; }catch(e){}
function kbSave(){ try{ localStorage.setItem('sopaan-kb-pref', KB.on?'on':'off'); }catch(e){} }
var KEYS_NUM=[['7','8','9','(',')'],['4','5','6','−','/'],['1','2','3','.',','],['0',':','%','°','⌫'],['abc','←','→','Clear','Done']];
var KEYS_FRAC=[['7','8','9','/'],['4','5','6','−'],['1','2','3','space'],['0',',','⌫','Clear'],['abc','←','→','Done']];
var KEYS_ALG=[['7','8','9','x','y','n'],['4','5','6','+','−','a'],['1','2','3','×','÷','b'],['0','.','(',')','^','²'],['/','π','|','t','⌫','Clear'],['abc','←','→','Done']];
function kbLayoutFor(inp){ try{ var ts=state.tabs[activeTab], sl=SLIDES[activeTab][ts.idx], stp=sl.flat[parseInt(inp.dataset.step,10)]; var m=stp.expr, key=String(stp.a[inp.dataset.bkey]||'');
  if(m==='words'||m==='glist'||m==='angle') return 'abc'; if(m===true||m==='pow'||m==='primes') return 'alg';
  if(['fv','fe','fl','fm','fi','flist'].indexOf(m)>=0) return 'frac'; if(m==='dec'||m==='approx'||m==='dlist'||m==='set'||m==='coord'||m==='list'||m==='time') return 'num';
  if(/^[\-−]?\d+ \d+\/\d+$/.test(key)||/^[\-−]?\d+\/\d+$/.test(key)) return 'frac'; if(/[a-df-z]/i.test(key.replace(/pi/gi,''))) return /\d/.test(key)?'alg':'abc'; return 'num'; }catch(e){ return 'num'; } }
var KEYS_ABC=[['q','w','e','r','t','y','u','i','o','p'],['a','s','d','f','g','h','j','k','l','-'],['z','x','c','v','b','n','m',',',':','/'],['123','space','←','→','⌫','Done']];
function kbBuild(){
  var el=document.getElementById('vkb'); if(!el){ el=document.createElement('div'); el.id='vkb'; el.className='vkb'; document.body.appendChild(el);
    el.addEventListener('pointerdown',function(e){ var b=e.target.closest('button[data-k]'); e.preventDefault(); if(b) kbPress(b.dataset.k); });
    el.addEventListener('mousedown',function(e){ e.preventDefault(); }); }
  var rows={num:KEYS_NUM,frac:KEYS_FRAC,alg:KEYS_ALG,abc:KEYS_ABC}[KB.page]||KEYS_NUM;
  el.innerHTML='<div class="vkb-top"><span>⌨️ Keyboard</span><button data-k="device" class="vkb-link">Use device keyboard</button></div>'+
    rows.map(function(r){ return '<div class="vkb-row">'+r.map(function(k){
      var cls='vkb-k'+(/^(abc|123|Done|Clear|⌫|←|→|space)$/.test(k)?' fn':'')+(k==='Done'?' done':'');
      return '<button type="button" class="'+cls+'" data-k="'+k+'">'+(k==='space'?'space':k)+'</button>'; }).join('')+'</div>'; }).join('');
  return el;
}
function kbShow(inp){ KB.target=inp; KB.home=kbLayoutFor(inp); KB.page=KB.home; if(!KB.on) return; var cp=document.getElementById('calcPanel'); if(cp&&cp.classList.contains('show')) return; var el=kbBuild(); var nb=document.querySelector('.navbar'); el.style.bottom=(nb?nb.getBoundingClientRect().height:0)+'px'; el.classList.add('show'); document.body.classList.add('kb-open'); setTimeout(function(){ var r=inp.getBoundingClientRect(), top=el.getBoundingClientRect().top; if(r.bottom>top-12) window.scrollBy({top:r.bottom-top+60,behavior:'smooth'}); else if(r.top<60) window.scrollBy({top:r.top-80,behavior:'smooth'}); },30); }
function kbHide(){ var el=document.getElementById('vkb'); if(el) el.classList.remove('show'); document.body.classList.remove('kb-open'); }
function kbInsert(s){
  var t=KB.target; if(!t||t.disabled) return;
  var a=t.selectionStart==null?t.value.length:t.selectionStart, b=t.selectionEnd==null?a:t.selectionEnd;
  t.value=t.value.slice(0,a)+s+t.value.slice(b); var p=a+s.length; try{ t.setSelectionRange(p,p); }catch(e){}
  t.dispatchEvent(new Event('input',{bubbles:true}));
}
function kbPress(k){
  var t=KB.target; if(k==='device'){ KB.on=false; kbSave(); kbHide(); document.querySelectorAll('.blank-input').forEach(function(i){ i.removeAttribute('inputmode'); }); if(t){ t.blur(); setTimeout(function(){ t.focus(); },50); } showToast('Device keyboard on. Tap ⌨️ on any blank to bring the on-screen keyboard back.'); return; }
  if(k==='Done'){ kbHide(); if(t) t.blur(); return; }
  if(k==='abc'||k==='123'){ KB.page=(k==='abc')?'abc':(KB.home&&KB.home!=='abc'?KB.home:'num'); kbBuild(); return; }
  if(!t) return;
  if(k==='⌫'){ var a=t.selectionStart, b=t.selectionEnd; if(a===b&&a>0){ t.value=t.value.slice(0,a-1)+t.value.slice(b); try{t.setSelectionRange(a-1,a-1);}catch(e){} } else { t.value=t.value.slice(0,a)+t.value.slice(b); try{t.setSelectionRange(a,a);}catch(e){} } t.dispatchEvent(new Event('input',{bubbles:true})); return; }
  if(k==='Clear'){ t.value=''; t.dispatchEvent(new Event('input',{bubbles:true})); return; }
  if(k==='←'||k==='→'){ var p=(t.selectionStart||0)+(k==='←'?-1:1); p=Math.max(0,Math.min(t.value.length,p)); try{t.setSelectionRange(p,p);}catch(e){} return; }
  var map={'−':'-','space':' '}; kbInsert(map[k]!==undefined?map[k]:k);
}
function kbWire(){
  document.querySelectorAll('.blank-input').forEach(function(inp){
    if(inp.dataset.kb) return; inp.dataset.kb='1';
    if(KB.on) inp.setAttribute('inputmode','none');
    inp.addEventListener('focus',function(){ kbShow(inp); });
    var btn=document.createElement('button'); btn.type='button'; btn.className='kb-toggle'; btn.title='On-screen keyboard'; btn.textContent='⌨️'; btn.tabIndex=-1;
    btn.addEventListener('mousedown',function(e){ e.preventDefault(); });
    btn.addEventListener('click',function(){ KB.on=true; kbSave(); document.querySelectorAll('.blank-input').forEach(function(i){ i.setAttribute('inputmode','none'); }); inp.focus(); kbShow(inp); });
    if(!inp.disabled) inp.insertAdjacentElement('afterend',btn);
  });
}
document.addEventListener('focusout',function(e){ setTimeout(function(){ var a=document.activeElement; if(!a||!a.classList||!a.classList.contains('blank-input')){ if(!document.querySelector('#vkb:hover')) kbHide(); } },120); });

/* ================= calculator ================= */
var CALC={expr:'', ans:0};
function calcEval(src){
  var s=String(src).replace(/×/g,'*').replace(/÷/g,'/').replace(/−/g,'-').replace(/π/g,'(PI)').replace(/Ans/g,'('+CALC.ans+')').replace(/\^/g,'**').replace(/√\(/g,'sqrt(').replace(/²/g,'**2').replace(/E/g,'*10**');
  s=s.replace(/(^|[(*\/+\-,])-/g,'$1(-1)*');
  if(/[^0-9+\-*/().,a-z A-Z]/.test(s)) throw 0;
  var ok=s.replace(/sin|cos|tan|asin|acos|atan|sqrt|log|ln|PI|abs/g,''); if(/[a-zA-Z]/.test(ok)) throw 0;
  var f=new Function('sin','cos','tan','asin','acos','atan','sqrt','log','ln','PI','abs','return ('+s+');');
  var d=Math.PI/180;
  var v=f(function(x){return Math.sin(x*d);},function(x){return Math.cos(x*d);},function(x){return Math.tan(x*d);},
    function(x){return Math.asin(x)/d;},function(x){return Math.acos(x)/d;},function(x){return Math.atan(x)/d;},Math.sqrt,Math.log10,Math.log,Math.PI,Math.abs);
  if(typeof v!=='number'||!isFinite(v)) throw 0; return v;
}
function fmtNum(v){ if(Math.abs(v)>=1e10||(Math.abs(v)<1e-6&&v!==0)) return v.toExponential(6).replace(/\.?0+e/,'e'); return String(parseFloat(v.toPrecision(10))); }
var CKEYS=[['sin(','cos(','tan(','√(','^','²'],['asin(','acos(','atan(','(',')','π'],['7','8','9','÷','⌫','AC'],['4','5','6','×','E','Ans'],['1','2','3','−','(−)','Insert'],['0','.','=','+']];
function openCalc(){
  var p=document.getElementById('calcPanel');
  if(!p){ p=document.createElement('div'); p.id='calcPanel'; p.className='tool-panel calc';
    p.innerHTML='<div class="tp-head"><b>🧮 Calculator</b><span class="tp-note">degrees · tap a blank, then Insert</span><button class="tp-x" data-c="close">✕</button></div>'+
      '<div class="calc-disp"><div class="calc-expr" id="calcExpr"></div><div class="calc-res" id="calcRes">0</div></div>'+
      '<div class="calc-keys">'+CKEYS.map(function(r){ return r.map(function(k){ return '<button type="button" data-c="'+k+'" class="'+(k==='='?'eq':(/^(AC|⌫|Insert)$/.test(k)?'fn':''))+'">'+({'sin(':'sin','cos(':'cos','tan(':'tan','asin(':'sin⁻¹','acos(':'cos⁻¹','atan(':'tan⁻¹','√(':'√'}[k]||k)+'</button>'; }).join(''); }).join('')+'</div>';
    document.body.appendChild(p);
    p.addEventListener('mousedown',function(e){ if(e.target.closest('button')) e.preventDefault(); });
    p.addEventListener('click',function(e){ var b=e.target.closest('button[data-c]'); if(!b) return; calcKey(b.dataset.c); });
  }
  kbHide(); var nb=document.querySelector('.navbar'); p.style.bottom=((nb?nb.getBoundingClientRect().height:0)+8)+'px'; p.classList.add('show'); document.body.classList.add('calc-open'); calcShow();
}
function calcShow(res){ document.getElementById('calcExpr').textContent=CALC.expr||' '; if(res!==undefined) document.getElementById('calcRes').textContent=res; }
function calcKey(k){
  if(k==='close'){ document.getElementById('calcPanel').classList.remove('show'); document.body.classList.remove('calc-open'); return; }
  if(k==='AC'){ CALC.expr=''; calcShow('0'); return; }
  if(k==='⌫'){ CALC.expr=CALC.expr.replace(/(asin\(|acos\(|atan\(|sin\(|cos\(|tan\(|√\(|Ans|.)$/,''); calcShow(); return; }
  if(k==='='){ try{ var v=calcEval(CALC.expr); CALC.ans=v; calcShow(fmtNum(v)); }catch(e){ calcShow('Error'); } return; }
  if(k==='(−)'){ CALC.expr+='−'; calcShow(); return; }
  if(k==='Insert'){ var r=document.getElementById('calcRes').textContent; if(KB.target && !KB.target.disabled && r!=='Error'){ KB.target.value=r; KB.target.dispatchEvent(new Event('input',{bubbles:true})); showToast('Inserted '+r+' into the blank.'); } else showToast('Tap a blank first, then press Insert.'); return; }
  CALC.expr+=k; calcShow();
}

/* ================= Desmos ================= */
var DESMOS_KEY='dcb31709b452b1cf9dc26972add0fda6', desmosCalc=null, desmosLoading=false;
function openDesmos(exprs){
  var p=document.getElementById('desmosPanel');
  if(!p){ p=document.createElement('div'); p.id='desmosPanel'; p.className='tool-panel desmos';
    p.innerHTML='<div class="tp-head"><b>📈 Desmos graphing calculator</b><button class="tp-x" id="desmosReset">Reset graph</button><button class="tp-x" id="desmosClose">✕</button></div><div id="desmosBox"><div class="desmos-msg">Loading Desmos…</div></div>';
    document.body.appendChild(p);
    document.getElementById('desmosClose').addEventListener('click',function(){ p.classList.remove('show'); });
    document.getElementById('desmosReset').addEventListener('click',function(){ if(desmosCalc) desmosSet(p._exprs||[]); });
  }
  p._exprs=exprs||[]; p.classList.add('show');
  if(window.Desmos){ desmosInit(); desmosSet(p._exprs); return; }
  if(desmosLoading) return; desmosLoading=true;
  var sc=document.createElement('script'); sc.src='https://www.desmos.com/api/v1.9/calculator.js?apiKey='+DESMOS_KEY;
  sc.onload=function(){ desmosInit(); desmosSet(p._exprs); };
  sc.onerror=function(){ desmosLoading=false; document.getElementById('desmosBox').innerHTML='<div class="desmos-msg">Desmos needs an internet connection. <a href="https://www.desmos.com/calculator" target="_blank" rel="noopener">Open Desmos in a new tab</a>.</div>'; };
  document.head.appendChild(sc);
}
function desmosInit(){ if(desmosCalc) return; var box=document.getElementById('desmosBox'); box.innerHTML=''; desmosCalc=Desmos.GraphingCalculator(box,{expressionsCollapsed:false,settingsMenu:false,border:false,degreeMode:true}); }
function desmosSet(exprs){ if(!desmosCalc) return; desmosCalc.setBlank(); (exprs||[]).forEach(function(e,i){ if(typeof e==='string') desmosCalc.setExpression({id:'e'+i,latex:e}); else desmosCalc.setExpression(Object.assign({id:'e'+i},e)); }); }

/* ================= toolbar on each question ================= */
var _rsTools = renderSlide;
renderSlide = function(){
  _rsTools();
  kbHide();
  if(activeTab==='theory'||activeTab==='report') return;
  var ts=state.tabs[activeTab]; if(!ts) return;
  var slide=SLIDES[activeTab][ts.idx], card=document.querySelector('#wrap .qcard');
  if(card && slide && slide.tools && slide.tools.length && !card.querySelector('.tool-bar')){
    var bar=document.createElement('div'); bar.className='tool-bar';
    bar.innerHTML=(slide.tools.indexOf('calc')>=0?'<button type="button" class="tool-btn" data-t="calc">🧮 Calculator</button>':'')+
                  (slide.tools.indexOf('desmos')>=0?'<button type="button" class="tool-btn" data-t="desmos">📈 Desmos graph</button>':'');
    card.insertBefore(bar, card.firstChild);
    bar.addEventListener('click',function(e){ var b=e.target.closest('[data-t]'); if(!b) return; if(b.dataset.t==='calc') openCalc(); else openDesmos(slide.desmos||[]); });
  }
  kbWire();
};



/* ================= signed fractions in text: {−3/4}, {3/−4}, {−2 1/3}, {p/q} ================= */
fr = function(s){ return String(s).replace(/&lt;(\/?)(b|sup|sub|i)>/g,'<$1$2>')
  .replace(/\{([−-]?\d+) (\d+)\/(\d+)\}/g,'<span class="mx">$1<span class="fq"><span>$2</span><span>$3</span></span></span>')
  .replace(/\{([−-]?[A-Za-z0-9]+)\/([−-]?[A-Za-z0-9]+)\}/g,'<span class="fq"><span>$1</span><span>$2</span></span>'); };
/* ================= BMA badge → main page of this sheet (theory hub) ================= */
(function(){
  var c=document.querySelector('.brand .crest'); if(!c) return;
  var a=document.createElement('button'); a.type='button'; a.className='crest crest-home'; a.title='Back to the main page (theory notes)'; a.setAttribute('aria-label','Main page');
  a.innerHTML='BM<span class="crest-h">⌂</span>'; c.parentNode.replaceChild(a,c);
  a.addEventListener('click',function(){
    if(!student||!MODE){ window.scrollTo({top:0,behavior:'smooth'}); return; }
    if(typeof kbHide==='function') kbHide(); if(typeof SP!=='undefined'&&SP.on) spToggle(false);
    var cp=document.getElementById('calcPanel'); if(cp) cp.classList.remove('show'); document.body.classList.remove('calc-open');
    activeTab = (typeof THEORY!=='undefined') ? 'theory' : TAB_DEFS[0].id;
    buildTabbar(); renderSlide(); window.scrollTo({top:0,behavior:'smooth'});
  });
})();

/* ================= session clock: starts at sign-in and keeps running ================= */
var CLK={t0:null};
(function(){
  var row=document.querySelector('.brand .brand-row'); if(!row) return;
  var d=document.createElement('div'); d.className='bmasw off'; d.id='swBox'; d.title='Time since you signed in';
  d.innerHTML='<span class="bmasw-ic">⏱</span><span class="bmasw-t" id="swT">00:00</span>';
  row.appendChild(d); setInterval(swTick,1000);
})();
function swFmt(s){ s=Math.floor(s||0); var h=Math.floor(s/3600), m=Math.floor(s%3600/60), x=s%60; return (h?h+':'+String(m).padStart(2,'0'):String(m).padStart(2,'0'))+':'+String(x).padStart(2,'0'); }
function swTick(){
  var box=document.getElementById('swBox'); if(!box) return;
  if(student && !CLK.t0) CLK.t0=Date.now();
  if(!student) CLK.t0=null;
  box.classList.toggle('off',!CLK.t0);
  document.getElementById('swT').textContent = CLK.t0 ? swFmt((Date.now()-CLK.t0)/1000) : '00:00';
}
function swTab(){ try{ if(!state||!state.tabs||activeTab==='theory'||activeTab==='report') return null; return state.tabs[activeTab]||null; }catch(e){ return null; } }
var _rsSW = renderSlide;
renderSlide = function(){ _rsSW(); swTick(); };
var _rfSW = renderFinished;
renderFinished = function(){ _rfSW(); var done=document.querySelector('#wrap .done-card'); if(CLK.t0 && done && !done.querySelector('.bmasw-done')){ var p=document.createElement('p'); p.className='bmasw-done'; p.textContent='⏱ Time since sign-in: '+swFmt((Date.now()-CLK.t0)/1000); var h2=done.querySelector('h2'); if(h2) h2.insertAdjacentElement('afterend',p); else done.appendChild(p); } };

/* ================= scratchpad (Khan-style, 4 pens) ================= */
var SP={on:false, draw:true, color:'ink', size:3, erase:false, store:{}, key:null, cv:null, ctx:null, down:false, last:null};
var SP_COL={ink:null, blue:'#2563EB', red:'#DC2626', green:'#16A34A'};
function spInk(){ return getComputedStyle(document.documentElement).getPropertyValue('--ink').trim()||'#211E1A'; }
function spKey(){ var ts=swTab(); return ts ? (MODE+'|'+activeTab+'|'+ts.idx) : null; }
function spBuild(){
  if(SP.cv) return;
  var cv=document.createElement('canvas'); cv.id='spCanvas'; cv.className='sp-canvas'; document.body.appendChild(cv);
  var bar=document.createElement('div'); bar.id='spBar'; bar.className='sp-bar';
  bar.innerHTML='<span class="sp-lbl">✏️ Scratchpad</span>'+
    ['ink','blue','red','green'].map(function(c){ return '<button type="button" class="sp-pen" data-c="'+c+'" title="'+(c==='ink'?'black':c)+' pen"><i style="background:'+(c==='ink'?'var(--ink)':SP_COL[c])+'"></i></button>'; }).join('')+
    '<button type="button" class="sp-tool" data-t="erase" title="Eraser">🧽</button><button type="button" class="sp-tool" data-t="size" title="Pen size">●</button><button type="button" class="sp-tool" data-t="scroll" title="Pause drawing to scroll or answer">✋</button>'+
    '<button type="button" class="sp-tool" data-t="clear" title="Clear page">🗑</button><button type="button" class="sp-tool" data-t="close" title="Close scratchpad">✕</button>';
  document.body.appendChild(bar);
  bar.addEventListener('click',function(e){ var b=e.target.closest('button'); if(!b) return;
    if(b.dataset.c){ SP.color=b.dataset.c; SP.erase=false; SP.draw=true; }
    else if(b.dataset.t==='erase'){ SP.erase=true; SP.draw=true; }
    else if(b.dataset.t==='size'){ SP.size = SP.size===3?6:(SP.size===6?1.5:3); b.textContent = SP.size===6?'⬤':(SP.size===1.5?'·':'●'); }
    else if(b.dataset.t==='scroll'){ SP.draw=!SP.draw; }
    else if(b.dataset.t==='clear'){ spClear(); }
    else if(b.dataset.t==='close'){ spToggle(false); return; }
    spUI(); });
  SP.cv=cv; SP.ctx=cv.getContext('2d');
  cv.addEventListener('pointerdown',function(e){ if(!SP.draw) return; e.preventDefault(); cv.setPointerCapture(e.pointerId); SP.down=true; SP.last=spPt(e); spDot(SP.last); });
  cv.addEventListener('pointermove',function(e){ if(!SP.down) return; e.preventDefault(); var p=spPt(e); spLine(SP.last,p); SP.last=p; });
  var up=function(){ if(SP.down){ SP.down=false; spSave(); } };
  cv.addEventListener('pointerup',up); cv.addEventListener('pointercancel',up); cv.addEventListener('pointerleave',up);
  window.addEventListener('resize',function(){ if(SP.on) spFit(true); });
}
function spPt(e){ var r=SP.cv.getBoundingClientRect(); return {x:e.clientX-r.left, y:e.clientY-r.top}; }
function spStyle(){ var c=SP.ctx; c.lineCap='round'; c.lineJoin='round'; c.globalCompositeOperation=SP.erase?'destination-out':'source-over'; c.strokeStyle=c.fillStyle=(SP.color==='ink'?spInk():SP_COL[SP.color]); c.lineWidth=SP.erase?22:SP.size; }
function spDot(p){ spStyle(); var c=SP.ctx; c.beginPath(); c.arc(p.x,p.y,(SP.erase?11:SP.size/2),0,Math.PI*2); c.fill(); }
function spLine(a,b){ spStyle(); var c=SP.ctx; c.beginPath(); c.moveTo(a.x,a.y); c.lineTo(b.x,b.y); c.stroke(); }
function spSave(){ if(SP.key&&SP.cv){ try{ SP.store[SP.key]=SP.cv.toDataURL(); }catch(e){} } }
function spClear(){ if(!SP.ctx) return; SP.ctx.save(); SP.ctx.setTransform(1,0,0,1,0,0); SP.ctx.clearRect(0,0,SP.cv.width,SP.cv.height); SP.ctx.restore(); if(SP.key) delete SP.store[SP.key]; }
function spFit(keep){
  var wrap=document.getElementById('wrap'); if(!wrap||!SP.cv) return;
  var r=wrap.getBoundingClientRect(), top=r.top+window.scrollY, h=Math.max(wrap.scrollHeight, window.innerHeight-r.top)+40, w=document.documentElement.clientWidth;
  var old=keep&&SP.key?SP.store[SP.key]:null, dpr=window.devicePixelRatio||1;
  SP.cv.style.top=top+'px'; SP.cv.style.left='0px'; SP.cv.style.width=w+'px'; SP.cv.style.height=h+'px';
  SP.cv.width=Math.round(w*dpr); SP.cv.height=Math.round(h*dpr); SP.ctx.setTransform(dpr,0,0,dpr,0,0);
  if(old){ var im=new Image(); im.onload=function(){ SP.ctx.save(); SP.ctx.setTransform(1,0,0,1,0,0); SP.ctx.drawImage(im,0,0); SP.ctx.restore(); }; im.src=old; }
}
function spLoad(){ spSave(); SP.key=spKey(); spFit(false); var d=SP.key&&SP.store[SP.key]; if(d){ var im=new Image(); im.onload=function(){ SP.ctx.save(); SP.ctx.setTransform(1,0,0,1,0,0); SP.ctx.drawImage(im,0,0); SP.ctx.restore(); }; im.src=d; } }
function spUI(){
  var bar=document.getElementById('spBar'); if(!bar) return;
  bar.querySelectorAll('.sp-pen').forEach(function(b){ b.classList.toggle('on', !SP.erase && SP.draw && b.dataset.c===SP.color); });
  bar.querySelector('[data-t=erase]').classList.toggle('on', SP.erase && SP.draw);
  bar.querySelector('[data-t=scroll]').classList.toggle('on', !SP.draw);
  SP.cv.classList.toggle('passive', !SP.draw);
  var fb=document.getElementById('spFab'); if(fb) fb.classList.toggle('on',SP.on);
}
function spToggle(on){
  spBuild(); SP.on=(on===undefined)?!SP.on:on;
  document.body.classList.toggle('sp-open',SP.on); SP.cv.style.display=SP.on?'block':'none'; document.getElementById('spBar').style.display=SP.on?'flex':'none';
  if(SP.on){ SP.draw=true; SP.erase=false; spLoad(); if(typeof kbHide==='function') kbHide(); } else { spSave(); }
  spUI();
}
(function(){ var f=document.createElement('button'); f.type='button'; f.id='spFab'; f.className='sp-fab'; f.innerHTML='✏️ <span>Scratchpad</span>'; f.title='Open a scratchpad to write your working'; f.addEventListener('click',function(){ spToggle(); }); document.body.appendChild(f); })();
var _rsSP = renderSlide;
renderSlide = function(){ _rsSP(); var fab=document.getElementById('spFab'); var q=!!swTab(); if(fab) fab.style.display=q?'':'none'; if(!q && SP.on) spToggle(false); if(SP.on) setTimeout(spLoad,30); };

renderLogin();
})();
</script>
</body>
</html>
