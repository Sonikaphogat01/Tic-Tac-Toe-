<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tic Tac Toe</title>
    <link rel="stylesheet" href="style.css">
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Finger+Paint&display=swap" rel="stylesheet"> 
</head>
<body>
    <div class="container">
        <h1 id="playerText">Tic Tac Toe</h1>
        <button id="restartBtn">Restart</button>

        <div id="gameboard">
            <div class="box" id="0"></div>
            <div class="box" id="1"></div>
            <div class="box" id="2"></div>
            <div class="box" id="3"></div>
            <div class="box" id="4"></div>
            <div class="box" id="5"></div>
            <div class="box" id="6"></div>
            <div class="box" id="7"></div>
            <div class="box" id="8"></div>
        </div>
    </div>

    <script src="/game_logic.js"></script>
</body>
</html>
{
    padding: 0;
    margin: 0;
    box-sizing: border-box;
}

:root {
    --orange: #F2C14E;
    --winning-blocks: #2d414b;
}

body {
    color: var(--orange);
    font-family: 'Finger Paint', cursive;
}
h1 {
    font-size: 54px;
    text-transform: uppercase;
}

.container {
    padding: 40px;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    background-color: #37505C;
}

#gameboard {
    width: 300px;
    display: flex;
    flex-wrap: wrap;
    margin-top: 40px;
}
.box {
    height: 100px;
    width: 100px;
    display: flex;
    align-items: center;
    justify-content: center;
    color: var(--orange);
    font-size: 120px;
    border-right: 2px solid;
    border-bottom: 2px solid;
}
.box:nth-child(3n) {
    border-right: none;
}
.box:nth-child(6) ~ .box {
    border-bottom: none;
} 
button {
    padding: 10px 20px;
    border-radius: 10px;
    background-color: var(--orange);
    color: #333;
    border-color: var(--orange);
    font-size: 18px;
    transition: 200ms transform;
    font-weight: 600;
}
button:hover {
    cursor: pointer;
    transform: translateY(-2px);
}
let playerText = document.getElementById('playerText')
let restartBtn = document.getElementById('restartBtn')
let boxes = Array.from(document.getElementsByClassName('box'))

let winnerIndicator = getComputedStyle(document.body).getPropertyValue('--winning-blocks')

const O_TEXT = "O"
const X_TEXT = "X"
let currentPlayer = X_TEXT
let spaces = Array(9).fill(null)

const startGame = () => {
    boxes.forEach(box => box.addEventListener('click', boxClicked))
}

function boxClicked(e) {
    const id = e.target.id

    if(!spaces[id]){
        spaces[id] = currentPlayer
        e.target.innerText = currentPlayer

        if(playerHasWon() !==false){
            playerText.innerHTML = `${currentPlayer} has won!`
            let winning_blocks = playerHasWon()

            winning_blocks.map( box => boxes[box].style.backgroundColor=winnerIndicator)
            return
        }

        currentPlayer = currentPlayer == X_TEXT ? O_TEXT : X_TEXT
    }
}

const winningCombos = [
    [0,1,2],
    [3,4,5],
    [6,7,8],
    [0,3,6],
    [1,4,7],
    [2,5,8],
    [0,4,8],
    [2,4,6]
]

function playerHasWon() {
    for (const condition of winningCombos) {
        let [a, b, c] = condition

        if(spaces[a] && (spaces[a] == spaces[b] && spaces[a] == spaces[c])) {
            return [a,b,c]
        }
    }
    return false
}

restartBtn.addEventListener('click', restart)

function restart() {
    spaces.fill(null)

    boxes.forEach( box => {
        box.innerText = ''
        box.style.backgroundColor=''
    })

    playerText.innerHTML = 'Tic Tac Toe'

    currentPlayer = X_TEXT
}

startGame()