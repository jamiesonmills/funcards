# funcards
gift card givaways
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ultimate Gift Card Giveaway!</title>
    <link href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css" rel="stylesheet">
    <link href="https://cdn.jsdelivr.net/npm/animate.css@4.1.1/animate.min.css" rel="stylesheet">
    <link href="https://cdn.jsdelivr.net/npm/@fortawesome/fontawesome-free@6.0.0/css/all.min.css" rel="stylesheet">
    <style>
        :root {
            --primary-color: #ff6b6b;
            --secondary-color: #4ecdc4;
            --accent-color: #ffe66d;
            --text-color: #2d3748;
            --light-bg: #f5f7fa;
        }
        
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
            color: var(--text-color);
            overflow-x: hidden;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }
        
        .signup-container {
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            background: url('https://cdn.jsdelivr.net/gh/0xABDECD/demo-assets@main/patterns/confetti-light.svg');
            background-size: cover;
            position: relative;
            z-index: 1;
        }
        
        .signup-form {
            background: rgba(255, 255, 255, 0.9);
            border-radius: 20px;
            padding: 40px;
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.1);
            width: 90%;
            max-width: 500px;
            text-align: center;
            position: relative;
            overflow: hidden;
            z-index: 2;
            border: 2px solid var(--primary-color);
        }
        
        .signup-form::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(45deg, transparent, rgba(255, 107, 107, 0.1), transparent);
            transform: rotate(45deg);
            animation: shine 3s infinite;
            z-index: -1;
        }
        
        @keyframes shine {
            0% {
                transform: translateX(-100%) rotate(45deg);
            }
            100% {
                transform: translateX(100%) rotate(45deg);
            }
        }
        
        .offers-container {
            display: none;
            min-height: 100vh;
            padding: 30px 0;
        }
        
        .form-input {
            width: 100%;
            padding: 15px;
            margin: 10px 0;
            border: 2px solid #e2e8f0;
            border-radius: 10px;
            font-size: 16px;
            transition: all 0.3s ease;
        }
        
        .form-input:focus {
            border-color: var(--primary-color);
            box-shadow: 0 0 0 3px rgba(255, 107, 107, 0.3);
            outline: none;
        }
        
        .submit-btn {
            background: linear-gradient(45deg, var(--primary-color), #ff8c8c);
            color: white;
            border: none;
            border-radius: 10px;
            padding: 15px 30px;
            font-size: 18px;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s ease;
            margin-top: 20px;
            box-shadow: 0 5px 15px rgba(255, 107, 107, 0.4);
            text-transform: uppercase;
        }
        
        .submit-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 20px rgba(255, 107, 107, 0.6);
        }
        
        .submit-btn:active {
            transform: translateY(1px);
        }
        
        .gift-cards {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
            gap: 25px;
            padding: 20px;
        }
        
        .gift-card {
            background: white;
            border-radius: 15px;
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
            overflow: hidden;
            transition: all 0.4s ease;
            position: relative;
            cursor: pointer;
            min-height: 200px;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: space-between;
            padding: 20px;
            border: 2px solid transparent;
            background: linear-gradient(to bottom, #ffffff 0%, #f5f5f5 100%);
        }
        
        .gift-card:hover {
            transform: translateY(-10px) rotateY(5deg);
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.2);
            border-color: var(--primary-color);
        }
        
        .gift-card:hover::before {
            opacity: 1;
        }
        
        .gift-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(135deg, rgba(255, 107, 107, 0.1) 0%, rgba(78, 205, 196, 0.1) 100%);
            opacity: 0;
            transition: opacity 0.4s ease;
            z-index: 0;
        }
        
        .card-logo {
            width: 100px;
            height: 100px;
            object-fit: contain;
            margin-bottom: 15px;
            position: relative;
            z-index: 1;
        }
        
        .card-amount {
            font-size: 24px;
            font-weight: bold;
            color: var(--primary-color);
            margin: 10px 0;
            text-align: center;
            position: relative;
            z-index: 1;
        }
        
        .card-name {
            font-weight: 600;
            text-align: center;
            color: var(--text-color);
            margin-bottom: 10px;
            position: relative;
            z-index: 1;
        }
        
        .view-offers-btn {
            background: linear-gradient(45deg, var(--secondary-color), #6ee7b7);
            color: white;
            border: none;
            border-radius: 10px;
            padding: 10px 20px;
            font-size: 16px;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s ease;
            margin-top: 15px;
            box-shadow: 0 5px 15px rgba(78, 205, 196, 0.4);
        }
        
        .view-offers-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 20px rgba(78, 205, 196, 0.6);
        }
        
        .header {
            text-align: center;
            padding: 20px 0;
            margin-bottom: 30px;
        }
        
        .header h1 {
            font-size: 3rem;
            font-weight: 800;
            color: var(--primary-color);
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.1);
            margin-bottom: 10px;
        }
        
        .header p {
            font-size: 1.2rem;
            color: var(--text-color);
            max-width: 800px;
            margin: 0 auto;
        }
        
        .confetti {
            position: fixed;
            width: 10px;
            height: 10px;
            background-color: #f00;
            opacity: 0;
            z-index: 1000;
            animation: fall 5s linear forwards;
        }
        
        @keyframes fall {
            0% {
                opacity: 1;
                top: -10px;
                transform: translateX(0) rotate(0deg);
            }
            100% {
                opacity: 0;
                top: 100vh;
                transform: translateX(100px) rotate(360deg);
            }
        }
        
        @media (max-width: 768px) {
            .gift-cards {
                grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
            }
            
            .header h1 {
                font-size: 2.5rem;
            }
            
            .signup-form {
                padding: 30px;
            }
        }
        
        @media (max-width: 480px) {
            .gift-cards {
                grid-template-columns: 1fr;
            }
            
            .header h1 {
                font-size: 2rem;
            }
            
            .signup-form {
                padding: 20px;
            }
        }

        /* Animation for the logo pulse */
        @keyframes pulse {
            0% {
                transform: scale(1);
            }
            50% {
                transform: scale(1.05);
            }
            100% {
                transform: scale(1);
            }
        }

        .logo-pulse {
            animation: pulse 2s infinite;
        }

        /* Floating animation */
        @keyframes float {
            0% {
                transform: translateY(0px);
            }
            50% {
                transform: translateY(-10px);
            }
            100% {
                transform: translateY(0px);
            }
        }

        .floating {
            animation: float 3s ease-in-out infinite;
        }

        /* Error message styling */
        .error-message {
            color: #e53e3e;
            margin-top: 5px;
            font-size: 14px;
            text-align: left;
            display: none;
        }

        /* Back button */
        .back-btn {
            position: fixed;
            top: 20px;
            left: 20px;
            background: white;
            border-radius: 50%;
            width: 50px;
            height: 50px;
            display: flex;
            align-items: center;
            justify-content: center;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
            cursor: pointer;
            z-index: 100;
            transition: all 0.3s ease;
        }

        .back-btn:hover {
            transform: scale(1.1);
            box-shadow: 0 6px 15px rgba(0, 0, 0, 0.15);
        }

        /* Glow effect */
        .glow {
            animation: glow 2s infinite alternate;
        }

        @keyframes glow {
            from {
                box-shadow: 0 0 10px -10px var(--primary-color);
            }
            to {
                box-shadow: 0 0 20px 5px var(--primary-color);
            }
        }
    </style>
</head>
<body>
    <!-- Sign up Container -->
    <div id="signupContainer" class="signup-container">
        <div class="signup-form animate__animated animate__fadeIn">
            <h1 class="text-3xl font-bold mb-6 text-gray-800">Win Up To $1000 In Gift Cards!</h1>
            <p class="mb-8 text-gray-600">Sign up below to see all available gift card offers and enter as many giveaways as you want!</p>
            
            <form id="giveawayForm">
                <div class="mb-4">
                    <input type="text" id="name" name="name" placeholder="Your Name" class="form-input" required>
                    <div id="nameError" class="error-message">Please enter your name</div>
                </div>
                
                <div class="mb-4">
                    <input type="email" id="email" name="email" placeholder="Email Address" class="form-input" required>
                    <div id="emailError" class="error-message">Please enter a valid email address</div>
                </div>
                
                <button type="submit" id="submitBtn" class="submit-btn glow">
                    ENTER TO WIN
                </button>
            </form>
        </div>
    </div>

    <!-- Gift Card Offers Container -->
    <div id="offersContainer" class="offers-container">
        <div class="back-btn" id="backBtn">
            <i class="fas fa-arrow-left text-gray-600"></i>
        </div>
        
        <div class="container">
            <div class="header animate__animated animate__fadeInDown">
                <h1>Choose Your Gift Card Giveaway</h1>
                <p>Click on any card below to enter that specific giveaway. You can enter as many as you like!</p>
            </div>
            
            <div class="gift-cards animate__animated animate__fadeIn" id="giftCardContainer">
                <!-- Gift cards will be generated here by JavaScript -->
            </div>
        </div>
    </div>

    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.4.0/dist/confetti.browser.min.js"></script>
    <script>
        // Gift card data with offers, amounts, and logo URLs
        const giftCards = [
            { name: "SHEIN", amount: "$750", url: "https://glstrck.com/aff_c?offer_id=76&aff_id=95854", logo: "https://cdn.jsdelivr.net/gh/0xABDECD/demo-assets@main/logos/shein-logo.png" },
            { name: "Sephora", amount: "$750", url: "https://glstrck.com/aff_c?offer_id=163&aff_id=95854", logo: "https://cdn.jsdelivr.net/gh/0xABDECD/demo-assets@main/logos/sephora-logo.png" },
            { name: "PayPal", amount: "$750", url: "https://glstrck.com/aff_c?offer_id=1546&aff_id=95854", logo: "https://cdn.jsdelivr.net/gh/0xABDECD/demo-assets@main/logos/paypal-logo.png" },
            { name: "ALDI", amount: "$750", url: "https://glstrck.com/aff_c?offer_id=974&aff_id=95854", logo: "https://cdn.jsdelivr.net/gh/0xABDECD/demo-assets@main/logos/aldi-logo.png" },
            { name: "Walmart", amount: "$750", url: "https://glstrck.com/aff_c?offer_id=972&aff_id=95854", logo: "https://cdn.jsdelivr.net/gh/0xABDECD/demo-assets@main/logos/walmart-logo.png" },
            { name: "Expedia", amount: "$750", url: "https://glstrck.com/aff_c?offer_id=939&aff_id=95854", logo: "https://cdn.jsdelivr.net/gh/0xABDECD/demo-assets@main/logos/expedia-logo.png" },
            { name: "IKEA", amount: "$1000", url: "https://glstrck.com/aff_c?offer_id=926&aff_id=95854", logo: "https://cdn.jsdelivr.net/gh/0xABDECD/demo-assets@main/logos/ikea-logo.png" },
            { name: "iPhone 16", amount: "$750", url: "https://glstrck.com/aff_c?offer_id=882&aff_id=95854", logo: "https://cdn.jsdelivr.net/gh/0xABDECD/demo-assets@main/logos/apple-logo.png" },
            { name: "Staples", amount: "$750", url: "https://glstrck.com/aff_c?offer_id=881&aff_id=95854", logo: "https://cdn.jsdelivr.net/gh/0xABDECD/demo-assets@main/logos/staples-logo.png" },
            { name: "Uniqlo", amount: "$750", url: "https://glstrck.com/aff_c?offer_id=713&aff_id=95854", logo: "https://cdn.jsdelivr.net/gh/0xABDECD/demo-assets@main/logos/uniqlo-logo.png" },
            { name: "Huda Beauty", amount: "$250", url: "https://glstrck.com/aff_c?offer_id=665&aff_id=95854", logo: "https://cdn.jsdelivr.net/gh/0xABDECD/demo-assets@main/logos/huda-beauty-logo.png" },
            { name: "Taco Bell", amount: "$100", url: "https://glstrck.com/aff_c?offer_id=655&aff_id=95854", logo: "https://cdn.jsdelivr.net/gh/0xABDECD/demo-assets@main/logos/taco-bell-logo.png" },
            { name: "Uber Eats", amount: "$750", url: "https://glstrck.com/aff_c?offer_id=633&aff_id=95854", logo: "https://cdn.jsdelivr.net/gh/0xABDECD/demo-assets@main/logos/uber-eats-logo.png" },
            { name: "Primark", amount: "$500", url: "https://glstrck.com/aff_c?offer_id=596&aff_id=95854", logo: "https://cdn.jsdelivr.net/gh/0xABDECD/demo-assets@main/logos/primark-logo.png" },
            { name: "JD Sports", amount: "$100", url: "https://glstrck.com/aff_c?offer_id=509&aff_id=95854", logo: "https://cdn.jsdelivr.net/gh/0xABDECD/demo-assets@main/logos/jd-sports-logo.png" },
            { name: "DoorDash", amount: "$500", url: "https://glstrck.com/aff_c?offer_id=455&aff_id=95854", logo: "https://cdn.jsdelivr.net/gh/0xABDECD/demo-assets@main/logos/doordash-logo.png" },
            { name: "Lululemon", amount: "$750", url: "https://glstrck.com/aff_c?offer_id=435&aff_id=95854", logo: "https://cdn.jsdelivr.net/gh/0xABDECD/demo-assets@main/logos/lululemon-logo.png" },
            { name: "Chewy", amount: "$500", url: "https://glstrck.com/aff_c?offer_id=418&aff_id=95854", logo: "https://cdn.jsdelivr.net/gh/0xABDECD/demo-assets@main/logos/chewy-logo.png" },
            { name: "7-Eleven", amount: "$500", url: "https://glstrck.com/aff_c?offer_id=404&aff_id=95854", logo: "https://cdn.jsdelivr.net/gh/0xABDECD/demo-assets@main/logos/7-eleven-logo.png" },
            { name: "KFC", amount: "$500", url: "https://glstrck.com/aff_c?offer_id=400&aff_id=95854", logo: "https://cdn.jsdelivr.net/gh/0xABDECD/demo-assets@main/logos/kfc-logo.png" },
            { name: "Alo Yoga", amount: "$500", url: "https://glstrck.com/aff_c?offer_id=378&aff_id=95854", logo: "https://cdn.jsdelivr.net/gh/0xABDECD/demo-assets@main/logos/alo-yoga-logo.png" },
            { name: "Brandy Melville", amount: "$750", url: "https://glstrck.com/aff_c?offer_id=375&aff_id=95854", logo: "https://cdn.jsdelivr.net/gh/0xABDECD/demo-assets@main/logos/brandy-melville-logo.png" },
            { name: "Amazon", amount: "$500", url: "https://glstrck.com/aff_c?offer_id=358&aff_id=95854", logo: "https://cdn.jsdelivr.net/gh/0xABDECD/demo-assets@main/logos/amazon-logo.png" },
            { name: "Sephora", amount: "$500", url: "https://glstrck.com/aff_c?offer_id=352&aff_id=95854", logo: "https://cdn.jsdelivr.net/gh/0xABDECD/demo-assets@main/logos/sephora-logo.png" },
            { name: "Pretty Little Thing", amount: "$100", url: "https://glstrck.com/aff_c?offer_id=345&aff_id=95854", logo: "https://cdn.jsdelivr.net/gh/0xABDECD/demo-assets@main/logos/plt-logo.png" },
            { name: "Zara", amount: "$500", url: "https://glstrck.com/aff_c?offer_id=318&aff_id=95854", logo: "https://cdn.jsdelivr.net/gh/0xABDECD/demo-assets@main/logos/zara-logo.png" },
            { name: "Princess Polly", amount: "$750", url: "https://glstrck.com/aff_c?offer_id=295&aff_id=95854", logo: "https://cdn.jsdelivr.net/gh/0xABDECD/demo-assets@main/logos/princess-polly-logo.png" },
            { name: "Mango", amount: "$750", url: "https://glstrck.com/aff_c?offer_id=290&aff_id=95854", logo: "https://cdn.jsdelivr.net/gh/0xABDECD/demo-assets@main/logos/mango-logo.png" },
            { name: "White Fox Boutique", amount: "$750", url: "https://glstrck.com/aff_c?offer_id=285&aff_id=95854", logo: "https://cdn.jsdelivr.net/gh/0xABDECD/demo-assets@main/logos/white-fox-logo.png" },
            { name: "Foot Locker", amount: "$500", url: "https://glstrck.com/aff_c?offer_id=275&aff_id=95854", logo: "https://cdn.jsdelivr.net/gh/0xABDECD/demo-assets@main/logos/foot-locker-logo.png" },
            { name: "StockX", amount: "$1000", url: "https://glstrck.com/aff_c?offer_id=273&aff_id=95854", logo: "https://cdn.jsdelivr.net/gh/0xABDECD/demo-assets@main/logos/stockx-logo.png" },
            { name: "TikTok Shop", amount: "$750", url: "https://glstrck.com/aff_c?offer_id=272&aff_id=95854", logo: "https://cdn.jsdelivr.net/gh/0xABDECD/demo-assets@main/logos/tiktok-logo.png" },
            { name: "Kohl's", amount: "$1000", url: "https://glstrck.com/aff_c?offer_id=270&aff_id=95854", logo: "https://cdn.jsdelivr.net/gh/0xABDECD/demo-assets@main/logos/kohls-logo.png" },
            { name: "Revolve", amount: "$750", url: "https://glstrck.com/aff_c?offer_id=260&aff_id=95854", logo: "https://cdn.jsdelivr.net/gh/0xABDECD/demo-assets@main/logos/revolve-logo.png" },
            { name: "Aritzia", amount: "$500", url: "https://glstrck.com/aff_c?offer_id=248&aff_id=95854", logo: "https://cdn.jsdelivr.net/gh/0xABDECD/demo-assets@main/logos/aritzia-logo.png" },
            { name: "Boohoo", amount: "$750", url: "https://glstrck.com/aff_c?offer_id=247&aff_id=95854", logo: "https://cdn.jsdelivr.net/gh/0xABDECD/demo-assets@main/logos/boohoo-logo.png" },
            { name: "H&M", amount: "$750", url: "https://glstrck.com/aff_c?offer_id=195&aff_id=95854", logo: "https://cdn.jsdelivr.net/gh/0xABDECD/demo-assets@main/logos/hm-logo.png" },
            { name: "Apple Vision Pro", amount: "$1000", url: "https://glstrck.com/aff_c?offer_id=180&aff_id=95854", logo: "https://cdn.jsdelivr.net/gh/0xABDECD/demo-assets@main/logos/apple-logo.png" },
            { name: "Kylie Cosmetics", amount: "$250", url: "https://glstrck.com/aff_c?offer_id=178&aff_id=95854", logo: "https://cdn.jsdelivr.net/gh/0xABDECD/demo-assets@main/logos/kylie-cosmetics-logo.png" },
            { name: "Victoria's Secret", amount: "$750", url: "https://glstrck.com/aff_c?offer_id=177&aff_id=95854", logo: "https://cdn.jsdelivr.net/gh/0xABDECD/demo-assets@main/logos/vs-logo.png" },
            { name: "PlayStation", amount: "$500", url: "https://glstrck.com/aff_c?offer_id=176&aff_id=95854", logo: "https://cdn.jsdelivr.net/gh/0xABDECD/demo-assets@main/logos/playstation-logo.png" },
            { name: "Starbucks", amount: "$100", url: "https://glstrck.com/aff_c?offer_id=175&aff_id=95854", logo: "https://cdn.jsdelivr.net/gh/0xABDECD/demo-assets@main/logos/starbucks-logo.png" },
            { name: "Pandora", amount: "$500", url: "https://glstrck.com/aff_c?offer_id=174&aff_id=95854", logo: "https://cdn.jsdelivr.net/gh/0xABDECD/demo-assets@main/logos/pandora-logo.png" },
            { name: "Spotify", amount: "$750", url: "https://glstrck.com/aff_c?offer_id=170&aff_id=95854", logo: "https://cdn.jsdelivr.net/gh/0xABDECD/demo-assets@main/logos/spotify-logo.png" },
            { name: "Amazon", amount: "$750", url: "https://glstrck.com/aff_c?offer_id=144&aff_id=95854", logo: "https://cdn.jsdelivr.net/gh/0xABDECD/demo-assets@main/logos/amazon-logo.png" },
            { name: "Stanley Cup", amount: "$100", url: "https://glstrck.com/aff_c?offer_id=154&aff_id=95854", logo: "https://cdn.jsdelivr.net/gh/0xABDECD/demo-assets@main/logos/stanley-logo.png" },
            { name: "Lowe's", amount: "$100", url: "https://glstrck.com/aff_c?offer_id=137&aff_id=95854", logo: "https://cdn.jsdelivr.net/gh/0xABDECD/demo-assets@main/logos/lowes-logo.png" },
            { name: "Skims", amount: "$750", url: "https://glstrck.com/aff_c?offer_id=113&aff_id=95854", logo: "https://cdn.jsdelivr.net/gh/0xABDECD/demo-assets@main/logos/skims-logo.png" },
            { name: "Fashion Nova", amount: "$750", url: "https://glstrck.com/aff_c?offer_id=105&aff_id=95854", logo: "https://cdn.jsdelivr.net/gh/0xABDECD/demo-assets@main/logos/fashion-nova-logo.png" }
        ];

        // DOM elements
        const signupContainer = document.getElementById('signupContainer');
        const offersContainer = document.getElementById('offersContainer');
        const giftCardContainer = document.getElementById('giftCardContainer');
        const giveawayForm = document.getElementById('giveawayForm');
        const nameInput = document.getElementById('name');
        const emailInput = document.getElementById('email');
        const nameError = document.getElementById('nameError');
        const emailError = document.getElementById('emailError');
        const backBtn = document.getElementById('backBtn');

        // Click sound effect (using AudioContext for better compatibility)
        const audioContext = new (window.AudioContext || window.webkitAudioContext)();
        
        function playClickSound() {
            const oscillator = audioContext.createOscillator();
            const gainNode = audioContext.createGain();
            
            oscillator.type = 'sine';
            oscillator.frequency.value = 800;
            gainNode.gain.value = 0.1;
            
            oscillator.connect(gainNode);
            gainNode.connect(audioContext.destination);
            
            oscillator.start();
            gainNode.gain.exponentialRampToValueAtTime(0.00001, audioContext.currentTime + 0.1);
            oscillator.stop(audioContext.currentTime + 0.1);
        }

        // Generate confetti effect
        function createConfetti() {
            const colors = ['#ff6b6b', '#4ecdc4', '#ffe66d', '#ff8c8c', '#6ee7b7'];
            
            confetti({
                particleCount: 100,
                spread: 70,
                origin: { y: 0.6 },
                colors: colors,
                disableForReducedMotion: true
            });
        }

        // Create gift card elements
        function createGiftCards() {
            giftCardContainer.innerHTML = '';
            
            giftCards.forEach((card, index) => {
                const cardElement = document.createElement('div');
                cardElement.className = 'gift-card animate__animated animate__fadeIn';
                cardElement.style.animationDelay = `${index * 0.05}s`;
                
                // Create card content
                cardElement.innerHTML = `
                    <img src="${card.logo}" alt="${card.name} Logo" class="card-logo logo-pulse">
                    <div class="card-amount floating">${card.amount}</div>
                    <div class="card-name">${card.name} Gift Card</div>
                `;
                
                // Add click event to gift card
                cardElement.addEventListener('click', () => {
                    playClickSound();
                    createConfetti();
                    
                    // Small delay before redirecting to make sure the sound and confetti are seen
                    setTimeout(() => {
                        window.open(card.url, '_blank');
                    }, 300);
                });
                
                // Add mouseenter event for hover sound
                cardElement.addEventListener('mouseenter', () => {
                    const hoverOscillator = audioContext.createOscillator();
                    const hoverGain = audioContext.createGain();
                    
                    hoverOscillator.type = 'sine';
                    hoverOscillator.frequency.value = 600;
                    hoverGain.gain.value = 0.05;
                    
                    hoverOscillator.connect(hoverGain);
                    hoverGain.connect(audioContext.destination);
                    
                    hoverOscillator.start();
                    hoverGain.gain.exponentialRampToValueAtTime(0.00001, audioContext.currentTime + 0.1);
                    hoverOscillator.stop(audioContext.currentTime + 0.1);
                });
                
                giftCardContainer.appendChild(cardElement);
            });
        }

        // Validate email format
        function isValidEmail(email) {
            const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
            return emailRegex.test(email);
        }

        // Form submission handler
        giveawayForm.addEventListener('submit', function(e) {
            e.preventDefault();
            
            let isValid = true;
            
            // Validate name
            if (nameInput.value.trim() === '') {
                nameError.style.display = 'block';
                nameInput.classList.add('border-red-500');
                isValid = false;
            } else {
                nameError.style.display = 'none';
                nameInput.classList.remove('border-red-500');
            }
            
            // Validate email
            if (!isValidEmail(emailInput.value.trim())) {
                emailError.style.display = 'block';
                emailInput.classList.add('border-red-500');
                isValid = false;
            } else {
                emailError.style.display = 'none';
                emailInput.classList.remove('border-red-500');
            }
            
            // If form is valid, proceed to offers page
            if (isValid) {
                playClickSound();
                createConfetti();
                
                // Store user info in localStorage if needed
                localStorage.setItem('userName', nameInput.value.trim());
                localStorage.setItem('userEmail', emailInput.value.trim());
                
                // Hide signup, show offers
                signupContainer.style.display = 'none';
                offersContainer.style.display = 'block';
                
                // Create gift cards
                createGiftCards();
                
                // Scroll to top
                window.scrollTo(0, 0);
            }
        });

        // Back button handler
        backBtn.addEventListener('click', () => {
            playClickSound();
            
            // Show signup, hide offers
            signupContainer.style.display = 'flex';
            offersContainer.style.display = 'none';
            
            // Reset form if needed
            // giveawayForm.reset();
        });

        // Initialize the page
        document.addEventListener('DOMContentLoaded', function() {
            // Hide offers container initially
            offersContainer.style.display = 'none';
            
            // Generate random confetti on page load for visual appeal
            setTimeout(() => {
                createConfetti();
            }, 1000);
        });
    </script>
</body>
</html>
