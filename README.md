<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Doodle Team Builder</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #222;
            color: white;
        }
        .team-container {
            display: flex;
            justify-content: center;
            gap: 10px;
            margin-bottom: 20px;
        }
        .doodle-list {
            display: flex;
            flex-direction: column;
            align-items: center;
        }
        .doodle-card {
            display: flex;
            align-items: center;
            background-color: #333;
            padding: 10px;
            border-radius: 5px;
            margin: 5px;
            width: 300px;
            justify-content: space-between;
        }
        .doodle-card img {
            width: 40px;
            height: 40px;
        }
        .doodle-card .info {
            flex-grow: 1;
            text-align: left;
            margin-left: 10px;
        }
        .type {
            display: inline-block;
            padding: 5px 10px;
            margin: 2px;
            border-radius: 5px;
            font-size: 12px;
        }
        .expand-btn, .remove-btn {
            background-color: #555;
            border: none;
            color: white;
            padding: 5px 10px;
            cursor: pointer;
        }
        .hidden { display: none; }
    </style>
</head>
<body>
    <h1>Doodle Team Builder</h1>
    <div>
        <label for="team-name">Team Name: </label>
        <input type="text" id="team-name" placeholder="Enter team name">
    </div>
    <div>
        <label for="doodle-select">Select Doodle</label>
        <select id="doodle-select">
            <option value="">--Select Doodle--</option>
        </select>
        <button onclick="addDoodle()">Add Doodle</button>
    </div>
    <h2>Current Team</h2>
    <div class="doodle-list" id="team-list"></div>
    <script>
        const doodles = [
            { name: "Doodle A", type: ["Water", "Light"], image: "https://via.placeholder.com/40", moves: "Water Blast, Shine", equipment: "Shell Armor", stats: "+10 Speed, +5 Defense" },
            { name: "Doodle B", type: ["Fire", "Air"], image: "https://via.placeholder.com/40", moves: "Flame Throw, Wind Gust", equipment: "Flame Cloak", stats: "+15 Attack, +5 Speed" }
        ];
        
        function populateDropdown() {
            let select = document.getElementById("doodle-select");
            doodles.forEach(doodle => {
                let option = document.createElement("option");
                option.value = doodle.name;
                option.textContent = doodle.name;
                select.appendChild(option);
            });
        }
        
        function addDoodle() {
            let select = document.getElementById("doodle-select");
            let doodle = doodles.find(d => d.name === select.value);
            if (!doodle) return;
            
            let list = document.getElementById("team-list");
            let card = document.createElement("div");
            card.classList.add("doodle-card");
            
            let img = document.createElement("img");
            img.src = doodle.image;
            
            let info = document.createElement("div");
            info.classList.add("info");
            info.innerHTML = `<strong>${doodle.name}</strong><br>` +
                doodle.type.map(t => `<span class='type' style='background-color: gray;'>${t}</span>`).join(" ");
            
            let expandBtn = document.createElement("button");
            expandBtn.classList.add("expand-btn");
            expandBtn.textContent = "Expand";
            expandBtn.onclick = function() {
                details.classList.toggle("hidden");
            };
            
            let removeBtn = document.createElement("button");
            removeBtn.classList.add("remove-btn");
            removeBtn.textContent = "Remove";
            removeBtn.onclick = function() {
                list.removeChild(card);
            };
            
            let details = document.createElement("div");
            details.classList.add("hidden");
            details.innerHTML = `<p>Moves: ${doodle.moves}</p><p>Equipment: ${doodle.equipment}</p><p>Stats: ${doodle.stats}</p>`;
            
            card.appendChild(img);
            card.appendChild(info);
            card.appendChild(expandBtn);
            card.appendChild(removeBtn);
            card.appendChild(details);
            list.appendChild(card);
        }
        
        populateDropdown();
    </script>
</body>
</html>
