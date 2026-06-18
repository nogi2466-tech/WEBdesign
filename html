<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8">
  <title>hayabee</title>
  <meta name="viewport" content="width=device-width, initial-scale=1">

  <style>
    body {
      margin: 0;
      font-family: "Segoe UI", sans-serif;
      background: #fafafa;
      color: #333;
    }

    /* メニュー */
    nav {
      background: #1565c0;
      padding: 10px;
      text-align: center;
    }
    nav a {
      color: #fff;
      margin: 0 12px;
      text-decoration: none;
      font-size: 16px;
      cursor: pointer;
    }

    /* ページ切り替え */
    .page {
      display: none;
      max-width: 900px;
      margin: 30px auto;
      padding: 0 20px;
    }
    .active {
      display: block;
    }

    h2 {
      border-left: 4px solid #1e88e5;
      padding-left: 10px;
    }

    /* カレンダー */
    table {
      width: 100%;
      border-collapse: collapse;
    }
    th, td {
      border: 1px solid #ccc;
      padding: 8px;
      text-align: center;
      height: 60px;
    }
    td:hover {
      background: #e3f2fd;
      cursor: pointer;
    }

    /* スマホ用 */
    @media (max-width: 600px) {
      th, td {
        height: 40px;
        font-size: 12px;
      }
    }

    /* 画像一覧 */
    .thumb {
      width: 120px;
      margin: 10px;
      display: block;
    }
    .imgBox {
      display: inline-block;
      margin: 10px;
      border: 1px solid #ccc;
      padding: 10px;
      position: relative;
    }
    .delBtn {
      position: absolute;
      top: -8px;
      right: -8px;
      background: red;
      color: #fff;
      border: none;
      border-radius: 50%;
      width: 24px;
      height: 24px;
      cursor: pointer;
    }
  </style>
</head>

<body>

<nav>
  <a onclick="showPage('home')">ホーム</a>
  <a onclick="showPage('calendar')">カレンダー</a>
  <a onclick="showPage('gallery')">画像</a>
</nav>

<!-- ホーム -->
<div id="home" class="page active">
  <h2>ホーム</h2>
  <p>ようこそ、hayabeeのサイトへ。</p>
</div>

<!-- カレンダー -->
<div id="calendar" class="page">
  <h2>カレンダー</h2>

  <div style="display:flex; justify-content:space-between; align-items:center; margin-bottom:10px;">
    <button onclick="prevMonth()">＜ 前の月</button>
    <h3 id="monthTitle"></h3>
    <button onclick="nextMonth()">次の月 ＞</button>
  </div>

  <table id="calendarTable"></table>
</div>

<!-- 画像ページ -->
<div id="gallery" class="page">
  <h2>画像</h2>

  <p>選択した日付：<span id="selectedDate">なし</span></p>

  <input type="date" id="imgDate"><br><br>
  <input type="file" id="imgFile" accept="image/*"><br><br>
  <button onclick="addImage()">画像を追加</button>

  <h3>画像一覧</h3>
  <div id="imgList"></div>
</div>

<script>
  /* -------------------------
     ページ切り替え
  ------------------------- */
  function showPage(pageId) {
    document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
    document.getElementById(pageId).classList.add('active');
  }

  /* -------------------------
     カレンダー機能
  ------------------------- */
  let currentYear = 2025;
  let currentMonth = 1; // 2月

  let schedules = {}; // 予定
  let images = [];    // 画像

  function renderCalendar() {
    const monthTitle = document.getElementById("monthTitle");
    const table = document.getElementById("calendarTable");

    const monthNames = ["1月","2月","3月","4月","5月","6月","7月","8月","9月","10月","11月","12月"];
    monthTitle.textContent = `${currentYear}年 ${monthNames[currentMonth]}`;

    const firstDay = new Date(currentYear, currentMonth, 1).getDay();
    const lastDate = new Date(currentYear, currentMonth + 1, 0).getDate();

    let html = "<tr><th>日</th><th>月</th><th>火</th><th>水</th><th>木</th><th>金</th><th>土</th></tr><tr>";

    for (let i = 0; i < firstDay; i++) html += "<td></td>";

    for (let date = 1; date <= lastDate; date++) {
      if ((firstDay + date - 1) % 7 === 0 && date !== 1) html += "</tr><tr>";

      const key = `${currentYear}-${currentMonth+1}-${date}`;
      const note = schedules[key] ? `<br><small>${schedules[key]}</small>` : "";

      html += `<td onclick="selectDate(${date})">${date}${note}</td>`;
    }

    html += "</tr>";
    table.innerHTML = html;
  }

  function prevMonth() {
    currentMonth--;
    if (currentMonth < 0) {
      currentMonth = 11;
      currentYear--;
    }
    renderCalendar();
  }

  function nextMonth() {
    currentMonth++;
    if (currentMonth > 11) {
      currentMonth = 0;
      currentYear++;
    }
    renderCalendar();
  }

  /* -------------------------
     日付クリック → 画像ページへ
  ------------------------- */
  function selectDate(date) {
    const key = `${currentYear}-${String(currentMonth+1).padStart(2,'0')}-${String(date).padStart(2,'0')}`;

    document.getElementById("selectedDate").textContent = key;
    document.getElementById("imgDate").value = key;

    showPage("gallery");
  }

  /* -------------------------
     画像追加
  ------------------------- */
  function addImage() {
    const date = document.getElementById("imgDate").value;
    const file = document.getElementById("imgFile").files[0];

    if (!date || !file) {
      alert("日付と画像を選んでください");
      return;
    }

    const reader = new FileReader();
    reader.onload = function(e) {
      images.push({ date: date, src: e.target.result });
      schedules[date] = "画像あり";
      displayImages();
      renderCalendar();
    };
    reader.readAsDataURL(file);
  }

  /* -------------------------
     画像表示＋削除
  ------------------------- */
  function displayImages() {
    const list = document.getElementById("imgList");
    list.innerHTML = "";

    images.forEach((img, index) => {
      list.innerHTML += `
        <div class="imgBox">
          <button class="delBtn" onclick="deleteImage(${index})">×</button>
          <p>${img.date}</p>
          <img src="${img.src}" class="thumb">
        </div>
      `;
    });
  }

  function deleteImage(index) {
    const date = images[index].date;

    images.splice(index, 1);

    if (!images.some(i => i.date === date)) {
      delete schedules[date];
    }

    displayImages();
    renderCalendar();
  }

  renderCalendar();
</script>

</body>
</html>

