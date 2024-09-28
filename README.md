# Internet-programming-II-Asignment-1
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Gideon's Calculator</title>
    <style>
        body {
            background-color: #0d47a1;
            color: #fff;
            font-family: 'Arial', sans-serif;
            margin: 0;
            padding: 0;
        }

        header {
            background-color: #1e88e5;
            padding: 20px;
            text-align: center;
            box-shadow: 0px 4px 15px rgba(0, 0, 0, 0.2);
        }

        header h1 {
            margin: 0;
            font-size: 2.5em;
        }

        .container {
            max-width: 800px;
            margin: 0 auto;
            padding: 20px;
            text-align: center;
        }

        .calculator {
            background-color: #1e88e5;
            border-radius: 15px;
            box-shadow: 0px 4px 15px rgba(0, 0, 0, 0.2);
            padding: 20px;
            width: 350px;
            margin: 30px auto;
        }

        .calculator input[type="text"] {
            background-color: #1565c0;
            border: none;
            border-radius: 10px;
            width: 100%;
            height: 60px;
            color: #fff;
            text-align: right;
            padding: 15px;
            font-size: 1.5em;
            margin-bottom: 20px;
            box-shadow: inset 0px 3px 5px rgba(0, 0, 0, 0.2);
        }

        .buttons {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            grid-gap: 10px;
        }

        button {
            background-color: #0d47a1;
            color: #fff;
            border: none;
            border-radius: 8px;
            height: 60px;
            font-size: 1.2em;
            box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.3);
            transition: background-color 0.3s ease;
            cursor: pointer;
        }

        button:hover {
            background-color: #0b3b91;
        }

        .special {
            background-color: #d32f2f;
        }

        .special:hover {
            background-color: #b71c1c;
        }

        .equals {
            background-color: #43a047;
        }

        .equals:hover {
            background-color: #388e3c;
        }

        footer {
            margin-top: 40px;
            padding: 10px;
            text-align: center;
            background-color: #0d47a1;
        }

        footer p {
            margin: 0;
            font-size: 0.9em;
        }
    </style>
</head>
<body>

    <header>
        <h1>Gideon's Calculator</h1>
    </header>

    <div class="container">
        <div class="calculator">
            <input type="text" id="display" placeholder="0">
            <div class="buttons">
                <button class="special" onclick="clearDisplay()">C</button>
                <button class="special" onclick="deleteLast()">DEL</button>
                <button onclick="inputValue('%')">%</button>
                <button onclick="inputValue('/')">/</button>

                <button onclick="inputValue('7')">7</button>
                <button onclick="inputValue('8')">8</button>
                <button onclick="inputValue('9')">9</button>
                <button onclick="inputValue('*')">*</button>

                <button onclick="inputValue('4')">4</button>
                <button onclick="inputValue('5')">5</button>
                <button onclick="inputValue('6')">6</button>
                <button onclick="inputValue('-')">-</button>

                <button onclick="inputValue('1')">1</button>
                <button onclick="inputValue('2')">2</button>
                <button onclick="inputValue('3')">3</button>
                <button onclick="inputValue('+')">+</button>

                <button onclick="inputValue('0')">0</button>
                <button onclick="inputValue('.')">.</button>
                <button class="special" onclick="calculateSquareRoot()">√</button>
                <button class="special" onclick="calculatePower()">x^y</button>
                <button class="special" onclick="calculateLog()">log</button>
                <button class="equals" onclick="calculate()">=</button>
            </div>
        </div>
    </div>

    <footer>
        <p>&copy; 2024 Gideon's Calculator. All Rights Reserved.</p>
    </footer>

    <script>
        let display = document.getElementById("display");

        function inputValue(value) {
            if (display.value === "0") {
                display.value = value;
            } else {
                display.value += value;
            }
        }

        function clearDisplay() {
            display.value = "0";
        }

        function deleteLast() {
            display.value = display.value.slice(0, -1);
            if (display.value === "") {
                display.value = "0";
            }
        }

        function calculateSquareRoot() {
            try {
                display.value = Math.sqrt(parseFloat(display.value));
            } catch (error) {
                display.value = "Error";
            }
        }

        function calculateLog() {
            try {
                display.value = Math.log10(parseFloat(display.value));
            } catch (error) {
                display.value = "Error";
            }
        }

        function calculatePower() {
            let base = prompt("Enter the base number:");
            let exponent = prompt("Enter the exponent:");
            try {
                display.value = Math.pow(parseFloat(base), parseFloat(exponent));
            } catch (error) {
                display.value = "Error";
            }
        }

        function calculate() {
            try {
                display.value = eval(display.value.replace('^', '**'));
            } catch (error) {
                display.value = "Error";
            }
        }
    </script>

</body>
</html>
