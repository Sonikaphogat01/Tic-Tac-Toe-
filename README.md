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