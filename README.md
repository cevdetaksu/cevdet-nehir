[index.html](https://github.com/user-attachments/files/25294500/index.html)
<!DOCTYPE html>
<html lang="tr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>CEVDET ❤️ NEHİR</title>

<style>
*{margin:0;padding:0;box-sizing:border-box;font-family:'Segoe UI',sans-serif}

body{
height:100vh;
display:flex;
flex-direction:column;
align-items:center;
background:linear-gradient(135deg,#ff4b7d,#ff758c,#ff7eb3);
color:white;
overflow:hidden;
}

h1{
margin-top:15px;
font-size:26px;
letter-spacing:2px;
animation: glow 2s infinite alternate;
}

@keyframes glow{
from{ text-shadow:0 0 5px #fff;}
to{ text-shadow:0 0 20px #fff;}
}

#timer{
margin-top:5px;
font-size:18px;
}

#startScreen{
position:fixed;
inset:0;
background:rgba(0,0,0,0.6);
display:flex;
justify-content:center;
align-items:center;
flex-direction:column;
z-index:10;
}

#startScreen button{
padding:15px 30px;
font-size:18px;
border:none;
border-radius:25px;
background:white;
color:#ff4b7d;
}

#game{
display:grid;
grid-template-columns:repeat(10,40px);
grid-template-rows:repeat(10,40px);
gap:4px;
margin-top:20px;
padding:15px;
background:rgba(255,255,255,0.1);
backdrop-filter:blur(10px);
border-radius:20px;
}

.cell{
width:40px;
height:40px;
border-radius:8px;
transition:0.2s;
}

.wall{background:white;}
.player{
background:#ff003c;
box-shadow:0 0 15px #ff003c;
animation:pulse 1s infinite;
}
@keyframes pulse{
0%{transform:scale(1);}
50%{transform:scale(1.15);}
100%{transform:scale(1);}
}
.goal{
background:gold;
box-shadow:0 0 15px gold;
}

.controls{
margin-top:20px;
display:grid;
grid-template-columns:60px 60px 60px;
gap:10px;
}

.controls button{
padding:15px;
font-size:20px;
border:none;
border-radius:15px;
background:white;
color:#ff4b7d;
}

#win{
display:none;
position:fixed;
top:50%;
left:50%;
transform:translate(-50%,-50%) scale(0);
background:white;
color:#ff4b7d;
padding:35px;
border-radius:25px;
text-align:center;
animation:pop 0.8s forwards;
z-index:20;
}

@keyframes pop{
to{transform:translate(-50%,-50%) scale(1);}
}

#win h2{
margin-bottom:15px;
}

#hearts{
position:fixed;
inset:0;
pointer-events:none;
}

.heart{
position:absolute;
font-size:25px;
animation:float 4s linear forwards;
}

@keyframes float{
from{transform:translateY(100vh);}
to{transform:translateY(-10vh);}
}
</style>
</head>

<body>

<div id="startScreen">
<h2>Hazır mısın Nehir? 💕</h2><br>
<button onclick="startGame()">Oyuna Başla</button>
</div>

<h1>CEVDET ❤️ NEHİR</h1>
<div id="timer">Süre: 0 saniye</div>

<div id="game"></div>

<div class="controls">
<div></div>
<button onclick="move(0,-1)">⬆</button>
<div></div>
<button onclick="move(-1,0)">⬅</button>
<button onclick="move(0,1)">⬇</button>
<button onclick="move(1,0)">➡</button>
</div>

<div id="win">
<h2>💖 Nehir...</h2>
<p>
Bu labirentte bana ulaştığın gibi,<br>
hayatın her yolunda elimi tutmanı istiyorum.<br><br>
Kalbim hep seninle atıyor ❤️<br>
Seni sonsuza kadar seveceğim.
</p>
</div>

<div id="hearts"></div>

<!-- ŞARKI BURAYA -->
<iframe id="music"
width="0"
height="0"
src=""
frameborder="0"
allow="autoplay"
allowfullscreen>
</iframe>

<script>
const videoID="qJNSoCCk8GU"; // BURAYA ŞARKININ YOUTUBE ID'sini yaz

const maze=[
[0,1,0,0,0,0,0,1,0,0],
[0,1,0,1,1,1,0,1,0,1],
[0,0,0,1,0,0,0,1,0,1],
[1,1,0,1,0,1,1,1,0,0],
[0,0,0,0,0,1,0,0,0,1],
[0,1,1,1,0,1,0,1,0,1],
[0,0,0,1,0,0,0,1,0,0],
[1,1,0,1,1,1,0,1,1,0],
[0,0,0,0,0,1,0,0,0,0],
[0,1,1,1,0,0,0,1,1,0]
];

let player={x:0,y:0};
const goal={x:9,y:9};
const game=document.getElementById("game");
let seconds=0;
let timerInterval;

function startGame(){
document.getElementById("startScreen").style.display="none";
timerInterval=setInterval(()=>{
seconds++;
document.getElementById("timer").innerText="Süre: "+seconds+" saniye";
},1000);
draw();
}

function draw(){
game.innerHTML="";
for(let y=0;y<10;y++){
for(let x=0;x<10;x++){
const cell=document.createElement("div");
cell.classList.add("cell");
if(maze[y][x]===1) cell.classList.add("wall");
if(player.x===x && player.y===y) cell.classList.add("player");
if(goal.x===x && goal.y===y) cell.classList.add("goal");
game.appendChild(cell);
}}}

function move(dx,dy){
const nx=player.x+dx;
const ny=player.y+dy;
if(nx>=0&&nx<10&&ny>=0&&ny<10&&maze[ny][nx]===0){
player.x=nx;
player.y=ny;
draw();
if(player.x===goal.x&&player.y===goal.y){
win();
}}
}

function win(){
clearInterval(timerInterval);
document.getElementById("win").style.display="block";

document.getElementById("music").src=
"https://www.youtube.com/embed/"+videoID+"?autoplay=1&loop=1&playlist="+videoID=qJNSoCCk8GU;

for(let i=0;i<40;i++){
const heart=document.createElement("div");
heart.classList.add("heart");
heart.innerHTML="❤️";
heart.style.left=Math.random()*100+"vw";
document.getElementById("hearts").appendChild(heart);
setTimeout(()=>heart.remove(),4000);
}
}

document.addEventListener("keydown",(e)=>{
if(e.key==="ArrowUp"||e.key==="w") move(0,-1);
if(e.key==="ArrowDown"||e.key==="s") move(0,1);
if(e.key==="ArrowLeft"||e.key==="a") move(-1,0);
if(e.key==="ArrowRight"||e.key==="d") move(1,0);
});
</script>

</body>
</html>
