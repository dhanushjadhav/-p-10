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


