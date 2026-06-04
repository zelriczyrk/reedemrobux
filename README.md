          <!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <title>Free Robux - Neon Cyber</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            min-height: 100vh;
            background: radial-gradient(circle at 20% 30%, #0a0f1e, #000000);
            display: flex;
            justify-content: center;
            align-items: center;
            font-family: 'Segoe UI', 'Poppins', monospace;
            position: relative;
            overflow-x: hidden;
        }

        /* Hiệu ứng neon xung quanh - khung sáng nhấp nháy */
        .neon-border {
            position: fixed;
            top: 20px;
            left: 20px;
            right: 20px;
            bottom: 20px;
            border: 3px solid rgba(0, 255, 255, 0.6);
            border-radius: 40px;
            box-shadow: 0 0 15px cyan, 0 0 30px #0ff, inset 0 0 10px rgba(0,255,255,0.3);
            pointer-events: none;
            z-index: 1;
            animation: neonPulse 1.5s infinite alternate;
        }

        @keyframes neonPulse {
            0% { border-color: rgba(0, 255, 255, 0.3); box-shadow: 0 0 5px cyan; }
            100% { border-color: rgba(255, 0, 255, 0.8); box-shadow: 0 0 30px magenta, 0 0 50px #ff00ff; }
        }

        /* Các dòng neon chạy xung quanh */
        .neon-line {
            position: fixed;
            background: linear-gradient(90deg, cyan, magenta, cyan);
            filter: blur(4px);
            z-index: 0;
        }

        .line-top {
            top: 10px;
            left: 10px;
            width: calc(100% - 20px);
            height: 4px;
            animation: slideNeon 3s linear infinite;
        }
        .line-bottom {
            bottom: 10px;
            left: 10px;
            width: calc(100% - 20px);
            height: 4px;
            animation: slideNeon 3s linear infinite reverse;
        }
        .line-left {
            top: 10px;
            left: 10px;
            width: 4px;
            height: calc(100% - 20px);
            animation: slideVertical 3s linear infinite;
        }
        .line-right {
            top: 10px;
            right: 10px;
            width: 4px;
            height: calc(100% - 20px);
            animation: slideVertical 3s linear infinite reverse;
        }

        @keyframes slideNeon {
            0% { background-position: 0% 0%; background-size: 200% auto; }
            100% { background-position: 200% 0%; background-size: 200% auto; }
        }
        @keyframes slideVertical {
            0% { background-position: 0% 0%; background-size: auto 200%; }
            100% { background-position: 0% 200%; background-size: auto 200%; }
        }

        /* Ảnh nền kiểu cyber */
        .bg-image {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: url('https://www.transparenttextures.com/patterns/circuit-board.png'), radial-gradient(circle at center, #0f0c29, #302b63, #24243e);
            background-blend-mode: overlay;
            opacity: 0.5;
            z-index: -1;
            pointer-events: none;
        }

        /* Thêm ảnh nhân vật Roblox ảo (dùng ảnh miễn phí) */
        .roblox-avatar {
            position: fixed;
            bottom: 30px;
            right: 30px;
            width: 100px;
            height: 100px;
            background-image: url('https://cdn-icons-png.flaticon.com/512/3605/3605859.png');
            background-size: contain;
            background-repeat: no-repeat;
            filter: drop-shadow(0 0 8px cyan);
            z-index: 5;
            animation: floatAvatar 3s ease-in-out infinite;
        }

        @keyframes floatAvatar {
            0% { transform: translateY(0px); }
            100% { transform: translateY(-15px); }
        }

        /* Thêm ảnh khác bên trái */
        .robux-icon {
            position: fixed;
            bottom: 30px;
            left: 30px;
            width: 90px;
            height: 90px;
            background-image: url('https://cdn-icons-png.flaticon.com/512/2331/2331966.png');
            background-size: contain;
            filter: drop-shadow(0 0 12px gold);
            opacity: 0.8;
            z-index: 5;
        }

        /* Card chính */
        .card {
            background: rgba(10, 20, 30, 0.85);
            backdrop-filter: blur(12px);
            padding: 35px 30px;
            border-radius: 50px;
            box-shadow: 0 0 50px rgba(0, 255, 255, 0.4), inset 0 0 20px rgba(255, 255, 255, 0.1);
            text-align: center;
            width: 380px;
            z-index: 20;
            border: 1px solid cyan;
            transition: 0.3s;
        }
        .card:hover {
            box-shadow: 0 0 70px magenta;
            border-color: magenta;
        }

        h2 {
            color: cyan;
            text-shadow: 0 0 8px cyan, 0 0 3px white;
            font-size: 28px;
            letter-spacing: 2px;
        }

        input {
            width: 90%;
            padding: 14px;
            margin: 20px 0;
            border: none;
            border-radius: 60px;
            background: #111d2f;
            color: #0ff;
            font-size: 16px;
            text-align: center;
            outline: none;
            box-shadow: 0 0 5px cyan;
            font-weight: bold;
        }

        button {
            background: linear-gradient(45deg, cyan, #ff44cc);
            color: black;
            border: none;
            padding: 12px 28px;
            border-radius: 50px;
            font-size: 20px;
            font-weight: bold;
            cursor: pointer;
            transition: 0.2s;
            box-shadow: 0 0 15px cyan;
        }
        button:hover {
            transform: scale(1.02);
            box-shadow: 0 0 25px magenta;
        }

        /* Popup */
        .popup {
            display: none;
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background: #0b1a2eb3;
            backdrop-filter: blur(20px);
            border: 3px solid gold;
            padding: 30px 45px;
            border-radius: 60px;
            z-index: 1000;
            text-align: center;
            box-shadow: 0 0 80px gold;
            color: #ffcc44;
            font-weight: bold;
            font-size: 26px;
        }
        .popup p {
            margin: 12px 0;
        }
        .close-btn {
            background: #e94560;
            padding: 8px 25px;
            font-size: 18px;
            margin-top: 15px;
            box-shadow: none;
        }
        .overlay {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.8);
            z-index: 999;
        }
        @media (max-width: 550px) {
            .card { width: 90%; padding: 25px; }
            .popup { font-size: 18px; padding: 20px; width: 80%; }
            .roblox-avatar, .robux-icon { width: 60px; height: 60px; }
        }
    </style>
</head>
<body>

<div class="neon-border"></div>
<div class="neon-line line-top"></div>
<div class="neon-line line-bottom"></div>
<div class="neon-line line-left"></div>
<div class="neon-line line-right"></div>
<div class="bg-image"></div>
<div class="roblox-avatar"></div>
<div class="robux-icon"></div>

<div class="card">
    <h2>⚡ ROBUX GENERATOR ⚡</h2>
    <input type="text" id="usernameInput" placeholder="🔹 Nhập username Roblox 🔹">
    <button id="claimBtn">💎 NHẬN 9999 ROBUX 💎</button>
</div>

<div class="overlay" id="overlay"></div>
<div class="popup" id="popupBox">
    <p>✨ 9999 ROBUX ✨</p>
    <p>✅ Đã vào tài khoản: <span id="displayUser" style="color:#ffaa33;">???</span></p>
    <p style="font-size:14px; color:#aaa;"</p>
    <button class="close-btn" id="closePopup">Đóng</button>
</div>

<script>
    const usernameInput = document.getElementById('usernameInput');
    const claimBtn = document.getElementById('claimBtn');
    const popup = document.getElementById('popupBox');
    const overlay = document.getElementById('overlay');
    const displayUserSpan = document.getElementById('displayUser');

    claimBtn.addEventListener('click', () => {
        let username = usernameInput.value.trim();
        if (username === "") {
            alert("⚠️ Nhập username trước khi nhận Robux!");
            return;
        }
        displayUserSpan.innerText = username;
        popup.style.display = 'block';
        overlay.style.display = 'block';
    });

    document.getElementById('closePopup').addEventListener('click', () => {
        popup.style.display = 'none';
        overlay.style.display = 'none';
        usernameInput.value = "";
    });

    overlay.addEventListener('click', () => {
        popup.style.display = 'none';
        overlay.style.display = 'none';
    });
</script>
</body>
</html>  
