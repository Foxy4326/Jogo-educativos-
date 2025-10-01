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

        .demo-accounts {
            margin-top: 20px;
            padding: 20px;
            background: #f7fafc;
            border-radius: 15px;
        }

        .demo-title {
            font-weight: bold;
            margin-bottom: 15px;
            color: #4a5568;
            text-align: center;
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

        /* Estilos específicos dos novos jogos */
        .memory-card {
            width: 80px;
            height: 80px;
            background: linear-gradient(135deg, #4facfe, #00f2fe);
            border-radius: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 2rem;
            cursor: pointer;
            transition: all 0.3s ease;
            color: white;
            font-weight: bold;
        }

        .memory-card.flipped {
            background: linear-gradient(135deg, #48bb78, #38a169);
            transform: rotateY(180deg);
        }

        .memory-card.matched {
            background: linear-gradient(135deg, #ffd700, #ffed4e);
            color: #333;
        }

        .memory-card:hover {
            transform: scale(1.05);
        }

        .wordsearch-cell {
            width: 25px;
            height: 25px;
            border: 1px solid #e2e8f0;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.2s ease;
            background: white;
        }

        .wordsearch-cell:hover {
            background: #f7fafc;
        }

        .wordsearch-cell.selected {
            background: linear-gradient(135deg, #4facfe, #00f2fe);
            color: white;
        }

        .wordsearch-cell.found {
            background: linear-gradient(135deg, #48bb78, #38a169);
            color: white;
        }

        .word-item {
            padding: 5px 10px;
            margin: 2px 0;
            border-radius: 8px;
            background: white;
            border: 1px solid #e2e8f0;
            font-size: 0.9rem;
        }

        .word-item.found {
            background: linear-gradient(135deg, #48bb78, #38a169);
            color: white;
            text-decoration: line-through;
        }

        .puzzle-piece {
            width: 90px;
            height: 90px;
            background: linear-gradient(135deg, #4facfe, #00f2fe);
            border-radius: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 2rem;
            font-weight: bold;
            color: white;
            cursor: pointer;
            transition: all 0.3s ease;
            border: 2px solid #e2e8f0;
        }

        .puzzle-piece:hover {
            transform: scale(1.05);
            box-shadow: 0 5px 15px rgba(79, 172, 254, 0.3);
        }

        .puzzle-piece.empty {
            background: #f7fafc;
            border: 2px dashed #cbd5e0;
            color: transparent;
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

            .memory-card {
                width: 60px;
                height: 60px;
                font-size: 1.5rem;
            }

            .wordsearch-cell {
                width: 20px;
                height: 20px;
                font-size: 0.8rem;
            }

            .puzzle-piece {
                width: 70px;
                height: 70px;
                font-size: 1.5rem;
            }
        }
    </style>
</head>
<body>
    <!-- Sistema de Moedas -->
    <div id="currency-display" class="currency-display">
        💰 <span id="user-coins">0</span> Moedas
    </div>

    <!-- Botão da Loja -->
    <button id="shop-btn" class="shop-btn" onclick="abrirLoja()">
        🛒 Loja
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
            <p class="subtitle">Plataforma educativa interativa completa!</p>
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

    <!-- Modal do Quiz de Português -->
    <div id="portuguese-modal" class="game-modal">
        <div class="modal-content">
            <button class="close-button" onclick="fecharModal()">&times;</button>
            <h2 style="text-align: center; margin-bottom: 30px; color: #4a5568;">📚 Quiz de Português</h2>
            
            <div class="game-interface">
                <div class="game-stats">
                    <div class="stat-item">
                        <div>Pontos: <span id="portuguese-points">0</span></div>
                    </div>
                    <div class="stat-item">
                        <div>Pergunta: <span id="portuguese-current">0</span>/5</div>
                    </div>
                    <div class="stat-item">
                        <div>Acertos: <span id="portuguese-correct">0</span></div>
                    </div>
                    <div class="stat-item">
                        <div>Precisão: <span id="portuguese-accuracy">0</span>%</div>
                    </div>
                </div>

                <div class="question-area" id="portuguese-question">
                    Clique em "Iniciar Quiz" para começar!
                </div>

                <div class="options-grid" id="portuguese-options" style="display: none;">
                </div>

                <button onclick="iniciarQuizPortugues()" id="portuguese-start-btn" class="control-btn" style="width: 100%;">
                    🚀 Iniciar Quiz
                </button>
            </div>
        </div>
    </div>

    <!-- Modal do Quiz de Geografia -->
    <div id="geography-modal" class="game-modal">
        <div class="modal-content">
            <button class="close-button" onclick="fecharModal()">&times;</button>
            <h2 style="text-align: center; margin-bottom: 30px; color: #4a5568;">🌍 Quiz de Geografia</h2>
            
            <div class="game-interface">
                <div class="game-stats">
                    <div class="stat-item">
                        <div>Pontos: <span id="geography-points">0</span></div>
                    </div>
                    <div class="stat-item">
                        <div>Pergunta: <span id="geography-current">0</span>/5</div>
                    </div>
                    <div class="stat-item">
                        <div>Acertos: <span id="geography-correct">0</span></div>
                    </div>
                    <div class="stat-item">
                        <div>Precisão: <span id="geography-accuracy">0</span>%</div>
                    </div>
                </div>

                <div class="question-area" id="geography-question">
                    Clique em "Iniciar Quiz" para começar!
                </div>

                <div class="options-grid" id="geography-options" style="display: none;">
                </div>

                <button onclick="iniciarQuizGeografia()" id="geography-start-btn" class="control-btn" style="width: 100%;">
                    🚀 Iniciar Quiz
                </button>
            </div>
        </div>
    </div>

    <!-- Modal do Quiz de História -->
    <div id="history-modal" class="game-modal">
        <div class="modal-content">
            <button class="close-button" onclick="fecharModal()">&times;</button>
            <h2 style="text-align: center; margin-bottom: 30px; color: #4a5568;">🏛️ Quiz de História</h2>
            
            <div class="game-interface">
                <div class="game-stats">
                    <div class="stat-item">
                        <div>Pontos: <span id="history-points">0</span></div>
                    </div>
                    <div class="stat-item">
                        <div>Pergunta: <span id="history-current">0</span>/5</div>
                    </div>
                    <div class="stat-item">
                        <div>Acertos: <span id="history-correct">0</span></div>
                    </div>
                    <div class="stat-item">
                        <div>Precisão: <span id="history-accuracy">0</span>%</div>
                    </div>
                </div>

                <div class="question-area" id="history-question">
                    Clique em "Iniciar Quiz" para começar!
                </div>

                <div class="options-grid" id="history-options" style="display: none;">
                </div>

                <button onclick="iniciarQuizHistoria()" id="history-start-btn" class="control-btn" style="width: 100%;">
                    🚀 Iniciar Quiz
                </button>
            </div>
        </div>
    </div>

    <!-- Modal do Quiz de Ciências -->
    <div id="science-modal" class="game-modal">
        <div class="modal-content">
            <button class="close-button" onclick="fecharModal()">&times;</button>
            <h2 style="text-align: center; margin-bottom: 30px; color: #4a5568;">🔬 Quiz de Ciências</h2>
            
            <div class="game-interface">
                <div class="game-stats">
                    <div class="stat-item">
                        <div>Pontos: <span id="science-points">0</span></div>
                    </div>
                    <div class="stat-item">
                        <div>Pergunta: <span id="science-current">0</span>/5</div>
                    </div>
                    <div class="stat-item">
                        <div>Acertos: <span id="science-correct">0</span></div>
                    </div>
                    <div class="stat-item">
                        <div>Precisão: <span id="science-accuracy">0</span>%</div>
                    </div>
                </div>

                <div class="question-area" id="science-question">
                    Clique em "Iniciar Quiz" para começar!
                </div>

                <div class="options-grid" id="science-options" style="display: none;">
                </div>

                <button onclick="iniciarQuizCiencias()" id="science-start-btn" class="control-btn" style="width: 100%;">
                    🚀 Iniciar Quiz
                </button>
            </div>
        </div>
    </div>

    <!-- Modal do Jogo da Memória -->
    <div id="memory-modal" class="game-modal">
        <div class="modal-content">
            <button class="close-button" onclick="fecharModal()">&times;</button>
            <h2 style="text-align: center; margin-bottom: 30px; color: #4a5568;">🧠 Jogo da Memória</h2>
            
            <div class="game-interface">
                <div class="game-stats">
                    <div class="stat-item">
                        <div>Pontos: <span id="memory-points">0</span></div>
                    </div>
                    <div class="stat-item">
                        <div>Pares: <span id="memory-pairs">0</span>/8</div>
                    </div>
                    <div class="stat-item">
                        <div>Tentativas: <span id="memory-attempts">0</span></div>
                    </div>
                    <div class="stat-item">
                        <div>Tempo: <span id="memory-timer">0</span>s</div>
                    </div>
                </div>

                <div id="memory-board" style="display: grid; grid-template-columns: repeat(4, 1fr); gap: 10px; margin: 20px 0; max-width: 400px; margin: 20px auto;">
                    <!-- Cartas serão geradas aqui -->
                </div>

                <button onclick="iniciarJogoMemoria()" id="memory-start-btn" class="control-btn" style="width: 100%;">
                    🚀 Iniciar Jogo
                </button>
            </div>
        </div>
    </div>

    <!-- Modal do Caça Palavras -->
    <div id="wordsearch-modal" class="game-modal">
        <div class="modal-content">
            <button class="close-button" onclick="fecharModal()">&times;</button>
            <h2 style="text-align: center; margin-bottom: 30px; color: #4a5568;">🔍 Caça Palavras</h2>
            
            <div class="game-interface">
                <div class="game-stats">
                    <div class="stat-item">
                        <div>Pontos: <span id="wordsearch-points">0</span></div>
                    </div>
                    <div class="stat-item">
                        <div>Palavras: <span id="wordsearch-found">0</span>/5</div>
                    </div>
                    <div class="stat-item">
                        <div>Tempo: <span id="wordsearch-timer">120</span>s</div>
                    </div>
                    <div class="stat-item">
                        <div>Dicas: <span id="wordsearch-hints">3</span></div>
                    </div>
                </div>

                <div style="display: flex; gap: 20px; align-items: flex-start;">
                    <div id="wordsearch-grid" style="display: grid; grid-template-columns: repeat(10, 1fr); gap: 2px; font-family: monospace; font-size: 14px;">
                        <!-- Grid será gerado aqui -->
                    </div>
                    
                    <div style="background: #f7fafc; padding: 15px; border-radius: 10px; min-width: 150px;">
                        <h4 style="margin-bottom: 10px; color: #4a5568;">Palavras:</h4>
                        <div id="wordsearch-words">
                            <!-- Lista de palavras -->
                        </div>
                        <button onclick="usarDica()" id="wordsearch-hint-btn" class="control-btn secondary" style="width: 100%; margin-top: 10px; font-size: 0.9rem;">
                            💡 Usar Dica
                        </button>
                    </div>
                </div>

                <button onclick="iniciarCacaPalavras()" id="wordsearch-start-btn" class="control-btn" style="width: 100%; margin-top: 20px;">
                    🚀 Iniciar Jogo
                </button>
            </div>
        </div>
    </div>

    <!-- Modal do Quiz de Inglês -->
    <div id="english-modal" class="game-modal">
        <div class="modal-content">
            <button class="close-button" onclick="fecharModal()">&times;</button>
            <h2 style="text-align: center; margin-bottom: 30px; color: #4a5568;">🇺🇸 Quiz de Inglês</h2>
            
            <div class="game-interface">
                <div class="game-stats">
                    <div class="stat-item">
                        <div>Pontos: <span id="english-points">0</span></div>
                    </div>
                    <div class="stat-item">
                        <div>Pergunta: <span id="english-current">0</span>/5</div>
                    </div>
                    <div class="stat-item">
                        <div>Acertos: <span id="english-correct">0</span></div>
                    </div>
                    <div class="stat-item">
                        <div>Precisão: <span id="english-accuracy">0</span>%</div>
                    </div>
                </div>

                <div class="question-area" id="english-question">
                    Clique em "Iniciar Quiz" para começar!
                </div>

                <div class="options-grid" id="english-options" style="display: none;">
                </div>

                <button onclick="iniciarQuizIngles()" id="english-start-btn" class="control-btn" style="width: 100%;">
                    🚀 Iniciar Quiz
                </button>
            </div>
        </div>
    </div>

    <!-- Modal do Quebra-Cabeça Numérico -->
    <div id="puzzle-modal" class="game-modal">
        <div class="modal-content">
            <button class="close-button" onclick="fecharModal()">&times;</button>
            <h2 style="text-align: center; margin-bottom: 30px; color: #4a5568;">🧩 Quebra-Cabeça Numérico</h2>
            
            <div class="game-interface">
                <div class="game-stats">
                    <div class="stat-item">
                        <div>Pontos: <span id="puzzle-points">0</span></div>
                    </div>
                    <div class="stat-item">
                        <div>Movimentos: <span id="puzzle-moves">0</span></div>
                    </div>
                    <div class="stat-item">
                        <div>Tempo: <span id="puzzle-timer">0</span>s</div>
                    </div>
                    <div class="stat-item">
                        <div>Melhor: <span id="puzzle-best-moves">∞</span></div>
                    </div>
                </div>

                <div id="puzzle-board" style="display: grid; grid-template-columns: repeat(3, 1fr); gap: 5px; max-width: 300px; margin: 20px auto;">
                    <!-- Peças do quebra-cabeça -->
                </div>

                <div style="display: flex; gap: 10px; justify-content: center;">
                    <button onclick="iniciarQuebraCabeca()" id="puzzle-start-btn" class="control-btn">
                        🚀 Novo Jogo
                    </button>
                    <button onclick="embaralharPuzzle()" id="puzzle-shuffle-btn" class="control-btn secondary" style="display: none;">
                        🔀 Embaralhar
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
                    permissoes: ['all']
                };
            } else {
                // Garantir que vitor202 sempre tenha privilégios de dono
                usuariosExistentes['vitor202'].isAdmin = true;
                usuariosExistentes['vitor202'].isOwner = true;
                usuariosExistentes['vitor202'].verificado = true;
                usuariosExistentes['vitor202'].nivel = 'DONO';
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
                    permissoes: ['admin', 'educacao']
                };
            } else {
                // Garantir que bruna sempre tenha privilégios de professora
                usuariosExistentes['bruna'].isAdmin = true;
                usuariosExistentes['bruna'].isProfessora = true;
                usuariosExistentes['bruna'].verificado = true;
                usuariosExistentes['bruna'].nivel = 'PROFESSORA';
                usuariosExistentes['bruna'].permissoes = ['admin', 'educacao'];
            }
            
            localStorage.setItem('usuarios', JSON.stringify(usuariosExistentes));
        }

        // Executar na inicialização
        inicializarContasEspeciais();

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
                dataCriacao: new Date().toISOString()
            };
            localStorage.setItem('usuarios', JSON.stringify(usuariosExistentes));

            criarNotificacao('🎉 Conta criada com sucesso!', 'success');
            
            // Fazer login automático
            usuarioLogado = usuario;
            document.getElementById('user-name').textContent = usuario;
            document.getElementById('login-section').style.display = 'none';
            document.getElementById('user-section').style.display = 'block';
            fecharLogin();
            
            // Inicializar sistema de pontuação
            sistemaPontuacao = new SistemaPontuacao();
            
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
                
                // Mostrar elementos do sistema monetário
                document.getElementById('currency-display').style.display = 'block';
                document.getElementById('shop-btn').style.display = 'block';
                
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
            document.getElementById('login-section').style.display = 'block';
            document.getElementById('user-section').style.display = 'none';
            document.getElementById('admin-panel-btn').style.display = 'none';
            document.getElementById('user-badges').innerHTML = '';
            document.getElementById('currency-display').style.display = 'none';
            document.getElementById('shop-btn').style.display = 'none';
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
                
                let badges = '';
                if (user.isOwner) badges += '<span style="background: #ffd700; color: #000; padding: 2px 6px; border-radius: 8px; font-size: 0.7rem; margin-right: 3px;">👑 DONO</span>';
                if (user.isProfessora) badges += '<span style="background: #ff6b6b; color: white; padding: 2px 6px; border-radius: 8px; font-size: 0.7rem; margin-right: 3px;">👩‍🏫 PROFESSORA</span>';
                if (user.isAdmin) badges += '<span style="background: #9f7aea; color: white; padding: 2px 6px; border-radius: 8px; font-size: 0.7rem; margin-right: 3px;">⚡ ADMIN</span>';
                if (user.verificado) badges += '<span style="background: #48bb78; color: white; padding: 2px 6px; border-radius: 8px; font-size: 0.7rem;">✅ VERIFICADO</span>';
                
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
                localStorage.removeItem(`${username}-math-best`);
                localStorage.removeItem(`${username}-portuguese-best`);
                localStorage.removeItem(`${username}-geography-best`);
                localStorage.removeItem(`${username}-history-best`);
            });
            
            criarNotificacao('🗑️ Dados de pontuação limpos com sucesso!', 'success');
            carregarDadosAdmin();
            
            // Atualizar sistema de pontuação se o usuário atual estiver logado
            if (sistemaPontuacao) {
                sistemaPontuacao = new SistemaPontuacao();
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
                    mathBest: localStorage.getItem(`${username}-math-best`) || '0',
                    portugueseBest: localStorage.getItem(`${username}-portuguese-best`) || '0',
                    geographyBest: localStorage.getItem(`${username}-geography-best`) || '0',
                    historyBest: localStorage.getItem(`${username}-history-best`) || '0'
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
            relatorio += '=' .repeat(50) + '\n\n';
            relatorio += `Data: ${new Date().toLocaleString('pt-BR')}\n`;
            relatorio += `Total de usuários: ${Object.keys(usuarios).length}\n\n`;
            
            relatorio += 'USUÁRIOS REGISTRADOS:\n';
            relatorio += '-'.repeat(30) + '\n';
            
            Object.keys(usuarios).forEach(username => {
                const user = usuarios[username];
                const pontos = localStorage.getItem(`${username}-totalPoints`) || '0';
                const jogos = localStorage.getItem(`${username}-gamesPlayed`) || '0';
                
                relatorio += `👤 ${username}\n`;
                relatorio += `   📧 Email: ${user.email}\n`;
                relatorio += `   🎮 Jogos: ${jogos} | ⭐ Pontos: ${pontos}\n`;
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
                this.moedas += quantidade;
                this.salvar();
                this.atualizarDisplay();
                
                if (motivo) {
                    this.mostrarRecompensa(`+${quantidade} moedas por ${motivo}!`);
                }
            }

            gastarMoedas(quantidade) {
                if (this.moedas >= quantidade) {
                    this.moedas -= quantidade;
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

                if (this.gastarMoedas(item.preco)) {
                    this.itensComprados.push(itemId);
                    localStorage.setItem(`${usuarioLogado}-items`, JSON.stringify(this.itensComprados));
                    criarNotificacao(`🎉 ${item.nome} comprado com sucesso!`, 'success');
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
                let html = '';

                itens.forEach(item => {
                    const jaComprado = this.itensComprados.includes(item.id);
                    const podeComprar = this.moedas >= item.preco && !jaComprado;

                    html += `
                        <div class="shop-item ${jaComprado ? 'owned' : ''}">
                            <div class="shop-item-icon">${item.icone}</div>
                            <div class="shop-item-name">${item.nome}</div>
                            <div class="shop-item-description">${item.descricao}</div>
                            ${!jaComprado ? 
                                `<div class="shop-item-price">💰 ${item.preco} moedas</div>
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
                
                if (this.pontos >= 100 && this.conquistas < 1) this.conquistas = 1;
                if (this.pontos >= 500 && this.conquistas < 2) this.conquistas = 2;
                if (this.sequencia >= 10 && this.conquistas < 3) this.conquistas = 3;

                this.salvar();
                this.atualizarDisplay();
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
                const num1 = Math.floor(Math.random() * 20) + 1;
                const num2 = Math.floor(Math.random() * 20) + 1;
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
                
                if (sistemaPontuacao) {
                    sistemaPontuacao.adicionarPontos(this.pontos, 'Matemática');
                }
                
                const melhorAnterior = parseInt(localStorage.getItem(`${usuarioLogado}-math-best`) || '0');
                if (this.pontos > melhorAnterior) {
                    localStorage.setItem(`${usuarioLogado}-math-best`, this.pontos.toString());
                    document.getElementById('math-best').textContent = this.pontos;
                }
            }

            atualizarDisplay() {
                document.getElementById('math-points').textContent = this.pontos;
                document.getElementById('math-correct').textContent = this.acertos;
                document.getElementById('math-streak').textContent = this.sequencia;
            }
        }

        // Quiz de Português
        class QuizPortugues {
            constructor() {
                this.pontos = 0;
                this.acertos = 0;
                this.perguntaAtual = 0;
                this.totalPerguntas = 5;
                this.perguntas = [
                    {
                        pergunta: "Qual é o plural de 'animal'?",
                        opcoes: ["animais", "animals", "animales", "animaes"],
                        correta: 0
                    },
                    {
                        pergunta: "Complete: 'Eu _____ na escola ontem.'",
                        opcoes: ["foi", "fui", "fomos", "foram"],
                        correta: 1
                    },
                    {
                        pergunta: "Qual palavra está escrita corretamente?",
                        opcoes: ["excessão", "exceção", "exeção", "excesão"],
                        correta: 1
                    },
                    {
                        pergunta: "O que é um substantivo?",
                        opcoes: ["Palavra que indica ação", "Palavra que nomeia seres", "Palavra que qualifica", "Palavra que liga"],
                        correta: 1
                    },
                    {
                        pergunta: "Qual é o feminino de 'galo'?",
                        opcoes: ["gala", "galinha", "galia", "galona"],
                        correta: 1
                    }
                ];
                this.ativo = false;
            }

            iniciar() {
                this.pontos = 0;
                this.acertos = 0;
                this.perguntaAtual = 0;
                this.ativo = true;
                
                this.perguntas = this.perguntas.sort(() => Math.random() - 0.5);
                
                document.getElementById('portuguese-start-btn').style.display = 'none';
                document.getElementById('portuguese-options').style.display = 'grid';
                
                this.mostrarPergunta();
                this.atualizarDisplay();
            }

            mostrarPergunta() {
                if (this.perguntaAtual >= this.perguntas.length) {
                    this.finalizarJogo();
                    return;
                }

                const pergunta = this.perguntas[this.perguntaAtual];
                document.getElementById('portuguese-question').textContent = pergunta.pergunta;
                
                const optionsContainer = document.getElementById('portuguese-options');
                optionsContainer.innerHTML = '';
                
                pergunta.opcoes.forEach((opcao, index) => {
                    const button = document.createElement('button');
                    button.className = 'option-btn';
                    button.textContent = opcao;
                    button.onclick = () => this.verificarResposta(index);
                    optionsContainer.appendChild(button);
                });
            }

            verificarResposta(opcaoSelecionada) {
                if (!this.ativo) return;
                
                const pergunta = this.perguntas[this.perguntaAtual];
                const buttons = document.querySelectorAll('#portuguese-options .option-btn');
                
                buttons.forEach((btn, index) => {
                    if (index === pergunta.correta) {
                        btn.classList.add('correct');
                    } else if (index === opcaoSelecionada && index !== pergunta.correta) {
                        btn.classList.add('incorrect');
                    }
                    btn.disabled = true;
                });
                
                if (opcaoSelecionada === pergunta.correta) {
                    this.acertos++;
                    this.pontos += 20;
                    criarNotificacao('✅ Correto!', 'success');
                } else {
                    criarNotificacao('❌ Incorreto!', 'error');
                }
                
                setTimeout(() => {
                    this.perguntaAtual++;
                    this.mostrarPergunta();
                    this.atualizarDisplay();
                }, 2000);
            }

            finalizarJogo() {
                this.ativo = false;
                const precisao = Math.round((this.acertos / this.perguntas.length) * 100);
                
                document.getElementById('portuguese-start-btn').style.display = 'block';
                document.getElementById('portuguese-options').style.display = 'none';
                
                document.getElementById('portuguese-question').innerHTML = `
                    <div style="text-align: center;">
                        <h3>🎉 Quiz Finalizado!</h3>
                        <p>Pontos: ${this.pontos}</p>
                        <p>Acertos: ${this.acertos}/${this.perguntas.length}</p>
                        <p>Precisão: ${precisao}%</p>
                    </div>
                `;
                
                if (sistemaPontuacao) {
                    sistemaPontuacao.adicionarPontos(this.pontos, 'Português');
                }
                
                const melhorAnterior = parseInt(localStorage.getItem(`${usuarioLogado}-portuguese-best`) || '0');
                if (this.pontos > melhorAnterior) {
                    localStorage.setItem(`${usuarioLogado}-portuguese-best`, this.pontos.toString());
                    document.getElementById('portuguese-best').textContent = this.pontos;
                }
            }

            atualizarDisplay() {
                document.getElementById('portuguese-points').textContent = this.pontos;
                document.getElementById('portuguese-current').textContent = this.perguntaAtual + 1;
                document.getElementById('portuguese-correct').textContent = this.acertos;
                const precisao = this.perguntaAtual > 0 ? Math.round((this.acertos / this.perguntaAtual) * 100) : 0;
                document.getElementById('portuguese-accuracy').textContent = precisao;
            }
        }

        // Quiz de Geografia
        class QuizGeografia {
            constructor() {
                this.pontos = 0;
                this.acertos = 0;
                this.perguntaAtual = 0;
                this.totalPerguntas = 5;
                this.perguntas = [
                    {
                        pergunta: "Qual é a capital do Brasil?",
                        opcoes: ["São Paulo", "Rio de Janeiro", "Brasília", "Salvador"],
                        correta: 2
                    },
                    {
                        pergunta: "Qual é o maior país do mundo?",
                        opcoes: ["China", "Estados Unidos", "Canadá", "Rússia"],
                        correta: 3
                    },
                    {
                        pergunta: "Em que continente fica o Egito?",
                        opcoes: ["Ásia", "África", "Europa", "América"],
                        correta: 1
                    },
                    {
                        pergunta: "Qual é o rio mais longo do mundo?",
                        opcoes: ["Amazonas", "Nilo", "Mississippi", "Yangtzé"],
                        correta: 1
                    },
                    {
                        pergunta: "Quantos continentes existem?",
                        opcoes: ["5", "6", "7", "8"],
                        correta: 2
                    }
                ];
                this.ativo = false;
            }

            iniciar() {
                this.pontos = 0;
                this.acertos = 0;
                this.perguntaAtual = 0;
                this.ativo = true;
                
                this.perguntas = this.perguntas.sort(() => Math.random() - 0.5);
                
                document.getElementById('geography-start-btn').style.display = 'none';
                document.getElementById('geography-options').style.display = 'grid';
                
                this.mostrarPergunta();
                this.atualizarDisplay();
            }

            mostrarPergunta() {
                if (this.perguntaAtual >= this.perguntas.length) {
                    this.finalizarJogo();
                    return;
                }

                const pergunta = this.perguntas[this.perguntaAtual];
                document.getElementById('geography-question').textContent = pergunta.pergunta;
                
                const optionsContainer = document.getElementById('geography-options');
                optionsContainer.innerHTML = '';
                
                pergunta.opcoes.forEach((opcao, index) => {
                    const button = document.createElement('button');
                    button.className = 'option-btn';
                    button.textContent = opcao;
                    button.onclick = () => this.verificarResposta(index);
                    optionsContainer.appendChild(button);
                });
            }

            verificarResposta(opcaoSelecionada) {
                if (!this.ativo) return;
                
                const pergunta = this.perguntas[this.perguntaAtual];
                const buttons = document.querySelectorAll('#geography-options .option-btn');
                
                buttons.forEach((btn, index) => {
                    if (index === pergunta.correta) {
                        btn.classList.add('correct');
                    } else if (index === opcaoSelecionada && index !== pergunta.correta) {
                        btn.classList.add('incorrect');
                    }
                    btn.disabled = true;
                });
                
                if (opcaoSelecionada === pergunta.correta) {
                    this.acertos++;
                    this.pontos += 20;
                    criarNotificacao('✅ Correto!', 'success');
                } else {
                    criarNotificacao('❌ Incorreto!', 'error');
                }
                
                setTimeout(() => {
                    this.perguntaAtual++;
                    this.mostrarPergunta();
                    this.atualizarDisplay();
                }, 2000);
            }

            finalizarJogo() {
                this.ativo = false;
                const precisao = Math.round((this.acertos / this.perguntas.length) * 100);
                
                document.getElementById('geography-start-btn').style.display = 'block';
                document.getElementById('geography-options').style.display = 'none';
                
                document.getElementById('geography-question').innerHTML = `
                    <div style="text-align: center;">
                        <h3>🎉 Quiz Finalizado!</h3>
                        <p>Pontos: ${this.pontos}</p>
                        <p>Acertos: ${this.acertos}/${this.perguntas.length}</p>
                        <p>Precisão: ${precisao}%</p>
                    </div>
                `;
                
                if (sistemaPontuacao) {
                    sistemaPontuacao.adicionarPontos(this.pontos, 'Geografia');
                }
                
                const melhorAnterior = parseInt(localStorage.getItem(`${usuarioLogado}-geography-best`) || '0');
                if (this.pontos > melhorAnterior) {
                    localStorage.setItem(`${usuarioLogado}-geography-best`, this.pontos.toString());
                    document.getElementById('geography-best').textContent = this.pontos;
                }
            }

            atualizarDisplay() {
                document.getElementById('geography-points').textContent = this.pontos;
                document.getElementById('geography-current').textContent = this.perguntaAtual + 1;
                document.getElementById('geography-correct').textContent = this.acertos;
                const precisao = this.perguntaAtual > 0 ? Math.round((this.acertos / this.perguntaAtual) * 100) : 0;
                document.getElementById('geography-accuracy').textContent = precisao;
            }
        }

        // Quiz de História
        class QuizHistoria {
            constructor() {
                this.pontos = 0;
                this.acertos = 0;
                this.perguntaAtual = 0;
                this.totalPerguntas = 5;
                this.perguntas = [
                    {
                        pergunta: "Em que ano o Brasil foi descoberto?",
                        opcoes: ["1498", "1500", "1502", "1504"],
                        correta: 1
                    },
                    {
                        pergunta: "Quem foi o primeiro presidente do Brasil?",
                        opcoes: ["Getúlio Vargas", "Deodoro da Fonseca", "Juscelino Kubitschek", "Tancredo Neves"],
                        correta: 1
                    },
                    {
                        pergunta: "Quando acabou a Segunda Guerra Mundial?",
                        opcoes: ["1944", "1945", "1946", "1947"],
                        correta: 1
                    },
                    {
                        pergunta: "Qual foi a primeira capital do Brasil?",
                        opcoes: ["Rio de Janeiro", "São Paulo", "Salvador", "Brasília"],
                        correta: 2
                    },
                    {
                        pergunta: "Em que século ocorreu a Revolução Francesa?",
                        opcoes: ["XVII", "XVIII", "XIX", "XX"],
                        correta: 1
                    }
                ];
                this.ativo = false;
            }

            iniciar() {
                this.pontos = 0;
                this.acertos = 0;
                this.perguntaAtual = 0;
                this.ativo = true;
                
                this.perguntas = this.perguntas.sort(() => Math.random() - 0.5);
                
                document.getElementById('history-start-btn').style.display = 'none';
                document.getElementById('history-options').style.display = 'grid';
                
                this.mostrarPergunta();
                this.atualizarDisplay();
            }

            mostrarPergunta() {
                if (this.perguntaAtual >= this.perguntas.length) {
                    this.finalizarJogo();
                    return;
                }

                const pergunta = this.perguntas[this.perguntaAtual];
                document.getElementById('history-question').textContent = pergunta.pergunta;
                
                const optionsContainer = document.getElementById('history-options');
                optionsContainer.innerHTML = '';
                
                pergunta.opcoes.forEach((opcao, index) => {
                    const button = document.createElement('button');
                    button.className = 'option-btn';
                    button.textContent = opcao;
                    button.onclick = () => this.verificarResposta(index);
                    optionsContainer.appendChild(button);
                });
            }

            verificarResposta(opcaoSelecionada) {
                if (!this.ativo) return;
                
                const pergunta = this.perguntas[this.perguntaAtual];
                const buttons = document.querySelectorAll('#history-options .option-btn');
                
                buttons.forEach((btn, index) => {
                    if (index === pergunta.correta) {
                        btn.classList.add('correct');
                    } else if (index === opcaoSelecionada && index !== pergunta.correta) {
                        btn.classList.add('incorrect');
                    }
                    btn.disabled = true;
                });
                
                if (opcaoSelecionada === pergunta.correta) {
                    this.acertos++;
                    this.pontos += 20;
                    criarNotificacao('✅ Correto!', 'success');
                } else {
                    criarNotificacao('❌ Incorreto!', 'error');
                }
                
                setTimeout(() => {
                    this.perguntaAtual++;
                    this.mostrarPergunta();
                    this.atualizarDisplay();
                }, 2000);
            }

            finalizarJogo() {
                this.ativo = false;
                const precisao = Math.round((this.acertos / this.perguntas.length) * 100);
                
                document.getElementById('history-start-btn').style.display = 'block';
                document.getElementById('history-options').style.display = 'none';
                
                document.getElementById('history-question').innerHTML = `
                    <div style="text-align: center;">
                        <h3>🎉 Quiz Finalizado!</h3>
                        <p>Pontos: ${this.pontos}</p>
                        <p>Acertos: ${this.acertos}/${this.perguntas.length}</p>
                        <p>Precisão: ${precisao}%</p>
                    </div>
                `;
                
                if (sistemaPontuacao) {
                    sistemaPontuacao.adicionarPontos(this.pontos, 'História');
                }
                
                const melhorAnterior = parseInt(localStorage.getItem(`${usuarioLogado}-history-best`) || '0');
                if (this.pontos > melhorAnterior) {
                    localStorage.setItem(`${usuarioLogado}-history-best`, this.pontos.toString());
                    document.getElementById('history-best').textContent = this.pontos;
                }
            }

            atualizarDisplay() {
                document.getElementById('history-points').textContent = this.pontos;
                document.getElementById('history-current').textContent = this.perguntaAtual + 1;
                document.getElementById('history-correct').textContent = this.acertos;
                const precisao = this.perguntaAtual > 0 ? Math.round((this.acertos / this.perguntaAtual) * 100) : 0;
                document.getElementById('history-accuracy').textContent = precisao;
            }
        }

        // Quiz de Ciências
        class QuizCiencias {
            constructor() {
                this.pontos = 0;
                this.acertos = 0;
                this.perguntaAtual = 0;
                this.perguntas = [
                    {
                        pergunta: "Qual é o planeta mais próximo do Sol?",
                        opcoes: ["Vênus", "Mercúrio", "Terra", "Marte"],
                        correta: 1
                    },
                    {
                        pergunta: "Quantos ossos tem o corpo humano adulto?",
                        opcoes: ["206", "208", "210", "204"],
                        correta: 0
                    },
                    {
                        pergunta: "Qual é a fórmula química da água?",
                        opcoes: ["CO2", "H2O", "O2", "NaCl"],
                        correta: 1
                    },
                    {
                        pergunta: "Qual animal é conhecido como o rei da selva?",
                        opcoes: ["Tigre", "Leopardo", "Leão", "Jaguar"],
                        correta: 2
                    },
                    {
                        pergunta: "Quantos corações tem uma minhoca?",
                        opcoes: ["1", "3", "5", "10"],
                        correta: 2
                    }
                ];
                this.ativo = false;
            }

            iniciar() {
                this.pontos = 0;
                this.acertos = 0;
                this.perguntaAtual = 0;
                this.ativo = true;
                
                this.perguntas = this.perguntas.sort(() => Math.random() - 0.5);
                
                document.getElementById('science-start-btn').style.display = 'none';
                document.getElementById('science-options').style.display = 'grid';
                
                this.mostrarPergunta();
                this.atualizarDisplay();
            }

            mostrarPergunta() {
                if (this.perguntaAtual >= this.perguntas.length) {
                    this.finalizarJogo();
                    return;
                }

                const pergunta = this.perguntas[this.perguntaAtual];
                document.getElementById('science-question').textContent = pergunta.pergunta;
                
                const optionsContainer = document.getElementById('science-options');
                optionsContainer.innerHTML = '';
                
                pergunta.opcoes.forEach((opcao, index) => {
                    const button = document.createElement('button');
                    button.className = 'option-btn';
                    button.textContent = opcao;
                    button.onclick = () => this.verificarResposta(index);
                    optionsContainer.appendChild(button);
                });
            }

            verificarResposta(opcaoSelecionada) {
                if (!this.ativo) return;
                
                const pergunta = this.perguntas[this.perguntaAtual];
                const buttons = document.querySelectorAll('#science-options .option-btn');
                
                buttons.forEach((btn, index) => {
                    if (index === pergunta.correta) {
                        btn.classList.add('correct');
                    } else if (index === opcaoSelecionada && index !== pergunta.correta) {
                        btn.classList.add('incorrect');
                    }
                    btn.disabled = true;
                });
                
                if (opcaoSelecionada === pergunta.correta) {
                    this.acertos++;
                    this.pontos += 25;
                    criarNotificacao('✅ Correto!', 'success');
                } else {
                    criarNotificacao('❌ Incorreto!', 'error');
                }
                
                setTimeout(() => {
                    this.perguntaAtual++;
                    this.mostrarPergunta();
                    this.atualizarDisplay();
                }, 2000);
            }

            finalizarJogo() {
                this.ativo = false;
                const precisao = Math.round((this.acertos / this.perguntas.length) * 100);
                
                document.getElementById('science-start-btn').style.display = 'block';
                document.getElementById('science-options').style.display = 'none';
                
                document.getElementById('science-question').innerHTML = `
                    <div style="text-align: center;">
                        <h3>🎉 Quiz Finalizado!</h3>
                        <p>Pontos: ${this.pontos}</p>
                        <p>Acertos: ${this.acertos}/${this.perguntas.length}</p>
                        <p>Precisão: ${precisao}%</p>
                    </div>
                `;
                
                if (sistemaPontuacao) {
                    sistemaPontuacao.adicionarPontos(this.pontos, 'Ciências');
                }
                
                const melhorAnterior = parseInt(localStorage.getItem(`${usuarioLogado}-science-best`) || '0');
                if (this.pontos > melhorAnterior) {
                    localStorage.setItem(`${usuarioLogado}-science-best`, this.pontos.toString());
                    document.getElementById('science-best').textContent = this.pontos;
                }
            }

            atualizarDisplay() {
                document.getElementById('science-points').textContent = this.pontos;
                document.getElementById('science-current').textContent = this.perguntaAtual + 1;
                document.getElementById('science-correct').textContent = this.acertos;
                const precisao = this.perguntaAtual > 0 ? Math.round((this.acertos / this.perguntaAtual) * 100) : 0;
                document.getElementById('science-accuracy').textContent = precisao;
            }
        }

        // Jogo da Memória
        class JogoMemoria {
            constructor() {
                this.pontos = 0;
                this.pares = 0;
                this.tentativas = 0;
                this.tempo = 0;
                this.timer = null;
                this.cartasViradas = [];
                this.cartas = ['🎮', '🎯', '🎲', '🎪', '🎨', '🎭', '🎪', '🎵'];
                this.tabuleiro = [];
                this.ativo = false;
            }

            iniciar() {
                this.pontos = 0;
                this.pares = 0;
                this.tentativas = 0;
                this.tempo = 0;
                this.cartasViradas = [];
                this.ativo = true;
                
                // Duplicar cartas e embaralhar
                this.tabuleiro = [...this.cartas, ...this.cartas].sort(() => Math.random() - 0.5);
                
                this.criarTabuleiro();
                this.iniciarTimer();
                this.atualizarDisplay();
                
                document.getElementById('memory-start-btn').style.display = 'none';
            }

            criarTabuleiro() {
                const board = document.getElementById('memory-board');
                board.innerHTML = '';
                
                this.tabuleiro.forEach((carta, index) => {
                    const cardElement = document.createElement('div');
                    cardElement.className = 'memory-card';
                    cardElement.textContent = '?';
                    cardElement.dataset.index = index;
                    cardElement.dataset.symbol = carta;
                    cardElement.onclick = () => this.virarCarta(index);
                    board.appendChild(cardElement);
                });
            }

            virarCarta(index) {
                if (!this.ativo || this.cartasViradas.length >= 2) return;
                
                const carta = document.querySelector(`[data-index="${index}"]`);
                if (carta.classList.contains('flipped') || carta.classList.contains('matched')) return;
                
                carta.classList.add('flipped');
                carta.textContent = carta.dataset.symbol;
                this.cartasViradas.push(index);
                
                if (this.cartasViradas.length === 2) {
                    this.tentativas++;
                    setTimeout(() => this.verificarPar(), 1000);
                }
            }

            verificarPar() {
                const [index1, index2] = this.cartasViradas;
                const carta1 = document.querySelector(`[data-index="${index1}"]`);
                const carta2 = document.querySelector(`[data-index="${index2}"]`);
                
                if (carta1.dataset.symbol === carta2.dataset.symbol) {
                    carta1.classList.add('matched');
                    carta2.classList.add('matched');
                    this.pares++;
                    this.pontos += 50;
                    criarNotificacao('✅ Par encontrado!', 'success');
                    
                    if (this.pares === 8) {
                        this.finalizarJogo();
                    }
                } else {
                    carta1.classList.remove('flipped');
                    carta2.classList.remove('flipped');
                    carta1.textContent = '?';
                    carta2.textContent = '?';
                }
                
                this.cartasViradas = [];
                this.atualizarDisplay();
            }

            iniciarTimer() {
                this.timer = setInterval(() => {
                    this.tempo++;
                    document.getElementById('memory-timer').textContent = this.tempo;
                }, 1000);
            }

            finalizarJogo() {
                this.ativo = false;
                clearInterval(this.timer);
                
                const bonus = Math.max(0, 300 - this.tempo);
                this.pontos += bonus;
                
                document.getElementById('memory-start-btn').style.display = 'block';
                
                criarNotificacao(`🎉 Parabéns! +${bonus} pontos de bônus!`, 'success');
                
                if (sistemaPontuacao) {
                    sistemaPontuacao.adicionarPontos(this.pontos, 'Memória');
                }
                
                const melhorAnterior = parseInt(localStorage.getItem(`${usuarioLogado}-memory-best`) || '0');
                if (this.pontos > melhorAnterior) {
                    localStorage.setItem(`${usuarioLogado}-memory-best`, this.pontos.toString());
                    document.getElementById('memory-best').textContent = this.pontos;
                }
            }

            atualizarDisplay() {
                document.getElementById('memory-points').textContent = this.pontos;
                document.getElementById('memory-pairs').textContent = this.pares;
                document.getElementById('memory-attempts').textContent = this.tentativas;
            }
        }

        // Quiz de Inglês
        class QuizIngles {
            constructor() {
                this.pontos = 0;
                this.acertos = 0;
                this.perguntaAtual = 0;
                this.perguntas = [
                    {
                        pergunta: "What color is the sky?",
                        opcoes: ["Red", "Blue", "Green", "Yellow"],
                        correta: 1
                    },
                    {
                        pergunta: "How do you say 'Obrigado' in English?",
                        opcoes: ["Please", "Sorry", "Thank you", "Excuse me"],
                        correta: 2
                    },
                    {
                        pergunta: "What is the opposite of 'big'?",
                        opcoes: ["Small", "Large", "Huge", "Giant"],
                        correta: 0
                    },
                    {
                        pergunta: "Complete: 'I ___ a student.'",
                        opcoes: ["is", "am", "are", "be"],
                        correta: 1
                    },
                    {
                        pergunta: "What does 'cat' mean in Portuguese?",
                        opcoes: ["Cão", "Gato", "Pássaro", "Peixe"],
                        correta: 1
                    }
                ];
                this.ativo = false;
            }

            iniciar() {
                this.pontos = 0;
                this.acertos = 0;
                this.perguntaAtual = 0;
                this.ativo = true;
                
                this.perguntas = this.perguntas.sort(() => Math.random() - 0.5);
                
                document.getElementById('english-start-btn').style.display = 'none';
                document.getElementById('english-options').style.display = 'grid';
                
                this.mostrarPergunta();
                this.atualizarDisplay();
            }

            mostrarPergunta() {
                if (this.perguntaAtual >= this.perguntas.length) {
                    this.finalizarJogo();
                    return;
                }

                const pergunta = this.perguntas[this.perguntaAtual];
                document.getElementById('english-question').textContent = pergunta.pergunta;
                
                const optionsContainer = document.getElementById('english-options');
                optionsContainer.innerHTML = '';
                
                pergunta.opcoes.forEach((opcao, index) => {
                    const button = document.createElement('button');
                    button.className = 'option-btn';
                    button.textContent = opcao;
                    button.onclick = () => this.verificarResposta(index);
                    optionsContainer.appendChild(button);
                });
            }

            verificarResposta(opcaoSelecionada) {
                if (!this.ativo) return;
                
                const pergunta = this.perguntas[this.perguntaAtual];
                const buttons = document.querySelectorAll('#english-options .option-btn');
                
                buttons.forEach((btn, index) => {
                    if (index === pergunta.correta) {
                        btn.classList.add('correct');
                    } else if (index === opcaoSelecionada && index !== pergunta.correta) {
                        btn.classList.add('incorrect');
                    }
                    btn.disabled = true;
                });
                
                if (opcaoSelecionada === pergunta.correta) {
                    this.acertos++;
                    this.pontos += 30;
                    criarNotificacao('✅ Correct!', 'success');
                } else {
                    criarNotificacao('❌ Wrong!', 'error');
                }
                
                setTimeout(() => {
                    this.perguntaAtual++;
                    this.mostrarPergunta();
                    this.atualizarDisplay();
                }, 2000);
            }

            finalizarJogo() {
                this.ativo = false;
                const precisao = Math.round((this.acertos / this.perguntas.length) * 100);
                
                document.getElementById('english-start-btn').style.display = 'block';
                document.getElementById('english-options').style.display = 'none';
                
                document.getElementById('english-question').innerHTML = `
                    <div style="text-align: center;">
                        <h3>🎉 Quiz Finished!</h3>
                        <p>Points: ${this.pontos}</p>
                        <p>Correct: ${this.acertos}/${this.perguntas.length}</p>
                        <p>Accuracy: ${precisao}%</p>
                    </div>
                `;
                
                if (sistemaPontuacao) {
                    sistemaPontuacao.adicionarPontos(this.pontos, 'Inglês');
                }
                
                const melhorAnterior = parseInt(localStorage.getItem(`${usuarioLogado}-english-best`) || '0');
                if (this.pontos > melhorAnterior) {
                    localStorage.setItem(`${usuarioLogado}-english-best`, this.pontos.toString());
                    document.getElementById('english-best').textContent = this.pontos;
                }
            }

            atualizarDisplay() {
                document.getElementById('english-points').textContent = this.pontos;
                document.getElementById('english-current').textContent = this.perguntaAtual + 1;
                document.getElementById('english-correct').textContent = this.acertos;
                const precisao = this.perguntaAtual > 0 ? Math.round((this.acertos / this.perguntaAtual) * 100) : 0;
                document.getElementById('english-accuracy').textContent = precisao;
            }
        }

        // Caça Palavras
        class CacaPalavras {
            constructor() {
                this.pontos = 0;
                this.palavrasEncontradas = 0;
                this.tempo = 120;
                this.dicas = 3;
                this.timer = null;
                this.palavras = ['CASA', 'GATO', 'AMOR', 'VIDA', 'FELIZ'];
                this.grid = [];
                this.palavrasColocadas = [];
                this.ativo = false;
            }

            iniciar() {
                this.pontos = 0;
                this.palavrasEncontradas = 0;
                this.tempo = 120;
                this.dicas = 3;
                this.ativo = true;
                
                this.criarGrid();
                this.colocarPalavras();
                this.preencherGrid();
                this.mostrarGrid();
                this.mostrarPalavras();
                this.iniciarTimer();
                this.atualizarDisplay();
                
                document.getElementById('wordsearch-start-btn').style.display = 'none';
            }

            criarGrid() {
                this.grid = Array(10).fill().map(() => Array(10).fill(''));
            }

            colocarPalavras() {
                this.palavrasColocadas = [];
                
                this.palavras.forEach(palavra => {
                    let colocada = false;
                    let tentativas = 0;
                    
                    while (!colocada && tentativas < 50) {
                        const direcao = Math.floor(Math.random() * 3); // 0: horizontal, 1: vertical, 2: diagonal
                        const linha = Math.floor(Math.random() * 10);
                        const coluna = Math.floor(Math.random() * 10);
                        
                        if (this.podeColocarPalavra(palavra, linha, coluna, direcao)) {
                            this.colocarPalavra(palavra, linha, coluna, direcao);
                            colocada = true;
                        }
                        tentativas++;
                    }
                });
            }

            podeColocarPalavra(palavra, linha, coluna, direcao) {
                const deltas = [[0, 1], [1, 0], [1, 1]];
                const [deltaL, deltaC] = deltas[direcao];
                
                for (let i = 0; i < palavra.length; i++) {
                    const novaLinha = linha + i * deltaL;
                    const novaColuna = coluna + i * deltaC;
                    
                    if (novaLinha >= 10 || novaColuna >= 10) return false;
                    if (this.grid[novaLinha][novaColuna] !== '' && this.grid[novaLinha][novaColuna] !== palavra[i]) return false;
                }
                return true;
            }

            colocarPalavra(palavra, linha, coluna, direcao) {
                const deltas = [[0, 1], [1, 0], [1, 1]];
                const [deltaL, deltaC] = deltas[direcao];
                const posicoes = [];
                
                for (let i = 0; i < palavra.length; i++) {
                    const novaLinha = linha + i * deltaL;
                    const novaColuna = coluna + i * deltaC;
                    this.grid[novaLinha][novaColuna] = palavra[i];
                    posicoes.push([novaLinha, novaColuna]);
                }
                
                this.palavrasColocadas.push({
                    palavra: palavra,
                    posicoes: posicoes,
                    encontrada: false
                });
            }

            preencherGrid() {
                const letras = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ';
                for (let i = 0; i < 10; i++) {
                    for (let j = 0; j < 10; j++) {
                        if (this.grid[i][j] === '') {
                            this.grid[i][j] = letras[Math.floor(Math.random() * letras.length)];
                        }
                    }
                }
            }

            mostrarGrid() {
                const gridContainer = document.getElementById('wordsearch-grid');
                gridContainer.innerHTML = '';
                
                for (let i = 0; i < 10; i++) {
                    for (let j = 0; j < 10; j++) {
                        const cell = document.createElement('div');
                        cell.className = 'wordsearch-cell';
                        cell.textContent = this.grid[i][j];
                        cell.dataset.row = i;
                        cell.dataset.col = j;
                        cell.onclick = () => this.selecionarCelula(i, j);
                        gridContainer.appendChild(cell);
                    }
                }
            }

            mostrarPalavras() {
                const wordsContainer = document.getElementById('wordsearch-words');
                wordsContainer.innerHTML = '';
                
                this.palavras.forEach(palavra => {
                    const wordElement = document.createElement('div');
                    wordElement.className = 'word-item';
                    wordElement.textContent = palavra;
                    wordElement.id = `word-${palavra}`;
                    wordsContainer.appendChild(wordElement);
                });
            }

            selecionarCelula(linha, coluna) {
                if (!this.ativo) return;
                
                // Verificar se a célula faz parte de alguma palavra
                this.palavrasColocadas.forEach(palavraObj => {
                    if (!palavraObj.encontrada) {
                        const posicaoEncontrada = palavraObj.posicoes.find(pos => pos[0] === linha && pos[1] === coluna);
                        if (posicaoEncontrada) {
                            this.marcarPalavraEncontrada(palavraObj);
                        }
                    }
                });
            }

            marcarPalavraEncontrada(palavraObj) {
                palavraObj.encontrada = true;
                this.palavrasEncontradas++;
                this.pontos += 40;
                
                // Marcar células como encontradas
                palavraObj.posicoes.forEach(pos => {
                    const cell = document.querySelector(`[data-row="${pos[0]}"][data-col="${pos[1]}"]`);
                    cell.classList.add('found');
                });
                
                // Marcar palavra na lista
                document.getElementById(`word-${palavraObj.palavra}`).classList.add('found');
                
                criarNotificacao(`✅ Palavra "${palavraObj.palavra}" encontrada!`, 'success');
                
                if (this.palavrasEncontradas === this.palavras.length) {
                    this.finalizarJogo();
                }
                
                this.atualizarDisplay();
            }

            usarDica() {
                if (this.dicas <= 0 || !this.ativo) return;
                
                const palavraNaoEncontrada = this.palavrasColocadas.find(p => !p.encontrada);
                if (palavraNaoEncontrada) {
                    const primeiraPos = palavraNaoEncontrada.posicoes[0];
                    const cell = document.querySelector(`[data-row="${primeiraPos[0]}"][data-col="${primeiraPos[1]}"]`);
                    cell.style.background = 'linear-gradient(135deg, #ffd700, #ffed4e)';
                    cell.style.color = '#333';
                    
                    this.dicas--;
                    this.atualizarDisplay();
                    
                    setTimeout(() => {
                        cell.style.background = '';
                        cell.style.color = '';
                    }, 3000);
                }
            }

            iniciarTimer() {
                this.timer = setInterval(() => {
                    this.tempo--;
                    document.getElementById('wordsearch-timer').textContent = this.tempo;
                    
                    if (this.tempo <= 0) {
                        this.finalizarJogo();
                    }
                }, 1000);
            }

            finalizarJogo() {
                this.ativo = false;
                clearInterval(this.timer);
                
                const bonus = this.tempo * 2;
                this.pontos += bonus;
                
                document.getElementById('wordsearch-start-btn').style.display = 'block';
                
                criarNotificacao(`🎉 Jogo finalizado! +${bonus} pontos de bônus!`, 'success');
                
                if (sistemaPontuacao) {
                    sistemaPontuacao.adicionarPontos(this.pontos, 'Caça Palavras');
                }
                
                const melhorAnterior = parseInt(localStorage.getItem(`${usuarioLogado}-wordsearch-best`) || '0');
                if (this.pontos > melhorAnterior) {
                    localStorage.setItem(`${usuarioLogado}-wordsearch-best`, this.pontos.toString());
                    document.getElementById('wordsearch-best').textContent = this.pontos;
                }
            }

            atualizarDisplay() {
                document.getElementById('wordsearch-points').textContent = this.pontos;
                document.getElementById('wordsearch-found').textContent = this.palavrasEncontradas;
                document.getElementById('wordsearch-hints').textContent = this.dicas;
            }
        }

        // Quebra-Cabeça Numérico
        class QuebraCabeca {
            constructor() {
                this.pontos = 0;
                this.movimentos = 0;
                this.tempo = 0;
                this.timer = null;
                this.tabuleiro = [1, 2, 3, 4, 5, 6, 7, 8, 0]; // 0 representa espaço vazio
                this.solucao = [1, 2, 3, 4, 5, 6, 7, 8, 0];
                this.ativo = false;
            }

            iniciar() {
                this.pontos = 0;
                this.movimentos = 0;
                this.tempo = 0;
                this.ativo = true;
                
                this.embaralhar();
                this.criarTabuleiro();
                this.iniciarTimer();
                this.atualizarDisplay();
                
                document.getElementById('puzzle-start-btn').textContent = '🔄 Reiniciar';
                document.getElementById('puzzle-shuffle-btn').style.display = 'block';
            }

            embaralhar() {
                // Embaralhar de forma que sempre seja solucionável
                for (let i = 0; i < 1000; i++) {
                    const movimentosPossiveis = this.obterMovimentosPossiveis();
                    if (movimentosPossiveis.length > 0) {
                        const movimento = movimentosPossiveis[Math.floor(Math.random() * movimentosPossiveis.length)];
                        this.moverPeca(movimento, false);
                    }
                }
                this.movimentos = 0;
            }

            obterMovimentosPossiveis() {
                const posicaoVazia = this.tabuleiro.indexOf(0);
                const linha = Math.floor(posicaoVazia / 3);
                const coluna = posicaoVazia % 3;
                const movimentos = [];
                
                if (linha > 0) movimentos.push(posicaoVazia - 3); // cima
                if (linha < 2) movimentos.push(posicaoVazia + 3); // baixo
                if (coluna > 0) movimentos.push(posicaoVazia - 1); // esquerda
                if (coluna < 2) movimentos.push(posicaoVazia + 1); // direita
                
                return movimentos;
            }

            criarTabuleiro() {
                const board = document.getElementById('puzzle-board');
                board.innerHTML = '';
                
                this.tabuleiro.forEach((numero, index) => {
                    const piece = document.createElement('div');
                    piece.className = numero === 0 ? 'puzzle-piece empty' : 'puzzle-piece';
                    piece.textContent = numero === 0 ? '' : numero;
                    piece.onclick = () => this.moverPeca(index);
                    board.appendChild(piece);
                });
            }

            moverPeca(posicao, contarMovimento = true) {
                if (!this.ativo && contarMovimento) return;
                
                const posicaoVazia = this.tabuleiro.indexOf(0);
                const movimentosPossiveis = this.obterMovimentosPossiveis();
                
                if (movimentosPossiveis.includes(posicao)) {
                    // Trocar peça com espaço vazio
                    [this.tabuleiro[posicao], this.tabuleiro[posicaoVazia]] = [this.tabuleiro[posicaoVazia], this.tabuleiro[posicao]];
                    
                    if (contarMovimento) {
                        this.movimentos++;
                        this.atualizarDisplay();
                    }
                    
                    this.criarTabuleiro();
                    
                    if (this.verificarVitoria()) {
                        this.finalizarJogo();
                    }
                }
            }

            verificarVitoria() {
                return JSON.stringify(this.tabuleiro) === JSON.stringify(this.solucao);
            }

            iniciarTimer() {
                this.timer = setInterval(() => {
                    this.tempo++;
                    document.getElementById('puzzle-timer').textContent = this.tempo;
                }, 1000);
            }

            finalizarJogo() {
                this.ativo = false;
                clearInterval(this.timer);
                
                // Calcular pontos baseado em movimentos e tempo
                const pontosBase = 1000;
                const penalidade = (this.movimentos * 5) + (this.tempo * 2);
                this.pontos = Math.max(100, pontosBase - penalidade);
                
                criarNotificacao(`🎉 Parabéns! Resolvido em ${this.movimentos} movimentos!`, 'success');
                
                if (sistemaPontuacao) {
                    sistemaPontuacao.adicionarPontos(this.pontos, 'Quebra-Cabeça');
                }
                
                const melhorAnterior = parseInt(localStorage.getItem(`${usuarioLogado}-puzzle-best`) || '0');
                if (this.pontos > melhorAnterior) {
                    localStorage.setItem(`${usuarioLogado}-puzzle-best`, this.pontos.toString());
                    document.getElementById('puzzle-best').textContent = this.pontos;
                }
                
                // Atualizar melhor número de movimentos
                const melhorMovimentos = localStorage.getItem(`${usuarioLogado}-puzzle-best-moves`) || '∞';
                if (melhorMovimentos === '∞' || this.movimentos < parseInt(melhorMovimentos)) {
                    localStorage.setItem(`${usuarioLogado}-puzzle-best-moves`, this.movimentos.toString());
                    document.getElementById('puzzle-best-moves').textContent = this.movimentos;
                }
            }

            atualizarDisplay() {
                document.getElementById('puzzle-points').textContent = this.pontos;
                document.getElementById('puzzle-moves').textContent = this.movimentos;
                
                // Carregar melhor número de movimentos
                const melhorMovimentos = localStorage.getItem(`${usuarioLogado}-puzzle-best-moves`) || '∞';
                document.getElementById('puzzle-best-moves').textContent = melhorMovimentos;
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

        // Funções principais
        function abrirJogo(tipo) {
            if (!usuarioLogado) {
                criarNotificacao('❌ Faça login para jogar!', 'error');
                mostrarLogin();
                return;
            }

            document.getElementById(`${tipo}-modal`).style.display = 'flex';
            
            switch(tipo) {
                case 'math':
                    jogoAtual = new DesafioMatematico();
                    break;
                case 'portuguese':
                    jogoAtual = new QuizPortugues();
                    break;
                case 'geography':
                    jogoAtual = new QuizGeografia();
                    break;
                case 'history':
                    jogoAtual = new QuizHistoria();
                    break;
                case 'science':
                    jogoAtual = new QuizCiencias();
                    break;
                case 'memory':
                    jogoAtual = new JogoMemoria();
                    break;
                case 'english':
                    jogoAtual = new QuizIngles();
                    break;
                case 'wordsearch':
                    jogoAtual = new CacaPalavras();
                    break;
                case 'puzzle':
                    jogoAtual = new QuebraCabeca();
                    break;
            }
        }

        function fecharModal() {
            const modals = document.querySelectorAll('.game-modal');
            modals.forEach(modal => {
                if (modal.id !== 'shop-modal') {
                    modal.style.display = 'none';
                }
            });
            jogoAtual = null;
        }

        function iniciarJogoMatematico() {
            if (jogoAtual) jogoAtual.iniciar();
        }

        function verificarRespostaMatematica() {
            if (jogoAtual) jogoAtual.verificarResposta();
        }

        function iniciarQuizPortugues() {
            if (jogoAtual) jogoAtual.iniciar();
        }

        function iniciarQuizGeografia() {
            if (jogoAtual) jogoAtual.iniciar();
        }

        function iniciarQuizHistoria() {
            if (jogoAtual) jogoAtual.iniciar();
        }

        function iniciarQuizCiencias() {
            if (jogoAtual) jogoAtual.iniciar();
        }

        function iniciarJogoMemoria() {
            if (jogoAtual) jogoAtual.iniciar();
        }

        function iniciarQuizIngles() {
            if (jogoAtual) jogoAtual.iniciar();
        }

        function iniciarCacaPalavras() {
            if (jogoAtual) jogoAtual.iniciar();
        }

        function iniciarQuebraCabeca() {
            if (jogoAtual) jogoAtual.iniciar();
        }

        function embaralharPuzzle() {
            if (jogoAtual) jogoAtual.embaralhar();
        }

        function usarDica() {
            if (jogoAtual) jogoAtual.usarDica();
        }

        // Função para criar notificações
        function criarNotificacao(mensagem, tipo) {
            const notificacao = document.createElement('div');
            notificacao.className = `notification ${tipo}`;
            notificacao.textContent = mensagem;
            document.body.appendChild(notificacao);

            setTimeout(() => {
                notificacao.remove();
            }, 3000);
        }

        // Event listeners
        document.addEventListener('keypress', function(e) {
            if (e.key === 'Enter') {
                if (document.getElementById('math-modal').style.display === 'flex' && jogoAtual && jogoAtual.ativo) {
                    verificarRespostaMatematica();
                }
            }
        });

        // Fechar modais clicando fora
        document.addEventListener('click', function(e) {
            if (e.target.classList.contains('game-modal')) {
                if (e.target.id === 'shop-modal') {
                    fecharLoja();
                } else {
                    fecharModal();
                }
            }
            if (e.target.classList.contains('login-modal')) {
                fecharLogin();
            }
        });
    </script>
<script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'987d7b56f08af1dd',t:'MTc1OTMzNzY2NS4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
