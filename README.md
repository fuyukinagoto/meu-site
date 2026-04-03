<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>RPG Pirata</title>

<style>
body {
  margin: 0;
  font-family: serif;
  background: black;
  color: #e0c68c;
  text-align: center;
}

/* MENU */
#menu {
  display: flex;
  flex-direction: column;
  gap: 10px;
  margin-top: 100px;
}

button {
  background: #1a1a1a;
  border: 1px solid #e0c68c;
  color: #e0c68c;
  padding: 10px;
  font-size: 16px;
  cursor: pointer;
}

button:hover {
  background: #333;
}

/* CAIXAS */
#loreBox, #personagemBox, #rituaisBox {
  display: none;
  padding: 20px;
}
</style>
</head>

<body>

<!-- MENU -->
<div id="menu">
  <button onclick="abrirLore()">📖 História</button>
  <button onclick="abrirPersonagem()">👤 Personagem</button>
  <button onclick="abrirRituais()">✨ Rituais</button>
</div>

<!-- HISTÓRIA -->
<div id="loreBox">
  <h2>📖 História</h2>
  <p>
  A era de ouro dos piratas começou  em 1650 e teve seu fim em 1730 pois n tinha motivos pra continuar todo o mundo foi explorado tesouro encontrado lendas descobertas, mas tudo mudou na execução de um homem o capitão Ragnar Draven conhecido por ser o rei dos mares rei dos piratas o homem com a relíquia mais poderosa que já existiu o homem que já mais conheceu a derrota após anos sem motivação e percebendo que o tempo dos piratas tava acabando ele decidiu esconder seu tesouro em uma ilha desconhecida já mais vista por qualquer outro pirata ele escondeu sua relíquia os segredos do mundo e depois voltou, se entregou pra Marinha, e no dia da sua excursão "a era dos piratas n pode acabar n deve acabar, passamos anos de nossas vitórias na maio aventura que já existiu vamos fazer a próxima geração segui os nossos passos o mundo vai muda o mundo vai se diferente ENTÃO VÁ! PEGUE MINHA RELÍQUIA MEUS TESOUROS DESCUBRA O SEGREDO SOBRE O MUNDO SE TORNE O PRÓXIMO REI DOS PIRATAS!" Depois de suas palavras ele foi morto foi executado pela marinha com sua morte o mundo realmente mudou criaturas novas Ilhas nova o mundo se expandiu as regras das relíquias mudou o mundo tava diferente grande o suficiente pra fazer a a era de ouro dos piratas continua por mais 6 Mill anos
  </p>
  <button onclick="voltar()">Voltar</button>
</div>

<!-- PERSONAGEM -->
<div id="personagemBox">
  <h2>👤 Personagem</h2>
  <input type="text" id="nome" placeholder="Seu nome"><br><br>
  <button onclick="salvar()">Salvar</button>
  <p id="resultado"></p>
  <button onclick="voltar()">Voltar</button>
</div>

<!-- RITUAIS -->
<div id="rituaisBox">
  <h2>✨ Rituais</h2>

  <div>
    <button onclick="filtrar('geral')">Geral</button>
    <button onclick="filtrar('ataque')">Ataque</button>
    <button onclick="filtrar('defesa')">Defesa</button>
    <button onclick="filtrar('invocacao')">Invocação</button>
    <button onclick="filtrar('controle')">Controle</button>
    <button onclick="filtrar('suporte')">Suporte</button>
  </div>

  <div id="listaRituais" style="margin-top:15px; text-align:left;"></div>

  <br>
  <button onclick="voltar()">Voltar</button>
</div>

<script>
// SOM
function playSound() {
  const audio = new Audio("https://www.soundjay.com/page-flip-01a.mp3");
  audio.play();
}

// MENU
function voltar() {
  playSound();
  document.getElementById("menu").style.display = "flex";
  document.getElementById("loreBox").style.display = "none";
  document.getElementById("personagemBox").style.display = "none";
  document.getElementById("rituaisBox").style.display = "none";
}

// HISTÓRIA
function abrirLore() {
  playSound();
  document.getElementById("menu").style.display = "none";
  document.getElementById("loreBox").style.display = "block";
}

// PERSONAGEM
function abrirPersonagem() {
  playSound();
  document.getElementById("menu").style.display = "none";
  document.getElementById("personagemBox").style.display = "block";
}

function salvar() {
  let nome = document.getElementById("nome").value;
  localStorage.setItem("nome", nome);
  document.getElementById("resultado").innerText = "Salvo: " + nome;
}

// RITUAIS
const rituais = [
  {nome: "Chamas do Abismo", tipo: "ataque", desc: "Causa dano massivo com fogo sombrio."},
  {nome: "Escudo Fantasma", tipo: "defesa", desc: "Protege o usuário contra ataques."},
  {nome: "Invocar Kraken", tipo: "invocacao", desc: "Invoca uma criatura gigante dos mares."},
  {nome: "Correntes do Mar", tipo: "controle", desc: "Imobiliza inimigos."},
  {nome: "Benção das Marés", tipo: "suporte", desc: "Aumenta o poder dos aliados."}
];

function abrirRituais() {
  playSound();
  document.getElementById("menu").style.display = "none";
  document.getElementById("rituaisBox").style.display = "block";
  mostrarRituais("geral");
}

function mostrarRituais(tipo) {
  const lista = document.getElementById("listaRituais");
  lista.innerHTML = "";

  let filtrados = tipo === "geral"
    ? rituais
    : rituais.filter(r => r.tipo === tipo);

  filtrados.forEach(r => {
    lista.innerHTML += `
      <div style="margin-bottom:10px;">
        <b>${r.nome}</b><br>
        <small>${r.desc}</small>
      </div>
    `;
  });
}

function filtrar(tipo) {
  playSound();
  mostrarRituais(tipo);
}
</script>

</body>
</html>
