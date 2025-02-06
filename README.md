# amigo-secreto
Este proyecto es una aplicación web sencilla para realizar un sorteo de "Amigo Secreto". Permite a los usuarios ingresar nombres en una lista y seleccionar aleatoriamente un ganador.

git clone https://github.com/marianis17/amigo-secreto.git


<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Amigo Secreto</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #f9f9f9;
            margin: 0;
            padding: 20px;
        }

        .container {
            max-width: 400px;
            margin: 0 auto;
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
        }

        button {
            background-color: #28a745;
            color: white;
            border: none;
            padding: 10px;
            margin: 5px;
            cursor: pointer;
            border-radius: 5px;
        }

        button:hover {
            background-color: #218838;
        }

        input {
            padding: 10px;
            width: 80%;
            margin-bottom: 10px;
            border: 1px solid #ccc;
            border-radius: 5px;
        }

        ul {
            list-style-type: none;
            padding: 0;
        }

        ul li {
            background: #ddd;
            margin: 5px;
            padding: 10px;
            border-radius: 5px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Juego de Amigo Secreto</h1>
        <input type="text" id="nombreInput" placeholder="Ingresa un nombre">
        <button onclick="agregarAmigo()">Adicionar</button>
        <ul id="listaAmigos"></ul>
        <button onclick="sortearAmigo()">Sortear Amigo</button>
        <p id="resultado"></p>
        <button onclick="reiniciarJuego()">Reiniciar</button>
    </div>

    <script>
        let amigos = [];

        function agregarAmigo() {
            let input = document.getElementById("nombreInput");
            let nombre = input.value.trim();

            if (nombre === "") {
                alert("Por favor, inserte un nombre válido.");
                return;
            }

            if (amigos.includes(nombre)) {
                alert("Este nombre ya fue agregado.");
                return;
            }

            amigos.push(nombre);
            actualizarLista();
            input.value = "";
        }

        function actualizarLista() {
            let lista = document.getElementById("listaAmigos");
            lista.innerHTML = "";

            amigos.forEach((amigo) => {
                let li = document.createElement("li");
                li.textContent = amigo;
                lista.appendChild(li);
            });
        }

        function sortearAmigo() {
            if (amigos.length === 0) {
                alert("No hay amigos en la lista para sortear.");
                return;
            }

            let indiceAleatorio = Math.floor(Math.random() * amigos.length);
            let amigoSorteado = amigos[indiceAleatorio];

            document.getElementById("resultado").textContent = `El amigo secreto es: ${amigoSorteado}`;
        }

        function reiniciarJuego() {
            amigos = [];
            actualizarLista();
            document.getElementById("resultado").textContent = "";
        }
    </script>
</body>
</html>


