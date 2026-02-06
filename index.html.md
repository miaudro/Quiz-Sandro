<!DOCTYPE html>  
<html lang="de">  
<head>  
  <meta charset="UTF-8">  
  <title>Quiz über Sandro ❤️</title>  
  <style>  
    body {  
      font-family: Arial, sans-serif;  
      background: linear-gradient(135deg, #ff758c, #ff7eb3);  
      color: white;  
      display: flex;  
      justify-content: center;  
      align-items: center;  
      height: 100vh;  
      margin: 0;  
      text-align: center;  
      overflow: hidden;  
    }  
  
    .card {  
      background: rgba(255,255,255,0.15);  
      padding: 30px;  
      border-radius: 20px;  
      max-width: 420px;  
      box-shadow: 0 0 30px rgba(0,0,0,0.3);  
      backdrop-filter: blur(10px);  
    }  
  
    h1 {  
      margin-bottom: 10px;  
    }  
  
    .question {  
      font-size: 1.2em;  
      margin: 20px 0;  
    }  
  
    button {  
      padding: 12px 22px;  
      margin: 10px;  
      border: none;  
      border-radius: 30px;  
      font-size: 1em;  
      cursor: pointer;  
      transition: transform 0.15s;  
      position: relative;  
    }  
  
    button:hover {  
      transform: scale(1.05);  
    }  
  
    .yes {  
      background: #ff3366;  
      color: white;  
    }  
  
    .no {  
      background: #555;  
      color: white;  
      position: absolute;  
    }  
  
    .emoji {  
      font-size: 2em;  
      margin: 10px 0;  
    }  
  
    .result {  
      font-size: 1.3em;  
      margin-top: 20px;  
    }  
  </style>  
</head>  
<body>  
  
<div class="card" id="quiz">  
  <h1>💙 Quiz über Sandro 💙</h1>  
  <div class="emoji">🚗💘</div>  
  <div class="question" id="question"></div>  
  <div id="answers"></div>  
</div>  
  
<script>  
  const quizData = [  
    {  
      question: "BMW oder Mercedes? 😏",  
      answers: [  
        { text: "BMW ❤️", correct: true },  
        { text: "Mercedes", correct: false }  
      ]  
    },  
    {  
      question: "Ich habe einen BMW … 🚗",  
      answers: [  
        { text: "F36 😎", correct: true },  
        { text: "F32", correct: false }  
      ]  
    },  
    {  
      question: "Willst du mein Valentinstags-Date sein? 💕",  
      answers: [  
        { text: "JA 💘", correct: true },  
        { text: "Nein 😈", correct: false, runaway: true }  
      ]  
    }  
  ];  
  
  let current = 0;  
  const questionEl = document.getElementById("question");  
  const answersEl = document.getElementById("answers");  
  
  function loadQuestion() {  
    answersEl.innerHTML = "";  
    questionEl.textContent = quizData[current].question;  
  
    quizData[current].answers.forEach(answer => {  
      const btn = document.createElement("button");  
      btn.textContent = answer.text;  
  
      if (answer.runaway) {  
        btn.className = "no";  
        btn.onmouseover = moveButton;  
      } else {  
        btn.className = "yes";  
        btn.onclick = () => handleAnswer(answer.correct);  
      }  
  
      answersEl.appendChild(btn);  
    });  
  }  
  
  function moveButton(e) {  
    const btn = e.target;  
    const x = Math.random() * (window.innerWidth - 100);  
    const y = Math.random() * (window.innerHeight - 50);  
    btn.style.left = x + "px";  
    btn.style.top = y + "px";  
  }  
  
  function handleAnswer(correct) {  
    if (!correct) {  
      document.getElementById("quiz").innerHTML = `  
        <h1>😏 Uuups…</h1>  
        <div class="result">  
          Das war leider falsch 😌<br><br>  
          👉 1× free head 💋  
        </div>  
      `;  
      return;  
    }  
  
    current++;  
    if (current < quizData.length) {  
      loadQuestion();  
    } else {  
      document.getElementById("quiz").innerHTML = `  
        <h1>🎉 Gewonnen! 🎉</h1>  
        <div class="emoji">💖🥰💖</div>  
        <div class="result">  
          Alles richtig beantwortet!<br><br>  
          ❤️ Ich freu mich riesig auf unser Valentinstags-Date ❤️  
        </div>  
      `;  
    }  
  }  
  
  loadQuestion();  
</script>  
  
</body>  
</html>  
