<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mera Day Counter</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background: linear-gradient(135deg, #74b9ff, #a29bfe);
            margin: 0;
        }
        .counter-container {
            text-align: center;
            background: white;
            padding: 40px;
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.15);
            max-width: 90%;
            width: 350px;
        }
        h1 {
            font-size: 4.5rem;
            color: #6c5ce7;
            margin: 15px 0;
        }
        p {
            color: #2d3436;
            font-size: 1.2rem;
            margin: 5px 0;
        }
        button {
            background-color: #ff7675;
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 8px;
            cursor: pointer;
            margin-top: 25px;
            font-weight: bold;
            transition: 0.2s;
        }
        button:hover {
            background-color: #d63031;
        }
    </style>
</head>
<body>

<div class="counter-container">
    <p id="message">Loading...</p>
    <h1 id="days-display">0</h1>
    <p id="sub-message">din ho gaye hain.</p>
    <button onclick="resetDate()">Reset Date</button>
</div>

<script>
    function calculateDays() {
        let savedDate = localStorage.getItem("webTargetDate");

        if (!savedDate) {
            let userInput = prompt("Format: YYYY-MM-DD mein date dalein (Example: 2026-01-01):");
            if (userInput) {
                localStorage.setItem("webTargetDate", userInput);
                savedDate = userInput;
            } else {
                document.getElementById("message").innerText = "Kripya date enter karein.";
                return;
            }
        }

        let date1 = new Date(savedDate);
        let date2 = new Date();
        
        let timeDiff = date2.getTime() - date1.getTime();
        let daysDiff = Math.floor(timeDiff / (1000 * 3600 * 24));

        document.getElementById("message").innerText = savedDate + " se lekar ab tak:";
        document.getElementById("days-display").innerText = daysDiff;
    }

    function resetDate() {
        localStorage.removeItem("webTargetDate");
        calculateDays();
    }

    calculateDays();
</script>

</body>
</html>
