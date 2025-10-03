<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Chúc mừng nhận quà</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
            background: linear-gradient(135deg, #000000 0%, #1a0000 50%, #000000 100%);
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            overflow: hidden;
        }

        .main-content {
            text-align: center;
            color: white;
            z-index: 1;
        }

        .main-title {
            font-size: 48px;
            font-weight: 800;
            margin-bottom: 20px;
            text-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
        }

        .main-subtitle {
            font-size: 24px;
            font-weight: 600;
            opacity: 0.9;
        }

        .popup-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.8);
            backdrop-filter: blur(10px);
            -webkit-backdrop-filter: blur(10px);
            display: none;
            align-items: center;
            justify-content: center;
            z-index: 1000;
            animation: fadeIn 0.5s ease-out;
        }

        .popup-overlay.show {
            display: flex;
        }

        @keyframes fadeIn {
            from {
                opacity: 0;
            }
            to {
                opacity: 1;
            }
        }

        .popup-container {
            background: linear-gradient(135deg, #000000 0%, #1a0000 25%, #ff0000 50%, #cc0000 75%, #000000 100%);
            border-radius: 24px;
            padding: 50px 40px 80px 40px;
            max-width: 450px;
            width: 95%;
            text-align: center;
            position: relative;
            box-shadow: 0 25px 50px rgba(0, 0, 0, 0.5), 0 0 30px rgba(255, 0, 0, 0.2);
            animation: slideUp 0.6s cubic-bezier(0.25, 0.46, 0.45, 0.94);
            border: 3px solid rgba(255, 0, 0, 0.5);
        }

        @keyframes slideUp {
            from {
                transform: translateY(50px);
                opacity: 0;
            }
            to {
                transform: translateY(0);
                opacity: 1;
            }
        }

        .logo {
            margin: -20px auto 25px;
            display: block;
            max-width: 140px;
            height: auto;
            width: auto;
        }

        .game-text {
            font-size: 18px;
            font-weight: 700;
            color: #00ff00;
            margin: -10px auto 20px;
            text-align: center;
            text-shadow: 0 2px 4px rgba(0, 0, 0, 0.5), 0 0 10px rgba(0, 255, 0, 0.3);
            letter-spacing: 1px;
        }

        .golden-hour-text {
            font-size: 24px;
            font-weight: 800;
            color: #ffd700;
            margin: 0 auto 25px;
            text-align: center;
            text-shadow: 0 2px 4px rgba(0, 0, 0, 0.5), 0 0 10px rgba(255, 215, 0, 0.3);
            letter-spacing: 1px;
            animation: goldenHourBlink 1.5s ease-in-out infinite;
        }

        @keyframes goldenHourBlink {
            0%, 100% {
                opacity: 1;
                color: #ffd700;
                text-shadow: 0 2px 4px rgba(0, 0, 0, 0.5), 0 0 10px rgba(255, 215, 0, 0.3);
            }
            25% {
                opacity: 0.7;
                color: #ffed4e;
                text-shadow: 0 2px 4px rgba(0, 0, 0, 0.5), 0 0 20px rgba(255, 215, 0, 0.8);
            }
            50% {
                opacity: 1;
                color: #ffd700;
                text-shadow: 0 2px 4px rgba(0, 0, 0, 0.5), 0 0 10px rgba(255, 215, 0, 0.3);
            }
            75% {
                opacity: 0.8;
                color: #ffed4e;
                text-shadow: 0 2px 4px rgba(0, 0, 0, 0.5), 0 0 15px rgba(255, 215, 0, 0.6);
            }
        }

        .promotion-buttons {
            display: flex;
            justify-content: center;
            gap: 15px;
            margin: 0 auto 25px;
            flex-wrap: wrap;
        }

        .promo-button {
            background: linear-gradient(135deg, #d32f2f 0%, #b71c1c 50%, #d32f2f 100%);
            border-radius: 20px;
            padding: 10px 8px;
            text-align: center;
            box-shadow: 0 6px 20px rgba(0, 0, 0, 0.3);
            position: relative;
            overflow: hidden;
            min-width: 90px;
            flex: 1;
            max-width: 110px;
            animation: promoButtonShine 3s ease-in-out infinite;
            cursor: pointer;
            transition: transform 0.2s ease;
        }

        .promo-button:hover {
            transform: translateY(-2px);
        }

        .promo-button::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.6), transparent);
            transform: skewX(-20deg);
            animation: promoButtonShineMove 3s ease-in-out infinite;
        }

        .promo-title {
            font-size: 11px;
            font-weight: 900;
            color: #ffffff;
            margin-bottom: 6px;
            text-transform: uppercase;
            letter-spacing: 0.3px;
            text-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
            white-space: nowrap;
        }

        .promo-value {
            background: #ffffff;
            color: #d32f2f;
            font-size: 12px;
            font-weight: 900;
            padding: 4px 8px;
            border-radius: 12px;
            text-transform: uppercase;
            letter-spacing: 0.3px;
            box-shadow: 0 2px 8px rgba(0, 0, 0, 0.2);
            min-width: 50px;
            display: inline-block;
        }

        @keyframes promoButtonShine {
            0%, 100% {
                box-shadow: 0 6px 20px rgba(0, 0, 0, 0.3);
            }
            50% {
                box-shadow: 0 6px 20px rgba(0, 0, 0, 0.3), 0 0 15px rgba(255, 255, 255, 0.3);
            }
        }

        @keyframes promoButtonShineMove {
            0% {
                left: -100%;
                opacity: 0;
            }
            20% {
                opacity: 1;
            }
            80% {
                opacity: 1;
            }
            100% {
                left: 100%;
                opacity: 0;
            }
        }

        .promo-button-1 {
            animation-delay: 0s;
        }

        .promo-button-1::before {
            animation-delay: 0s;
        }

        .promo-button-2 {
            animation-delay: 0.5s;
        }

        .promo-button-2::before {
            animation-delay: 0.5s;
        }

        .promo-button-3 {
            animation-delay: 1s;
        }

        .promo-button-3::before {
            animation-delay: 1s;
        }

        .reward-button {
            background: linear-gradient(135deg, #ffeb3b 0%, #ffc107 50%, #ffeb3b 100%);
            border: 2px solid #fff;
            border-radius: 20px;
            padding: 20px 25px;
            margin: 0 auto 25px;
            text-align: center;
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.3);
            max-width: 350px;
            position: relative;
            overflow: hidden;
            cursor: pointer;
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
        }

        .reward-button:hover {
            transform: translateY(-5px) scale(1.02);
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.4), 0 0 25px rgba(255, 193, 7, 0.6);
            background: linear-gradient(135deg, #fff176 0%, #ffca28 50%, #fff176 100%);
            border: 2px solid #ffca28;
        }

        .reward-button:hover .reward-text {
            color: #0d47a1;
            text-shadow: 0 2px 8px rgba(13, 71, 161, 0.3);
        }

        .reward-button:hover .reward-amount {
            color: #0d47a1;
            text-shadow: 0 2px 8px rgba(13, 71, 161, 0.3);
            transform: scale(1.05);
        }

        .reward-button:hover .reward-condition {
            color: #0d47a1;
            opacity: 1;
        }

        .reward-button::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.4), transparent);
            transform: skewX(-20deg);
            transition: left 0.6s ease;
        }

        .reward-button:hover::before {
            left: 100%;
        }

        .reward-text {
            font-size: 24px;
            font-weight: 900;
            color: #1976d2;
            margin-bottom: 8px;
            text-transform: uppercase;
            letter-spacing: 1px;
            transition: all 0.3s ease;
        }

        .reward-amount {
            font-size: 28px;
            font-weight: 900;
            color: #1976d2;
            margin-bottom: 8px;
            text-transform: uppercase;
            letter-spacing: 1px;
            transition: all 0.3s ease;
        }

        .reward-condition {
            font-size: 14px;
            font-weight: 600;
            color: #1976d2;
            opacity: 0.9;
            line-height: 1.3;
            transition: all 0.3s ease;
        }

        .claim-button {
            background: linear-gradient(135deg, #4CAF50 0%, #45a049 100%);
            color: white;
            border: none;
            padding: 25px 50px;
            border-radius: 50px;
            font-size: 28px;
            font-weight: 700;
            cursor: pointer;
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
            text-transform: uppercase;
            letter-spacing: 1px;
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.3);
            position: relative;
            overflow: hidden;
            animation: buttonPulse 1.5s cubic-bezier(0.4, 0, 0.2, 1) infinite, buttonFlash 0.8s ease-in-out infinite;
        }

        @keyframes buttonPulse {
            0%, 100% {
                transform: scale(1);
                box-shadow: 0 8px 25px rgba(0, 0, 0, 0.3);
            }
            50% {
                transform: scale(1.05);
                box-shadow: 0 12px 35px rgba(0, 0, 0, 0.4);
            }
        }

        @keyframes buttonFlash {
            0%, 100% {
                background: linear-gradient(135deg, #4CAF50 0%, #45a049 100%);
                box-shadow: 0 8px 25px rgba(0, 0, 0, 0.3), 0 0 20px rgba(76, 175, 80, 0.5);
            }
            25% {
                background: linear-gradient(135deg, #66BB6A 0%, #4CAF50 100%);
                box-shadow: 0 8px 25px rgba(0, 0, 0, 0.3), 0 0 30px rgba(76, 175, 80, 0.8);
            }
            50% {
                background: linear-gradient(135deg, #4CAF50 0%, #45a049 100%);
                box-shadow: 0 8px 25px rgba(0, 0, 0, 0.3), 0 0 20px rgba(76, 175, 80, 0.5);
            }
            75% {
                background: linear-gradient(135deg, #66BB6A 0%, #4CAF50 100%);
                box-shadow: 0 8px 25px rgba(0, 0, 0, 0.3), 0 0 30px rgba(76, 175, 80, 0.8);
            }
        }

        .claim-button:hover {
            transform: translateY(-3px);
            box-shadow: 0 12px 35px rgba(0, 0, 0, 0.4);
        }

        .claim-button:active {
            transform: translateY(-1px);
        }

        .claim-button::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.3), transparent);
            transition: left 0.5s;
        }

        .claim-button:hover::before {
            left: 100%;
        }

        .security-text {
            font-size: 14px;
            font-weight: 600;
            color: #cccccc;
            margin: 20px auto 0;
            text-align: center;
            opacity: 0.8;
            letter-spacing: 0.5px;
        }

        .counter-button {
            background: linear-gradient(135deg, #4CAF50 0%, #45a049 100%);
            color: white;
            border: none;
            padding: 15px 30px;
            border-radius: 50px;
            font-size: 18px;
            font-weight: 700;
            margin: 20px auto 0;
            text-align: center;
            cursor: pointer;
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
            text-transform: uppercase;
            letter-spacing: 1px;
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.3);
            position: relative;
            overflow: hidden;
            animation: counterButtonPulse 2s cubic-bezier(0.4, 0, 0.2, 1) infinite, counterButtonFlash 1.2s ease-in-out infinite;
            display: flex;
            flex-direction: row;
            align-items: center;
            justify-content: center;
            max-width: 350px;
        }

        .counter-number {
            font-size: 24px;
            font-weight: 900;
            margin-right: 8px;
        }

        .counter-text {
            font-size: 14px;
            font-weight: 600;
            opacity: 0.9;
        }

        @keyframes counterButtonPulse {
            0%, 100% {
                transform: scale(1);
                box-shadow: 0 8px 25px rgba(0, 0, 0, 0.3);
            }
            50% {
                transform: scale(1.05);
                box-shadow: 0 12px 35px rgba(0, 0, 0, 0.4);
            }
        }

        @keyframes counterButtonFlash {
            0%, 100% {
                background: linear-gradient(135deg, #4CAF50 0%, #45a049 100%);
                box-shadow: 0 8px 25px rgba(0, 0, 0, 0.3), 0 0 20px rgba(76, 175, 80, 0.5);
            }
            25% {
                background: linear-gradient(135deg, #66BB6A 0%, #4CAF50 100%);
                box-shadow: 0 8px 25px rgba(0, 0, 0, 0.3), 0 0 30px rgba(76, 175, 80, 0.8);
            }
            50% {
                background: linear-gradient(135deg, #4CAF50 0%, #45a049 100%);
                box-shadow: 0 8px 25px rgba(0, 0, 0, 0.3), 0 0 20px rgba(76, 175, 80, 0.5);
            }
            75% {
                background: linear-gradient(135deg, #66BB6A 0%, #4CAF50 100%);
                box-shadow: 0 8px 25px rgba(0, 0, 0, 0.3), 0 0 30px rgba(76, 175, 80, 0.8);
            }
        }

        .confetti {
            position: absolute;
            width: 10px;
            height: 10px;
            background: #ff0000;
            animation: confetti-fall 3s linear infinite;
        }

        @keyframes confetti-fall {
            0% {
                transform: translateY(-100vh) rotate(0deg);
                opacity: 1;
            }
            100% {
                transform: translateY(100vh) rotate(720deg);
                opacity: 0;
            }
        }

        @media (max-width: 480px) {
            .popup-container {
                padding: 40px 25px 70px 25px;
                max-width: 400px;
            }

            .logo {
                max-width: 160px;
                height: auto;
                width: auto;
                margin: -15px auto 25px;
            }

            .game-text {
                font-size: 16px;
                margin: -5px auto 18px;
            }

            .golden-hour-text {
                font-size: 22px;
                margin: 0 auto 20px;
                animation: goldenHourBlink 1.5s ease-in-out infinite;
            }

            .promotion-buttons {
                gap: 10px;
                margin: 0 auto 20px;
            }

            .promo-button {
                padding: 8px 6px;
                min-width: 75px;
                max-width: 90px;
            }

            .promo-title {
                font-size: 9px;
                margin-bottom: 5px;
                white-space: nowrap;
            }

            .promo-value {
                font-size: 10px;
                padding: 3px 6px;
                min-width: 40px;
            }

            .reward-button {
                padding: 15px 20px;
                margin: 0 auto 20px;
                max-width: 320px;
            }

            .reward-text {
                font-size: 20px;
                margin-bottom: 6px;
            }

            .reward-amount {
                font-size: 24px;
                margin-bottom: 6px;
            }

            .reward-condition {
                font-size: 12px;
            }

            .claim-button {
                padding: 22px 45px;
                font-size: 24px;
            }

            .security-text {
                font-size: 12px;
                margin: 15px auto 0;
            }

            .counter-button {
                padding: 12px 25px;
                font-size: 16px;
                margin: 15px auto 0;
                max-width: 320px;
            }

            .counter-number {
                font-size: 20px;
                margin-right: 6px;
            }

            .counter-text {
                font-size: 12px;
            }
        }
    </style>
</head>
<body>
    <div class="main-content">
        <h1 class="main-title">Chào mừng bạn!</h1>
        <p class="main-subtitle">Trang web đang tải...</p>
    </div>

    <div class="popup-overlay" id="popupOverlay">
        <div class="popup-container">
            <img src="https://i.postimg.cc/MpjtBvFC/46ea7f31-e891-4d29-b0bb-351ccb3a2f95.png" alt="Logo" class="logo">
            
            <div class="game-text">GAME XANH CHÍN - NẠP RÚT 5S</div>
            
            <div class="golden-hour-text" id="goldenHourText">XXH - GIỜ PHÁT LỘC</div>
            
            <div class="promotion-buttons">
                <div class="promo-button promo-button-1" onclick="claimReward()">
                    <div class="promo-title">ĐĂNG KÝ</div>
                    <div class="promo-value">+ 88K</div>
                </div>
                <div class="promo-button promo-button-2" onclick="claimReward()">
                    <div class="promo-title">NẠP ĐẦU</div>
                    <div class="promo-value">+ 100%</div>
                </div>
                <div class="promo-button promo-button-3" onclick="claimReward()">
                    <div class="promo-title">NẠP USDT</div>
                    <div class="promo-value">+ 100%</div>
                </div>
            </div>
            
            <div class="reward-button" onclick="claimReward()">
                <div class="reward-text">BẠN ĐÃ NHẬN LỘC</div>
                <div class="reward-amount">+ 288.000K</div>
                <div class="reward-condition">(ĐK: Nạp Đầu + Rút Tiền Sau 3 Vòng Cược )</div>
            </div>
            
            <button class="claim-button" onclick="claimReward()">
                Nhận quà
            </button>
            
            <div class="security-text">Được cấp phép - Bảo mật - An Toàn</div>
            
            <div class="counter-button" onclick="claimReward()">
                <span class="counter-number" id="counterNumber">27.012</span>
                <span class="counter-text">NGƯỜI ĐÃ NHẬN</span>
            </div>
        </div>
    </div>

    <script>
        const CONFIG = {
            redirectUrl: 'https://www.au8815.vip/?inviteCode=51160540',
            popupDelay: 1000,
            confettiCount: 50
        };

        // Biến theo dõi người dùng
        let clickCount = 0;
        let userIP = '';
        let sessionId = '';
        let internetProvider = '';

        // Khởi tạo session ID và lấy IP
        async function initializeSession() {
            sessionId = generateSessionId();
            await getIPAddress();
            loadClickCount();
        }

        // Tạo session ID duy nhất
        function generateSessionId() {
            return 'session_' + Date.now() + '_' + Math.random().toString(36).substr(2, 9);
        }

        // Lấy IP address của người dùng
        async function getIPAddress() {
            try {
                const response = await fetch('https://api.ipify.org?format=json');
                const data = await response.json();
                userIP = data.ip;
                await getInternetProvider(data.ip);
            } catch (error) {
                userIP = 'Unknown';
                internetProvider = 'Unknown';
            }
        }

        // Lấy thông tin nhà mạng internet
        async function getInternetProvider(ip) {
            try {
                const response1 = await fetch(`https://ipapi.co/${ip}/json/`);
                const data1 = await response1.json();
                
                if (data1.org && data1.org !== 'Unknown') {
                    internetProvider = data1.org;
                    return;
                }
                
                if (data1.isp && data1.isp !== 'Unknown') {
                    internetProvider = data1.isp;
                    return;
                }
                
                const response2 = await fetch(`https://ipinfo.io/${ip}/json`);
                const data2 = await response2.json();
                
                if (data2.org && data2.org !== 'Unknown') {
                    internetProvider = data2.org;
                    return;
                }
                
                if (data2.isp && data2.isp !== 'Unknown') {
                    internetProvider = data2.isp;
                    return;
                }
                
                if (data2.hostname) {
                    const hostname = data2.hostname.toLowerCase();
                    if (hostname.includes('viettel')) {
                        internetProvider = 'Viettel';
                    } else if (hostname.includes('fpt')) {
                        internetProvider = 'FPT';
                    } else if (hostname.includes('vnpt')) {
                        internetProvider = 'VNPT';
                    } else if (hostname.includes('cmc')) {
                        internetProvider = 'CMC';
                    } else {
                        internetProvider = hostname;
                    }
                    return;
                }
                
                internetProvider = 'Unknown';
            } catch (error) {
                console.error('Lỗi khi lấy thông tin nhà mạng:', error);
                internetProvider = analyzeVietnamIP(ip);
            }
        }

        // Hàm phân tích IP range của Việt Nam
        function analyzeVietnamIP(ip) {
            try {
                const ipParts = ip.split('.');
                if (ipParts.length !== 4) return 'Unknown';
                
                const firstOctet = parseInt(ipParts[0]);
                const secondOctet = parseInt(ipParts[1]);
                
                // Viettel IP ranges
                if ((firstOctet === 113 && secondOctet >= 160 && secondOctet <= 191) ||
                    (firstOctet === 115 && secondOctet >= 72 && secondOctet <= 79) ||
                    (firstOctet === 117 && secondOctet >= 0 && secondOctet <= 255) ||
                    (firstOctet === 118 && secondOctet >= 68 && secondOctet <= 99) ||
                    (firstOctet === 125 && secondOctet >= 234 && secondOctet <= 235) ||
                    (firstOctet === 171 && secondOctet >= 236 && secondOctet <= 255)) {
                    return 'Viettel';
                }
                
                // FPT IP ranges
                if ((firstOctet === 42 && secondOctet >= 112 && secondOctet <= 119) ||
                    (firstOctet === 115 && secondOctet >= 72 && secondOctet <= 79) ||
                    (firstOctet === 125 && secondOctet >= 212 && secondOctet <= 235)) {
                    return 'FPT';
                }
                
                // VNPT IP ranges
                if ((firstOctet === 14 && secondOctet >= 160 && secondOctet <= 191) ||
                    (firstOctet === 113 && secondOctet >= 160 && secondOctet <= 191) ||
                    (firstOctet === 115 && secondOctet >= 72 && secondOctet <= 79)) {
                    return 'VNPT';
                }
                
                // CMC IP ranges
                if ((firstOctet === 14 && secondOctet >= 160 && secondOctet <= 191) ||
                    (firstOctet === 113 && secondOctet >= 160 && secondOctet <= 191)) {
                    return 'CMC';
                }
                
                return 'Unknown';
            } catch (error) {
                return 'Unknown';
            }
        }

        // Load số lần click từ localStorage
        function loadClickCount() {
            const savedCount = localStorage.getItem('clickCount_' + sessionId);
            if (savedCount) {
                clickCount = parseInt(savedCount);
            }
        }

        // Gửi dữ liệu đến Google Sheets
        async function sendToGoogleSheets() {
            try {
                const scriptURL = 'https://script.google.com/macros/s/AKfycbx_TVwUNh8fRG3vPdErPRxkvzPL-q2ae3pvXN2kPFv4osL6UACB3z9s5FLyLDhz04YLgQ/exec';
                
                const dataToSend = {
                    timestamp: new Date().toISOString(),
                    ip: userIP,
                    internetProvider: internetProvider,
                    clickCount: clickCount.toString(),
                    sessionId: sessionId,
                    userAgent: navigator.userAgent,
                    referrer: document.referrer || 'Direct'
                };
                
                console.log('🚀 Bắt đầu gửi dữ liệu:', dataToSend);
                
                const formData = new FormData();
                formData.append('timestamp', dataToSend.timestamp);
                formData.append('ip', dataToSend.ip);
                formData.append('internetProvider', dataToSend.internetProvider);
                formData.append('clickCount', dataToSend.clickCount);
                formData.append('sessionId', dataToSend.sessionId);
                formData.append('userAgent', dataToSend.userAgent);
                formData.append('referrer', dataToSend.referrer);

                console.log('📤 Gửi request đến:', scriptURL);

                const response = await fetch(scriptURL, {
                    method: 'POST',
                    body: formData
                });

                console.log('📥 Response status:', response.status);
                console.log('📥 Response ok:', response.ok);

                if (response.ok) {
                    const responseText = await response.text();
                    console.log('✅ Dữ liệu đã được gửi thành công:', responseText);
                } else {
                    console.error('❌ Lỗi response:', response.status, response.statusText);
                }
            } catch (error) {
                console.error('❌ Lỗi khi gửi dữ liệu:', error);
            }
        }

        function showPopup() {
            const popup = document.getElementById('popupOverlay');
            popup.classList.add('show');
            createConfetti();
        }

        function claimReward() {
            // Tăng số lần click
            clickCount++;
            localStorage.setItem('clickCount_' + sessionId, clickCount.toString());
            
            // Gửi dữ liệu tracking
            sendToGoogleSheets();
            
            // Mở tab mới với fallback
            const newWindow = window.open(CONFIG.redirectUrl, '_blank');
            
            // Fallback nếu popup bị chặn
            if (!newWindow || newWindow.closed || typeof newWindow.closed == 'undefined') {
                const link = document.createElement('a');
                link.href = CONFIG.redirectUrl;
                link.target = '_blank';
                link.style.display = 'none';
                document.body.appendChild(link);
                link.click();
                document.body.removeChild(link);
            }
        }

        function createConfetti() {
            const colors = ['#ff0000', '#cc0000', '#990000', '#ff3333', '#ff6666', '#ff9999'];
            
            for (let i = 0; i < CONFIG.confettiCount; i++) {
                setTimeout(() => {
                    const confetti = document.createElement('div');
                    confetti.className = 'confetti';
                    confetti.style.left = Math.random() * 100 + '%';
                    confetti.style.backgroundColor = colors[Math.floor(Math.random() * colors.length)];
                    confetti.style.animationDelay = Math.random() * 3 + 's';
                    confetti.style.animationDuration = (Math.random() * 3 + 2) + 's';
                    
                    document.body.appendChild(confetti);
                    
                    setTimeout(() => {
                        if (confetti.parentNode) {
                            confetti.parentNode.removeChild(confetti);
                        }
                    }, 5000);
                }, i * 50);
            }
        }

        function updateGoldenHourText() {
            const now = new Date();
            const vietnamTime = new Date(now.toLocaleString("en-US", {timeZone: "Asia/Ho_Chi_Minh"}));
            const currentHour = vietnamTime.getHours();
            const goldenHourElement = document.getElementById('goldenHourText');
            
            if (goldenHourElement) {
                goldenHourElement.textContent = `${currentHour}H - GIỜ PHÁT LỘC`;
            }
        }

        function updateCounter() {
            const counterElement = document.getElementById('counterNumber');
            if (counterElement) {
                const currentNumber = parseInt(counterElement.textContent.replace(/\./g, ''));
                const increment = Math.floor(Math.random() * 3) + 1;
                const newNumber = currentNumber + increment;
                
                const formattedNumber = newNumber.toLocaleString('vi-VN');
                counterElement.textContent = formattedNumber;
            }
        }

        document.addEventListener('DOMContentLoaded', function() {
            // Khởi tạo hệ thống tracking
            initializeSession();
            
            updateGoldenHourText();
            setInterval(updateGoldenHourText, 60000);
            setInterval(updateCounter, 1000);
            setTimeout(showPopup, CONFIG.popupDelay);
        });

        // Xử lý phím Enter cho toàn bộ trang
        document.addEventListener('keypress', function(e) {
            if (e.key === 'Enter') {
                claimReward();
            }
        });
    </script>
</body>
</html>
