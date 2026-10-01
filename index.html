<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Sign in to Questlog</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Chakra+Petch:wght@500;700&family=Barlow:wght@400;500;600&display=swap" rel="stylesheet">
<style>
:root{--bg:#e9eff7;--panel:#fff;--ink:#0f1b2d;--mute:#56677f;--line:#d0dbe8;--amb:#f59e0b;--teal:#0d9488;--late:#c81e3a;--soft:#f3f7fb;
box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px)}
@media (prefers-color-scheme:dark){:root:not([data-theme="light"]){--bg:#0a1322;--panel:#13213a;--ink:#eaf1ff;--mute:#93a7c8;--line:#263a5e;--teal:#2dd4bf;--late:#fb7185;--soft:#0f1b31}}
:root[data-theme="dark"]{--bg:#0a1322;--panel:#13213a;--ink:#eaf1ff;--mute:#93a7c8;--line:#263a5e;--teal:#2dd4bf;--late:#fb7185;--soft:#0f1b31}
*,*::before,*::after{box-sizing:inherit}
body{margin:0;min-height:100vh;display:grid;place-items:center;background:var(--bg);color:var(--ink);font:400 17px/1.45 Barlow,"Segoe UI",sans-serif;padding:16px}
.box{width:100%;max-width:400px;background:var(--panel);border:1px solid var(--line);border-radius:18px;padding:26px;border-top:6px solid var(--amb)}
h1{font:700 32px "Chakra Petch","Trebuchet MS",sans-serif;margin:0 0 4px}
.sub{color:var(--mute);margin:0 0 18px}
.tabs{display:grid;grid-template-columns:1fr 1fr;gap:6px;margin-bottom:16px}
.tab{background:var(--soft);border:1px solid var(--line);border-radius:10px;padding:8px;font:700 15px "Chakra Petch",sans-serif;color:var(--mute);cursor:pointer}
.tab[aria-pressed="true"]{background:var(--ink);color:var(--bg);border-color:var(--ink)}
form{display:grid;gap:12px}
label{display:grid;gap:4px;color:var(--mute);font-weight:500}
input[type=text],input[type=password]{font:inherit;color:var(--ink);background:var(--soft);border:1px solid var(--line);border-radius:8px;padding:10px;width:100%}
input:focus-visible,button:focus-visible{outline:3px solid var(--teal);outline-offset:2px}
.chk{display:flex;gap:8px;align-items:center;color:var(--ink)}
.btn{background:var(--amb);color:#0f1b2d;border:0;border-radius:10px;padding:12px;font:700 17px "Chakra Petch",sans-serif;cursor:pointer}
.btn:disabled{opacity:.6;cursor:wait}
#e{color:var(--late);min-height:1.4em;margin:0;font-weight:600}
.fine{color:var(--mute);font-size:14px;margin:14px 0 0}
</style>
</head>
<body>
<main class="box">
  <h1>Questlog</h1>
  <p class="sub" id="sub">Sign in to open your schedule.</p>
  <div class="tabs">
    <button class="tab" type="button" data-m="in" aria-pressed="true">Sign in</button>
    <button class="tab" type="button" data-m="up" aria-pressed="false">Create account</button>
  </div>
  <form id="f">
    <label>Username<input id="u" type="text" autocomplete="username" maxlength="20" required></label>
    <label>Password<input id="p" type="password" autocomplete="current-password" minlength="6" required></label>
    <label id="cw" hidden>Confirm password<input id="c" type="password" autocomplete="new-password"></label>
    <label class="chk"><input id="r" type="checkbox" checked> Keep me signed in on this device</label>
    <p id="e" role="alert"></p>
    <button class="btn" id="go" type="submit">Sign in</button>
  </form>
  <p class="fine">Accounts and schedules are saved in this browser on this device.</p>
</main>
<script>
/* The page to open after a successful sign in. */
const APP_URL = "https://shockingparty2.github.io/Questlog";
const DAYS30 = 30 * 864e5;
const $ = s => document.querySelector(s);
let mode = "in";

function session() {
  try { return JSON.parse(localStorage.getItem("ql.session") || sessionStorage.getItem("ql.session") || "null"); } catch (e) { return null; }
}
const s0 = session();
if (s0 && s0.user && Date.now() - s0.at < DAYS30) location.replace(APP_URL);

const users = () => { try { return JSON.parse(localStorage.getItem("ql.users") || "{}"); } catch (e) { return {}; } };
const hex = b => [...new Uint8Array(b)].map(x => x.toString(16).padStart(2, "0")).join("");
const unhex = h => new Uint8Array(h.match(/../g).map(x => parseInt(x, 16)));
async function hashPw(pw, salt) {
  const k = await crypto.subtle.importKey("raw", new TextEncoder().encode(pw), "PBKDF2", false, ["deriveBits"]);
  return hex(await crypto.subtle.deriveBits({ name: "PBKDF2", hash: "SHA-256", salt, iterations: 150000 }, k, 256));
}
const err = m => { $("#e").textContent = m; };

document.querySelectorAll(".tab").forEach(t => t.onclick = () => {
  mode = t.dataset.m; err("");
  document.querySelectorAll(".tab").forEach(x => x.setAttribute("aria-pressed", x === t));
  $("#cw").hidden = mode !== "up"; $("#c").required = mode === "up";
  $("#p").autocomplete = mode === "up" ? "new-password" : "current-password";
  $("#go").textContent = mode === "up" ? "Create account" : "Sign in";
  $("#sub").textContent = mode === "up" ? "Pick a username and password." : "Sign in to open your schedule.";
});

$("#f").onsubmit = async e => {
  e.preventDefault(); err("");
  const u = $("#u").value.trim().toLowerCase(), p = $("#p").value;
  if (!/^[a-z0-9_]{3,20}$/.test(u)) return err("Usernames use 3 to 20 letters, numbers or underscores.");
  if (p.length < 6) return err("Passwords need at least 6 characters.");
  $("#go").disabled = true;
  try {
    const all = users();
    if (mode === "up") {
      if (p !== $("#c").value) throw "The passwords don't match.";
      if (all[u]) throw "That username is already taken here. Sign in instead.";
      const salt = crypto.getRandomValues(new Uint8Array(16));
      all[u] = { salt: hex(salt), hash: await hashPw(p, salt) };
      localStorage.setItem("ql.users", JSON.stringify(all));
    } else {
      const r = all[u];
      if (!r || (await hashPw(p, unhex(r.salt))) !== r.hash) throw "Wrong username or password.";
    }
    const s = JSON.stringify({ user: u, at: Date.now() });
    localStorage.removeItem("ql.session"); sessionStorage.removeItem("ql.session");
    ($("#r").checked ? localStorage : sessionStorage).setItem("ql.session", s);
    location.replace(APP_URL);
  } catch (x) {
    err(typeof x === "string" ? x : "Sign in needs browser storage, which is blocked here.");
    $("#go").disabled = false;
  }
};
</script>
</body>
</html>
