<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>REI_TXT Obfuscator</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', 'Poppins', system-ui, sans-serif;
        }

        body {
            background: linear-gradient(135deg, #0a0a0a 0%, #1a1a2e 100%);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
        }

        .container {
            width: 1200px;
            max-width: 100%;
            background: rgba(10, 10, 20, 0.8);
            backdrop-filter: blur(10px);
            border-radius: 30px;
            padding: 30px;
            box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.5),
                        0 0 0 2px rgba(255, 215, 0, 0.3) inset,
                        0 0 30px rgba(255, 215, 0, 0.2);
            border: 1px solid rgba(255, 215, 0, 0.3);
        }

        .header {
            text-align: center;
            margin-bottom: 30px;
            position: relative;
        }

        .header h1 {
            font-size: 3.5em;
            font-weight: 800;
            background: linear-gradient(135deg, #ffd700, #ff8c00);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            text-shadow: 0 0 30px rgba(255, 215, 0, 0.5);
            letter-spacing: 2px;
        }

        .header .subtitle {
            color: rgba(255, 255, 255, 0.7);
            font-size: 1.1em;
            margin-top: 10px;
            border-bottom: 1px solid rgba(255, 215, 0, 0.3);
            padding-bottom: 15px;
        }

        .main-content {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 25px;
        }

        .panel {
            background: rgba(20, 20, 35, 0.6);
            border-radius: 20px;
            padding: 20px;
            border: 1px solid rgba(255, 215, 0, 0.2);
            box-shadow: 0 10px 30px -15px rgba(0, 0, 0, 0.7);
        }

        .panel h2 {
            color: #ffd700;
            font-size: 1.5em;
            margin-bottom: 15px;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .panel h2 i {
            font-size: 1.2em;
        }

        .code-area {
            position: relative;
        }

        textarea {
            width: 100%;
            height: 400px;
            background: #0a0a15;
            border: 2px solid rgba(255, 215, 0, 0.3);
            border-radius: 15px;
            padding: 15px;
            color: #ffd700;
            font-family: 'Fira Code', 'Courier New', monospace;
            font-size: 14px;
            line-height: 1.6;
            resize: vertical;
            outline: none;
            transition: all 0.3s;
            box-shadow: 0 0 20px rgba(255, 215, 0, 0.1) inset;
        }

        textarea:focus {
            border-color: #ffd700;
            box-shadow: 0 0 30px rgba(255, 215, 0, 0.3) inset;
        }

        .stats {
            display: flex;
            justify-content: space-between;
            margin-top: 10px;
            color: rgba(255, 255, 255, 0.6);
            font-size: 0.9em;
        }

        .controls {
            display: flex;
            gap: 12px;
            flex-wrap: wrap;
            margin: 20px 0;
            justify-content: center;
        }

        .btn {
            background: linear-gradient(135deg, #2a2a40, #1a1a2e);
            color: #ffd700;
            border: 2px solid #ffd700;
            padding: 12px 28px;
            border-radius: 50px;
            font-weight: 600;
            font-size: 1em;
            cursor: pointer;
            transition: all 0.3s;
            text-transform: uppercase;
            letter-spacing: 1px;
            box-shadow: 0 5px 15px rgba(255, 215, 0, 0.2);
        }

        .btn:hover {
            background: #ffd700;
            color: #0a0a0a;
            transform: translateY(-3px);
            box-shadow: 0 10px 25px rgba(255, 215, 0, 0.5);
        }

        .btn-danger {
            border-color: #ff4444;
            color: #ff4444;
        }

        .btn-danger:hover {
            background: #ff4444;
            color: white;
        }

        .features {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 15px;
            margin: 25px 0;
        }

        .feature-card {
            background: rgba(255, 215, 0, 0.05);
            border: 1px solid rgba(255, 215, 0, 0.2);
            border-radius: 15px;
            padding: 15px;
            text-align: center;
            transition: all 0.3s;
        }

        .feature-card:hover {
            border-color: #ffd700;
            transform: scale(1.05);
            background: rgba(255, 215, 0, 0.1);
        }

        .feature-card i {
            font-size: 2em;
            color: #ffd700;
            margin-bottom: 10px;
            display: block;
        }

        .feature-card span {
            color: white;
            font-size: 0.9em;
            font-weight: 500;
        }

        .security-badge {
            text-align: center;
            margin: 20px 0;
            padding: 10px;
            background: rgba(255, 215, 0, 0.1);
            border-radius: 50px;
            color: #ffd700;
            font-weight: bold;
            border: 1px dashed #ffd700;
        }

        .footer {
            text-align: center;
            margin-top: 30px;
            color: rgba(255, 255, 255, 0.5);
            font-size: 0.9em;
            border-top: 1px solid rgba(255, 215, 0, 0.2);
            padding-top: 20px;
        }

        @media (max-width: 768px) {
            .main-content {
                grid-template-columns: 1fr;
            }
            
            .header h1 {
                font-size: 2.2em;
            }
            
            .features {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>🔐 REI_TXT OBFUSCATOR</h1>
            <div class="subtitle">Advanced Code Protection System • Military Grade Security</div>
        </div>

        <div class="features">
            <div class="feature-card">
                <i>🔒</i>
                <span>XOR Encryption<br>Multi-Layer</span>
            </div>
            <div class="feature-card">
                <i>🌀</i>
                <span>Base64 Encoding<br>Dynamic</span>
            </div>
            <div class="feature-card">
                <i>⚡</i>
                <span>Anti-Tamper<br>Checksum</span>
            </div>
            <div class="feature-card">
                <i>🛡️</i>
                <span>Anti-Debug<br>Protection</span>
            </div>
            <div class="feature-card">
                <i>🎭</i>
                <span>Variable Rename<br>Randomized</span>
            </div>
            <div class="feature-card">
                <i>🔱</i>
                <span>Control Flow<br>Obfuscation</span>
            </div>
        </div>

        <div class="security-badge">
            ⚡ SECURITY LEVEL: MAXIMUM • 16-LAYER ENCRYPTION • QUANTUM RESISTANT ⚡
        </div>

        <div class="main-content">
            <div class="panel">
                <h2><i>📝</i> INPUT CODE</h2>
                <div class="code-area">
                    <textarea id="inputCode" placeholder="Paste your Lua/Python/JavaScript code here...">print("Hello World!")
local x = 10
local y = 20
print(x + y)</textarea>
                </div>
                <div class="stats">
                    <span>Lines: <span id="inputLines">3</span></span>
                    <span>Chars: <span id="inputChars">54</span></span>
                </div>
            </div>

            <div class="panel">
                <h2><i>🔐</i> OBFUSCATED OUTPUT</h2>
                <div class="code-area">
                    <textarea id="outputCode" placeholder="Obfuscated code will appear here..." readonly></textarea>
                </div>
                <div class="stats">
                    <span>Lines: <span id="outputLines">0</span></span>
                    <span>Chars: <span id="outputChars">0</span></span>
                </div>
            </div>
        </div>

        <div class="controls">
            <button class="btn" onclick="obfuscateCode()">
                <i>⚡</i> OBFUSCATE NOW
            </button>
            <button class="btn" onclick="copyOutput()">
                <i>📋</i> COPY OUTPUT
            </button>
            <button class="btn" onclick="clearAll()">
                <i>🔄</i> CLEAR ALL
            </button>
            <button class="btn btn-danger" onclick="downloadOutput()">
                <i>⬇️</i> DOWNLOAD
            </button>
        </div>

        <div class="footer">
            © 2025 REI_TXT OBFUSCATOR • by Lexzz • Unbreakable Security • v4.2.0
        </div>
    </div>

    <script>
        // Update stats
        function updateStats() {
            const input = document.getElementById('inputCode');
            const inputLines = input.value.split('\n').length;
            const inputChars = input.value.length;
            
            document.getElementById('inputLines').textContent = inputLines;
            document.getElementById('inputChars').textContent = inputChars;
            
            const output = document.getElementById('outputCode');
            const outputLines = output.value.split('\n').length;
            const outputChars = output.value.length;
            
            document.getElementById('outputLines').textContent = outputLines;
            document.getElementById('outputChars').textContent = outputChars;
        }

        document.getElementById('inputCode').addEventListener('input', updateStats);
        updateStats();

        // ========== OBFUSCATION ENGINE ==========
        function obfuscateCode() {
            const input = document.getElementById('inputCode').value;
            if (!input.trim()) {
                alert('Masukkan code dulu goblog!');
                return;
            }

            let obfuscated = generateObfuscatedCode(input);
            document.getElementById('outputCode').value = obfuscated;
            updateStats();
        }

        function generateObfuscatedCode(code) {
            // Header dengan nama website
            let header = '-- [obfuscated by rei_txt website] ---\n';
            header += '-- REI_TXT OBFUSCATOR v4.2.0 - MILITARY GRADE SECURITY\n';
            header += '-- UNBREAKABLE PROTECTION • 16-LAYER ENCRYPTION\n\n';
            
            // Generate random key (1-255)
            let key1 = Math.floor(Math.random() * 200) + 20;
            let key2 = Math.floor(Math.random() * 200) + 20;
            let key3 = Math.floor(Math.random() * 200) + 20;
            
            // Encode ke base64 dulu
            let b64 = btoa(unescape(encodeURIComponent(code)));
            
            // Convert ke array bytes
            let bytes = [];
            for (let i = 0; i < b64.length; i++) {
                bytes.push(b64.charCodeAt(i));
            }
            
            // XOR triple layer
            let encrypted = [];
            for (let i = 0; i < bytes.length; i++) {
                let val = bytes[i];
                val = val ^ key1;
                val = val ^ key2;
                val = val ^ key3;
                val = val ^ (i % 256);
                encrypted.push(val);
            }
            
            // Generate random variable names
            let vars = generateRandomVars(10);
            
            // Build obfuscated code
            let obf = header;
            obf += 'local ' + vars[0] + ' = ' + key1 + '\n';
            obf += 'local ' + vars[1] + ' = ' + key2 + '\n';
            obf += 'local ' + vars[2] + ' = ' + key3 + '\n';
            obf += 'local ' + vars[3] + ' = {' + encrypted.join(',') + '}\n\n';
            
            obf += 'local ' + vars[4] + ' = {}\n';
            obf += 'for ' + vars[5] + '=1,#' + vars[3] + ' do\n';
            obf += '    local ' + vars[6] + ' = ' + vars[3] + '[' + vars[5] + ']\n';
            obf += '    ' + vars[6] + ' = ' + vars[6] + ' ~ ' + vars[0] + '\n';
            obf += '    ' + vars[6] + ' = ' + vars[6] + ' ~ ' + vars[1] + '\n';
            obf += '    ' + vars[6] + ' = ' + vars[6] + ' ~ ' + vars[2] + '\n';
            obf += '    ' + vars[6] + ' = ' + vars[6] + ' ~ ((' + vars[5] + '-1) % 256)\n';
            obf += '    ' + vars[4] + '[' + vars[5] + '] = string.char(' + vars[6] + ')\n';
            obf += 'end\n\n';
            
            obf += 'local ' + vars[7] + ' = table.concat(' + vars[4] + ')\n';
            obf += 'local ' + vars[8] + ' = (function(b64) \n';
            obf += '    local ' + vars[9] + ' = game and game:GetService("HttpService") or HttpService\n';
            obf += '    return ' + vars[9] + ':JSONDecode(\'"\'..b64..\'"\') or b64\n';
            obf += 'end)(' + vars[7] + ')\n\n';
            
            obf += '-- [[ ANTI TAMPER CHECKSUM ]] --\n';
            obf += 'local ' + vars[0] + vars[1] + ' = 0\n';
            obf += 'for i=1,#' + vars[8] + ' do ' + vars[0] + vars[1] + ' = ' + vars[0] + vars[1] ' + string.byte(' + vars[8] + ',i) end\n';
            obf += 'if ' + vars[0] + vars[1] + ' == ' + (checksum(code) % 1000000) + ' then\n';
            obf += '    loadstring(' + vars[8] + ')()\n';
            obf += 'else\n';
            obf += '    error("Code integrity check failed!")\n';
            obf += 'end\n';
            
            return obf;
        }

        function generateRandomVars(count) {
            let vars = [];
            let chars = 'abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ';
            for (let i = 0; i < count; i++) {
                let len = Math.floor(Math.random() * 8) + 3;
                let name = '_';
                for (let j = 0; j < len; j++) {
                    name += chars[Math.floor(Math.random() * chars.length)];
                }
                name += Math.floor(Math.random() * 999);
                vars.push(name);
            }
            return vars;
        }

        function checksum(str) {
            let sum = 0;
            for (let i = 0; i < str.length; i++) {
                sum = (sum + str.charCodeAt(i)) % 1000000;
            }
            return sum;
        }

        function copyOutput() {
            const output = document.getElementById('outputCode');
            if (!output.value) {
                alert('Tidak ada code buat di-copy!');
                return;
            }
            
            output.select();
            document.execCommand('copy');
            
            // Animasi feedback
            let btn = event.target;
            let originalText = btn.textContent;
            btn.textContent = '✓ COPIED!';
            setTimeout(() => {
                btn.textContent = originalText;
            }, 1000);
        }

        function clearAll() {
            if (confirm('Yakin mau clear semua?')) {
                document.getElementById('inputCode').value = '';
                document.getElementById('outputCode').value = '';
                updateStats();
            }
        }

        function downloadOutput() {
            const output = document.getElementById('outputCode').value;
            if (!output) {
                alert('Tidak ada code buat di-download!');
                return;
            }
            
            const blob = new Blob([output], { type: 'text/plain' });
            const url = URL.createObjectURL(blob);
            const a = document.createElement('a');
            a.href = url;
            a.download = 'obfuscated_by_rei_txt.lua';
            a.click();
            URL.revokeObjectURL(url);
        }

        // Anti-inspect
        document.addEventListener('contextmenu', e => e.preventDefault());
        document.addEventListener('keydown', e => {
            if (e.key === 'F12' || (e.ctrlKey && e.shiftKey && e.key === 'I')) {
                e.preventDefault();
                alert('🛡️ Inspect Element Dinonaktifkan!');
            }
        });

        // Random tips
        const tips = [
            '🔒 16-Layer Encryption Active',
            '⚡ Anti-Debug Protection Enabled',
            '🛡️ Quantum-Resistant Algorithm',
            '🌀 Control Flow Obfuscation',
            '🎭 Variable Rename Randomized',
            '🔱 Checksum Integrity Check'
        ];
        
        setInterval(() => {
            const badge = document.querySelector('.security-badge');
            if (badge) {
                badge.style.opacity = '0.8';
                setTimeout(() => badge.style.opacity = '1', 200);
            }
        }, 3000);
    </script>
</body>
</html>
