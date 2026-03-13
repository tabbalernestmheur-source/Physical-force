<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>🔬 Physics: Work, Kinetic & Potential Energy</title>

<style>

*{
margin:0;
padding:0;
box-sizing:border-box;
}

body{
font-family:'Segoe UI',Tahoma,Geneva,Verdana,sans-serif;
background:linear-gradient(135deg,#667eea 0%,#764ba2 100%);
min-height:100vh;
color:#333;
padding-top:120px;
}

/* TELEPORT NAV */

.teleport-nav{
position:fixed;
top:20px;
left:50%;
transform:translateX(-50%);
background:white;
padding:15px;
border-radius:30px;
box-shadow:0 10px 30px rgba(0,0,0,0.3);
display:flex;
gap:10px;
z-index:1000;
}

.teleport-btn{
background:linear-gradient(45deg,#ff6b6b,#4ecdc4);
border:none;
color:white;
padding:10px 20px;
border-radius:20px;
cursor:pointer;
font-weight:bold;
transition:.3s;
}

.teleport-btn:hover{
transform:scale(1.1);
}

/* CONTENT */

.container{
max-width:1000px;
margin:auto;
padding:20px;
}

h1{
text-align:center;
color:white;
font-size:3em;
margin-bottom:30px;
}

.content-section{
display:none;
background:white;
border-radius:20px;
padding:35px;
margin-bottom:30px;
box-shadow:0 15px 40px rgba(0,0,0,0.3);
}

.content-section.active{
display:block;
}

.section-title{
text-align:center;
font-size:2em;
margin-bottom:20px;
}

/* FORMULA */

.formula{
background:linear-gradient(45deg,#ff6b6b,#4ecdc4);
color:white;
padding:25px;
border-radius:15px;
font-size:1.8em;
text-align:center;
margin:20px 0;
}

/* QUIZ */

.quiz-container{
background:#f4f8ff;
padding:25px;
border-radius:15px;
}

.question{
background:white;
padding:20px;
margin:20px 0;
border-radius:12px;
border-left:6px solid #007bff;
}

/* OPTIONS FIX */

.option{
display:flex;
align-items:center;
padding:14px;
margin:10px 0;
background:#f8f9fa;
border-radius:10px;
border:2px solid transparent;
cursor:pointer;
transition:.25s;
}

.option input{
display:none;
}

.option-label{
width:100%;
cursor:pointer;
}

.option:hover{
background:#e3f2fd;
border-color:#007bff;
}

.option input:checked + .option-label{
background:linear-gradient(45deg,#007bff,#0056b3);
color:white;
padding:8px;
border-radius:6px;
}

/* PROGRESS BAR */

.progress{
background:#ddd;
height:14px;
border-radius:10px;
overflow:hidden;
margin:20px 0;
}

.progress-bar{
height:100%;
width:0%;
background:linear-gradient(90deg,#007bff,#00c6ff);
transition:.4s;
}

/* BUTTON */

.submit-btn{
background:#28a745;
color:white;
border:none;
padding:12px 25px;
border-radius:20px;
cursor:pointer;
font-size:16px;
margin-top:20px;
}

.score-display{
font-size:2em;
text-align:center;
margin-top:20px;
color:#28a745;
font-weight:bold;
}

</style>
</head>

<body>

<!-- TELEPORT NAV -->

<div class="teleport-nav">
<button class="teleport-btn" onclick="showSection('work')">Work</button>
<button class="teleport-btn" onclick="showSection('ke')">Kinetic Energy</button>
<button class="teleport-btn" onclick="showSection('pe')">Potential Energy</button>
<button class="teleport-btn" onclick="showSection('quiz')">Quiz</button>
</div>

<div class="container">

<h1>🔬 Physics: Work, Kinetic & Potential Energy</h1>

<!-- WORK -->

<div id="work" class="content-section active">

<h2 class="section-title">Work</h2>

<p>Work is done when a force moves an object over a distance.</p>

<div class="formula">
W = F × d
</div>

</div>

<!-- KE -->

<div id="ke" class="content-section">

<h2 class="section-title">Kinetic Energy</h2>

<p>Kinetic energy is the energy of motion.</p>

<div class="formula">
KE = ½mv²
</div>

</div>

<!-- PE -->

<div id="pe" class="content-section">

<h2 class="section-title">Potential Energy</h2>

<p>Potential energy is stored energy due to position.</p>

<div class="formula">
PE = mgh
</div>

</div>

<!-- QUIZ -->

<div id="quiz" class="content-section">

<h2 class="section-title">Physics Quiz</h2>

<div class="quiz-container">

<div class="progress">
<div class="progress-bar" id="progressBar"></div>
</div>

<form id="quizForm">

<div class="question">

<p><strong>1. What is the formula for Kinetic Energy?</strong></p>

<div class="option">
<input type="radio" name="q1" value="0">
<label class="option-label">A. KE = mv</label>
</div>

<div class="option">
<input type="radio" name="q1" value="1">
<label class="option-label">B. KE = ½mv²</label>
</div>

<div class="option">
<input type="radio" name="q1" value="0">
<label class="option-label">C. KE = mgh</label>
</div>

</div>

<div class="question">

<p><strong>2. Potential energy depends on:</strong></p>

<div class="option">
<input type="radio" name="q2" value="1">
<label class="option-label">A. Height</label>
</div>

<div class="option">
<input type="radio" name="q2" value="0">
<label class="option-label">B. Speed</label>
</div>

</div>

<button type="button" class="submit-btn" onclick="submitQuiz()">
Submit Quiz
</button>

</form>

<div class="score-display" id="scoreDisplay"></div>

</div>

</div>

</div>

<script>

/* TELEPORT NAV */

function showSection(id){

document.querySelectorAll(".content-section").forEach(section=>{
section.classList.remove("active")
})

document.getElementById(id).classList.add("active")

}

/* QUIZ SCORE */

function submitQuiz(){

let score=0

document.querySelectorAll("#quizForm input:checked").forEach(ans=>{
score+=parseInt(ans.value)
})

let total=2

document.getElementById("scoreDisplay").innerHTML=
"Your Score: "+score+" / "+total

document.getElementById("progressBar").style.width=
(score/total*100)+"%"

}

</script>

</body>
</html>
