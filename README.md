<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Oasis.OS</title>
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Figtree:wght@400;600;700;800&display=swap">
<style>
:root{--ink:#10302f;--mut:#5b7573;--win:#f6faf8;--bar:#e3eeea;--line:#cfdedb;--card:#fff;--glass:rgba(246,250,248,.8);--shadow:0 18px 50px rgba(5,40,45,.35);--accent:#14b8a6;--onacc:#04201c;box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px)}
@media(prefers-color-scheme:dark){:root:not([data-theme="light"]){--ink:#e6f4f1;--mut:#8fb0ab;--win:#10201f;--bar:#173130;--line:#254543;--card:#0c1a19;--glass:rgba(10,24,24,.76)}}
:root[data-theme="dark"]{--ink:#e6f4f1;--mut:#8fb0ab;--win:#10201f;--bar:#173130;--line:#254543;--card:#0c1a19;--glass:rgba(10,24,24,.76)}
*{box-sizing:border-box}
html,body{height:100%;margin:0}
body{background:#0b3b4a;font:14px/1.45 Figtree,system-ui,-apple-system,"Segoe UI",sans-serif;color:var(--ink);overflow:hidden;-webkit-tap-highlight-color:transparent}
button{font:inherit}
:focus-visible{outline:2px solid var(--accent);outline-offset:2px}
#desk{position:fixed;inset:0}
#desk[data-wall=lagoon]{background:radial-gradient(900px 500px at 15% 0,rgba(45,212,191,.35),transparent 60%),linear-gradient(160deg,#0b3b4a,#0f766e 62%,#164e63)}
#desk[data-wall=dusk]{background:radial-gradient(800px 500px at 85% 100%,rgba(251,191,36,.4),transparent 60%),linear-gradient(170deg,#1e1b4b,#7c3a6b 58%,#e8894a)}
#desk[data-wall=grove]{background:radial-gradient(900px 500px at 80% 0,rgba(190,242,100,.28),transparent 60%),linear-gradient(165deg,#0b2a1c,#1c6b47 60%,#3f8f5b)}
.icons{position:absolute;left:14px;top:calc(14px + env(safe-area-inset-top,0px));display:grid;gap:8px}
.ic{width:88px;background:none;border:0;color:#fff;text-align:center;cursor:pointer;padding:6px;border-radius:12px;text-shadow:0 1px 3px rgba(0,0,0,.55)}
.ic:hover{background:rgba(255,255,255,.14)}
.ic i{display:grid;place-items:center;width:54px;height:54px;margin:0 auto 4px;border-radius:16px;background:var(--accent);font-size:27px;font-style:normal;box-shadow:0 6px 16px rgba(0,0,0,.25)}
.win{position:absolute;display:flex;flex-direction:column;min-width:260px;background:var(--win);color:var(--ink);border:1px solid var(--line);border-radius:14px;box-shadow:var(--shadow);overflow:hidden}
.win[hidden]{display:none}
.win.top{border-color:var(--accent)}
.win header{display:flex;align-items:center;justify-content:space-between;padding:7px 8px 7px 14px;background:var(--bar);border-bottom:1px solid var(--line);cursor:grab;touch-action:none;user-select:none}
.win header b{font-weight:700}
.win header button{width:30px;height:30px;border:0;border-radius:8px;background:none;color:var(--ink);cursor:pointer}
.win header button:hover{background:var(--line)}
.win header button[data-a=close]:hover{background:#e5484d;color:#fff}
.body{flex:1;overflow:auto;padding:14px}
.win.max,.win.max.top{inset:0 0 calc(52px + env(safe-area-inset-bottom,0px)) 0!important;width:auto!important;height:auto!important;border-radius:0}
@media(max-width:640px){.win{inset:0 0 calc(52px + env(safe-area-inset-bottom,0px)) 0!important;width:auto!important;height:auto!important;border-radius:0}.win header{cursor:default}.win header [data-a=max]{display:none}}
#bar{position:fixed;left:0;right:0;bottom:0;z-index:9999;display:flex;align-items:center;gap:8px;height:calc(52px + env(safe-area-inset-bottom,0px));padding:6px 10px env(safe-area-inset-bottom,0px);background:var(--glass);backdrop-filter:blur(16px);-webkit-backdrop-filter:blur(16px);border-top:1px solid var(--line);color:var(--ink)}
#start{display:flex;align-items:center;gap:8px;height:38px;padding:0 14px;border:0;border-radius:10px;background:var(--accent);color:var(--onacc);font-weight:800;cursor:pointer}
.dot{width:10px;height:10px;border-radius:50%;background:var(--onacc);box-shadow:0 0 0 3px rgba(4,32,28,.2)}
#tasks{flex:1;display:flex;gap:6px;overflow-x:auto}
.tab{height:36px;padding:0 12px;border:1px solid var(--line);border-radius:9px;background:none;color:var(--ink);white-space:nowrap;cursor:pointer}
.tab.on{border-color:var(--accent);background:var(--bar)}
#clk{min-width:64px;text-align:right;font-size:12px;line-height:1.25;font-weight:600}
#clk span{display:block;color:var(--mut);font-weight:400}
#menu{position:fixed;left:10px;bottom:calc(60px + env(safe-area-inset-bottom,0px));z-index:9998;width:240px;padding:8px;background:var(--win);border:1px solid var(--line);border-radius:14px;box-shadow:var(--shadow)}
#menu[hidden]{display:none}
#menu button{display:flex;gap:10px;align-items:center;width:100%;padding:9px 10px;border:0;border-radius:9px;background:none;color:var(--ink);text-align:left;cursor:pointer}
#menu button:hover{background:var(--bar)}
.gh{display:flex;justify-content:space-between;align-items:center;margin-bottom:10px;color:var(--mut);gap:10px}
.gh b{color:var(--ink)}
.btn{padding:7px 14px;border:0;border-radius:9px;background:var(--accent);color:var(--onacc);font-weight:700;cursor:pointer}
.gc{display:flex;gap:12px;align-items:center;width:100%;padding:12px;margin-bottom:8px;border:1px solid var(--line);border-radius:12px;background:var(--card);color:var(--ink);text-align:left;cursor:pointer}
.gc:hover{border-color:var(--accent)}
.gc i{font-size:28px;font-style:normal}
.gc small{display:block;color:var(--mut)}
canvas{display:block;width:100%;max-width:304px;margin:0 auto;border:1px solid var(--line);border-radius:10px;touch-action:none}
.pad{display:none;grid-template-columns:repeat(3,54px);gap:6px;justify-content:center;margin-top:10px}
.pad button{height:46px;border:1px solid var(--line);border-radius:10px;background:var(--card);color:var(--ink)}
@media(hover:none){.pad{display:grid}}
.hint{margin:10px 0 0;color:var(--mut);font-size:12px;text-align:center}
.mg{display:grid;grid-template-columns:repeat(4,1fr);gap:8px;max-width:320px;margin:0 auto}
.mc{aspect-ratio:1;border:1px solid transparent;border-radius:12px;background:var(--accent);font-size:28px;cursor:pointer}
.mc span{opacity:0;transition:opacity .15s}
.mc.up{background:var(--card);border-color:var(--line)}
.mc.up span{opacity:1}
.mc.ok{background:var(--bar)}
.tg{display:grid;grid-template-columns:repeat(3,1fr);gap:8px;max-width:270px;margin:0 auto}
.tc{aspect-ratio:1;border:1px solid var(--line);border-radius:12px;background:var(--card);font-size:36px;font-weight:800;line-height:1;cursor:pointer}
.tc:disabled{cursor:default}
.grp{margin-bottom:18px}
.grp h3{margin:0 0 8px;font-size:13px;font-weight:600;color:var(--mut)}
.seg{display:flex;gap:6px}
.seg button{flex:1;padding:8px;border:1px solid var(--line);border-radius:9px;background:var(--card);color:var(--ink);cursor:pointer}
.seg button[aria-pressed=true]{border-color:var(--accent);box-shadow:inset 0 0 0 1px var(--accent);font-weight:700}
.sw{display:flex;gap:10px}
.sw button{width:36px;height:36px;border-radius:50%;border:3px solid transparent;cursor:pointer;background-clip:padding-box}
.sw button[aria-pressed=true]{border-color:var(--ink)}
.gs{flex:1;min-width:0;padding:8px 12px;border:1px solid var(--line);border-radius:10px;background:var(--card);color:var(--ink);font:inherit}
textarea{flex:1;width:100%;min-height:200px;padding:10px;border:1px solid var(--line);border-radius:10px;background:var(--card);color:var(--ink);font:inherit;resize:none}
#media,#fx,#rain{position:absolute;inset:0;width:100%;height:100%;max-width:none;margin:0;border:0;border-radius:0;pointer-events:none}
#media{background:center/cover no-repeat}
#desk[data-wall=custom]{background:#0b3b4a}
#desk[data-wall=stars]{background:radial-gradient(900px 600px at 50% 50%,#1b2a5e,#050b1e 70%)}
#desk[data-wall=waves]{background:linear-gradient(180deg,#0a1f3d,#0b3b4a 60%,#0f766e)}
#desk[data-wall=aurora]{background:linear-gradient(120deg,#0b1d3a,#0f766e,#6d28d9,#0b3b4a,#0f766e);background-size:300% 300%}
.icons{z-index:1}
.seg{flex-wrap:wrap}.seg button{flex:1 0 28%}
.ic,.ic i,.gc{transition:transform .18s cubic-bezier(.2,.8,.2,1),background .18s,border-color .18s}
@media(prefers-reduced-motion:no-preference){
#desk[data-wall=aurora]{animation:flow 22s ease-in-out infinite}
@keyframes flow{50%{background-position:100% 60%}}
.win{animation:pop .24s cubic-bezier(.2,.8,.2,1)}
@keyframes pop{from{opacity:0;transform:scale(.9) translateY(16px)}}
.win.bye{animation:out .15s ease forwards}
@keyframes out{to{opacity:0;transform:scale(.94) translateY(10px)}}
#menu{animation:pop .16s cubic-bezier(.2,.8,.2,1)}
.ic:hover i{transform:translateY(-4px) scale(1.08)}
.ic:active i{transform:scale(.9)}
.ic.go i{animation:hop .5s cubic-bezier(.3,1.6,.5,1)}
@keyframes hop{30%{transform:translateY(-14px) scale(1.12)}}
.gc:hover{transform:translateX(4px)}
}
.gl{display:grid;grid-template-columns:repeat(auto-fill,minmax(150px,1fr));gap:10px;align-content:start}
.gl .gc{display:block;margin:0;padding:0;overflow:hidden}
.gl .gc:hover{transform:translateY(-3px)}
.th{aspect-ratio:16/10;display:grid;place-items:center;font-size:46px;line-height:1}
.gl .gc b{display:block;padding:8px 10px 0}.gl .gc small{padding:0 10px 10px}
:root{--accent2:#8b5cf6;--accent3:#f59e0b}
.icons{display:flex;flex-direction:column;flex-wrap:wrap;align-content:flex-start;gap:8px;max-height:calc(100% - 90px - env(safe-area-inset-bottom,0px))}
.btn,#start{position:relative;overflow:hidden;background:linear-gradient(135deg,var(--accent),var(--accent2));color:var(--onacc);box-shadow:0 3px 10px rgba(0,0,0,.22),inset 0 1px 0 rgba(255,255,255,.35);transition:transform .15s,filter .15s}
.btn::after,#start::after,.ic i::after,.gc::after{content:"";position:absolute;inset:0;background:linear-gradient(105deg,transparent 35%,rgba(255,255,255,.55) 50%,transparent 65%);transform:translateX(-130%);pointer-events:none}
.btn:hover,#start:hover{transform:translateY(-1px);filter:brightness(1.07)}
.btn:active,#start:active{transform:scale(.96)}
.btn:disabled{filter:grayscale(.4);cursor:default}
.ic i{position:relative;overflow:hidden;background:linear-gradient(135deg,var(--accent),var(--accent2))}
.ic:nth-child(3n+2) i{background:linear-gradient(135deg,var(--accent2),var(--accent3))}
.ic:nth-child(3n) i{background:linear-gradient(135deg,var(--accent3),var(--accent))}
.win header{position:relative}
.win header::after{content:"";position:absolute;left:0;right:0;bottom:-1px;height:2px;background:linear-gradient(90deg,var(--accent),var(--accent2),var(--accent3))}
.gc{position:relative;overflow:hidden}
.gc:hover{border-color:var(--accent2)}
.seg button{transition:border-color .15s,transform .15s}
.seg button:hover{border-color:var(--accent2);transform:translateY(-1px)}
.tab.on{box-shadow:inset 0 -3px 0 var(--accent2)}
#menu{max-height:62vh;overflow:auto}
#menu button:hover{box-shadow:inset 3px 0 0 var(--accent2)}
.pad button:active{background:var(--accent);color:var(--onacc)}
@media(prefers-reduced-motion:no-preference){
@keyframes shine{0%{transform:translateX(-130%)}40%,100%{transform:translateX(130%)}}
.btn::after,#start::after{animation:shine 4s 1.2s infinite}
.btn:hover::after,#start:hover::after,.ic:hover i::after,.gc:hover::after{animation:shine .7s}
}
.st{cursor:default;gap:12px}.st:hover{transform:none}.st>span:first-of-type{flex:1}
.sb{display:flex;align-items:center}
.pb{position:absolute;left:0;right:0;bottom:0;height:3px;background:var(--line)}
.pb i{display:block;height:100%;width:0;background:linear-gradient(90deg,var(--accent),var(--accent2),var(--accent3));transition:width 1.1s cubic-bezier(.3,.7,.3,1)}
.x{border:0;background:none;color:var(--mut);cursor:pointer;margin-left:8px;text-decoration:underline}
.cd{padding:12px 14px;margin-bottom:10px;border-radius:12px;background:var(--card);border:1px solid var(--line);text-align:right;min-height:74px}
.cd small{display:block;color:var(--mut);min-height:18px}.cd b{font-size:34px;font-weight:800;word-break:break-all}
.ck{display:grid;grid-template-columns:repeat(4,1fr);gap:8px}
.ck button{padding:14px 0;border:1px solid var(--line);border-radius:12px;background:var(--card);color:var(--ink);font-size:18px;cursor:pointer;transition:transform .12s}
.ck button:active{transform:scale(.94)}
.ck .op{border:0;background:linear-gradient(135deg,var(--accent),var(--accent2));color:var(--onacc);font-weight:800}
.big{font-size:40px;font-weight:800;line-height:1.1;margin:6px 0 12px;font-variant-numeric:tabular-nums}
.laps{margin:10px 0 0;padding-left:22px;color:var(--mut)}
.ti{display:flex;gap:10px;align-items:center;padding:10px;border:1px solid var(--line);border-radius:10px;background:var(--card);margin-bottom:6px}
.ti span{flex:1}.ti input{accent-color:var(--accent)}.dn{text-decoration:line-through;color:var(--mut)}
.pk{position:relative;display:flex;height:170px;border-radius:10px;overflow:hidden;border:1px solid var(--line)}
.wk{flex:1;border:0;border-right:1px solid var(--line);background:#fff;cursor:pointer}
.wk.on{background:linear-gradient(180deg,#fff,var(--accent))}
.bk{position:absolute;top:0;width:7%;height:62%;border:0;border-radius:0 0 6px 6px;background:#13262a;cursor:pointer;z-index:1}
.bk.on{background:var(--accent2)}
.cg{display:grid;grid-template-columns:repeat(7,1fr);gap:4px;text-align:center}
.cg i{font-style:normal;color:var(--mut);font-size:12px}
.cg span{padding:8px 0;border-radius:9px;background:var(--card)}
.cg .td{background:linear-gradient(135deg,var(--accent),var(--accent2));color:var(--onacc);font-weight:800}
.am{flex:1;overflow:auto;padding:14px;display:flex;flex-direction:column;gap:10px}
.ms{max-width:86%;padding:10px 12px;border-radius:14px;line-height:1.5;word-break:break-word}
.ms.ai{align-self:flex-start;background:var(--card);border:1px solid var(--line)}
.ms.me{align-self:flex-end;background:linear-gradient(135deg,var(--accent),var(--accent2));color:var(--onacc)}
.ms pre{overflow:auto;background:var(--bar);padding:8px;border-radius:8px;margin:6px 0}
.ms code{background:var(--bar);padding:1px 5px;border-radius:5px}
.ar{display:flex;align-items:center;gap:8px;padding:10px 12px;border-top:1px solid var(--line);background:var(--win)}
.chips{display:flex;flex-wrap:wrap;gap:6px}
.chips button{border:1px solid var(--line);background:var(--card);color:var(--ink);border-radius:999px;padding:6px 12px;cursor:pointer;transition:border-color .15s,transform .15s}
.chips button:hover{border-color:var(--accent2);transform:translateY(-1px)}
.chip{display:grid;place-items:center;height:36px;min-width:36px;padding:0 10px;border:1px solid var(--line);border-radius:10px;background:none;color:var(--ink);font-weight:700;cursor:pointer;white-space:nowrap;transition:border-color .15s,transform .15s}
.chip:hover{border-color:var(--accent2);transform:translateY(-1px)}
.chip img{display:block;width:26px;height:26px;border-radius:50%}
.acc{display:flex;align-items:center;gap:14px;padding:14px;margin-bottom:14px;border-radius:14px;background:linear-gradient(135deg,var(--card),var(--bar));border:1px solid var(--line)}
.av{display:grid;place-items:center;width:56px;height:56px;flex:none;border-radius:50%;background:linear-gradient(135deg,var(--accent),var(--accent2));font-size:28px;overflow:hidden}
.acc b{display:block;font-size:18px}.acc small,.note{color:var(--mut)}
.sts{display:grid;grid-template-columns:repeat(3,1fr);gap:8px;margin-bottom:14px}
.sts div{padding:14px 6px;border-radius:12px;background:var(--card);border:1px solid var(--line);text-align:center}
.sts b{display:block;font-size:28px;font-weight:800;background:linear-gradient(135deg,var(--accent),var(--accent2));-webkit-background-clip:text;background-clip:text;color:transparent}
.sts small{color:var(--mut)}
.ti small{color:var(--mut)}
.h3{margin:0 0 8px;font-size:13px;font-weight:600;color:var(--mut)}
.vl{margin:0 0 12px}
#ann{position:fixed;top:calc(10px + env(safe-area-inset-top,0px));left:50%;transform:translateX(-50%);z-index:9990;display:flex;align-items:center;gap:12px;max-width:min(560px,92vw);padding:10px 12px 10px 16px;border-radius:12px;background:linear-gradient(135deg,var(--accent),var(--accent2));color:var(--onacc);font-weight:600;box-shadow:var(--shadow)}
#ann button{border:0;border-radius:8px;background:rgba(255,255,255,.4);color:inherit;cursor:pointer;padding:4px 8px}
#boot{position:fixed;inset:0;z-index:99999;display:grid;place-items:center;background:linear-gradient(180deg,#06161d,#0b2f3a);color:#e8fffb;transition:opacity .6s,transform .6s}
#boot.out{opacity:0;transform:scale(1.03);pointer-events:none}
#rain{position:absolute;inset:0;width:100%;height:100%}
.bc{position:relative;width:min(280px,72vw);text-align:center}
.bc h1{margin:0 0 22px;font-size:48px;font-weight:800;letter-spacing:-.02em}
.bar{height:4px;border-radius:4px;background:rgba(255,255,255,.14);overflow:hidden}
.bar i{display:block;height:100%;width:0;border-radius:4px;background:linear-gradient(90deg,#2dd4bf,#7dd3fc);box-shadow:0 0 12px rgba(45,212,191,.8)}
.pc{margin:10px 0 0;font-size:12px;color:#8fb8b2}
@media(prefers-reduced-motion:reduce){.mc span{transition:none}}
</style>
</head>
<body>
<div id="desk"><div id="media"></div><canvas id="fx"></canvas><nav class="icons" aria-label="Desktop"></nav></div>
<div id="menu" hidden></div>
<div id="bar"><button id="start"><span class="dot"></span>Oasis</button><div id="tasks"></div><button class="chip" id="cnt" aria-label="Visitor stats">👥 –</button><button class="chip" id="acct" aria-label="Account">👤</button><div id="clk"></div></div>
<div id="boot"><canvas id="rain"></canvas><div class="bc"><h1>Oasis.OS</h1><div class="bar"><i></i></div><p class="pc">Starting up… 0%</p></div></div>
<script>
const $=(s,r=document)=>r.querySelector(s),desk=$('#desk'),menu=$('#menu');
const ls=(k,v)=>{try{if(v===undefined)return localStorage.getItem(k);localStorage.setItem(k,v)}catch(e){return null}};
const DEF={theme:'auto',accent:'#14b8a6',wall:'lagoon',h24:false},S={...DEF};
try{Object.assign(S,JSON.parse(ls('oasis-s')||'{}'))}catch(e){}
S.apps=S.apps||[];if(S.sync===undefined)S.sync=true;
const save=()=>{ls('oasis-s',JSON.stringify(S));push()};
let DB=null,U=null,ME=null,UID=null,pt,ADMIN=false,WL=[];
function push(){if(!DB||!UID||!S.sync)return;clearTimeout(pt);pt=setTimeout(()=>{DB.doc('data/users/'+UID+'/profile').set({theme:S.theme,accent:S.accent,wall:S.wall,h24:S.h24,apps:S.apps}).catch(()=>{})},800)}
async function pull(){try{const sn=await DB.doc('data/users/'+UID+'/profile').get();if(sn.exists&&S.sync){const c=sn.data();['theme','accent','wall','h24'].forEach(k=>{if(k in c)S[k]=c[k]});if(Array.isArray(c.apps))S.apps=c.apps;ls('oasis-s',JSON.stringify(S));apply();shell()}}catch(e){}}
async function track(){try{const r=DB.doc('visitors/'+UID),sn=await r.get(),d=sn.exists?sn.data():{},n=Date.now();await r.set({visits:(d.visits||0)+(n-(d.last||0)>1800000?1:0),first:d.first||n,last:n})}catch(e){}}
async function stats(){if(!DB)return null;try{const q=await DB.collection('visitors').get(),n=Date.now();let t=0,a=0;const rows=[];q.docs.forEach(d=>{const x=d.data()||{};t+=x.visits||0;if(n-(x.last||0)<864e5)a++;rows.push({id:d.id,last:x.last||0,visits:x.visits||0})});return{u:q.size,t,a,rows}}catch(e){return null}}
async function refreshCount(){const r=await stats();$('#cnt').textContent=r?'👥 '+r.u:'👥 –'}
function paintAcct(){const a=$('#acct');if(UID&&ME&&ME.avatarUrl){const i=new Image();i.src=ME.avatarUrl;i.alt='';a.replaceChildren(i)}else a.textContent='👤'}
function banner(t){if($('#ann'))return;const d=document.createElement('div');d.id='ann';d.setAttribute('role','status');const m=document.createElement('span'),x=document.createElement('button');m.textContent=t;x.textContent='Dismiss';x.onclick=()=>d.remove();d.append(m,x);document.body.append(d)}
async function loadAdmin(){if(!DB)return;try{const w=await DB.doc('admin/whitelist').get();WL=w.exists&&Array.isArray(w.data().ids)?w.data().ids:[]}catch(e){}
 ADMIN=!!(ME&&(ME.isOwner||(UID&&WL.includes(UID))));shell();
 try{const a=await DB.doc('admin/announcement').get();if(a.exists&&a.data().text)banner(a.data().text)}catch(e){}}
async function boot2(){
 $('#cnt').onclick=()=>open('stats');$('#acct').onclick=()=>open('account');
 if(typeof claude==='undefined')return;
 try{U=await claude.use('user');if(U){ME=await U.me();UID=await U.id()}DB=await claude.use('db')}catch(e){}
 paintAcct();if(DB&&UID){await pull();await track()}refreshCount();loadAdmin();
}
const clamp=(v,a,b)=>Math.max(a,Math.min(b,v)),css=v=>getComputedStyle(document.documentElement).getPropertyValue(v).trim();
function hs(h,d){const r=parseInt(h.slice(1,3),16)/255,g=parseInt(h.slice(3,5),16)/255,b=parseInt(h.slice(5,7),16)/255,mx=Math.max(r,g,b),mn=Math.min(r,g,b),dl=mx-mn;let H=0;if(dl){H=mx==r?((g-b)/dl)%6:mx==g?(b-r)/dl+2:(r-g)/dl+4;H*=60}return`hsl(${((H+d)%360+360)%360} 80% 62%)`}
let AC;function tone(f,d=.35){try{AC=AC||new(window.AudioContext||window.webkitAudioContext)();const o=AC.createOscillator(),g=AC.createGain(),t=AC.currentTime;o.type='triangle';o.frequency.value=f;g.gain.setValueAtTime(.0001,t);g.gain.exponentialRampToValueAtTime(.3,t+.01);g.gain.exponentialRampToValueAtTime(.0001,t+d);o.connect(g);g.connect(AC.destination);o.start();o.stop(t+d+.02)}catch(e){}}
const idb=(m,v)=>new Promise(r=>{try{const q=indexedDB.open('oasis',1);q.onupgradeneeded=()=>q.result.createObjectStore('k');q.onsuccess=()=>{const o=q.result.transaction('k',m=='get'?'readonly':'readwrite').objectStore('k'),x=m=='get'?o.get('bg'):o.put(v,'bg');x.onsuccess=()=>r(x.result);x.onerror=()=>r()};q.onerror=()=>r()}catch(e){r()}});
let lw,raf;const fx=$('#fx'),cx=fx.getContext('2d');
const fit=()=>{fx.width=innerWidth;fx.height=innerHeight};addEventListener('resize',fit);fit();
function loadBg(blob){const m=$('#media');m.innerHTML='';m.style.backgroundImage='';if(!blob)return;const u=URL.createObjectURL(blob);
 if(blob.type.startsWith('video')){const v=document.createElement('video');Object.assign(v,{src:u,autoplay:true,muted:true,loop:true,playsInline:true});v.setAttribute('style','width:100%;height:100%;object-fit:cover');m.append(v);v.play().catch(()=>{})}
 else m.style.backgroundImage=`url(${u})`}
function runFx(){cancelAnimationFrame(raf);cx.clearRect(0,0,fx.width,fx.height);const m=S.wall;
 if(matchMedia('(prefers-reduced-motion:reduce)').matches||(m!='stars'&&m!='waves'))return;
 const st=Array.from({length:140},()=>({a:Math.random()*6.28,r:Math.random(),s:.002+Math.random()*.004}));
 (function f(t){const W=fx.width,H=fx.height;cx.clearRect(0,0,W,H);
  if(m=='stars'){cx.fillStyle='#fff';st.forEach(p=>{p.r+=p.s*(1+p.r*2);if(p.r>1){p.r=.02;p.a=Math.random()*6.28}const d=p.r*Math.hypot(W,H)/2;cx.globalAlpha=Math.min(1,p.r*1.6);cx.fillRect(W/2+Math.cos(p.a)*d,H/2+Math.sin(p.a)*d,1+p.r*2.5,1+p.r*2.5)})}
  else for(let k=0;k<4;k++){cx.beginPath();cx.moveTo(0,H);for(let x=0;x<=W;x+=12)cx.lineTo(x,H*(.55+k*.1)+Math.sin(x/(140+k*50)+t/(1400-k*200)+k)*(18+k*8));cx.lineTo(W,H);cx.fillStyle=S.accent;cx.globalAlpha=.12+k*.06;cx.fill()}
  cx.globalAlpha=1;raf=requestAnimationFrame(f)})(0)}
function apply(){const r=document.documentElement;S.theme=='auto'?r.removeAttribute('data-theme'):r.dataset.theme=S.theme;r.style.setProperty('--accent',S.accent);r.style.setProperty('--accent2',hs(S.accent,45));r.style.setProperty('--accent3',hs(S.accent,-55));desk.dataset.wall=S.wall;if(S.wall!==lw){lw=S.wall;runFx();S.wall=='custom'?idb('get').then(loadBg):loadBg()}tick()}
function tick(){const d=new Date();$('#clk').innerHTML=d.toLocaleTimeString([],{hour:'numeric',minute:'2-digit',hour12:!S.h24})+'<span>'+d.toLocaleDateString([],{weekday:'short',month:'short',day:'numeric'})+'</span>'}

const G=[];
G.push(['Snake','Arcade · built in','🐍','app:snake'],['Memory','Puzzle · built in','🐚','app:memory'],['Tic-Tac-Toe','Board · built in','⭕','app:ttt']);
G.unshift(['Territory Rush','Multiplayer-style · built in','🟩','app:territory'],['Tag Arena','Chase · built in','🏃','app:tag'],['Blob Feast','Eat or be eaten · built in','🟣','app:blob'],['Soccer Random','Sports · built in','⚽','app:soccer'],['Breakout','Arcade · built in','🧱','app:breakout'],['Pong','Arcade · built in','🏓','app:pong']);
const gid=i=>G[i][3].slice(4);
const APPS={
 games:{t:'Games',i:'🎮',w:500,h:580,b:gamesApp},
 random:{t:'Random game',i:'🎲'},
 soccer:{t:'Soccer Random',i:'⚽',w:520,h:470,b:soccerApp},
 breakout:{t:'Breakout',i:'🧱',w:370,h:470,b:breakoutApp},
 territory:{t:'Territory Rush',i:'🟩',w:440,h:540,b:territoryApp},
 tag:{t:'Tag Arena',i:'🏃',w:440,h:480,b:tagApp},
 blob:{t:'Blob Feast',i:'🟣',w:440,h:510,b:blobApp},
 admin:{t:'Admin Panel',i:'🛡️',w:480,h:560,b:adminApp},
 account:{t:'Account',i:'👤',w:400,h:430,b:accountApp},
 stats:{t:'Visitors',i:'📊',w:420,h:460,b:statsApp},
 ai:{t:'Oasis AI',i:'✨',w:440,h:560,b:aiApp},
 store:{t:'Oasis Store',i:'🛍️',w:440,h:540,b:storeApp},
 calc:{t:'Calculator',i:'🧮',w:320,h:480,b:calcApp},
 paint:{t:'Sketchpad',i:'🎨',w:560,h:450,b:paintApp},
 timer:{t:'Stopwatch & Timer',i:'⏱️',w:360,h:480,b:timerApp},
 tasks:{t:'Tasks',i:'✅',w:360,h:430,b:tasksApp},
 piano:{t:'Piano',i:'🎹',w:520,h:280,b:pianoApp},
 cal:{t:'Calendar',i:'📅',w:380,h:420,b:calApp},
 pong:{t:'Pong',i:'🏓',w:450,h:400,b:pongApp},
 snake:{t:'Snake',i:'🐍',w:360,h:470,b:snakeApp},
 memory:{t:'Memory',i:'🐚',w:380,h:440,b:memApp},
 ttt:{t:'Tic-Tac-Toe',i:'⭕',w:340,h:410,b:tttApp},
 notes:{t:'Notes',i:'📝',w:380,h:340,b:notesApp},
 settings:{t:'Settings',i:'⚙️',w:400,h:580,b:settingsApp}
};
let z=10,act=null;const wins={};

function open(id){
 menu.hidden=true;
 if(id=='random'){return open(gid(Math.random()*G.length|0))}
 if(wins[id])return show(id);
 const a=APPS[id],w=document.createElement('section'),n=Object.keys(wins).length;
 w.className='win';w.setAttribute('role','dialog');w.setAttribute('aria-label',a.t);
 w.style.cssText=`width:${a.w}px;height:${Math.min(a.h,innerHeight-90)}px;left:${Math.min(110+n*30,Math.max(0,innerWidth-a.w-10))}px;top:${40+n*30}px`;
 w.innerHTML=`<header><b>${a.i} ${a.t}</b><span><button data-a="min" aria-label="Minimize">–</button><button data-a="max" aria-label="Maximize">▢</button><button data-a="close" aria-label="Close">✕</button></span></header><div class="body"></div>`;
 desk.append(w);
 const o=wins[id]={id,el:w,off:null},hd=$('header',w);
 o.off=a.b($('.body',w));
 w.addEventListener('pointerdown',()=>wins[id]&&focus(id));
 hd.onclick=e=>{const x=e.target.closest('button');if(!x)return;const k=x.dataset.a;k=='close'?close(id):k=='min'?min(id):w.classList.toggle('max')};
 hd.onpointerdown=e=>{
  if(e.target.closest('button')||innerWidth<=640||w.classList.contains('max'))return;
  const dx=e.clientX-w.offsetLeft,dy=e.clientY-w.offsetTop;hd.setPointerCapture(e.pointerId);
  hd.onpointermove=m=>{w.style.left=Math.max(80-w.offsetWidth,Math.min(innerWidth-80,m.clientX-dx))+'px';w.style.top=Math.max(0,Math.min(innerHeight-110,m.clientY-dy))+'px'};
  hd.onpointerup=()=>{hd.onpointermove=null};
 };
 focus(id);
}
function focus(id){act=id;for(const k in wins)wins[k].el.classList.toggle('top',k==id);wins[id].el.style.zIndex=++z;tabs()}
function show(id){wins[id].el.hidden=false;focus(id)}
function min(id){const w=wins[id].el;w.classList.add('bye');setTimeout(()=>{w.hidden=true;w.classList.remove('bye')},150);if(act==id)act=null;tabs()}
function close(id){const o=wins[id];o.off&&o.off();o.el.classList.add('bye');setTimeout(()=>o.el.remove(),150);delete wins[id];if(act==id)act=null;tabs()}
function tabs(){$('#tasks').innerHTML=Object.keys(wins).map(k=>`<button class="tab${k==act&&!wins[k].el.hidden?' on':''}" data-t="${k}">${APPS[k].i} ${APPS[k].t}</button>`).join('')}
$('#tasks').onclick=e=>{const t=e.target.closest('[data-t]');if(!t)return;const id=t.dataset.t;(wins[id].el.hidden||act!=id)?show(id):min(id)};
desk.onclick=e=>{const o=e.target.closest('.ic');if(o){o.classList.add('go');setTimeout(()=>o.classList.remove('go'),500);open(o.dataset.o)}};

const CORE=['ai','games','random','notes','settings','store','account','stats'];
function shell(){S.apps=S.apps.filter(k=>APPS[k]);
 $('.icons').innerHTML=[...CORE,...(ADMIN?['admin']:[]),...S.apps].map(k=>`<button class="ic" data-o="${k}"><i>${APPS[k].i}</i>${APPS[k].t}</button>`).join('');
 menu.innerHTML=['ai','account','stats','games','random','store','territory','tag','blob','soccer','breakout','pong','snake','memory','ttt','notes','settings',...(ADMIN?['admin']:[]),...S.apps].map(k=>`<button data-o="${k}">${APPS[k].i} ${APPS[k].t}</button>`).join('')}
shell();
menu.onclick=e=>{const o=e.target.closest('[data-o]');if(o)open(o.dataset.o)};
$('#start').onclick=()=>{menu.hidden=!menu.hidden};
document.addEventListener('pointerdown',e=>{if(!e.target.closest('#menu,#start'))menu.hidden=true});

function gamesApp(b){
 b.style.cssText='display:flex;flex-direction:column;gap:10px';
 b.innerHTML=`<div style="display:flex;gap:8px"><input type="search" class="gs" placeholder="Search ${G.length} games" aria-label="Search games"><button class="btn" data-rand>🎲 Random</button></div><div class="gl" style="flex:1;overflow:auto"></div>`;
 const L=$('.gl',b),q=$('.gs',b),X=[['Paper.io','Online game','🟩','https://paper-io.com/'],['Tag','Online · 2-4 players','🏃','https://poki.com/en/g/tag'],['Tag 2','Online · 2-4 players','🏃','https://poki.com/en/g/tag-2'],['Monkey Tag IO','Online game','🐒','https://poki.com/en/g/monkey-tag-arena'],['Slither.io','Online game','🐍','https://slither.io/'],['Agar.io','Online game','🟣','https://agar.io/'],['Diep.io','Online game','🔫','https://diep.io/'],['Krunker','Online shooter','🎯','https://krunker.io/'],['Shell Shockers','Online shooter','🥚','https://shellshock.io/'],['Smash Karts','Online racing','🏁','https://smashkarts.io/'],['Skribbl.io','Online drawing','🖍️','https://skribbl.io/'],['Stickman Hook','Online arcade','🪝','https://poki.com/en/g/stickman-hook']];
 const links=v=>{const r=X.filter(g=>!v||(g[0]+' '+g[1]).toLowerCase().includes(v));return r.length?'<h3 style="grid-column:1/-1;margin:8px 0 0;font-size:13px;color:var(--mut)">Real games on their own sites (open in a new tab)</h3>'+r.map(g=>{const h=Math.abs([...g[0]].reduce((a,c)=>a*31+c.charCodeAt(0)|0,7))%360;return`<a class="gc" href="${g[3]}" target="_blank" rel="noopener noreferrer" style="text-decoration:none"><div class="th" style="background:linear-gradient(135deg,hsl(${h} 70% 46%),hsl(${(h+55)%360} 70% 28%))">${g[2]}</div><b>${g[0]}</b><small>${g[1]}</small></a>`}).join(''):''};
 const list=()=>{const v=q.value.trim().toLowerCase(),r=G.map((g,i)=>[g,i]).filter(([g])=>!v||(g[0]+' '+g[1]).toLowerCase().includes(v));
  L.innerHTML=(r.length?r.map(([g,i])=>{const h=Math.abs([...g[0]].reduce((a,c)=>a*31+c.charCodeAt(0)|0,7))%360;return`<button class="gc" data-i="${i}"><div class="th" style="background:linear-gradient(135deg,hsl(${h} 70% 46%),hsl(${(h+55)%360} 70% 28%))">${g[2]}</div><b>${g[0]}</b><small>${g[1]}</small></button>`}).join(''):'<p class="hint" style="grid-column:1/-1">No built-in games match.</p>')+links(v)};
 q.oninput=list;
 b.onclick=e=>{const c=e.target.closest('[data-i]');if(c)open(gid(+c.dataset.i));else if(e.target.closest('[data-rand]'))open('random')};
 list();
}

function snakeApp(b){
 const N=16,C=19,K={ArrowUp:[0,-1],w:[0,-1],ArrowDown:[0,1],s:[0,1],ArrowLeft:[-1,0],a:[-1,0],ArrowRight:[1,0],d:[1,0]};
 b.innerHTML=`<div class="gh"><span>Score <b class="sc">0</b></span><span>Best <b class="bs">0</b></span></div><canvas width="304" height="304" aria-label="Snake board"></canvas><div class="pad"><i></i><button data-v="0,-1" aria-label="Up">▲</button><i></i><button data-v="-1,0" aria-label="Left">◀</button><button data-v="0,1" aria-label="Down">▼</button><button data-v="1,0" aria-label="Right">▶</button></div><p class="hint">Arrow keys or WASD to steer. Space restarts.</p>`;
 const g=$('canvas',b).getContext('2d');let s,d,nd,f,sc,dead,best=+ls('snake')||0;
 const food=()=>{do f={x:Math.random()*N|0,y:Math.random()*N|0};while(s.some(p=>p.x==f.x&&p.y==f.y))};
 const upd=()=>{if(sc>best){best=sc;ls('snake',best)}$('.sc',b).textContent=sc;$('.bs',b).textContent=best};
 const reset=()=>{s=[{x:8,y:8},{x:7,y:8},{x:6,y:8}];d=nd={x:1,y:0};sc=0;dead=false;food();upd();draw()};
 const turn=v=>{if(!(v[0]==-d.x&&v[1]==-d.y))nd={x:v[0],y:v[1]}};
 function step(){
  if(dead||act!=='snake')return;d=nd;const h={x:s[0].x+d.x,y:s[0].y+d.y};
  if(h.x<0||h.y<0||h.x>=N||h.y>=N||s.some(p=>p.x==h.x&&p.y==h.y)){dead=true;return draw()}
  s.unshift(h);if(h.x==f.x&&h.y==f.y){sc++;food()}else s.pop();upd();draw();
 }
 function draw(){
  const cs=getComputedStyle(document.documentElement),cl=v=>cs.getPropertyValue(v).trim();
  g.fillStyle=cl('--card');g.fillRect(0,0,304,304);
  g.fillStyle='#f59e0b';g.beginPath();g.arc(f.x*C+C/2,f.y*C+C/2,C/2-3,0,7);g.fill();
  g.fillStyle=cl('--accent');s.forEach((p,i)=>{g.globalAlpha=i?.8:1;g.fillRect(p.x*C+1,p.y*C+1,C-2,C-2)});g.globalAlpha=1;
  if(dead){g.fillStyle='rgba(0,0,0,.6)';g.fillRect(0,0,304,304);g.fillStyle='#fff';g.textAlign='center';g.font='700 24px Figtree,sans-serif';g.fillText('Game over',152,148);g.font='14px Figtree,sans-serif';g.fillText('Space or tap to play again',152,174)}
 }
 const key=e=>{if(act!=='snake')return;const k=e.key.length==1?e.key.toLowerCase():e.key;if(K[k]){e.preventDefault();turn(K[k])}else if(k==' '){e.preventDefault();if(dead)reset()}};
 addEventListener('keydown',key);
 b.onclick=e=>{const p=e.target.closest('.pad button');if(p)turn(p.dataset.v.split(',').map(Number));else if(e.target.tagName=='CANVAS'&&dead)reset()};
 const t=setInterval(step,115);reset();
 return()=>{clearInterval(t);removeEventListener('keydown',key)};
}

function memApp(b){
 const E=['🌴','🐚','🌊','🦀','🐠','🌵','☀️','🐪'];let cards,open=[],lock,moves,found;
 b.innerHTML=`<div class="gh"><span>Moves <b class="mv">0</b></span><span class="msg"></span><button class="btn" data-r>New game</button></div><div class="mg"></div>`;
 const grid=$('.mg',b);
 function deal(){cards=[...E,...E].sort(()=>Math.random()-.5);open=[];moves=found=0;lock=false;$('.mv',b).textContent=0;$('.msg',b).textContent='';grid.innerHTML=cards.map((c,i)=>`<button class="mc" data-i="${i}" aria-label="Card ${i+1}"><span>${c}</span></button>`).join('')}
 b.onclick=e=>{
  if(e.target.closest('[data-r]'))return deal();
  const c=e.target.closest('.mc');if(!c||lock||c.classList.contains('up'))return;
  c.classList.add('up');open.push(c);
  if(open.length==2){
   $('.mv',b).textContent=++moves;const [p,q]=open;
   if(cards[p.dataset.i]==cards[q.dataset.i]){p.classList.add('ok');q.classList.add('ok');open=[];if(++found==8)$('.msg',b).textContent='Cleared!'}
   else{lock=true;setTimeout(()=>{p.classList.remove('up');q.classList.remove('up');open=[];lock=false},700)}
  }
 };
 deal();
}

function tttApp(b){
 const W=[[0,1,2],[3,4,5],[6,7,8],[0,3,6],[1,4,7],[2,5,8],[0,4,8],[2,4,6]];let B=Array(9).fill(0),done=false;
 const win=X=>{for(const[a,c,d]of W)if(X[a]&&X[a]==X[c]&&X[a]==X[d])return X[a];return X.includes(0)?null:'T'};
 function mm(X,p){const w=win(X);if(w)return w=='O'?1:w=='X'?-1:0;let r=p=='O'?-2:2;for(let i=0;i<9;i++)if(!X[i]){X[i]=p;const v=mm(X,p=='O'?'X':'O');X[i]=0;r=p=='O'?Math.max(r,v):Math.min(r,v)}return r}
 function ai(){const m=[];B.forEach((v,i)=>v||m.push(i));if(!m.length)return;let pick,bv=-2;
  if(Math.random()<.3)pick=m[Math.random()*m.length|0];
  else m.forEach(i=>{B[i]='O';const v=mm(B,'X');B[i]=0;if(v>bv){bv=v;pick=i}});
  B[pick]='O'}
 function render(){const w=win(B);done=!!w;
  b.innerHTML=`<div class="gh"><b>${w=='X'?'You win!':w=='O'?'Computer wins':w=='T'?'It’s a draw':'Your move'}</b><button class="btn" data-r>New game</button></div><div class="tg">${B.map((v,i)=>`<button class="tc" data-i="${i}" ${v||done?'disabled':''} aria-label="Cell ${i+1}: ${v||'empty'}" style="color:${v=='O'?'var(--accent)':'var(--ink)'}">${v||''}</button>`).join('')}</div>`}
 b.onclick=e=>{
  if(e.target.closest('[data-r]')){B=Array(9).fill(0);return render()}
  const c=e.target.closest('.tc');if(!c||done)return;
  B[c.dataset.i]='X';if(!win(B))ai();render();
 };
 render();
}


function keysFor(id){const k={},f=e=>{if(act!==id)return;const n=e.key.length==1?e.key.toLowerCase():e.key;k[n]=e.type=='keydown';if(n.startsWith('Arrow')||n==' ')e.preventDefault()};addEventListener('keydown',f);addEventListener('keyup',f);return[k,()=>{removeEventListener('keydown',f);removeEventListener('keyup',f)}]}

function soccerApp(b){
 const W=480,H=270,GY=H-18,GH=90;
 b.innerHTML=`<div class="gh"><span>You <b class="a">0</b> – <b class="c">0</b> CPU</span><span class="rn"></span></div><canvas width="480" height="270" style="max-width:480px" aria-label="Soccer Random pitch"></canvas><div class="pad" style="grid-template-columns:repeat(4,54px)"><button data-k="l">◀</button><button data-k="r">▶</button><button data-k="u">▲</button><button data-k="k">⚽</button></div><p class="hint">A/D or arrows move, W or Up jumps, Space kicks. First to 5 wins. Every goal re-rolls the physics.</p>`;
 const g=$('canvas',b).getContext('2d'),[K,off]=keysFor('soccer');let sc=[0,0],R,P,Bl,msg='',mt=0;
 b.querySelectorAll('.pad button').forEach(x=>{const k=x.dataset.k;x.onpointerdown=()=>K[k]=true;x.onpointerup=x.onpointerleave=()=>K[k]=false});
 function roll(){const G1=[['Low gravity',.22],['Normal gravity',.5],['Heavy gravity',.8]][Math.random()*3|0],B1=[['tiny ball',7],['normal ball',12],['big ball',19]][Math.random()*3|0],P1=[['small players',17],['normal players',24],['giant players',32]][Math.random()*3|0];
  R={g:G1[1],br:B1[1],pr:P1[1]};$('.rn',b).textContent=`${G1[0]}, ${B1[0]}, ${P1[0]}`;
  P=[{x:100,y:GY-R.pr,vx:0,vy:0},{x:W-100,y:GY-R.pr,vx:0,vy:0}];Bl={x:W/2,y:60,vx:0,vy:0}}
 function goal(i){sc[i]++;$('.a',b).textContent=sc[0];$('.c',b).textContent=sc[1];msg=i?'CPU scores':'GOAL!';mt=50;if(sc[i]>=5){msg=i?'CPU wins the match':'You win the match!';mt=120;sc=[0,0];$('.a',b).textContent=0;$('.c',b).textContent=0}roll()}
 function cpu(){const p=P[1],tx=Bl.x<W*.45?W-90:Bl.x+R.pr*.9,d=Math.hypot(Bl.x-p.x,Bl.y-p.y);
  return{l:p.x>tx+6,r:p.x<tx-6,u:Math.abs(Bl.x-p.x)<R.pr*2.2&&Bl.y<p.y-R.pr&&Math.random()<.08,k:d<R.pr+R.br+14&&Bl.x<p.x+4}}
 function step(){
  if(act!=='soccer')return;
  const C=[{l:K.ArrowLeft||K.a||K.l,r:K.ArrowRight||K.d||K.r,u:K.ArrowUp||K.w||K.u,k:K[' ']||K.k},cpu()];
  P.forEach((p,i)=>{const c=C[i];p.vx=(c.r?3.2:0)-(c.l?3.2:0);if(c.u&&p.y>=GY-R.pr-.5)p.vy=-9;p.vy+=R.g;p.x=clamp(p.x+p.vx,R.pr,W-R.pr);p.y+=p.vy;if(p.y>GY-R.pr){p.y=GY-R.pr;p.vy=0}
   const dx=Bl.x-p.x,dy=Bl.y-p.y,d=Math.hypot(dx,dy),m=R.pr+R.br;
   if(d<m+(c.k?10:0)&&d>0){const nx=dx/d,ny=dy/d,pw=c.k?9:4;Bl.x=p.x+nx*m;Bl.y=p.y+ny*m;Bl.vx=nx*pw+p.vx*.6;Bl.vy=ny*pw+p.vy*.4-(c.k?2:0)}});
  Bl.vy+=R.g;Bl.x+=Bl.vx;Bl.y+=Bl.vy;Bl.vx*=.995;
  if(Bl.y>GY-R.br){Bl.y=GY-R.br;Bl.vy*=-.72;Bl.vx*=.97}
  if(Bl.y<R.br){Bl.y=R.br;Bl.vy=Math.abs(Bl.vy)*.8}
  const inG=Bl.y>GY-GH;
  if(!inG&&Bl.x<R.br){Bl.x=R.br;Bl.vx=Math.abs(Bl.vx)*.8}
  if(!inG&&Bl.x>W-R.br){Bl.x=W-R.br;Bl.vx=-Math.abs(Bl.vx)*.8}
  if(Bl.x<-R.br)goal(1);else if(Bl.x>W+R.br)goal(0);
 }
 function draw(){
  g.fillStyle='#2f8f5b';g.fillRect(0,0,W,H);g.fillStyle='rgba(255,255,255,.07)';for(let i=0;i<8;i+=2)g.fillRect(i*60,0,60,H);
  g.fillStyle='#1f6f45';g.fillRect(0,GY,W,H-GY);g.strokeStyle='#fff';g.lineWidth=3;g.strokeRect(-3,GY-GH,22,GH);g.strokeRect(W-19,GY-GH,22,GH);
  P.forEach((p,i)=>{g.fillStyle=i?'#f59e0b':S.accent;g.beginPath();g.arc(p.x,p.y,R.pr,0,7);g.fill();g.fillStyle='#fff';g.beginPath();g.arc(p.x+(i?-1:1)*R.pr*.35,p.y-R.pr*.2,R.pr*.28,0,7);g.fill()});
  g.fillStyle='#fff';g.beginPath();g.arc(Bl.x,Bl.y,R.br,0,7);g.fill();g.strokeStyle='#222';g.lineWidth=2;g.stroke();
  if(mt-->0){g.fillStyle='#fff';g.font='800 30px Figtree,sans-serif';g.textAlign='center';g.fillText(msg,W/2,90)}
 }
 roll();const t=setInterval(()=>{step();draw()},1000/60);
 return()=>{clearInterval(t);off()};
}

function breakoutApp(b){
 b.innerHTML=`<div class="gh"><span>Score <b class="sc">0</b></span><span>Lives <b class="lv">3</b></span></div><canvas width="320" height="320" aria-label="Breakout board"></canvas><p class="hint">Move the mouse or your finger, or use arrow keys. Tap or press Space to launch.</p>`;
 const cv=$('canvas',b),g=cv.getContext('2d'),[K,off]=keysFor('breakout');let px,ball,br,sc,lv,live;
 const rst=full=>{px=130;ball={x:160,y:298,vx:0,vy:0};live=false;if(full){br=[];for(let r=0;r<5;r++)for(let c=0;c<8;c++)br.push({x:c*40+2,y:r*18+34,c:`hsl(${160+r*40} 65% 55%)`,h:1});sc=0;lv=3}$('.sc',b).textContent=sc;$('.lv',b).textContent=lv};
 const go=()=>{if(!live){live=true;ball.vx=2.4;ball.vy=-3.6}};
 cv.onpointermove=e=>{const r=cv.getBoundingClientRect();px=clamp((e.clientX-r.left)*320/r.width-30,0,260)};cv.onpointerdown=go;
 const t=setInterval(()=>{
  if(act!=='breakout')return;
  if(K.ArrowLeft||K.a)px=Math.max(0,px-5);if(K.ArrowRight||K.d)px=Math.min(260,px+5);if(K[' '])go();
  if(!live){ball.x=px+30;ball.y=298}else{
   ball.x+=ball.vx;ball.y+=ball.vy;
   if(ball.x<5||ball.x>315)ball.vx*=-1;if(ball.y<5)ball.vy=Math.abs(ball.vy);
   if(ball.vy>0&&ball.y>=300&&ball.y<=310&&ball.x>px-4&&ball.x<px+64){ball.vy=-Math.abs(ball.vy);ball.vx=(ball.x-px-30)/8}
   for(const k of br)if(k.h&&ball.x>k.x&&ball.x<k.x+36&&ball.y>k.y&&ball.y<k.y+14){k.h=0;ball.vy*=-1;sc++;$('.sc',b).textContent=sc;break}
   if(!br.some(k=>k.h))rst(true);
   if(ball.y>325){lv--;lv>0?rst():rst(true)}
  }
  g.fillStyle=css('--card');g.fillRect(0,0,320,320);br.forEach(k=>{if(k.h){g.fillStyle=k.c;g.fillRect(k.x,k.y,36,14)}});
  g.fillStyle=S.accent;g.fillRect(px,306,60,8);g.fillStyle=css('--ink');g.beginPath();g.arc(ball.x,ball.y,5,0,7);g.fill()},16);
 rst(true);
 return()=>{clearInterval(t);off()};
}

function pongApp(b){
 b.innerHTML=`<div class="gh"><span>You <b class="a">0</b> – <b class="c">0</b> CPU</span></div><canvas width="400" height="250" aria-label="Pong table"></canvas><p class="hint">Move the mouse or drag, or use W/S or arrow keys.</p>`;
 const cv=$('canvas',b),g=cv.getContext('2d'),[K,off]=keysFor('pong');let y=100,cy=100,s=[0,0],ball;
 const serve=d=>{ball={x:200,y:125,vx:3.4*d,vy:(Math.random()-.5)*4}};serve(1);
 cv.onpointermove=e=>{const r=cv.getBoundingClientRect();y=(e.clientY-r.top)*250/r.height-25};
 const sc=i=>{s[i]++;$('.a',b).textContent=s[0];$('.c',b).textContent=s[1];serve(i?1:-1)};
 const t=setInterval(()=>{
  if(act!=='pong')return;
  if(K.w||K.ArrowUp)y-=5;if(K.s||K.ArrowDown)y+=5;y=clamp(y,0,200);cy=clamp(cy+clamp(ball.y-25-cy,-3,3),0,200);
  ball.x+=ball.vx;ball.y+=ball.vy;if(ball.y<4||ball.y>246)ball.vy*=-1;
  if(ball.vx<0&&ball.x<22&&ball.x>10&&ball.y>y-4&&ball.y<y+54){ball.vx=Math.abs(ball.vx)*1.06;ball.vy+=(ball.y-y-25)/6}
  if(ball.vx>0&&ball.x>378&&ball.x<390&&ball.y>cy-4&&ball.y<cy+54){ball.vx=-Math.abs(ball.vx)*1.06;ball.vy+=(ball.y-cy-25)/6}
  if(ball.x<0)sc(1);else if(ball.x>400)sc(0);
  g.fillStyle=css('--card');g.fillRect(0,0,400,250);g.fillStyle=css('--line');for(let i=0;i<250;i+=20)g.fillRect(198,i,4,10);
  g.fillStyle=S.accent;g.fillRect(12,y,10,50);g.fillStyle='#f59e0b';g.fillRect(378,cy,10,50);g.fillStyle=css('--ink');g.beginPath();g.arc(ball.x,ball.y,5,0,7);g.fill()},16);
 return()=>{clearInterval(t);off()};
}

function territoryApp(b){
 const N=40,C=10,CL=[0,S.accent,'#f59e0b','#a78bfa','#f472b6'],[K,off]=keysFor('territory');
 b.innerHTML=`<div class="gh"><span>Territory <b class="sc">0</b>%</span><span class="st"></span></div><canvas width="400" height="400" aria-label="Territory Rush board"></canvas><p class="hint">Arrow keys, WASD or swipe. Leave your color, loop back home to claim land. Cross a rival's trail to knock them out.</p>`;
 const cv=$('canvas',b),g=cv.getContext('2d');let own,tr,P,over,sx,sy;
 const dir=(p,a,c)=>{if(a==-p.dx&&c==-p.dy&&(p.dx||p.dy))return;p.dx=a;p.dy=c};
 function spawn(p,x,y){p.x=p.hx=x;p.y=p.hy=y;p.dx=p.dy=0;p.out=false;p.n=0;p.L=8;p.alive=true;for(let a=-1;a<2;a++)for(let c=-1;c<2;c++)own[(y+c)*N+x+a]=p.id}
 function init(){own=new Int8Array(N*N);tr=new Int8Array(N*N);over=false;P=[1,2,3,4].map(id=>({id,bot:id>1,rs:0}));[[6,33],[33,6],[6,6],[33,33]].forEach((s,i)=>spawn(P[i],s[0],s[1]));P.slice(1).forEach(p=>p.dx=1)}
 function kill(p){p.alive=false;for(let i=0;i<N*N;i++){if(own[i]==p.id)own[i]=0;if(tr[i]==p.id)tr[i]=0}if(p.bot)p.rs=30;else over=true}
 function close(p){p.out=false;p.n=0;p.L=6+Math.random()*10|0;for(let i=0;i<N*N;i++)if(tr[i]==p.id){tr[i]=0;own[i]=p.id}
  const v=new Uint8Array(N*N),q=[],add=i=>{if(!v[i]&&own[i]!=p.id){v[i]=1;q.push(i)}};
  for(let k=0;k<N;k++){add(k);add((N-1)*N+k);add(k*N);add(k*N+N-1)}
  while(q.length){const i=q.pop(),x=i%N;if(i>=N)add(i-N);if(i<N*N-N)add(i+N);if(x>0)add(i-1);if(x<N-1)add(i+1)}
  for(let i=0;i<N*N;i++)if(!v[i]&&own[i]!=p.id)own[i]=p.id}
 function ai(p){
  const ok=(a,c)=>{const x=p.x+a,y=p.y+c;return x>=0&&y>=0&&x<N&&y<N&&tr[y*N+x]!=p.id&&!(a==-p.dx&&c==-p.dy)};let w=null;
  if(p.out&&p.n>p.L){const ex=p.hx-p.x,ey=p.hy-p.y;w=Math.abs(ex)>Math.abs(ey)?[Math.sign(ex),0]:[0,Math.sign(ey)||1]}
  else if(Math.random()<.12){const q=Math.random()<.5?1:-1;w=[q*p.dy,q*p.dx]}
  if(w&&(w[0]||w[1])&&ok(w[0],w[1]))dir(p,w[0],w[1]);
  if(!ok(p.dx,p.dy)){const o=[[p.dy,p.dx],[-p.dy,-p.dx],[1,0],[-1,0],[0,1],[0,-1]].find(d=>(d[0]||d[1])&&ok(d[0],d[1]));if(o)dir(p,o[0],o[1])}}
 function draw(){
  g.fillStyle=css('--card');g.fillRect(0,0,400,400);
  for(let i=0;i<N*N;i++){const o=own[i],t=tr[i];if(o||t){g.globalAlpha=t?.95:.5;g.fillStyle=CL[t||o];g.fillRect(i%N*C,(i/N|0)*C,C,C)}}
  g.globalAlpha=1;g.fillStyle=css('--ink');P.forEach(p=>{if(p.alive)g.fillRect(p.x*C+1,p.y*C+1,C-2,C-2)});
  if(over){g.fillStyle='rgba(0,0,0,.6)';g.fillRect(0,0,400,400);g.fillStyle='#fff';g.textAlign='center';g.font='800 26px Figtree,sans-serif';g.fillText('Knocked out',200,195);g.font='14px Figtree,sans-serif';g.fillText('Tap or press Space to play again',200,222)}}
 function tick(){
  if(act!=='territory')return;
  if(over){if(K[' '])init();return draw()}
  const me=P[0];if(K.ArrowUp||K.w)dir(me,0,-1);else if(K.ArrowDown||K.s)dir(me,0,1);else if(K.ArrowLeft||K.a)dir(me,-1,0);else if(K.ArrowRight||K.d)dir(me,1,0);
  P.forEach(p=>{
   if(!p.alive){if(p.bot&&--p.rs<=0){spawn(p,3+Math.random()*(N-7)|0,3+Math.random()*(N-7)|0);p.dx=1}return}
   if(p.bot)ai(p);if(!p.dx&&!p.dy)return;
   const x=p.x+p.dx,y=p.y+p.dy;if(x<0||y<0||x>=N||y>=N)return kill(p);
   const i=y*N+x,t=tr[i];if(t==p.id)return kill(p);if(t)kill(P[t-1]);
   p.x=x;p.y=y;if(own[i]!=p.id){tr[i]=p.id;p.out=true;p.n++}else if(p.out)close(p)});
  let c=0;for(let i=0;i<N*N;i++)if(own[i]==1)c++;$('.sc',b).textContent=Math.round(c/16);draw()}
 cv.onpointerdown=e=>{sx=e.clientX;sy=e.clientY;if(over)init()};
 cv.onpointerup=e=>{const a=e.clientX-sx,c=e.clientY-sy;if(Math.max(Math.abs(a),Math.abs(c))>20)Math.abs(a)>Math.abs(c)?dir(P[0],Math.sign(a),0):dir(P[0],0,Math.sign(c))};
 init();const t=setInterval(tick,85);return()=>{clearInterval(t);off()};
}

function tagApp(b){
 b.innerHTML=`<div class="gh"><span>Safe <b class="sf">0</b>s</span><span class="tm">60s</span></div><canvas width="400" height="300" aria-label="Tag Arena"></canvas><p class="hint">Arrow keys, WASD, or point and drag. Don't be "it" when the clock hits zero.</p>`;
 const cv=$('canvas',b),g=cv.getContext('2d'),[K,off]=keysFor('tag'),COL=[S.accent,'#f59e0b','#a78bfa','#f472b6'];let E,it,f,sf,ptr,done;
 const init=()=>{E=COL.map((c,i)=>({x:60+i*90,y:60+(i%2)*170,c,im:0}));it=1+Math.random()*3|0;f=sf=0;done=false;ptr=null};
 const mv=e=>{const r=cv.getBoundingClientRect();ptr={x:(e.clientX-r.left)*400/r.width,y:(e.clientY-r.top)*300/r.height}};
 cv.onpointerdown=e=>{if(done)init();mv(e)};cv.onpointermove=mv;cv.onpointerleave=()=>ptr=null;cv.onpointerup=e=>{if(e.pointerType=='touch')ptr=null};
 const dist=(a,c)=>Math.hypot(a.x-c.x,a.y-c.y);
 const t=setInterval(()=>{
  if(act!=='tag')return;
  if(!done){
   f++;if(it)sf++;
   E.forEach((p,i)=>{let vx=0,vy=0;
    if(!i){vx=(K.ArrowRight||K.d?1:0)-(K.ArrowLeft||K.a?1:0);vy=(K.ArrowDown||K.s?1:0)-(K.ArrowUp||K.w?1:0);if(ptr){const dx=ptr.x-p.x,dy=ptr.y-p.y;if(Math.hypot(dx,dy)>8){vx=dx;vy=dy}}}
    else if(it==i){const q=E.filter((o,j)=>j!=i&&!o.im).sort((a,c)=>dist(a,p)-dist(c,p))[0];if(q){vx=q.x-p.x;vy=q.y-p.y}}
    else{const q=E[it];vx=p.x-q.x;vy=p.y-q.y;if(p.x<40)vx+=200;if(p.x>360)vx-=200;if(p.y<40)vy+=200;if(p.y>260)vy-=200}
    const m=Math.hypot(vx,vy);if(m){const s=i?(it==i?2.5:2.35):2.7;p.x=clamp(p.x+vx/m*s,12,388);p.y=clamp(p.y+vy/m*s,12,288)}if(p.im)p.im--});
   const a=E[it];let hit=false;E.forEach((p,j)=>{if(!hit&&j!=it&&!p.im&&dist(p,a)<24){hit=true;a.im=60;it=j}});
   $('.sf',b).textContent=Math.floor(sf/60);$('.tm',b).textContent=Math.max(0,60-Math.floor(f/60))+'s';if(f>=3600)done=true;
  }
  g.fillStyle=css('--card');g.fillRect(0,0,400,300);
  E.forEach((p,i)=>{g.globalAlpha=p.im?.45:1;g.fillStyle=p.c;g.beginPath();g.arc(p.x,p.y,12,0,7);g.fill();if(i==it){g.globalAlpha=1;g.strokeStyle=css('--ink');g.lineWidth=3;g.stroke();g.fillStyle=css('--ink');g.font='800 11px Figtree,sans-serif';g.textAlign='center';g.fillText('IT',p.x,p.y-18)}});
  g.globalAlpha=1;
  if(done){g.fillStyle='rgba(0,0,0,.6)';g.fillRect(0,0,400,300);g.fillStyle='#fff';g.textAlign='center';g.font='800 26px Figtree,sans-serif';g.fillText(it?'You made it! Safe '+Math.floor(sf/60)+'s':'You were it',200,140);g.font='14px Figtree,sans-serif';g.fillText('Tap to play again',200,168)}
 },16);
 init();return()=>{clearInterval(t);off()};
}

function blobApp(b){
 b.innerHTML=`<div class="gh"><span>Size <b class="sc">0</b></span><span>Eat smaller blobs</span></div><canvas width="400" height="400" aria-label="Blob Feast arena"></canvas><p class="hint">Move the mouse, drag a finger, or use arrow keys. Don't get eaten.</p>`;
 const cv=$('canvas',b),g=cv.getContext('2d'),[K,off]=keysFor('blob'),W=1200,COL=['#f59e0b','#a78bfa','#f472b6','#38bdf8','#84cc16','#fb7185','#f97316','#22d3ee'];let me,B,pel,ptr,over;
 const rnd=()=>({x:Math.random()*W,y:Math.random()*W}),rad=m=>Math.sqrt(m)*3;
 const init=()=>{me={...rnd(),m:20,c:S.accent};B=Array.from({length:9},(_,i)=>({...rnd(),m:12+Math.random()*50,c:COL[i%8]}));pel=Array.from({length:150},rnd);over=false;ptr=null};
 const go=(p,vx,vy)=>{const m=Math.hypot(vx,vy);if(!m)return;const s=3.2/(1+rad(p.m)/70);p.x=clamp(p.x+vx/m*s,0,W);p.y=clamp(p.y+vy/m*s,0,W)};
 const aim=e=>{const r=cv.getBoundingClientRect();ptr={x:(e.clientX-r.left)*400/r.width-200,y:(e.clientY-r.top)*400/r.height-200}};
 cv.onpointerdown=e=>{if(over)init();aim(e)};cv.onpointermove=aim;cv.onpointerleave=()=>ptr=null;cv.onpointerup=e=>{if(e.pointerType=='touch')ptr=null};
 const t=setInterval(()=>{
  if(act!=='blob')return;
  if(!over){
   let vx=(K.ArrowRight||K.d?1:0)-(K.ArrowLeft||K.a?1:0),vy=(K.ArrowDown||K.s?1:0)-(K.ArrowUp||K.w?1:0);if(ptr&&Math.hypot(ptr.x,ptr.y)>10){vx=ptr.x;vy=ptr.y}go(me,vx,vy);
   const A=[me,...B];
   B.forEach(p=>{let tg=null,fl=null;for(const q of A){if(q==p)continue;const d=Math.hypot(q.x-p.x,q.y-p.y);if(q.m>p.m*1.15&&d<200){if(!fl||d<fl.d)fl={q,d}}else if(p.m>q.m*1.15&&d<250&&(!tg||d<tg.d))tg={q,d}}
    if(fl)go(p,p.x-fl.q.x,p.y-fl.q.y);else if(tg)go(p,tg.q.x-p.x,tg.q.y-p.y);else{let n=null,bd=1e9;for(const q of pel){const d=Math.hypot(q.x-p.x,q.y-p.y);if(d<bd){bd=d;n=q}}if(n)go(p,n.x-p.x,n.y-p.y)}});
   A.forEach(p=>{pel.forEach((q,i)=>{if(Math.hypot(q.x-p.x,q.y-p.y)<rad(p.m)){p.m+=1;pel[i]=rnd()}});if(p.m>40)p.m*=.9997;
    A.forEach(q=>{if(q!=p&&p.m>q.m*1.15&&Math.hypot(q.x-p.x,q.y-p.y)<rad(p.m)-rad(q.m)*.4){p.m+=q.m*.8;if(q==me)over=true;else Object.assign(q,rnd(),{m:12+Math.random()*30})}})});
   $('.sc',b).textContent=Math.round(me.m);
  }
  const z=clamp(1.1-rad(me.m)/90,.5,1);
  g.setTransform(1,0,0,1,0,0);g.fillStyle=css('--card');g.fillRect(0,0,400,400);
  g.setTransform(z,0,0,z,200-me.x*z,200-me.y*z);g.strokeStyle=css('--line');g.lineWidth=1;g.beginPath();for(let k=0;k<=W;k+=100){g.moveTo(k,0);g.lineTo(k,W);g.moveTo(0,k);g.lineTo(W,k)}g.stroke();g.strokeRect(0,0,W,W);
  g.fillStyle=css('--mut');pel.forEach(q=>{g.fillRect(q.x-2,q.y-2,4,4)});
  [me,...B].sort((a,c)=>a.m-c.m).forEach(p=>{g.globalAlpha=.9;g.fillStyle=p.c;g.beginPath();g.arc(p.x,p.y,rad(p.m),0,7);g.fill();g.globalAlpha=1;g.strokeStyle=css('--ink');g.lineWidth=2;g.stroke()});
  g.setTransform(1,0,0,1,0,0);
  if(over){g.fillStyle='rgba(0,0,0,.6)';g.fillRect(0,0,400,400);g.fillStyle='#fff';g.textAlign='center';g.font='800 26px Figtree,sans-serif';g.fillText('You were eaten',200,195);g.font='14px Figtree,sans-serif';g.fillText('Tap to play again',200,222)}
 },16);
 init();return()=>{clearInterval(t);off()};
}

const STORE=[['calc','Calculator','Quick math with big, clear keys.'],['paint','Sketchpad','Draw with colors and brush sizes.'],['timer','Stopwatch & Timer','Laps and a countdown with a chime.'],['tasks','Tasks','A checklist that saves on this device.'],['piano','Piano','Play notes with touch or your keyboard.'],['cal','Calendar','Browse any month at a glance.']];
function storeApp(b){
 const draw=()=>{b.innerHTML='<div class="grp"><h3>Built-in apps, ready to install</h3></div>'+STORE.map(([id,n,d])=>{const on=S.apps.includes(id);return`<div class="gc st"><i>${APPS[id].i}</i><span><b>${n}</b><small>${d}</small></span>${on?`<span class="sb"><button class="btn" data-open="${id}">Open</button><button class="x" data-rm="${id}" aria-label="Remove ${n}">Remove</button></span>`:`<button class="btn" data-get="${id}">Get</button>`}</div>`}).join('')};
 b.onclick=e=>{const g=e.target.closest('[data-get]'),o=e.target.closest('[data-open]'),r=e.target.closest('[data-rm]');
  if(g){g.disabled=true;g.textContent='Installing…';const c=g.closest('.st');c.insertAdjacentHTML('beforeend','<div class="pb"><i></i></div>');requestAnimationFrame(()=>requestAnimationFrame(()=>{$('.pb i',c).style.width='100%'}));
   setTimeout(()=>{if(!S.apps.includes(g.dataset.get))S.apps.push(g.dataset.get);save();shell();if(wins.store)draw()},1150)}
  else if(o)open(o.dataset.open);
  else if(r){const id=r.dataset.rm;if(wins[id])close(id);S.apps=S.apps.filter(k=>k!=id);save();shell();draw()}};
 draw();
}

function calcApp(b){
 let cur='0',acc=null,op=null,fresh=true;const ap=(a,o,c)=>o=='+'?a+c:o=='−'?a-c:o=='×'?a*c:o=='÷'?(c?a/c:NaN):c;
 b.innerHTML=`<div class="cd"><small class="ce"></small><b class="cr">0</b></div><div class="ck">${['C','⌫','%','÷','7','8','9','×','4','5','6','−','1','2','3','+','±','0','.','='].map(k=>`<button data-k="${k}" class="${'÷×−+='.includes(k)?'op':''}">${k}</button>`).join('')}</div>`;
 const show=()=>{$('.cr',b).textContent=cur;$('.ce',b).textContent=op&&acc!==null?acc+' '+op:''};
 b.onclick=e=>{const k=e.target.dataset.k;if(!k)return;
  if(/\d/.test(k)){cur=fresh||cur=='0'?k:cur+k;fresh=false}
  else if(k=='.'){if(fresh){cur='0.';fresh=false}else if(!cur.includes('.'))cur+='.'}
  else if(k=='C'){cur='0';acc=op=null;fresh=true}
  else if(k=='⌫'){cur=cur.length>1&&cur!='Error'?cur.slice(0,-1):'0'}
  else if(k=='±'){cur=cur[0]=='-'?cur.slice(1):cur=='0'?cur:'-'+cur}
  else if(k=='%'){cur=String(+cur/100)}
  else{const v=+cur;acc=op&&!fresh?ap(acc,op,v):v;op=k=='='?null:k;cur=isFinite(acc)?String(+acc.toFixed(10)):'Error';fresh=true;if(cur=='Error'){acc=null;op=null}}
  show()};
}

function paintApp(b){
 const CL=[S.accent,'#f59e0b','#a78bfa','#f472b6','#38bdf8','#84cc16','#ef4444','#111111','#ffffff'];let c=CL[0];
 b.innerHTML=`<div class="gh"><span class="sw">${CL.map(x=>`<button data-c="${x}" style="background:${x};border-color:var(--line)" aria-label="Color ${x}"></button>`).join('')}</span><button class="btn" data-clr>Clear</button></div><input type="range" min="2" max="30" value="6" aria-label="Brush size" style="width:100%;accent-color:var(--accent)"><canvas width="520" height="300" style="width:100%;max-width:100%;margin-top:8px;background:#fff" aria-label="Drawing canvas"></canvas>`;
 const cv=$('canvas',b),g=cv.getContext('2d'),rg=$('input',b);g.lineCap=g.lineJoin='round';
 const pt=e=>{const r=cv.getBoundingClientRect();return[(e.clientX-r.left)*520/r.width,(e.clientY-r.top)*300/r.height]};
 cv.onpointerdown=e=>{cv.setPointerCapture(e.pointerId);const[x,y]=pt(e);g.strokeStyle=c;g.lineWidth=+rg.value;g.beginPath();g.moveTo(x,y);g.lineTo(x+.1,y);g.stroke()};
 cv.onpointermove=e=>{if(!cv.hasPointerCapture(e.pointerId))return;const[x,y]=pt(e);g.lineTo(x,y);g.stroke()};
 b.onclick=e=>{const k=e.target.closest('[data-c]');if(k)c=k.dataset.c;else if(e.target.closest('[data-clr]'))g.clearRect(0,0,520,300)};
}

function timerApp(b){
 let t0=0,acc=0,run=false,laps=[],end=0;const f=ms=>{const m=Math.floor(ms/60000),s=Math.floor(ms/1000)%60,c=Math.floor(ms/10)%100,p=n=>String(n).padStart(2,'0');return`${p(m)}:${p(s)}.${p(c)}`};
 b.innerHTML=`<div class="grp"><h3>Stopwatch</h3><div class="big s1">00:00.00</div><div class="seg"><button data-a="go">Start</button><button data-a="lap">Lap</button><button data-a="rs">Reset</button></div><ol class="laps"></ol></div><div class="grp"><h3>Countdown</h3><div class="big c1">--:--</div><div class="seg"><button data-m="1">1 min</button><button data-m="5">5 min</button><button data-m="10">10 min</button></div></div>`;
 const s1=$('.s1',b),c1=$('.c1',b),gb=$('[data-a=go]',b),now=()=>acc+(run?performance.now()-t0:0);
 b.onclick=e=>{const a=e.target.dataset.a,m=e.target.dataset.m;
  if(a=='go'){if(run){acc+=performance.now()-t0;run=false}else{t0=performance.now();run=true}gb.textContent=run?'Pause':'Start'}
  else if(a=='lap'&&now()){laps.unshift(f(now()));$('.laps',b).innerHTML=laps.map(l=>`<li>${l}</li>`).join('')}
  else if(a=='rs'){run=false;acc=0;laps=[];gb.textContent='Start';$('.laps',b).innerHTML=''}
  else if(m)end=Date.now()+m*60000};
 const t=setInterval(()=>{s1.textContent=f(now());if(end){const l=end-Date.now();if(l<=0){end=0;c1.textContent='00:00';tone(880,.5);setTimeout(()=>tone(1175,.6),300)}else c1.textContent=f(l).slice(0,5)}},50);
 return()=>clearInterval(t);
}

function tasksApp(b){
 let L=[];try{L=JSON.parse(ls('oasis-tasks')||'[]')}catch(e){}
 const esc=s=>s.replace(/[&<>"]/g,c=>({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;'}[c])),sv=()=>ls('oasis-tasks',JSON.stringify(L));
 b.innerHTML=`<div class="gh"><input class="gs" placeholder="Add a task" aria-label="New task"><button class="btn" data-add>Add</button></div><div class="tl"></div>`;
 const q=$('.gs',b),box=$('.tl',b);
 const draw=()=>{box.innerHTML=L.length?L.map((t,i)=>`<label class="ti"><input type="checkbox" data-i="${i}" ${t.d?'checked':''}><span class="${t.d?'dn':''}">${esc(t.t)}</span><button class="x" data-x="${i}" aria-label="Delete task">Delete</button></label>`).join(''):'<p class="hint">No tasks yet. Add your first one above.</p>'};
 const add=()=>{const v=q.value.trim();if(v){L.push({t:v,d:false});q.value='';sv();draw()}};
 q.onkeydown=e=>{if(e.key=='Enter')add()};
 b.onclick=e=>{const t=e.target;if(t.closest('[data-add]'))add();else if(t.matches('[data-i]')){L[+t.dataset.i].d=t.checked;sv();draw()}else if(t.matches('[data-x]')){L.splice(+t.dataset.x,1);sv();draw()}};
 draw();
}

function pianoApp(b){
 const W=[0,2,4,5,7,9,11,12],BK=[[1,0],[3,1],[6,3],[8,4],[10,5]],KW='asdfghjk',KB={w:1,e:3,t:6,y:8,u:10},fr=n=>261.63*Math.pow(2,n/12);
 b.style.padding='10px';
 b.innerHTML=`<div class="pk">${W.map(n=>`<button class="wk" data-n="${n}" aria-label="Note ${n}"></button>`).join('')}${BK.map(([n,i])=>`<button class="bk" data-n="${n}" style="left:calc(${(i+1)*12.5}% - 3.5%)" aria-label="Note ${n}"></button>`).join('')}</div><p class="hint">Click, tap, or play with A S D F G H J K and W E T Y U.</p>`;
 const hit=n=>{tone(fr(n),.7);const el=b.querySelector(`[data-n="${n}"]`);el.classList.add('on');setTimeout(()=>el.classList.remove('on'),160)};
 b.onpointerdown=e=>{const k=e.target.closest('[data-n]');if(k)hit(+k.dataset.n)};
 const key=e=>{if(act!=='piano'||e.repeat)return;const k=e.key.toLowerCase(),i=KW.indexOf(k);if(k.length==1&&i>=0)hit(W[i]);else if(KB[k]!=null)hit(KB[k])};
 addEventListener('keydown',key);return()=>removeEventListener('keydown',key);
}

function calApp(b){
 const d=new Date();d.setDate(1);
 const draw=()=>{const y=d.getFullYear(),m=d.getMonth(),n=new Date(y,m+1,0).getDate(),td=new Date();
  b.innerHTML=`<div class="gh"><button class="btn" data-n="-1" aria-label="Previous month">‹</button><b>${d.toLocaleDateString([],{month:'long',year:'numeric'})}</b><button class="btn" data-n="1" aria-label="Next month">›</button></div><div class="cg">${'SMTWTFS'.split('').map(x=>`<i>${x}</i>`).join('')}${'<span></span>'.repeat(d.getDay())}${Array.from({length:n},(_,i)=>`<span class="${y==td.getFullYear()&&m==td.getMonth()&&i+1==td.getDate()?'td':''}">${i+1}</span>`).join('')}</div>`};
 b.onclick=e=>{const x=e.target.closest('[data-n]');if(x){d.setMonth(d.getMonth()+ +x.dataset.n);draw()}};
 draw();
}

function aiApp(b){
 const SYS='You are Oasis AI, a friendly assistant built into Oasis.OS, a browser-based desktop. Answer clearly and concisely. Use short paragraphs, and simple **bold** or `code` only when it helps. You cannot browse the web or control the desktop apps.';
 b.style.cssText='display:flex;flex-direction:column;padding:0';
 b.innerHTML=`<div class="am" role="log" aria-live="polite"></div><div class="ar"><input class="gs" placeholder="Ask anything" aria-label="Message Oasis AI"><button class="btn" data-send>Send</button><button class="x" data-clr>Clear</button></div>`;
 const M=$('.am',b),q=$('.gs',b),sb=$('[data-send]',b);let H=[],busy=false,ctl=null,smp=null;
 const esc=s=>s.replace(/[&<>"]/g,c=>({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;'}[c]));
 const md=s=>esc(s).replace(/```(?:\w*\n)?([\s\S]*?)```/g,'<pre>$1</pre>').replace(/`([^`\n]+)`/g,'<code>$1</code>').replace(/\*\*([^*\n]+)\*\*/g,'<b>$1</b>').replace(/\n/g,'<br>');
 const add=(r,t)=>{const d=document.createElement('div');d.className='ms '+r;d.innerHTML=md(t);M.append(d);M.scrollTop=M.scrollHeight;return d};
 const hello=()=>{H=[];M.innerHTML='';add('ai','Hi, I’m Oasis AI. Ask me a question, get help writing, or talk through an idea.');M.insertAdjacentHTML('beforeend','<div class="chips">'+['Explain how rain forms','Give me 5 game ideas','Help me write a short email'].map(t=>`<button data-p="${t}">${t}</button>`).join('')+'</div>')};
 async function send(t){
  t=(t||q.value).trim();if(!t||busy)return;q.value='';const c=$('.chips',M);if(c)c.remove();
  add('me',t);H.push({role:'user',content:t});busy=true;sb.textContent='Stop';const d=add('ai','…');ctl=new AbortController();
  try{
   if(!smp&&typeof claude!=='undefined')smp=await claude.use('sample');
   if(!smp){d.textContent='AI isn’t available here. It works on the published page once you allow it.';H.pop();return}
   let s0=Math.max(0,H.length-11);if(s0%2)s0++;
   const turns=H.slice(s0).map((m,i)=>i?m:{role:'user',content:SYS+'\n\n'+m.content});
   const r=await smp(turns,{cache:false,signal:ctl.signal,onText:({text})=>{d.innerHTML=md(text);M.scrollTop=M.scrollHeight}});
   d.innerHTML=md(r.text);H.push({role:'assistant',content:r.text});
  }catch(e){
   if(e&&e.code=='cancelled'&&e.text){d.innerHTML=md(e.text);H.push({role:'assistant',content:e.text})}
   else{H.pop();d.textContent=e&&e.code=='not_granted'?'Permission wasn’t granted, so I can’t answer. Send your message again and choose Allow.':e&&e.code=='rate_limited'?'Too many requests. Wait a moment, then try again.':e&&e.code=='cancelled'?'Stopped.':'Something went wrong. Try sending that again.'}
  }finally{busy=false;ctl=null;sb.textContent='Send'}
 }
 q.onkeydown=e=>{if(e.key=='Enter')send()};
 b.onclick=e=>{const p=e.target.closest('[data-p]');if(p)send(p.dataset.p);else if(e.target.closest('[data-send]')){busy&&ctl?ctl.abort():send()}else if(e.target.closest('[data-clr]')){if(ctl)ctl.abort();hello()}};
 hello();return()=>{if(ctl)ctl.abort()};
}

function accountApp(b){
 b.innerHTML=`<div class="acc"><span class="av">👤</span><div><b class="an">Guest</b><small class="ar2"></small></div></div><p class="note"></p><div class="grp sg"><h3>Sync</h3><div class="seg"><button data-sync>Sync settings</button></div></div><p class="note vs"></p>`;
 const an=$('.an',b),role=$('.ar2',b),note=$('.note',b),sg=$('.sg',b),vs=$('.vs',b),sb=$('[data-sync]',b);
 async function paint(){
  if(!UID){an.textContent='Guest';role.textContent='Not signed in';note.textContent='Sign in to claude.ai and open this page to save your theme, accent, wallpaper and installed apps to your account.';sg.hidden=true;return}
  an.textContent=(ME&&ME.name)||'You';role.textContent=ME.isOwner?'Owner':ME.canEdit?'Editor':'Signed in';
  if(ME.avatarUrl){const i=new Image();i.src=ME.avatarUrl;i.alt='';i.width=i.height=56;$('.av',b).replaceChildren(i)}
  sg.hidden=!DB;sb.setAttribute('aria-pressed',String(!!S.sync));sb.textContent=S.sync?'Sync is on':'Sync is off';
  note.textContent=DB?(S.sync?'Your theme, accent, wallpaper, clock and installed apps follow you to other devices.':'Settings stay on this device only.'):'Account storage isn’t available right now.';
  if(DB)try{const d=await DB.doc('visitors/'+UID).get();if(d.exists){const x=d.data();vs.textContent=`You’ve visited ${x.visits||1} time${(x.visits||1)==1?'':'s'}. First visit: ${new Date(x.first).toLocaleDateString()}.`}}catch(e){}
 }
 b.onclick=e=>{if(e.target.closest('[data-sync]')){S.sync=!S.sync;save();paint()}};
 paint();
}

function statsApp(b){
 b.innerHTML=`<div class="sts"><div><b class="v1">–</b><small>People</small></div><div><b class="v2">–</b><small>Total visits</small></div><div><b class="v3">–</b><small>Active in 24h</small></div></div><div class="grp rec" hidden><h3>Recent visitors</h3><div class="rl"></div></div><button class="btn" data-r>Refresh</button><p class="hint">Counts people signed in to claude.ai who open this page. Anonymous visitors can’t be recorded.</p>`;
 const v=[1,2,3].map(i=>$('.v'+i,b)),rec=$('.rec',b),rl=$('.rl',b);
 async function load(){
  const r=await stats();if(!r){v.forEach(x=>x.textContent='–');return}
  v[0].textContent=r.u;v[1].textContent=r.t;v[2].textContent=r.a;refreshCount();
  if(ADMIN&&U){const rows=r.rows.sort((a,c)=>c.last-a.last).slice(0,8);let P={};try{P=await U.profiles(rows.map(x=>x.id))}catch(e){}
   rl.replaceChildren(...rows.map(x=>{const d=document.createElement('div');d.className='ti';const n=document.createElement('span'),t=document.createElement('small');n.textContent=(P[x.id]&&P[x.id].name)||'Someone';t.textContent=new Date(x.last).toLocaleString();d.append(n,t);return d}));rec.hidden=!rows.length}
 }
 b.onclick=e=>{if(e.target.closest('[data-r]'))load()};
 load();
}

function adminApp(b){
 if(!ADMIN){b.innerHTML='<p class="hint">This area is for admins only.</p>';return}
 const own=!!(ME&&ME.isOwner);
 b.innerHTML=`<div class="seg" style="margin-bottom:14px"><button data-t="o">Overview</button><button data-t="w">Admins</button><button data-t="a">Announcement</button></div><div data-p="o"></div><div data-p="w" hidden></div><div data-p="a" hidden></div>`;
 const P=k=>$('[data-p='+k+']',b);
 const hint=t=>{const p=document.createElement('p');p.className='hint';p.textContent=t;return p};
 const row=(name,sub,btn)=>{const d=document.createElement('div');d.className='ti';const n=document.createElement('span'),m=document.createElement('small');n.textContent=name;m.textContent=sub||'';d.append(n,m);if(btn)d.append(btn);return d};
 const mk=(txt,k,v,c)=>{const x=document.createElement('button');x.className=c||'x';x.textContent=txt;x.dataset[k]=v;return x};
 const show=t=>{b.querySelectorAll('[data-p]').forEach(p=>p.hidden=p.dataset.p!=t);b.querySelectorAll('[data-t]').forEach(x=>x.setAttribute('aria-pressed',String(x.dataset.t==t)))};
 async function ov(){const el=P('o');
  el.innerHTML=`<div class="sts"><div><b>–</b><small>People</small></div><div><b>–</b><small>Total visits</small></div><div><b>–</b><small>Active in 24h</small></div></div><div class="vl"></div><div class="seg"><button data-r>Refresh</button>${own?'<button data-reset>Reset visitor stats</button>':''}</div>`;
  const r=await stats();if(!r)return;const bs=el.querySelectorAll('.sts b');bs[0].textContent=r.u;bs[1].textContent=r.t;bs[2].textContent=r.a;
  const rows=r.rows.sort((a,c)=>c.last-a.last).slice(0,30);let N={};try{N=await U.profiles(rows.map(x=>x.id))}catch(e){}
  $('.vl',el).replaceChildren(...rows.map(x=>row((N[x.id]&&N[x.id].name)||'Someone',`${x.visits} visit${x.visits==1?'':'s'}, last ${new Date(x.last).toLocaleString()}`)));}
 const saveWL=()=>DB.doc('admin/whitelist').set({ids:WL});
 async function ad(){const el=P('w');
  el.innerHTML=`<h3 class="h3">Whitelisted admins</h3><div class="wl"></div>${own?'<h3 class="h3" style="margin-top:14px">Add someone</h3><input class="gs" style="width:100%" placeholder="Search people by name" aria-label="Search people"><div class="sr" style="margin-top:8px"></div>':'<p class="hint">Only the owner can change this list.</p>'}`;
  let N={};try{N=await U.profiles(WL)}catch(e){}
  $('.wl',el).replaceChildren(...(WL.length?WL.map(id=>row((N[id]&&N[id].name)||'Someone',id==UID?'You':'',own?mk('Remove','rm',id):null)):[hint('No one is whitelisted yet.')]));
  if(own){const inp=$('.gs',el),sr=$('.sr',el);let tm;inp.oninput=()=>{clearTimeout(tm);tm=setTimeout(async()=>{let h=[];try{h=await U.search(inp.value.trim())}catch(e){}
   sr.replaceChildren(...h.filter(x=>x.id!==UID&&!WL.includes(x.id)).slice(0,6).map(x=>row(x.name||'Someone','',mk('Add','add',x.id,'btn'))))},250)}}}
 async function an(){const el=P('a');let cur='';try{const d=await DB.doc('admin/announcement').get();cur=d.exists?(d.data().text||''):''}catch(e){}
  el.innerHTML=own?`<h3 class="h3">Banner shown to everyone who opens the page</h3><textarea maxlength="200" aria-label="Announcement" style="min-height:90px" placeholder="Write a short announcement"></textarea><div class="seg" style="margin-top:8px"><button data-pub>Publish</button><button data-clearann>Remove</button></div><p class="hint ms2"></p>`:`<h3 class="h3">Current announcement</h3><p class="note"></p>`;
  if(own)$('textarea',el).value=cur;else $('.note',el).textContent=cur||'None right now.'}
 let rc=0;
 b.onclick=async e=>{const t=e.target.closest('button');if(!t)return;
  if(t.dataset.t){show(t.dataset.t);({o:ov,w:ad,a:an})[t.dataset.t]()}
  else if('r' in t.dataset)ov();
  else if('reset' in t.dataset){if(!rc){rc=1;t.textContent='Click again to confirm';setTimeout(()=>{rc=0;t.textContent='Reset visitor stats'},4000)}else{rc=0;const r=await stats();if(r)await Promise.all(r.rows.map(x=>DB.doc('visitors/'+x.id).delete().catch(()=>{})));refreshCount();ov()}}
  else if(t.dataset.add){if(!WL.includes(t.dataset.add))WL.push(t.dataset.add);await saveWL().catch(()=>{});ad()}
  else if(t.dataset.rm){WL=WL.filter(i=>i!=t.dataset.rm);await saveWL().catch(()=>{});ad()}
  else if('pub' in t.dataset||'clearann' in t.dataset){const v='pub' in t.dataset?$('textarea',b).value.trim().slice(0,200):'';
   try{await DB.doc('admin/announcement').set({text:v,ts:Date.now()});$('.ms2',b).textContent=v?'Published. People see it the next time they open the page.':'Removed.';if(!v)$('textarea',b).value=''}catch(e){$('.ms2',b).textContent='Couldn’t save that. Try again.'}}};
 show('o');ov();
}

function notesApp(b){
 b.style.display='flex';b.innerHTML='<textarea aria-label="Notes" placeholder="Jot something down. Notes stay on this device."></textarea>';
 const t=$('textarea',b);t.value=ls('oasis-notes')||'';t.oninput=()=>ls('oasis-notes',t.value);
}

function settingsApp(b){
 const AC=['#14b8a6','#38bdf8','#f59e0b','#a78bfa','#f472b6'],cap=s=>s[0].toUpperCase()+s.slice(1);
 const seg=(k,vals)=>`<div class="seg">${vals.map(v=>`<button data-k="${k}" data-v="${v[0]}">${v[1]}</button>`).join('')}</div>`;
 b.innerHTML=`<div class="grp"><h3>Appearance</h3>${seg('theme',['auto','light','dark'].map(v=>[v,cap(v)]))}</div>
 <div class="grp"><h3>Accent color</h3><div class="sw">${AC.map(c=>`<button data-k="accent" data-v="${c}" style="background:${c}" aria-label="Accent ${c}"></button>`).join('')}</div></div>
 <div class="grp"><h3>Wallpaper</h3>${seg('wall',['lagoon','dusk','grove','aurora','stars','waves','custom'].map(v=>[v,cap(v)]))}<button class="btn" data-imp style="margin-top:8px">Import image or video</button><input type="file" accept="image/*,video/*" hidden></div>
 <div class="grp"><h3>Clock</h3>${seg('h24',[['false','12-hour'],['true','24-hour']])}</div>
 <button class="btn" data-reset>Reset to defaults</button>`;
 const paint=()=>b.querySelectorAll('[data-k]').forEach(x=>x.setAttribute('aria-pressed',String(S[x.dataset.k])===x.dataset.v));
 const fi=$('input[type=file]',b);
 b.onclick=async e=>{
  if(e.target.closest('[data-imp]'))return fi.click();
  const x=e.target.closest('[data-k]');
  if(x&&x.dataset.k=='wall'&&x.dataset.v=='custom'&&!(await idb('get')))return fi.click();
  if(x){const k=x.dataset.k;S[k]=k=='h24'?x.dataset.v=='true':x.dataset.v}
  else if(e.target.closest('[data-reset]'))Object.assign(S,DEF);
  else return;
  apply();save();paint();
 };
 fi.onchange=async()=>{const f=fi.files[0];if(!f)return;await idb('put',f);S.wall='custom';lw=null;apply();save();paint()};
 paint();
}

apply();setInterval(tick,20000);boot2();setInterval(refreshCount,90000);
const boot=$('#boot'),rn=$('#rain'),rc=rn.getContext('2d'),still=matchMedia('(prefers-reduced-motion:reduce)').matches;let rid,drops=[],done=false;
const rs=()=>{rn.width=innerWidth;rn.height=innerHeight;drops=Array.from({length:Math.min(220,innerWidth/4|0)},()=>({x:Math.random()*rn.width,y:Math.random()*rn.height,l:10+Math.random()*18,v:7+Math.random()*9}))};rs();addEventListener('resize',rs);
function rain(){rc.clearRect(0,0,rn.width,rn.height);rc.strokeStyle='rgba(160,215,230,.35)';rc.lineWidth=1;rc.beginPath();drops.forEach(d=>{rc.moveTo(d.x,d.y);rc.lineTo(d.x-d.l*.12,d.y+d.l);d.y+=d.v;d.x-=d.v*.12;if(d.y>rn.height){d.y=-20;d.x=Math.random()*(rn.width+60)}});rc.stroke();rid=requestAnimationFrame(rain)}
if(!still)rain();
const bar=$('.bar i'),pc=$('.pc'),dur=still?500:2600;
const hide=()=>{if(done)return;done=true;boot.classList.add('out');setTimeout(()=>{cancelAnimationFrame(rid);boot.remove()},650)};
let t0;(function prog(t){t0=t0||t;const p=Math.min(1,(t-t0)/dur),e=1-Math.pow(1-p,2.2);bar.style.width=e*100+'%';pc.textContent=(p<.35?'Starting up':p<.75?'Loading apps':p<1?'Almost there':'Welcome')+'… '+Math.round(e*100)+'%';p<1?requestAnimationFrame(prog):setTimeout(hide,250)})(performance.now());
boot.onclick=hide;
</script>
</body>
</html>
