<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Cabiao Senior High School Clinic Health Information System</title>
<style>
:root{--bg:#eef2ea;--surface:#fff;--ink:#1d2a1f;--muted:#5c6b5e;--line:#d5dccf;--green:#4a6b43;--green-d:#364f31;--warn:#b45309;--warn-bg:#fdf0dc;--bad:#b42318;--bad-bg:#fde8e6;--ok-bg:#e3efdf;box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px)}
@media (prefers-color-scheme:dark){:root:not([data-theme="light"]){--bg:#141b15;--surface:#1d261e;--ink:#e8efe6;--muted:#9fb0a0;--line:#2f3d30;--green:#7fa876;--green-d:#2f4a2a;--warn:#f0b35a;--warn-bg:#3a2d14;--bad:#f28b82;--bad-bg:#3d1d1a;--ok-bg:#223523;color-scheme:dark}}
:root[data-theme="dark"]{--bg:#141b15;--surface:#1d261e;--ink:#e8efe6;--muted:#9fb0a0;--line:#2f3d30;--green:#7fa876;--green-d:#2f4a2a;--warn:#f0b35a;--warn-bg:#3a2d14;--bad:#f28b82;--bad-bg:#3d1d1a;--ok-bg:#223523;color-scheme:dark}
*{box-sizing:border-box}
html{scroll-padding-top:env(safe-area-inset-top,0px)}
body{margin:0;background:var(--bg);color:var(--ink);font:15px/1.5 "Segoe UI",system-ui,-apple-system,sans-serif}
h1,h2,h3{font-family:Georgia,"Times New Roman",serif;margin:0}
button,input,select,textarea{font:inherit;color:inherit}
button:focus-visible,input:focus-visible,select:focus-visible,textarea:focus-visible{outline:3px solid var(--green);outline-offset:2px}
.hidden{display:none!important}
/* login */
#login{min-height:100vh;display:grid;grid-template-columns:minmax(0,1fr) minmax(0,1.1fr);background:linear-gradient(120deg,var(--green-d),var(--green))}
.welcome{padding:48px;color:#fff;align-self:center}
.welcome h2{font-size:44px;font-style:italic;font-weight:400}
.welcome p{max-width:280px;opacity:.9}
.card{background:var(--surface);margin:24px;border-radius:28px;padding:36px 32px;display:flex;flex-direction:column;align-items:center;justify-content:center;text-align:center}
.logo{width:120px;height:120px;border-radius:50%;object-fit:cover;background:#fff;margin-bottom:12px}
.card .school{font-size:13px;letter-spacing:.04em;color:var(--muted);font-weight:600}
.card h1{font-size:34px;line-height:1.05;color:var(--green-d);font-weight:800;margin:4px 0}
@media (prefers-color-scheme:dark){:root:not([data-theme="light"]) .card h1{color:var(--green)}}
.card .sub{font-weight:700;color:var(--green-d);margin-bottom:18px}
.field{width:100%;max-width:340px;text-align:left;margin-bottom:12px}
.field label{display:block;font-size:12px;font-weight:700;color:var(--muted);margin-bottom:4px}
.field input,.field select,.field textarea,.search{width:100%;padding:11px 14px;border:1px solid var(--line);border-radius:12px;background:var(--bg)}
.pw{position:relative}.pw button{position:absolute;right:8px;top:50%;transform:translateY(-50%);border:0;background:none;cursor:pointer;color:var(--muted);padding:6px}
.btn{border:0;border-radius:999px;background:var(--green-d);color:#fff;padding:11px 22px;font-weight:700;cursor:pointer}
.btn.wide{width:100%;max-width:340px;padding:13px}
.btn.alt{background:transparent;color:var(--ink);border:1px solid var(--line)}
.btn.sm{padding:6px 12px;font-size:13px}
.btn.danger{background:var(--bad-bg);color:var(--bad)}
.err{color:var(--bad);font-size:13px;min-height:20px;margin:4px 0}
.hint{font-size:12px;color:var(--muted);margin-top:10px}
@media(max-width:760px){#login{grid-template-columns:1fr}.welcome{padding:28px 28px 0}.welcome h2{font-size:34px}}
/* app */
header.top{background:var(--green-d);color:#fff;display:flex;align-items:center;gap:14px;padding:12px 20px;flex-wrap:wrap}
header.top b{font-family:Georgia,serif;font-size:18px;flex:1;min-width:200px}
nav{display:flex;gap:6px}
nav button{background:transparent;border:0;color:#fff;padding:8px 14px;border-radius:999px;cursor:pointer;opacity:.8}
nav button.on{background:rgba(255,255,255,.18);opacity:1;font-weight:700}
main{max-width:1060px;margin:0 auto;padding:22px 18px 60px}
.stats{display:grid;grid-template-columns:repeat(auto-fit,minmax(190px,1fr));gap:14px;margin-bottom:22px}
.stat{background:var(--surface);border:1px solid var(--line);border-radius:14px;padding:16px 18px}
.stat b{display:block;font-family:Georgia,serif;font-size:32px}
.stat span{color:var(--muted);font-size:13px}
.bar{display:flex;gap:10px;align-items:center;margin:14px 0;flex-wrap:wrap}
.bar h2{flex:1;font-size:24px}.search{max-width:260px}
.panel{background:var(--surface);border:1px solid var(--line);border-radius:14px;padding:18px;margin-bottom:18px}
.grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(200px,1fr));gap:12px}
.grid .field{max-width:none;margin:0}
.scroll{overflow-x:auto;background:var(--surface);border:1px solid var(--line);border-radius:14px}
table{border-collapse:collapse;width:100%;min-width:640px}
th,td{text-align:left;padding:10px 14px;border-bottom:1px solid var(--line);vertical-align:middle}
th{font-size:13px;color:var(--muted);font-weight:600}
tr:last-child td{border-bottom:0}
.tag{display:inline-block;padding:2px 10px;border-radius:999px;font-size:12px;font-weight:700;background:var(--ok-bg);color:var(--green)}
.tag.low{background:var(--warn-bg);color:var(--warn)}.tag.out{background:var(--bad-bg);color:var(--bad)}
.qty{display:inline-flex;align-items:center;gap:6px}
.qty button{width:26px;height:26px;border-radius:50%;border:1px solid var(--line);background:var(--bg);cursor:pointer}
.empty{padding:30px;text-align:center;color:var(--muted)}
.detail dl{display:grid;grid-template-columns:150px 1fr;gap:6px 14px;margin:12px 0}
.detail dt{color:var(--muted)}.detail dd{margin:0}
.sheetT{min-width:1300px}.sheetT th,.sheetT td{border:1px solid var(--line);white-space:nowrap;font-size:14px;padding:8px 12px}.sheetT th{background:var(--ok-bg);color:var(--ink)}.sheetT .rn{background:var(--ok-bg);color:var(--muted);text-align:center}
.sf{max-width:760px;margin:0 auto;padding:28px 18px 60px}.sf h2{font-size:28px;color:var(--green-d)}.sf .panel p{color:var(--muted)}
@media (prefers-color-scheme:dark){:root:not([data-theme="light"]) .sf h2{color:var(--green)}}
.toast{position:fixed;bottom:calc(20px + env(safe-area-inset-bottom,0px));left:50%;transform:translateX(-50%);background:var(--green-d);color:#fff;padding:10px 18px;border-radius:999px;z-index:20}
</style>
</head>
<body>

<section id="login">
  <div class="welcome">
    <h2>Welcome!</h2>
    <p>Please log in to access the clinic health information system.</p>
  </div>
  <div class="card">
    <img class="logo" src="LOGO_DATA_URI_DITO" alt="Cabiao Senior High School logo">
    <div class="school">CABIAO SENIOR HIGH SCHOOL</div>
    <h1>CLINIC HEALTH</h1>
    <div class="sub">INFORMATION SYSTEM</div>
    <div class="field"><label for="u">USERNAME</label><input id="u" autocomplete="username" placeholder="Enter your username"></div>
    <div class="field"><label for="p">PASSWORD</label>
      <div class="pw"><input id="p" type="password" autocomplete="current-password" placeholder="Enter your password"><button type="button" id="eye" aria-label="Show password">Show</button></div>
    </div>
    <div class="err" id="err" role="alert"></div>
    <button class="btn wide" id="go">LOGIN</button>
    <button class="btn alt wide" id="tostu" style="margin-top:12px">Student? Fill in your health form</button>
