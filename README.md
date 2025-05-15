
# tic-tac-toe
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  
  <title>Tic-Tac-Toe</title>
  <style>
        
  body {
      text-align: center;
      font-family: cursive;
      margin: 0;
      padding: 20px;
      background: #c8edf7;
      
    }
    

    h1 {
      font-size: 2rem;
      margin-bottom: 10px;
      
    }

    .board {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 5px;
      max-width: 300px;
      margin: 0 auto 20px;
    }

    .cell {
      aspect-ratio: 1;
      width: 100%;
      font-size: 2.5rem;
      background: #fff;
      border: 2px solid #ffffdf;
      display: flex;
      justify-content: center;
      align-items: center;
      cursor: pointer;
      user-select: none;
      transition: background 0.2s;
    }

    .cell.taken {
      pointer-events: none;
      background: #fcdce1;
    }

    button {
      padding: 10px 20px ;
      font-size: 1rem;
      background-color: #e8bbbe;
      color: white;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      
    }

    button:hover {
      background-color: #f9fobc;
     
    }

    #status {
      margin-bottom: 10px;
      font-size: 1.2rem;
    }
    
   .link {
       color: purple;
       }
       
    .container { 
        margin-top: 10px;
    }
    .board {
        color: black;
        font-family: fantasy;
    }
   h2 {
       color: ;
       font-family: fantasy;
       border: dotted 1px;
       padding: 10px;
   }
   
  </style>
</head>
<body>
    <h1>Game Developed by Dhanu</h1>
  <h2>Tic-Tac-Toe</h2>
  <p id="status">Player X's turn</p>
  <div class="board" id="board"></div>
  <button onclick="resetGame()">Restart</button>
   
   <div class="container">
  <a class="link" 


href="https://www.instagram.com/_moon_light_79?igsh=ZTl2Z3VmeGozOTJv">Follow me on Instagram.</a>
</div>
  
      
  
  
    <script>
    const board = document.getElementById('board');
    const statusText = document.getElementById('status');
    let currentPlayer = 'X';
    let cells = Array(9).fill('');

    function createBoard() {
      board.innerHTML = '';
      cells.forEach((_, i) => {
        const cell = document.createElement('div');
        cell.classList.add('cell');
        cell.dataset.index = i;
        cell.addEventListener('click', handleClick);
        board.appendChild(cell);
      });
      statusText.textContent = "Player X's turn";
    }

    function handleClick(e) {
      const index = e.target.dataset.index;
      if (cells[index]) return;
      cells[index] = currentPlayer;
      e.target.textContent = currentPlayer;
      e.target.classList.add('taken');

      if (checkWin()) {
        statusText.textContent = `Player ${currentPlayer} wins!`;
        endGame();
      } else if (!cells.includes('')) {
        statusText.textContent = "It's a draw!";
        endGame();
      } else {
        currentPlayer = currentPlayer === 'X' ? 'O' : 'X';
        statusText.textContent = `Player ${currentPlayer}'s turn`;
      }
    }

    function checkWin() {
      const winPatterns = [
        [0,1,2], [3,4,5], [6,7,8],
        [0,3,6], [1,4,7], [2,5,8],
        [0,4,8], [2,4,6]
      ];
      return winPatterns.some(pattern =>
        pattern.every(i => cells[i] === currentPlayer)
      );
    }

    function endGame() {
      document.querySelectorAll('.cell').forEach(cell =>
        cell.classList.add('taken')
      );
    }

    function resetGame() {
      cells = Array(9).fill('');
      currentPlayer = 'X';
      createBoard();
    }

    createBoard();
  </script>
</body>
</html>