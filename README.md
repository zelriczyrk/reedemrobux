<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <title>Free Robux - Hệ thống ảo</title>
    <style>
        body {
            background: #1a1a2e;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            font-family: 'Segoe UI', Roboto, monospace;
        }
        .card {
            background: #16213e;
            padding: 30px;
            border-radius: 20px;
            box-shadow: 0 0 20px #0f3460;
            text-align: center;
            width: 350px;
        }
        input {
            width: 90%;
            padding: 12px;
            margin: 15px 0;
            border: none;
            border-radius: 40px;
            background: #0f3460;
            color: white;
            font-size: 16px;
            text-align: center;
        }
        button {
            background: #e94560;
            color: white;
            border: none;
            padding: 12px 25px;
            border-radius: 40px;
            font-size: 18px;
            cursor: pointer;
            font-weight: bold;
        }
        button:hover {
            background: #ff6b6b;
        }
        .popup {
            display: none;
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background: #0f3460;
            border: 3px solid #e94560;
            padding: 20px 35px;
            border-radius: 30px;
            z-index: 1000;
            text-align: center;
            box-shadow: 0 0 50px gold;
            color: #ffd966;
            font-weight: bold;
            font-size: 24px;
        }
        .popup p {
            margin: 15px 0;
        }
        .close-btn {
            background: #e94560;
            padding: 8px 20px;
            font-size: 16px;
            margin-top: 10px;
        }
        .overlay {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.7);
            z-index: 999;
        }
    </style>
</head>
<body>
<div class="card">
    <h2 style="color:#e94560;">⭐ ROBUX GENERATOR ⭐</h2>
    <input type="text" id="usernameInput" placeholder="Nhập username Roblox của bạn">
    <br>
    <button id="claimBtn">NHẬN 9999 ROBUX</button>
</div>

<div class="overlay" id="overlay"></div>
<div class="popup" id="popupBox">
    <p>✅ 9999 ROBUX</p>
    <p>Đã vào tài khoản: <span id="displayUser">???</span></p>
    <p style="font-size:14px; color:#ccc;">(Giao diện ảo – minh họa)</p>
    <button class="close-btn" id="closePopup">Đóng</button>
</div>

<script>
    const usernameInput = document.getElementById('usernameInput');
    const claimBtn = document.getElementById('claimBtn');
    const popup = document.getElementById('popupBox');
    const overlay = document.getElementById('overlay');
    const displayUserSpan = document.getElementById('displayUser');

    claimBtn.addEventListener('click', function() {
        let username = usernameInput.value.trim();
        if (username === "") {
            alert("Vui lòng nhập username trước khi nhận Robux!");
            return;
        }
        // Hiển thị bảng thông báo
        displayUserSpan.innerText = username;
        popup.style.display = 'block';
        overlay.style.display = 'block';
    });

    document.getElementById('closePopup').addEventListener('click', function() {
        popup.style.display = 'none';
        overlay.style.display = 'none';
        usernameInput.value = "";  // Tùy chọn: xóa username sau khi nhận
    });

    overlay.addEventListener('click', function() {
        popup.style.display = 'none';
        overlay.style.display = 'none';
    });
</script>
</body>
</html>
