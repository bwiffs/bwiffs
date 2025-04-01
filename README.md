<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Team Coverage Tool</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
        }
        .team-container {
            display: flex;
            justify-content: center;
            gap: 10px;
            margin-bottom: 20px;
        }
        .coverage-grid {
            display: grid;
            grid-template-columns: repeat(5, 1fr);
            gap: 5px;
            max-width: 400px;
            margin: 0 auto;
        }
        .grid-item {
            padding: 10px;
            background-color: lightgray;
            border: 1px solid #000;
        }
    </style>
</head>
<body>
    <h1>Team Coverage Tool</h1>
    <div class="team-container">
        <select class="team-member">
            <option value="">Select Member</option>
        </select>
        <select class="team-member">
            <option value="">Select Member</option>
        </select>
        <select class="team-member">
            <option value="">Select Member</option>
        </select>
    </div>
    <div class="coverage-grid">
        <div class="grid-item">1</div>
        <div class="grid-item">2</div>
        <div class="grid-item">3</div>
        <div class="grid-item">4</div>
        <div class="grid-item">5</div>
        <div class="grid-item">6</div>
        <div class="grid-item">7</div>
        <div class="grid-item">8</div>
        <div class="grid-item">9</div>
        <div class="grid-item">10</div>
    </div>
    <script>
        document.querySelectorAll('.team-member').forEach(select => {
            select.addEventListener('change', () => {
                console.log('Selection changed:', select.value);
            });
        });
    </script>
</body>
</html>
