# Conquer-calculator
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lot Size Calculator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
            text-align: center;
        }
        a {
            margin: 10px;
            text-decoration: none;
            color: #007BFF;
            font-size: 1.2rem;
            cursor: pointer;
        }
        a:hover {
            text-decoration: underline;
        }
        .calculator {
            display: none;
            margin-top: 20px;
        }
        .calculator.active {
            display: block;
        }
        input, button {
            margin: 10px 0;
            padding: 10px;
            font-size: 1rem;
        }
    </style>
</head>
<body>
    <h1>Lot Size Calculator</h1>
    <p>Click a link below to select the instrument for calculation:</p>
    <a onclick="showCalculator('nasdaq')">Nasdaq</a>
    <a onclick="showCalculator('sp500')">S&P 500</a>
    <a onclick="showCalculator('eurusd')">EUR/USD</a>
    <a onclick="showCalculator('gbpusd')">GBP/USD</a>

    <div id="nasdaq" class="calculator">
        <h2>Nasdaq Lot Size Calculator</h2>
        <form>
            <input type="number" id="nasdaqBalance" placeholder="Account Balance ($)" required><br>
            <input type="number" id="nasdaqRisk" placeholder="Risk Percentage (%)" required><br>
            <button type="button" onclick="calculateLotSize('nasdaq')">Calculate</button>
        </form>
        <p id="nasdaqResult"></p>
    </div>

    <div id="sp500" class="calculator">
        <h2>S&P 500 Lot Size Calculator</h2>
        <form>
            <input type="number" id="sp500Balance" placeholder="Account Balance ($)" required><br>
            <input type="number" id="sp500Risk" placeholder="Risk Percentage (%)" required><br>
            <button type="button" onclick="calculateLotSize('sp500')">Calculate</button>
        </form>
        <p id="sp500Result"></p>
    </div>

    <div id="eurusd" class="calculator">
        <h2>EUR/USD Lot Size Calculator</h2>
        <form>
            <input type="number" id="eurusdBalance" placeholder="Account Balance ($)" required><br>
            <input type="number" id="eurusdRisk" placeholder="Risk Percentage (%)" required><br>
            <button type="button" onclick="calculateLotSize('eurusd')">Calculate</button>
        </form>
        <p id="eurusdResult"></p>
    </div>

    <div id="gbpusd" class="calculator">
        <h2>GBP/USD Lot Size Calculator</h2>
        <form>
            <input type="number" id="gbpusdBalance" placeholder="Account Balance ($)" required><br>
            <input type="number" id="gbpusdRisk" placeholder="Risk Percentage (%)" required><br>
            <button type="button" onclick="calculateLotSize('gbpusd')">Calculate</button>
        </form>
        <p id="gbpusdResult"></p>
    </div>

    <script>
        function showCalculator(type) {
            const calculators = document.querySelectorAll('.calculator');
            calculators.forEach(calculator => calculator.classList.remove('active'));
            document.getElementById(type).classList.add('active');
        }

        function calculateLotSize(type) {
            const balance = parseFloat(document.getElementById(`${type}Balance`).value);
            const risk = parseFloat(document.getElementById(`${type}Risk`).value);
            if (isNaN(balance) || isNaN(risk) || balance <= 0 || risk <= 0) {
                document.getElementById(`${type}Result`).innerText = "Please enter valid positive numbers.";
                return;
            }
            const lotSize = (balance * (risk / 100)).toFixed(2);
            document.getElementById(`${type}Result`).innerText = `Your lot size for ${type.toUpperCase()} is $${lotSize}`;
        }
    </script>
</body>
</html>
