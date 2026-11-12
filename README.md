<!doctype html>
<html lang="fr">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<meta name="theme-color" content="#090817">
<title>Anime Universe</title>
<style>
:root{
--bg:#080716;--panel:#121027;--text:#f7f5ff;
--muted:#aaa5c7;--purple:#9b4dff;--blue:#28baff;
--line:#30265b
}
*{box-sizing:border-box}
body{
margin:0;background:radial-gradient(ellipse at 75% 0%,#24104b 0,transparent 38%),var(--bg);
color:var(--text);font-family:system-ui,Arial,sans-serif
}
button,input,select{font:inherit}
button{cursor:pointer}
.wrap{width:min(1120px,92%);margin:auto}
header{
position:sticky;top:0;z-index:5;
background:#090817ed;border-bottom:1px solid var(--line)
}
.nav{
height:68px;display:flex;align-items:center;
justify-content:space-between;gap:12px
}
.brand{font-weight:900;letter-spacing:.5px}
.brand b{color:#b77aff}
.nav a{color:var(--muted);text-decoration:none}
.hero{padding:42px 0 30px}
.hero h1{font-size:clamp(32px,6vw,58px);line-height:1.05;margin:8px 0}
.gradient{
background:linear-gradient(90deg,#fff,#7edcff,#c18aff);
color:transparent;background-clip:text
}
.hero p,.muted{color:var(--muted)}
.notice{
border:1px solid #58428d;background:#15102b;
padding:14px 16px;border-radius:14px;color:#dcd6f5;line-height:1.5
}
.section-head{display:flex;justify-content:space-between;align-items:center;gap:12px;margin:26px 0 14px}
.section-head h2{margin:0}
.search{
width:100%;padding:13px 16px;border:1px solid #57418d;
border-radius:14px;background:#100d25;color:white;outline:none
}
.filters{display:flex;gap:8px;overflow:auto;padding:12px 0}
.chip,.btn{
border:1px solid var(--line);border-radius:22px;
padding:9px 14px;background:#17132e;color:#eee;white-space:nowrap
}
.chip.active,.btn.primary{
background:linear-gradient(100deg,#762cff,#287dff);border:0
}
.grid{display:grid;grid-template-columns:repeat(3,1fr);gap:14px}
.card{
background:linear-gradient(160deg,#171431,#0e0c20);
border:1px solid var(--line);border-radius:16px;overflow:hidden
}
.art{height:120px;display:grid;place-items:center;font-size:52px;background:var(--art)}
.body{padding:14px}
.body h3{margin:0 0 5px}
.body p{margin:0 0 12px;color:var(--muted);font-size:13px}
.playerbox{
margin:28px 0;padding:18px;background:#100d24;
border:1px solid #57418d;border-radius:18px
}
.playerbox h2{margin:0 0 8px}
.screen{
aspect-ratio:16/9;background:#020208;border-radius:12px;
overflow:hidden;display:grid;place-items:center;margin:14px 0
}
.screen video,.screen iframe{width:100%;height:100%;border:0;background:#000}
.placeholder{text-align:center;color:#aaa5c7;padding:20px}
.controls{display:flex;gap:10px;flex-wrap:wrap;align-items:center}
.controls select{
flex:1;min-width:180px;padding:11px;border-radius:10px;
background:#17132e;color:white;border:1px solid var(--line)
}
.episode-list{display:flex;gap:8px;flex-wrap:wrap;margin-top:12px}
.episode-list button{
border:1px solid var(--line);border-radius:10px;
background:#17132e;color:white;padding:9px 12px
}
.episode-list button.active{border-color:#a879ff;background:#2a1749}
.small{font-size:12px;color:var(--muted);line-height:1.5}
.empty{
padding:24px;text-align:center;color:var(--muted);
border:1px dashed var(--line);border-radius:14px;grid-column:1/-1
}
footer{margin-top:36px;padding:24px 0;border-top:1px solid var(--line);color:var(--muted);font-size:12px}
@media(max-width:700px){.grid{grid-template-columns:repeat(2,1fr)}.hero{padding-top:28px}.playerbox{padding:12px}}
@media(max-width:430px){.grid{gap:9px}.art{height:100px}.body{padding:10px}.body h3{font-size:14px}}
</style>
</head>
<body>

<header>
<div class="wrap nav">
<div class="brand">✦ ANIME <b>UNIVERSE</b></div>
<a href="#catalogue">Catalogue</a>
<a href="#lecteur">Lecteur</a>
<a href="#favoris">Favoris</a>
</div>
</header>

<main class="wrap">

<section class="hero">
<div class="muted">TA PLATEFORME DE DÉCOUVERTE ET DE VISIONNAGE</div>
<h1>Bienvenue dans<br><span class="gradient">ANIME UNIVERSE V4</span></h1>
<p>Découvre tes prochaines séries et regarde les épisodes autorisés dans le lecteur intégré.</p>
<div class="notice">
<strong>Sans publicité ajoutée par Anime Universe.</strong>
Les vidéos doivent provenir de fichiers que tu as le droit d'héberger ou d'un fournisseur qui autorise l'intégration et garantit une diffusion sans publicité.
</div>
</section>

<section id="catalogue">
<div class="section-head"><h2>🎌 Catalogue</h2></div>
<input id="search" class="search" type="search" placeholder="Rechercher un animé…">
<div class="filters" id="filters"></div>
<div class="grid" id="catalogueGrid"></div>
</section>

<section class="playerbox" id="lecteur">
<h2>▶ Lecteur Anime Universe</h2>
<div id="nowPlaying" class="muted">Choisis un animé puis un épisode.</div>
<div class="screen" id="screen">
<div class="placeholder">
🌌 Ton épisode apparaîtra ici.<br>
<span class="small">Aucune vidéo n'est chargée tant qu'une source autorisée n'a pas été configurée.</span>
</div>
</div>
<div class="controls">
<select id="episodeSelect" aria-label="Choisir un épisode">
<option value="">Choisir un épisode</option>
</select>
<button class="btn primary" id="playBtn">Lire l'épisode</button>
<button class="btn" id="fullscreenBtn">Plein écran</button>
</div>
<div class="episode-list" id="episodeList"></div>
<p class="small" id="playerStatus">
Le lecteur accepte les fichiers MP4/WebM hébergés avec autorisation et les lecteurs intégrés de fournisseurs autorisés.
</p>
</section>

<section id="favoris">
<div class="section-head"><h2>❤️ Mes favoris</h2></div>
<div class="grid" id="favoritesGrid"></div>
</section>

</main>

<footer>
<div class="wrap">
© 2026 Anime Universe. Projet indépendant.
Les droits des œuvres et des vidéos appartiennent à leurs propriétaires.
</div>
</footer>

<script>

const anime = [

{id:1,title:"One Piece",year:1999,genres:["Aventure","Action"],mark:"☠️",art:"linear-gradient(135deg,#114c78,#8b3e27)",desc:"Luffy et son équipage partent à la recherche du légendaire trésor One Piece.",episodes:[]},

{id:2,title:"Naruto",year:2002,genres:["Action","Aventure"],mark:"🍥",art:"linear-gradient(135deg,#e56b18,#5a267f)",desc:"Un jeune ninja poursuit son rêve de devenir Hokage.",episodes:[]},

{id:3,title:"Demon Slayer",year:2019,genres:["Action","Fantastique"],mark:"⚔️",art:"linear-gradient(135deg,#0c786b,#8d294c)",desc:"Tanjiro se lance dans une quête pour protéger sa famille.",episodes:[]},

{id:4,title:"Haikyu!!",year:2014,genres:["Sport","Comédie"],mark:"🏐",art:"linear-gradient(135deg,#d56b16,#164f80)",desc:"Une équipe de volley vise les sommets grâce au travail collectif.",episodes:[]},

{id:5,title:"Spy x Family",year:2022,genres:["Comédie","Action"],mark:"🕵️",art:"linear-gradient(135deg,#376a54,#593b83)",desc:"Une famille atypique tente de garder ses secrets.",episodes:[]},

{id:6,title:"Frieren",year:2023,genres:["Fantastique","Aventure"],mark:"✨",art:"linear-gradient(135deg,#216e91,#6e3c91)",desc:"Un voyage sur le temps, les souvenirs et l'amitié.",episodes:[]}

];

const categories=["Tous","Action","Aventure","Comédie","Fantastique","Sport"];

let active="Tous",selectedAnime=null;

const favs=()=>JSON.parse(localStorage.getItem("au_v4_favs")||"[]");

function card(a){
return `<article class="card">
<div class="art" style="--art:${a.art}">${a.mark}</div>
<div class="body">
<h3>${a.title}</h3>
<p>${a.year} · ${a.genres.join(" · ")}</p>
<p>${a.desc}</p>
<div class="controls">
<button class="btn primary" onclick="chooseAnime(${a.id})">Ouvrir</button>
<button class="btn" onclick="toggleFav(${a.id})">${favs().includes(a.id)?"♥":"♡"}</button>
</div>
</div>
</article>`;
}

function render(){
const q=document.getElementById('search').value.trim().toLowerCase();

const list=anime.filter(a=>
(active==='Tous'||a.genres.includes(active))&&
(a.title.toLowerCase().includes(q)||a.genres.join(' ').toLowerCase().includes(q))
);

document.getElementById('catalogueGrid').innerHTML=
list.length?list.map(card).join(''):'<div class="empty">Aucun résultat.</div>';

document.getElementById('favoritesGrid').innerHTML=
anime.filter(a=>favs().includes(a.id)).map(card).join('')||
'<div class="empty">Tes favoris apparaîtront ici.</div>';

document.getElementById('filters').innerHTML=
categories.map(c=>`<button class="chip ${active===c?'active':''}" onclick="active='${c}';render()">${c}</button>`).join('');
}

function chooseAnime(id){
selectedAnime=anime.find(a=>a.id===id);

document.getElementById('nowPlaying').textContent=
selectedAnime.title+' — '+selectedAnime.year;

const sel=document.getElementById('episodeSelect');

sel.innerHTML='<option value="">Choisir un épisode</option>'+
selectedAnime.episodes.map((e,i)=>
`<option value="${i}">${e.title||'Épisode '+e.number}</option>`
).join('');

document.getElementById('episodeList').innerHTML=
selectedAnime.episodes.length?
selectedAnime.episodes.map((e,i)=>
`<button onclick="playEpisode(${i})">Épisode ${e.number}</button>`
).join(''):
'<div class="small">Aucun épisode configuré pour le moment.</div>';

document.getElementById('screen').innerHTML=
'<div class="placeholder">📺 '+selectedAnime.title+
'<br><span class="small">Sélectionne un épisode.</span></div>';

document.getElementById('playerStatus').textContent=
'Aucun épisode disponible tant qu’une source autorisée n’est pas configurée.';

document.getElementById('lecteur').scrollIntoView({behavior:'smooth'});
}

function playEpisode(index){
if(!selectedAnime)return;

const e=selectedAnime.episodes[index];
if(!e)return;

const screen=document.getElementById('screen');

if(e.type==='file'){
const v=document.createElement('video');
v.controls=true;
v.playsInline=true;
v.preload='metadata';
v.src=e.src;
screen.replaceChildren(v);
v.play().catch(()=>{});

}else if(e.type==='embed'){
const f=document.createElement('iframe');
f.src=e.src;
f.title=selectedAnime.title;
f.allowFullscreen=true;
f.allow='fullscreen; autoplay; encrypted-media; picture-in-picture';
screen.replaceChildren(f);

}else{
return;
}

document.getElementById('nowPlaying').textContent=
selectedAnime.title+' — '+(e.title||'Épisode '+e.number);

document.getElementById('episodeSelect').value=String(index);
}

function toggleFav(id){
let f=favs();

f=f.includes(id)?f.filter(x=>x!==id):[...f,id];

localStorage.setItem('au_v4_favs',JSON.stringify(f));

render();
}

document.getElementById('search').addEventListener('input',render);

document.getElementById('playBtn').addEventListener('click',()=>{
const i=document.getElementById('episodeSelect').value;

if(i!=='')playEpisode(Number(i));
else document.getElementById('playerStatus').textContent=
'Choisis d’abord un épisode.';
});

document.getElementById('fullscreenBtn').addEventListener('click',()=>{
const s=document.getElementById('screen');
if(s.requestFullscreen)s.requestFullscreen();
});

render();

</script>
</body>
</html>

