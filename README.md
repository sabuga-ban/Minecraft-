<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Verificação de Acesso</title>
  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    }

    body {
      background-color: #121214;
      color: #ffffff;
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
      padding: 20px;
    }

    .card {
      background-color: #202024;
      padding: 30px;
      border-radius: 8px;
      max-width: 400px;
      width: 100%;
      text-align: center;
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.5);
    }

    h2 {
      margin-bottom: 12px;
      color: #00b37e;
      font-size: 1.4rem;
    }

    p {
      color: #a8a8b3;
      font-size: 0.95rem;
      margin-bottom: 20px;
      line-height: 1.4;
    }

    .step {
      display: none;
    }

    .step.active {
      display: block;
    }

    input[type="text"] {
      width: 100%;
      padding: 12px;
      margin-bottom: 15px;
      border-radius: 4px;
      border: 1px solid #323238;
      background-color: #121214;
      color: #fff;
      font-size: 1.2rem;
      text-align: center;
      letter-spacing: 2px;
    }

    input[type="text"]:focus {
      outline: none;
      border-color: #00b37e;
    }

    button {
      width: 100%;
      padding: 12px;
      border: none;
      border-radius: 4px;
      background-color: #00875f;
      color: #fff;
      font-weight: bold;
      font-size: 1rem;
      cursor: pointer;
      transition: background-color 0.2s;
    }

    button:hover {
      background-color: #00b37e;
    }

    .checkbox-container {
      display: flex;
      align-items: center;
      gap: 10px;
      justify-content: center;
      margin-bottom: 20px;
      font-size: 0.95rem;
      cursor: pointer;
    }

    .checkbox-container input {
      width: 18px;
      height: 18px;
      cursor: pointer;
    }

    .error-message {
      color: #f75a68;
      font-size: 0.85rem;
      margin-top: 12px;
      display: none;
    }
  </style>
</head>
<body>

  <div class="card">
    
    <!-- ETAPA 1 -->
    <div id="step-1" class="step active">
      <h2>Etapa 1 de 2</h2>
      <p>Confirme a caixa de seleção abaixo para continuar.</p>
      
      <label class="checkbox-container">
        <input type="checkbox" id="check-step-1">
        <span>Sou maior de idade</span>
      </label>

      <button type="button" id="btn-step-1">Avançar</button>
      <div id="error-1" class="error-message">Você precisa marcar a opção para continuar.</div>
    </div>

    <!-- ETAPA 2 -->
    <div id="step-2" class="step">
      <h2>Etapa 2 de 2</h2>
      <p>Digite a senha de acesso (PIN de 4 dígitos):</p>
      
      <input type="text" id="pin-input" placeholder="1234" maxlength="4" autocomplete="off">

      <button type="button" id="btn-step-2">Continuar</button>
      <div id="error-2" class="error-message">Senha incorreta. Tente novamente!</div>
    </div>

    <!-- TELA FINAL / REDIRECIONAMENTO -->
    <div id="step-3" class="step">
      <h2>Acesso Concedido!</h2>
      <p>Aguarde, você está sendo redirecionado...</p>
    </div>

  </div>

  <script>
    // -------------------------------------------------------------
    // CONFIGURE O SEU LINK DE DESTINO E SENHA AQUI
    // -------------------------------------------------------------
    const LINK_DESTINO = "https://www.google.com"; // Troque pelo link que quiser
    const SENHA_CORRETA = "1234";                  // Troque pela senha que desejar

    // Capturando elementos do HTML
    const step1 = document.getElementById('step-1');
    const step2 = document.getElementById('step-2');
    const step3 = document.getElementById('step-3');

    const checkStep1 = document.getElementById('check-step-1');
    const btnStep1 = document.getElementById('btn-step-1');
    const error1 = document.getElementById('error-1');

    const pinInput = document.getElementById('pin-input');
    const btnStep2 = document.getElementById('btn-step-2');
    const error2 = document.getElementById('error-2');

    // Ação do Botão da Etapa 1
    btnStep1.onclick = function () {
      if (checkStep1.checked) {
        error1.style.display = 'none';
        step1.classList.remove('active');
        step2.classList.add('active');
      } else {
        error1.style.display = 'block';
      }
    };

    // Ação do Botão da Etapa 2 (Continuar)
    btnStep2.onclick = function () {
      const valorDigitado = pinInput.value.trim();

      if (valorDigitado === SENHA_CORRETA) {
        error2.style.display = 'none';
        step2.classList.remove('active');
        step3.classList.add('active');

        // Redireciona imediatamente após o sucesso
        window.location.href = LINK_DESTINO;
      } else {
        error2.style.display = 'block';
      }
    };
  </script>

</body>
</html>
