<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        body {
            background-color: black;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            flex-direction: column;
            font-family: "Press Start 2P", monospace;
        }

        table {
            border-collapse: collapse;
            table-layout: fixed; /* Define a largura da tabela como fixa */
        }

        table, th, td {
            border: 1px solid white;
            background-color: black;
        }

        th, td {
            width: 30px;
            height: 30px;
            text-align: center;
            cursor: pointer;
        }

        th {
            background-color: #f2f2f2;
            color: black;
        }

        th.letter, th.number {
            background-color: black;
            color: white;
        }

        td.clicked {
            background-color: red;
        }

        td.hit {
            animation: explode 0.5s infinite alternate;
        }

        @keyframes explode {
            0% { background-color: red; }
            33% { background-color: yellow; }
            66% { background-color: white; }
            100% { background-color: red; }
        }

        td.miss {
            background-color: black;
        }

        td.red {
            background-color: red;
        }

        td.blue {
            background-color: blue;
        }

        td.yellow {
            background-color: yellow;
        }

        td.green {
            background-color: green;
        }

        #map-title {
            font-size: 32px;
            margin-bottom: 10px;
            animation: holographic 0.5s infinite;
        }

        @keyframes holographic {
            0%, 100% { color: #FF0000; }
            20% { color: #FF9900; }
            40% { color: #FFFF00; }
            60% { color: #33FF33; }
            80% { color: #3366FF; }
        }

        #shots, #time, #hits {
            font-size: 20px;
            display: inline-block;
            margin-right: 12px;
        }

        #shots {
            color: yellow;
        }

        #time {
            color: yellow;
        }

        #hits {
            color: yellow;
        }

        /* Centralize o campo de senha e o botão START */
        #password-input, #start-button {
            display: block;
            margin: 10px auto;
            width: 150px;
            padding: 5px;
            text-align: center;
            color: blue;
        }

        #teriana-coordinates {
            color: yellow;
            font-size: 20px;
            animation: blink 1s infinite;
        }

        @keyframes blink {
            0%, 100% {
                opacity: 1;
            }
            50% {
                opacity: 0;
            }
        }

        #time-left {
            color: yellow;
            font-size: 20px;
        }

        body {
            background-image: url("https://i.gifer.com/XzZg.gif");
            background-size: cover;
        }
    </style>
</head>
<body>
    <h1 id="map-title">BATTLESHIP GALAXY©</h1>
    <div>
        <span id="shots">SHOTS: <span id="shots-remaining" style="color: red;">12</span></span>
        <span id="time">TIME: <span id="time-left" style="color: green;">120</span> s</span>
        <span id="hits">PTS: <span id="hits-count" style="color: yellow;">0</span></span>
    </div>
    <table>
        <thead>
            <tr>
                <th class="letter"></th>
                <th class="letter">A</th>
                <th class="letter">B</th>
                <th class="letter">C</th>
                <th class="letter">D</th>
                <th class="letter">E</th>
                <th class="letter">F</th>
                <th class="letter">G</th>
                <th class="letter">H</th>
                <th class="letter">I</th>
                <th class="letter">J</th>
            </tr>
        </thead>
        <tbody>
            <!-- Quadrante Vermelho -->
            <tr>
                <th class="number">01</th>
                <td class="red"></td>
                <td class="red"></td>
                <td class="red"></td>
                <td class="red"></td>
                <td class="red"></td>
                <td class="blue"></td>
                <td class="blue"></td>
                <td class="blue"></td>
                <td class="blue"></td>
                <td class="blue"></td>
            </tr>
            <tr>
                <th class="number">02</th>
                <td class="red"></td>
                <td class="red"></td>
                <td class="red"></td>
                <td class="red"></td>
                <td class="red"></td>
                <td class="blue"></td>
                <td class="blue"></td>
                <td class="blue"></td>
                <td class="blue"></td>
                <td class="blue"></td>
            </tr>
            <tr>
                <th class="number">03</th>
                <td class="red"></td>
                <td class="red"></td>
                <td class="red"></td>
                <td class="red"></td>
                <td class="red"></td>
                <td class="blue"></td>
                <td class="blue"></td>
                <td class="blue"></td>
                <td class="blue"></td>
                <td class="blue"></td>
            </tr>
            <tr>
                <th class="number">04</th>
                <td class="red"></td>
                <td class="red"></td>
                <td class="red"></td>
                <td class="red"></td>
                <td class="red"></td>
                <td class="blue"></td>
                <td class="blue"></td>
                <td class="blue"></td>
                <td class="blue"></td>
                <td class="blue"></td>
            </tr>
            <tr>
                <th class="number">05</th>
                <td class="red"></td>
                <td class="red"></td>
                <td class="red"></td>
                <td class="red"></td>
                <td class="red"></td>
                <td class="blue"></td>
                <td class="blue"></td>
                <td class="blue"></td>
                <td class="blue"></td>
                <td class="blue"></td>
            </tr>
            <!-- Quadrante Amarelo -->
            <tr>
                <th class="number">06</th>
                <td class="yellow"></td>
                <td class="yellow"></td>
                <td class="yellow"></td>
                <td class="yellow"></td>
                <td class="yellow"></td>
                <td class="green"></td>
                <td class="green"></td>
                <td class="green"></td>
                <td class="green"></td>
                <td class="green"></td>
            </tr>
            <tr>
                <th class="number">07</th>
                <td class="yellow"></td>
                <td class="yellow"></td>
                <td class="yellow"></td>
                <td class="yellow"></td>
                <td class="yellow"></td>
                <td class="green"></td>
                <td class="green"></td>
                <td class="green"></td>
                <td class="green"></td>
                <td class="green"></td>
            </tr>
            <tr>
                <th class="number">08</th>
                <td class="yellow"></td>
                <td class="yellow"></td>
                <td class="yellow"></td>
                <td class="yellow"></td>
                <td class="yellow"></td>
                <td class="green"></td>
                <td class="green"></td>
                <td class="green"></td>
                <td class="green"></td>
                <td class="green"></td>
            </tr>
            <tr>
                <th class="number">09</th>
                <td class="yellow"></td>
                <td class="yellow"></td>
                <td class="yellow"></td>
                <td class="yellow"></td>
                <td class="yellow"></td>
                <td class="green"></td>
                <td class="green"></td>
                <td class="green"></td>
                <td class="green"></td>
                <td class="green"></td>
            </tr>
            <tr>
                <th class="number">10</th>
                <td class="yellow"></td>
                <td class="yellow"></td>
                <td class="yellow"></td>
                <td class="yellow"></td>
                <td class="yellow"></td>
                <td class="green"></td>
                <td class="green"></td>
                <td class="green"></td>
                <td class="green"></td>
                <td class="green"></td>
            </tr>
        </tbody>
    </table>
    <!-- Centralize o campo de senha e o botão START verticalmente -->
    <div style="text-align: center;">
        <input type="password" id="password-input" placeholder="PASSWORD">
        <button id="start-button">!!!     START     !!!</button>
    </div>

    <!-- POSIÇÃO INIMIGA -->
    <div id="teriana-coordinates"></div>

    <script>
        const table = document.querySelector('table');
        const tbody = table.querySelector('tbody');
        const shotsCounter = document.getElementById('shots-remaining');
        const terianaCoordinates = document.getElementById('teriana-coordinates');
        const timeLeft = document.getElementById('time-left');
        const hitsCount = document.getElementById('hits-count');
        const startButton = document.getElementById('start-button');
        const passwordInput = document.getElementById('password-input');
        let shotsRemaining = 12;
        let time = 120; // Alteração do tempo para 120 segundos
        let timerRunning = false;
        let hits = 0;

        // Função para atualizar o tempo restante
        function updateTime() {
            timeLeft.textContent = time;
            if (time === 0) {
                clearInterval(timer);
                alert('TEMPO ESGOTADO! VERIFIQUE SEUS PONTOS E RETIRE SEU BRINDE!');
            }
            time--;
        }

        // Evento de clique no botão INICIAR
        startButton.addEventListener('click', () => {
            const password = passwordInput.value;
            if (password === 'u55C@ttal!n!') { // Alteração da senha
                if (!timerRunning) {
                    timerRunning = true;
                    timer = setInterval(updateTime, 1000);
                }
            } else {
                alert('Senha incorreta. Gariani Tá de Olho!');
            }
        });

        const cells = document.querySelectorAll('td');

        cells.forEach(cell => {
            cell.addEventListener('click', () => {
                if (timerRunning && shotsRemaining > 0) {
                    if (!cell.classList.contains('clicked')) {
                        cell.classList.toggle('clicked');
                        shotsRemaining--;
                        shotsCounter.textContent = shotsRemaining;

                        const columnIndex = cell.cellIndex;
                        const rowIndex = cell.parentNode.rowIndex;

                        const columnLetter = String.fromCharCode(65 + columnIndex - 1);
                        const rowNumber = rowIndex;

                        const shotCoordinate = columnLetter + rowNumber;

                        // Verifique se o tiro acertou uma coordenada da nave Teriana
                        if (isTerianaCoordinate(shotCoordinate)) {
                            cell.classList.remove('blue', 'red', 'yellow', 'green');
                            cell.classList.add('hit');
                            hits++;
                            hitsCount.textContent = hits;
                        } else {
                            cell.classList.remove('blue', 'red', 'yellow', 'green');
                            cell.classList.add('miss');
                        }

                        if (shotsRemaining === 0) {
                            // Todos os tiros foram dados, exibe a FRASE
                            terianaCoordinates.textContent = 'ICHI.. EFETIVAMENTE SEUS TIROS ACABARAM!';
                        }
                    }
                }
            });
        });

        // Função para verificar se a coordenada pertence à nave Teriana
        function isTerianaCoordinate(coordinate) {
            const terianaCoordinates = ['H2', 'H3', 'H5', 'I2', 'I3', 'I4', 'I5', 'J2', 'J3', 'J4'];
            return terianaCoordinates.includes(coordinate);
        }
    </script>
</body>
</html>
