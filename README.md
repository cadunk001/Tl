<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Para minha Rapunzel</title>
  <link href="https://fonts.googleapis.com/css2?family=Sacramento&family=Montserrat:wght@400;600&display=swap" rel="stylesheet">
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }
    body {
      font-family: 'Montserrat', sans-serif;
      background: #000; /* Fundo preto */
      color: #fff;
      text-align: center;
      overflow-x: hidden;
      position: relative;
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      align-items: center;
    }
    /* Efeito de sobreposição roxa/lilás */
    body::before {
      content: '';
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: linear-gradient(135deg, rgba(138, 43, 226, 0.3), rgba(186, 85, 211, 0.2));
      z-index: -1;
    }
    header {
      padding: 40px 20px;
      position: relative;
      z-index: 1;
    }
    h1 {
      font-family: 'Sacramento', cursive;
      font-size: 4.5em;
      margin: 0;
      color: #fff;
      text-shadow: 2px 2px 6px rgba(0, 0, 0, 0.5);
    }
    p {
      font-size: 1.3em;
      margin: 10px auto;
      max-width: 700px;
      line-height: 1.6;
      color: #000;
      background: rgba(255, 255, 255, 0.9);
      padding: 10px 20px;
      border-radius: 10px;
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
    }
    .upload-section {
      margin: 30px auto;
      padding: 20px;
      background: rgba(255, 255, 255, 0.95);
      border-radius: 15px;
      max-width: 600px;
      box-shadow: 0 8px 16px rgba(0, 0, 0, 0.3);
      position: relative;
      z-index: 1;
    }
    input[type="file"] {
      margin: 10px;
      padding: 10px;
      font-size: 1em;
      border: 2px solid #8a2be2;
      border-radius: 25px;
      background: #fff;
      color: #000;
      transition: border-color 0.3s;
    }
    input[type="file"]:focus {
      border-color: #ba55d3;
      outline: none;
    }
    button {
      padding: 12px 30px;
      font-size: 1.2em;
      font-family: 'Montserrat', sans-serif;
      background: linear-gradient(45deg, #8a2be2, #ba55d3);
      color: #fff;
      border: none;
      border-radius: 25px;
      cursor: pointer;
      transition: transform 0.3s, box-shadow 0.3s;
      position: relative;
      z-index: 1;
    }
    button:hover {
      transform: scale(1.05);
      box-shadow: 0 6px 15px rgba(138, 43, 226, 0.5);
    }
    .gallery {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
      gap: 20px;
      padding: 20px;
      max-width: 1200px;
      position: relative;
      z-index: 1;
    }
    .gallery img {
      max-width: 100%;
      border-radius: 10px;
      box-shadow: 0 6px 12px rgba(0, 0, 0, 0.3);
      transition: transform 0.3s, box-shadow 0.3s;
    }
    .gallery img:hover {
      transform: scale(1.1);
      box-shadow: 0 8px 20px rgba(138, 43, 226, 0.5);
    }
    .proposal {
      margin: 40px auto;
      padding: 20px;
      background: rgba(255, 255, 255, 0.95);
      border-radius: 15px;
      max-width: 600px;
      box-shadow: 0 8px 16px rgba(0, 0, 0, 0.3);
      position: relative;
      z-index: 1;
    }
    #proposal-text {
      display: none;
      font-size: 2.2em;
      color: #000;
      margin-top: 20px;
      animation: fadeIn 1.5s;
    }
    @keyframes fadeIn {
      from { opacity: 0; }
      to { opacity: 1; }
    }
    /* Efeitos de corações no pedido */
    .heart-proposal {
      position: absolute;
      width: 25px;
      height: 25px;
      background: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="%23ffffff"><path d="M12 21.35l-1.45-1.32C5.4 15.36 2 12.28 2 8.5 2 5.42 4.42 3 7.5 3c1.74 0 3.41.81 4.5 2.09C13.09 3.81 14.76 3 16.5 3 19.58 3 22 5.42 22 8.5c0 3.78-3.4 6.86-8.55 11.54L12 21.35z"/></svg>') no-repeat center;
      background-size: contain;
      animation: floatProposal 4s ease-in-out;
    }
    @keyframes floatProposal {
      0% { transform: translateY(0) rotate(0deg); opacity: 0.8; }
      100% { transform: translateY(-60vh) rotate(360deg); opacity: 0; }
    }
    @media (max-width: 600px) {
      h1 { font-size: 2.8em; }
      p { font-size: 1.1em; }
      .gallery { grid-template-columns: 1fr; }
    }
  </style>
</head>
<body>
  <header>
    <h1>Para minha Rapunzel</h1>
    <p>Você transformou meus dias em algo mágico, e quero te mostrar o quanto você é especial para mim.</p>
  </header>

  <section class="upload-section">
    <h2>Adicione Nossas Fotos</h2>
    <input type="file" id="photoInput" accept="image/*" multiple>
    <button onclick="uploadPhotos()">Enviar Fotos</button>
  </section>

  <section class="gallery" id="gallery"></section>

  <section class="proposal">
    <p>Você é o
