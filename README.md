# LoveCarts
Suas cartas , seus momentos 
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Carta de Amor - Crie Momentos Inesquecíveis</title>
    <link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@400;700&family=Playfair+Display:ital,wght@0,400;0,600;1,400&family=Lato:wght@300;400;700&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Lato', sans-serif;
            background: linear-gradient(135deg, #1a1a2e 0%, #16213e 50%, #0f3460 100%);
            min-height: 100vh;
            overflow-x: hidden;
            color: #fff;
        }

        /* Partículas de coração flutuantes */
        .hearts-container {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 0;
            overflow: hidden;
        }

        .floating-heart {
            position: absolute;
            font-size: 20px;
            animation: float 15s infinite linear;
            opacity: 0.6;
        }

        @keyframes float {
            0% {
                transform: translateY(100vh) rotate(0deg);
                opacity: 0;
            }
            10% {
                opacity: 0.6;
            }
            90% {
                opacity: 0.6;
            }
            100% {
                transform: translateY(-100vh) rotate(360deg);
                opacity: 0;
            }
        }

        /* Container principal */
        .main-container {
            position: relative;
            z-index: 1;
            max-width: 1200px;
            margin: 0 auto;
            padding: 40px 20px;
        }

        /* Header */
        header {
            text-align: center;
            margin-bottom: 50px;
            animation: fadeInDown 1s ease;
        }

        h1 {
            font-family: 'Dancing Script', cursive;
            font-size: 4rem;
            background: linear-gradient(45deg, #ff6b6b, #feca57, #ff9ff3, #54a0ff);
            background-size: 300% 300%;
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            animation: gradient 5s ease infinite;
            margin-bottom: 10px;
            text-shadow: 0 0 30px rgba(255, 107, 107, 0.3);
        }

        @keyframes gradient {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        .subtitle {
            font-family: 'Playfair Display', serif;
            font-size: 1.2rem;
            color: #dfe6e9;
            font-style: italic;
            opacity: 0.9;
        }

        /* Área de criação */
        .creation-area {
            display: grid;
            grid-template-columns: 1fr 2fr;
            gap: 30px;
            margin-bottom: 40px;
        }

        @media (max-width: 968px) {
            .creation-area {
                grid-template-columns: 1fr;
            }
        }

        /* Painel de controles */
        .controls-panel {
            background: rgba(255, 255, 255, 0.05);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 30px;
            border: 1px solid rgba(255, 255, 255, 0.1);
            height: fit-content;
            animation: fadeInLeft 1s ease 0.3s both;
        }

        .control-section {
            margin-bottom: 25px;
        }

        .control-section h3 {
            font-family: 'Playfair Display', serif;
            color: #ff6b6b;
            margin-bottom: 15px;
            font-size: 1.3rem;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .control-section h3::before {
            content: '♥';
            color: #ff6b6b;
            font-size: 1.2rem;
        }

        /* Inputs estilizados */
        .input-group {
            margin-bottom: 15px;
        }

        label {
            display: block;
            margin-bottom: 8px;
            color: #b2bec3;
            font-size: 0.9rem;
            font-weight: 300;
        }

        input[type="text"],
        textarea {
            width: 100%;
            padding: 12px 15px;
            border: 2px solid rgba(255, 255, 255, 0.1);
            border-radius: 12px;
            background: rgba(0, 0, 0, 0.2);
            color: #fff;
            font-family: 'Lato', sans-serif;
            font-size: 1rem;
            transition: all 0.3s ease;
        }

        input[type="text"]:focus,
        textarea:focus {
            outline: none;
            border-color: #ff6b6b;
            background: rgba(0, 0, 0, 0.3);
            box-shadow: 0 0 20px rgba(255, 107, 107, 0.2);
        }

        textarea {
            min-height: 120px;
            resize: vertical;
            font-family: 'Playfair Display', serif;
            line-height: 1.6;
        }

        /* Upload de fotos */
        .photo-upload-area {
            border: 3px dashed rgba(255, 107, 107, 0.3);
            border-radius: 15px;
            padding: 30px;
            text-align: center;
            cursor: pointer;
            transition: all 0.3s ease;
            background: rgba(255, 107, 107, 0.05);
        }

        .photo-upload-area:hover {
            border-color: #ff6b6b;
            background: rgba(255, 107, 107, 0.1);
            transform: translateY(-2px);
        }

        .photo-upload-area.dragover {
            border-color: #ff6b6b;
            background: rgba(255, 107, 107, 0.2);
            transform: scale(1.02);
        }

        .upload-icon {
            font-size: 3rem;
            margin-bottom: 10px;
            opacity: 0.7;
        }

        .upload-text {
            color: #b2bec3;
            font-size: 0.9rem;
        }

        input[type="file"] {
            display: none;
        }

        .photos-preview {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 10px;
            margin-top: 15px;
        }

        .photo-item {
            position: relative;
            border-radius: 10px;
            overflow: hidden;
            aspect-ratio: 1;
            cursor: move;
            transition: transform 0.3s ease;
        }

        .photo-item:hover {
            transform: scale(1.05);
            z-index: 10;
        }

        .photo-item img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .remove-photo {
            position: absolute;
            top: 5px;
            right: 5px;
            background: rgba(255, 0, 0, 0.8);
            color: white;
            border: none;
            width: 25px;
            height: 25px;
            border-radius: 50%;
            cursor: pointer;
            font-size: 1rem;
            display: flex;
            align-items: center;
            justify-content: center;
            opacity: 0;
            transition: opacity 0.3s;
        }

        .photo-item:hover .remove-photo {
            opacity: 1;
        }

        /* Seletor de música */
        .music-selector {
            display: flex;
            flex-direction: column;
            gap: 10px;
        }

        .music-option {
            display: flex;
            align-items: center;
            gap: 12px;
            padding: 12px;
            background: rgba(255, 255, 255, 0.05);
            border-radius: 10px;
            cursor: pointer;
            transition: all 0.3s ease;
            border: 2px solid transparent;
        }

        .music-option:hover {
            background: rgba(255, 255, 255, 0.1);
            transform: translateX(5px);
        }

        .music-option.active {
            border-color: #ff6b6b;
            background: rgba(255, 107, 107, 0.1);
        }

        .music-option input[type="radio"] {
            display: none;
        }

        .play-btn {
            width: 35px;
            height: 35px;
            border-radius: 50%;
            background: linear-gradient(135deg, #ff6b6b, #ff8e8e);
            border: none;
            color: white;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 0.9rem;
            transition: transform 0.2s;
        }

        .play-btn:hover {
            transform: scale(1.1);
        }

        .music-info {
            flex: 1;
        }

        .music-title {
            font-weight: 600;
            color: #fff;
            font-size: 0.95rem;
        }

        .music-artist {
            font-size: 0.8rem;
            color: #b2bec3;
        }

        /* Botões de tema */
        .theme-buttons {
            display: flex;
            gap: 10px;
            flex-wrap: wrap;
        }

        .theme-btn {
            padding: 8px 16px;
            border: 2px solid rgba(255, 255, 255, 0.2);
            background: transparent;
            color: #fff;
            border-radius: 20px;
            cursor: pointer;
            transition: all 0.3s;
            font-size: 0.9rem;
        }

        .theme-btn:hover, .theme-btn.active {
            background: #ff6b6b;
            border-color: #ff6b6b;
            transform: translateY(-2px);
        }

        /* Preview da carta */
        .letter-preview-container {
            animation: fadeInRight 1s ease 0.3s both;
        }

        .letter-preview {
            background: linear-gradient(135deg, #fff5f5 0%, #ffe0e0 100%);
            border-radius: 20px;
            padding: 50px;
            min-height: 600px;
            box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3);
            position: relative;
            overflow: hidden;
            transition: all 0.5s ease;
        }

        .letter-preview::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background-image: 
                radial-gradient(circle at 20% 50%, rgba(255, 107, 107, 0.1) 0%, transparent 50%),
                radial-gradient(circle at 80% 80%, rgba(255, 159, 243, 0.1) 0%, transparent 50%);
            pointer-events: none;
        }

        .letter-preview.romantic {
            background: linear-gradient(135deg, #fff5f5 0%, #ffe0e0 100%);
        }

        .letter-preview.vintage {
            background: linear-gradient(135deg, #f4e4c1 0%, #e8d5b5 100%);
            font-family: 'Courier New', monospace;
        }

        .letter-preview.modern {
            background: linear-gradient(135deg, #2c3e50 0%, #34495e 100%);
            color: #ecf0f1;
        }

        .letter-preview.ocean {
            background: linear-gradient(135deg, #e0f7fa 0%, #b2ebf2 100%);
            color: #006064;
        }

        .letter-header {
            text-align: center;
            margin-bottom: 30px;
            position: relative;
            z-index: 1;
        }

        .letter-date {
            font-family: 'Playfair Display', serif;
            color: #888;
            font-size: 0.9rem;
            margin-bottom: 10px;
        }

        .letter-recipient {
            font-family: 'Dancing Script', cursive;
            font-size: 2.5rem;
            color: #e74c3c;
            margin-bottom: 20px;
        }

        .letter-photos {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
            gap: 15px;
            margin: 30px 0;
            position: relative;
            z-index: 1;
        }

        .letter-photo {
            border-radius: 15px;
            overflow: hidden;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
            transition: transform 0.3s;
            animation:
            
