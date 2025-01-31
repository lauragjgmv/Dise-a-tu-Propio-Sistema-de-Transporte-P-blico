<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Diseña tu Propio Sistema de Transporte</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #f0f0f0;
        }
        .container {
            width: 80%;
            margin: auto;
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0px 0px 10px gray;
        }
        .map {
            width: 100%;
            height: 400px;
            background: url('(https://upload.wikimedia.org/wikipedia/commons/thumb/e/e7/Urban_Transit_Map.svg/1200px-Urban_Transit_Map.svg.png)') no-repeat center center;
            background-size: cover;
            position: relative;
        }
        .station {
            width: 20px;
            height: 20px;
            background: red;
            border-radius: 50%;
            position: absolute;
            cursor: pointer;
        }
        select {
            padding: 10px;
            margin: 10px;
            font-size: 16px;
            border-radius: 5px;
        }
        button {
            padding: 12px 20px;
            font-size: 18px;
            border: none;
            background: #007BFF;
            color: white;
            border-radius: 5px;
            cursor: pointer;
        }
        button:hover {
            background: #0056b3;
        }
        #resultado {
            margin-top: 20px;
            font-size: 18px;
        }
    </style>
</head>
<body>

    <div class="container">
        <h1>🚍 Diseña tu Sistema de Transporte Público 🚆</h1>
        <p>Selecciona el tipo de transporte y coloca estaciones estratégicamente en la ciudad.</p>

        <label for="transporte">🚊 Elige el tipo de transporte:</label>
        <select id="transporte">
            <option value="Metro">Metro</option>
            <option value="Autobús">Autobús</option>
            <option value="Tranvía">Tranvía</option>
        </select>

        <button onclick="agregarEstacion()">➕ Agregar Estación</button>
        <button onclick="validarSistema()">✅ Validar Ruta</button>

        <div class="map" id="mapa">
            <!-- Estaciones se agregarán aquí dinámicamente -->
        </div>

        <p id="resultado"></p>
    </div>

    <script>
        let estaciones = [];
        let maxEstaciones = 5; // Número máximo de estaciones permitidas

        function agregarEstacion() {
            if (estaciones.length < maxEstaciones) {
                let mapa = document.getElementById("mapa");
                let estacion = document.createElement("div");
                estacion.classList.add("station");

                // Posicionamiento aleatorio dentro del mapa
                let x = Math.random() * (mapa.clientWidth - 20);
                let y = Math.random() * (mapa.clientHeight - 20);
                estacion.style.left = x + "px";
                estacion.style.top = y + "px";

                mapa.appendChild(estacion);
                estaciones.push({ x, y });
            } else {
                alert("¡Has alcanzado el número máximo de estaciones permitidas!");
            }
        }

        function validarSistema() {
            let transporte = document.getElementById("transporte").value;
            let resultado = document.getElementById("resultado");

            if (estaciones.length < 3) {
                resultado.innerHTML = "❌ No hay suficientes estaciones. Agrega más para que la red sea eficiente.";
                resultado.style.color = "red";
                return;
            }

            if (transporte === "Metro" && estaciones.length >= 4) {
                resultado.innerHTML = "✅ Excelente elección. Tu sistema de metro optimiza la movilidad en la ciudad.";
                resultado.style.color = "green";
            } else if (transporte === "Autobús" && estaciones.length >= 3) {
                resultado.innerHTML = "✅ Bien hecho. Tu sistema de autobuses mejora la conexión entre barrios.";
                resultado.style.color = "green";
            } else if (transporte === "Tranvía" && estaciones.length >= 3) {
                resultado.innerHTML = "✅ Gran solución. El tranvía es eficiente y ecológico.";
                resultado.style.color = "green";
            } else {
                resultado.innerHTML = "❌ Tu sistema de transporte no es óptimo. Prueba otra estrategia.";
                resultado.style.color = "red";
            }
        }
    </script>

</body>
</html>
