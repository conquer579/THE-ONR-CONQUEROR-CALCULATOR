# <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>THE CONQUEROR CALCULATOR</title>
    <style>
        /* General Styles */
        body {
            font-family: 'Arial', sans-serif;
            background: #1e1e2f;
            color: #ffffff;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: flex-start;
            min-height: 100vh;
            overflow-y: auto;
            position: relative;
        }

        /* Trading Chart Background */
        .chart-background {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: url('https://www.tradingview.com/x/zZ7Jv8yO/') no-repeat center center/cover;
            opacity: 0.3;
            z-index: -1;
            animation: chartMotion 20s linear infinite;
        }

        @keyframes chartMotion {
            0% { background-position: 0 0; }
            100% { background-position: 100% 100%; }
        }

        .calculator {
            background: rgba(42, 42, 64, 0.9);
            padding: 25px;
            border-radius: 15px;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.3);
            width: 100%;
            max-width: 800px;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.1);
            animation: fadeIn 1s ease-in-out;
            z-index: 1;
            margin: 20px;
        }

        h1 {
            color: #bb86fc;
            text-align: center;
            margin-bottom: 25px;
            font-size: 2.2rem;
            font-weight: bold;
            text-shadow: 0 4px 10px rgba(187, 134, 252, 0.3);
            animation: slideDown 1s ease-in-out;
        }

        /* Tabs */
        .tabs {
            display: flex;
            justify-content: center;
            margin-bottom: 20px;
        }

        .tab {
            padding: 10px 20px;
            background: rgba(51, 51, 51, 0.8);
            border: 1px solid rgba(187, 134, 252, 0.3);
            border-radius: 8px;
            cursor: pointer;
            margin: 0 10px;
            transition: all 0.3s ease;
        }

        .tab.active {
            background: linear-gradient(135deg, #bb86fc, #9a67ea);
            color: #1e1e2f;
            border-color: #bb86fc;
        }

        .tab:hover {
            background: linear-gradient(135deg, #9a67ea, #bb86fc);
            color: #1e1e2f;
        }

        /* Sections */
        .section {
            display: none;
            margin-bottom: 30px;
            animation: slideUp 1s ease-in-out;
            padding: 20px;
            background: rgba(42, 42, 64, 0.8);
            border-radius: 10px;
            border: 1px solid rgba(187, 134, 252, 0.2);
        }

        .section.active {
            display: block;
        }

        label {
            display: block;
            margin: 12px 0 6px;
            color: #bb86fc;
            font-size: 0.95rem;
            animation: fadeIn 1.5s ease-in-out;
        }

        input, select {
            width: 100%;
            padding: 10px;
            margin-bottom: 15px;
            border: 1px solid rgba(187, 134, 252, 0.3);
            border-radius: 8px;
            background: rgba(51, 51, 51, 0.8);
            color: #ffffff;
            font-size: 0.95rem;
            transition: all 0.3s ease;
        }

        input:focus, select:focus {
            border-color: #bb86fc;
            box-shadow: 0 0 8px rgba(187, 134, 252, 0.5);
            background: rgba(51, 51, 51, 1);
        }

        button {
            width: 100%;
            padding: 10px;
            background: linear-gradient(135deg, #bb86fc, #9a67ea);
            color: #1e1e2f;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-size: 1rem;
            font-weight: bold;
            transition: all 0.3s ease;
            animation: fadeIn 2s ease-in-out;
        }

        button:hover {
            background: linear-gradient(135deg, #9a67ea, #bb86fc);
            transform: translateY(-2px);
            box-shadow: 0 4px 15px rgba(187, 134, 252, 0.4);
        }

        .result {
            margin-top: 20px;
            padding: 15px;
            background: rgba(51, 51, 51, 0.8);
            border-radius: 10px;
            color: #ffffff;
            animation: fadeIn 2.5s ease-in-out;
        }

        .result p {
            margin: 8px 0;
            font-size: 0.95rem;
        }

        .result span {
            color: #bb86fc;
            font-weight: bold;
        }

        /* Animations */
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        @keyframes slideDown {
            from { transform: translateY(-50px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }

        @keyframes slideLeft {
            from { transform: translateX(-50px); opacity: 0; }
            to { transform: translateX(0); opacity: 1; }
        }

        @keyframes slideUp {
            from { transform: translateY(50px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }
    </style>
</head>
<body>

<!-- Trading Chart Background -->
<div class="chart-background"></div>

<div class="calculator">
    <h1>THE CONQUEROR CALCULATOR</h1>

    <!-- Tabs -->
    <div class="tabs">
        <div class="tab active" onclick="switchTab('forex')">Forex</div>
        <div class="tab" onclick="switchTab('indices')">Indices</div>
    </div>

    <!-- Forex Section -->
    <div class="section active" id="forexSection">
        <h2>Forex Calculator</h2>
        <label for="forexAccountBalance">Account Balance ($):</label>
        <input type="number" id="forexAccountBalance" placeholder="Enter account balance">

        <label for="forexRiskPercentage">Risk Percentage (%):</label>
        <input type="number" id="forexRiskPercentage" placeholder="Enter risk percentage">

        <label for="forexStopLoss">Stop Loss (Pips):</label>
        <input type="number" id="forexStopLoss" placeholder="Enter stop loss in pips">

        <label for="forexTakeProfit">Take Profit (Pips):</label>
        <input type="number" id="forexTakeProfit" placeholder="Enter take profit in pips">

        <label for="forexInstrument">Currency Pair:</label>
        <select id="forexInstrument">
            <option value="EURUSD">EUR/USD</option>
            <option value="GBPUSD">GBP/USD</option>
        </select>

        <button onclick="calculateForex()">Calculate Forex</button>

        <div class="result" id="forexResult">
            <p>Amount Risked: <span id="forexAmountRisked">-</span></p>
            <p>Amount Gained: <span id="forexAmountGained">-</span></p>
            <p>Lot Size: <span id="forexLotSize">-</span></p>
            <p>Risk-to-Reward Ratio: <span id="forexRrRatio">-</span></p>
            <p>Lot Size ÷ 4: <span id="forexLotSizeDivided">-</span></p>
        </div>
    </div>

    <!-- Indices Section -->
    <div class="section" id="indicesSection">
        <h2>Indices Calculator</h2>
        <label for="indicesAccountBalance">Account Balance ($):</label>
        <input type="number" id="indicesAccountBalance" placeholder="Enter account balance">

        <label for="indicesRiskPercentage">Risk Percentage (%):</label>
        <input type="number" id="indicesRiskPercentage" placeholder="Enter risk percentage">

        <label for="indicesStopLoss">Stop Loss (Points):</label>
        <input type="number" id="indicesStopLoss" placeholder="Enter stop loss in points">

        <label for="indicesTakeProfit">Take Profit (Points):</label>
        <input type="number" id="indicesTakeProfit" placeholder="Enter take profit in points">

        <label for="indicesInstrument">Index:</label>
        <select id="indicesInstrument">
            <option value="NAS100">NAS100</option>
            <option value="S&P500">S&P500</option>
        </select>

        <button onclick="calculateIndices()">Calculate Indices</button>

        <div class="result" id="indicesResult">
            <p>Amount Risked: <span id="indicesAmountRisked">-</span></p>
            <p>Amount Gained: <span id="indicesAmountGained">-</span></p>
            <p>Lot Size: <span id="indicesLotSize">-</span></p>
            <p>Risk-to-Reward Ratio: <span id="indicesRrRatio">-</span></p>
            <p>Lot Size ÷ 4: <span id="indicesLotSizeDivided">-</span></p>
        </div>
    </div>
</div>

<script>
    // Switch Tabs
    function switchTab(tabName) {
        document.querySelectorAll('.section').forEach(section => {
            section.classList.remove('active');
        });
        document.querySelectorAll('.tab').forEach(tab => {
            tab.classList.remove('active');
        });

        document.getElementById(`${tabName}Section`).classList.add('active');
        document.querySelector(`.tab[onclick="switchTab('${tabName}')"]`).classList.add('active');
    }

    // Forex Calculation
    function calculateForex() {
        const accountBalance = parseFloat(document.getElementById('forexAccountBalance').value);
        const riskPercentage = parseFloat(document.getElementById('forexRiskPercentage').value);
        const stopLoss = parseFloat(document.getElementById('forexStopLoss').value);
        const takeProfit = parseFloat(document.getElementById('forexTakeProfit').value);
        const instrument = document.getElementById('forexInstrument').value;

        if (isNaN(accountBalance) || isNaN(riskPercentage) || isNaN(stopLoss) || isNaN(takeProfit)) {
            alert("Please fill in all fields with valid numbers.");
            return;
        }

        const amountRisked = accountBalance * (riskPercentage / 100);
        const pipValue = 10; // 1 pip = $10 for Forex
        const lotSize = amountRisked / (stopLoss * pipValue);
        const amountGained = lotSize * takeProfit * pipValue;
        const rrRatio = (takeProfit / stopLoss).toFixed(2);
        const lotSizeDivided = (lotSize / 4).toFixed(2);

        document.getElementById('forexAmountRisked').innerText = `$${amountRisked.toFixed(2)}`;
        document.getElementById('forexAmountGained').innerText = `$${amountGained.toFixed(2)}`;
        document.getElementById('forexLotSize').innerText = lotSize.toFixed(2);
        document.getElementById('forexRrRatio').innerText = rrRatio;
        document.getElementById('forexLotSizeDivided').innerText = lotSizeDivided;
    }

    // Indices Calculation
    function calculateIndices() {
        const accountBalance = parseFloat(document.getElementById('indicesAccountBalance').value);
        const riskPercentage = parseFloat(document.getElementById('indicesRiskPercentage').value);
        const stopLoss = parseFloat(document.getElementById('indicesStopLoss').value);
        const takeProfit = parseFloat(document.getElementById('indicesTakeProfit').value);
        const instrument = document.getElementById('indicesInstrument').value;

        if (isNaN(accountBalance) || isNaN(riskPercentage) || isNaN(stopLoss) || isNaN(takeProfit)) {
            alert("Please fill in all fields with valid numbers.");
            return;
        }

        const amountRisked = accountBalance * (riskPercentage / 100);
        const pointValue = getPointValue(instrument); // Get point value for indices
        const lotSize = amountRisked / (stopLoss * pointValue);
        const amountGained = lotSize * takeProfit * pointValue;
        const rrRatio = (takeProfit / stopLoss).toFixed(2);
        const lotSizeDivided = (lotSize / 4).toFixed(2);

        document.getElementById('indicesAmountRisked').innerText = `$${amountRisked.toFixed(2)}`;
        document.getElementById('indicesAmountGained').innerText = `$${amountGained.toFixed(2)}`;
        document.getElementById('indicesLotSize').innerText = lotSize.toFixed(2);
        document.getElementById('indicesRrRatio').innerText = rrRatio;
        document.getElementById('indicesLotSizeDivided').innerText = lotSizeDivided;
    }

    function getPointValue(instrument) {
        // Point values for indices
        const pointValues = {
            'NAS100': 1,    // 1 point = $1 per standard lot
            'S&P500': 10    // 1 point = $10 per standard lot
        };
        return pointValues[instrument] || 1; // Default to 1 if not found
    }
</script>

</body>
</html>
