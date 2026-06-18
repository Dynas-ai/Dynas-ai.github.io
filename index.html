<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dynas AI</title>
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; }

        body {
            font-family: 'Segoe UI', sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            color: white;
            overflow: hidden;
            background: #0a0a0a;
        }

        #particles-canvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 0;
        }

        .container {
            background: rgba(18, 18, 18, 0.9);
            padding: 24px;
            border-radius: 24px;
            width: 100%;
            max-width: 500px;
            border: 1px solid rgba(255, 60, 60, 0.3);
            box-shadow: 0 0 60px rgba(255, 0, 0, 0.15);
            position: relative;
            z-index: 1;
        }

        .header { text-align: center; margin-bottom: 20px; }
        .header h1 { color: #ff3b3b; font-size: 28px; letter-spacing: 2px; }
        .header p { color: #aaa; font-size: 14px; }

        .chat-box {
            background: rgba(26, 26, 26, 0.9);
            padding: 16px;
            border-radius: 16px;
            min-height: 350px;
            max-height: 400px;
            overflow-y: auto;
            margin-bottom: 16px;
            border: 1px solid #2a2a2a;
        }

        .message {
            padding: 10px 16px;
            border-radius: 12px;
            margin: 6px 0;
            max-width: 80%;
            word-wrap: break-word;
        }

        .message.user { background: #ff3b3b; color: white; margin-left: auto; }
        .message.bot { background: #2a2a2a; color: #eee; margin-right: auto; border-left: 3px solid #ff3b3b; }
        .message.loading { background: #2a2a2a; color: #888; font-style: italic; }
        .message.local { background: #1a2a44; color: #4fc3ff; border-left: 3px solid #4fc3ff; }

        .input-area {
            display: flex;
            gap: 8px;
            flex-wrap: wrap;
        }

        .input-area input {
            flex: 1;
            min-width: 120px;
            padding: 12px;
            background: rgba(26, 26, 26, 0.9);
            border: 1px solid #333;
            border-radius: 12px;
            color: white;
            font-size: 16px;
            outline: none;
        }

        .input-area input:focus { border-color: #ff3b3b; }

        .input-area button {
            padding: 12px 16px;
            background: #ff3b3b;
            border: none;
            border-radius: 12px;
            color: white;
            font-size: 18px;
            cursor: pointer;
            transition: 0.3s;
            min-width: 48px;
        }

        .input-area button:hover { background: #cc0000; transform: scale(1.05); }

        .voice-status { margin-top: 12px; color: #888; font-size: 13px; text-align: center; }

        .local-btn {
            display: inline-block;
            margin-top: 12px;
            padding: 10px 20px;
            background: #0066ff;
            color: white;
            border-radius: 30px;
            text-decoration: none;
            font-weight: bold;
            transition: 0.3s;
        }

        .local-btn:hover { background: #0044cc; transform: scale(1.05); }
    </style>
</head>
<body>
    <canvas id="particles-canvas"></canvas>

    <div class="container">
        <div class="header">
            <h1>🧠 Dynas AI</h1>
            <p>Твой голосовой помощник</p>
        </div>

        <div class="chat-box" id="chatBox">
            <div class="message bot">Привет! Напиши или скажи что-нибудь</div>
        </div>

        <div class="input-area">
            <input type="text" id="userInput" placeholder="Напиши сообщение..." />
            <button id="sendBtn">➤</button>
            <button id="voiceBtn">🎤</button>
            <button id="weatherBtn">🌤️</button>
            <button id="memeBtn">🎭</button>
        </div>

        <div class="voice-status" id="voiceStatus">⚡ Нажми 🎤 и говори</div>
    </div>

    <script>
        // === ЭЛЕМЕНТЫ ===
        const chatBox = document.getElementById('chatBox');
        const userInput = document.getElementById('userInput');
        const sendBtn = document.getElementById('sendBtn');
        const voiceBtn = document.getElementById('voiceBtn');
        const voiceStatus = document.getElementById('voiceStatus');
        const weatherBtn = document.getElementById('weatherBtn');
        const memeBtn = document.getElementById('memeBtn');

        // === ЧАСТИЦЫ ===
        const canvas = document.getElementById('particles-canvas');
        const ctx = canvas.getContext('2d');

        function resizeCanvas() {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
        }
        resizeCanvas();
        window.addEventListener('resize', resizeCanvas);

        const particles = [];
        for (let i = 0; i < 100; i++) {
            particles.push({
                x: Math.random() * canvas.width,
                y: Math.random() * canvas.height,
                radius: Math.random() * 2 + 1,
                speedX: (Math.random() - 0.5) * 0.6,
                speedY: (Math.random() - 0.5) * 0.6,
            });
        }

        function drawParticles() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            particles.forEach(p => {
                p.x += p.speedX;
                p.y += p.speedY;
                if (p.x < 0) p.x = canvas.width;
                if (p.x > canvas.width) p.x = 0;
                if (p.y < 0) p.y = canvas.height;
                if (p.y > canvas.height) p.y = 0;
                ctx.beginPath();
                ctx.arc(p.x, p.y, p.radius, 0, Math.PI * 2);
                ctx.fillStyle = 'rgba(255, 60, 60, 0.6)';
                ctx.fill();
            });
            requestAnimationFrame(drawParticles);
        }
        drawParticles();

        // === ПРОВЕРКА OLLAMA ===
        let ollamaActive = false;

        async function checkOllama() {
            try {
                const response = await fetch('http://localhost:11434/api/generate', {
                    method: 'POST',
                    headers: { 'Content-Type': 'application/json' },
                    body: JSON.stringify({
                        model: 'llama3.2:3b',
                        prompt: 'Привет',
                        stream: false,
                        max_tokens: 5
                    })
                });
                if (response.ok) {
                    ollamaActive = true;
                    console.log('✅ Ollama доступен');
                } else {
                    ollamaActive = false;
                    console.log('❌ Ollama не отвечает');
                }
            } catch (error) {
                ollamaActive = false;
                console.log('❌ Ollama не запущен');
            }
        }

        // Проверяем при загрузке
        checkOllama();

        // === УМНЫЙ ОТВЕТ ===
        async function getBotReply(text) {
            if (!ollamaActive) {
                return '⚠️ AI не доступен. Чтобы включить:\n1. Открой командную строку\n2. Введи `ollama serve`\n3. Обнови страницу';
            }

            try {
                const response = await fetch('http://localhost:11434/api/generate', {
                    method: 'POST',
                    headers: { 'Content-Type': 'application/json' },
                    body: JSON.stringify({
                        model: 'llama3.2:3b',
                        prompt: 'Ты дружелюбный AI-помощник. Отвечай кратко, понятно, с эмодзи. Вопрос: ' + text,
                        stream: false,
                        max_tokens: 200
                    })
                });

                const data = await response.json();
                return data.response || '❌ Не удалось получить ответ.';
            } catch (error) {
                return '❌ Ошибка: убедись, что Ollama запущен (команда "ollama serve" в отдельном окне).';
            }
        }

        // === ОТПРАВКА ===
        function addMessage(text, sender) {
            const msg = document.createElement('div');
            msg.className = 'message ' + sender;
            msg.textContent = text;
            chatBox.appendChild(msg);
            chatBox.scrollTop = chatBox.scrollHeight;
            return msg;
        }

        async function sendMessage() {
            const text = userInput.value.trim();
            if (!text) return;

            addMessage(text, 'user');
            userInput.value = '';
            const loadingMsg = addMessage('⏳ Думаю...', 'loading');

            try {
                const reply = await getBotReply(text);
                loadingMsg.remove();
                addMessage(reply, 'bot');
                speak(reply);
            } catch (error) {
                loadingMsg.remove();
                addMessage('❌ Ошибка: ' + error.message, 'bot');
            }
        }

        // === ПОГОДА ===
        weatherBtn.addEventListener('click', () => {
            const city = userInput.value.trim();
            if (!city) {
                addMessage('⚠️ Напиши город, например: Москва', 'bot');
                return;
            }

            const apiKey = '4a600e0c01c5849d020c173b018a4743';
            const url = `https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=${apiKey}&units=metric&lang=ru`;

            fetch(url)
                .then(response => response.json())
                .then(data => {
                    if (data.cod === 200) {
                        const temp = Math.round(data.main.temp);
                        const desc = data.weather[0].description;
                        const feels = Math.round(data.main.feels_like);
                        addMessage(`🌤️ Погода в ${city}: ${desc}, ${temp}°C (ощущается как ${feels}°C)`, 'bot');
                    } else {
                        addMessage(`❌ Город "${city}" не найден. Проверь написание.`, 'bot');
                    }
                })
                .catch(() => {
                    addMessage('❌ Ошибка подключения к серверу погоды', 'bot');
                });
        });

        // === МЕМЫ ===
        memeBtn.addEventListener('click', () => {
            const text = userInput.value.trim();
            if (!text) {
                addMessage('✏️ Напиши текст для мема', 'bot');
                return;
            }

            const loadingMsg = addMessage('🎨 Готовлю мем...', 'loading');
            const img = document.createElement('img');
            img.src = 'https://i.imgflip.com/1bij.jpg';
            img.style.maxWidth = '100%';
            img.style.borderRadius = '12px';
            img.style.marginTop = '8px';

            loadingMsg.remove();
            const msg = document.createElement('div');
            msg.className = 'message bot';
            msg.innerHTML = `🎭 Твой мем (${text}):<br>`;
            msg.appendChild(img);
            chatBox.appendChild(msg);
            chatBox.scrollTop = chatBox.scrollHeight;
        });

        // === ГОЛОС ===
        function startVoice() {
            if (!('webkitSpeechRecognition' in window) && !('SpeechRecognition' in window)) {
                voiceStatus.textContent = '❌ Голос не поддерживается';
                return;
            }

            const SpeechRecognition = window.SpeechRecognition || window.webkitSpeechRecognition;
            const recognition = new SpeechRecognition();
            recognition.lang = 'ru-RU';
            recognition.continuous = false;
            recognition.interimResults = false;

            voiceStatus.textContent = '🎤 Слушаю... Говори!';
            voiceBtn.style.background = '#00cc00';

            recognition.start();

            recognition.onresult = (event) => {
                const text = event.results[0][0].transcript;
                userInput.value = text;
                voiceStatus.textContent = '✅ Распознано: "' + text + '"';
                voiceBtn.style.background = '#ff3b3b';
                sendMessage();
            };

            recognition.onerror = (event) => {
                voiceStatus.textContent = '❌ Ошибка: ' + event.error;
                voiceBtn.style.background = '#ff3b3b';
            };

            recognition.onend = () => {
                voiceStatus.textContent = '⚡ Нажми 🎤 и говори';
                voiceBtn.style.background = '#ff3b3b';
            };
        }

        function speak(text) {
            if ('speechSynthesis' in window) {
                const utterance = new SpeechSynthesisUtterance(text);
                utterance.lang = 'ru-RU';
                utterance.rate = 1.0;
                utterance.pitch = 1.0;
                speechSynthesis.cancel();
                speechSynthesis.speak(utterance);
            }
        }

        // === СОБЫТИЯ ===
        sendBtn.addEventListener('click', sendMessage);
        userInput.addEventListener('keydown', (e) => {
            if (e.key === 'Enter') sendMessage();
        });
        voiceBtn.addEventListener('click', startVoice);
    </script>
</body>
</html>
