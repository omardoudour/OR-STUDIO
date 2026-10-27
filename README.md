<!DOCTYPE html>
<html lang="en"><head>
<meta charset="UTF-8"><meta name="viewport" content="width=device-width,initial-scale=1">
<title>OR STUDIO — WHERE FEAR BECOMES ART</title>
<script src="https://cdn.tailwindcss.com"></script>
<link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@900&family=Poppins:wght@400;600&display=swap" rel="stylesheet">
<style>
*{font-family:Poppins} .orb{font-family:Orbitron} body{background:#000;color:#fff;cursor:none}
#cursor{width:20px;height:20px;border:2px solid #FF0033;border-radius:50%;position:fixed;pointer-events:none;z-index:99999;mix-blend-mode:screen;transition:.1s}
#dot{width:4px;height:4px;background:#FF0033;border-radius:50%;position:fixed;pointer-events:none;z-index:99999}
.grain{position:fixed;inset:0;pointer-events:none;opacity:.04;background-image:url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0naHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmcnIHdpZHRoPSIzMDAiIGhlaWdodD0iMzAwIj48ZmlsdGVyIGlkPSJhIj48ZmVUdXJidWxlbmNlIHR5cGU9ImZyYWN0YWxOb2lzZSIgYmFzZUZyZXF1ZW5jeT0iLjc1Ii8+PC9maWx0ZXI+PHJlY3Qgd2lkdGg9IjEwMCUiIGhlaWdodD0iMTAwJSIgZmlsdGVyPSJ1cmwoI2EpIi8+PC9zdmc+)}
.glitch:hover{animation:gl .3s infinite} @keyframes gl{0%{transform:translate(0)}20%{transform:translate(-2px,2px)}40%{transform:translate(2px,-2px)}100%{transform:translate(0)}}
@keyframes breath{0%,100%{text-shadow:0 0 20px #FF0033}50%{text-shadow:0 0 50px #FF0033,0 0 100px #FF0033}}
</style></head>
<body>
<div class="grain"></div><div id="cursor"></div><div id="dot"></div>

<nav class="fixed top-0 w-full z-50 bg-black/80 backdrop-blur-xl border-b border-zinc-900 px-6 py-4 flex justify-between">
<div class="flex items-center gap-8">
<h1 class="orb font-black text-2xl tracking-widest">OR<span class="text-[10px] block -mt-2 tracking-[6px]">STUDIO</span></h1>
<div class="hidden md:flex gap-6 text-xs text-zinc-400">
<a onclick="go('home')" class="hover:text-white cursor-pointer">HOME</a>
<a onclick="go('games')" class="hover:text-white cursor-pointer">GAMES</a>
<a onclick="go('comp')" class="hover:text-white cursor-pointer">COMPETITIONS</a>
<a onclick="go('dev')" class="hover:text-white cursor-pointer">DEVELOPERS</a>
</div></div>
<button onclick="openAdmin()" class="text-zinc-600 text-xs">🔒 ADMIN</button>
</nav>

<div id="home" class="page">
<div class="h-screen flex items-center justify-center text-center relative overflow-hidden">
<video autoplay muted loop class="absolute inset-0 w-full h-full object-cover opacity-30"><source src="https://videos.pexels.com/video-files/18069234/18069234-uhd_2560_1440_24fps.mp4"></video>
<div class="relative z-10">
<h1 class="orb text-[15vw] font-black leading-none glitch" style="animation:breath 3s infinite">OR</h1>
<p class="orb text-sm tracking-[12px] -mt-6">STUDIO</p>
<p class="mt-8 tracking-[8px] text-xs text-zinc-400">WHERE FEAR BECOMES ART — NADOR, MOROCCO</p>
<div class="mt-10 flex gap-4 justify-center">
<button onclick="go('comp')" class="bg-[#FF0033] px-8 py-3 orb text-xs font-bold hover:bg-white hover:text-black transition">ENTER THE VOID</button>
<button onclick="go('games')" class="border border-white px-8 py-3 orb text-xs">OUR GAMES</button>
</div></div>
<div class="absolute bottom-0 w-full grid grid-cols-3 text-center py-4 bg-black border-t border-zinc-900 text-xs orb">
<div>500K+<span class="block text-[9px] text-zinc-500">PLAYERS</span></div>
<div>3<span class="block text-[9px] text-zinc-500">GAMES</span></div>
<div>12<span class="block text-[9px] text-zinc-500">AWARDS</span></div>
</div></div>

<div class="max-w-6xl mx-auto p-6 grid md:grid-cols-3 gap-6 mt-10" id="gamesPreview"></div>

<div class="max-w-6xl mx-auto p-6 mt-10 bg-gradient-to-r from-red-900/30 to-black border border-red-900/50 rounded-2xl flex justify-between items-center">
<div><p class="orb text-red-500 text-xs">● LIVE TOURNAMENT</p><h3 class="text-xl font-bold mt-1" id="liveTitle">OR: FORGOTTEN — NIGHTMARE RUN</h3><p class="text-zinc-400 text-xs">Prize $500 • <span id="timer">00:00:00</span> left</p></div>
<button onclick="go('comp')" class="bg-white text-black px-6 py-2 orb text-xs font-bold">JOIN NOW</button>
</div>
</div>

<div id="games" class="page hidden pt-20 p-6 max-w-6xl mx-auto">
<div class="flex gap-3 mb-6"><button onclick="filterGames('all')" class="fbtn bg-white text-black px-4 py-1 text-xs">ALL</button><button onclick="filterGames('Horror')" class="fbtn border border-zinc-700 px-4 py-1 text-xs">HORROR</button><button onclick="filterGames('Survival')" class="fbtn border border-zinc-700 px-4 py-1 text-xs">SURVIVAL</button></div>
<div id="gamesGrid" class="grid md:grid-cols-3 gap-6"></div></div>

<div id="comp" class="page hidden pt-20 p-6 max-w-6xl mx-auto">
<div id="compList"></div>
<div id="compDetail" class="hidden mt-8 bg-zinc-900 rounded-2xl p-6">
<h2 id="cdTitle" class="orb text-2xl"></h2>
<div class="grid md:grid-cols-2 gap-6 mt-6">
<div><h4 class="text-xs text-zinc-500 orb mb-2">LEADERBOARD (LIVE)</h4><div id="lb"></div></div>
<div><h4 class="text-xs text-zinc-500 orb mb-2">REGISTER</h4>
<input id="rName" placeholder="Name" class="w-full bg-black border border-zinc-800 p-2 text-xs mb-2">
<input id="rDiscord" placeholder="Discord#0000" class="w-full bg-black border border-zinc-800 p-2 text-xs mb-2">
<button onclick="register()" class="w-full bg-[#FF0033] py-2 orb text-xs font-bold">CONFIRM ENTRY</button></div>
</div></div></div>

<div id="dev" class="page hidden pt-20 p-6 max-w-6xl mx-auto">
<h2 class="orb text-4xl mb-8">THE MINDS BEHIND FEAR</h2>
<div id="devGrid" class="grid md:grid-cols-4 gap-6"></div>
<div class="mt-16 border-t border-zinc-900 pt-8">
<h3 class="orb">2023 FOUNDED IN NADOR → 2024 FIRST PROTOTYPE → 2026 AAA</h3>
</div></div>

<div id="admin" class="page hidden fixed inset-0 bg-black z-[100] p-6 overflow-auto">
<div id="adminLogin" class="h-screen flex items-center justify-center flex-col">
<p class="orb text-xs tracking-[10px] mb-4">OR STUDIO SECURE TERMINAL</p>
<input id="adminPass" type="password" placeholder="ENTER CODE" class="bg-zinc-900 border border-red-900 p-3 text-center orb text-sm w-64">
<button onclick="login()" class="mt-4 bg-[#FF0033] px-8 py-2 orb text-xs">UNLOCK</button></div>
<div id="adminPanel" class="hidden max-w-6xl mx-auto">
<div class="flex justify-between items-center mb-8"><h2 class="orb text-2xl">ADMIN DASHBOARD</h2><button onclick="closeAdmin()" class="text-xs border px-4 py-1">EXIT</button></div>
<div class="grid md:grid-cols-3 gap-4 mb-8 text-xs orb">
<div class="bg-zinc-900 p-4 rounded">GAMES: <span id="aGames">0</span></div>
<div class="bg-zinc-900 p-4 rounded">COMPETITIONS: <span id="aComps">0</span></div>
<div class="bg-zinc-900 p-4 rounded">PARTICIPANTS: <span id="aParts">0</span></div>
</div>
<h3 class="orb text-sm mb-2">ADD GAME</h3>
<div class="flex gap-2 mb-8"><input id="gName" placeholder="Name" class="bg-zinc-900 border border-zinc-800 p-2 text-xs flex-1"><input id="gGenre" placeholder="Genre" class="bg-zinc-900 border border-zinc-800 p-2 text-xs w-24"><button onclick="addGame()" class="bg-white text-black px-4 orb text-xs">ADD</button></div>
<h3 class="orb text-sm mb-2">ADD COMPETITION</h3>
<div class="flex gap-2 mb-8"><input id="cName" placeholder="Title" class="bg-zinc-900 border border-zinc-800 p-2 text-xs flex-1"><input id="cPrize" placeholder="$500" class="bg-zinc-900 border border-zinc-800 p-2 text-xs w-20"><button onclick="addComp()" class="bg-[#FF0033] px-4 orb text-xs">CREATE</button></div>
<div id="aList" class="space-y-2 text-xs"></div>
</div></div>

<footer class="py-10 text-center text-[10px] text-zinc-600 orb tracking-widest border-t border-zinc-900 mt-20">OR STUDIO © 2026 — NADOR, MOROCCO — WHERE FEAR BECOMES ART</footer>

<script>
const $=s=>document.getElementById(s);
let games=JSON.parse(localStorage.getItem('or_games')||'null')||[{id:1,name:'OR: THE FORGOTTEN',genre:'Horror',players:'125K',rating:4.9},{id:2,name:'OR: ECHOES',genre:'Survival',players:'89K',rating:4.7},{id:3,name:'OR: VOID',genre:'Horror',players:'Coming Soon',rating:5}];
let comps=JSON.parse(localStorage.getItem('or_comps')||'null')||[{id:1,title:'NIGHTMARE RUN',game:'FORGOTTEN',prize:'$500',joined:47,max:100,ends:Date.now()+86400000*2},{id:2,title:'ECHO CHALLENGE',game:'ECHOES',prize:'$300',joined:12,max:50,ends:Date.now()+86400000*5}];
let parts=JSON.parse(localStorage.getItem('or_parts')||'[]');
let devs=[{name:'YASSINE OR',role:'Founder / Lead Dev'},{name:'AMINE B.',role:'Horror Artist'},{name:'SARA M.',role:'Level Designer'},{name:'DRISS K.',role:'Sound / Fear'}];
let currentComp=null;
function save(){localStorage.setItem('or_games',JSON.stringify(games));localStorage.setItem('or_comps',JSON.stringify(comps));localStorage.setItem('or_parts',JSON.stringify(parts))}
function go(p){document.querySelectorAll('.page').forEach(e=>e.classList.add('hidden'));$(p).classList.remove('hidden');window.scrollTo(0,0);render()}
function render(){
$('gamesPreview').innerHTML=games.map(g=>`<div class="bg-zinc-900 border border-zinc-800 rounded-xl p-4 hover:border-red-600 transition"><h4 class="orb text-sm">${g.name}</h4><p class="text-[10px] text-zinc-500">${g.genre} • ${g.players}</p></div>`).join('');
$('gamesGrid').innerHTML=games.map(g=>`<div data-genre="${g.genre}" class="game-card bg-zinc-900 border border-zinc-800 rounded-xl overflow-hidden hover:-translate-y-2 transition"><div class="h-40 bg-gradient-to-br from-zinc-800 to-black flex items-center justify-center orb">${g.name}</div><div class="p-4"><p class="text-xs text-zinc-500">${g.genre}</p><p class="text-xs mt-2">★ ${g.rating} • ${g.players} Players</p></div></div>`).join('');
$('compList').innerHTML=comps.map(c=>`<div class="bg-zinc-900 border border-zinc-800 rounded-xl p-4 flex justify-between items-center mb-3"><div><p class="orb text-sm">${c.title}</p><p class="text-[10px] text-zinc-500">${c.game} • ${c.prize} • ${c.joined}/${c.max}</p></div><button onclick="openComp(${c.id})" class="bg-white text-black px-4 py-1 orb text-[10px]">VIEW</button></div>`).join('');
$('devGrid').innerHTML=devs.map(d=>`<div class="bg-zinc-900 border border-zinc-800 rounded-xl p-6 text-center"><div class="w-20 h-20 mx-auto rounded-full bg-black border-2 border-red-600 mb-3"></div><p class="orb text-xs">${d.name}</p><p class="text-[10px] text-zinc-500">${d.role}</p></div>`).join('');
$('aGames').innerText=games.length;$('aComps').innerText=comps.length;$('aParts').innerText=parts.length;
$('aList').innerHTML=parts.map((p,i)=>`${i+1}. ${p.name} (${p.discord}) - ${p.compTitle} - ${p.score}pts`).join('<br>');
}
function filterGames(g){document.querySelectorAll('.game-card').forEach(c=>{c.style.display=(g==='all'||c.dataset.genre===g)?'block':'none'})}
function openComp(id){currentComp=comps.find(c=>c.id===id);$('compDetail').classList.remove('hidden');$('cdTitle').innerText=currentComp.title;let lp=parts.filter(p=>p.compId===id).sort((a,b)=>b.score-a.score);$('lb').innerHTML=lp.map((p,i)=>`<div class="flex justify-between text-xs py-1 border-b border-zinc-800"><span>#${i+1} ${p.name}</span><span class="text-red-500">${p.score}</span></div>`).join('')||'No entries yet';window.scrollTo(0,500)}
function register(){if(!currentComp)return;let n=$('rName').value,d=$('rDiscord').value;if(!n)return alert('Name required');parts.push({compId:currentComp.id,compTitle:currentComp.title,name:n,discord:d,score:Math.floor(Math.random()*1000)});currentComp.joined++;save();render();openComp(currentComp.id);alert('Registered!');}
function openAdmin(){document.querySelectorAll('.page').forEach(e=>e.classList.add('hidden'));$('admin').classList.remove('hidden')}
function closeAdmin(){ $('admin').classList.add('hidden');go('home')}
function login(){if($('adminPass').value==='082009'){$('adminLogin').classList.add('hidden');$('adminPanel').classList.remove('hidden');render()}else alert('WRONG CODE')}
function addGame(){let n=$('gName').value,g=$('gGenre').value||'Horror';if(!n)return;games.push({id:Date.now(),name:n,genre:g,players:'0',rating:5});save();render();$('gName').value=''}
function addComp(){let n=$('cName').value,p=$('cPrize').value||'$100';if(!n)return;comps.push({id:Date.now(),title:n,game:'FORGOTTEN',prize:p,joined:0,max:100,ends:Date.now()+86400000});save();render();$('cName').value=''}

// custom cursor
document.addEventListener('mousemove',e=>{let c=$('cursor'),d=$('dot');c.style.left=e.clientX-10+'px';c.style.top=e.clientY-10+'px';d.style.left=e.clientX-2+'px';d.style.top=e.clientY-2+'px';});
// live timer
setInterval(()=>{if(!comps[0])return;let diff=comps[0].ends-Date.now();if(diff<0)diff=0;let h=Math.floor(diff/3600000),m=Math.floor(diff%3600000/60000),s=Math.floor(diff%60000/1000);$('timer').innerText=`${h}h ${m}m ${s}s`;},1000);
render();
</script></body></html>
