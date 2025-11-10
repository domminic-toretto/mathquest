<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MathQuest - Protótipo</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Comic Sans MS', cursive, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            padding: 20px;
        }
        
        .container {
            max-width: 1000px;
            width: 100%;
        }
        
        h1 {
            color: white;
            text-align: center;
            margin-bottom: 30px;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
            font-size: 2.5em;
        }
        
        .tabs {
            display: flex;
            gap: 10px;
            margin-bottom: 20px;
            flex-wrap: wrap;
        }
        
        .tab {
            background: rgba(255,255,255,0.2);
            color: white;
            border: none;
            padding: 12px 24px;
            cursor: pointer;
            border-radius: 10px;
            font-size: 16px;
            transition: all 0.3s;
            font-weight: bold;
        }
        
        .tab:hover {
            background: rgba(255,255,255,0.3);
            transform: translateY(-2px);
        }
        
        .tab.active {
            background: white;
            color: #667eea;
        }
        
        .screen {
            display: none;
            background: white;
            border-radius: 20px;
            padding: 30px;
            box-shadow: 0 10px 40px rgba(0,0,0,0.3);
            min-height: 500px;
        }
        
        .screen.active {
            display: block;
            animation: fadeIn 0.3s;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .game-canvas {
            background: linear-gradient(180deg, #87CEEB 0%, #90EE90 100%);
            border: 4px solid #333;
            border-radius: 10px;
            padding: 20px;
            position: relative;
            height: 400px;
            margin-bottom: 20px;
            overflow: hidden;
        }
        
        .platform {
            background: #8B4513;
            border: 3px solid #654321;
            position: absolute;
            border-radius: 5px;
        }
        
        .character {
            width: 40px;
            height: 60px;
            background: #2E7DD2;
            border: 3px solid #1a4d8f;
            border-radius: 5px;
            position: absolute;
            transition: all 0.3s;
        }
        
        .character::before {
            content: '◕◡◕';
            position: absolute;
            top: 5px;
            left: 50%;
            transform: translateX(-50%);
            font-size: 20px;
        }
        
        .character::after {
            content: '∞';
            position: absolute;
            bottom: 5px;
            left: 50%;
            transform: translateX(-50%);
            color: #FFD700;
            font-weight: bold;
        }
        
        .obstacle {
            background: #FF6B6B;
            border: 3px solid #C92A2A;
            position: absolute;
            border-radius: 5px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 24px;
            color: white;
            font-weight: bold;
        }
        
        .collectible {
            position: absolute;
            font-size: 30px;
            animation: float 2s ease-in-out infinite;
        }
        
        @keyframes float {
            0%, 100% { transform: translateY(0px); }
            50% { transform: translateY(-10px); }
        }
        
        .challenge-panel {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 20px;
            border-radius: 15px;
            margin-top: 20px;
        }
        
        .challenge-panel h3 {
            margin-bottom: 15px;
            font-size: 1.5em;
        }
        
        .options {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 10px;
            margin-top: 15px;
        }
        
        .option {
            background: white;
            color: #667eea;
            border: none;
            padding: 15px;
            border-radius: 10px;
            font-size: 18px;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.2s;
        }
        
        .option:hover {
            transform: scale(1.05);
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
        }
        
        .option.correct {
            background: #51CF66;
            color: white;
        }
        
        .option.wrong {
            background: #FF6B6B;
            color: white;
        }
        
        .wireframe {
            border: 2px dashed #333;
            padding: 20px;
            margin: 20px 0;
            background: #f9f9f9;
            border-radius: 10px;
        }
        
        .wireframe h3 {
            color: #667eea;
            margin-bottom: 15px;
        }
        
        .ui-element {
            background: white;
            border: 2px solid #333;
            padding: 10px;
            margin: 10px 0;
            border-radius: 5px;
            display: flex;
            align-items: center;
            justify-content: space-between;
        }
        
        .storyboard {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin-top: 20px;
        }
        
        .storyboard-panel {
            border: 3px solid #333;
            border-radius: 10px;
            padding: 15px;
            background: #f0f0f0;
        }
        
        .storyboard-panel img {
            width: 100%;
            height: 150px;
            background: #ddd;
            border-radius: 5px;
            margin-bottom: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 40px;
        }
        
        .storyboard-panel p {
            font-size: 14px;
            line-height: 1.6;
        }
        
        .control-info {
            background: #f8f9fa;
            padding: 20px;
            border-radius: 10px;
            margin-top: 20px;
        }
        
        .control-info h3 {
            color: #667eea;
            margin-bottom: 15px;
        }
        
        .controls {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 15px;
        }
        
        .control-item {
            background: white;
            padding: 15px;
            border-radius: 8px;
            border-left: 4px solid #667eea;
        }
        
        .feedback {
            text-align: center;
            padding: 20px;
            margin-top: 20px;
            border-radius: 10px;
            display: none;
            font-size: 1.2em;
            font-weight: bold;
        }
        
        .feedback.show {
            display: block;
            animation: slideDown 0.3s;
        }
        
        @keyframes slideDown {
            from { transform: translateY(-20px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }
        
        .feedback.success {
            background: #51CF66;
            color: white;
        }
        
        .feedback.error {
            background: #FF6B6B;
            color: white;
        }
        
        .stats {
            display: flex;
            justify-content: space-around;
            margin-top: 20px;
            flex-wrap: wrap;
            gap: 10px;
        }
        
        .stat-box {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 15px 25px;
            border-radius: 10px;
            text-align: center;
            min-width: 120px;
        }
        
        .stat-box strong {
            display: block;
            font-size: 24px;
            margin-top: 5px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>🎮 MathQuest - Protótipo Interativo</h1>
        
        <div class="tabs">
            <button class="tab active" onclick="showScreen(0)">Tela Principal</button>
            <button class="tab" onclick="showScreen(1)">Gameplay</button>
            <button class="tab" onclick="showScreen(2)">Desafio Matemático</button>
            <button class="tab" onclick="showScreen(3)">Wireframes</button>
            <button class="tab" onclick="showScreen(4)">Storyboard</button>
        </div>
        
        <!-- Tela 1: Menu Principal -->
        <div class="screen active" id="screen0">
            <h2 style="color: #667eea; text-align: center; margin-bottom: 30px;">Menu Principal</h2>
            
            <div class="wireframe">
                <h3>Layout do Menu</h3>
                <div style="text-align: center; padding: 40px;">
                    <div style="font-size: 48px; margin-bottom: 20px;">🎮</div>
                    <h2 style="color: #667eea;">MathQuest</h2>
                    <p style="color: #666; margin: 10px 0;">Aventura Matemática 2D</p>
                    
                    <div style="margin-top: 40px;">
                        <button class="option" style="display: block; margin: 10px auto; max-width: 300px;">
                            ▶️ Jogar
                        </button>
                        <button class="option" style="display: block; margin: 10px auto; max-width: 300px;">
                            📊 Progresso
                        </button>
                        <button class="option" style="display: block; margin: 10px auto; max-width: 300px;">
                            ⚙️ Configurações
                        </button>
                        <button class="option" style="display: block; margin: 10px auto; max-width: 300px;">
                            ❓ Como Jogar
                        </button>
                    </div>
                </div>
            </div>
            
            <div class="stats">
                <div class="stat-box">
                    <div>Nível Atual</div>
                    <strong>3</strong>
                </div>
                <div class="stat-box">
                    <div>Estrelas ★</div>
                    <strong>15/45</strong>
                </div>
                <div class="stat-box">
                    <div>Moedas 🪙</div>
                    <strong>237</strong>
                </div>
            </div>
        </div>
        
        <!-- Tela 2: Gameplay -->
        <div class="screen" id="screen1">
            <h2 style="color: #667eea; margin-bottom: 20px;">Gameplay - Mundo 1: Floresta dos Números</h2>
            
            <div class="game-canvas" id="gameCanvas">
                <!-- Plataformas -->
                <div class="platform" style="bottom: 0; left: 0; width: 200px; height: 30px;"></div>
                <div class="platform" style="bottom: 100px; left: 250px; width: 150px; height: 30px;"></div>
                <div class="platform" style="bottom: 200px; left: 450px; width: 180px; height: 30px;"></div>
                <div class="platform" style="bottom: 150px; right: 100px; width: 120px; height: 30px;"></div>
                
                <!-- Personagem -->
                <div class="character" id="character" style="bottom: 30px; left: 50px;"></div>
                
                <!-- Obstáculo -->
                <div class="obstacle" style="bottom: 130px; left: 250px; width: 80px; height: 80px;">
                    ?
                </div>
                
                <!-- Colecionáveis -->
                <div class="collectible" style="bottom: 230px; left: 500px;">★</div>
                <div class="collectible" style="bottom: 180px; right: 150px;">🪙</div>
                <div class="collectible" style="bottom: 50px; left: 300px;">📖</div>
            </div>
            
            <div class="control-info">
                <h3>Controles do Jogo</h3>
                <div class="controls">
                    <div class="control-item">
                        <strong>← →</strong> ou <strong>A D</strong>
                        <p>Mover para esquerda/direita</p>
                    </div>
                    <div class="control-item">
                        <strong>↑</strong> ou <strong>W</strong> ou <strong>Espaço</strong>
                        <p>Pular</p>
                    </div>
                    <div class="control-item">
                        <strong>↓</strong> ou <strong>S</strong>
                        <p>Agachar / Descer plataforma</p>
                    </div>
                    <div class="control-item">
                        <strong>E</strong> ou <strong>Enter</strong>
                        <p>Interagir com obstáculos</p>
                    </div>
                </div>
            </div>
            
            <div style="background: #f8f9fa; padding: 20px; border-radius: 10px; margin-top: 20px;">
                <h3 style="color: #667eea; margin-bottom: 15px;">Objetivo do Nível</h3>
                <p>🎯 Colete as 3 estrelas ★</p>
                <p>🚪 Chegue até a porta de saída</p>
                <p>❓ Resolva os desafios matemáticos nos obstáculos</p>
                <p>🪙 (Opcional) Colete moedas para desbloquear customizações</p>
            </div>
        </div>
        
        <!-- Tela 3: Desafio Matemático -->
        <div class="screen" id="screen2">
            <h2 style="color: #667eea; margin-bottom: 20px;">Desafio Matemático Interativo</h2>
            
            <div class="game-canvas" style="height: 200px; display: flex; align-items: center; justify-content: center;">
                <div style="text-align: center;">
                    <div class="character" style="position: static; margin: 0 auto 20px;"></div>
                    <p style="font-size: 18px; color: #333; font-weight: bold;">Alex encontrou um obstáculo!</p>
                </div>
            </div>
            
            <div class="challenge-panel">
                <h3>🧮 Desafio: Adição Básica</h3>
                <p style="font-size: 20px; margin: 15px 0;">Se você tem 12 maçãs e ganha mais 8 maçãs, quantas maçãs você tem ao todo?</p>
                
                <div class="options">
                    <button class="option" onclick="checkAnswer(this, false)">18</button>
                    <button class="option" onclick="checkAnswer(this, true)">20</button>
                    <button class="option" onclick="checkAnswer(this, false)">21</button>
                    <button class="option" onclick="checkAnswer(this, false)">24</button>
                </div>
                
                <div style="margin-top: 20px; text-align: center;">
                    <button class="option" style="background: rgba(255,255,255,0.2); color: white;" onclick="useHint()">
                        💡 Usar Dica (3 disponíveis)
                    </button>
                </div>
            </div>
            
            <div class="feedback" id="feedback"></div>
            
            <div style="background: #f8f9fa; padding: 20px; border-radius: 10px; margin-top: 20px;">
                <h3 style="color: #667eea; margin-bottom: 15px;">Tipos de Desafios</h3>
                <ul style="line-height: 2;">
                    <li><strong>Escolha Múltipla:</strong> Selecione a resposta correta entre as opções</li>
                    <li><strong>Arrasta e Solta:</strong> Organize números/operações na ordem correta</li>
                    <li><strong>Sequência:</strong> Complete padrões numéricos</li>
                    <li><strong>Digitação:</strong> Digite a resposta (níveis avançados)</li>
                </ul>
            </div>
        </div>
        
        <!-- Tela 4: Wireframes -->
        <div class="screen" id="screen3">
            <h2 style="color: #667eea; margin-bottom: 20px;">Wireframes das Interfaces</h2>
            
            <div class="wireframe">
                <h3>1. HUD (Interface Durante o Jogo)</h3>
                <div class="ui-element">
                    <div>❤️ ❤️ ❤️</div>
                    <div style="font-weight: bold;">Vidas/Tentativas</div>
                </div>
                <div class="ui-element">
                    <div>⭐ 2/3</div>
                    <div style="font-weight: bold;">Estrelas Coletadas</div>
                </div>
                <div class="ui-element">
                    <div>🪙 45</div>
                    <div style="font-weight: bold;">Moedas do Nível</div>
                </div>
                <div class="ui-element">
                    <div>⏱️ 05:23</div>
                    <div style="font-weight: bold;">Tempo Decorrido</div>
                </div>
                <div class="ui-element">
                    <div>⚙️ ⏸️</div>
                    <div style="font-weight: bold;">Configurações / Pausar</div>
                </div>
            </div>
            
            <div class="wireframe">
                <h3>2. Tela de Vitória do Nível</h3>
                <div style="text-align: center; padding: 30px; background: white; border-radius: 10px;">
                    <div style="font-size: 60px; margin-bottom: 20px;">🎉</div>
                    <h2 style="color: #51CF66;">Nível Completo!</h2>
                    
                    <div style="margin: 30px 0;">
                        <div style="background: #f8f9fa; padding: 15px; border-radius: 8px; margin: 10px 0;">
                            <strong>Estrelas:</strong> ⭐⭐⭐ (3/3)
                        </div>
                        <div style="background: #f8f9fa; padding: 15px; border-radius: 8px; margin: 10px 0;">
                            <strong>Moedas Coletadas:</strong> 🪙 45
                        </div>
                        <div style="background: #f8f9fa; padding: 15px; border-radius: 8px; margin: 10px 0;">
                            <strong>Tempo:</strong> ⏱️ 03:45
                        </div>
                        <div style="background: #f8f9fa; padding: 15px; border-radius: 8px; margin: 10px 0;">
                            <strong>Acertos:</strong> ✅ 5/5 (100%)
                        </div>
                    </div>
                    
                    <div class="options" style="max-width: 400px; margin: 0 auto;">
                        <button class="option">🔄 Rejogar</button>
                        <button class="option">➡️ Próximo Nível</button>
                    </div>
                </div>
            </div>
            
            <div class="wireframe">
                <h3>3. Seleção de Mundo</h3>
                <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(150px, 1fr)); gap: 15px;">
                    <div style="background: linear-gradient(135deg, #90EE90, #228B22); padding: 20px; border-radius: 10px; text-align: center; color: white;">
                        <div style="font-size: 40px;">🌳</div>
                        <strong>Mundo 1</strong>
                        <p style="font-size: 12px;">Floresta dos Números</p>
                        <p style="margin-top: 10px;">⭐ 12/15</p>
                    </div>
                    <div style="background: linear-gradient(135deg, #8B4513, #654321); padding: 20px; border-radius: 10px; text-align: center; color: white;">
                        <div style="font-size: 40px;">⛏️</div>
                        <strong>Mundo 2</strong>
                        <p style="font-size: 12px;">Cavernas da Multiplicação</p>
                        <p style="margin-top: 10px;">⭐ 8/15</p>
                    </div>
                    <div style="background: linear-gradient(135deg, #D4AF37, #B8860B); padding: 20px; border-radius: 10px; text-align: center; color: white; opacity: 0.5;">
                        <div style="font-size: 40px;">🏛️</div>
                        <strong>Mundo 3</strong>
                        <p style="font-size: 12px;">Templo das Frações</p>
                        <p style="margin-top: 10px;">🔒 Bloqueado</p>
                    </div>
                </div>
            </div>
            
            <div class="wireframe">
                <h3>4. Loja de Customização</h3>
                <p style="margin-bottom: 15px;"><strong>Saldo:</strong> 🪙 237 moedas</p>
                <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(120px, 1fr)); gap: 10px;">
                    <div style="background: white; border: 2px solid #ddd; padding: 15px; border-radius: 8px; text-align: center;">
                        <div style="font-size: 30px;">🎩</div>
                        <p style="font-size: 12px; margin: 5px 0;">Chapéu Mágico</p>
                        <strong style="color: #667eea;">50 🪙</strong>
                    </div>
                    <div style="background: white; border: 2px solid #ddd; padding: 15px; border-radius: 8px; text-align: center;">
                        <div style="font-size: 30px;">⚡</div>
                        <p style="font-size: 12px; margin: 5px 0;">Efeito de Velocidade</p>
                        <strong style="color: #667eea;">30 🪙</strong>
                    </div>
                    <div style="background: white; border: 2px solid #ddd; padding: 15px; border-radius: 8px; text-align: center;">
                        <div style="font-size: 30px;">🌈</div>
                        <p style="font-size: 12px; margin: 5px 0;">Trilha Colorida</p>
                        <strong style="color: #667eea;">40 🪙</strong>
                    </div>
                </div>
            </div>
        </div>
        
        <!-- Tela 5: Storyboard -->
        <div class="screen" id="screen4">
            <h2 style="color: #667eea; margin-bottom: 20px;">Storyboard do Gameplay</h2>
            
            <div class="storyboard">
                <div class="storyboard-panel">
                    <div style="width: 100%; height: 150px; background: linear-gradient(180deg, #87CEEB, #90EE90); border-radius: 5px; display: flex; align-items: center; justify-content: center; font-size: 40px; margin-bottom: 10px;">
                        🏁
                    </div>
                    <strong>Cena 1: Início do Nível</strong>
                    <p>Alex aparece no ponto de partida. Tutorial rápido mostra os controles. Música ambiente começa.</p>
                </div>
                
                <div class="storyboard-panel">
                    <div style="width: 100%; height: 150px; background: linear-gradient(180deg, #87CEEB, #90EE90); border-radius: 5px; display: flex; align-items: center; justify-content: center; font-size: 40px; margin-bottom: 10px;">
                        🏃➡️
                    </div>
                    <strong>Cena 2: Exploração</strong>
                    <p>Jogador move Alex pelas plataformas, coleta moedas 🪙 e descobre o ambiente. Música continua.</p>
                </div>
                
                <div class="storyboard-panel">
                    <div style="width: 100%; height: 150px; background: linear-gradient(180deg, #87CEEB, #90EE90); border-radius: 5px; display: flex; align-items: center; justify-content: center; font-size: 40px; margin-bottom: 10px;">
                        ❓
                    </div>
                    <strong>Cena 3: Primeiro Obstáculo</strong>
                    <p>Alex encontra um obstáculo com símbolo "?". A música diminui. Interface de desafio aparece com transição suave.</p>
                </div>
                
                <div class="storyboard-panel">
                    <div style="width: 100%; height: 150px; background: linear-gradient(135deg, #667eea, #764ba2); border-radius: 5px; display: flex; align-items: center; justify-content: center; font-size: 40px; color: white; margin-bottom: 10px;">
                        🧮
                    </div>
                    <strong>Cena 4: Desafio Matemático</strong>
                    <p>Tela do desafio aparece com a pergunta e opções. Jogador lê, pensa e seleciona uma resposta.</p>
                </div>
                
                <div class="storyboard-panel">
                    <div style="width: 100%; height: 150px; background: #51CF66; border-radius: 5px; display: flex; align-items: center; justify-content: center; font-size: 40px; color: white; margin-bottom: 10px;">
                        ✅
                    </div>
                    <strong>Cena 5: Resposta Correta</strong>
                    <p>Tela verde pisca, som de vitória toca, partículas douradas aparecem. Obstáculo desaparece. +10 pontos.</p>
                </div>
                
                <div class="storyboard-panel">
                    <div style="width: 100%; height: 150px; background: linear-gradient(180deg, #87CEEB, #90EE90); border-radius: 5px; display: flex; align-items: center; justify-content: center; font-size: 40px; margin-bottom: 10px;">
                        ⭐
                    </div>
                    <strong>Cena 6: Coleta de Estrela</strong>
                    <p>Alex pula e coleta uma estrela. Animação especial, som brilhante, contador de estrelas atualiza (1/3).</p>
                </div>
                
                <div class="storyboard-panel">
                    <div style="width: 100%; height: 150px; background: #FF6B6B; border-radius: 5px; display: flex; align-items: center; justify-content: center; font-size: 40px; color: white; margin-bottom: 10px;">
                        ⚠️
                    </div>
                    <strong>Cena 7: Armadilha</strong>
                    <p>Alex pisa em espinho/armadilha. Pequeno piscar vermelho, som de "ops!", volta ao último checkpoint. Sem penalidade grave.</p>
                </div>
                
                <div class="storyboard-panel">
                    <div style="width: 100%; height: 150px; background: linear-gradient(180deg, #87CEEB, #90EE90); border-radius: 5px; display: flex; align-items: center; justify-content: center; font-size: 40px; margin-bottom: 10px;">
                        🚪
                    </div>
                    <strong>Cena 8: Porta de Saída</strong>
                    <p>Alex chega à porta final. Porta se abre com animação. Alex entra. Transição para tela de vitória.</p>
                </div>
                
                <div class="storyboard-panel">
                    <div style="width: 100%; height: 150px; background: linear-gradient(135deg, #FFD700, #FFA500); border-radius: 5px; display: flex; align-items: center; justify-content: center; font-size: 40px; color: white; margin-bottom: 10px;">
                        🎉
                    </div>
                    <strong>Cena 9: Tela de Vitória</strong>
                    <p>Estatísticas aparecem: estrelas coletadas, tempo, acertos. Música triunfante. Botões: Rejogar ou Próximo Nível.</p>
                </div>
            </div>
            
            <div style="background: #f8f9fa; padding: 20px; border-radius: 10px; margin-top: 30px;">
                <h3 style="color: #667eea; margin-bottom: 15px;">Flow do Jogador</h3>
                <div style="text-align: center; line-height: 2.5;">
                    🏁 Início → 🏃 Exploração → ❓ Obstáculo → 🧮 Desafio → 
                    <br>
                    ✅ Acerto / ❌ Erro → 🏃 Continua → ⭐ Coleta → 
                    <br>
                    🚪 Saída → 🎉 Vitória → ➡️ Próximo Nível
                </div>
            </div>
            
            <div style="background: #f8f9fa; padding: 20px; border-radius: 10px; margin-top: 20px;">
                <h3 style="color: #667eea; margin-bottom: 15px;">Elementos de Game Feel</h3>
                <ul style="line-height: 2;">
                    <li><strong>Juice Visual:</strong> Partículas ao coletar itens, screen shake sutil em acertos</li>
                    <li><strong>Feedback Sonoro:</strong> Sons distintos para cada ação (pulo, coleta, acerto, erro)</li>
                    <li><strong>Animações:</strong> Squash & stretch no personagem, bounce nas plataformas</li>
                    <li><strong>Transições:</strong> Fade suave entre telas, slide-in para desafios</li>
                    <li><strong>Resposta Imediata:</strong> Feedback instantâneo (< 0.1s) para todas as ações</li>
                </ul>
            </div>
        </div>
    </div>
    
    <script>
        let hintsAvailable = 3;
        
        function showScreen(index) {
            const screens = document.querySelectorAll('.screen');
            const tabs = document.querySelectorAll('.tab');
            
            screens.forEach((screen, i) => {
                screen.classList.remove('active');
                tabs[i].classList.remove('active');
            });
            
            screens[index].classList.add('active');
            tabs[index].classList.add('active');
        }
        
        function checkAnswer(button, isCorrect) {
            const feedback = document.getElementById('feedback');
            const options = document.querySelectorAll('.option');
            
            // Desabilita todos os botões
            options.forEach(opt => opt.style.pointerEvents = 'none');
            
            if (isCorrect) {
                button.classList.add('correct');
                feedback.className = 'feedback success show';
                feedback.innerHTML = '🎉 Correto! Muito bem!<br><small>12 + 8 = 20</small>';
                
                setTimeout(() => {
                    alert('Obstáculo superado! Alex pode continuar a jornada.');
                    location.reload();
                }, 2000);
            } else {
                button.classList.add('wrong');
                feedback.className = 'feedback error show';
                feedback.innerHTML = '❌ Ops! Tente novamente.<br><small>Dica: Some os dois números</small>';
                
                setTimeout(() => {
                    button.classList.remove('wrong');
                    feedback.classList.remove('show');
                    options.forEach(opt => opt.style.pointerEvents = 'auto');
                }, 2000);
            }
        }
        
        function useHint() {
            if (hintsAvailable > 0) {
                hintsAvailable--;
                const hints = [
                    '💡 Dica 1: Esta é uma soma simples. Some 12 + 8.',
                    '💡 Dica 2: 12 + 8 = 10 + 2 + 8 = 10 + 10 = ?',
                    '💡 Dica 3: A resposta é 20!'
                ];
                alert(hints[3 - hintsAvailable - 1] + '\n\nDicas restantes: ' + hintsAvailable);
            } else {
                alert('❌ Você não tem mais dicas disponíveis neste nível!');
            }
        }
    </script>
</body>
</html>
