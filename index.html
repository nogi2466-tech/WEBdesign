<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>紫句守鉄道 運行状況 管理コントロールパネル（PC用）</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Firebase SDK (Compat) -->
    <script src="https://www.gstatic.com/firebasejs/9.23.0/firebase-app-compat.js"></script>
    <script src="https://www.gstatic.com/firebasejs/9.23.0/firebase-database-compat.js"></script>
    <style>
        body { font-family: system-ui, -apple-system, sans-serif; }
    </style>
</head>
<body class="bg-slate-950 text-slate-100 min-h-screen flex flex-col">

    <!-- ヘッダー -->
    <header class="bg-slate-900 border-b border-slate-800 p-4 shadow-lg flex justify-between items-center px-8">
        <div class="flex items-center space-x-3">
            <span class="text-3xl">🎛️</span>
            <div>
                <h1 class="text-xl font-bold tracking-wider text-indigo-200">紫句守鉄道 <span class="text-xs font-normal text-indigo-400">運行管理コントロールパネル</span></h1>
                <p class="text-xs text-slate-400">司令所・運行管理者専用PCコンソール</p>
            </div>
        </div>
        <div class="flex items-center space-x-4">
            <div id="live-datetime" class="bg-slate-950 px-3 py-1.5 rounded-lg border border-slate-800 text-xs font-mono text-indigo-300">
                2026/10/12(月) 00:00:00
            </div>
            <div class="flex items-center space-x-2 bg-slate-950 px-3 py-1.5 rounded-lg border border-slate-800 text-xs">
                <span id="sync-status-dot" class="w-2.5 h-2.5 rounded-full bg-amber-500 animate-pulse"></span>
                <span id="sync-status-text">同期待機中</span>
            </div>
        </div>
    </header>

    <!-- メインコンテンツ -->
    <main class="flex-1 p-8 max-w-7xl mx-auto w-full space-y-6">

        <!-- アラート・通知エリア -->
        <div id="alert-banner" class="hidden p-4 rounded-xl border flex items-center justify-between shadow-lg">
            <div class="flex items-center space-x-3">
                <span id="alert-icon" class="text-2xl">⚠️</span>
                <div>
                    <h3 id="alert-title-text" class="font-bold text-sm">運行障害発生中</h3>
                    <p id="alert-desc-text" class="text-xs opacity-90">現在、一部の路線でダイヤの乱れが発生しています。</p>
                </div>
            </div>
            <span class="text-xs font-mono bg-black/30 px-3 py-1 rounded">システム連動中</span>
        </div>

        <div class="grid grid-cols-1 lg:grid-cols-3 gap-6">

            <!-- 左側：全線一括ステータス変更 -->
            <div class="bg-slate-900 p-6 rounded-2xl border border-slate-800 shadow-xl space-y-5 lg:col-span-1">
                <h2 class="text-lg font-bold text-indigo-200 border-b border-slate-800 pb-3 flex items-center gap-2">
                    <span>⚡</span> 全線一括ステータス変更
                </h2>
                <p class="text-xs text-slate-400">すべての路線または主要路線に一斉に遅延・運休情報を適用します。</p>

                <div class="space-y-4 text-sm">
                    <div>
                        <label class="block text-xs text-slate-400 mb-1">運行状況ステータス</label>
                        <select id="global-status-select" class="w-full bg-slate-950 border border-slate-800 rounded-lg px-3 py-2.5 text-white font-medium focus:border-indigo-500 outline-none">
                            <option value="normal">🟢 全線正常運転中</option>
                            <option value="delay">🟡 一部遅延・ダイヤ乱れ</option>
                            <option value="suspended">🔴 運転見合わせ（全線・一部）</option>
                            <option value="event">🎉 イベントダイヤ運行中</option>
                        </select>
                    </div>

                    <div>
                        <label class="block text-xs text-slate-400 mb-1">詳細メッセージ（運行情報テロップ用）</label>
                        <textarea id="global-status-message" rows="3" class="w-full bg-slate-950 border border-slate-800 rounded-lg p-3 text-xs text-white focus:border-indigo-500 outline-none" placeholder="例: 〇〇駅での車両点検の影響により、上下線に最大15分の遅れが出ています。"></textarea>
                    </div>

                    <button onclick="updateGlobalStatus()" class="w-full bg-indigo-600 hover:bg-indigo-500 text-white font-bold py-2.5 rounded-lg transition shadow text-sm">
                        ステータスを即時反映する
                    </button>
                </div>
            </div>

            <!-- 右側：個別列車・路線の運行状態微調整 -->
            <div class="bg-slate-900 p-6 rounded-2xl border border-slate-800 shadow-xl space-y-5 lg:col-span-2">
                <h2 class="text-lg font-bold text-indigo-200 border-b border-slate-800 pb-3 flex items-center gap-2">
                    <span>🚆</span> 路線別・個別列車 運行状態管理
                </h2>
                <p class="text-xs text-slate-400">特定の列車や路線を選択して、個別に遅延時間や運行状態を操作できます。</p>

                <div class="overflow-x-auto max-h-[420px] rounded-xl border border-slate-800">
                    <table class="w-full text-left text-xs">
                        <thead class="bg-slate-950 text-indigo-300 sticky top-0 border-b border-slate-800">
                            <tr>
                                <th class="p-3">列車番号</th>
                                <th class="p-3">種別・行き先</th>
                                <th class="p-3">運用番号</th>
                                <th class="p-3">現在の状態</th>
                                <th class="p-3 text-right">操作</th>
                            </tr>
                        </thead>
                        <tbody id="admin-train-list" class="divide-y divide-slate-800 text-slate-300">
                            <!-- 動的読み込み -->
                        </tbody>
                    </table>
                </div>
            </div>

        </div>

    </main>

    <!-- 個別列車ステータス変更モーダル -->
    <div id="train-edit-modal" class="fixed inset-0 bg-slate-950/80 z-50 flex items-center justify-center hidden backdrop-blur-sm">
        <div class="bg-slate-900 border border-indigo-700 p-6 rounded-2xl w-full max-w-md space-y-4 shadow-2xl">
            <div class="flex justify-between items-center border-b border-slate-800 pb-3">
                <h3 id="modal-title" class="font-bold text-indigo-200 text-sm">列車運行状態の変更</h3>
                <button onclick="closeModal()" class="text-slate-400 hover:text-white text-lg font-bold bg-slate-950 w-7 h-7 rounded-full flex items-center justify-center border border-slate-800">×</button>
            </div>
            <input type="hidden" id="edit-train-id">
            <div class="space-y-3 text-xs">
                <div>
                    <label class="block text-slate-400 mb-1">状態ステータス</label>
                    <select id="modal-train-status" class="w-full bg-slate-950 border border-slate-800 rounded px-3 py-2 text-white">
                        <option value="走行中">走行中（正常）</option>
                        <option value="遅延運転中">遅延運転中</option>
                        <option value="停車中">停車中</option>
                        <option value="運転見合わせ">運転見合わせ</option>
                    </select>
                </div>
                <div>
                    <label class="block text-slate-400 mb-1">遅延分数（分）</label>
                    <input type="number" id="modal-train-delay" class="w-full bg-slate-950 border border-slate-800 rounded px-3 py-2 text-white" value="0" min="0" max="120">
                </div>
            </div>
            <div class="flex justify-end gap-2 pt-2">
                <button onclick="closeModal()" class="bg-slate-800 hover:bg-slate-700 text-slate-300 px-4 py-2 rounded text-xs transition">キャンセル</button>
                <button onclick="saveTrainStatus()" class="bg-indigo-600 hover:bg-indigo-500 text-white px-4 py-2 rounded text-xs font-bold transition shadow">変更を保存</button>
            </div>
        </div>
    </div>

    <script>
        let appData = {
            trains: [],
            globalStatus: {
                status: "normal",
                message: "全線平常通り運行しています。"
            }
        };
        let dbRef = null;
        const DEFAULT_FB_URL = "https://original-tetsudo-430ac-default-rtdb.firebaseio.com";

        function initFirebase() {
            try {
                if(firebase.apps.length === 0) {
                    firebase.initializeApp({ databaseURL: DEFAULT_FB_URL });
                }
                dbRef = firebase.database().ref('shinomori_railway_master');
                dbRef.on('value', (snapshot) => {
                    const val = snapshot.val();
                    if(val) {
                        appData = val;
                        if(!appData.globalStatus) {
                            appData.globalStatus = { status: "normal", message: "全線平常通り運行しています。" };
                        }
                        updateUI();
                    }
                });
                document.getElementById('sync-status-dot').className = "w-2.5 h-2.5 rounded-full bg-emerald-500 animate-pulse";
                document.getElementById('sync-status-text').innerText = "リアルタイム同期中";
            } catch(e) {
                document.getElementById('sync-status-dot').className = "w-2.5 h-2.5 rounded-full bg-red-500";
                document.getElementById('sync-status-text').innerText = "同期エラー";
            }
        }

        function pushData() {
            if(dbRef) dbRef.set(appData);
        }

        function updateUI() {
            // グローバルステータスの反映
            const gs = appData.globalStatus || { status: "normal", message: "" };
            document.getElementById('global-status-select').value = gs.status;
            document.getElementById('global-status-message').value = gs.message || "";

            const banner = document.getElementById('alert-banner');
            const titleEl = document.getElementById('alert-title-text');
            const descEl = document.getElementById('alert-desc-text');
            const iconEl = document.getElementById('alert-icon');

            if(gs.status === 'normal') {
                banner.className = "p-4 rounded-xl border flex items-center justify-between shadow-lg bg-emerald-950/40 border-emerald-800 text-emerald-200";
                iconEl.innerText = "🟢";
                titleEl.innerText = "全線正常運転中";
                descEl.innerText = gs.message || "現在、ダイヤの乱れはありません。";
            } else if(gs.status === 'delay') {
                banner.className = "p-4 rounded-xl border flex items-center justify-between shadow-lg bg-amber-950/40 border-amber-800 text-amber-200";
                iconEl.innerText = "🟡";
                titleEl.innerText = "一部遅延発生中";
                descEl.innerText = gs.message || "ダイヤに乱れが生じています。";
            } else if(gs.status === 'suspended') {
                banner.className = "p-4 rounded-xl border flex items-center justify-between shadow-lg bg-rose-950/40 border-rose-800 text-rose-200";
                iconEl.innerText = "🔴";
                titleEl.innerText = "運転見合わせ中";
                descEl.innerText = gs.message || "運転を見合わせている区間があります。";
            } else {
                banner.className = "p-4 rounded-xl border flex items-center justify-between shadow-lg bg-indigo-950/40 border-indigo-800 text-indigo-200";
                iconEl.innerText = "🎉";
                titleEl.innerText = "イベント日ダイヤ運行";
                descEl.innerText = gs.message || "特別ダイヤで運行中です。";
            }
            banner.classList.remove('hidden');

            // 列車リストの描画
            const tbody = document.getElementById('admin-train-list');
            const trains = appData.trains || [];
            if(trains.length === 0) {
                tbody.innerHTML = `<tr><td colspan="5" class="p-4 text-center text-slate-500">登録されている列車がありません。</td></tr>`;
                return;
            }

            tbody.innerHTML = trains.map(t => {
                let badgeClass = "bg-emerald-950 text-emerald-300 border border-emerald-800";
                if(t.status === "遅延運転中") badgeClass = "bg-amber-950 text-amber-300 border border-amber-800";
                if(t.status === "運転見合わせ") badgeClass = "bg-rose-950 text-rose-300 border border-rose-800";

                return `
                    <tr class="hover:bg-slate-950/50 transition">
                        <td class="p-3 font-bold text-indigo-300 font-mono text-sm">${t.trainNum}</td>
                        <td class="p-3">
                            <span class="px-1.5 py-0.5 rounded bg-slate-800 text-slate-200 mr-1">${t.type}</span>
                            <span class="text-slate-300">${t.endSt}行</span>
                        </td>
                        <td class="p-3 font-mono text-sky-300">${t.opNum || '-'}</td>
                        <td class="p-3"><span class="px-2 py-0.5 rounded text-[10px] font-bold ${badgeClass}">${t.status || '走行中'}</span></td>
                        <td class="p-3 text-right">
                            <button onclick="openEditModal(${t.id})" class="bg-indigo-600 hover:bg-indigo-500 text-white px-3 py-1 rounded text-xs transition">変更</button>
                        </td>
                    </tr>
                `;
            }).join('');
        }

        function updateGlobalStatus() {
            const status = document.getElementById('global-status-select').value;
            const message = document.getElementById('global-status-message').value;
            appData.globalStatus = { status, message };
            pushData();
            alert("全線ステータスを更新し、利用システムに同期しました！");
        }

        function openEditModal(trainId) {
            const train = (appData.trains || []).find(t => t.id === trainId);
            if(!train) return;
            document.getElementById('edit-train-id').value = train.id;
            document.getElementById('modal-train-status').value = train.status || '走行中';
            document.getElementById('modal-title').innerText = `列車番号: ${train.trainNum} の運行状態変更`;
            document.getElementById('train-edit-modal').classList.remove('hidden');
        }

        function closeModal() {
            document.getElementById('train-edit-modal').classList.add('hidden');
        }

        function saveTrainStatus() {
            const id = Number(document.getElementById('edit-train-id').value);
            const status = document.getElementById('modal-train-status').value;
            
            const train = (appData.trains || []).find(t => t.id === id);
            if(train) {
                train.status = status;
                pushData();
                closeModal();
                updateUI();
            }
        }

        function updateLiveDateTime() {
            const now = new Date();
            const yyyy = now.getFullYear();
            const mm = String(now.getMonth() + 1).padStart(2, '0');
            const dd = String(now.getDate()).padStart(2, '0');
            const days = ['日', '月', '火', '水', '木', '金', '土'];
            const dayOfWeek = days[now.getDay()];
            const hours = String(now.getHours()).padStart(2, '0');
            const minutes = String(now.getMinutes()).padStart(2, '0');
            const seconds = String(now.getSeconds()).padStart(2, '0');
            const el = document.getElementById('live-datetime');
            if(el) el.innerText = `${yyyy}/${mm}/${dd}(${dayOfWeek}) ${hours}:${minutes}:${seconds}`;
        }

        window.onload = function() {
            initFirebase();
            setInterval(updateLiveDateTime, 1000);
            updateLiveDateTime();
        };
    </script>
</body>
</html>
