<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Portal de Projetos - C.E.C.M. Princesa Izabel</title>
  <style>
    :root {
      --primary-color: #0d3b66;
      --secondary-color: #f4d35e;
      --accent-color: #f95738;
      --bg-color: #f4f4f9;
      --card-bg: #ffffff;
      --text-color: #333333;
    }

    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background-color: var(--bg-color);
      color: var(--text-color);
      margin: 0;
      padding: 0;
    }

    header {
      background-color: var(--primary-color);
      color: white;
      padding: 1.5rem 2rem;
      text-align: center;
      box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    }

    header h1 {
      margin: 0;
      font-size: 1.8rem;
    }

    header p {
      margin: 0.5rem 0 0;
      font-size: 1rem;
      color: var(--secondary-color);
    }

    nav {
      background-color: #092c4c;
      display: flex;
      justify-content: center;
      gap: 15px;
      padding: 10px;
    }

    nav button {
      background: transparent;
      border: 1px solid white;
      color: white;
      padding: 8px 16px;
      border-radius: 4px;
      cursor: pointer;
      transition: 0.3s;
    }

    nav button:hover {
      background-color: var(--secondary-color);
      color: var(--primary-color);
    }

    .container {
      max-width: 1100px;
      margin: 20px auto;
      padding: 0 20px;
    }

    .auth-box, .submission-box {
      background: var(--card-bg);
      padding: 20px;
      border-radius: 8px;
      box-shadow: 0 2px 4px rgba(0,0,0,0.1);
      margin-bottom: 25px;
    }

    .form-group {
      margin-bottom: 15px;
    }

    .form-group label {
      display: block;
      margin-bottom: 5px;
      font-weight: bold;
    }

    .form-group input, .form-group select, .form-group textarea {
      width: 100%;
      padding: 10px;
      border: 1px solid #ccc;
      border-radius: 4px;
      box-sizing: border-box;
    }

    .btn-submit {
      background-color: var(--primary-color);
      color: white;
      border: none;
      padding: 10px 20px;
      border-radius: 4px;
      cursor: pointer;
      font-size: 1rem;
    }

    .btn-submit:hover {
      background-color: #092c4c;
    }

    .turmas-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));
      gap: 15px;
      margin-top: 15px;
    }

    .turma-card {
      background: var(--card-bg);
      border-left: 5px solid var(--primary-color);
      padding: 15px;
      border-radius: 4px;
      text-align: center;
      box-shadow: 0 2px 4px rgba(0,0,0,0.05);
      cursor: pointer;
      font-weight: bold;
      transition: transform 0.2s;
    }

    .turma-card:hover {
      transform: translateY(-3px);
    }

    .badge-prof {
      background-color: var(--accent-color);
      color: white;
      padding: 3px 8px;
      border-radius: 12px;
      font-size: 0.8rem;
    }
  </style>
</head>
<body>

  <header>
    <h1>Colégio Estadual Cívico Militar Princesa Izabel</h1>
    <p>Plataforma de Projetos Acadêmicos e Trabalhos de Sala de Aula</p>
  </header>

  <nav>
    <button onclick="filtrarNivel('todos')">Todas as Turmas</button>
    <button onclick="filtrarNivel('fundamental')">Ensino Fundamental</button>
    <button onclick="filtrarNivel('medio')">Ensino Médio</button>
  </nav>

  <div class="container">
    
    <!-- ÁREA DE AUTENTICAÇÃO / LOGIN -->
    <div class="auth-box">
      <h3>Acesso ao Sistema</h3>
      <p>Utilize seu e-mail institucional (<strong>@escola.pr.gov.br</strong>) para acessar.</p>
      <div class="form-group">
        <label for="email">E-mail Institucional:</label>
        <input type="email" id="email" placeholder="seu.nome@escola.pr.gov.br">
      </div>
      <div class="form-group">
        <label for="tipoUsuario">Perfil de Acesso:</label>
        <select id="tipoUsuario">
          <option value="aluno">Aluno (Acesso Restrito à Turma)</option>
          <option value="professor">Professor (Acesso Livre Total)</option>
        </select>
      </div>
      <button class="btn-submit" onclick="validarAcesso()">Entrar</button>
    </div>

    <!-- SELEÇÃO DE TURMAS -->
    <h2>Turmas Cadastradas</h2>
    
    <h3>Ensino Fundamental</h3>
    <div class="turmas-grid">
      <div class="turma-card">8° Ano A</div>
      <div class="turma-card">8° Ano B</div>
      <div class="turma-card">8° Ano C</div>
      <div class="turma-card">9° Ano A</div>
      <div class="turma-card">9° Ano B</div>
      <div class="turma-card">9° Ano C</div>
      <div class="turma-card">9° Ano D</div>
    </div>

    <h3 style="margin-top: 30px;">Ensino Médio</h3>
    <div class="turmas-grid">
      <div class="turma-card">1° Ano A</div>
      <div class="turma-card">1° Ano B</div>
      <div class="turma-card">1° Ano C</div>
      <div class="turma-card">2° Ano A</div>
      <div class="turma-card">2° Ano B</div>
      <div class="turma-card">2° Ano C</div>
    </div>

    <!-- ENVIAR PROJETO (ALUNOS) -->
    <div class="submission-box" style="margin-top: 40px;">
      <h3>Publicar Novo Projeto</h3>
      <form id="projectForm">
        <div class="form-group">
          <label for="titulo">Título do Projeto:</label>
          <input type="text" id="titulo" required placeholder="Ex: Maquete de Célula Animal">
        </div>
        <div class="form-group">
          <label for="turmaSelect">Selecione sua Turma:</label>
          <select id="turmaSelect" required>
            <option value="">-- Selecione --</option>
            <option value="8A">8° Ano A</option>
            <option value="8B">8° Ano B</option>
            <option value="8C">8° Ano C</option>
            <option value="9A">9° Ano A</option>
            <option value="9B">9° Ano B</option>
            <option value="9C">9° Ano C</option>
            <option value="9D">9° Ano D</option>
            <option value="1A">1° Ano A</option>
            <option value="1B">1° Ano B</option>
            <option value="1C">1° Ano C</option>
            <option value="2A">2° Ano A</option>
            <option value="2B">2° Ano B</option>
            <option value="2C">2° Ano C</option>
          </select>
        </div>
        <div class="form-group">
          <label for="descricao">Descrição do Trabalho:</label>
          <textarea id="descricao" rows="4" placeholder="Escreva sobre o que é o projeto..."></textarea>
        </div>
        <div class="form-group">
          <label for="link">Link do Arquivo/Vídeo/Drive:</label>
          <input type="url" id="link" placeholder="https://drive.google.com/...">
        </div>
        <button type="button" class="btn-submit" onclick="salvarProjeto()">Enviar Projeto</button>
      </form>
    </div>

  </div>

  <script>
    function validarAcesso() {
      const email = document.getElementById('email').value.trim();
      const tipo = document.getElementById('tipoUsuario').value;

      if (!email.endsWith('@escola.pr.gov.br')) {
        alert('Erro: É necessário utilizar um e-mail válido com o domínio @escola.pr.gov.br');
        return;
      }

      if (tipo === 'professor') {
        alert('Acesso concedido como PROFESSOR. Você tem acesso livre a todas as turmas e projetos.');
      } else {
        alert('Acesso concedido como ALUNO. Seu acesso é restrito à sua turma e projetos.');
      }
    }

    function salvarProjeto() {
      const titulo = document.getElementById('titulo').value;
      const turma = document.getElementById('turmaSelect').value;

      if (!titulo || !turma) {
        alert('Por favor, preencha o título e selecione a turma.');
        return;
      }

      alert('Projeto "' + titulo + '" enviado com sucesso para a turma ' + turma + '!');
    }
  </script>
</body>
</html>
