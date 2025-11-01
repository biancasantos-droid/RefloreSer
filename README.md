# RefloreSer
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>RefloreSer</title>
  <link href="https://fonts.googleapis.com/css2?family=Comic+Neue:wght@400;700&display=swap" rel="stylesheet">
  <style>
    :root {
      --color1: #FF6B6B; --color2: #4ECDC4; --color3: #FFD166; --color4: #06D6A0; --color5: #118AB2; --color6: #EF476F;
      --background: linear-gradient(135deg, #A1C4FD 0%, #C2E9FB 100%); --card-bg: rgba(255, 255, 255, 0.95); --shadow: 0 8px 25px rgba(0, 0, 0, 0.1);
    }
    * { margin: 0; padding: 0; box-sizing: border-box; }
    body { font-family: 'Comic Neue', cursive; background: var(--background); min-height: 100vh; padding: 1rem; }
    .container { max-width: 1200px; margin: 0 auto; }
    .header { text-align: center; margin-bottom: 2rem; animation: bounce 2s infinite; }
    .logo { display: inline-flex; align-items: center; gap: 1rem; margin-bottom: 1rem; background: white; padding: 1rem 2rem; border-radius: 50px; box-shadow: var(--shadow); }
    .logo-emoji { font-size: 3rem; animation: spin 4s linear infinite; }
    .logo-text h1 { font-size: 2.5rem; font-weight: 700; color: var(--color5); margin-bottom: 0.5rem; text-shadow: 2px 2px 0px rgba(0,0,0,0.1); }
    .logo-text p { font-size: 1.1rem; color: var(--color1); font-weight: 400; }
    .developers { font-size: 1rem; color: var(--color5); font-weight: 600; margin-top: 0.5rem; background: rgba(255, 255, 255, 0.8); padding: 0.8rem 1.5rem; border-radius: 20px; display: inline-block; line-height: 1.4; }
    .cards-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 1.5rem; margin-bottom: 2rem; }
    .card { background: var(--card-bg); border-radius: 25px; padding: 1.5rem; box-shadow: var(--shadow); transition: all 0.3s ease; border: 4px solid; position: relative; overflow: hidden; }
    .card:hover { transform: translateY(-10px) scale(1.02); }
    .card-header { display: flex; align-items: center; margin-bottom: 1rem; gap: 1rem; }
    .card-emoji { font-size: 3.5rem; width: 80px; height: 80px; display: flex; align-items: center; justify-content: center; border-radius: 20px; animation: float 3s ease-in-out infinite; }
    .card-title { font-size: 1.8rem; font-weight: 700; flex: 1; text-shadow: 1px 1px 0px rgba(0,0,0,0.1); }
    .card-content { font-size: 1.1rem; line-height: 1.6; }
    .fun-fact { background: rgba(255, 255, 255, 0.7); padding: 1rem; border-radius: 15px; margin-top: 1rem; border-left: 4px solid var(--color3); }
    .fun-fact-title { font-weight: 700; color: var(--color6); margin-bottom: 0.5rem; display: flex; align-items: center; gap: 0.5rem; }
    .card-sun { border-color: var(--color3); background: linear-gradient(135deg, #FFF9C4, #FFEB3B); }
    .card-sun .card-emoji { background: var(--color3); }
    .card-plants { border-color: var(--color4); background: linear-gradient(135deg, #C8E6C9, #4CAF50); }
    .card-plants .card-emoji { background: var(--color4); }
    .card-water { border-color: var(--color5); background: linear-gradient(135deg, #B3E5FC, #03A9F4); }
    .card-water .card-emoji { background: var(--color5); }
    .card-animals { border-color: var(--color1); background: linear-gradient(135deg, #FFCDD2, #F44336); }
    .card-animals .card-emoji { background: var(--color1); }
    .card-conservation { border-color: var(--color2); background: linear-gradient(135deg, #B2EBF2, #00BCD4); }
    .card-conservation .card-emoji { background: var(--color2); }
    .card-mission { border-color: var(--color6); background: linear-gradient(135deg, #F8BBD0, #E91E63); }
    .card-mission .card-emoji { background: var(--color6); }
    .actions { display: flex; justify-content: center; margin-top: 2rem; }
    .action-btn { padding: 1.5rem 3rem; border: none; border-radius: 50px; font-family: 'Comic Neue', cursive; font-weight: 700; cursor: pointer; transition: all 0.3s ease; display: flex; align-items: center; gap: 1rem; font-size: 1.5rem; box-shadow: 0 6px 0 rgba(0,0,0,0.2); position: relative; transform: translateY(0); background: var(--color3); color: #333; }
    .action-btn:hover { transform: translateY(-3px); box-shadow: 0 8px 0 rgba(0,0,0,0.2); }
    .action-btn:active { transform: translateY(2px); box-shadow: 0 2px 0 rgba(0,0,0,0.2); }
    .quiz-modal { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0, 0, 0, 0.8); z-index: 1000; align-items: center; justify-content: center; }
    .quiz-content { background: white; border-radius: 25px; padding: 2rem; max-width: 500px; width: 90%; text-align: center; box-shadow: 0 20px 50px rgba(0,0,0,0.3); }
    .quiz-question { font-size: 1.5rem; margin-bottom: 1.5rem; color: var(--color5); }
    .quiz-options { display: flex; flex-direction: column; gap: 1rem; margin-bottom: 1.5rem; }
    .quiz-option { padding: 1rem; background: var(--color2); color: white; border: none; border-radius: 15px; font-family: 'Comic Neue', cursive; font-size: 1.2rem; cursor: pointer; transition: all 0.3s ease; }
    .quiz-option:hover { transform: scale(1.05); background: var(--color4); }
    .quiz-result { font-size: 1.3rem; font-weight: 700; margin-top: 1rem; padding: 1rem; border-radius: 15px; }
    .correct { background: #C8E6C9; color: #2E8B57; }
    .wrong { background: #FFCDD2; color: #D32F2F; }
    .decoration { position: fixed; font-size: 2rem; z-index: -1; animation: float 6s ease-in-out infinite; }
    .decoration:nth-child(1) { top: 10%; left: 5%; animation-delay: 0s; }
    .decoration:nth-child(2) { top: 20%; right: 10%; animation-delay: 1s; }
    .decoration:nth-child(3) { bottom: 30%; left: 8%; animation-delay: 2s; }
    .decoration:nth-child(4) { bottom: 20%; right: 5%; animation-delay: 3s; }
    .decoration:nth-child(5) { top: 40%; left: 15%; animation-delay: 4s; }
    @keyframes bounce { 0%, 100% { transform: translateY(0); } 50% { transform: translateY(-10px); } }
    @keyframes spin { 0% { transform: rotate(0deg); } 100% { transform: rotate(360deg); } }
    @keyframes float { 0%, 100% { transform: translateY(0); } 50% { transform: translateY(-10px); } }
    @keyframes wiggle { 0%, 100% { transform: rotate(0deg); } 25% { transform: rotate(-5deg); } 75% { transform: rotate(5deg); } }
    @media (max-width: 768px) {
      body { padding: 0.5rem; }
      .logo { flex-direction: column; text-align: center; }
      .cards-grid { grid-template-columns: 1fr; }
      .card-header { flex-direction: column; text-align: center; }
      .action-btn { width: 100%; max-width: 300px; justify-content: center; }
      .decoration { display: none; }
    }
    .card:hover .card-emoji { animation: wiggle 0.5s ease-in-out; }
    .highlight { background: linear-gradient(120deg, transparent 0%, transparent 50%, var(--color3) 50%); background-size: 220% 100%; background-position: 100% 0; transition: all 0.3s ease; }
    .card:hover .highlight { background-position: 0 0; }
  </style>
</head>
<body>
  <div class="decoration">🌿</div><div class="decoration">🐾</div><div class="decoration">💧</div><div class="decoration">🌞</div><div class="decoration">🦋</div>
  <div class="container">
    <header class="header">
      <div class="logo">
        <div class="logo-emoji">🌎</div>
        <div class="logo-text">
          <h1>RefloreSer</h1>
          <p>Uma aventura na floresta! 🎉</p>
          <div class="developers">
            <strong>QUEM VAI APRESENTAR, TÁ NA FRENTE DE VOCÊS!</strong><br>
            Desenvolvido por: Bianca Rufino, tia do Matthew 👩‍💻
          </div>
        </div>
      </div>
    </header>
    <div class="cards-grid">
      <div class="card card-sun"><div class="card-header"><div class="card-emoji">☀️</div><h2 class="card-title">Super Sol</h2></div><div class="card-content"><p>O sol é como um <span class="highlight">super-herói</span> que dá energia para todas as plantinhas crescerem fortes e saudáveis! 🌱</p><div class="fun-fact"><div class="fun-fact-title">🤔 Sabia que?</div><p>Sem o sol, não teríamos frutas deliciosas como manga, banana e laranja! 🍌🍊</p></div></div></div>
      <div class="card card-plants"><div class="card-header"><div class="card-emoji">🌳</div><h2 class="card-title">Plantas Mágicas</h2></div><div class="card-content"><p>As plantas são os <span class="highlight">pulmões do planeta</span>! Elas transformam o ar que respiramos em algo super fresco! 💚</p><div class="fun-fact"><div class="fun-fact-title">🌺 Por que plantar é importante?</div><p>Plantar mudinhas ajuda a deixar o ar mais limpinho, dá casa para os bichinhos e deixa o mundo mais bonito! 🏡</p></div></div></div>
      <div class="card card-water"><div class="card-header"><div class="card-emoji">💧</div><h2 class="card-title">Água Divertida</h2></div><div class="card-content"><p>A água é como um <span class="highlight">parque de diversões</span> para os animais! Eles bebem, nadam e se refrescam nela! 🐠</p><div class="fun-fact"><div class="fun-fact-title">💙 Dica Importante</div><p>Feche a torneira enquanto escova os dentes para ajudar a natureza! É super fácil e faz muita diferença! 😊</p></div></div></div>
      <div class="card card-animals"><div class="card-header"><div class="card-emoji">🐆</div><h2 class="card-title">Amigos Animais</h2></div><div class="card-content"><p>Os animais precisam da natureza para <span class="highlight">viver felizes</span>! Eles precisam de árvores, água limpa e ar puro! 🐒</p><div class="fun-fact"><div class="fun-fact-title">🏠 Casa dos Bichinhos</div><p>A onça-pintada 🐆 precisa da floresta para caçar, e os passarinhos 🐦 precisam das árvores para fazer seus ninhos!</p></div></div></div>
      <div class="card card-conservation"><div class="card-header"><div class="card-emoji">🛡️</div><h2 class="card-title">Heróis da Natureza</h2></div><div class="card-content"><p>Você também pode ser um <span class="highlight">super-herói</span> da natureza! Basta cuidar das plantinhas e dos bichinhos! 🦸‍♀️🦸‍♂️</p><div class="fun-fact"><div class="fun-fact-title">💪 Como Ajudar</div><p>Não jogue lixo no chão e avise um adulto se ver alguém maltratando a natureza! 👮‍♀️</p></div></div></div>
      <div class="card card-mission"><div class="card-header"><div class="card-emoji">🎯</div><h2 class="card-title">Missão Especial</h2></div><div class="card-content"><p>Que tal fazer uma <span class="highlight">aventura super legal</span> na sua escola? Vamos plantar uma mudinha juntos! 🌱</p><div class="fun-fact"><div class="fun-fact-title">🌟 Parte 2 da Diversão</div><p>Peça para sua professora ajudar a plantar uma árvore na escola! Vocês vão ver ela crescer e ficar gigante! 🌳</p></div></div></div>
    </div>
    <div class="actions">
      <button class="action-btn" onclick="startQuiz()"><span>🎮</span> Quiz da Natureza</button>
    </div>
  </div>
  <div class="quiz-modal" id="quizModal">
    <div class="quiz-content">
      <h2 class="quiz-question" id="quizQuestion">Pergunta aqui?</h2>
      <div class="quiz-options" id="quizOptions"></div>
      <div class="quiz-result" id="quizResult" style="display: none;"></div>
      <button class="quiz-option" onclick="closeQuiz()" style="background: var(--color1);">Fechar</button>
    </div>
  </div>
  <script>
    const quizQuestions = [
      {question: "O que as plantas produzem durante a fotossíntese? 🌿", options: ["Oxigênio para respirarmos 💨", "Bolinhas de sabão 🫧", "Som de música 🎵", "Luz colorida 💡"], correct: 0},
      {question: "Por que os animais precisam das árvores? 🌳", options: ["Para ter casa e comida 🏠", "Para fazer penteados 💇", "Para brincar de esconde-esconde 🙈", "Para contar histórias 📖"], correct: 0},
      {question: "Qual é a missão do RefloreSer? 🎯", options: ["Plantar mudinhas e cuidar da natureza 🌱", "Comer todas as frutas 🍉", "Correr na floresta 🏃", "Pintar as folhas 🎨"], correct: 0},
      {question: "Como podemos economizar água? 💧", options: ["Fechando a torneira ao escovar os dentes 🦷", "Bebendo menos água 🚱", "Nadando na piscina 🏊", "Chovendo menos ☔"], correct: 0},
      {question: "O que acontece se não tivermos sol? ☀️", options: ["As plantas não crescem 🌱", "Fica sempre noite 🌙", "Os animais dormem mais 😴", "Chove chocolate 🍫"], correct: 0},
      {question: "Por que não devemos jogar lixo no chão? 🗑️", options: ["Para não poluir a natureza 🌍", "Porque é divertido 🎪", "Para os bichos brincarem 🐭", "Para fazer arte 🎨"], correct: 0},
      {question: "O que a onça-pintada precisa para viver? 🐆", options: ["Floresta para caçar e água limpa 🌳", "Roupas coloridas 👗", "Carro para passear 🚗", "Televisão 📺"], correct: 0},
      {question: "Qual é o benefício de plantar árvores? 🌴", options: ["Ar mais limpo e casa para animais 💨", "Fazer sombra para ninguém ☂️", "Cair folhas no chão 🍂", "Fazer barulho com o vento 🍃"], correct: 0},
      {question: "O que podemos fazer na escola? 🏫", options: ["Plantar uma mudinha com a professora 🌱", "Correr nos corredores 🏃", "Fazer bagunça na aula 🤪", "Comer toda a merenda 🍎"], correct: 0},
      {question: "Por que a natureza é importante? 💚", options: ["Ela nos dá ar, água e comida 🌍", "É bonita de se ver 👀", "Tem cores legais 🎨", "Faz som no vento 🎵"], correct: 0}
    ];
    let currentQuestion = 0, score = 0;
    function startQuiz() { currentQuestion = 0; score = 0; showQuestion(); document.getElementById('quizModal').style.display = 'flex'; }
    function showQuestion() {
      const question = quizQuestions[currentQuestion], questionElement = document.getElementById('quizQuestion'), optionsElement = document.getElementById('quizOptions'), resultElement = document.getElementById('quizResult');
      resultElement.style.display = 'none'; questionElement.textContent = question.question; optionsElement.innerHTML = '';
      question.options.forEach((option, index) => {
        const button = document.createElement('button'); button.className = 'quiz-option'; button.textContent = option; button.onclick = () => checkAnswer(index); optionsElement.appendChild(button);
      });
    }
    function checkAnswer(selectedIndex) {
      const question = quizQuestions[currentQuestion], resultElement = document.getElementById('quizResult');
      if (selectedIndex === question.correct) { resultElement.textContent = "🎉 Parabéns! Resposta correta! 🌟"; resultElement.className = 'quiz-result correct'; score++; } 
      else { resultElement.textContent = "💡 Que pena! Tente a próxima! 😊"; resultElement.className = 'quiz-result wrong'; }
      resultElement.style.display = 'block';
      setTimeout(() => {
        currentQuestion++;
        if (currentQuestion < quizQuestions.length) showQuestion();
        else { const percentage = Math.round((score / quizQuestions.length) * 100); resultElement.textContent = `🏆 Quiz completo! Você acertou ${score} de ${quizQuestions.length} perguntas! (${percentage}%) 🦸`; resultElement.className = 'quiz-result correct'; }
      }, 2000);
    }
    function closeQuiz() { document.getElementById('quizModal').style.display = 'none'; }
    document.addEventListener('DOMContentLoaded', function() {
      const cards = document.querySelectorAll('.card');
      cards.forEach((card, index) => {
        card.style.animationDelay = `${index * 0.2}s`; card.style.opacity = '0'; card.style.animation = `float 0.5s ease-out ${index * 0.2}s forwards`;
        card.addEventListener('click', function() { this.style.transform = 'scale(0.95)'; setTimeout(() => { this.style.transform = 'scale(1)'; }, 150); });
      });
      setTimeout(() => { cards.forEach(card => { card.style.opacity = '1'; }); }, 500);
    });
    document.querySelector('.action-btn').addEventListener('click', function() {
      this.style.animation = 'bounce 0.5s ease-in-out'; setTimeout(() => { this.style.animation = ''; }, 500);
    });
  </script>
</body>
</html>
