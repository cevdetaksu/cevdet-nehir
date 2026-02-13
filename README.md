<!DOCTYPE html>
<html lang="tr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>CEVDET ❤️ NEHİR</title>

<style>
body{
margin:0;
text-align:center;
background:linear-gradient(135deg,#ff4b7d,#ff758c);
font-family:Arial, sans-serif;
color:white;
}

h1{margin-top:20px;}

#game{
display:grid;
grid-template-columns:repeat(10,35px);
grid-template-rows:repeat(10,35px);
gap:4px;
justify-content:center;
margin-top:20px;
}

.cell{width:35px;height:35px;border-radius:6px;}
.wall{background:white;}
.player{background:#ff003c;}
.goal{background:gold;}

button{
padding:10px 20px;
border:none;
border-radius:20px;
background:white;
color:#ff4b7d;
margin-top:15px;
font-size:16px;
}

#win{
display:none;
position:fixed;
top:50%;
left:50%;
transform:translate(-50%,-50%);
background:white;
color:#ff4b7d;
padding:30px;
border-radius:20px;
}

.controls{
margin-top:15px;
}

.controls button{
margin:5px;
}
</style>
</head>

<body>

<h1>CEVDET ❤️ NEHİR</h1>
<p>Nehir kalbini Cevdet’e ulaştır 💕</p>

<div id="game"></div>

<div class="controls">
<br>
<button onclick="move(0,-1)">⬆</button><br>
<button onclick="move(-1,0)">⬅</button>
<button onclick="move(0,1)">⬇</button>
<button onclick="move(1,0)">➡</button>
</div>

<div id="win">
<h2>💖 Nehir...</h2>
<p>
Kalbim seninle atıyor... pat pat 🤍<br><br>
Hayatımın her yolunda seninle yürümek istiyorum.<br>
Seni sonsuza kadar seveceğim.
</p>
</div>

<script>
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
}}
}

function move(dx,dy){
const nx=player.x+dx;
const ny=player.y+dy;
if(nx>=0&&nx<10&&ny>=0&&ny<10&&maze[ny][nx]===0){
player.x=nx;
player.y=ny;
draw();
if(player.x===goal.x&&player.y===goal.y){
document.getElementById("win").style.display="block";
}
}
}

document.addEventListener("keydown",(e)=>{
if(e.key==="ArrowUp") move(0,-1);
if(e.key==="ArrowDown") move(0,1);
if(e.key==="ArrowLeft") move(-1,0);
if(e.key==="ArrowRight") move(1,0);
});

draw();
</script>

</body>
</html>
