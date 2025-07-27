index.html:

<html>
<head>
  <title>Stylish Calculator</title>
  <link rel="stylesheet" href="style.css" />
</head>
<body>
  <div class="container">
    <div class="calculator">
      <input type="text" id="display" readonly />
      <div class="buttons">
        <button onclick="clearDisplay()">C</button>
        <button onclick="deleteLast()">DEL</button>
        <button onclick="append('%')">%</button>
        <button onclick="append('/')">/</button>
        <button onclick="append('7')">7</button>
        <button onclick="append('8')">8</button>
        <button onclick="append('9')">9</button>
        <button onclick="append('*')">*</button>
        <button onclick="append('4')">4</button>
        <button onclick="append('5')">5</button>
        <button onclick="append('6')">6</button>
        <button onclick="append('-')">-</button>
        <button onclick="append('1')">1</button>
        <button onclick="append('2')">2</button>
        <button onclick="append('3')">3</button>
        <button onclick="append('+')">+</button>
        <button onclick="append('0')">0</button>
        <button onclick="append('.')">.</button>
        <button onclick="calculate()" style="grid-column: span 2;">=</button>
      </div>
    </div>
  </div>
  <script src="script.js"></script>
</body>
</html>


style.css:

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'Poppins', sans-serif;
  background: linear-gradient(135deg, #1f1c2c, #928dab);
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

.container {
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(15px);
  border-radius: 20px;
  box-shadow: 0 8px 30px rgba(0, 0, 0, 0.4);
  padding: 30px;
  width: 320px;
}

.calculator {
  display: flex;
  flex-direction: column;
}

#display {
  height: 60px;
  width: 100%;
  border-radius: 10px;
  border: none;
  outline: none;
  text-align: right;
  padding: 10px 20px;
  font-size: 1.8rem;
  color: #fff;
  background: rgba(255, 255, 255, 0.05);
  box-shadow: inset 0 0 5px rgba(255, 255, 255, 0.1);
}

.buttons {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 15px;
  margin-top: 20px;
}

button {
  padding: 20px;
  font-size: 1.2rem;
  font-weight: bold;
  border: none;
  border-radius: 12px;
  background: rgba(255, 255, 255, 0.15);
  color: #fff;
  cursor: pointer;
  transition: 0.2s ease;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.25);
}

button:hover {
  background: rgba(255, 255, 255, 0.25);
  transform: scale(1.05);
}

button:active {
  box-shadow: 0 0 10px #00ffd5, 0 0 20px #00ffd5;
  background: #00ffd5;
  color: #000;
}

script.js:

function append(value) {
  document.getElementById("display").value += value;
}

function clearDisplay() {
  document.getElementById("display").value = "";
}

function deleteLast() {
  const display = document.getElementById("display");
  display.value = display.value.slice(0, -1);
}

function calculate() {
  try {
    const result = eval(document.getElementById("display").value);
    document.getElementById("display").value = result;
  } catch (error) {
    alert("Invalid Expression");
  }
}
