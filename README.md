<!DOCTYPE html>
<html lang="zh-TW">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>航用字母圖版</title>

<style>
body {
    font-family: Arial;
    background: #f5f5f5;
    padding: 20px;
}

.grid {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 15px;
}

.item {
    display: flex;
    align-items: center;
    background: white;
    padding: 10px;
    border-radius: 8px;
    cursor: pointer;
    transition: 0.2s;
}

.item:hover {
    background: #e0f0ff;
}

.letter {
    background: black;
    color: white;
    font-size: 28px;
    width: 40px;
    height: 40px;
    display: flex;
    align-items: center;
    justify-content: center;
    margin-right: 10px;
}

.word {
    font-size: 20px;
}
</style>
</head>

<body>

<h2>✈️ 航用字母（點擊播放）</h2>

<div class="grid" id="grid"></div>

<script>
const data = [
["A","Alfa"],["B","Bravo"],["C","Charlie"],["D","Delta"],
["E","Echo"],["F","Foxtrot"],["G","Golf"],["H","Hotel"],
["I","India"],["J","Juliet"],["K","Kilo"],["L","Lima"],
["M","Mike"],["N","November"],["O","Oscar"],["P","Papa"],
["Q","Quebec"],["R","Romeo"],["S","Sierra"],["T","Tango"],
["U","Uniform"],["V","Victor"],["W","Whiskey"],["X","Xray"],
["Y","Yankee"],["Z","Zulu"]
];

const grid = document.getElementById("grid");

data.forEach(item => {
    const div = document.createElement("div");
    div.className = "item";
    div.onclick = () => speak(item[1]);

    div.innerHTML = `
        <div class="letter">${item[0]}</div>
        <div class="word">${item[1]}</div>
    `;

    grid.appendChild(div);
});

function speak(text){
    const u = new SpeechSynthesisUtterance(text);
    u.lang = "en-US";
    speechSynthesis.speak(u);
}
</script>

</body>
</html>
