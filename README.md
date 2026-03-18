<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Venda de Casas</title>
  <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="bg-gray-100">

  <!-- LOGIN -->
  <div id="loginScreen" class="flex items-center justify-center h-screen">
    <div class="bg-white p-8 rounded-2xl shadow w-80">
      <h2 class="text-xl font-bold mb-4 text-center">Login Administrador</h2>
      <input id="user" type="text" placeholder="Usuário" class="border p-2 rounded w-full mb-3">
      <input id="pass" type="password" placeholder="Senha" class="border p-2 rounded w-full mb-3">
      <button onclick="login()" class="bg-blue-600 text-white w-full p-2 rounded">Entrar</button>
      <p id="erro" class="text-red-500 text-sm mt-2 text-center"></p>
    </div>
  </div>

  <!-- SITE -->
  <div id="site" class="hidden">
    <header class="bg-blue-600 text-white p-5 text-center text-2xl font-bold">
      Casas à Venda
      <button onclick="logout()" class="ml-4 bg-red-500 px-3 py-1 rounded">Sair</button>
    </header>

    <main class="p-6 grid grid-cols-1 md:grid-cols-3 gap-6" id="listaCasas">

      <!-- Casas aparecem aqui -->

    </main>

    <section class="p-6 bg-white mt-6">
      <h2 class="text-xl font-bold mb-4">Adicionar Nova Casa</h2>
      <form onsubmit="adicionarCasa(event)" class="grid gap-4">
        <input id="nome" type="text" placeholder="Nome da casa" class="border p-2 rounded" required>
        <input id="desc" type="text" placeholder="Descrição" class="border p-2 rounded" required>
        <input id="preco" type="text" placeholder="Preço" class="border p-2 rounded" required>
        <input id="img" type="text" placeholder="URL da imagem" class="border p-2 rounded" required>
        <button class="bg-green-600 text-white p-2 rounded">Adicionar</button>
      </form>
    </section>

    <footer class="bg-gray-800 text-white text-center p-4 mt-6">
      © 2026 Venda de Casas
    </footer>
  </div>

  <script>
    const USER = "admin";
    const PASS = "1234";

    function login(){
      const u = document.getElementById('user').value;
      const p = document.getElementById('pass').value;

      if(u === USER && p === PASS){
        document.getElementById('loginScreen').classList.add('hidden');
        document.getElementById('site').classList.remove('hidden');
      } else {
        document.getElementById('erro').innerText = "Usuário ou senha inválidos";
      }
    }

    function logout(){
      document.getElementById('site').classList.add('hidden');
      document.getElementById('loginScreen').classList.remove('hidden');
    }

    function adicionarCasa(e){
      e.preventDefault();

      const nome = document.getElementById('nome').value;
      const desc = document.getElementById('desc').value;
      const preco = document.getElementById('preco').value;
      const img = document.getElementById('img').value;

      const card = `
        <div class="bg-white rounded-2xl shadow p-4">
          <img src="${img}" class="rounded-xl mb-3" />
          <h2 class="text-xl font-bold">${nome}</h2>
          <p class="text-gray-600">${desc}</p>
          <p class="text-green-600 font-bold text-lg mt-2">${preco}</p>
        </div>
      `;

      document.getElementById('listaCasas').innerHTML += card;

      e.target.reset();
    }
  </script>

</body>
</html>
