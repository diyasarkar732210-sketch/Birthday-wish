# Index-HTML-20
My web
<!DOCTYPE html>
<html lang="bn">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Happy Birthday  ❤️</title>
    
    <!-- Google Fonts & FontAwesome Icons -->
    <link href="https://fonts.googleapis.com/css2?family=Hind+Siliguri:wght@300;400;600;700&family=Great+Vibes&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <!-- Canvas Confetti Library -->
    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>

    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Hind Siliguri', sans-serif;
        }

        body {
            min-height: 100vh;
            background: linear-gradient(135deg, #0f051d 0%, #290a38 50%, #4a0e4e 100%);
            color: #ffffff;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            overflow-x: hidden;
            position: relative;
            padding: 20px 15px;
        }

        /* Floating Background Hearts */
        .heart-bg {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 1;
            overflow: hidden;
        }

        .floating-heart {
            position: absolute;
            color: rgba(255, 105, 180, 0.3);
            animation: floatUp 8s linear infinite;
            bottom: -50px;
        }

        @keyframes floatUp {
            0% { transform: translateY(0) scale(0.8) rotate(0deg); opacity: 0; }
            20% { opacity: 0.8; }
            100% { transform: translateY(-110vh) scale(1.3) rotate(360deg); opacity: 0; }
        }

        /* Container Styling for Pages */
        .container {
            width: 100%;
            max-width: 480px;
            margin: auto;
            text-align: center;
            z-index: 10;
            padding: 25px 20px;
            background: rgba(255, 255, 255, 0.08);
            backdrop-filter: blur(18px);
            -webkit-backdrop-filter: blur(18px);
            border-radius: 25px;
            border: 1px solid rgba(255, 255, 255, 0.18);
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.6), 0 0 25px rgba(255, 105, 180, 0.25);
            animation: fadeIn 0.8s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        }

        .hidden {
            display: none !important;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(30px) scale(0.95); }
            to { opacity: 1; transform: translateY(0) scale(1); }
        }

        .badge {
            display: inline-block;
            padding: 6px 16px;
            background: rgba(255, 105, 180, 0.25);
            border: 1px solid rgba(255, 105, 180, 0.5);
            border-radius: 50px;
            font-size: 0.9rem;
            color: #ffb6c1;
            margin-bottom: 12px;
            letter-spacing: 1px;
        }

        .main-title {
            font-size: 2.1rem;
            font-weight: 700;
            background: linear-gradient(45deg, #ff9a9e, #fecfef, #fe9a8b);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            margin-bottom: 5px;
        }

        .romantic-sub {
            font-family: 'Great Vibes', cursive;
            font-size: 2.7rem;
            color: #ff758c;
            margin-bottom: 15px;
            text-shadow: 0 0 12px rgba(255, 117, 140, 0.6);
        }

        /* Photo Frame Styling */
        .photo-box {
            width: 100%;
            height: 260px;
            border-radius: 18px;
            overflow: hidden;
            margin-bottom: 15px;
            border: 2px solid rgba(255, 182, 193, 0.4);
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.4);
            position: relative;
            background: rgba(0, 0, 0, 0.3);
        }

        .photo-box img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.5s ease;
        }

        .photo-box:hover img {
            transform: scale(1.05);
        }

        .wishes-card {
            background: rgba(0, 0, 0, 0.25);
            padding: 18px;
            border-radius: 15px;
            border-left: 3px solid #ff758c;
            margin-bottom: 15px;
            text-align: left;
        }

        .wish-line {
            font-size: 1.05rem;
            line-height: 1.7;
            color: #f1f1f1;
            font-weight: 300;
        }

        .highlight {
            color: #ff9a9e;
            font-weight: 600;
        }

        /* Forward Only Button */
        .btn-next-only {
            width: 100%;
            padding: 16px 20px;
            background: linear-gradient(45deg, #ff416c, #ff4b2b);
            border: none;
            border-radius: 50px;
            color: white;
            font-size: 1.1rem;
            font-weight: 600;
            cursor: pointer;
            box-shadow: 0 8px 25px rgba(255, 65, 108, 0.5);
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 12px;
            transition: all 0.3s ease;
            margin-top: 10px;
        }

        .btn-next-only:hover:not(:disabled) {
            transform: translateY(-2px);
            box-shadow: 0 10px 30px rgba(255, 65, 108, 0.7);
        }

        /* Disabled State for 5s Timer */
        .btn-next-only:disabled {
            background: rgba(255, 255, 255, 0.2);
            box-shadow: none;
            cursor: not-allowed;
            color: rgba(255, 255, 255, 0.6);
        }

        .page-indicator {
            font-size: 0.85rem;
            color: #ffb6c1;
            margin-top: 12px;
            display: block;
            opacity: 0.8;
        }
    </style>
</head>
<body>

    <!-- Background Floating Hearts -->
    <div class="heart-bg" id="heartContainer"></div>

    <!-- PAGE 1: Welcome & Start -->
    <div class="container page" id="page1">
        <span class="badge">❤️ শুভ জন্মদিন প্রিয় ❤️</span>
        <h1 class="main-title">Happy Birthday</h1>
        <div class="romantic-sub">Myra</div>

        <div class="wishes-card">
            <p class="wish-line">
                ✨ তোমার জীবনের এই বিশেষ দিনে আমি শুধু একটাই কথা বলতে চাই— তুমি আমার জীবনের সবচেয়ে সুন্দর উপহার।
            </p>
            <p class="wish-line" style="margin-top: 10px;">
                💖 <span class="highlight">তুমি পাশে থাকলে মনে হয় পুরো পৃথিবীটাই আমার।</span> আজকের এই দিনটি তোমার জন্য অনেক আনন্দময় হোক!
            </p>
        </div>

        <button class="btn-next-only" id="btn-page1" disabled onclick="startExperience()">
            <i class="fa-solid fa-clock"></i>
            <span class="btn-text">Wait 5s... ✨</span>
        </button>
        <span class="page-indicator">Page 1 of 5</span>
    </div>

    <!-- PAGE 2: Photo 1 -->
    <div class="container page hidden" id="page2">
        <span class="badge">✨ প্রথম মিষ্টি স্মৃতি</span>
        <h2 class="main-title">Sweet Moments</h2>
        
        <!-- Photo 1 Location -->
        <div class="photo-box">
            <img src="https://files.catbox.moe/4pvjsx.jpg" alt="Myra">
        </div>

        <div class="wishes-card">
            <p class="wish-line">
                🌹 তোমার এই সুন্দর হাসিটা যেন জীবনের প্রতিটি পদক্ষেপে এমনভাবেই অটুট থাকে।
            </p>
        </div>

        <button class="btn-next-only" id="btn-page2" disabled onclick="nextPage(3)">
            <i class="fa-solid fa-clock"></i>
            <span class="btn-text">Wait 5s... ❤️</span>
        </button>
        <span class="page-indicator">Page 2 of 5</span>
    </div>

    <!-- PAGE 3: Photo 2 -->
    <div class="container page hidden" id="page3">
        <span class="badge">💖 আমার জীবনের আলো</span>
        <h2 class="main-title">You & Me</h2>
        
        <!-- Photo 2 Location -->
        <div class="photo-box">
            <img src="https://files.catbox.moe/b6lr3t.jpg" alt="Myra">
        </div>

        <div class="wishes-card">
            <p class="wish-line">
                ✨ তোমার সাথে কাটানো প্রতিটি মুহূর্ত আমার কাছে সবথেকে মূল্যবান ধন।
            </p>
        </div>

        <button class="btn-next-only" id="btn-page3" disabled onclick="nextPage(4)">
            <i class="fa-solid fa-clock"></i>
            <span class="btn-text">Wait 5s... ✨</span>
        </button>
        <span class="page-indicator">Page 3 of 5</span>
    </div>

    <!-- PAGE 4: Photo 3 -->
    <div class="container page hidden" id="page4">
        <span class="badge">🌸 চিরকালের ভালোবাসা</span>
        <h2 class="main-title">Precious Memory</h2>
        
        <!-- Photo 3 Location -->
        <div class="photo-box">
            <img src="https://files.catbox.moe/t1p5kl.jpg" alt="Myra">
        </div>

        <div class="wishes-card">
            <p class="wish-line">
                💖 ঈশ্বর যেন তোমার জীবনের সমস্ত চাওয়া পূরণ করেন এবং তোমাকে সব সুখে রাখেন।
            </p>
        </div>

        <button class="btn-next-only" id="btn-page4" disabled onclick="nextPage(5)">
            <i class="fa-solid fa-clock"></i>
            <span class="btn-text">Wait 5s... 🎁</span>
        </button>
        <span class="page-indicator">Page 4 of 5</span>
    </div>

    <!-- PAGE 5: Final Wish -->
    <div class="container page hidden" id="page5">
        <span class="badge">🎉 শুভ জন্মদিন মাইরা 🎉</span>
        <h1 class="main-title">Forever & Always</h1>
        <div class="romantic-sub">I Love You ❤️</div>

        <div class="wishes-card" style="text-align: center;">
            <p class="wish-line">
                আজকের দিনটি তোমার মতোই সুন্দর এবং স্পেশাল হোক! <br>
                <span class="highlight">Happy Birthday My Love! 🎂✨</span>
            </p>
        </div>

        <button class="btn-next-only" id="btn-page5" disabled onclick="triggerConfetti()">
            <i class="fa-solid fa-clock"></i>
            <span class="btn-text">Wait 5s... ❤️</span>
        </button>
        <span class="page-indicator">Page 5 of 5</span>
    </div>

    <!-- Background Music Audio -->
    <audio id="bgMusic" loop preload="auto">
  <source src="https://files.catbox.moe/a6wf9z.m4a" type="audio/mp4">
</audio>


    <script>
        // Background Floating Hearts Effect
        function createHearts() {
            const container = document.getElementById('heartContainer');
            const heartIcons = ['❤️', '💖', '💕', '💗', '✨'];
            
            for (let i = 0; i < 22; i++) {
                const heart = document.createElement('div');
                heart.className = 'floating-heart';
                heart.innerHTML = heartIcons[Math.floor(Math.random() * heartIcons.length)];
                heart.style.left = Math.random() * 100 + 'vw';
                heart.style.animationDuration = (Math.random() * 5 + 5) + 's';
                heart.style.animationDelay = (Math.random() * 5) + 's';
                heart.style.fontSize = (Math.random() * 15 + 15) + 'px';
                container.appendChild(heart);
            }
        }

        let musicStarted = false;
        let timerInterval;

        // Button Timer Function (5 Seconds Delay)
        function enableButtonWithTimer(pageNumber, activeText, iconClass) {
            let timeLeft = 5;
            const btn = document.getElementById('btn-page' + pageNumber);
            if (!btn) return;

            const btnText = btn.querySelector('.btn-text');
            const btnIcon = btn.querySelector('i');

            btn.disabled = true;
            btnIcon.className = 'fa-solid fa-clock';
            btnText.innerHTML = `Wait ${timeLeft}s... ✨`;

            clearInterval(timerInterval);

            timerInterval = setInterval(() => {
                timeLeft--;
                if (timeLeft > 0) {
                    btnText.innerHTML = `Wait ${timeLeft}s... ✨`;
                } else {
                    clearInterval(timerInterval);
                    btn.disabled = false;
                    btnIcon.className = iconClass;
                    btnText.innerHTML = activeText;
                }
            }, 1000);
        }

        // Start Experience on First Click
        function startExperience() {
            const music = document.getElementById('bgMusic');

            if (!musicStarted) {
                music.play().then(() => {
                    musicStarted = true;
                }).catch(error => {
                    console.log("Audio playback error: ", error);
                });
            }
            triggerConfetti();
            nextPage(2);
        }

        // Forward Only Page Navigation with Timer Init
        function nextPage(targetPageNumber) {
            const pages = document.querySelectorAll('.page');
            pages.forEach(p => p.classList.add('hidden'));

            const targetPage = document.getElementById('page' + targetPageNumber);
            if (targetPage) {
                targetPage.classList.remove('hidden');
                
                // Initialize timer for the newly visible page
                if (targetPageNumber === 2) {
                    enableButtonWithTimer(2, 'Next Surprise ❤️', 'fa-solid fa-arrow-right');
                } else if (targetPageNumber === 3) {
                    enableButtonWithTimer(3, 'Keep Going ✨', 'fa-solid fa-arrow-right');
                } else if (targetPageNumber === 4) {
                    enableButtonWithTimer(4, 'Final Gift 🎁', 'fa-solid fa-arrow-right');
                } else if (targetPageNumber === 5) {
                    enableButtonWithTimer(5, 'Celebrate Again ❤️', 'fa-solid fa-heart');
                }
            }
            triggerConfetti();
        }

        // Fireworks/Confetti Effect
        function triggerConfetti() {
            var count = 180;
            var defaults = { origin: { y: 0.8 } };

            function fire(particleRatio, opts) {
                confetti(Object.assign({}, defaults, opts, {
                    particleCount: Math.floor(count * particleRatio)
                }));
            }

            fire(0.25, { spread: 26, startVelocity: 55, colors: ['#ff0000', '#ffa500'] });
            fire(0.2, { spread: 60, colors: ['#ffffff', '#ff69b4'] });
            fire(0.35, { spread: 100, decay: 0.91, scalar: 0.8 });
            fire(0.1, { spread: 120, startVelocity: 25, decay: 0.92, colors: ['#e60073', '#ff3399'] });
            fire(0.1, { spread: 120, startVelocity: 45 });
        }

        window.onload = function() {
            createHearts();
            // Start timer for the first page
            enableButtonWithTimer(1, 'Tap to Continue ✨', 'fa-solid fa-music');
        };
    </script>
</body>
</html>
