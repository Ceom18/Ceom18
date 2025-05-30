<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Cls Contas FF</title>
  <style>
    body {
      background: #111;
      color: white;
      font-family: Arial, sans-serif;
      padding: 20px;
    }
    h1 {
      color: #00ff99;
    }
    .filtro {
      margin-bottom: 20px;
    }
    .conta {
      padding: 15px;
      margin-bottom: 10px;
      background: #222;
      border-left: 5px solid #00ff99;
    }
    .estrelas {
      unicode-bidi: bidi-override;
      direction: rtl;
      font-size: 22px;
      user-select: none;
    }
    .estrelas > span {
      display: inline-block;
      position: relative;
      color: gray;
      cursor: pointer;
    }
    .estrelas > span:hover,
    .estrelas > span:hover ~ span {
      color: gold;
    }
    .estrelas.avaliado > span {
      color: gold;
    }
  </style>
  <script>
    window.onload = function () {
      const senha = prompt("Digite a senha para acessar o site:");
      if (senha !== "Cls#118119") {
        alert("Acesso negado.");
        window.location.href = "https://google.com";
        return;
      }

      window.filtrar = function () {
        const filtro = document.getElementById("raridade").value;
        const contas = document.querySelectorAll(".conta");

        contas.forEach(conta => {
          if (filtro === "todas" || conta.getAttribute("data-raridade") === filtro) {
            conta.style.display = "block";
          } else {
            conta.style.display = "none";
          }
        });
      };

      window.avaliar = function (estrelasEl, nota) {
        estrelasEl.classList.add('avaliado');
        const estrelas = estrelasEl.querySelectorAll('span');
        estrelas.forEach((estrela, index) => {
          estrela.style.color = index < nota ? 'gold' : 'gray';
        });
        const contaId = estrelasEl.getAttribute("data-conta-id");
        localStorage.setItem(`avaliacao_${contaId}`, nota);
      };

      function carregarAvaliacoes() {
        const todos = document.querySelectorAll('.estrelas');
        todos.forEach(el => {
          const contaId = el.getAttribute("data-conta-id");
          const nota = localStorage.getItem(`avaliacao_${contaId}`);
          if (nota) {
            avaliar(el, parseInt(nota));
          }
        });
      }

      carregarAvaliacoes();
    };
  </script>
</head>
<body>
  <h1>Cls Contas FF</h1>
  <div class="filtro">
    <label for="raridade">Filtrar por raridade:</label>
    <select id="raridade" onchange="filtrar()">
      <option value="todas">Todas</option>
      <option value="comum">Comum</option>
      <option value="intermediaria">Intermediária</option>
      <option value="rara">Rara</option>
      <option value="lendaria">Lendária</option>
    </select>
  </div>
  <div class="contas">
    <div class="conta" data-raridade="comum">
      Conta 1 - Comum
      <div class="estrelas" data-conta-id="conta1">
        <span onclick="avaliar(this.parentNode, 5)">★</span>
        <span onclick="avaliar(this.parentNode, 4)">★</span>
        <span onclick="avaliar(this.parentNode, 3)">★</span>
        <span onclick="avaliar(this.parentNode, 2)">★</span>
        <span onclick="avaliar(this.parentNode, 1)">★</span>
      </div>
    </div>
    <div class="conta" data-raridade="intermediaria">
      Conta 2 - Intermediária
      <div class="estrelas" data-conta-id="conta2">
        <span onclick="avaliar(this.parentNode, 5)">★</span>
        <span onclick="avaliar(this.parentNode, 4)">★</span>
        <span onclick="avaliar(this.parentNode, 3)">★</span>
        <span onclick="avaliar(this.parentNode, 2)">★</span>
        <span onclick="avaliar(this.parentNode, 1)">★</span>
      </div>
    </div>
    <div class="conta" data-raridade="rara">
      Conta 3 - Rara
      <div class="estrelas" data-conta-id="conta3">
        <span onclick="avaliar(this.parentNode, 5)">★</span>
        <span onclick="avaliar(this.parentNode, 4)">★</span>
        <span onclick="avaliar(this.parentNode, 3)">★</span>
        <span onclick="avaliar(this.parentNode, 2)">★</span>
        <span onclick="avaliar(this.parentNode, 1)">★</span>
      </div>
    </div>
    <div class="conta" data-raridade="lendaria">
      Conta 4 - Lendária
      <div class="estrelas" data-conta-id="conta4">
        <span onclick="avaliar(this.parentNode, 5)">★</span>
        <span onclick="avaliar(this.parentNode, 4)">★</span>
        <span onclick="avaliar(this.parentNode, 3)">★</span>
        <span onclick="avaliar(this.parentNode, 2)">★</span>
        <span onclick="avaliar(this.parentNode, 1)">★</span>
      </div>
    </div>
    <div class="conta" data-raridade="rara">
      Conta 5 - Rara
      <div class="estrelas" data-conta-id="conta5">
        <span onclick="avaliar(this.parentNode, 5)">★</span>
        <span onclick="avaliar(this.parentNode, 4)">★</span>
        <span onclick="avaliar(this.parentNode, 3)">★</span>
        <span onclick="avaliar(this.parentNode, 2)">★</span>
        <span onclick="avaliar(this.parentNode, 1)">★</span>
      </div>
    </div>
    <div class="conta" data-raridade="comum">
      Conta 6 - Comum
      <div class="estrelas" data-conta-id="conta6">
        <span onclick="avaliar(this.parentNode, 5)">★</span>
        <span onclick="avaliar(this.parentNode, 4)">★</span>
        <span onclick="avaliar(this.parentNode, 3)">★</span>
        <span onclick="avaliar(this.parentNode, 2)">★</span>
        <span onclick="avaliar(this.parentNode, 1)">★</span>
      </div>
    </div>
    <div class="conta" data-raridade="intermediaria">
      Conta 7 - Intermediária
      <div class="estrelas" data-conta-id="conta7">
        <span onclick="avaliar(this.parentNode, 5)">★</span>
        <span onclick="avaliar(this.parentNode, 4)">★</span>
        <span onclick="avaliar(this.parentNode, 3)">★</span>
        <span onclick="avaliar(this.parentNode, 2)">★</span>
        <span onclick="avaliar(this.parentNode, 1)">★</span>
      </div>
    </div>
    <div class="conta" data-raridade="lendaria">
      Conta 8 - Lendária
      <div class="estrelas" data-conta-id="conta8">
        <span onclick="avaliar(this.parentNode, 5)">★</span>
        <span onclick="avaliar(this.parentNode, 4)">★</span>
        <span onclick="avaliar(this.parentNode, 3)">★</span>
        <span onclick="avaliar(this.parentNode, 2)">★</span>
        <span onclick="avaliar(this.parentNode, 1)">★</span>
      </div>
    </div>
  </div>
</body>
</html>
