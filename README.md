<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Dark Calculator</title>

<style>
body {
    margin: 0;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    background: #0f172a;
    font-family: Arial, Helvetica, sans-serif;
}

.calculator {
    background: #1e293b;
    padding: 25px;
    border-radius: 20px;
    box-shadow: 0 0 40px rgba(0,0,0,0.6);
    width: 320px;
}

.display {
    width: 100%;
    height: 70px;
    background: #0f172a;
    border: none;
    border-radius: 12px;
    margin-bottom: 20px;
    text-align: right;
    font-size: 28px;
    padding: 10px;
    color: white;
}

.buttons {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 12px;
}

button {
    height: 60px;
    border: none;
    border-radius: 12px;
    font-size: 20px;
    cursor: pointer;
    background: #334155;
    color: white;
    transition: 0.2s;
}

button:hover {
    background: #475569;
}

.operator {
    background: #2563eb;
}

.operator:hover {
    background: #1d4ed8;
}

.equal {
    background: #16a34a;
    grid-column: span 2;
}

.equal:hover {
    background: #15803d;
}

.clear {
    background: #dc2626;
}

.clear:hover {
    background: #b91c1c;
}
</style>
</head>

<body>

<div class="calculator">
    <input type="text" class="display" id="display" disabled>

    <div class="buttons">
        <button class="clear" onclick="clearDisplay()">C</button>
        <button class="operator" onclick="appendValue('/')">÷</button>
        <button class="operator" onclick="appendValue('*')">×</button>
        <button class="operator" onclick="appendValue('-')">−</button>

        <button onclick="appendValue('7')">7</button>
        <button onclick="appendValue('8')">8</button>
        <button onclick="appendValue('9')">9</button>
        <button class="operator" onclick="appendValue('+')">+</button>

        <button onclick="appendValue('4')">4</button>
        <button onclick="appendValue('5')">5</button>
        <button onclick="appendValue('6')">6</button>
        <button onclick="appendValue('.')">.</button>

        <button onclick="appendValue('1')">1</button>
        <button onclick="appendValue('2')">2</button>
        <button onclick="appendValue('3')">3</button>
        <button class="equal" onclick="calculate()">=</button>

        <button onclick="appendValue('0')" style="grid-column: span 2;">0</button>
    </div>
</div>

<script>
let display = document.getElementById("display");

// suara tombol
function playSound() {
    let audio = new Audio("https://www.soundjay.com/buttons/sounds/button-16.mp3");
    audio.play();
}

function appendValue(value) {
    playSound();
    display.value += value;
}

function clearDisplay() {
    playSound();
    display.value = "";
}

function calculate() {
    playSound();
    try {
        display.value = eval(display.value);
    } catch {
        display.value = "Error";
    }
}
</script>

</body>
</html>
