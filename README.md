<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Jogos Educativos - Plataforma Completa</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            color: #333;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }

        /* Sistema de Login */
        .login-section {
            position: fixed;
            top: 20px;
            right: 20px;
            z-index: 1000;
        }

        .login-btn {
            background: linear-gradient(135deg, #4facfe, #00f2fe);
            color: white;
            border: none;
            padding: 12px 25px;
            border-radius: 25px;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 5px 15px rgba(79, 172, 254, 0.3);
        }

        .login-btn:hover {
            transform: scale(1.05);
        }

        .user-info {
            display: none;
            background: rgba(255, 255, 255, 0.95);
            padding: 15px 20px;
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
        }

        .user-name {
            font-weight: bold;
            color: #4a5568;
            margin-bottom: 10px;
        }

        .logout-btn {
            background: linear-gradient(135deg, #ff6b6b, #ee5a24);
            color: white;
            border: none;
            padding: 8px 15px;
            border-radius: 15px;
            cursor: pointer;
        }

        /* Modal de Login */
        .login-modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.8);
            z-index: 2000;
            justify-content: center;
            align-items: center;
        }

        .login-content {
            background: white;
            border-radius: 25px;
            padding: 40px;
            max-width: 450px;
            width: 90%;
            box-shadow: 0 25px 50px rgba(0, 0, 0, 0.3);
            position: relative;
        }

        .login-close {
            position: absolute;
            top: 15px;
            right: 20px;
            background: none;
            border: none;
            font-size: 1.5rem;
            cursor: pointer;
            color: #666;
        }

        .login-title {
            text-align: center;
            font-size: 2rem;
            margin-bottom: 30px;
            background: linear-gradient(135deg, #667eea, #764ba2);
            background-clip: text;
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .form-group {
            margin-bottom: 20px;
        }

        .form-label {
            display: block;
            margin-bottom: 8px;
            font-weight: bold;
            color: #4a5568;
        }

        .form-input {
            width: 100%;
            padding: 15px;
            border: 2px solid #e2e8f0;
            border-radius: 10px;
            font-size: 1rem;
            transition: all 0.3s ease;
        }

        .form-input:focus {
            border-color: #4facfe;
            outline: none;
            box-shadow: 0 0 10px rgba(79, 172, 254, 0.2);
        }

        .form-btn {
            width: 100%;
            padding: 15px;
            border: none;
            border-radius: 10px;
            font-size: 1.1rem;
            font-weight: bold;
            cursor: pointer;
            background: linear-gradient(135deg, #48bb78, #38a169);
            color: white;
            margin-bottom: 15px;
        }

        .demo-btn {
            width: 100%;
            padding: 10px;
            margin-bottom: 8px;
            border: 2px solid #e2e8f0;
            border-radius: 8px;
            background: white;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .demo-btn:hover {
            border-color: #4facfe;
            background: #f7fafc;
        }

        /* Header */
        header {
            text-align: center;
            margin-bottom: 40px;
            background: rgba(255, 255, 255, 0.95);
            padding: 50px;
            border-radius: 30px;
            box-shadow: 0 25px 50px rgba(0, 0, 0, 0.15);
        }

        h1 {
            font-size: 4rem;
            background: linear-gradient(135deg, #667eea, #764ba2);
            background-clip: text;
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            margin-bottom: 20px;
        }

        .subtitle {
            font-size: 1.4rem;
            color: #4a5568;
            margin-bottom: 30px;
            font-weight: 600;
        }

        .version-badge {
            display: inline-block;
            background: linear-gradient(135deg, #ff6b6b, #ee5a24);
            color: white;
            padding: 8px 16px;
            border-radius: 20px;
            font-size: 0.9rem;
            font-weight: bold;
            margin-top: 15px;
        }

        /* Sistema de Pontuação */
        .score-system {
            background: linear-gradient(135deg, #667eea, #764ba2);
            color: white;
            padding: 20px;
            border-radius: 20px;
            margin-bottom: 30px;
            text-align: center;
            box-shadow: 0 10px 30px rgba(102, 126, 234, 0.3);
        }

        .score-title {
            font-size: 1.2rem;
            font-weight: bold;
            margin-bottom: 15px;
        }

        .score-stats {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(120px, 1fr));
            gap: 15px;
        }

        .score-stat {
            background: rgba(255, 255, 255, 0.2);
            padding: 15px;
            border-radius: 15px;
        }

        .score-number {
            font-size: 2rem;
            font-weight: bold;
            margin-bottom: 5px;
        }

        .score-label {
            font-size: 0.9rem;
            opacity: 0.9;
        }

        /* Sistema de Moedas */
        .currency-display {
            position: fixed;
            top: 20px;
            left: 20px;
            background: linear-gradient(135deg, #ffd700, #ffed4e);
            color: #333;
            padding: 15px 20px;
            border-radius: 25px;
            font-weight: bold;
            font-size: 1.1rem;
            box-shadow: 0 10px 30px rgba(255, 215, 0, 0.3);
            z-index: 1000;
            display: none;
        }

        /* Sistema de Planos */
        .plan-badge {
            position: fixed;
            top: 80px;
            left: 20px;
            padding: 8px 15px;
            border-radius: 20px;
            font-weight: bold;
            font-size: 0.9rem;
            z-index: 1000;
            display: none;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
        }

        .plan-badge.basic {
            background: linear-gradient(135deg, #718096, #4a5568);
            color: white;
        }

        .plan-badge.premium {
            background: linear-gradient(135deg, #9f7aea, #805ad5);
            color: white;
        }

        .plan-badge.ultra {
            background: linear-gradient(135deg, #ffd700, #ff8c00);
            color: #333;
        }

        .shop-btn {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background: linear-gradient(135deg, #ff6b6b, #ee5a24);
            color: white;
            border: none;
            padding: 15px 20px;
            border-radius: 25px;
            font-weight: bold;
            cursor: pointer;
            font-size: 1.1rem;
            box-shadow: 0 10px 30px rgba(255, 107, 107, 0.3);
            z-index: 1000;
            display: none;
            transition: all 0.3s ease;
        }

        .shop-btn:hover {
            transform: scale(1.05);
        }

        .plans-btn {
            position: fixed;
            bottom: 80px;
            right: 20px;
            background: linear-gradient(135deg, #9f7aea, #805ad5);
            color: white;
            border: none;
            padding: 15px 20px;
            border-radius: 25px;
            font-weight: bold;
            cursor: pointer;
            font-size: 1.1rem;
            box-shadow: 0 10px 30px rgba(159, 122, 234, 0.3);
            z-index: 1000;
            display: none;
            transition: all 0.3s ease;
        }

        .plans-btn:hover {
            transform: scale(1.05);
        }

        /* Loja */
        .shop-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 20px;
            margin-bottom: 20px;
        }

        .shop-item {
            background: white;
            border-radius: 15px;
            padding: 20px;
            text-align: center;
            border: 2px solid #e2e8f0;
            transition: all 0.3s ease;
        }

        .shop-item:hover {
            border-color: #4facfe;
            transform: translateY(-5px);
        }

        .shop-item.owned {
            background: linear-gradient(135deg, #48bb78, #38a169);
            color: white;
            border-color: #48bb78;
        }

        .shop-item-icon {
            font-size: 3rem;
            margin-bottom: 15px;
        }

        .shop-item-name {
            font-size: 1.2rem;
            font-weight: bold;
            margin-bottom: 10px;
        }

        .shop-item-description {
            font-size: 0.9rem;
            color: #666;
            margin-bottom: 15px;
        }

        .shop-item.owned .shop-item-description {
            color: rgba(255, 255, 255, 0.8);
        }

        .shop-item-price {
            background: linear-gradient(135deg, #ffd700, #ffed4e);
            color: #333;
            padding: 8px 15px;
            border-radius: 20px;
            font-weight: bold;
            margin-bottom: 15px;
            display: inline-block;
        }

        .shop-buy-btn {
            background: linear-gradient(135deg, #4facfe, #00f2fe);
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 15px;
            font-weight: bold;
            cursor: pointer;
            width: 100%;
        }

        .shop-buy-btn:disabled {
            background: #ccc;
            cursor: not-allowed;
        }

        .shop-owned-badge {
            background: rgba(255, 255, 255, 0.2);
            padding: 8px 15px;
            border-radius: 15px;
            font-weight: bold;
        }

        /* Modal de Planos */
        .plans-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 25px;
            margin-bottom: 20px;
        }

        .plan-card {
            background: white;
            border-radius: 20px;
            padding: 30px;
            text-align: center;
            border: 3px solid #e2e8f0;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .plan-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
        }

        .plan-card.basic {
            border-color: #718096;
        }

        .plan-card.premium {
            border-color: #9f7aea;
            transform: scale(1.05);
        }

        .plan-card.ultra {
            border-color: #ffd700;
            background: linear-gradient(135deg, #fff9e6, #ffffff);
        }

        .plan-card.current {
            background: linear-gradient(135deg, #48bb78, #38a169);
            color: white;
            border-color: #48bb78;
        }

        .plan-popular {
            position: absolute;
            top: -10px;
            right: -10px;
            background: linear-gradient(135deg, #ff6b6b, #ee5a24);
            color: white;
            padding: 8px 20px;
            border-radius: 20px;
            font-size: 0.8rem;
            font-weight: bold;
            transform: rotate(15deg);
        }

        .plan-icon {
            font-size: 3rem;
            margin-bottom: 15px;
        }

        .plan-name {
            font-size: 1.8rem;
            font-weight: bold;
            margin-bottom: 10px;
            color: #2d3748;
        }

        .plan-card.current .plan-name {
            color: white;
        }

        .plan-price {
            font-size: 2.5rem;
            font-weight: bold;
            margin-bottom: 5px;
            color: #4a5568;
        }

        .plan-card.current .plan-price {
            color: white;
        }

        .plan-period {
            font-size: 0.9rem;
            color: #666;
            margin-bottom: 25px;
        }

        .plan-card.current .plan-period {
            color: rgba(255, 255, 255, 0.8);
        }

        .plan-features {
            list-style: none;
            padding: 0;
            margin-bottom: 25px;
        }

        .plan-features li {
            padding: 8px 0;
            border-bottom: 1px solid #e2e8f0;
            color: #4a5568;
        }

        .plan-card.current .plan-features li {
            color: rgba(255, 255, 255, 0.9);
            border-bottom-color: rgba(255, 255, 255, 0.2);
        }

        .plan-features li:last-child {
            border-bottom: none;
        }

        .plan-btn {
            width: 100%;
            padding: 15px;
            border: none;
            border-radius: 15px;
            font-size: 1.1rem;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .plan-btn.basic {
            background: linear-gradient(135deg, #718096, #4a5568);
            color: white;
        }

        .plan-btn.premium {
            background: linear-gradient(135deg, #9f7aea, #805ad5);
            color: white;
        }

        .plan-btn.ultra {
            background: linear-gradient(135deg, #ffd700, #ff8c00);
            color: #333;
        }

        .plan-btn.current {
            background: rgba(255, 255, 255, 0.2);
            color: white;
            cursor: default;
        }

        .plan-btn:hover:not(.current) {
            transform: scale(1.05);
        }

        .plan-btn:disabled {
            background: #ccc;
            cursor: not-allowed;
        }

        /* Benefícios dos Planos */
        .plan-benefits {
            background: #f7fafc;
            padding: 20px;
            border-radius: 15px;
            margin-top: 20px;
        }

        .benefit-item {
            display: flex;
            align-items: center;
            padding: 10px 0;
            border-bottom: 1px solid #e2e8f0;
        }

        .benefit-item:last-child {
            border-bottom: none;
        }

        .benefit-icon {
            font-size: 1.5rem;
            margin-right: 15px;
            width: 30px;
            text-align: center;
        }

        .benefit-text {
            flex: 1;
            color: #4a5568;
        }

        /* Recompensas */
        .reward-notification {
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background: linear-gradient(135deg, #ffd700, #ffed4e);
            color: #333;
            padding: 30px;
            border-radius: 20px;
            text-align: center;
            font-size: 1.2rem;
            font-weight: bold;
            box-shadow: 0 25px 50px rgba(0, 0, 0, 0.3);
            z-index: 3000;
            display: none;
            animation: rewardPulse 0.5s ease-in-out;
        }

        @keyframes rewardPulse {
            0% { transform: translate(-50%, -50%) scale(0.8); opacity: 0; }
            50% { transform: translate(-50%, -50%) scale(1.1); }
            100% { transform: translate(-50%, -50%) scale(1); opacity: 1; }
        }

        /* Grid de jogos */
        .games-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 30px;
            margin-bottom: 50px;
        }

        .game-card {
            background: rgba(255, 255, 255, 0.95);
            border-radius: 25px;
            padding: 30px;
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.1);
            transition: all 0.3s ease;
            cursor: pointer;
        }

        .game-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 25px 50px rgba(0, 0, 0, 0.2);
        }

        .game-icon {
            font-size: 4rem;
            text-align: center;
            margin-bottom: 20px;
        }

        .game-title {
            font-size: 1.5rem;
            font-weight: bold;
            color: #2d3748;
            margin-bottom: 15px;
            text-align: center;
        }

        .game-description {
            color: #4a5568;
            text-align: center;
            margin-bottom: 20px;
            line-height: 1.6;
        }

        .score-display {
            background: linear-gradient(135deg, #667eea, #764ba2);
            color: white;
            padding: 10px 15px;
            border-radius: 20px;
            font-size: 0.9rem;
            margin-bottom: 20px;
            text-align: center;
            font-weight: bold;
        }

        .play-button {
            background: linear-gradient(135deg, #4facfe, #00f2fe);
            color: white;
            border: none;
            padding: 15px 30px;
            border-radius: 25px;
            font-size: 1.1rem;
            font-weight: bold;
            cursor: pointer;
            width: 100%;
            transition: all 0.3s ease;
        }

        .play-button:hover {
            transform: scale(1.05);
        }

        /* Modais dos Jogos */
        .game-modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.8);
            z-index: 2000;
            justify-content: center;
            align-items: center;
        }

        .modal-content {
            background: white;
            border-radius: 25px;
            padding: 40px;
            max-width: 700px;
            width: 90%;
            max-height: 85vh;
            overflow-y: auto;
            position: relative;
            box-shadow: 0 25px 50px rgba(0, 0, 0, 0.3);
        }

        .close-button {
            position: absolute;
            top: 20px;
            right: 25px;
            background: linear-gradient(135deg, #ff6b6b, #ee5a24);
            color: white;
            border: none;
            border-radius: 50%;
            width: 40px;
            height: 40px;
            font-size: 1.3rem;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .game-interface {
            background: rgba(255, 255, 255, 0.95);
            border-radius: 20px;
            padding: 30px;
            margin-bottom: 20px;
        }

        .game-stats {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(100px, 1fr));
            gap: 15px;
            margin-bottom: 25px;
        }

        .stat-item {
            background: linear-gradient(135deg, #4facfe, #00f2fe);
            color: white;
            padding: 15px;
            border-radius: 15px;
            text-align: center;
            font-weight: bold;
        }

        .question-area {
            background: linear-gradient(135deg, #f7fafc, #edf2f7);
            padding: 30px;
            border-radius: 20px;
            margin-bottom: 25px;
            text-align: center;
            font-size: 1.5rem;
            font-weight: bold;
            color: #2d3748;
            min-height: 120px;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .answer-input {
            width: 100%;
            padding: 20px;
            border: 3px solid #e2e8f0;
            border-radius: 15px;
            font-size: 1.3rem;
            text-align: center;
            margin-bottom: 20px;
        }

        .answer-input:focus {
            border-color: #4facfe;
            outline: none;
        }

        .options-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 15px;
            margin-bottom: 25px;
        }

        .option-btn {
            padding: 20px;
            border: 3px solid #e2e8f0;
            border-radius: 15px;
            background: white;
            cursor: pointer;
            transition: all 0.3s ease;
            font-size: 1.1rem;
            font-weight: bold;
            color: #2d3748;
        }

        .option-btn:hover {
            border-color: #4facfe;
            background: #f7fafc;
        }

        .option-btn.correct {
            background: linear-gradient(135deg, #48bb78, #38a169);
            color: white;
            border-color: #48bb78;
        }

        .option-btn.incorrect {
            background: linear-gradient(135deg, #e53e3e, #c53030);
            color: white;
            border-color: #e53e3e;
        }

        .control-btn {
            background: linear-gradient(135deg, #48bb78, #38a169);
            color: white;
            border: none;
            padding: 15px 25px;
            border-radius: 15px;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s ease;
            margin: 5px;
        }

        .control-btn:hover {
            transform: scale(1.05);
        }

        .control-btn.secondary {
            background: linear-gradient(135deg, #4facfe, #00f2fe);
        }

        /* Notificações */
        .notification {
            position: fixed;
            top: 20px;
            right: 20px;
            padding: 15px 20px;
            border-radius: 15px;
            color: white;
            font-weight: bold;
            z-index: 3000;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
        }

        .notification.success {
            background: linear-gradient(135deg, #48bb78, #38a169);
        }

        .notification.error {
            background: linear-gradient(135deg, #e53e3e, #c53030);
        }

        /* Responsividade */
        @media (max-width: 768px) {
            h1 {
                font-size: 2.5rem;
            }
            
            .games-grid {
                grid-template-columns: 1fr;
            }

            .modal-content {
                padding: 20px;
                margin: 10px;
            }

            .plans-grid {
                grid-template-columns: 1fr;
            }

            .plan-card.premium {
                transform: none;
            }
        }
    </style>
</head>
<body>
    <!-- Sistema de Moedas -->
    <div id="currency-display" class="currency-display">
        💰 <span id="user-coins">0</span> Moedas
    </div>

    <!-- Badge do Plano -->
    <div id="plan-badge" class="plan-badge basic">
        <span id="plan-name">📦 Plano Básico</span>
    </div>

    <!-- Botão da Loja -->
    <button id="shop-btn" class="shop-btn" onclick="abrirLoja()">
        🛒 Loja
    </button>

    <!-- Botão dos Planos -->
    <button id="plans-btn" class="plans-btn" onclick="abrirPlanos()">
        ⭐ Planos
    </button>

    <!-- Sistema de Login -->
    <div class="login-section">
        <div id="login-section">
            <button class="login-btn" onclick="mostrarLogin()">🔐 Fazer Login</button>
        </div>
        <div id="user-section" class="user-info">
            <div class="user-name">👋 Olá, <span id="user-name"></span>!</div>
            <div id="user-badges" style="margin: 8px 0; font-size: 0.85rem;"></div>
            <div style="display: flex; gap: 8px;">
                <button id="admin-panel-btn" class="logout-btn" onclick="abrirPainelAdmin()" style="background: linear-gradient(135deg, #9f7aea, #805ad5); display: none;">⚙️ Admin</button>
                <button class="logout-btn" onclick="logout()">🚪 Sair</button>
            </div>
        </div>
    </div>

    <!-- Modal de Login -->
    <div id="login-modal" class="login-modal">
        <div class="login-content">
            <button class="login-close" onclick="fecharLogin()">&times;</button>
            <h2 class="login-title">🎮 Acesso à Plataforma</h2>
            
            <!-- Formulário de Login -->
            <div id="login-form">
                <div class="form-group">
                    <label class="form-label">👤 Usuário</label>
                    <input type="text" id="login-usuario" class="form-input" placeholder="Digite seu usuário">
                </div>
                <div class="form-group">
                    <label class="form-label">🔒 Senha</label>
                    <input type="password" id="login-senha" class="form-input" placeholder="Digite sua senha">
                </div>
                <button class="form-btn" onclick="fazerLogin()">🚀 Entrar</button>
                
                <div style="text-align: center; margin-top: 20px;">
                    <p style="color: #666; margin-bottom: 10px;">Não tem conta ainda?</p>
                    <button class="demo-btn" onclick="mostrarCadastro()">
                        ✨ Criar Nova Conta
                    </button>
                </div>
            </div>

            <!-- Formulário de Cadastro -->
            <div id="cadastro-form" style="display: none;">
                <div class="form-group">
                    <label class="form-label">👤 Escolha um usuário</label>
                    <input type="text" id="cadastro-usuario" class="form-input" placeholder="Digite um nome de usuário">
                </div>
                <div class="form-group">
                    <label class="form-label">📧 Email</label>
                    <input type="email" id="cadastro-email" class="form-input" placeholder="Digite seu email">
                </div>
                <div class="form-group">
                    <label class="form-label">🔒 Crie uma senha</label>
                    <input type="password" id="cadastro-senha" class="form-input" placeholder="Digite uma senha">
                </div>
                <div class="form-group">
                    <label class="form-label">🔒 Confirme a senha</label>
                    <input type="password" id="cadastro-confirma" class="form-input" placeholder="Digite a senha novamente">
                </div>
                <button class="form-btn" onclick="fazerCadastro()">🎉 Criar Conta</button>
                
                <div style="text-align: center; margin-top: 20px;">
                    <p style="color: #666; margin-bottom: 10px;">Já tem conta?</p>
                    <button class="demo-btn" onclick="mostrarLoginForm()">
                        🔑 Fazer Login
                    </button>
                </div>
            </div>
        </div>
    </div>

    <div class="container">
        <header>
            <h1>🎮 Jogos Educativos</h1>
            <p class="subtitle">Plataforma educativa interativa completa com planos Básico, Premium e Ultra!</p>
            <div style="font-size: 2.5rem; margin-top: 20px;">🌟📚🎯🧠✨🚀🏆</div>
            <div class="version-badge">VERSÃO COMPLETA - 100% FUNCIONAL!</div>
        </header>

        <!-- Sistema de Pontuação Global -->
        <div class="score-system">
            <div class="score-title">📊 Seu Progresso Global</div>
            <div class="score-stats">
                <div class="score-stat">
                    <div class="score-number" id="total-points">0</div>
                    <div class="score-label">Pontos Totais</div>
                </div>
                <div class="score-stat">
                    <div class="score-number" id="games-played">0</div>
                    <div class="score-label">Jogos Jogados</div>
                </div>
                <div class="score-stat">
                    <div class="score-number" id="achievements">0</div>
                    <div class="score-label">Conquistas</div>
                </div>
                <div class="score-stat">
                    <div class="score-number" id="streak">0</div>
                    <div class="score-label">Sequência</div>
                </div>
                <div class="score-stat">
                    <div class="score-number" id="total-coins">0</div>
                    <div class="score-label">💰 Moedas</div>
                </div>
            </div>
        </div>

        <div class="games-grid">
            <!-- Desafio Matemático -->
            <div class="game-card">
                <div class="game-icon">🔢</div>
                <h3 class="game-title">Desafio Matemático</h3>
                <p class="game-description">Resolva operações matemáticas contra o tempo!</p>
                <div class="score-display">⭐ Melhor: <span id="math-best">0</span> pontos</div>
                <button class="play-button" onclick="abrirJogo('math')">🚀 Jogar Agora</button>
            </div>

            <!-- Quiz de Português -->
            <div class="game-card">
                <div class="game-icon">📚</div>
                <h3 class="game-title">Quiz de Português</h3>
                <p class="game-description">Teste seus conhecimentos de gramática e literatura!</p>
                <div class="score-display">⭐ Melhor: <span id="portuguese-best">0</span> pontos</div>
                <button class="play-button" onclick="abrirJogo('portuguese')">🚀 Jogar Agora</button>
            </div>

            <!-- Quiz de Geografia -->
            <div class="game-card">
                <div class="game-icon">🌍</div>
                <h3 class="game-title">Quiz de Geografia</h3>
                <p class="game-description">Explore o mundo através de perguntas!</p>
                <div class="score-display">⭐ Melhor: <span id="geography-best">0</span> pontos</div>
                <button class="play-button" onclick="abrirJogo('geography')">🚀 Jogar Agora</button>
            </div>

            <!-- Quiz de História -->
            <div class="game-card">
                <div class="game-icon">🏛️</div>
                <h3 class="game-title">Quiz de História</h3>
                <p class="game-description">Viaje no tempo e teste seus conhecimentos!</p>
                <div class="score-display">⭐ Melhor: <span id="history-best">0</span> pontos</div>
                <button class="play-button" onclick="abrirJogo('history')">🚀 Jogar Agora</button>
            </div>

            <!-- Quiz de Ciências -->
            <div class="game-card">
                <div class="game-icon">🔬</div>
                <h3 class="game-title">Quiz de Ciências</h3>
                <p class="game-description">Explore o mundo da ciência e natureza!</p>
                <div class="score-display">⭐ Melhor: <span id="science-best">0</span> pontos</div>
                <button class="play-button" onclick="abrirJogo('science')">🚀 Jogar Agora</button>
            </div>

            <!-- Jogo da Memória -->
            <div class="game-card">
                <div class="game-icon">🧠</div>
                <h3 class="game-title">Jogo da Memória</h3>
                <p class="game-description">Teste sua memória com cartas coloridas!</p>
                <div class="score-display">⭐ Melhor: <span id="memory-best">0</span> pontos</div>
                <button class="play-button" onclick="abrirJogo('memory')">🚀 Jogar Agora</button>
            </div>

            <!-- Caça Palavras -->
            <div class="game-card">
                <div class="game-icon">🔍</div>
                <h3 class="game-title">Caça Palavras</h3>
                <p class="game-description">Encontre palavras escondidas no grid!</p>
                <div class="score-display">⭐ Melhor: <span id="wordsearch-best">0</span> pontos</div>
                <button class="play-button" onclick="abrirJogo('wordsearch')">🚀 Jogar Agora</button>
            </div>

            <!-- Quiz de Inglês -->
            <div class="game-card">
                <div class="game-icon">🇺🇸</div>
                <h3 class="game-title">Quiz de Inglês</h3>
                <p class="game-description">Pratique seu inglês com perguntas divertidas!</p>
                <div class="score-display">⭐ Melhor: <span id="english-best">0</span> pontos</div>
                <button class="play-button" onclick="abrirJogo('english')">🚀 Jogar Agora</button>
            </div>

            <!-- Quebra-Cabeça Numérico -->
            <div class="game-card">
                <div class="game-icon">🧩</div>
                <h3 class="game-title">Quebra-Cabeça Numérico</h3>
                <p class="game-description">Organize os números em sequência!</p>
                <div class="score-display">⭐ Melhor: <span id="puzzle-best">0</span> pontos</div>
                <button class="play-button" onclick="abrirJogo('puzzle')">🚀 Jogar Agora</button>
            </div>
        </div>
    </div>

    <!-- Modal do Desafio Matemático -->
    <div id="math-modal" class="game-modal">
        <div class="modal-content">
            <button class="close-button" onclick="fecharModal()">&times;</button>
            <h2 style="text-align: center; margin-bottom: 30px; color: #4a5568;">🔢 Desafio Matemático</h2>
            
            <div class="game-interface">
                <div class="game-stats">
                    <div class="stat-item">
                        <div>Pontos: <span id="math-points">0</span></div>
                    </div>
                    <div class="stat-item">
                        <div>Tempo: <span id="math-timer">30</span>s</div>
                    </div>
                    <div class="stat-item">
                        <div>Acertos: <span id="math-correct">0</span></div>
                    </div>
                    <div class="stat-item">
                        <div>Sequência: <span id="math-streak">0</span></div>
                    </div>
                </div>

                <div class="question-area" id="math-question">
                    Clique em "Iniciar Jogo" para começar!
                </div>

                <input type="number" class="answer-input" id="math-answer" placeholder="Digite sua resposta" style="display: none;">

                <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 15px;">
                    <button onclick="iniciarJogoMatematico()" id="math-start-btn" class="control-btn">
                        🚀 Iniciar Jogo
                    </button>
                    <button onclick="verificarRespostaMatematica()" id="math-submit-btn" class="control-btn secondary" style="display: none;">
                        ✅ Confirmar
                    </button>
                </div>
            </div>
        </div>
    </div>

    <!-- Modal da Loja -->
    <div id="shop-modal" class="game-modal">
        <div class="modal-content" style="max-width: 900px;">
            <button class="close-button" onclick="fecharLoja()">&times;</button>
            <h2 style="text-align: center; margin-bottom: 30px; color: #4a5568;">🛒 Loja de Itens</h2>
            
            <div style="text-align: center; margin-bottom: 30px;">
                <div style="background: linear-gradient(135deg, #ffd700, #ffed4e); color: #333; padding: 15px 25px; border-radius: 20px; display: inline-block; font-size: 1.3rem; font-weight: bold;">
                    💰 Suas Moedas: <span id="shop-coins">0</span>
                </div>
            </div>
            
            <div class="shop-grid" id="shop-items">
                <!-- Itens da loja serão carregados aqui -->
            </div>
        </div>
    </div>

    <!-- Modal dos Planos -->
    <div id="plans-modal" class="game-modal">
        <div class="modal-content" style="max-width: 1000px;">
            <button class="close-button" onclick="fecharPlanos()">&times;</button>
            <h2 style="text-align: center; margin-bottom: 30px; color: #4a5568;">⭐ Planos de Assinatura</h2>
            
            <div class="plans-grid" id="plans-container">
                <!-- Planos serão carregados aqui -->
            </div>

            <div class="plan-benefits">
                <h3 style="text-align: center; margin-bottom: 20px; color: #4a5568;">🎁 Compare os Benefícios</h3>
                
                <div class="benefit-item">
                    <div class="benefit-icon">🎮</div>
                    <div class="benefit-text">
                        <strong>Acesso aos Jogos:</strong><br>
                        <span style="color: #718096;">Básico: 5 jogos</span> | 
                        <span style="color: #9f7aea;">Premium: 9 jogos</span> | 
                        <span style="color: #ff8c00;">Ultra: Todos os jogos + Exclusivos</span>
                    </div>
                </div>

                <div class="benefit-item">
                    <div class="benefit-icon">💰</div>
                    <div class="benefit-text">
                        <strong>Moedas por Jogo:</strong><br>
                        <span style="color: #718096;">Básico: 1x</span> | 
                        <span style="color: #9f7aea;">Premium: 2x</span> | 
                        <span style="color: #ff8c00;">Ultra: 3x</span>
                    </div>
                </div>

                <div class="benefit-item">
                    <div class="benefit-icon">🛒</div>
                    <div class="benefit-text">
                        <strong>Desconto na Loja:</strong><br>
                        <span style="color: #718096;">Básico: 0%</span> | 
                        <span style="color: #9f7aea;">Premium: 20%</span> | 
                        <span style="color: #ff8c00;">Ultra: 50%</span>
                    </div>
                </div>

                <div class="benefit-item">
                    <div class="benefit-icon">🎯</div>
                    <div class="benefit-text">
                        <strong>Recursos Especiais:</strong><br>
                        <span style="color: #718096;">Básico: Básicos</span> | 
                        <span style="color: #9f7aea;">Premium: Estatísticas + Temas</span> | 
                        <span style="color: #ff8c00;">Ultra: Tudo + Suporte VIP</span>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Modal do Painel de Administração -->
    <div id="admin-modal" class="game-modal">
        <div class="modal-content" style="max-width: 900px;">
            <button class="close-button" onclick="fecharPainelAdmin()">&times;</button>
            <h2 style="text-align: center; margin-bottom: 30px; color: #4a5568;">⚙️ Painel de Administração</h2>
            
            <div class="admin-interface" style="background: rgba(255, 255, 255, 0.95); border-radius: 20px; padding: 30px;">
                
                <!-- Status do Sistema -->
                <div style="background: linear-gradient(135deg, #667eea, #764ba2); color: white; padding: 20px; border-radius: 15px; margin-bottom: 25px;">
                    <h3 style="margin-bottom: 15px;">📊 Status do Sistema</h3>
                    <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(150px, 1fr)); gap: 15px;">
                        <div style="background: rgba(255,255,255,0.2); padding: 15px; border-radius: 10px; text-align: center;">
                            <div style="font-size: 1.5rem; font-weight: bold;" id="total-users">0</div>
                            <div style="font-size: 0.9rem;">Usuários Totais</div>
                        </div>
                        <div style="background: rgba(255,255,255,0.2); padding: 15px; border-radius: 10px; text-align: center;">
                            <div style="font-size: 1.5rem; font-weight: bold;" id="online-users">1</div>
                            <div style="font-size: 0.9rem;">Usuários Online</div>
                        </div>
                        <div style="background: rgba(255,255,255,0.2); padding: 15px; border-radius: 10px; text-align: center;">
                            <div style="font-size: 1.5rem; font-weight: bold;" id="total-games-played">0</div>
                            <div style="font-size: 0.9rem;">Jogos Realizados</div>
                        </div>
                    </div>
                </div>

                <!-- Gerenciamento de Usuários -->
                <div style="background: #f7fafc; padding: 20px; border-radius: 15px; margin-bottom: 25px;">
                    <h3 style="margin-bottom: 15px; color: #4a5568;">👥 Gerenciamento de Usuários</h3>
                    <div id="users-list" style="max-height: 300px; overflow-y: auto;">
                        <!-- Lista de usuários será carregada aqui -->
                    </div>
                </div>

                <!-- Ferramentas de Administração -->
                <div style="background: #f7fafc; padding: 20px; border-radius: 15px;">
                    <h3 style="margin-bottom: 15px; color: #4a5568;">🛠️ Ferramentas</h3>
                    <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 15px;">
                        <button onclick="limparDadosGerais()" class="control-btn" style="background: linear-gradient(135deg, #ff6b6b, #ee5a24);">
                            🗑️ Limpar Dados Gerais
                        </button>
                        <button onclick="exportarDados()" class="control-btn secondary">
                            📥 Exportar Dados
                        </button>
                        <button onclick="gerarRelatorio()" class="control-btn">
                            📊 Gerar Relatório
                        </button>
                        <button onclick="atualizarSistema()" class="control-btn" style="background: linear-gradient(135deg, #9f7aea, #805ad5);">
                            🔄 Atualizar Sistema
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Notificação de Recompensas -->
    <div id="reward-notification" class="reward-notification">
        <div id="reward-text">🎉 Recompensa!</div>
    </div>

    <script>
        // Variáveis globais
        let usuarioLogado = null;
        let sistemaPontuacao = null;
        let jogoAtual = null;
        let sistemaMonetario = null;
        let sistemaPlanos = null;

        // Inicializar contas especiais
        function inicializarContasEspeciais() {
            const usuariosExistentes = JSON.parse(localStorage.getItem('usuarios') || '{}');
            
            // Conta do dono vitor202
            if (!usuariosExistentes['vitor202']) {
                usuariosExistentes['vitor202'] = {
                    senha: 'dono',
                    email: 'vitor202@jogoseducativos.com',
                    dataCriacao: new Date().toISOString(),
                    isAdmin: true,
                    isOwner: true,
                    verificado: true,
                    nivel: 'DONO',
                    plano: 'ultra',
                    permissoes: ['all']
                };
            } else {
                // Garantir que vitor202 sempre tenha privilégios de dono
                usuariosExistentes['vitor202'].isAdmin = true;
                usuariosExistentes['vitor202'].isOwner = true;
                usuariosExistentes['vitor202'].verificado = true;
                usuariosExistentes['vitor202'].nivel = 'DONO';
                usuariosExistentes['vitor202'].plano = 'ultra';
                usuariosExistentes['vitor202'].permissoes = ['all'];
            }
            
            // Conta da professora bruna
            if (!usuariosExistentes['bruna']) {
                usuariosExistentes['bruna'] = {
                    senha: 'bruna',
                    email: 'bruna@jogoseducativos.com',
                    dataCriacao: new Date().toISOString(),
                    isAdmin: true,
                    isProfessora: true,
                    verificado: true,
                    nivel: 'PROFESSORA',
                    plano: 'premium',
                    permissoes: ['admin', 'educacao']
                };
            } else {
                // Garantir que bruna sempre tenha privilégios de professora
                usuariosExistentes['bruna'].isAdmin = true;
                usuariosExistentes['bruna'].isProfessora = true;
                usuariosExistentes['bruna'].verificado = true;
                usuariosExistentes['bruna'].nivel = 'PROFESSORA';
                usuariosExistentes['bruna'].plano = 'premium';
                usuariosExistentes['bruna'].permissoes = ['admin', 'educacao'];
            }
            
            localStorage.setItem('usuarios', JSON.stringify(usuariosExistentes));
        }

        // Executar na inicialização
        inicializarContasEspeciais();

        // Sistema de Planos
        class SistemaPlanos {
            constructor() {
                this.planoAtual = this.obterPlanoUsuario();
                this.atualizarBadgePlano();
            }

            obterPlanoUsuario() {
                const usuarios = JSON.parse(localStorage.getItem('usuarios') || '{}');
                const dadosUsuario = usuarios[usuarioLogado];
                return dadosUsuario?.plano || 'basic';
            }

            obterPlanos() {
                return [
                    {
                        id: 'basic',
                        nome: 'Básico',
                        icone: '📦',
                        preco: 'Grátis',
                        periodo: 'Para sempre',
                        recursos: [
                            '✅ 5 jogos educativos',
                            '✅ Sistema de pontuação',
                            '✅ Moedas básicas (1x)',
                            '✅ Salvamento de progresso',
                            '❌ Sem desconto na loja',
                            '❌ Recursos limitados'
                        ],
                        multiplicadorMoedas: 1,
                        descontoLoja: 0,
                        jogosLiberados: 5
                    },
                    {
                        id: 'premium',
                        nome: 'Premium',
                        icone: '⭐',
                        preco: 'R$ 9,90',
                        periodo: 'por mês',
                        popular: true,
                        recursos: [
                            '✅ 9 jogos educativos',
                            '✅ Moedas dobradas (2x)',
                            '✅ 20% desconto na loja',
                            '✅ Estatísticas avançadas',
                            '✅ Temas personalizados',
                            '✅ Suporte prioritário'
                        ],
                        multiplicadorMoedas: 2,
                        descontoLoja: 20,
                        jogosLiberados: 9
                    },
                    {
                        id: 'ultra',
                        nome: 'Ultra',
                        icone: '👑',
                        preco: 'R$ 19,90',
                        periodo: 'por mês',
                        recursos: [
                            '✅ TODOS os jogos + exclusivos',
                            '✅ Moedas triplicadas (3x)',
                            '✅ 50% desconto na loja',
                            '✅ Acesso antecipado',
                            '✅ Avatar dourado exclusivo',
                            '✅ Suporte VIP 24/7'
                        ],
                        multiplicadorMoedas: 3,
                        descontoLoja: 50,
                        jogosLiberados: 999
                    }
                ];
            }

            alterarPlano(novoPlano) {
                const usuarios = JSON.parse(localStorage.getItem('usuarios') || '{}');
                if (usuarios[usuarioLogado]) {
                    usuarios[usuarioLogado].plano = novoPlano;
                    localStorage.setItem('usuarios', JSON.stringify(usuarios));
                    this.planoAtual = novoPlano;
                    this.atualizarBadgePlano();
                    
                    // Reinicializar sistema monetário com novos multiplicadores
                    if (sistemaMonetario) {
                        sistemaMonetario = new SistemaMonetario();
                    }
                    
                    criarNotificacao(`🎉 Plano alterado para ${this.obterPlanos().find(p => p.id === novoPlano).nome}!`, 'success');
                    this.atualizarModalPlanos();
                }
            }

            atualizarBadgePlano() {
                const badge = document.getElementById('plan-badge');
                const planName = document.getElementById('plan-name');
                const plano = this.obterPlanos().find(p => p.id === this.planoAtual);
                
                if (badge && planName && plano) {
                    badge.className = `plan-badge ${this.planoAtual}`;
                    planName.textContent = `${plano.icone} Plano ${plano.nome}`;
                    badge.style.display = 'block';
                }
            }

            atualizarModalPlanos() {
                const container = document.getElementById('plans-container');
                if (!container) return;

                const planos = this.obterPlanos();
                let html = '';

                planos.forEach(plano => {
                    const isAtual = plano.id === this.planoAtual;
                    
                    html += `
                        <div class="plan-card ${plano.id} ${isAtual ? 'current' : ''}">
                            ${plano.popular ? '<div class="plan-popular">MAIS POPULAR</div>' : ''}
                            <div class="plan-icon">${plano.icone}</div>
                            <div class="plan-name">${plano.nome}</div>
                            <div class="plan-price">${plano.preco}</div>
                            <div class="plan-period">${plano.periodo}</div>
                            <ul class="plan-features">
                                ${plano.recursos.map(recurso => `<li>${recurso}</li>`).join('')}
                            </ul>
                            <button class="plan-btn ${plano.id} ${isAtual ? 'current' : ''}" 
                                    onclick="sistemaPlanos.alterarPlano('${plano.id}')"
                                    ${isAtual ? 'disabled' : ''}>
                                ${isAtual ? '✅ Plano Atual' : `🚀 Escolher ${plano.nome}`}
                            </button>
                        </div>
                    `;
                });

                container.innerHTML = html;
            }

            obterMultiplicadorMoedas() {
                const plano = this.obterPlanos().find(p => p.id === this.planoAtual);
                return plano?.multiplicadorMoedas || 1;
            }

            obterDescontoLoja() {
                const plano = this.obterPlanos().find(p => p.id === this.planoAtual);
                return plano?.descontoLoja || 0;
            }

            podeJogar(indiceJogo) {
                const plano = this.obterPlanos().find(p => p.id === this.planoAtual);
                return indiceJogo < (plano?.jogosLiberados || 5);
            }
        }

        // Sistema de Login
        function mostrarLogin() {
            // Resetar para o formulário de login
            document.getElementById('login-form').style.display = 'block';
            document.getElementById('cadastro-form').style.display = 'none';
            
            // Limpar campos
            document.getElementById('login-usuario').value = '';
            document.getElementById('login-senha').value = '';
            document.getElementById('cadastro-usuario').value = '';
            document.getElementById('cadastro-email').value = '';
            document.getElementById('cadastro-senha').value = '';
            document.getElementById('cadastro-confirma').value = '';
            
            document.getElementById('login-modal').style.display = 'flex';
        }

        function fecharLogin() {
            document.getElementById('login-modal').style.display = 'none';
        }

        function mostrarCadastro() {
            document.getElementById('login-form').style.display = 'none';
            document.getElementById('cadastro-form').style.display = 'block';
        }

        function mostrarLoginForm() {
            document.getElementById('cadastro-form').style.display = 'none';
            document.getElementById('login-form').style.display = 'block';
        }

        function fazerCadastro() {
            const usuario = document.getElementById('cadastro-usuario').value.trim();
            const email = document.getElementById('cadastro-email').value.trim();
            const senha = document.getElementById('cadastro-senha').value;
            const confirmaSenha = document.getElementById('cadastro-confirma').value;

            // Validações
            if (!usuario || !email || !senha || !confirmaSenha) {
                criarNotificacao('❌ Preencha todos os campos!', 'error');
                return;
            }

            if (usuario.length < 3) {
                criarNotificacao('❌ Usuário deve ter pelo menos 3 caracteres!', 'error');
                return;
            }

            if (senha.length < 6) {
                criarNotificacao('❌ Senha deve ter pelo menos 6 caracteres!', 'error');
                return;
            }

            if (senha !== confirmaSenha) {
                criarNotificacao('❌ As senhas não coincidem!', 'error');
                return;
            }

            // Verificar se usuário já existe
            const usuariosExistentes = JSON.parse(localStorage.getItem('usuarios') || '{}');
            if (usuariosExistentes[usuario]) {
                criarNotificacao('❌ Este usuário já existe! Escolha outro.', 'error');
                return;
            }

            // Salvar novo usuário
            usuariosExistentes[usuario] = {
                senha: senha,
                email: email,
                dataCriacao: new Date().toISOString(),
                plano: 'basic'
            };
            localStorage.setItem('usuarios', JSON.stringify(usuariosExistentes));

            criarNotificacao('🎉 Conta criada com sucesso!', 'success');
            
            // Fazer login automático
            usuarioLogado = usuario;
            document.getElementById('user-name').textContent = usuario;
            document.getElementById('login-section').style.display = 'none';
            document.getElementById('user-section').style.display = 'block';
            fecharLogin();
            
            // Inicializar sistemas
            sistemaPontuacao = new SistemaPontuacao();
            sistemaMonetario = new SistemaMonetario();
            sistemaPlanos = new SistemaPlanos();
            
            // Mostrar elementos
            document.getElementById('currency-display').style.display = 'block';
            document.getElementById('shop-btn').style.display = 'block';
            document.getElementById('plans-btn').style.display = 'block';
            
            setTimeout(() => {
                criarNotificacao(`🎮 Bem-vindo à plataforma, ${usuario}!`, 'success');
            }, 1000);
        }

        function fazerLogin() {
            const usuario = document.getElementById('login-usuario').value.trim();
            const senha = document.getElementById('login-senha').value;

            if (!usuario || !senha) {
                criarNotificacao('❌ Preencha usuário e senha!', 'error');
                return;
            }

            // Verificar usuários cadastrados
            const usuariosExistentes = JSON.parse(localStorage.getItem('usuarios') || '{}');
            
            if (usuariosExistentes[usuario] && usuariosExistentes[usuario].senha === senha) {
                usuarioLogado = usuario;
                const dadosUsuario = usuariosExistentes[usuario];
                
                document.getElementById('user-name').textContent = usuario;
                
                // Mostrar badges de verificação
                mostrarBadgesUsuario(dadosUsuario);
                
                // Mostrar botão admin se for administrador
                if (dadosUsuario.isAdmin) {
                    document.getElementById('admin-panel-btn').style.display = 'block';
                }
                
                document.getElementById('login-section').style.display = 'none';
                document.getElementById('user-section').style.display = 'block';
                fecharLogin();
                
                // Inicializar sistemas
                sistemaPontuacao = new SistemaPontuacao();
                sistemaMonetario = new SistemaMonetario();
                sistemaPlanos = new SistemaPlanos();
                
                // Mostrar elementos do sistema
                document.getElementById('currency-display').style.display = 'block';
                document.getElementById('shop-btn').style.display = 'block';
                document.getElementById('plans-btn').style.display = 'block';
                
                // Mensagem personalizada baseada no nível
                let mensagem = `🎉 Bem-vindo de volta, ${usuario}!`;
                if (dadosUsuario.isOwner) {
                    mensagem = `👑 Bem-vindo de volta, Dono ${usuario}!`;
                } else if (dadosUsuario.isProfessora) {
                    mensagem = `👩‍🏫 Bem-vinda de volta, Professora ${usuario}!`;
                } else if (dadosUsuario.isAdmin) {
                    mensagem = `⚡ Bem-vindo de volta, Admin ${usuario}!`;
                }
                
                criarNotificacao(mensagem, 'success');
            } else {
                criarNotificacao('❌ Usuário ou senha incorretos!', 'error');
            }
        }

        function logout() {
            usuarioLogado = null;
            sistemaPontuacao = null;
            sistemaMonetario = null;
            sistemaPlanos = null;
            document.getElementById('login-section').style.display = 'block';
            document.getElementById('user-section').style.display = 'none';
            document.getElementById('admin-panel-btn').style.display = 'none';
            document.getElementById('user-badges').innerHTML = '';
            document.getElementById('currency-display').style.display = 'none';
            document.getElementById('shop-btn').style.display = 'none';
            document.getElementById('plans-btn').style.display = 'none';
            document.getElementById('plan-badge').style.display = 'none';
            criarNotificacao('👋 Logout realizado com sucesso!', 'success');
        }

        // Função para mostrar badges do usuário
        function mostrarBadgesUsuario(dadosUsuario) {
            const badgesContainer = document.getElementById('user-badges');
            let badges = '';
            
            if (dadosUsuario.isOwner) {
                badges += '<span style="background: linear-gradient(135deg, #ffd700, #ffed4e); color: #000; padding: 3px 8px; border-radius: 10px; font-size: 0.75rem; font-weight: bold; margin-right: 5px;">👑 DONO DO SITE</span>';
            }
            
            if (dadosUsuario.isProfessora) {
                badges += '<span style="background: linear-gradient(135deg, #ff6b6b, #ee5a24); color: white; padding: 3px 8px; border-radius: 10px; font-size: 0.75rem; font-weight: bold; margin-right: 5px;">👩‍🏫 PROFESSORA</span>';
            }
            
            if (dadosUsuario.isAdmin) {
                badges += '<span style="background: linear-gradient(135deg, #9f7aea, #805ad5); color: white; padding: 3px 8px; border-radius: 10px; font-size: 0.75rem; font-weight: bold; margin-right: 5px;">⚡ ADMIN</span>';
            }
            
            if (dadosUsuario.verificado) {
                badges += '<span style="background: linear-gradient(135deg, #48bb78, #38a169); color: white; padding: 3px 8px; border-radius: 10px; font-size: 0.75rem; font-weight: bold;">✅ VERIFICADO</span>';
            }
            
            badgesContainer.innerHTML = badges;
        }

        // Funções dos Planos
        function abrirPlanos() {
            if (!usuarioLogado) {
                criarNotificacao('❌ Faça login para ver os planos!', 'error');
                mostrarLogin();
                return;
            }

            document.getElementById('plans-modal').style.display = 'flex';
            if (sistemaPlanos) {
                sistemaPlanos.atualizarModalPlanos();
            }
        }

        function fecharPlanos() {
            document.getElementById('plans-modal').style.display = 'none';
        }

        // Funções do Painel de Administração
        function abrirPainelAdmin() {
            const usuariosExistentes = JSON.parse(localStorage.getItem('usuarios') || '{}');
            const dadosUsuario = usuariosExistentes[usuarioLogado];
            
            if (!dadosUsuario || !dadosUsuario.isAdmin) {
                criarNotificacao('❌ Acesso negado! Apenas administradores.', 'error');
                return;
            }
            
            document.getElementById('admin-modal').style.display = 'flex';
            carregarDadosAdmin();
        }

        function fecharPainelAdmin() {
            document.getElementById('admin-modal').style.display = 'none';
        }

        function carregarDadosAdmin() {
            const usuarios = JSON.parse(localStorage.getItem('usuarios') || '{}');
            const totalUsuarios = Object.keys(usuarios).length;
            
            document.getElementById('total-users').textContent = totalUsuarios;
            
            // Calcular total de jogos realizados
            let totalJogos = 0;
            Object.keys(usuarios).forEach(user => {
                totalJogos += parseInt(localStorage.getItem(`${user}-gamesPlayed`) || '0');
            });
            document.getElementById('total-games-played').textContent = totalJogos;
            
            // Carregar lista de usuários
            carregarListaUsuarios();
        }

        function carregarListaUsuarios() {
            const usuarios = JSON.parse(localStorage.getItem('usuarios') || '{}');
            const container = document.getElementById('users-list');
            
            let html = '';
            Object.keys(usuarios).forEach(username => {
                const user = usuarios[username];
                const pontos = localStorage.getItem(`${username}-totalPoints`) || '0';
                const jogos = localStorage.getItem(`${username}-gamesPlayed`) || '0';
                const plano = user.plano || 'basic';
                
                let badges = '';
                if (user.isOwner) badges += '<span style="background: #ffd700; color: #000; padding: 2px 6px; border-radius: 8px; font-size: 0.7rem; margin-right: 3px;">👑 DONO</span>';
                if (user.isProfessora) badges += '<span style="background: #ff6b6b; color: white; padding: 2px 6px; border-radius: 8px; font-size: 0.7rem; margin-right: 3px;">👩‍🏫 PROFESSORA</span>';
                if (user.isAdmin) badges += '<span style="background: #9f7aea; color: white; padding: 2px 6px; border-radius: 8px; font-size: 0.7rem; margin-right: 3px;">⚡ ADMIN</span>';
                if (user.verificado) badges += '<span style="background: #48bb78; color: white; padding: 2px 6px; border-radius: 8px; font-size: 0.7rem; margin-right: 3px;">✅ VERIFICADO</span>';
                
                // Badge do plano
                const planoBadge = plano === 'ultra' ? '👑 ULTRA' : plano === 'premium' ? '⭐ PREMIUM' : '📦 BÁSICO';
                const planoColor = plano === 'ultra' ? '#ff8c00' : plano === 'premium' ? '#9f7aea' : '#718096';
                badges += `<span style="background: ${planoColor}; color: white; padding: 2px 6px; border-radius: 8px; font-size: 0.7rem;">${planoBadge}</span>`;
                
                html += `
                    <div style="background: white; padding: 15px; border-radius: 10px; margin-bottom: 10px; border-left: 4px solid #4facfe;">
                        <div style="display: flex; justify-content: between; align-items: center; margin-bottom: 8px;">
                            <strong style="color: #2d3748;">${username}</strong>
                            <div>${badges}</div>
                        </div>
                        <div style="font-size: 0.85rem; color: #666;">
                            📧 ${user.email} | 🎮 ${jogos} jogos | ⭐ ${pontos} pontos
                        </div>
                        <div style="font-size: 0.75rem; color: #999; margin-top: 5px;">
                            Criado em: ${new Date(user.dataCriacao).toLocaleDateString('pt-BR')}
                        </div>
                    </div>
                `;
            });
            
            container.innerHTML = html || '<p style="text-align: center; color: #666;">Nenhum usuário encontrado.</p>';
        }

        function limparDadosGerais() {
            if (!confirm('⚠️ ATENÇÃO: Isso irá limpar TODOS os dados de pontuação de TODOS os usuários! Continuar?')) {
                return;
            }
            
            const usuarios = JSON.parse(localStorage.getItem('usuarios') || '{}');
            Object.keys(usuarios).forEach(username => {
                localStorage.removeItem(`${username}-totalPoints`);
                localStorage.removeItem(`${username}-gamesPlayed`);
                localStorage.removeItem(`${username}-achievements`);
                localStorage.removeItem(`${username}-streak`);
                localStorage.removeItem(`${username}-coins`);
                localStorage.removeItem(`${username}-items`);
                localStorage.removeItem(`${username}-math-best`);
                localStorage.removeItem(`${username}-portuguese-best`);
                localStorage.removeItem(`${username}-geography-best`);
                localStorage.removeItem(`${username}-history-best`);
                localStorage.removeItem(`${username}-science-best`);
                localStorage.removeItem(`${username}-memory-best`);
                localStorage.removeItem(`${username}-wordsearch-best`);
                localStorage.removeItem(`${username}-english-best`);
                localStorage.removeItem(`${username}-puzzle-best`);
            });
            
            criarNotificacao('🗑️ Dados de pontuação limpos com sucesso!', 'success');
            carregarDadosAdmin();
            
            // Atualizar sistemas se o usuário atual estiver logado
            if (sistemaPontuacao) {
                sistemaPontuacao = new SistemaPontuacao();
            }
            if (sistemaMonetario) {
                sistemaMonetario = new SistemaMonetario();
            }
        }

        function exportarDados() {
            const usuarios = JSON.parse(localStorage.getItem('usuarios') || '{}');
            const dados = {
                usuarios: usuarios,
                pontuacoes: {},
                timestamp: new Date().toISOString()
            };
            
            Object.keys(usuarios).forEach(username => {
                dados.pontuacoes[username] = {
                    totalPoints: localStorage.getItem(`${username}-totalPoints`) || '0',
                    gamesPlayed: localStorage.getItem(`${username}-gamesPlayed`) || '0',
                    achievements: localStorage.getItem(`${username}-achievements`) || '0',
                    streak: localStorage.getItem(`${username}-streak`) || '0',
                    coins: localStorage.getItem(`${username}-coins`) || '0',
                    items: localStorage.getItem(`${username}-items`) || '[]',
                    mathBest: localStorage.getItem(`${username}-math-best`) || '0',
                    portugueseBest: localStorage.getItem(`${username}-portuguese-best`) || '0',
                    geographyBest: localStorage.getItem(`${username}-geography-best`) || '0',
                    historyBest: localStorage.getItem(`${username}-history-best`) || '0',
                    scienceBest: localStorage.getItem(`${username}-science-best`) || '0',
                    memoryBest: localStorage.getItem(`${username}-memory-best`) || '0',
                    wordsearchBest: localStorage.getItem(`${username}-wordsearch-best`) || '0',
                    englishBest: localStorage.getItem(`${username}-english-best`) || '0',
                    puzzleBest: localStorage.getItem(`${username}-puzzle-best`) || '0'
                };
            });
            
            const blob = new Blob([JSON.stringify(dados, null, 2)], { type: 'application/json' });
            const url = URL.createObjectURL(blob);
            const a = document.createElement('a');
            a.href = url;
            a.download = `jogos-educativos-backup-${new Date().toISOString().split('T')[0]}.json`;
            a.click();
            URL.revokeObjectURL(url);
            
            criarNotificacao('📥 Dados exportados com sucesso!', 'success');
        }

        function gerarRelatorio() {
            const usuarios = JSON.parse(localStorage.getItem('usuarios') || '{}');
            let relatorio = '📊 RELATÓRIO DO SISTEMA - JOGOS EDUCATIVOS\n';
            relatorio += '='.repeat(50) + '\n\n';
            relatorio += `Data: ${new Date().toLocaleString('pt-BR')}\n`;
            relatorio += `Total de usuários: ${Object.keys(usuarios).length}\n\n`;
            
            relatorio += 'USUÁRIOS REGISTRADOS:\n';
            relatorio += '-'.repeat(30) + '\n';
            
            Object.keys(usuarios).forEach(username => {
                const user = usuarios[username];
                const pontos = localStorage.getItem(`${username}-totalPoints`) || '0';
                const jogos = localStorage.getItem(`${username}-gamesPlayed`) || '0';
                const moedas = localStorage.getItem(`${username}-coins`) || '0';
                const plano = user.plano || 'basic';
                
                relatorio += `👤 ${username}\n`;
                relatorio += `   📧 Email: ${user.email}\n`;
                relatorio += `   🎮 Jogos: ${jogos} | ⭐ Pontos: ${pontos} | 💰 Moedas: ${moedas}\n`;
                relatorio += `   📦 Plano: ${plano.toUpperCase()}\n`;
                relatorio += `   📅 Criado: ${new Date(user.dataCriacao).toLocaleDateString('pt-BR')}\n`;
                if (user.isOwner) relatorio += `   👑 DONO DO SITE\n`;
                if (user.isAdmin) relatorio += `   ⚡ ADMINISTRADOR\n`;
                if (user.verificado) relatorio += `   ✅ VERIFICADO\n`;
                relatorio += '\n';
            });
            
            const blob = new Blob([relatorio], { type: 'text/plain' });
            const url = URL.createObjectURL(blob);
            const a = document.createElement('a');
            a.href = url;
            a.download = `relatorio-sistema-${new Date().toISOString().split('T')[0]}.txt`;
            a.click();
            URL.revokeObjectURL(url);
            
            criarNotificacao('📊 Relatório gerado com sucesso!', 'success');
        }

        function atualizarSistema() {
            criarNotificacao('🔄 Sistema atualizado com sucesso!', 'success');
            carregarDadosAdmin();
        }

        // Sistema Monetário
        class SistemaMonetario {
            constructor() {
                this.moedas = parseInt(localStorage.getItem(`${usuarioLogado}-coins`) || '0');
                this.itensComprados = JSON.parse(localStorage.getItem(`${usuarioLogado}-items`) || '[]');
                this.atualizarDisplay();
                this.inicializarLoja();
            }

            adicionarMoedas(quantidade, motivo = '') {
                // Aplicar multiplicador do plano
                const multiplicador = sistemaPlanos ? sistemaPlanos.obterMultiplicadorMoedas() : 1;
                const moedasFinais = quantidade * multiplicador;
                
                this.moedas += moedasFinais;
                this.salvar();
                this.atualizarDisplay();
                
                if (motivo) {
                    const textoMultiplicador = multiplicador > 1 ? ` (${multiplicador}x)` : '';
                    this.mostrarRecompensa(`+${moedasFinais} moedas por ${motivo}${textoMultiplicador}!`);
                }
            }

            gastarMoedas(quantidade) {
                // Aplicar desconto do plano
                const desconto = sistemaPlanos ? sistemaPlanos.obterDescontoLoja() : 0;
                const precoFinal = Math.round(quantidade * (1 - desconto / 100));
                
                if (this.moedas >= precoFinal) {
                    this.moedas -= precoFinal;
                    this.salvar();
                    this.atualizarDisplay();
                    return true;
                }
                return false;
            }

            comprarItem(itemId) {
                const item = this.obterItemPorId(itemId);
                if (!item) return false;

                if (this.itensComprados.includes(itemId)) {
                    criarNotificacao('❌ Você já possui este item!', 'error');
                    return false;
                }

                // Calcular preço com desconto
                const desconto = sistemaPlanos ? sistemaPlanos.obterDescontoLoja() : 0;
                const precoFinal = Math.round(item.preco * (1 - desconto / 100));

                if (this.gastarMoedas(item.preco)) {
                    this.itensComprados.push(itemId);
                    localStorage.setItem(`${usuarioLogado}-items`, JSON.stringify(this.itensComprados));
                    
                    const textoDesconto = desconto > 0 ? ` (${desconto}% desconto!)` : '';
                    criarNotificacao(`🎉 ${item.nome} comprado por ${precoFinal} moedas${textoDesconto}!`, 'success');
                    this.atualizarLoja();
                    return true;
                } else {
                    criarNotificacao('❌ Moedas insuficientes!', 'error');
                    return false;
                }
            }

            obterItemPorId(id) {
                const itens = this.obterItensLoja();
                return itens.find(item => item.id === id);
            }

            obterItensLoja() {
                return [
                    {
                        id: 'multiplicador_pontos',
                        nome: 'Multiplicador de Pontos',
                        descricao: 'Dobra os pontos ganhos nos próximos 5 jogos',
                        preco: 100,
                        icone: '⚡',
                        tipo: 'boost'
                    },
                    {
                        id: 'tempo_extra',
                        nome: 'Tempo Extra',
                        descricao: 'Adiciona +15 segundos no jogo de matemática',
                        preco: 75,
                        icone: '⏰',
                        tipo: 'boost'
                    },
                    {
                        id: 'dica_magica',
                        nome: 'Dica Mágica',
                        descricao: 'Revela uma resposta correta nos quizzes',
                        preco: 50,
                        icone: '💡',
                        tipo: 'boost'
                    },
                    {
                        id: 'escudo_erro',
                        nome: 'Escudo Anti-Erro',
                        descricao: 'Protege de 1 erro sem perder a sequência',
                        preco: 80,
                        icone: '🛡️',
                        tipo: 'boost'
                    },
                    {
                        id: 'avatar_dourado',
                        nome: 'Avatar Dourado',
                        descricao: 'Avatar especial com efeito dourado',
                        preco: 200,
                        icone: '👑',
                        tipo: 'cosmético'
                    },
                    {
                        id: 'tema_escuro',
                        nome: 'Tema Escuro',
                        descricao: 'Interface com tema escuro elegante',
                        preco: 150,
                        icone: '🌙',
                        tipo: 'cosmético'
                    }
                ];
            }

            inicializarLoja() {
                this.atualizarLoja();
            }

            atualizarLoja() {
                const container = document.getElementById('shop-items');
                if (!container) return;

                const itens = this.obterItensLoja();
                const desconto = sistemaPlanos ? sistemaPlanos.obterDescontoLoja() : 0;
                let html = '';

                itens.forEach(item => {
                    const jaComprado = this.itensComprados.includes(item.id);
                    const precoFinal = Math.round(item.preco * (1 - desconto / 100));
                    const podeComprar = this.moedas >= precoFinal && !jaComprado;

                    html += `
                        <div class="shop-item ${jaComprado ? 'owned' : ''}">
                            <div class="shop-item-icon">${item.icone}</div>
                            <div class="shop-item-name">${item.nome}</div>
                            <div class="shop-item-description">${item.descricao}</div>
                            ${!jaComprado ? 
                                `<div class="shop-item-price">
                                    💰 ${precoFinal} moedas
                                    ${desconto > 0 ? `<br><small style="text-decoration: line-through; opacity: 0.7;">${item.preco} moedas</small> <span style="color: #e53e3e; font-weight: bold;">-${desconto}%</span>` : ''}
                                 </div>
                                 <button class="shop-buy-btn" ${!podeComprar ? 'disabled' : ''} 
                                         onclick="sistemaMonetario.comprarItem('${item.id}')">
                                     ${podeComprar ? '🛒 Comprar' : '❌ Sem moedas'}
                                 </button>` :
                                `<div class="shop-owned-badge">✅ Adquirido</div>`
                            }
                        </div>
                    `;
                });

                container.innerHTML = html;
            }

            mostrarRecompensa(texto) {
                const notification = document.getElementById('reward-notification');
                const textElement = document.getElementById('reward-text');
                
                textElement.textContent = texto;
                notification.style.display = 'block';
                
                setTimeout(() => {
                    notification.style.display = 'none';
                }, 3000);
            }

            salvar() {
                localStorage.setItem(`${usuarioLogado}-coins`, this.moedas.toString());
            }

            atualizarDisplay() {
                document.getElementById('user-coins').textContent = this.moedas;
                document.getElementById('total-coins').textContent = this.moedas;
                const shopCoins = document.getElementById('shop-coins');
                if (shopCoins) shopCoins.textContent = this.moedas;
            }
        }

        // Sistema de Pontuação
        class SistemaPontuacao {
            constructor() {
                this.pontos = parseInt(localStorage.getItem(`${usuarioLogado}-totalPoints`) || '0');
                this.jogosJogados = parseInt(localStorage.getItem(`${usuarioLogado}-gamesPlayed`) || '0');
                this.conquistas = parseInt(localStorage.getItem(`${usuarioLogado}-achievements`) || '0');
                this.sequencia = parseInt(localStorage.getItem(`${usuarioLogado}-streak`) || '0');
                this.atualizarDisplay();
                this.carregarMelhoresPontuacoes();
            }

            adicionarPontos(pontos, jogo) {
                this.pontos += pontos;
                this.jogosJogados++;
                this.sequencia++;
                
                // Calcular moedas baseado nos pontos (1 moeda a cada 10 pontos)
                const moedasGanhas = Math.floor(pontos / 10);
                if (moedasGanhas > 0 && sistemaMonetario) {
                    sistemaMonetario.adicionarMoedas(moedasGanhas, jogo);
                }
                
                // Verificar conquistas
                this.verificarConquistas();
                
                this.salvar();
                this.atualizarDisplay();
            }

            verificarConquistas() {
                let conquistasAntigas = this.conquistas;
                
                if (this.pontos >= 100 && this.conquistas < 1) {
                    this.conquistas = 1;
                    if (sistemaMonetario) sistemaMonetario.adicionarMoedas(25, 'Primeira Conquista');
                }
                if (this.pontos >= 500 && this.conquistas < 2) {
                    this.conquistas = 2;
                    if (sistemaMonetario) sistemaMonetario.adicionarMoedas(25, 'Meio Milhar');
                }
                if (this.sequencia >= 10 && this.conquistas < 3) {
                    this.conquistas = 3;
                    if (sistemaMonetario) sistemaMonetario.adicionarMoedas(25, 'Sequência de Ouro');
                }
                if (this.jogosJogados >= 50 && this.conquistas < 4) {
                    this.conquistas = 4;
                    if (sistemaMonetario) sistemaMonetario.adicionarMoedas(25, 'Jogador Dedicado');
                }
                
                if (this.conquistas > conquistasAntigas) {
                    criarNotificacao(`🏆 Nova conquista desbloqueada! (+25 moedas)`, 'success');
                }
            }

            salvar() {
                localStorage.setItem(`${usuarioLogado}-totalPoints`, this.pontos.toString());
                localStorage.setItem(`${usuarioLogado}-gamesPlayed`, this.jogosJogados.toString());
                localStorage.setItem(`${usuarioLogado}-achievements`, this.conquistas.toString());
                localStorage.setItem(`${usuarioLogado}-streak`, this.sequencia.toString());
            }

            atualizarDisplay() {
                document.getElementById('total-points').textContent = this.pontos;
                document.getElementById('games-played').textContent = this.jogosJogados;
                document.getElementById('achievements').textContent = this.conquistas;
                document.getElementById('streak').textContent = this.sequencia;
            }

            carregarMelhoresPontuacoes() {
                const jogos = ['math', 'portuguese', 'geography', 'history', 'science', 'memory', 'wordsearch', 'english', 'puzzle'];
                jogos.forEach(jogo => {
                    const melhor = localStorage.getItem(`${usuarioLogado}-${jogo}-best`) || '0';
                    const elemento = document.getElementById(`${jogo}-best`);
                    if (elemento) elemento.textContent = melhor;
                });
            }
        }

        // Desafio Matemático
        class DesafioMatematico {
            constructor() {
                this.pontos = 0;
                this.acertos = 0;
                this.sequencia = 0;
                this.tempo = 30;
                this.timer = null;
                this.perguntaAtual = null;
                this.respostaCorreta = null;
                this.ativo = false;
            }

            gerarPergunta() {
                let num1 = Math.floor(Math.random() * 20) + 1;
                let num2 = Math.floor(Math.random() * 20) + 1;
                const operacao = Math.random() > 0.5 ? '+' : '-';
                
                if (operacao === '-' && num1 < num2) {
                    [num1, num2] = [num2, num1];
                }
                
                this.perguntaAtual = `${num1} ${operacao} ${num2}`;
                this.respostaCorreta = operacao === '+' ? num1 + num2 : num1 - num2;
                
                document.getElementById('math-question').textContent = this.perguntaAtual + ' = ?';
            }

            iniciar() {
                this.pontos = 0;
                this.acertos = 0;
                this.sequencia = 0;
                this.tempo = 30;
                this.ativo = true;
                
                document.getElementById('math-start-btn').style.display = 'none';
                document.getElementById('math-submit-btn').style.display = 'block';
                document.getElementById('math-answer').style.display = 'block';
                document.getElementById('math-answer').focus();
                
                this.gerarPergunta();
                this.iniciarTimer();
                this.atualizarDisplay();
            }

            iniciarTimer() {
                this.timer = setInterval(() => {
                    this.tempo--;
                    document.getElementById('math-timer').textContent = this.tempo;
                    
                    if (this.tempo <= 0) {
                        this.finalizarJogo();
                    }
                }, 1000);
            }

            verificarResposta() {
                if (!this.ativo) return;
                
                const resposta = parseFloat(document.getElementById('math-answer').value);
                
                if (resposta === this.respostaCorreta) {
                    this.acertos++;
                    this.sequencia++;
                    this.pontos += 10 + (this.sequencia * 2);
                    criarNotificacao('✅ Correto!', 'success');
                } else {
                    this.sequencia = 0;
                    criarNotificacao(`❌ Errado! Era ${this.respostaCorreta}`, 'error');
                }
                
                document.getElementById('math-answer').value = '';
                this.gerarPergunta();
                this.atualizarDisplay();
            }

            finalizarJogo() {
                this.ativo = false;
                clearInterval(this.timer);
                
                document.getElementById('math-start-btn').style.display = 'block';
                document.getElementById('math-submit-btn').style.display = 'none';
                document.getElementById('math-answer').style.display = 'none';
                
                document.getElementById('math-question').innerHTML = `
                    <div style="text-align: center;">
                        <h3>🎉 Jogo Finalizado!</h3>
                        <p>Pontos: ${this.pontos}</p>
                        <p>Acertos: ${this.acertos}</p>
                    </div>
                `;
                
                // Salvar melhor pontuação
                const melhorAnterior = parseInt(localStorage.getItem(`${usuarioLogado}-math-best`) || '0');
                if (this.pontos > melhorAnterior) {
                    localStorage.setItem(`${usuarioLogado}-math-best`, this.pontos.toString());
                    document.getElementById('math-best').textContent = this.pontos;
                    criarNotificacao('🏆 Nova melhor pontuação!', 'success');
                }
                
                // Adicionar pontos ao sistema
                if (sistemaPontuacao) {
                    sistemaPontuacao.adicionarPontos(this.pontos, 'Desafio Matemático');
                }
            }

            atualizarDisplay() {
                document.getElementById('math-points').textContent = this.pontos;
                document.getElementById('math-correct').textContent = this.acertos;
                document.getElementById('math-streak').textContent = this.sequencia;
            }
        }

        // Funções dos Jogos
        function abrirJogo(tipoJogo) {
            if (!usuarioLogado) {
                criarNotificacao('❌ Faça login para jogar!', 'error');
                mostrarLogin();
                return;
            }

            // Verificar se o plano permite jogar este jogo
            const jogos = ['math', 'portuguese', 'geography', 'history', 'science', 'memory', 'wordsearch', 'english', 'puzzle'];
            const indiceJogo = jogos.indexOf(tipoJogo);
            
            if (sistemaPlanos && !sistemaPlanos.podeJogar(indiceJogo)) {
                criarNotificacao('❌ Este jogo requer um plano superior! Veja os planos disponíveis.', 'error');
                abrirPlanos();
                return;
            }

            document.getElementById(`${tipoJogo}-modal`).style.display = 'flex';
            
            if (tipoJogo === 'math') {
                jogoAtual = new DesafioMatematico();
            }
        }

        function fecharModal() {
            const modals = document.querySelectorAll('.game-modal');
            modals.forEach(modal => {
                modal.style.display = 'none';
            });
            
            // Limpar jogo atual
            if (jogoAtual && jogoAtual.timer) {
                clearInterval(jogoAtual.timer);
            }
            jogoAtual = null;
        }

        function iniciarJogoMatematico() {
            if (jogoAtual) {
                jogoAtual.iniciar();
            }
        }

        function verificarRespostaMatematica() {
            if (jogoAtual) {
                jogoAtual.verificarResposta();
            }
        }

        // Funções da Loja
        function abrirLoja() {
            if (!usuarioLogado) {
                criarNotificacao('❌ Faça login para acessar a loja!', 'error');
                mostrarLogin();
                return;
            }

            document.getElementById('shop-modal').style.display = 'flex';
            if (sistemaMonetario) {
                sistemaMonetario.atualizarLoja();
            }
        }

        function fecharLoja() {
            document.getElementById('shop-modal').style.display = 'none';
        }

        // Sistema de Notificações
        function criarNotificacao(mensagem, tipo) {
            const notification = document.createElement('div');
            notification.className = `notification ${tipo}`;
            notification.textContent = mensagem;
            
            document.body.appendChild(notification);
            
            setTimeout(() => {
                notification.remove();
            }, 4000);
        }

        // Event listeners
        document.addEventListener('keydown', function(event) {
            if (event.key === 'Enter') {
                const mathAnswer = document.getElementById('math-answer');
                if (mathAnswer && mathAnswer.style.display !== 'none' && document.activeElement === mathAnswer) {
                    verificarRespostaMatematica();
                }
            }
        });

        // Inicialização
        document.addEventListener('DOMContentLoaded', function() {
            // Verificar se há usuário logado salvo
            const usuarioSalvo = localStorage.getItem('usuarioLogado');
            if (usuarioSalvo) {
                const usuarios = JSON.parse(localStorage.getItem('usuarios') || '{}');
                if (usuarios[usuarioSalvo]) {
                    usuarioLogado = usuarioSalvo;
                    document.getElementById('user-name').textContent = usuarioSalvo;
                    document.getElementById('login-section').style.display = 'none';
                    document.getElementById('user-section').style.display = 'block';
                    
                    // Mostrar badges
                    mostrarBadgesUsuario(usuarios[usuarioSalvo]);
                    
                    // Mostrar botão admin se necessário
                    if (usuarios[usuarioSalvo].isAdmin) {
                        document.getElementById('admin-panel-btn').style.display = 'block';
                    }
                    
                    // Inicializar sistemas
                    sistemaPontuacao = new SistemaPontuacao();
                    sistemaMonetario = new SistemaMonetario();
                    sistemaPlanos = new SistemaPlanos();
                    
                    // Mostrar elementos
                    document.getElementById('currency-display').style.display = 'block';
                    document.getElementById('shop-btn').style.display = 'block';
                    document.getElementById('plans-btn').style.display = 'block';
                }
            }
        });
    </script>
<script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'98e917f5d31d190e',t:'MTc2MDQ2NjA1Ni4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
