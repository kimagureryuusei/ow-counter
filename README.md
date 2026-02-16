<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>OWアンチピック検索</title>

<style>
body {
    font-family: Arial, sans-serif;
    background: #1e1e2f;
    color: white;
    text-align: center;
    padding: 40px;
}
.container {
    background: #2c2c3f;
    padding: 30px;
    border-radius: 15px;
    max-width: 400px;
    margin: auto;
}
select {
    padding: 10px;
    font-size: 16px;
    margin-top: 15px;
}
.result {
    margin-top: 20px;
    font-size: 18px;
}
</style>
</head>

<body>

<div class="container">
<h2>Overwatch アンチピック検索</h2>

<select id="enemyHero" onchange="showCounter()">
    <option value="">敵ヒーローを選択</option>
</select>

<div class="result" id="result"></div>
</div>

<script>

// 🔥 ここだけ触ればOK
const counters = {
    "ファラ": {
        picks: "ソルジャー76, キャスディ",
        reason: "空中に強いヒーローが有効"
    },
    "ウィンストン": {
        picks: "リーパー, バスティオン",
        reason: "タンク削り性能が高い"
    },
    "ゲンジ": {
        picks: "メイ, モイラ",
        reason: "機動力を止めやすい"
    },
    "ラインハルト": {
        picks: "バスティオン, ジャンクラット",
        reason: "シールド破壊が速い"
    }
};

// 🔥 自動で選択肢を作る
const select = document.getElementById("enemyHero");

Object.keys(counters).forEach(hero => {
    const option = document.createElement("option");
    option.value = hero;
    option.textContent = hero;
    select.appendChild(option);
});

function showCounter() {
    const hero = select.value;

    if (!hero) {
        document.getElementById("result").innerHTML = "";
        return;
    }

    const result = counters[hero];

    document.getElementById("result").innerHTML =
        "<b>おすすめアンチ:</b><br>" + result.picks +
        "<br><br><b>理由:</b><br>" + result.reason;
}

</script>

</body>
</html>
