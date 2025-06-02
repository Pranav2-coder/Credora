<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Advanced Tic Tac Toe</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@600&display=swap" rel="stylesheet">
  <style>
    body {
      font-family: 'Orbitron', sans-serif;
    }
  </style>
</head>

<body class="bg-gradient-to-br from-indigo-900 via-purple-800 to-pink-700 min-h-screen flex items-center justify-center">
  <div class="bg-white/10 backdrop-blur-md p-6 rounded-2xl shadow-2xl w-[90vw] max-w-md text-white text-center">
    <h1 class="text-3xl md:text-4xl font-bold mb-4">Tic Tac Toe</h1>
    <div id="gameBoard" class="grid grid-cols-3 gap-2 p-4 bg-white/10 rounded-xl">
      <!-- Game cells will be inserted here -->
    </div>
    <p id="gameStatus" class="text-lg mt-4 font-semibold"></p>
    <button id="resetBtn" class="mt-6 px-6 py-2 bg-white text-purple-700 font-bold rounded-xl hover:bg-gray-200 transition">Restart Game</button>
  </div>

  <script>
    const board = Array(9).fill(null);
    let currentPlayer = 'X';
    let gameActive = true;

    const gameBoard = document.getElementById('gameBoard');
    const gameStatus = document.getElementById('gameStatus');
    const resetBtn = document.getElementById('resetBtn');

    function renderBoard() {
      gameBoard.innerHTML = '';
      board.forEach((cell, index) => {
        const cellBtn = document.createElement('button');
        cellBtn.className = `aspect-square w-full h-[80px] sm:h-[100px] text-3xl font-black rounded-lg transition duration-300 flex items-center justify-center ${cell ? 'bg-white text-purple-800 cursor-not-allowed' : 'bg-purple-500 hover:bg-purple-400'}`;
        cellBtn.textContent = cell || '';
        cellBtn.disabled = !!cell || !gameActive;
        cellBtn.onclick = () => makeMove(index);
        gameBoard.appendChild(cellBtn);
      });
    }

    function makeMove(index) {
      if (!gameActive || board[index]) return;
      board[index] = currentPlayer;
      if (checkWinner()) {
        gameStatus.textContent = `Player ${currentPlayer} wins! 🎉`;
        gameActive = false;
      } else if (board.every(cell => cell)) {
        gameStatus.textContent = "It's a draw! 🤝";
        gameActive = false;
      } else {
        currentPlayer = currentPlayer === 'X' ? 'O' : 'X';
        gameStatus.textContent = `Player ${currentPlayer}'s turn`;
      }
      renderBoard();
    }

    function checkWinner() {
      const winningCombos = [
        [0, 1, 2], [3, 4, 5], [6, 7, 8],
        [0, 3, 6], [1, 4, 7], [2, 5, 8],
        [0, 4, 8], [2, 4, 6]
      ];
      return winningCombos.some(([a, b, c]) =>
        board[a] && board[a] === board[b] && board[a] === board[c]
      );
    }

    resetBtn.onclick = () => {
      board.fill(null);
      currentPlayer = 'X';
      gameActive = true;
      gameStatus.textContent = "Player X's turn";
      renderBoard();
    };

    // Initialize game
    renderBoard();
    gameStatus.textContent = "Player X's turn";
  </script>
</body>

</html>
