<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"><meta name="viewport" content="width=device-width, initial-scale=1.0">
<link rel="icon" type="image/x-icon" href="/images/favicon.ico">
<title>Net Chat (P2P)</title>
<script src="https://cdn.tailwindcss.com"></script>
<script src="https://unpkg.com/lucide@latest"></script>
<style>
body{font-family:Inter,system-ui,sans-serif} .msg{max-width:80%;white-space:pre-wrap;word-break:break-word}
html{color-scheme:dark}
*{scrollbar-width:thin;scrollbar-color:#475569 #0f172a}
*::-webkit-scrollbar{width:10px;height:10px}
*::-webkit-scrollbar-track{background:#0f172a;border-radius:9999px}
*::-webkit-scrollbar-thumb{background:#475569;border-radius:9999px;border:2px solid #0f172a}
*::-webkit-scrollbar-thumb:hover{background:#64748b}
*::-webkit-scrollbar-corner{background:#0f172a}
</style>
</head>
<body class="bg-slate-950 text-slate-100 min-h-screen">
<div class="max-w-5xl mx-auto p-4">
  <header class="flex items-center justify-between mb-4">
    <div class="flex items-center gap-3"><div class="w-10 h-10 rounded-xl bg-indigo-600 flex items-center justify-center"><i data-lucide="shield" class="w-5 h-5"></i></div><div><h1 class="text-xl font-bold">Net Chat</h1><p class="text-xs text-slate-400">Anonymous P2P chat & file transfer (WebRTC)</p></div></div>
    <div id="connStatus" class="text-xs px-3 py-1 rounded-full bg-slate-800 border border-slate-700">Not connected</div>
  </header>

  <section id="lobby" class="grid md:grid-cols-2 gap-4">
    <div class="bg-slate-900 border border-slate-800 rounded-2xl p-5 space-y-4">
      <h2 class="font-semibold flex items-center gap-2"><i data-lucide="plus-circle" class="w-4 h-4 text-indigo-400"></i>Create session</h2>
      <p class="text-sm text-slate-400">Generate a 6-digit PIN, share link, and QR for others to join.</p>
      <button id="createBtn" class="w-full py-2.5 rounded-xl bg-indigo-600 hover:bg-indigo-500 font-medium">Create P2P Chat Session</button>
      <div id="createdBox" class="hidden space-y-3">
        <div><label class="text-xs text-slate-400">6-digit PIN</label><div class="flex gap-2"><input id="pinOut" readonly class="flex-1 min-w-0 bg-slate-950 border border-slate-700 rounded-lg px-3 py-2 font-mono text-lg tracking-widest"/><button id="copyPin" data-copy-icon class="shrink-0 px-3 py-2 rounded-lg bg-slate-800 border border-slate-700 flex items-center justify-center" title="Copy PIN" aria-label="Copy PIN"></button></div></div>
        <div><label class="text-xs text-slate-400">Share link</label><div class="flex gap-2"><input id="linkOut" readonly class="flex-1 min-w-0 bg-slate-950 border border-slate-700 rounded-lg px-3 py-2 text-xs"/><button id="copyLink" data-copy-icon class="shrink-0 px-3 py-2 rounded-lg bg-slate-800 border border-slate-700 flex items-center justify-center" title="Copy link" aria-label="Copy link"></button></div></div>
        <div class="flex flex-col items-center gap-2"><canvas id="qrCanvas" class="bg-white p-2 rounded-lg"></canvas><p class="text-xs text-slate-400">Scan to join this session</p></div>
        <p class="text-xs text-amber-300">Waiting for peer to join...</p>
      </div>
    </div>
    <div class="bg-slate-900 border border-slate-800 rounded-2xl p-5 space-y-4">
      <h2 class="font-semibold flex items-center gap-2"><i data-lucide="log-in" class="w-4 h-4 text-emerald-400"></i>Join session</h2>
      <p class="text-sm text-slate-400">Enter a 6-digit PIN or open a shared link.</p>
      <input id="pinIn" maxlength="300" placeholder="Enter 6-digit PIN or invite link" class="w-full bg-slate-950 border border-slate-700 rounded-lg px-3 py-2 font-mono tracking-widest"/>
      <button id="joinBtn" class="w-full py-2.5 rounded-xl bg-emerald-600 hover:bg-emerald-500 font-medium">Join Chat</button>
      <div class="text-xs text-slate-500">Connections are peer-to-peer via WebRTC. Signaling uses public relays; ICE uses public STUN/TURN servers.</div>
    </div>
  </section>

  <section id="chatUI" class="hidden grid md:grid-cols-[1fr_280px] gap-4">
    <div class="bg-slate-900 border border-slate-800 rounded-2xl flex flex-col h-[75vh]">
      <div class="p-3 border-b border-slate-800 flex items-center justify-between"><div><div class="font-semibold">Session <span id="roomLabel" class="font-mono text-indigo-300"></span></div><div id="peerInfo" class="text-xs text-slate-400">0 peers connected</div></div><button id="leaveBtn" class="text-xs px-3 py-1.5 rounded bg-slate-800 hover:bg-slate-700">Leave</button></div>
      <div id="messages" class="flex-1 overflow-y-auto p-4 space-y-3"></div>
      <div class="p-3 border-t border-slate-800 space-y-2">
        <div id="filePreview" class="hidden text-xs text-slate-300 flex items-center gap-2 bg-slate-950 p-2 rounded"><span id="fileName"></span><button id="clearFile" class="ml-auto text-rose-400">remove</button></div>
        <div class="flex gap-2 items-end">
          <label class="p-2.5 rounded-lg bg-slate-800 hover:bg-slate-700 cursor-pointer" title="Attach file"><i data-lucide="paperclip" class="w-4 h-4"></i><input id="fileInput" type="file" class="hidden"></label>
          <textarea id="msgInput" rows="2" placeholder="Type a message..." class="flex-1 bg-slate-950 border border-slate-700 rounded-lg px-3 py-2 text-sm"></textarea>
          <button id="sendBtn" class="px-4 py-2 rounded-lg bg-indigo-600 hover:bg-indigo-500 font-medium">Send</button>
        </div>
      </div>
    </div>
    <div class="bg-slate-900 border border-slate-800 rounded-2xl p-4 space-y-3 h-fit">
      <h3 class="font-semibold text-sm">Session details</h3>
      <div class="text-xs text-slate-400">PIN</div><div class="flex gap-2"><input id="pinSide" readonly class="flex-1 min-w-0 bg-slate-950 border border-slate-700 rounded px-2 py-1 font-mono"/><button id="copyPin2" data-copy-icon class="shrink-0 px-2 py-1.5 rounded bg-slate-800 flex items-center justify-center" title="Copy PIN" aria-label="Copy PIN"></button></div>
      <div class="text-xs text-slate-400">Share link</div><div class="flex gap-2"><input id="linkSide" readonly class="flex-1 min-w-0 bg-slate-950 border border-slate-700 rounded px-2 py-1 text-xs"/><button id="copyLink2" data-copy-icon class="shrink-0 px-2 py-1.5 rounded bg-slate-800 flex items-center justify-center" title="Copy link" aria-label="Copy link"></button></div>
      <canvas id="qrSide" class="bg-white p-2 rounded w-full"></canvas>
      <div class="text-xs text-slate-500">Files are sent directly P2P in chunks. Keep tab open during transfers.</div>
    </div>
  </section>
</div>

<script>
(function(){
'use strict';

const SHARE_BASE = 'https://jnetai.com/apps/p2p-chat/';
const TRYSTERO_URLS = [
  'https://cdn.jsdelivr.net/npm/trystero@0.21.8/nostr/+esm',
  'https://esm.sh/trystero@0.21.8/nostr'
];
const QR_URLS = [
  'https://cdn.jsdelivr.net/npm/qrcode@1.5.3/+esm',
  'https://esm.sh/qrcode@1.5.3'
];
const cfg = { appId: 'netchat-p2p-demo-v1', rtcConfig: { iceServers: [
  {urls:['stun:stun.l.google.com:19302','stun:stun1.l.google.com:19302']},
  {urls:['turn:openrelay.metered.ca:80'], username:'openrelayproject', credential:'openrelayproject'},
  {urls:['turn:openrelay.metered.ca:443'], username:'openrelayproject', credential:'openrelayproject'},
  {urls:['turn:openrelay.metered.ca:443?transport=tcp'], username:'openrelayproject', credential:'openrelayproject'}
]}};

let room = null, sendMsg = null, sendFileMeta = null, sendFileChunk = null, sendFileEnd = null;
let peers = new Set();
let pendingFile = null;
let trysteroMod = null, qrMod = null, starting = false;
let currentPin = null, hasConnected = false;
let reconnectTimer = null, reconnectAttempts = 0, reconnecting = false;
const outbox = [];
let flushing = false;
const incomingFiles = new Map();
const $ = id => document.getElementById(id);

function setStatus(text, ok=false){ const el=$('connStatus'); el.textContent=text; el.className='text-xs px-3 py-1 rounded-full border '+(ok?'bg-emerald-900/40 border-emerald-700 text-emerald-300':'bg-slate-800 border-slate-700'); }
function genPin(){ return String(Math.floor(100000 + Math.random()*900000)); }
function roomLink(pin){ const u = new URL(SHARE_BASE); u.searchParams.set('code', pin); return u.toString(); }
function updateUrl(pin){ try{ history.replaceState(null, '', '?code='+encodeURIComponent(pin)); }catch(e){} }
async function copyText(t){ try{ await navigator.clipboard.writeText(t); toast('Copied'); }catch(e){ prompt('Copy:', t); } }
function toast(t){ setStatus(t, peers.size>0); setTimeout(()=>setStatus(peers.size?`Connected (${peers.size} peer)`:(room?'Waiting for peer':'Not connected'), peers.size>0), 1500); }
function esc(s){ return String(s==null?'':s).replace(/[&<>"]/g,c=>({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;'}[c])); }
function fmtBytes(b){ if(!b) return '0 B'; const k=1024,s=['B','KB','MB','GB'],i=Math.floor(Math.log(b)/Math.log(k)); return (b/Math.pow(k,i)).toFixed(1)+' '+s[i]; }
const MIME_BY_EXT={png:'image/png',jpg:'image/jpeg',jpeg:'image/jpeg',gif:'image/gif',webp:'image/webp',svg:'image/svg+xml',bmp:'image/bmp',avif:'image/avif',ico:'image/x-icon',pdf:'application/pdf',txt:'text/plain',md:'text/markdown',json:'application/json',mp4:'video/mp4',webm:'video/webm',mp3:'audio/mpeg',wav:'audio/wav',ogg:'audio/ogg',zip:'application/zip'};
function mimeFor(name){ const ext=String(name||'').split('.').pop().toLowerCase(); return MIME_BY_EXT[ext]||'application/octet-stream'; }
function isImageFile(file){ return /^image\//.test(file.type||'') || /\.(png|jpe?g|gif|webp|svg|bmp|avif|ico)$/i.test(file.name||''); }
const COPY_SVG='<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="w-4 h-4" aria-hidden="true"><rect width="14" height="14" x="8" y="8" rx="2" ry="2"/><path d="M4 16c-1.1 0-2-.9-2-2V4c0-1.1.9-2 2-2h10c1.1 0 2 .9 2 2"/></svg>';

async function importFirst(urls, pick, label){
  let lastErr = null;
  for(const url of urls){
    try{
      const mod = await import(url);
      const value = pick(mod);
      if(value) return value;
      lastErr = new Error(label+' missing expected export');
    }catch(e){ lastErr = e; console.warn('[netchat] failed to load '+label+' from '+url, e); }
  }
  throw lastErr || new Error('Unable to load '+label);
}
async function loadTrystero(){
  if(!trysteroMod) trysteroMod = await importFirst(TRYSTERO_URLS, m => (m && m.joinRoom) ? m : null, 'signaling library');
  return trysteroMod;
}
async function loadQr(){
  if(qrMod === null){
    try{
      qrMod = await importFirst(QR_URLS, m => { const q = m && m.default ? m.default : m; return (q && typeof q.toCanvas === 'function') ? q : null; }, 'QR library');
    }catch(e){ qrMod = false; console.warn('[netchat] QR library unavailable', e); }
  }
  return qrMod || null;
}
async function renderQr(canvasId, text){
  try{
    const c = $(canvasId); if(!c) return;
    const QR = await loadQr(); if(!QR) return;
    await QR.toCanvas(c, text, { width: 240, margin: 1 });
  }catch(e){ console.error('QR render failed', e); }
}
function scrollMessagesToBottom(){
  const box=$('messages'); if(!box) return;
  box.scrollTop=box.scrollHeight;
}
function focusComposer(){
  const input=$('msgInput'), chat=$('chatUI');
  if(!input || !chat || chat.classList.contains('hidden')) return;
  try{ input.focus({preventScroll:true}); }catch(e){ input.focus(); }
}
function showChat(pin){
  $('lobby').classList.add('hidden'); $('chatUI').classList.remove('hidden');
  $('roomLabel').textContent = pin; $('pinSide').value = pin; $('linkSide').value = roomLink(pin);
  renderQr('qrSide', roomLink(pin));
  setStatus('Waiting for peer', false);
  scrollMessagesToBottom();
  setTimeout(focusComposer, 0);
}

function addMessage({from, text, ts, self=false, file=null}){
  const wrap=document.createElement('div'); wrap.className='flex '+(self?'justify-end':'justify-start');
  const b=document.createElement('div'); b.className='msg rounded-2xl px-3 py-2 text-sm '+(self?'bg-indigo-600':'bg-slate-800 border border-slate-700');
  const meta=`<div class="text-[10px] opacity-70 mb-1">${self?'You':esc(from||'peer')} &bull; ${new Date(ts||Date.now()).toLocaleTimeString()}</div>`;
  let body='';
  if(text) body += `<div>${esc(text)}</div>`;
  if(file){
    const url=URL.createObjectURL(file.blob);
    const preview = isImageFile(file)
      ? `<a href="${url}" target="_blank" rel="noopener"><img src="${url}" alt="${esc(file.name)}" class="mt-2 max-h-64 max-w-full rounded-lg object-contain bg-black/20"/></a>`
      : '';
    body += `<div class="mt-2 p-2 rounded bg-black/20"><div class="font-medium text-xs">${esc(file.name)} <span class="opacity-70">(${fmtBytes(file.size)})</span></div>
      ${preview}
      <div class="flex gap-2 mt-2"><a href="${url}" download="${esc(file.name)}" class="px-2 py-1 rounded bg-emerald-700 text-xs">Download</a>
      <button data-copyfile="${esc(file.name)}" class="px-2 py-1 rounded bg-slate-700 text-xs">Copy name</button></div></div>`;
  }
  b.innerHTML = meta + body + `<div class="mt-1 flex justify-end"><button class="copymsg shrink-0 p-1.5 rounded-md hover:bg-white/15 opacity-70" title="Copy message" aria-label="Copy message">${COPY_SVG}</button></div>`;
  b.querySelector('.copymsg').onclick=()=>copyText(text||(file?file.name:''));
  const cf=b.querySelector('[data-copyfile]'); if(cf) cf.onclick=()=>copyText(cf.dataset.copyfile);
  wrap.appendChild(b); $('messages').appendChild(wrap);
  scrollMessagesToBottom();
  requestAnimationFrame(scrollMessagesToBottom);
  const img=b.querySelector('img');
  if(img){
    img.addEventListener('load', scrollMessagesToBottom, {once:true});
    if(img.complete) scrollMessagesToBottom();
  }
  setTimeout(scrollMessagesToBottom, 120);
  focusComposer();
}

function canSend(){ return !!(room && sendMsg && peers.size>0); }
function clearReconnectTimer(){ if(reconnectTimer){ clearTimeout(reconnectTimer); reconnectTimer=null; } }
function scheduleReconnect(delay){
  if(!currentPin || reconnecting || starting) return;
  if(room && peers.size>0){ clearReconnectTimer(); return; }
  if(reconnectTimer) return;
  const wait = (delay==null) ? Math.min(15000, 4000*Math.pow(2, Math.min(reconnectAttempts, 3))) : delay;
  reconnectTimer=setTimeout(()=>{ reconnectTimer=null; reconnectNow(); }, wait);
}
async function reconnectNow(){
  if(!currentPin || reconnecting || starting) return;
  if(room && peers.size>0){ clearReconnectTimer(); return; }
  reconnecting=true;
  setStatus('Reconnecting...', false);
  try{ await startRoom(currentPin, true); }
  finally{ reconnecting=false; }
  if(!peers.size){
    reconnectAttempts++;
    scheduleReconnect();
  }
}
async function flushOutbox(){
  if(flushing || !canSend()) return;
  flushing=true;
  try{
    while(outbox.length && canSend()){
      const item=outbox.shift();
      if(item.kind==='text') await sendMsg(item.payload);
      else if(item.kind==='file') await transmitFile(item.file, item.caption);
    }
  }catch(e){
    console.error('Outbox flush failed', e);
    scheduleReconnect(0);
  }finally{
    flushing=false;
  }
  if(outbox.length && peers.size===0) scheduleReconnect();
}

async function startRoom(pin, isReconnect=false){
  if(!pin || starting) return;
  currentPin = pin;
  try{ sessionStorage.setItem('netchat-pin', pin); }catch(e){}
  if(!isReconnect){
    hasConnected = false;
    outbox.length = 0;
    reconnectAttempts = 0;
    clearReconnectTimer();
    updateUrl(pin);
  }
  starting = true;
  if(room){ try{ await room.leave(); }catch(e){} room = null; }
  peers.clear(); incomingFiles.clear();
  sendMsg = sendFileMeta = sendFileChunk = sendFileEnd = null;
  $('peerInfo').textContent = '0 peers connected';
  setStatus('Connecting to room...', false);
  try{
    const { joinRoom } = await loadTrystero();
    room = joinRoom(cfg, 'netchat-'+pin);
    const [_sendMsg, _getMsg] = room.makeAction('msg');
    const [_sendMeta, _getMeta] = room.makeAction('fmeta');
    const [_sendChunk, _getChunk] = room.makeAction('fchunk');
    const [_sendEnd, _getEnd] = room.makeAction('fend');
    sendMsg=_sendMsg; sendFileMeta=_sendMeta; sendFileChunk=_sendChunk; sendFileEnd=_sendEnd;

    room.onPeerJoin(id=>{
      peers.add(id);
      hasConnected = true;
      reconnectAttempts = 0;
      clearReconnectTimer();
      $('peerInfo').textContent = `${peers.size} peer(s) connected`;
      setStatus(`Connected (${peers.size} peer)`, true);
      addMessage({from:'system', text:'Peer joined: '+String(id).slice(0,6), self:false, ts:Date.now()});
      flushOutbox();
    });
    room.onPeerLeave(id=>{
      peers.delete(id);
      $('peerInfo').textContent = `${peers.size} peer(s) connected`;
      setStatus(peers.size?`Connected (${peers.size} peer)`:(hasConnected?'Reconnecting...':'Waiting for peer'), peers.size>0);
      if(peers.size===0 && currentPin && (hasConnected || outbox.length)) scheduleReconnect(1000);
    });

    _getMsg((data, id)=> addMessage({from:String(id).slice(0,6), text:data.text, ts:data.ts, self:false}));
    _getMeta((m, id)=> incomingFiles.set(m.id, {meta:m, chunks:[], received:0, from:id}));
    _getChunk((data, id, meta)=>{
      if(!meta) return;
      const e=incomingFiles.get(meta.id); if(!e) return;
      const chunk = data instanceof Uint8Array ? data : new Uint8Array(data);
      e.chunks[meta.i]=chunk;
      e.received+=chunk.byteLength;
    });
    _getEnd((eInfo, id)=>{
      const e=incomingFiles.get(eInfo.id); if(!e) return;
      incomingFiles.delete(eInfo.id);
      const parts=[];
      for(let i=0;i<e.chunks.length;i++){ if(e.chunks[i]) parts.push(e.chunks[i]); }
      const type=e.meta.type||mimeFor(e.meta.name);
      const blob=new Blob(parts, {type});
      if(blob.size!==e.meta.size){
        addMessage({from:'system', text:`File "${e.meta.name}" failed: received ${fmtBytes(blob.size)} of ${fmtBytes(e.meta.size)}`, self:false, ts:Date.now()});
        return;
      }
      addMessage({from:String(id).slice(0,6), text:eInfo.text||'', file:{name:e.meta.name,size:e.meta.size,type,blob}, ts:Date.now(), self:false});
    });

    showChat(pin);
  }catch(e){
    console.error(e);
    setStatus('Connection failed', false);
    if(isReconnect){ scheduleReconnect(); }
    else alert('Could not start chat: ' + (e && e.message ? e.message : e));
  }finally{
    starting = false;
  }
}

function queuedNotice(){
  if(!hasConnected){ toast('Will send when peer connects'); return; }
  toast('Queued — reconnecting...');
  scheduleReconnect(0);
}
function addLocalFileMessage(file, caption, ts){
  const type=file.type||mimeFor(file.name);
  addMessage({from:'me', text:caption||'', file:{name:file.name,size:file.size,type,blob:file}, ts:ts||Date.now(), self:true});
}
async function transmitFile(file, caption){
  if(!sendFileMeta || !sendFileChunk || !sendFileEnd) throw new Error('Not connected');
  const id=crypto.randomUUID();
  const type=file.type||mimeFor(file.name);
  const meta={id,name:file.name,size:file.size,type};
  await sendFileMeta(meta);
  const buf=new Uint8Array(await file.arrayBuffer());
  const chunkSize=16*1024;
  for(let i=0,seq=0;i<buf.length;i+=chunkSize,seq++){
    await sendFileChunk(buf.slice(i,i+chunkSize), null, {id,i:seq});
  }
  await sendFileEnd({id,text:caption||''});
}

async function sendCurrent(){
  const text=$('msgInput').value; if(!text && !pendingFile) return;
  const ts=Date.now();
  if(pendingFile){
    const file=pendingFile;
    pendingFile=null; $('filePreview').classList.add('hidden'); $('fileInput').value='';
    addLocalFileMessage(file, text, ts);
    if(canSend()){ try{ await transmitFile(file, text); }catch(e){ console.error(e); outbox.push({kind:'file', file, caption:text}); queuedNotice(); } }
    else { outbox.push({kind:'file', file, caption:text}); queuedNotice(); }
  } else {
    const payload={text, ts};
    addMessage({from:'me', text, ts, self:true});
    if(canSend()){ try{ await sendMsg(payload); }catch(e){ console.error(e); outbox.push({kind:'text', payload}); queuedNotice(); } }
    else { outbox.push({kind:'text', payload}); queuedNotice(); }
  }
  $('msgInput').value='';
  focusComposer();
}

function parseCode(raw){
  const v=(raw||'').trim(); if(!v) return '';
  try{ const u=new URL(v); const c=u.searchParams.get('code')||u.searchParams.get('room'); if(c) return c; }catch(e){}
  const m=v.match(/[?&#](?:code|room)=([^&\s]+)/i); if(m) return decodeURIComponent(m[1]);
  const d=v.match(/\b\d{6}\b/); if(d) return d[0];
  return v;
}

$('createBtn').onclick=async()=>{
  const btn=$('createBtn'); btn.disabled=true;
  try{
    const pin=genPin(); const link=roomLink(pin);
    $('pinOut').value=pin; $('linkOut').value=link;
    $('createdBox').classList.remove('hidden');
    updateUrl(pin);
    renderQr('qrCanvas', link);
    await startRoom(pin);
  }finally{ btn.disabled=false; }
};
$('joinBtn').onclick=()=>{
  const pin=parseCode($('pinIn').value);
  if(!pin){ alert('Enter a PIN or invite link'); return; }
  $('pinIn').value=pin;
  updateUrl(pin);
  startRoom(pin);
};
$('sendBtn').onclick=sendCurrent;
$('msgInput').addEventListener('keydown',e=>{ if(e.key==='Enter' && !e.shiftKey){ e.preventDefault(); sendCurrent(); }});
$('fileInput').onchange=e=>{ pendingFile=e.target.files[0]||null; if(pendingFile){ $('fileName').textContent=`${pendingFile.name} (${fmtBytes(pendingFile.size)})`; $('filePreview').classList.remove('hidden'); }};
$('clearFile').onclick=()=>{ pendingFile=null; $('fileInput').value=''; $('filePreview').classList.add('hidden'); };
$('copyPin').onclick=()=>copyText($('pinOut').value); $('copyLink').onclick=()=>copyText($('linkOut').value);
$('copyPin2').onclick=()=>copyText($('pinSide').value); $('copyLink2').onclick=()=>copyText($('linkSide').value);
$('leaveBtn').onclick=async()=>{
  currentPin=null; hasConnected=false; outbox.length=0; clearReconnectTimer();
  try{ sessionStorage.removeItem('netchat-pin'); }catch(e){}
  try{ if(room) await room.leave(); }catch(e){}
  location.href=location.origin+location.pathname;
};

const qp=new URLSearchParams(location.search); const hp=new URLSearchParams(location.hash.slice(1));
let savedPin=null; try{ savedPin=sessionStorage.getItem('netchat-pin'); }catch(e){}
const initial=qp.get('code')||qp.get('room')||hp.get('room')||hp.get('code')||savedPin;
if(initial){ $('pinIn').value=initial; startRoom(initial); }

document.querySelectorAll('[data-copy-icon]').forEach(el=>{ el.innerHTML=COPY_SVG; });
function resumeConnection(){
  focusComposer();
  if(currentPin && peers.size===0 && (hasConnected || outbox.length)) scheduleReconnect(0);
}
window.addEventListener('focus', resumeConnection);
window.addEventListener('online', resumeConnection);
window.addEventListener('offline', ()=>{ if(currentPin) setStatus('Offline — will reconnect', false); });
document.addEventListener('visibilitychange', ()=>{ if(!document.hidden) resumeConnection(); });
setInterval(()=>{
  if(!currentPin || starting || reconnecting || peers.size>0) return;
  if(hasConnected || outbox.length) scheduleReconnect();
}, 12000);
if(window.lucide && lucide.createIcons) lucide.createIcons();
})();
</script>
</body>
</html>
