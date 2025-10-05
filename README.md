<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Online Game Tournament Management</title>
  <script src="https://cdn.tailwindcss.com"></script>
</head>

<body class="bg-gray-900 text-gray-100 font-sans">

  <!-- ===== Navbar ===== -->
  <nav class="bg-gray-800 py-4 shadow-md">
    <div class="container mx-auto flex justify-between items-center px-4">
      <h1 class="text-2xl font-bold text-blue-400">Game Tournament Manager</h1>
      <span class="text-sm text-gray-400">v1.0</span>
    </div>
  </nav>

  <!-- ===== Header Section ===== -->
  <section class="text-center py-10 bg-gradient-to-b from-gray-900 to-gray-800">
    <h2 class="text-4xl font-bold text-blue-400 mb-2">Online Game Tournament Registration</h2>
    <p class="text-gray-300 mb-6">Register your details and see how many players have joined!</p>

    <!-- ===== Game Image Banner ===== -->
    <div class="flex justify-center">
      <img src="https://upload.wikimedia.org/wikipedia/en/5/51/Valorant_cover_art.jpg" 
           alt="Game Banner" 
           class="rounded-xl shadow-lg w-full max-w-2xl border-4 border-gray-700">
    </div>
  </section>

  <!-- ===== Registration Form ===== -->
  <section class="max-w-3xl mx-auto bg-gray-800 p-6 rounded-xl shadow-lg mt-8">
    <h3 class="text-2xl font-bold text-center text-blue-400 mb-6">Player Registration</h3>

    <form id="registrationForm" class="grid grid-cols-1 md:grid-cols-2 gap-6">
      <input type="text" id="playerName" placeholder="Player Name" required
        class="p-3 rounded-lg bg-gray-700 text-gray-200 focus:outline-none focus:ring-2 focus:ring-blue-400">

      <input type="email" id="playerEmail" placeholder="Email" required
        class="p-3 rounded-lg bg-gray-700 text-gray-200 focus:outline-none focus:ring-2 focus:ring-blue-400">

      <input type="text" id="playerGame" placeholder="Game Name (e.g. Valorant, PUBG)" required
        class="p-3 rounded-lg bg-gray-700 text-gray-200 focus:outline-none focus:ring-2 focus:ring-blue-400">

      <input type="text" id="playerCountry" placeholder="Country" required
        class="p-3 rounded-lg bg-gray-700 text-gray-200 focus:outline-none focus:ring-2 focus:ring-blue-400">

      <button type="submit" class="col-span-2 bg-blue-600 hover:bg-blue-700 py-3 rounded-lg font-semibold transition">
        Register Player
      </button>
    </form>
  </section>

  <!-- ===== Player List ===== -->
  <section class="max-w-4xl mx-auto mt-10 p-6 bg-gray-800 rounded-xl shadow-lg">
    <h3 class="text-2xl font-bold text-center text-blue-400 mb-6">Registered Players</h3>
    <table class="w-full text-left border-collapse">
      <thead>
        <tr class="bg-gray-700 text-gray-200">
          <th class="py-2 px-3">#</th>
          <th class="py-2 px-3">Name</th>
          <th class="py-2 px-3">Email</th>
          <th class="py-2 px-3">Game</th>
          <th class="py-2 px-3">Country</th>
        </tr>
      </thead>
      <tbody id="playerTable" class="text-gray-300">
        <!-- Players will appear here -->
      </tbody>
    </table>

    <!-- ===== Show Total Button ===== -->
    <div class="text-center mt-8">
      <button id="showTotalBtn"
        class="bg-green-600 hover:bg-green-700 px-6 py-3 rounded-lg font-semibold transition">
        Show Total Registered Players
      </button>
      <p id="totalPlayers" class="text-xl font-bold text-blue-400 mt-4"></p>
    </div>
  </section>

  <!-- ===== Footer ===== -->
  <footer class="bg-gray-800 text-center py-6 mt-12">
    <p>© 2025 Rahul Gaming Tournament | All Rights Reserved 🎮</p>
  </footer>

  <!-- ===== JavaScript Logic ===== -->
  <script>
    const form = document.getElementById('registrationForm');
    const tableBody = document.getElementById('playerTable');
    const totalPlayersText = document.getElementById('totalPlayers');
    const showTotalBtn = document.getElementById('showTotalBtn');

    let players = [];

    form.addEventListener('submit', (e) => {
      e.preventDefault();

      const name = document.getElementById('playerName').value.trim();
      const email = document.getElementById('playerEmail').value.trim();
      const game = document.getElementById('playerGame').value.trim();
      const country = document.getElementById('playerCountry').value.trim();

      if (name && email && game && country) {
        const player = { name, email, game, country };
        players.push(player);
        updateTable();
        form.reset();
      }
    });

    function updateTable() {
      tableBody.innerHTML = '';
      players.forEach((p, index) => {
        const row = `
          <tr class="border-b border-gray-700 hover:bg-gray-700">
            <td class="py-2 px-3">${index + 1}</td>
            <td class="py-2 px-3">${p.name}</td>
            <td class="py-2 px-3">${p.email}</td>
            <td class="py-2 px-3">${p.game}</td>
            <td class="py-2 px-3">${p.country}</td>
          </tr>
        `;
        tableBody.insertAdjacentHTML('beforeend', row);
      });
    }

    showTotalBtn.addEventListener('click', () => {
      totalPlayersText.textContent = Total Registered Players: ${players.length};
    });
  </script>
</body>
</html>
