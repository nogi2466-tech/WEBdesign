<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8">
  <title>My Website</title>
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <style>
    body {
      font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
      margin: 0;
      padding: 0;
      background: #f5f5f5;
      color: #333;
    }
    header {
      background: #1e88e5;
      color: #fff;
      padding: 16px 24px;
    }
    header h1 {
      margin: 0;
      font-size: 24px;
    }
    nav {
      background: #1565c0;
      padding: 8px 24px;
    }
    nav a {
      color: #fff;
      text-decoration: none;
      margin-right: 16px;
      font-size: 14px;
    }
    main {
      max-width: 960px;
      margin: 24px auto;
      padding: 0 16px 40px;
      background: #fff;
      box-shadow: 0 2px 6px rgba(0,0,0,0.08);
      border-radius: 8px;
    }
    section {
      padding: 24px 20px;
      border-bottom: 1px solid #eee;
    }
    section:last-of-type {
      border-bottom: none;
    }
    h2 {
      margin-top: 0;
      font-size: 20px;
      border-left: 4px solid #1e88e5;
      padding-left: 8px;
    }
    footer {
      text-align: center;
      font-size: 12px;
      color: #777;
      padding: 16px 0 24px;
    }
    .btn {
      display: inline-block;
      padding: 8px 16px;
      background: #1e88e5;
      color: #fff;
      text-decoration: none;
      border-radius: 4px;
      font-size: 14px;
    }
    .btn:hover {
      background: #1565c0;
    }
  </style>
</head>
<body>
  <header>
    <h1>聖介のサイト</h1>
  </header>

  <nav>
    <a href="#about">プロフィール</a>
    <a href="#works">作品・実績</a>
    <a href="#contact">お問い合わせ</a>
  </nav>

  <main>
    <section id="about">
      <h2>プロフィール</h2>
      <p>
        ここに自己紹介を書きます。<br>
        例）東京都在住の聖介です。WEB制作やプログラミング、デザインに興味があります。
      </p>
    </section>

    <section id="works">
      <h2>作品・実績</h2>
      <ul>
        <li>作品A：説明をここに書く</li>
        <li>作品B：説明をここに書く</li>
        <li>作品C：説明をここに書く</li>
      </ul>
      <a href="#" class="btn">もっと見る</a>
    </section>

    <section id="contact">
      <h2>お問い合わせ</h2>
      <p>ご連絡は以下のフォームからどうぞ。（ダミー）</p>
      <form>
        <div>
          <label>お名前：</label><br>
          <input type="text" name="name" style="width: 100%; max-width: 320px;">
        </div>
        <div style="margin-top: 8px;">
          <label>メールアドレス：</label><br>
          <input type="email" name="email" style="width: 100%; max-width: 320px;">
        </div>
        <div style="margin-top: 8px;">
          <label>メッセージ：</label><br>
          <textarea name="message" rows="4" style="width: 100%; max-width: 480px;"></textarea>
        </div>
        <div style="margin-top: 12px;">
          <button type="submit" class="btn">送信</button>
        </div>
      </form>
    </section>
  </main>

  <footer>
    &copy; 2026 聖介
  </footer>
</body>
</html>

