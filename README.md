from IPython.display import HTML

HTML("""
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>For You ❤️</title>

<style>
*{
    margin:0;
    padding:0;
    box-sizing:border-box;
    font-family:'Segoe UI',sans-serif;
}

body{
    height:100vh;
    background:linear-gradient(135deg,#ffeef3,#ffd9e2);
    display:flex;
    align-items:center;
    justify-content:center;
    overflow:hidden;
}

.card{
    background:white;
    padding:26px;
    width:90%;
    max-width:360px;
    border-radius:24px;
    text-align:center;
    box-shadow:0 20px 50px rgba(0,0,0,0.15);
    animation:pop 0.8s ease;
    position:relative;
    z-index:5;
}

.sticker img{
    width:130px;
    margin-bottom:8px;
}

h1{
    color:#e75480;
    margin-bottom:10px;
}

p{
    color:#555;
    font-size:15px;
    margin-bottom:18px;
    line-height:1.6;
}

.buttons{
    display:flex;
    justify-content:space-around;
    gap:10px;
}

button{
    padding:10px 22px;
    border:none;
    border-radius:20px;
    font-size:15px;
    cursor:pointer;
}

.yes{
    background:#e75480;
    color:white;
}

.no{
    background:#ddd;
}

.heart{
    position:absolute;
    bottom:-30px;
    font-size:20px;
    animation:float 7s linear infinite;
}

@keyframes float{
    to{
        transform:translateY(-120vh) scale(1.5);
        opacity:0;
    }
}

@keyframes pop{
    from{transform:scale(0.6);opacity:0}
    to{transform:scale(1);opacity:1}
}

.confetti{
    position:fixed;
    width:8px;
    height:8px;
    animation:confetti 3s linear infinite;
}

@keyframes confetti{
    to{transform:translateY(120vh) rotate(720deg);}
}
</style>
</head>

<body>

<audio id="music" loop>
  <source src="https://cdn.pixabay.com/audio/2022/03/15/audio_5a0c6c7f1d.mp3" type="audio/mpeg">
</audio>

<div class="card" id="card">
    <div class="sticker">
        <!-- cute shy cartoon couple -->
        <img src="https://media.giphy.com/media/3oz8xKaR836UJOYeOc/giphy.gif">
    </div>
    <h1>Do you love me? 💖</h1>
    <p>Be honest… there is only one right answer 😌</p>

    <div class="buttons">
        <button class="yes" onclick="firstYes()">YES 💕</button>
        <button class="no" onmouseover="moveNo(this)">NO 🙃</button>
    </div>
</div>

<script>
function playMusic(){
    document.getElementById("music").play();
}

function firstYes(){
    playMusic();
    document.getElementById("card").innerHTML = `
        <div class="sticker">
            <!-- cute kiss cartoon -->
            <img src="https://media.giphy.com/media/MDJ9IbxxvDUQM/giphy.gif">
        </div>
        <h1>I know you love me 😛❤️</h1>
        <p>But are you reallyyyy sure you love me? 🤨💖</p>

        <div class="buttons">
            <button class="yes" onclick="finalYes()">YES 💕</button>
            <button class="no" onclick="sureNo()">NO 🙃</button>
        </div>
    `;
}

function finalYes(){
    launchConfetti();
    document.getElementById("card").innerHTML = `
        <div class="sticker">
            <!-- super cute hugging couple -->
            <img src="https://media.giphy.com/media/l0HlBO7eyXzSZkJri/giphy.gif">
        </div>
        <h1>I LOVE YOU SO MUCH ❤️</h1>
        <p id="typing"></p>
    `;
    typeText();
}

function typeText(){
    const text =
`

Venky, I love you so much ❤️
You are my Love, always.

Life feels right with you,
and I don’t want a future
that doesn’t have you in it 💕

I’m marrying you 😌💍
No arguments allowed 😈;
    let i = 0;
    const target = document.getElementById("typing");
    const timer = setInterval(()=>{
        target.innerHTML = text.substring(0,i).replace(/\\n/g,"<br>");
        i++;
        if(i > text.length) clearInterval(timer);
    },45);
}

function sureNo(){
    document.getElementById("card").innerHTML = `
        <div class="sticker">
            <!-- cute teasing cartoon -->
            <img src="https://media.giphy.com/media/JIX9t2j0ZTN9S/giphy.gif">
        </div>
        <h1>Nice try 😏,
I already know you love me 😛
But tell me… are you REALLY sure? 🤨💖</h1>
        <p>Your heart says YES,I hope you’re ready…
because I’m not letting you go 😈💖💖</p>

        <div class="buttons">
            <button class="yes" onclick="firstYes()">OK FINE 😌</button>
            <button class="no" onclick="location.reload()">GO BACK 🔄</button>
        </div>
    `;
}

function moveNo(btn){
    btn.style.position="relative";
    btn.style.left=(Math.random()*80-40)+"px";
    btn.style.top=(Math.random()*40-20)+"px";
}

setInterval(()=>{
    const h=document.createElement("div");
    h.className="heart";
    h.innerHTML="❤️";
    h.style.left=Math.random()*100+"vw";
    document.body.appendChild(h);
    setTimeout(()=>h.remove(),7000);
},500);

function launchConfetti(){
    for(let i=0;i<120;i++){
        const c=document.createElement("div");
        c.className="confetti";
        c.style.left=Math.random()*100+"vw";
        c.style.backgroundColor=["#ff4d6d","#ffb3c6","#ff758f"][Math.floor(Math.random()*3)];
        c.style.animationDuration=(Math.random()*2+2)+"s";
        document.body.appendChild(c);
        setTimeout(()=>c.remove(),3000);
    }
}
</script>

</body>
</html>
""")
