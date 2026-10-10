
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <title>SISTEMA OPERACIONAL CENTRAL - V1.0 (UNIFICADO)</title>
    <style>
        :root {
            --neon-green: #00ff41;
            --dark-bg: #050505;
            --panel-bg: rgba(0, 20, 0, 0.85);
            --border-glow: 0 0 10px rgba(0, 255, 65, 0.4);
        }
        * { box-sizing: border-box; }
        body {
            background: var(--dark-bg);
            color: var(--neon-green);
            font-family: 'Courier New', monospace;
            margin: 0;
            overflow-x: hidden;
        }
        #matrixCanvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100vw;
            height: 100vh;
            pointer-events: none;
            z-index: 0;
        }
        .container {
            position: relative;
            z-index: 10;
            max-width: 1600px;
            margin: 0 auto;
            padding: 15px;
        }
        .overview-banner {
            border: 1px solid var(--neon-green);
            background: rgba(0, 10, 0, 0.95);
            padding: 15px;
            margin-bottom: 15px;
            box-shadow: var(--border-glow);
        }
        .overview-banner h2 {
            margin-top: 0;
            border-bottom: 1px solid var(--neon-green);
            padding-bottom: 5px;
            font-size: 1.1em;
            letter-spacing: 2px;
        }
        .modules-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
            gap: 10px;
            margin-top: 10px;
            font-size: 0.85em;
        }
        .module-card {
            border: 1px dashed var(--neon-green);
            padding: 8px;
            background: rgba(0, 30, 0, 0.5);
        }
        .dashboard {
            display: grid;
            grid-template-columns: 280px 1fr 320px;
            gap: 15px;
            min-height: 70vh;
        }
        @media(max-width: 1100px) {
            .dashboard { grid-template-columns: 1fr; }
        }
        .panel {
            border: 1px solid var(--neon-green);
            padding: 15px;
            background: var(--panel-bg);
            box-shadow: var(--border-glow);
            display: flex;
            flex-direction: column;
            gap: 12px;
        }
        .status-on {
            color: var(--neon-green);
            text-shadow: 0 0 5px var(--neon-green);
        }
        .header {
            text-align: center;
            border-bottom: 2px solid var(--neon-green);
            padding-bottom: 8px;
            font-weight: bold;
            letter-spacing: 1px;
        }
        input, button {
            background: #000;
            border: 1px solid var(--neon-green);
            color: var(--neon-green);
            width: 100%;
            padding: 8px;
            margin-top: 5px;
            font-family: 'Courier New', monospace;
            cursor: pointer;
        }
        button:hover {
            background: #00ff41;
            color: #000;
            box-shadow: 0 0 10px #00ff41;
        }
        #log {
            font-size: 0.8em;
            white-space: pre-wrap;
            background: #000;
            border: 1px solid #00ff41;
            padding: 10px;
            flex-grow: 1;
            overflow-y: auto;
            max-height: 250px;
        }
    </style>
</head>
<body>

<canvas id="matrixCanvas"></canvas>

<div class="container">
    <!-- VISÃO GERAL DO APLICATIVO -->
    <div class="overview-banner">
        <h2>// VISÃO GERAL DO APLICATIVO - SISTEMA OPERACIONAL CENTRAL V1.0</h2>
        <p>Arquitetura unificada de alta segurança, combinando módulos especializados para monitoramento de infraestrutura, criptografia e inteligência de redes:</p>
        <div class="modules-grid">
            <div class="module-card">
                <strong>[HTML/CSS/JS] Frontend:</strong> Interface reativa com efeito Matrix dinâmico, radares de conexões e painéis táticos em tempo real.
            </div>
            <div class="module-card">
                <strong>[PYTHON] Backend & Criptografia:</strong> Gerenciamento de banco de dados SQLite (`global_security.db`), túneis Tor (SOCKS5) e hashes SHA-256.
            </div>
            <div class="module-card">
                <strong>[C++] Baixo Nível & Hardware:</strong> Escaneamento de frequências RF/Wi-Fi, criptografia acelerada (AES-NI) e sincronização de relógio atômico.
            </div>
            <div class="module-card">
                <strong>[GO] Alta Performance:</strong> Goroutines concorrentes para gerenciamento simultâneo de múltiplos nós de rede e fluxos de dados.
            </div>
            <div class="module-card">
                <strong>[BASH] Automação & DevOps:</strong> Blindagem com regras de firewall `iptables` e verificação contínua de integridade de arquivos.
            </div>
        </div>
    </div>

    <!-- DASHBOARD PRINCIPAL -->
    <div class="dashboard">
        <!-- Coluna Esquerda: Conexões e Hardware -->
        <div class="panel">
            <div class="header">SISTEMAS CONECTADOS</div>
            <p>SATÉLITE: <span class="status-on" id="sat-status">SINCRO...</span></p>
            <p>DEEP WEB: <span class="status-on">TOR_GATEWAY_ON</span></p>
            <p>WI-FI/RF: <span class="status-on">MONITORING</span></p>
            <hr style="border-color: #00ff41; opacity: 0.3;">
            
            <div class="header">HARDWARE (C++)</div>
            <div id="cpu-load">CPU USAGE: 14.2%</div>
            <button onclick="runCppScan()">Scan RF / Wi-Fi</button>
            
            <div class="header" style="margin-top:10px;">CONCORRÊNCIA (GO)</div>
            <button onclick="runGoWorkers()">Executar Goroutines</button>
        </div>

        <!-- Centro: Terminal Global e Radar -->
        <div class="panel">
            <div class="header">TERMINAL GLOBAL DE ACESSO & LOGS</div>
            <div id="log">> [INIT] Inicializando protocolos de segurança...
> [DB] Conectando ao banco de dados global (SQLite)...
> [TOR] Roteando tráfego via SOCKS5 127.0.0.1:9050...
> [SYSTEM READY] Aguardando comando do operador.</div>
            
            <div class="header" style="margin-top: 10px;">RADAR DE CONEXÕES</div>
            <canvas id="mapCanvas" width="550" height="150" style="background:#000; border:1px solid #00ff41; width:100%;"></canvas>
        </div>

        <!-- Direita: Credenciais, Bash e Câmeras -->
        <div class="panel">
            <div class="header">GERENCIAMENTO (PYTHON)</div>
            <label>GMAIL / E-MAIL:</label>
            <input type="text" id="email" value="admin@system.central">
            <label>CHAVE MESTRA (SHA-256):</label>
            <input type="password" id="pass" value="Sua_Chave_Mestra">
            <button onclick="executePythonAuth()">AUTENTICAR CONEXÃO</button>
            
            <div class="header" style="margin-top:10px;">FIREWALL (BASH)</div>
            <button onclick="runBashSecurity()">Aplicar iptables & Check</button>
            
            <div class="header" style="margin-top:10px;">VIGILÂNCIA (CAMS)</div>
            <div style="background:#000; height:90px; border:1px solid #00ff41; display:flex; align-items:center; justify-content:center; text-shadow: 0 0 8px #00ff41;">
                [CÂMERA ATIVA - SECURE FEED]
            </div>
        </div>
    </div>
</div>

<script>
    // --- EFEITO MATRIX (FRONTEND) ---
    const canvas = document.getElementById('matrixCanvas');
    const ctx = canvas.getContext('2d');
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;

    const chars = "0123456789ABCDEFHIJKLMNOPQRSTUVWXYZ@#$%&*<>\\/[]{}=";
    const fontSize = 14;
    const columns = canvas.width / fontSize;
    const drops = Array(Math.floor(columns)).fill(1);

    function drawMatrix() {
        ctx.fillStyle = "rgba(0, 0, 0, 0.05)";
        ctx.fillRect(0, 0, canvas.width, canvas.height);
        ctx.fillStyle = "#00ff41";
        ctx.font = fontSize + "px monospace";
        for (let i = 0; i < drops.length; i++) {
            const text = chars.charAt(Math.floor(Math.random() * chars.length));
            ctx.fillText(text, i * fontSize, drops[i] * fontSize);
            if (drops[i] * fontSize > canvas.height && Math.random() > 0.975) drops[i] = 0;
            drops[i]++;
        }
    }
    setInterval(drawMatrix, 50);

    // --- RADAR / MAPA CANVAS ---
    const mapCanvas = document.getElementById('mapCanvas');
    const mapCtx = mapCanvas.getContext('2d');
    let radarAngle = 0;

    function drawRadar() {
        mapCtx.fillStyle = "rgba(0, 10, 0, 0.3)";
        mapCtx.fillRect(0, 0, mapCanvas.width, mapCanvas.height);
        
        const centerX = mapCanvas.width / 2;
        const centerY = mapCanvas.height / 2;
        const radius = Math.min(centerX, centerY) - 10;

        mapCtx.strokeStyle = "rgba(0, 255, 65, 0.3)";
        mapCtx.lineWidth = 1;
        mapCtx.beginPath();
        mapCtx.arc(centerX, centerY, radius, 0, Math.PI * 2);
        mapCtx.arc(centerX, centerY, radius * 0.6, 0, Math.PI * 2);
        mapCtx.arc(centerX, centerY, radius * 0.3, 0, Math.PI * 2);
        mapCtx.stroke();

        mapCtx.strokeStyle = "#00ff41";
        mapCtx.beginPath();
        mapCtx.moveTo(centerX, centerY);
        mapCtx.lineTo(centerX + Math.cos(radarAngle) * radius, centerY + Math.sin(radarAngle) * radius);
        mapCtx.stroke();

        mapCtx.fillStyle = "#00ff41";
        mapCtx.fillRect(centerX + 40, centerY - 30, 4, 4);
        mapCtx.fillRect(centerX - 70, centerY + 20, 4, 4);
        mapCtx.fillRect(centerX + 90, centerY + 40, 4, 4);

        radarAngle += 0.05;
    }
    setInterval(drawRadar, 50);

    // --- SIMULAÇÃO DE LOGS DOS MÓDULOS UNIFICADOS ---
    function appendLog(text) {
        const log = document.getElementById('log');
        log.innerHTML += "\n> " + text;
        log.scrollTop = log.scrollHeight;
    }

    function executePythonAuth() {
        const email = document.getElementById('email').value;
        appendLog(`[PYTHON BACKEND] Conectando ao banco SQLite (global_security.db)...`);
        appendLog(`[PYTHON BACKEND] Autenticando E-mail: ${email}`);
        setTimeout(() => {
            appendLog(`[PYTHON BACKEND] SHA-256 gerado com sucesso.`);
            appendLog(`[TOR GATEWAY] Conexão socks5h://127.0.0.1:9050 estabelecida.`);
            document.getElementById('sat-status').innerText = "ONLINE (SINCRO)";
        }, 500);
    }

    function runCppScan() {
        appendLog(`[C++ HARDWARE] Escaneando frequências RF e redes Wi-Fi...`);
        setTimeout(() => {
            appendLog(`[C++ HARDWARE] Criptografia AES-NI ativada no barramento.`);
            appendLog(`[C++ HARDWARE] Sincronização de Relógio Atômico (Satélite) OK.`);
        }, 500);
    }

    function runGoWorkers() {
        appendLog(`[GO NETWORK] Inicializando Goroutines concorrentes...`);
        const nodes = ["192.168.1.1", "Satellite_IP", "Database_Global"];
        nodes.forEach((node, idx) => {
            setTimeout(() => {
                appendLog(`[GO WORKER #${idx+1}] Monitorando tráfego de rede para: ${node}`);
            }, 300 * (idx + 1));
        });
    }

    function runBashSecurity() {
        appendLog(`[BASH SECURITY] Configurando regras de Firewall (iptables)...`);
        setTimeout(() => {
            appendLog(`[BASH SECURITY] Porta 22 aceita. Verificando sha256sum da base de dados...`);
            appendLog(`[BASH SECURITY] Sistema operacional de segurança pronto.`);
        }, 500);
    }
</script>

</body>
</html>
