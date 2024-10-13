<!DOCTYPE html>
<html lang="sv">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>OKörkortsteori - Körkortsquiz</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="container">
        <h1>Välkommen till OKörkortsteori</h1>
        <p>Testa dina kunskaper med vårt omfattande quiz om körkortsteori.</p>
        <button onclick="location.href='quiz.html'">Starta Quiz</button>
    </div>
</body>
</html>
<!DOCTYPE html>
<html lang="sv">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Körkortsquiz</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="container">
        <h1>Körkortsquiz</h1>
        <form id="quizForm">
            <div id="questionContainer"></div>
            <button type="button" onclick="submitQuiz()">Skicka in svar</button>
        </form>
    </div>

    <script src="quiz.js"></script>
</body>
</html>
body {
    font-family: Arial, sans-serif;
    background-color: #f4f4f4;
    margin: 0;
    padding: 20px;
}

.container {
    max-width: 800px;
    margin: 0 auto;
    background: white;
    padding: 20px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

h1 {
    text-align: center;
}

form {
    margin-top: 20px;
}

button {
    background-color: #4CAF50;
    color: white;
    padding: 10px 20px;
    border: none;
    cursor: pointer;
    margin-top: 20px;
}

button:hover {
    background-color: #45a049;
}
const questions = [
    {
        question: "1. Vad betyder en gul heldragen linje vid vägkanten?",
        options: {
            A: "Förbud att stanna eller parkera",
            B: "Förbud att parkera, men tillåtet att stanna kort",
            C: "Förbud att stanna, men tillåtet att parkera",
            D: "Inget av ovanstående"
        },
        correct: "B"
    },
    {
        question: "2. Vilken hastighet gäller på en huvudled om ingen skylt finns?",
        options: {
            A: "30 km/h",
            B: "50 km/h",
            C: "70 km/h",
            D: "90 km/h"
        },
        correct: "B"
    },
    // Lägg till alla 100 frågor här
    // Exempel på sista fråga:
    {
        question: "100. Vad är den högsta tillåtna promillegränsen för rattfylleri i Sverige?",
        options: {
            A: "0.2 promille",
            B: "0.5 promille",
            C: "1.0 promille",
            D: "2.0 promille"
        },
        correct: "A"
    }
];

function loadQuestions() {
    const questionContainer = document.getElementById('questionContainer');
    questions.forEach((q, index) => {
        const questionDiv = document.createElement('div');
        questionDiv.className = 'question';

        // Fråga
        const questionTitle = document.createElement('h3');
        questionTitle.textContent = q.question;
        questionDiv.appendChild(questionTitle);

        // Alternativ
        Object.keys(q.options).forEach(option => {
            const label = document.createElement('label');
            label.innerHTML = `<input type="radio" name="question${index}" value="${option}"> ${option}) ${q.options[option]}`;
            questionDiv.appendChild(label);
            questionDiv.appendChild(document.createElement('br'));
        });

        questionContainer.appendChild(questionDiv);
    });
}

function submitQuiz() {
    let score = 0;
    questions.forEach((q, index) => {
        const userAnswer = document.querySelector(`input[name="question${index}"]:checked`);
        if (userAnswer && userAnswer.value === q.correct) {
            score++;
        }
    });
    alert(`Du fick ${score} av ${questions.length} rätt!`);
}

window.onload = loadQuestions;
