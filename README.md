<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SAM.IA</title>
    <style>
        /* Colores pastel */
        :root {
            --pastel-pink: #f5c0e6;
            --pastel-blue: #fc00b0;
            --background: #6a90c1;
        }

        body {
            font-family: Arial, sans-serif;
            background-color: var(--background);
            margin: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }

        .chat-container {
            width: 400px;
            max-width: 90%;
            background-color: white;
            border-radius: 15px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
            display: flex;
            flex-direction: column;
            overflow: hidden;
        }

        .chat-header {
            background-color: var(--pastel-pink);
            color: white;
            padding: 15px;
            font-size: 1.2em;
            text-align: center;
            font-weight: bold;
        }

        .chat-messages {
            padding: 15px;
            flex: 1;
            overflow-y: auto;
        }

        .message {
            margin-bottom: 10px;
            padding: 8px 12px;
            border-radius: 10px;
            max-width: 80%;
        }

        .user {
            background-color: var(--pastel-blue);
            color: #333;
            align-self: flex-end;
        }

        .ai {
            background-color: var(--pastel-pink);
            color: #333;
            align-self: flex-start;
        }

        .chat-input {
            display: flex;
            border-top: 1px solid #ddd;
        }

        .chat-input input {
            flex: 1;
            padding: 10px;
            border: none;
            outline: none;
            font-size: 1em;
        }

        .chat-input button {
            background-color: var(--pastel-blue);
            border: none;
            color: white;
            padding: 10px 15px;
            cursor: pointer;
            font-weight: bold;
        }

        .chat-input button:hover {
            opacity: 0.9;
        }
    </style>
</head>
<body>
    <div class="chat-container">
        <div class="chat-header">SAM IA</div>
        <div class="chat-messages" id="messages"></div>
        <div class="chat-input">
            <input type="text" id="userInput" placeholder="Escribe aquí..." />
            <button onclick="sendMessage()">Enviar</button>
        </div>
    </div>

    <script>
        const messages = document.getElementById("messages");
        const userInput = document.getElementById("userInput");

        function addMessage(text, className) {
            const msg = document.createElement("div");
            msg.classList.add("message", className);
            msg.textContent = text;
            messages.appendChild(msg);
            messages.scrollTop = messages.scrollHeight;
        }

        function sendMessage() {
            const text = userInput.value.trim();
            if (!text) return;

            addMessage(text, "user");
            userInput.value = "";

            // Simular respuesta de la IA
            setTimeout(() => {
                addMessage("SAM: He recibido tu mensaje \"" + text + "\"", "ai");
            }, 800);
        }

        // Permitir enviar con Enter
        userInput.addEventListener("keypress", function(e) {
            if (e.key === "Enter") sendMessage();
        });
    </script>
</body>
</html>
