# beamedbylynx.github.io

<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Soul Forum</title>
<link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700;900&family=Inter:wght@300;400;500;600&display=swap" rel="stylesheet">
<style>
*{margin:0;padding:0;box-sizing:border-box}
:root{
  --void:#000000;
  --deep:#080808;
  --panel:rgba(255,255,255,0.05);
  --panel-hover:rgba(255,255,255,0.08);
  --border:rgba(255,255,255,0.10);
  --border-hover:rgba(255,255,255,0.22);
  --soul-red:#7a0000;
  --soul-red-dim:rgba(122,0,0,0.18);
  --gold:#ffffff;
  --gold-dim:rgba(255,255,255,0.12);
  --text-primary:#ffffff;
  --text-secondary:#d0d0d0;
  --text-dim:#777777;
  --glass:rgba(10,10,10,0.7);
}
html,body{min-height:100vh;background:var(--void);color:var(--text-primary);font-family:'Inter',sans-serif;overflow-x:hidden}
body{background:radial-gradient(circle at top left,rgba(122,0,0,0.25) 0%,transparent 40%),radial-gradient(circle at bottom right,rgba(255,255,255,0.04) 0%,transparent 50%),#000}

/* NAV */
nav{position:sticky;top:16px;z-index:100;display:flex;justify-content:center;padding:0 16px;margin-bottom:32px}
.nav-pill{display:flex;align-items:center;gap:4px;background:rgba(13,13,26,0.85);border:1px solid var(--border);border-radius:50px;padding:6px 8px;backdrop-filter:blur(20px);transition:all 0.3s}
.nav-logo{font-family:'Orbitron',monospace;font-weight:900;font-size:14px;color:var(--soul-red);letter-spacing:2px;padding:0 12px 0 8px;white-space:nowrap}
.nav-item{position:relative;display:flex;align-items:center;gap:0;padding:8px 10px;border-radius:40px;cursor:pointer;transition:all 0.35s cubic-bezier(0.34,1.56,0.64,1);border:1px solid transparent;white-space:nowrap;overflow:hidden;max-width:40px;color:var(--text-secondary);font-size:13px;font-weight:500}
.nav-item:hover{max-width:160px;background:var(--panel-hover);border-color:var(--border-hover);color:var(--text-primary);padding:8px 16px}
.nav-item.active{background:var(--soul-red-dim);border-color:rgba(233,69,96,0.3);color:var(--soul-red);max-width:160px;padding:8px 16px}
.nav-item.vip-nav{color:#aaa}
.nav-item.vip-nav:hover,.nav-item.vip-nav.active{background:var(--gold-dim);border-color:rgba(255,215,0,0.3);color:var(--gold)}
.nav-icon{font-size:16px;min-width:18px;display:flex;align-items:center;justify-content:center}
.nav-label{overflow:hidden;width:0;opacity:0;transition:all 0.35s cubic-bezier(0.34,1.56,0.64,1);white-space:nowrap;margin-left:0}
.nav-item:hover .nav-label,.nav-item.active .nav-label{width:auto;opacity:1;margin-left:8px}
.nav-sep{width:1px;height:24px;background:var(--border);margin:0 4px}

/* TILT BUTTONS */
.tilt-btn{transition:transform 0.2s ease,box-shadow 0.2s ease;cursor:pointer}
.tilt-btn:hover{transform:rotateX(12deg) rotateY(-8deg);box-shadow:4px 8px 24px rgba(0,0,0,0.4)}

/* MAIN */
main{max-width:860px;margin:0 auto;padding:0 16px 80px}

/* SECTIONS */
.section{display:none}
.section.active{display:block}

/* HERO */
.forum-header{text-align:center;padding:40px 0 48px}
.forum-title{font-family:'Orbitron',monospace;font-weight:900;font-size:clamp(36px,6vw,64px);color:var(--text-primary);letter-spacing:4px;line-height:1}
.forum-title span{color:var(--soul-red)}
.forum-subtitle{color:var(--text-secondary);font-size:14px;margin-top:12px;letter-spacing:2px;text-transform:uppercase}

/* POSTS */
.new-post-bar{display:flex;gap:12px;margin-bottom:28px;align-items:center}
.avatar-circle{width:40px;height:40px;border-radius:50%;background:var(--panel);border:1px solid var(--border);display:flex;align-items:center;justify-content:center;font-size:14px;font-weight:600;flex-shrink:0;overflow:hidden}
.post-input-fake{flex:1;background:var(--panel);border:1px solid var(--border);border-radius:24px;padding:11px 20px;color:var(--text-secondary);font-size:14px;cursor:pointer;transition:all 0.2s}
.post-input-fake:hover{border-color:var(--border-hover);background:var(--panel-hover);color:var(--text-primary)}
.btn{display:inline-flex;align-items:center;gap:8px;padding:10px 20px;border-radius:24px;font-size:13px;font-weight:600;cursor:pointer;border:1px solid;transition:all 0.2s;font-family:'Inter',sans-serif;letter-spacing:0.5px}
.btn-primary{background:var(--soul-red);border-color:var(--soul-red);color:#fff}
.btn-primary:hover{background:#c73050;border-color:#c73050;transform:translateY(-1px)}
.btn-ghost{background:transparent;border-color:var(--border);color:var(--text-secondary)}
.btn-ghost:hover{border-color:var(--border-hover);color:var(--text-primary);background:var(--panel)}
.btn-gold{background:var(--gold-dim);border-color:rgba(255,215,0,0.4);color:var(--gold)}
.btn-gold:hover{background:rgba(255,215,0,0.25);border-color:var(--gold)}

.posts-list{display:flex;flex-direction:column;gap:16px}
.post-card{background:var(--panel);border:1px solid var(--border);border-radius:16px;padding:20px;transition:all 0.2s;cursor:default}
.post-card:hover{border-color:var(--border-hover);background:var(--panel-hover)}
.post-card.vip-post{border-color:rgba(255,215,0,0.2)}
.post-card.vip-post:hover{border-color:rgba(255,215,0,0.4)}
.post-head{display:flex;align-items:center;gap:12px;margin-bottom:12px}
.post-author{display:flex;align-items:center;gap:8px}
.author-name{font-size:14px;font-weight:600}
.author-name.anon{color:var(--text-secondary);font-style:italic}
.author-name.vip{color:var(--gold)}
.tag{display:inline-block;font-size:10px;font-weight:700;padding:2px 8px;border-radius:20px;letter-spacing:1px;text-transform:uppercase}
.tag-vip{background:var(--gold-dim);color:var(--gold);border:1px solid rgba(255,215,0,0.3)}
.tag-anon{background:rgba(255,255,255,0.05);color:var(--text-dim);border:1px solid var(--border)}
.post-time{margin-left:auto;color:var(--text-dim);font-size:12px}
.post-body{color:var(--text-primary);font-size:14px;line-height:1.7;margin-bottom:14px}
.post-actions{display:flex;gap:16px;align-items:center}
.post-action{display:flex;align-items:center;gap:6px;color:var(--text-dim);font-size:13px;cursor:pointer;transition:color 0.2s;background:none;border:none;font-family:inherit}
.post-action:hover{color:var(--text-secondary)}
.post-action.liked{color:var(--soul-red)}
.post-action svg{width:15px;height:15px}
.vip-crown{font-size:14px;margin-right:2px}

/* MODAL */
.modal-overlay{display:none;position:fixed;inset:0;background:rgba(0,0,0,0.75);backdrop-filter:blur(8px);z-index:200;align-items:center;justify-content:center;padding:16px}
.modal-overlay.open{display:flex}
.modal{background:rgba(15,15,28,0.98);border:1px solid var(--border);border-radius:20px;padding:32px;width:100%;max-width:440px;max-height:90vh;overflow-y:auto}
.modal-title{font-family:'Orbitron',monospace;font-size:18px;font-weight:700;margin-bottom:6px;color:var(--text-primary)}
.modal-sub{color:var(--text-secondary);font-size:13px;margin-bottom:24px}
.field{margin-bottom:16px}
.field label{display:block;font-size:12px;font-weight:600;color:var(--text-secondary);letter-spacing:1px;text-transform:uppercase;margin-bottom:6px}
.field input,.field textarea{width:100%;background:var(--panel);border:1px solid var(--border);border-radius:10px;padding:11px 14px;color:var(--text-primary);font-family:'Inter',sans-serif;font-size:14px;outline:none;transition:border-color 0.2s;resize:vertical}
.field textarea{min-height:100px}
.field input:focus,.field textarea:focus{border-color:rgba(233,69,96,0.5)}
.modal-actions{display:flex;gap:10px;justify-content:flex-end;margin-top:24px;flex-wrap:wrap}
.divider{text-align:center;color:var(--text-dim);font-size:12px;margin:16px 0;position:relative}
.divider::before,.divider::after{content:'';position:absolute;top:50%;width:42%;height:1px;background:var(--border)}
.divider::before{left:0}.divider::after{right:0}
.anon-toggle{display:flex;align-items:center;gap:10px;padding:12px;background:var(--panel);border:1px solid var(--border);border-radius:10px;cursor:pointer;transition:all 0.2s}
.anon-toggle:hover{border-color:var(--border-hover)}
.toggle-switch{width:36px;height:20px;background:var(--border);border-radius:10px;position:relative;transition:background 0.2s;flex-shrink:0}
.toggle-switch.on{background:var(--soul-red)}
.toggle-switch::after{content:'';position:absolute;width:14px;height:14px;background:#fff;border-radius:50%;top:3px;left:3px;transition:transform 0.2s}
.toggle-switch.on::after{transform:translateX(16px)}
.toggle-text{font-size:13px;color:var(--text-secondary)}

/* TABS */
.tabs{display:flex;gap:4px;margin-bottom:28px;background:var(--panel);border:1px solid var(--border);border-radius:12px;padding:4px}
.tab{flex:1;padding:9px;text-align:center;font-size:13px;font-weight:600;cursor:pointer;border-radius:9px;transition:all 0.2s;color:var(--text-secondary);border:1px solid transparent}
.tab.active{background:var(--panel-hover);color:var(--text-primary);border-color:var(--border)}

/* VIP PAGE */
.vip-hero{text-align:center;padding:48px 0 56px}
.vip-crown-big{font-size:56px;display:block;margin-bottom:16px}
.vip-title{font-family:'Orbitron',monospace;font-weight:900;font-size:clamp(28px,5vw,48px);color:var(--gold);letter-spacing:3px}
.vip-sub{color:var(--text-secondary);font-size:15px;margin-top:10px;max-width:460px;margin-left:auto;margin-right:auto;line-height:1.7}
.perks-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(200px,1fr));gap:16px;margin-bottom:48px}
.perk-card{background:var(--panel);border:1px solid var(--border);border-radius:16px;padding:20px;text-align:center;transition:all 0.25s}
.perk-card:hover{border-color:rgba(255,215,0,0.25);background:rgba(255,215,0,0.04);transform:translateY(-3px)}
.perk-icon{font-size:32px;display:block;margin-bottom:10px}
.perk-name{font-weight:700;font-size:14px;color:var(--gold);margin-bottom:6px}
.perk-desc{font-size:12px;color:var(--text-secondary);line-height:1.5}
.pricing-card{background:linear-gradient(135deg,rgba(255,215,0,0.06),rgba(255,215,0,0.02));border:1px solid rgba(255,215,0,0.25);border-radius:20px;padding:36px;text-align:center;max-width:380px;margin:0 auto}
.price-tag{font-family:'Orbitron',monospace;font-size:52px;font-weight:900;color:var(--gold)}
.price-per{font-size:14px;color:var(--text-secondary);margin-bottom:24px}
.locked-msg{text-align:center;color:var(--text-secondary);font-size:14px;margin-top:16px;padding:12px;background:rgba(255,255,255,0.03);border-radius:10px;border:1px solid var(--border)}

/* PROFILE PAGE */
.profile-card{background:var(--panel);border:1px solid var(--border);border-radius:20px;padding:32px;margin-bottom:24px;text-align:center}
.profile-avatar{width:80px;height:80px;border-radius:50%;background:var(--soul-red-dim);border:2px solid rgba(233,69,96,0.3);display:flex;align-items:center;justify-content:center;font-size:28px;font-weight:700;margin:0 auto 16px;color:var(--soul-red)}
.profile-avatar.vip-avatar{background:var(--gold-dim);border-color:rgba(255,215,0,0.4);color:var(--gold)}
.profile-name{font-family:'Orbitron',monospace;font-size:20px;font-weight:700;margin-bottom:6px}
.profile-name.vip-name{color:var(--gold)}
.profile-badge{display:inline-flex;align-items:center;gap:6px;padding:4px 14px;background:var(--soul-red-dim);border:1px solid rgba(233,69,96,0.3);border-radius:20px;color:var(--soul-red);font-size:12px;font-weight:700;letter-spacing:1px}
.profile-badge.vip-badge{background:var(--gold-dim);border-color:rgba(255,215,0,0.3);color:var(--gold)}
.stats-row{display:flex;justify-content:center;gap:32px;margin-top:20px}
.stat{text-align:center}
.stat-num{font-family:'Orbitron',monospace;font-size:22px;font-weight:700;color:var(--text-primary)}
.stat-label{font-size:11px;color:var(--text-dim);text-transform:uppercase;letter-spacing:1px;margin-top:2px}

/* ALERTS */
.alert{padding:12px 16px;border-radius:10px;font-size:13px;margin-bottom:16px}
.alert-err{background:rgba(233,69,96,0.1);border:1px solid rgba(233,69,96,0.25);color:var(--soul-red)}
.alert-ok{background:rgba(0,200,100,0.1);border:1px solid rgba(0,200,100,0.25);color:#00c864}

/* SCROLLBAR */
::-webkit-scrollbar{width:4px;height:4px}
::-webkit-scrollbar-track{background:transparent}
::-webkit-scrollbar-thumb{background:var(--border);border-radius:2px}

/* EMPTY STATE */
.empty-state{text-align:center;padding:60px 0;color:var(--text-dim)}
.empty-icon{font-size:48px;margin-bottom:12px}
.empty-text{font-size:14px}

/* RESPONSIVE */
@media(max-width:600px){
  .perks-grid{grid-template-columns:1fr 1fr}
  .stats-row{gap:20px}
  .modal{padding:24px}
  .forum-title{font-size:32px}
}

.online-widget{position:fixed;left:12px;bottom:12px;background:rgba(0,0,0,.8);border:1px solid rgba(255,255,255,.12);padding:10px 14px;border-radius:12px;font-size:12px;z-index:999}
.online-dot{display:inline-block;width:8px;height:8px;background:red;border-radius:50%;margin-right:8px}

</style>
</head>
<body>

<!-- NAV -->
<nav>
  <div class="nav-pill" id="navPill">
    <span class="nav-logo">SOUL</span>
    <div class="nav-sep"></div>
    <div class="nav-item active tilt-btn" onclick="showSection('forum')" id="nav-forum">
      <span class="nav-icon">
        <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M21 15a2 2 0 0 1-2 2H7l-4 4V5a2 2 0 0 1 2-2h14a2 2 0 0 1 2 2z"/></svg>
      </span>
      <span class="nav-label">Forum</span>
    </div>
    <div class="nav-item vip-nav tilt-btn" onclick="showSection('vip')" id="nav-vip">
      <span class="nav-icon"></span>
      <span class="nav-label">👑 VIP</span>
    </div>
    <div class="nav-sep"></div>
    <div class="nav-item tilt-btn" onclick="handleProfileNav()" id="nav-profile">
      <span class="nav-icon">
        <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M20 21v-2a4 4 0 0 0-4-4H8a4 4 0 0 0-4 4v2"/><circle cx="12" cy="7" r="4"/></svg>
      </span>
      <span class="nav-label" id="nav-profile-label">Account</span>
    </div>
  </div>
</nav>

<main>

<!-- FORUM SECTION -->
<div class="section active" id="section-forum">
  <div class="forum-header">
    <h1 class="forum-title">SOUL<span>.</span>FORUM</h1>
    
  </div>

  <div class="new-post-bar">
    <div class="avatar-circle" id="nav-avatar">
      <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M20 21v-2a4 4 0 0 0-4-4H8a4 4 0 0 0-4 4v2"/><circle cx="12" cy="7" r="4"/></svg>
    </div>
    <div class="post-input-fake" onclick="openPostModal()">Share something with the forum...</div>
    <button class="btn btn-primary tilt-btn" onclick="openPostModal()">Post</button>
  </div>

  <div class="posts-list" id="postsList">
    <!-- posts rendered by JS -->
  </div>
</div>

<!-- VIP SECTION -->
<div class="section" id="section-vip">
  <div class="vip-hero">
    <span class="vip-crown-big"></span>
    <h1 class="vip-title">SOUL VIP</h1>
    <p class="vip-sub">Elevate your presence. Stand out. Be recognised as one of the inner circle of Soul Forum.</p>
  </div>

  <div class="perks-grid">
    <div class="perk-card tilt-btn">
      <span class="perk-icon"></span>
      <div class="perk-name">Golden Nametag</div>
      <div class="perk-desc">Your name glows in gold across every post and reply you make.</div>
    </div>
    <div class="perk-card tilt-btn">
      <span class="perk-icon"></span>
      <div class="perk-name">VIP Crown Badge</div>
      <div class="perk-desc">A crown badge displayed next to your name throughout the forum.</div>
    </div>
    <div class="perk-card tilt-btn">
      <span class="perk-icon"></span>
      <div class="perk-name">Priority Visibility</div>
      <div class="perk-desc">Your posts are featured at the top of the feed for 24 hours.</div>
    </div>
    <div class="perk-card tilt-btn">
      <span class="perk-icon"></span>
      <div class="perk-name">Custom Flair</div>
      <div class="perk-desc">Choose a colour for your profile border from an exclusive VIP palette.</div>
    </div>
    <div class="perk-card tilt-btn">
      <span class="perk-icon"></span>
      <div class="perk-name">VIP Lounge</div>
      <div class="perk-desc">Access to a private VIP-only section of the forum. Members only.</div>
    </div>
    <div class="perk-card tilt-btn">
      <span class="perk-icon"></span>
      <div class="perk-name">Soul Diamond Role</div>
      <div class="perk-desc">After 90 days, unlock Diamond tier with even more exclusive perks.</div>
    </div>
  </div>

  <div class="pricing-card">
    <div class="price-tag">£4</div>
    <div class="price-per">per month · cancel anytime</div>
    <div id="vip-btn-area">
      <!-- rendered by JS based on auth state -->
    </div>
  </div>
</div>

<!-- PROFILE SECTION -->
<div class="section" id="section-profile">
  <!-- rendered by JS -->
</div>

<!-- AUTH SECTION -->
<div class="section" id="section-auth">
  <div style="max-width:400px;margin:60px auto 0">
    <div class="tabs">
      <div class="tab active" onclick="switchAuthTab('login')" id="tab-login">Sign In</div>
      <div class="tab" onclick="switchAuthTab('register')" id="tab-register">Create Account</div>
    </div>
    <div id="auth-form-area"></div>
  </div>
</div>

</main>

<!-- POST MODAL -->
<div class="modal-overlay" id="postModal">
  <div class="modal">
    <div class="modal-title">New Post</div>
    <div class="modal-sub" id="post-modal-sub">Sharing as yourself</div>
    <div id="post-modal-alert"></div>
    <div class="field">
      <label>Title</label>
      <input type="text" id="post-title" placeholder="Give your post a title...">
    </div>
    <div class="field">
      <label>Message</label>
      <textarea id="post-body" placeholder="What's on your mind?"></textarea>
    </div>
    <div class="field">
      <label>Image</label>
      <input type="file" id="post-image" accept="image/*">
    </div>
    <div class="anon-toggle" onclick="toggleAnon()" id="anonToggle">
      <div class="toggle-switch" id="anonSwitch"></div>
      <span class="toggle-text" id="anonText">Post anonymously — hide your identity</span>
    </div>
    <div class="modal-actions">
      <button class="btn btn-ghost tilt-btn" onclick="closePostModal()">Cancel</button>
      <button class="btn btn-primary tilt-btn" onclick="submitPost()">Publish Post</button>
    </div>
  </div>
</div>

<!-- VIP PURCHASE MODAL -->
<div class="modal-overlay" id="vipModal">
  <div class="modal">
    <div class="modal-title" style="color:var(--gold)">Activate VIP</div>
    <div class="modal-sub">You're about to unlock Soul VIP — £4/month</div>
    <div id="vip-modal-alert"></div>
    <div class="field">
      <label>Card Number</label>
      <input type="text" id="card-num" placeholder="4242 4242 4242 4242" maxlength="19" oninput="fmtCard(this)">
    </div>
    <div style="display:flex;gap:12px">
      <div class="field" style="flex:1">
        <label>Expiry</label>
        <input type="text" id="card-exp" placeholder="MM/YY" maxlength="5" oninput="fmtExp(this)">
      </div>
      <div class="field" style="flex:1">
        <label>CVV</label>
        <input type="text" id="card-cvv" placeholder="123" maxlength="3">
      </div>
    </div>
    <div class="modal-actions">
      <button class="btn btn-ghost tilt-btn" onclick="closeVipModal()">Cancel</button>
      <button class="btn btn-gold tilt-btn" onclick="purchaseVip()">Pay £4 · Activate VIP</button>
    </div>
  </div>
</div>

<script>
// ── STATE ──────────────────────────────────────────────────────────────────
let currentUser = null; // {name, initials, isVip, postCount, likeCount}
let anonMode = false;
let posts = [];
let nextPostId = 1;

const USERS_KEY = 'sf_users';
const SESSION_KEY = 'sf_session';

function getUsers(){try{return JSON.parse(localStorage.getItem(USERS_KEY)||'[]')}catch{return[]}}
function saveUsers(u){localStorage.setItem(USERS_KEY,JSON.stringify(u))}
function getSession(){try{return JSON.parse(localStorage.getItem(SESSION_KEY)||'null')}catch{return null}}
function saveSession(u){localStorage.setItem(SESSION_KEY,JSON.stringify(u))}
function clearSession(){localStorage.removeItem(SESSION_KEY)}

function initials(name){return name.split(' ').map(w=>w[0]).join('').toUpperCase().slice(0,2)}

// ── INIT ───────────────────────────────────────────────────────────────────
window.addEventListener('load',()=>{
  const sess = getSession();
  if(sess){
    const users = getUsers();
    const found = users.find(u=>u.name===sess.name);
    if(found) currentUser = found;
  }
  updateNavAvatar();
  renderPosts();
  renderVipBtnArea();
  showSection('forum');
});

// ── NAV ────────────────────────────────────────────────────────────────────
function showSection(id){
  document.querySelectorAll('.section').forEach(s=>s.classList.remove('active'));
  document.querySelectorAll('.nav-item').forEach(n=>n.classList.remove('active'));
  document.getElementById('section-'+id).classList.add('active');
  const navEl = document.getElementById('nav-'+id);
  if(navEl) navEl.classList.add('active');
  if(id==='profile') renderProfile();
  if(id==='auth') renderAuthForm('login');
  if(id==='vip') renderVipBtnArea();
}

function handleProfileNav(){
  if(currentUser){showSection('profile')}
  else{showSection('auth')}
}

function updateNavAvatar(){
  const a = document.getElementById('nav-avatar');
  const lbl = document.getElementById('nav-profile-label');
  if(currentUser){
    a.textContent = currentUser.initials;
    a.style.background = currentUser.isVip ? 'rgba(255,215,0,0.15)':'rgba(233,69,96,0.15)';
    a.style.color = currentUser.isVip ? 'var(--gold)':'var(--soul-red)';
    a.style.border = currentUser.isVip ? '1px solid rgba(255,215,0,0.3)':'1px solid rgba(233,69,96,0.3)';
    lbl.textContent = currentUser.name;
  } else {
    a.innerHTML = '<svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M20 21v-2a4 4 0 0 0-4-4H8a4 4 0 0 0-4 4v2"/><circle cx="12" cy="7" r="4"/></svg>';
    a.style.background='';a.style.color='';a.style.border='';
    lbl.textContent = 'Account';
  }
}

// ── TILT EFFECT ────────────────────────────────────────────────────────────
document.addEventListener('mousemove',e=>{
  document.querySelectorAll('.tilt-btn').forEach(el=>{
    const r = el.getBoundingClientRect();
    const cx = r.left+r.width/2;
    const cy = r.top+r.height/2;
    const dx = (e.clientX-cx)/(r.width/2);
    const dy = (e.clientY-cy)/(r.height/2);
    const dist = Math.sqrt(dx*dx+dy*dy);
    if(dist<1.5){
      el.style.transform = `rotateX(${-dy*8}deg) rotateY(${dx*8}deg)`;
    } else {
      el.style.transform = 'rotateX(0) rotateY(0)';
    }
  });
});
document.addEventListener('mouseleave',()=>{
  document.querySelectorAll('.tilt-btn').forEach(el=>{el.style.transform='rotateX(0) rotateY(0)'});
});

// ── POSTS ──────────────────────────────────────────────────────────────────
function renderPosts(){
  const list = document.getElementById('postsList');
  if(!posts.length){list.innerHTML='<div class="empty-state"><div class="empty-icon"></div><div class="empty-text">No posts yet. Be the first to speak.</div></div>';return}
  list.innerHTML = posts.map(p=>postHTML(p)).join('');
}

function postHTML(p){
  const anonClass = p.isAnon ? 'anon':'';
  const vipClass = (!p.isAnon && p.isVip) ? 'vip':'';
  const nameDisplay = p.isAnon ? 'Anonymous' : p.author;
  const tagHTML = p.isAnon
    ? '<span class="tag tag-anon">ANON</span>'
    : (p.isVip ? '<span class="tag tag-vip">👑 VIP</span>' : '');
  const avatarStyle = (!p.isAnon && p.isVip)
    ? 'background:rgba(255,215,0,0.15);border:1px solid rgba(255,215,0,0.3);color:var(--gold)'
    : (!p.isAnon ? 'background:rgba(233,69,96,0.1);border:1px solid rgba(233,69,96,0.2);color:var(--soul-red)' : 'background:rgba(255,255,255,0.04);border:1px solid rgba(255,255,255,0.08);color:var(--text-dim)');
  const initDisplay = p.isAnon ? '?' : p.initials;
  const cardClass = (!p.isAnon && p.isVip) ? 'post-card vip-post' : 'post-card';
  const likeColor = p.liked ? 'style="color:var(--soul-red)"' : '';
  return `<div class="${cardClass}" id="post-${p.id}">
    <div class="post-head">
      <div class="avatar-circle" style="${avatarStyle}">${initDisplay}</div>
      <div class="post-author">
        <span class="author-name ${anonClass} ${vipClass}">${nameDisplay}</span>
        ${tagHTML}
      </div>
      <span class="post-time">${p.time}</span>
    </div>
    <div style="font-weight:600;font-size:15px;margin-bottom:8px;color:var(--text-primary)">${escHtml(p.title)}</div>
    <div class="post-body">${escHtml(p.body)}</div>${p.image?`<img src="${p.image}" style="max-width:100%;border-radius:12px;margin-top:10px">`:``}
    <div class="post-actions">
      <button class="post-action ${p.liked?'liked':''}" onclick="likePost(${p.id})" ${likeColor}>
        <svg viewBox="0 0 24 24" fill="${p.liked?'currentColor':'none'}" stroke="currentColor" stroke-width="2"><path d="M20.84 4.61a5.5 5.5 0 0 0-7.78 0L12 5.67l-1.06-1.06a5.5 5.5 0 0 0-7.78 7.78l1.06 1.06L12 21.23l7.78-7.78 1.06-1.06a5.5 5.5 0 0 0 0-7.78z"/></svg>
        ${p.likes}
      </button>
      <button class="post-action">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M21 15a2 2 0 0 1-2 2H7l-4 4V5a2 2 0 0 1 2-2h14a2 2 0 0 1 2 2z"/></svg>
        Reply
      </button>
    </div>
  </div>`;
}

function escHtml(s){return s.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;')}

function likePost(id){
  const p = posts.find(x=>x.id===id);
  if(!p)return;
  p.liked = !p.liked;
  p.likes += p.liked ? 1 : -1;
  if(currentUser){currentUser.likeCount=Math.max(0,(currentUser.likeCount||0)+(p.liked?1:-1));syncUser()}
  renderPosts();
}

// ── POST MODAL ─────────────────────────────────────────────────────────────
function openPostModal(){
  anonMode = false;
  document.getElementById('post-title').value='';
  document.getElementById('post-body').value='';
  document.getElementById('anonSwitch').className='toggle-switch';
  document.getElementById('post-modal-alert').innerHTML='';
  updatePostModalSub();
  document.getElementById('postModal').classList.add('open');
}
function closePostModal(){document.getElementById('postModal').classList.remove('open')}

function updatePostModalSub(){
  const sub = document.getElementById('post-modal-sub');
  if(anonMode){sub.textContent='Posting anonymously — identity hidden'}
  else if(currentUser){sub.textContent=`Sharing as ${currentUser.name}`}
  else{sub.textContent='Guest post — sign in to use your name'}
}

function toggleAnon(){
  anonMode = !anonMode;
  document.getElementById('anonSwitch').className='toggle-switch'+(anonMode?' on':'');
  document.getElementById('anonText').textContent = anonMode ? 'Anonymous mode ON — identity hidden' : 'Post anonymously — hide your identity';
  updatePostModalSub();
}

function submitPost(){
  const title = document.getElementById('post-title').value.trim();
  const body = document.getElementById('post-body').value.trim();
  const alertEl = document.getElementById('post-modal-alert');
  if(!title||!body){alertEl.innerHTML='<div class="alert alert-err">Please fill in both title and message.</div>';return}
  alertEl.innerHTML='';
  const isVip = currentUser?.isVip || false;
  const p = {
    id:nextPostId++,
    author: anonMode ? null : (currentUser?.name||'Guest'),
    initials: anonMode ? '?' : (currentUser?.initials||'GS'),
    isVip: !anonMode && isVip,
    isAnon: anonMode,
    title, body,
    time:'just now',
    likes:0,
    liked:false,
    image:null
  };
  const f=document.getElementById('post-image');
  if(f && f.files && f.files[0]){
    const r=new FileReader();
    r.onload=e=>{p.image=e.target.result;posts.unshift(p);renderPosts();};
    r.readAsDataURL(f.files[0]);
  } else {
    posts.unshift(p);
  }
  if(currentUser){currentUser.postCount=(currentUser.postCount||0)+1;syncUser()}
  renderPosts();
  closePostModal();
}

// ── VIP ────────────────────────────────────────────────────────────────────
function renderVipBtnArea(){
  const area = document.getElementById('vip-btn-area');
  if(!area)return;
  if(!currentUser){
    area.innerHTML=`<button class="btn btn-ghost tilt-btn" style="width:100%;justify-content:center;margin-bottom:8px" onclick="showSection('auth')">Sign in to purchase VIP</button>
    <div class="locked-msg"> You must have an account to buy VIP</div>`;
  } else if(currentUser.isVip){
    area.innerHTML=`<div style="display:flex;align-items:center;justify-content:center;gap:10px;padding:16px;background:var(--gold-dim);border:1px solid rgba(255,215,0,0.3);border-radius:12px;color:var(--gold);font-weight:700;font-size:15px">👑 You are VIP — enjoy your perks!</div>`;
  } else {
    area.innerHTML=`<button class="btn btn-gold tilt-btn" style="width:100%;justify-content:center;font-size:15px;padding:14px" onclick="openVipModal()">👑 👑 Activate VIP · £4/mo</button>`;
  }
}

function openVipModal(){
  document.getElementById('vip-modal-alert').innerHTML='';
  document.getElementById('card-num').value='';
  document.getElementById('card-exp').value='';
  document.getElementById('card-cvv').value='';
  document.getElementById('vipModal').classList.add('open');
}
function closeVipModal(){document.getElementById('vipModal').classList.remove('open')}

function fmtCard(el){let v=el.value.replace(/\D/g,'').slice(0,16);el.value=v.replace(/(.{4})/g,'$1 ').trim()}
function fmtExp(el){let v=el.value.replace(/\D/g,'').slice(0,4);if(v.length>2)v=v.slice(0,2)+'/'+v.slice(2);el.value=v}

function purchaseVip(){
  const num=document.getElementById('card-num').value.replace(/\s/g,'');
  const exp=document.getElementById('card-exp').value;
  const cvv=document.getElementById('card-cvv').value;
  const alertEl=document.getElementById('vip-modal-alert');
  if(num.length<16||exp.length<5||cvv.length<3){alertEl.innerHTML='<div class="alert alert-err">Please fill in all payment details.</div>';return}
  // Simulate payment
  alertEl.innerHTML='<div class="alert alert-ok">Payment successful! Activating VIP...</div>';
  setTimeout(()=>{
    currentUser.isVip=true;
    syncUser();
    closeVipModal();
    renderVipBtnArea();
    updateNavAvatar();
    alertEl.innerHTML='';
    // Show success in VIP section
    const priceCard=document.querySelector('.pricing-card');
    if(priceCard) renderVipBtnArea();
  },1200);
}

// ── AUTH ───────────────────────────────────────────────────────────────────
function switchAuthTab(t){
  document.getElementById('tab-login').classList.toggle('active',t==='login');
  document.getElementById('tab-register').classList.toggle('active',t==='register');
  renderAuthForm(t);
}

function renderAuthForm(mode){
  const area=document.getElementById('auth-form-area');
  if(mode==='login'){
    area.innerHTML=`
      <div id="auth-alert"></div>
      <div class="field"><label>Username</label><input type="text" id="auth-name" placeholder="your username"></div>
      <div class="field"><label>Password</label><input type="password" id="auth-pass" placeholder="••••••••"></div>
      <button class="btn btn-primary tilt-btn" style="width:100%;justify-content:center;margin-top:8px" onclick="doLogin()">Sign In</button>
      <div style="text-align:center;margin-top:16px;font-size:13px;color:var(--text-secondary)">No account? <span style="color:var(--soul-red);cursor:pointer" onclick="switchAuthTab('register')">Create one</span></div>
    `;
  } else {
    area.innerHTML=`
      <div id="auth-alert"></div>
      <div class="field"><label>Username</label><input type="text" id="auth-name" placeholder="choose a username" maxlength="20"></div>
      <div class="field"><label>Password</label><input type="password" id="auth-pass" placeholder="at least 6 characters"></div>
      <div class="field"><label>Confirm Password</label><input type="password" id="auth-pass2" placeholder="repeat password"></div>
      <button class="btn btn-primary tilt-btn" style="width:100%;justify-content:center;margin-top:8px" onclick="doRegister()">Create Account</button>
      <div style="text-align:center;margin-top:16px;font-size:13px;color:var(--text-secondary)">Already have one? <span style="color:var(--soul-red);cursor:pointer" onclick="switchAuthTab('login')">Sign in</span></div>
    `;
  }
}

function doLogin(){
  const name=document.getElementById('auth-name').value.trim();
  const pass=document.getElementById('auth-pass').value;
  const alertEl=document.getElementById('auth-alert');
  if(!name||!pass){alertEl.innerHTML='<div class="alert alert-err">Please fill in all fields.</div>';return}
  const users=getUsers();
  const found=users.find(u=>u.name===name&&u.pass===pass);
  if(!found){alertEl.innerHTML='<div class="alert alert-err">Incorrect username or password.</div>';return}
  currentUser=found;
  saveSession({name});
  updateNavAvatar();
  alertEl.innerHTML='<div class="alert alert-ok">Welcome back, '+name+'!</div>';
  setTimeout(()=>{showSection('forum')},800);
}

function doRegister(){
  const name=document.getElementById('auth-name').value.trim();
  const pass=document.getElementById('auth-pass').value;
  const pass2=document.getElementById('auth-pass2').value;
  const alertEl=document.getElementById('auth-alert');
  if(!name||!pass||!pass2){alertEl.innerHTML='<div class="alert alert-err">Please fill in all fields.</div>';return}
  if(pass.length<6){alertEl.innerHTML='<div class="alert alert-err">Password must be at least 6 characters.</div>';return}
  if(pass!==pass2){alertEl.innerHTML='<div class="alert alert-err">Passwords do not match.</div>';return}
  const users=getUsers();
  if(users.find(u=>u.name===name)){alertEl.innerHTML='<div class="alert alert-err">That username is already taken.</div>';return}
  const user={name,pass,initials:initials(name),isVip:false,postCount:0,likeCount:0};
  users.push(user);
  saveUsers(users);
  currentUser=user;
  saveSession({name});
  updateNavAvatar();
  alertEl.innerHTML='<div class="alert alert-ok">Account created! Welcome to Soul Forum.</div>';
  setTimeout(()=>{showSection('forum')},900);
}

function syncUser(){
  const users=getUsers();
  const i=users.findIndex(u=>u.name===currentUser.name);
  if(i>-1){users[i]=currentUser;saveUsers(users)}
}

// ── PROFILE ────────────────────────────────────────────────────────────────
function renderProfile(){
  const sec=document.getElementById('section-profile');
  if(!currentUser){sec.innerHTML=`<div style="text-align:center;padding:80px 0"><div style="font-size:48px;margin-bottom:16px"></div><p style="color:var(--text-secondary);margin-bottom:20px">You're not signed in.</p><button class="btn btn-primary tilt-btn" onclick="showSection('auth')">Sign In</button></div>`;return}
  const u=currentUser;
  sec.innerHTML=`
    <div class="profile-card">
      <div class="avatar-circle profile-avatar ${u.isVip?'vip-avatar':''}" style="width:80px;height:80px;font-size:28px;margin:0 auto 16px">${u.initials}</div>
      <div class="profile-name ${u.isVip?'vip-name':''}">${u.name}</div>
      <div style="margin-top:8px"><span class="profile-badge ${u.isVip?'vip-badge':''}">${u.isVip?' VIP MEMBER':'MEMBER'}</span></div>
      <div class="stats-row">
        <div class="stat"><div class="stat-num">${u.postCount||0}</div><div class="stat-label">Posts</div></div>
        <div class="stat"><div class="stat-num">${u.likeCount||0}</div><div class="stat-label">Likes Given</div></div>
        <div class="stat"><div class="stat-num">${u.isVip?'VIP':'Free'}</div><div class="stat-label">Plan</div></div>
      </div>
    </div>
    ${!u.isVip?`<div style="text-align:center;margin-bottom:24px"><p style="color:var(--text-secondary);font-size:14px;margin-bottom:12px">Upgrade to VIP and let the world know who you are.</p><button class="btn btn-gold tilt-btn" onclick="showSection('vip')">👑 View VIP Perks</button></div>`:'<div style="text-align:center;padding:16px;background:var(--gold-dim);border:1px solid rgba(255,215,0,0.2);border-radius:14px;color:var(--gold);font-size:14px;margin-bottom:24px">👑 You are a VIP member — enjoy all perks!</div>'}
    <div style="display:flex;gap:10px;flex-wrap:wrap">
      <button class="btn btn-ghost tilt-btn" style="flex:1;justify-content:center" onclick="openPostModal()">New Post</button>
      <button class="btn btn-ghost tilt-btn" style="flex:1;justify-content:center" onclick="doLogout()">Sign Out</button>
    </div>
  `;
}

function doLogout(){
  currentUser=null;
  clearSession();
  updateNavAvatar();
  showSection('forum');
}

window.addEventListener('load',()=>{
 let c=(parseInt(localStorage.getItem('sf_online')||'0')+1);
 localStorage.setItem('sf_online',c);
 const u=document.getElementById('onlineStats');
 if(u)u.textContent=c+' online • '+c+' on page';
 window.addEventListener('beforeunload',()=>{
   let n=Math.max(0,(parseInt(localStorage.getItem('sf_online')||'1')-1));
   localStorage.setItem('sf_online',n);
 });
});

</script>
<div class="online-widget"><span class="online-dot"></span><span id="onlineStats">1 online • 1 on page</span></div></body>
</html>
