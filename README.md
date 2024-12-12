<!DOCTYPE html>
<html>
  <head>
    <title>Talha - Quiz Game</title>
    <link rel="stylesheet" href="style.css" />
    <link rel="icon" href="https://i.ibb.co/M6KTWnf/pic.jpg" />
</head>
  <body>
    <div class="container">
      <h1 style="margin-bottom: 2px;">Quiz App</h1>
      <h4 style="margin-top: 0px;">20 Questions</h4>
      <div id="quiz"></div>
      <div id="result" class="result"></div>
      <button id="submit" class="button">Submit</button>
      <button id="retry" class="button hide">Retry</button>
      <button id="showAnswer" class="button hide">Show Answer</button>
    </div>
    <script src="script.js"></script>
  </body>
</html>

body {
  font-family: "Poppins", sans-serif;
  background: #b9b3a9;
  display: flex;
  justify-content: center;
}

.container {
  width: 450px;
  padding: 20px;
  margin-top: 80px;
  background-color: #fff;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  border-radius: 20px;
}

h1 {
  text-align: center;
}
h4 {
  text-align: center;
}

.question {
  font-weight: bold;
  margin-bottom: 10px;
}

.options {
  margin-bottom: 20px;
}

.option {
  display: block;
  margin-bottom: 10px;
}

.button {
  display: inline-block;
  padding: 10px 20px;
  background-color: #428bca;
  color: #fff;
  border: none;
  cursor: pointer;
  font-size: 16px;
  border-radius: 4px;
  transition: background-color 0.3s;
  margin-right: 10px;
}

.button:hover {
  background-color: #3071a9;
}

.result {
  text-align: center;
  margin-top: 20px;
  font-weight: bold;
}

.hide {
  display: none;
}


quizContainer.appendChild(questionElement);
  quizContainer.appendChild(optionsElement);
}

function checkAnswer() {
  const selectedOption = document.querySelector('input[name="quiz"]:checked');
  if (selectedOption) {
    const answer = selectedOption.value;
    if (answer === quizData[currentQuestion].answer) {
      score++;
    } else {
      incorrectAnswers.push({
        question: quizData[currentQuestion].question,
        incorrectAnswer: answer,
        correctAnswer: quizData[currentQuestion].answer,
      });
    }
    currentQuestion++;
    selectedOption.checked = false;
    if (currentQuestion < quizData.length) {
      displayQuestion();
    } else {
      displayResult();
    }
  }
}

function displayResult() {
  quizContainer.style.display = "none";
  submitButton.style.display = "none";
  retryButton.style.display = "inline-block";
  showAnswerButton.style.display = "inline-block";
  resultContainer.innerHTML = You scored ${score} out of ${quizData.length}!;
}

function retryQuiz() {
  currentQuestion = 0;
  score = 0;
  incorrectAnswers = [];
  quizContainer.style.display = "block";
  submitButton.style.display = "inline-block";
  retryButton.style.display = "none";
  showAnswerButton.style.display = "none";
  resultContainer.innerHTML = "";
  displayQuestion();
}

function showAnswer() {
  quizContainer.style.display = "none";
  submitButton.style.display = "none";
  retryButton.style.display = "inline-block";
  showAnswerButton.style.display = "none";

  let incorrectAnswersHtml = "";
  for (let i = 0; i < incorrectAnswers.length; i++) {
    incorrectAnswersHtml += `
        <p>
          <strong>Question:</strong> ${incorrectAnswers[i].question}<br>
          <strong>Your Answer:</strong> ${incorrectAnswers[i].incorrectAnswer}<br>
          <strong>Correct Answer:</strong> ${incorrectAnswers[i].correctAnswer}
        </p>
      `;
  }

  resultContainer.innerHTML = `
      <p>You scored ${score} out of ${quizData.length}!</p>
      <p>Incorrect Answers:</p>
      ${incorrectAnswersHtml}
    `;
}

submitButton.addEventListener("click", checkAnswer);
retryButton.addEventListener("click", retryQuiz);
showAnswerButton.addEventListener("click", showAnswer);

displayQuestion();
