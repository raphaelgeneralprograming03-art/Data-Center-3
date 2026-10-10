
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <title>SISTEMA OPERACIONAL CENTRAL - V1.0</title>
    <style>
        body { background: #050505; color: #00ff41; font-family: 'Courier New', monospace; margin: 0; overflow: hidden; }
        #canvas-overlay { position: absolute; top: 0; left: 0; pointer-events: none; }
        .dashboard { display: grid; grid-template-columns: 250px 1fr 300px; height: 100vh; }
        .panel { border: 1px solid #00ff41; padding: 15px; background: rgba(0, 20, 0, 0.8); overflow-y: auto; }
        .status-on { color: #00ff41; text-shadow: 0 0 5px #00ff41; }
        .header { text-align: center; border-bottom: 2px solid #00ff41; padding: 10px; font-weight: bold; }
        input, button { background: #000; border: 1px solid #00ff41; color: #00ff41; width: 100%; margin-top: 5px; }
        #log { font-size: 0.8em; white-space: pre-wrap; }
    </style>
</head>
<body>

<canvas id="matrixCanvas"></canvas>

<div class="dashboard" style="position: relative; z-index: 10;">
    <!-- Coluna Esquerda: Conexões -->
    <div class="panel">
        <div class="header">SISTEMAS CONECTADOS</div>
        <p>SATÉLITE: <span class="status-on" id="sat-status">SINCRO...</span></p>
        <p>DEEP WEB: <span class="status-on">TOR_GATEWAY_ON</span></p>
        <p>WI-FI/RF: <span class="status-on">MONITORING</span></p>
        <hr>
        <div id="hardware-monitor">
            <small>HARDWARE STATUS:</small>
            <div id="cpu-load">CPU: 0%</div>
            <canvas id="cpuGraph" width="200" height="50"></canvas>
        </div>
    </div>

    <!-- Centro: Mapa de Conexões e Logs -->
    <div class="panel">
        <div class="header">TERMINAL GLOBAL DE ACESSO</div>
        <div id="log">Iniciando protocolos de segurança...
Conectando ao banco de dados global...
Autenticando chaves de criptografia...</div>
        <canvas id="mapCanvas" width="600" height="300"></canvas>
    </div>

    <!-- Direita: Controle de Credenciais -->
    <div class="panel">
        <div class="header">GERENCIADOR DE ACESSO</div>
        <label>GMAIL / E-MAIL:</label>
        <input type="text" id="email" placeholder="admin@system.com">
        <label>ENCRYPTION KEY:</label>
        <input type="password" id="pass" placeholder="********">
        <button onclick="executeCommand()">EXECUTAR CONEXÃO</button>
        <hr>
        <div class="header">VIGILÂNCIA (CAMS)</div>
        <div style="background:#000; height:150px; border:1px solid #00ff41; display:flex; align-items:center; justify-content:center;">
            [CÂMERA ATIVA]
        </div>
    </div>
</div>

<script>
    const canvas = document.getElementById('matrixCanvas');
    const ctx = canvas.getContext('2d');
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;

    const chars = "0123456789ABCDEFHIJKLMNOPQRSTUVWXYZ@#$%&*";
    const fontSize = 14;
    const columns = canvas.width / fontSize;
    const drops = Array(Math.floor(columns)).fill(1);

    function drawMatrix() {
        ctx.fillStyle = "rgba(0, 0, 0, 0.05)";
        ctx.fillRect(0, 0, canvas.width, canvas.height);
        ctx.fillStyle = "#0F0";
        ctx.font = fontSize + "px monospace";
        for (let i = 0; i < drops.length; i++) {
            const text = chars.charAt(Math.floor(Math.random() * chars.length));
            ctx.fillText(text, i * fontSize, drops[i] * fontSize);
            if (drops[i] * fontSize > canvas.height && Math.random() > 0.975) drops[i] = 0;
            drops[i]++;
        }
    }

    function executeCommand() {
        const log = document.getElementById('log');
        log.innerHTML += "\n> Estabelecendo conexão segura via RSA-4096...";
        log.innerHTML += "\n> Acessando Base de Dados Global...";
        // Aqui o JS chamaria as APIs do Python/Go
    }

    setInterval(drawMatrix, 50);
</script>
</body>
</html>
