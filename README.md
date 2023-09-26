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
        }

        th, td {
            width: 30px;
            height: 30px;
            text-align: center;
            cursor: pointer;
            background-color: black !important; /* Fundo preto para todas as células */
        }

        th {
            background-color: #f2f2f2;
            color: black;
        }

        th.I {
            width: 30px; /* Largura fixa para a coluna "I" */
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
            background-color: black !important; /* Fundo preto para células não atingidas */
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

        td.white {
            background-color: white; /* Fundo branco para células da coluna J */
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
            font-size: 18px;
            display: inline-block;
            margin-right: 10px;
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

        #password-input, #start-button {
            width: 150px;
            margin: 5px;
            padding: 5px;
            text-align: center;
            color: yellow;
        }

        .center-container {
            display: flex;
            flex-direction: column;
            align-items: center;
            margin-top: 20px; /* Ajuste a margem superior conforme necessário */
        }

        #password-input, #start-button {
            margin: 5px;
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
            color: white;
            font-size: 18px;
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
                <th class="letter I">I</th> <!-- Adicionada classe I para a coluna "I" -->
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
            <!-- Quadrante Azul -->
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
            <!-- Quadrante Amarelo -->
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
            <!-- Quadrante Verde -->
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
            <!-- Quadrante Branco -->
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
            <!-- Quadrante Vermelho -->
            <tr>
                <th class="number">06</th>
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
            <!-- Quadrante Azul -->
            <tr>
                <th class="number">07</th>
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
                <th class="number">08</th>
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
            <!-- Quadrante Verde -->
            <tr>
                <th class="number">09</th>
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
            <!-- Quadrante Branco -->
            <tr>
                <th class="number">10</th>
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
        </tbody>
    </table>
    <div class="center-container">
        <input type="password" id="password-input" placeholder="PASSWORD">
        <button id="start-button">START</button>
    </div>

    <!-- POSIÇÃO INIMIGA -->
    <div id="teriana-coordinates"></div>

    <script>
        // O restante do seu código JavaScript aqui...
    </script>
</body>
</html>
