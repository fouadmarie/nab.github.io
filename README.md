<!DOCTYPE html>
<html>
<head>
    <title>Mini Royale</title>
    <style>
        #game-board {
            width: 300px;
            height: 500px;
            background: #7cfc00; /* Grass color */
            position: relative;
            border: 5px solid #555;
            margin: 0 auto;
            overflow: hidden;
        }
        .unit {
            width: 30px;
            height: 30px;
            position: absolute;
            border-radius: 50%;
        }
        .player-unit { background: blue; }
        .enemy-unit { background: red; }
        
        .controls { text-align: center; margin-top: 10px; }
    </style>
</head>
<body>

    <div id="game-board">
        </div>

    <div class="controls">
        <button onclick="spawnUnit('player')">Spawn Blue Knight</button>
    </div>

    <script>
        const board = document.getElementById('game-board');

        function spawnUnit(type) {
            const unit = document.createElement('div');
            unit.className = `unit ${type}-unit`;
            unit.style.left = '135px'; // Middle
            unit.style.bottom = '10px';
            board.appendChild(unit);

            // Basic AI: Move upward
            let position = 10;
            const moveInterval = setInterval(() => {
                position += 2;
                unit.style.bottom = position + 'px';

                if (position > 470) {
                    clearInterval(moveInterval);
                    unit.remove(); // Reached the end
                }
            }, 50);
        }
    </script>
</body>
</html>
