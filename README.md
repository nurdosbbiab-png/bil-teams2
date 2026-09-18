<!DOCTYPE html>
<html lang="ru" data-theme="blue">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>БІЛІМ-ИННОВАЦИЯ ЛИЦЕЙІ — Генератор Сбалансированных Команд</title>
    <style>
        :root {
            /* Базовые цвета бренда БИЛ */
            --bil-gold: #facc15;
            --bil-gold-hover: #fde047;
            --bil-blue: #0284c7;
            --bil-blue-light: #38bdf8;
            --bil-red: #ef4444;
            --transition-speed: 0.3s;
        }

        /* 1. ТЁМНО-СИНИЙ ФОН (ПО УМОЛЧАНИЮ) */
        [data-theme="blue"] {
            --bg-page: linear-gradient(135deg, #0f172a 0%, #1e3a8a 50%, #0f172a 100%);
            --bg-page-attachment: fixed;
            --container-bg: rgba(15, 23, 42, 0.92);
            --card-bg: rgba(30, 41, 59, 0.85);
            --card-border: rgba(250, 204, 21, 0.3);
            --text-main: #f8fafc;
            --text-muted: #94a3b8;
            --input-bg: rgba(15, 23, 42, 0.85);
            --input-border: rgba(250, 204, 21, 0.3);
            --input-text: #ffffff;
            --row-bg: rgba(30, 41, 59, 0.6);
            --row-hover: rgba(30, 41, 59, 0.9);
            --header-shadow: 0 0 20px rgba(250, 204, 21, 0.4);
            --backdrop: blur(12px);
            --badge-bg: rgba(2, 132, 199, 0.3);
            --badge-text: #38bdf8;
        }

        /* 2. БЕЛЫЙ ФОН */
        [data-theme="white"] {
            --bg-page: #f1f5f9;
            --bg-page-attachment: scroll;
            --container-bg: #ffffff;
            --card-bg: #f8fafc;
            --card-border: #cbd5e1;
            --text-main: #0f172a;
            --text-muted: #64748b;
            --input-bg: #ffffff;
            --input-border: #94a3b8;
            --input-text: #0f172a;
            --row-bg: #f1f5f9;
            --row-hover: #e2e8f0;
            --header-shadow: none;
            --backdrop: none;
            --badge-bg: #e0f2fe;
            --badge-text: #0369a1;
        }

        /* 3. ФОН С ФОТО БИЛ */
        [data-theme="photo"] {
            --bg-page: linear-gradient(rgba(15, 23, 42, 0.82), rgba(15, 23, 42, 0.9)), 
                        url('bil-bg.jpg') no-repeat center center fixed;
            --bg-page-attachment: fixed;
            --container-bg: rgba(15, 23, 42, 0.75);
            --card-bg: rgba(30, 41, 59, 0.75);
            --card-border: rgba(250, 204, 21, 0.4);
            --text-main: #ffffff;
            --text-muted: #cbd5e1;
            --input-bg: rgba(15, 23, 42, 0.85);
            --input-border: rgba(250, 204, 21, 0.35);
            --input-text: #ffffff;
            --row-bg: rgba(30, 41, 59, 0.5);
            --row-hover: rgba(30, 41, 59, 0.85);
            --header-shadow: 0 0 25px rgba(250, 204, 21, 0.5);
            --backdrop: blur(16px);
            --badge-bg: rgba(2, 132, 199, 0.4);
            --badge-text: #7dd3fc;
        }

        * {
            box-sizing: border-box;
            font-family: 'Segoe UI', system-ui, -apple-system, sans-serif;
        }

        body {
            background: var(--bg-page);
            background-size: cover;
            background-attachment: var(--bg-page-attachment);
            min-height: 100vh;
            margin: 0;
            padding: 25px 15px;
            display: flex;
            justify-content: center;
            align-items: flex-start;
            color: var(--text-main);
            transition: background var(--transition-speed) ease, color var(--transition-speed) ease;
        }

        .container {
            background: var(--container-bg);
            backdrop-filter: var(--backdrop);
            -webkit-backdrop-filter: var(--backdrop);
            padding: 35px;
            border-radius: 20px;
            box-shadow: 0 20px 50px rgba(0, 0, 0, 0.35);
            max-width: 1050px;
            width: 100%;
            border: 1px solid var(--card-border);
            transition: all var(--transition-speed) ease;
        }

        .top-bar {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 25px;
            flex-wrap: wrap;
            gap: 15px;
        }

        .theme-switcher {
            display: flex;
            background: rgba(0, 0, 0, 0.15);
            padding: 4px;
            border-radius: 12px;
            border: 1px solid var(--card-border);
            gap: 4px;
        }

        .theme-btn {
            background: transparent;
            border: none;
            color: var(--text-muted);
            padding: 8px 14px;
            border-radius: 8px;
            font-size: 13px;
            font-weight: 700;
            cursor: pointer;
            transition: all 0.2s ease;
            display: flex;
            align-items: center;
            gap: 6px;
        }

        .theme-btn.active {
            background: var(--bil-gold);
            color: #0f172a;
            box-shadow: 0 2px 8px rgba(0,0,0,0.2);
        }

        .header {
            text-align: center;
            margin-bottom: 30px;
        }

        .logo-title {
            margin: 0 0 6px 0;
            font-size: 32px;
            font-weight: 900;
            color: var(--bil-gold);
            text-shadow: var(--header-shadow);
            letter-spacing: 1px;
            text-transform: uppercase;
        }

        p.subtitle {
            margin: 0;
            color: var(--badge-text);
            font-size: 15px;
            font-weight: 600;
        }

        .section-title {
            font-size: 15px;
            font-weight: 700;
            color: var(--bil-gold);
            margin-bottom: 12px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .students-table-header {
            display: grid;
            grid-template-columns: 2.2fr 1.3fr 1fr 1fr 45px;
            gap: 10px;
            padding: 0 10px 8px 10px;
            font-size: 12px;
            font-weight: 700;
            color: var(--badge-text);
            border-bottom: 2px solid var(--card-border);
            margin-bottom: 10px;
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }

        .students-list {
            display: flex;
            flex-direction: column;
            gap: 10px;
            max-height: 400px;
            overflow-y: auto;
            padding-right: 5px;
            margin-bottom: 15px;
        }

        .students-list::-webkit-scrollbar {
            width: 6px;
        }
        .students-list::-webkit-scrollbar-track {
            background: rgba(0, 0, 0, 0.1);
            border-radius: 4px;
        }
        .students-list::-webkit-scrollbar-thumb {
            background: var(--bil-gold);
            border-radius: 4px;
        }

        .student-row {
            display: grid;
            grid-template-columns: 2.2fr 1.3fr 1fr 1fr 45px;
            gap: 10px;
            align-items: center;
            background: var(--row-bg);
            padding: 8px 10px;
            border-radius: 10px;
            border: 1px solid var(--card-border);
            transition: all 0.2s ease;
        }

        .student-row:hover {
            background: var(--row-hover);
        }

        input[type="text"], input[type="number"], select {
            width: 100%;
            padding: 10px 12px;
            border: 1px solid var(--input-border);
            border-radius: 8px;
            font-size: 14px;
            color: var(--input-text);
            background-color: var(--input-bg);
            transition: all 0.25s ease;
        }

        select option {
            background-color: #0f172a;
            color: #ffffff;
        }

        [data-theme="white"] select option {
            background-color: #ffffff;
            color: #0f172a;
        }

        input[type="text"]:focus, input[type="number"]:focus, select:focus {
            outline: none;
            border-color: var(--bil-gold);
            box-shadow: 0 0 10px rgba(250, 204, 21, 0.3);
        }

        .btn-delete-row {
            background: rgba(239, 68, 68, 0.15);
            color: var(--bil-red);
            border: 1px solid rgba(239, 68, 68, 0.4);
            border-radius: 8px;
            width: 100%;
            height: 38px;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            font-size: 16px;
            font-weight: bold;
            transition: all 0.2s ease;
        }

        .btn-delete-row:hover {
            background: var(--bil-red);
            color: #ffffff;
        }

        .toolbar-btns {
            display: flex;
            gap: 10px;
            flex-wrap: wrap;
            margin-bottom: 25px;
        }

        button {
            padding: 11px 18px;
            border: none;
            border-radius: 10px;
            font-size: 13px;
            font-weight: 700;
            cursor: pointer;
            transition: all 0.25s ease;
            text-transform: uppercase;
            letter-spacing: 0.5px;
            display: inline-flex;
            align-items: center;
            justify-content: center;
            gap: 6px;
        }

        .btn-add {
            background: rgba(250, 204, 21, 0.15);
            color: var(--text-main);
            border: 1px solid var(--bil-gold);
        }

        .btn-add:hover {
            background: var(--bil-gold);
            color: #0f172a;
        }

        .btn-example {
            background: var(--badge-bg);
            color: var(--badge-text);
            border: 1px solid var(--bil-blue-light);
        }

        .btn-example:hover {
            background: var(--bil-blue);
            color: #ffffff;
        }

        .btn-clear {
            background: rgba(148, 163, 184, 0.15);
            color: var(--text-muted);
            border: 1px solid var(--card-border);
        }

        .btn-clear:hover {
            background: rgba(148, 163, 184, 0.3);
            color: var(--text-main);
        }

        .settings-grid {
            display: grid;
            grid-template-columns: 2fr 1fr 1fr;
            gap: 15px;
            margin-bottom: 25px;
            background: var(--card-bg);
            padding: 18px;
            border-radius: 12px;
            border: 1px solid var(--card-border);
        }

        .form-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
            color: var(--bil-gold);
            font-size: 13px;
        }

        .btn-submit {
            width: 100%;
            padding: 15px;
            font-size: 16px;
            background: linear-gradient(135deg, #facc15, #eab308);
            color: #0f172a;
            box-shadow: 0 4px 15px rgba(250, 204, 21, 0.3);
        }

        .btn-submit:hover {
            transform: translateY(-2px);
            background: linear-gradient(135deg, #fde047, #facc15);
            box-shadow: 0 6px 20px rgba(250, 204, 21, 0.5);
        }

        .error-box {
            color: #f87171;
            margin-top: 20px;
            font-size: 14px;
            font-weight: 600;
            white-space: pre-line;
            background-color: rgba(239, 68, 68, 0.15);
            padding: 14px 18px;
            border-radius: 10px;
            border: 1px solid rgba(239, 68, 68, 0.4);
            display: none;
        }

        .variant-block {
            background: var(--card-bg);
            border: 1px solid var(--card-border);
            border-radius: 16px;
            padding: 24px;
            margin-top: 30px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
        }

        .variant-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-bottom: 1px solid var(--card-border);
            padding-bottom: 12px;
            margin-bottom: 20px;
            flex-wrap: wrap;
            gap: 10px;
        }

        .variant-header h2 {
            margin: 0;
            font-size: 20px;
            color: var(--bil-gold);
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .variant-stats {
            font-size: 12px;
            color: var(--badge-text);
            background: var(--badge-bg);
            padding: 6px 12px;
            border-radius: 20px;
            font-weight: 700;
            border: 1px solid var(--card-border);
        }

        .teams-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 18px;
        }

        .team-card {
            background: var(--row-bg);
            border: 1px solid var(--card-border);
            border-top: 4px solid var(--bil-gold);
            border-radius: 12px;
            padding: 16px;
            transition: transform 0.2s ease;
        }

        .team-card:hover {
            transform: translateY(-3px);
        }

        .team-header {
            border-bottom: 1px solid var(--card-border);
            padding-bottom: 10px;
            margin-bottom: 12px;
        }

        .team-title-row {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 6px;
        }

        .team-title-row h3 {
            margin: 0;
            color: var(--text-main);
            font-size: 16px;
            font-weight: 700;
        }

        .team-metrics-row {
            display: flex;
            gap: 6px;
            font-size: 11px;
            flex-wrap: wrap;
        }

        .metric-badge {
            background-color: var(--badge-bg);
            color: var(--badge-text);
            padding: 3px 8px;
            border-radius: 6px;
            font-weight: 700;
        }

        .metric-badge.yellow {
            background-color: rgba(250, 204, 21, 0.15);
            color: var(--bil-gold);
        }

        .player-list {
            list-style: none;
            padding: 0;
            margin: 0;
        }

        .player-item {
            padding: 9px 0;
            border-bottom: 1px solid rgba(148, 163, 184, 0.15);
            font-size: 13px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .player-item:last-child {
            border-bottom: none;
        }

        .player-info {
            display: flex;
            flex-direction: column;
            gap: 2px;
        }

        .player-name {
            font-weight: 600;
            color: var(--text-main);
        }

        .player-details {
            font-size: 11px;
            color: var(--text-muted);
        }

        .player-badges {
            display: flex;
            flex-direction: column;
            align-items: flex-end;
            gap: 3px;
        }

        .football-badge {
            font-weight: 800;
            color: #ffffff;
            background: linear-gradient(135deg, #0284c7, #0369a1);
            padding: 2px 7px;
            border-radius: 6px;
            font-size: 11px;
        }

        .bmi-badge-small {
            font-size: 10px;
            font-weight: 700;
            color: var(--bil-gold);
            background: rgba(250, 204, 21, 0.1);
            padding: 2px 5px;
            border-radius: 4px;
        }

        @media (max-width: 768px) {
            .students-table-header {
                display: none;
            }
            .student-row {
                grid-template-columns: 1fr;
                gap: 8px;
                position: relative;
                padding: 12px;
            }
            .btn-delete-row {
                position: absolute;
                top: 8px;
                right: 8px;
                width: 32px;
                height: 32px;
            }
            .settings-grid {
                grid-template-columns: 1fr;
            }
            .top-bar {
                justify-content: center;
            }
        }
    </style>
</head>
<body>

<div class="container">
    <div class="top-bar">
        <div style="font-size: 13px; font-weight: 700; color: var(--text-muted);">
            🎨 ТЕМА ОФОРМЛЕНИЯ:
        </div>
        <div class="theme-switcher">
            <button class="theme-btn active" onclick="setTheme('blue')" id="btn-theme-blue">
                🔵 Тёмно-синий
            </button>
            <button class="theme-btn" onclick="setTheme('white')" id="btn-theme-white">
                ⚪ Белый
            </button>
            <button class="theme-btn" onclick="setTheme('photo')" id="btn-theme-photo">
                🖼️ Фото БИЛ
            </button>
        </div>
    </div>

    <div class="header">
        <h1 class="logo-title">БІЛІМ-ИННОВАЦИЯ ЛИЦЕЙІ</h1>
        <p class="subtitle">Генератор сбалансированных команд (Футбол + ИМТ)</p>
    </div>

    <div class="section-title">
        <span>Учащиеся</span>
        <span id="studentsCountBadge" style="font-size: 12px; color: var(--badge-text); font-weight: normal;">Учеников: 0</span>
    </div>

    <div class="students-table-header">
        <div>ИМЯ УЧЕНИКА</div>
        <div>ФУТБОЛ (1-10)</div>
        <div>РОСТ (СМ)</div>
        <div>ВЕС (КГ)</div>
        <div>✕</div>
    </div>

    <div id="studentsList" class="students-list">
        <!-- Динамические строки учеников -->
    </div>

    <div class="toolbar-btns">
        <button class="btn-add" onclick="addStudentRow()">+ Добавить ученика</button>
        <button class="btn-example" onclick="fillExample()">Заполнить примером</button>
        <button class="btn-clear" onclick="clearAllStudents()">Очистить список</button>
    </div>

    <div class="settings-grid">
        <div class="form-group">
            <label for="balanceCriterion">Критерий балансировки:</label>
            <select id="balanceCriterion">
                <option value="football">⚽ По футбольному рейтингу (1-10)</option>
                <option value="bmi">⚖️ По ИМТ (Рост / Вес)</option>
                <option value="combined" selected>🔥 Комбинированный (Футбол + ИМТ)</option>
            </select>
        </div>
        <div class="form-group">
            <label for="teamsCount">Количество команд:</label>
            <input type="number" id="teamsCount" min="1" value="3">
        </div>
        <div class="form-group">
            <label for="variantsCount">Вариантов (1-10):</label>
            <input type="number" id="variantsCount" min="1" max="10" value="3">
        </div>
    </div>

    <button class="btn-submit" onclick="generateVariants()">⚡ Сгенерировать команды</button>

    <div id="error" class="error-box"></div>
    <div id="results"></div>
</div>

<script>
    // Переключение тем
    function setTheme(themeName) {
        document.documentElement.setAttribute('data-theme', themeName);
        document.querySelectorAll('.theme-btn').forEach(btn => btn.classList.remove('active'));
        const activeBtn = document.getElementById(`btn-theme-${themeName}`);
        if (activeBtn) activeBtn.classList.add('active');
    }

    function addStudentRow(name = '', rating = '', height = '', weight = '') {
        const list = document.getElementById('studentsList');
        const row = document.createElement('div');
        row.className = 'student-row';
        row.innerHTML = `
            <div>
                <input type="text" class="student-name" placeholder="Имя и фамилия" value="${name}">
            </div>
            <div>
                <input type="number" class="student-rating" placeholder="Балл 1-10" min="1" max="10" step="1" value="${rating}">
            </div>
            <div>
                <input type="number" class="student-height" placeholder="Рост (см)" min="50" max="250" value="${height}">
            </div>
            <div>
                <input type="number" class="student-weight" placeholder="Вес (кг)" min="20" max="250" value="${weight}">
            </div>
            <div>
                <button class="btn-delete-row" title="Удалить" onclick="removeStudentRow(this)">✕</button>
            </div>
        `;
        list.appendChild(row);
        updateStudentsCount();
    }

    function removeStudentRow(btn) {
        const row = btn.closest('.student-row');
        row.remove();
        updateStudentsCount();
    }

    function clearAllStudents() {
        document.getElementById('studentsList').innerHTML = '';
        addStudentRow();
    }

    function updateStudentsCount() {
        const rows = document.querySelectorAll('.student-row');
        document.getElementById('studentsCountBadge').innerText = `Учеников: ${rows.length}`;
    }

    function fillExample() {
        document.getElementById('studentsList').innerHTML = '';
        const exampleData = [
            { name: 'Арман Касымов', rating: 9, height: 185, weight: 90 },
            { name: 'Алихан Нурланов', rating: 7, height: 175, weight: 70 },
            { name: 'Мадияр Сериков', rating: 5, height: 165, weight: 52 },
            { name: 'Данияр Ахметов', rating: 10, height: 192, weight: 105 },
            { name: 'Айбек Искаков', rating: 6, height: 170, weight: 62 },
            { name: 'Сергей Попов', rating: 8, height: 180, weight: 82 },
            { name: 'Нурсултан Оспанов', rating: 4, height: 160, weight: 48 },
            { name: 'Мирас Болатов', rating: 8, height: 178, weight: 76 },
            { name: 'Санжар Ермеков', rating: 6, height: 168, weight: 58 },
            { name: 'Алдияр Муратов', rating: 9, height: 183, weight: 88 }
        ];

        exampleData.forEach(st => addStudentRow(st.name, st.rating, st.height, st.weight));
        document.getElementById('teamsCount').value = 3;
        document.getElementById('variantsCount').value = 3;
        document.getElementById('balanceCriterion').value = 'combined';
    }

    function getStudentsData() {
        const rows = document.querySelectorAll('.student-row');
        const players = [];
        const errors = [];

        rows.forEach((row, idx) => {
            const nameInput = row.querySelector('.student-name').value.trim();
            const ratingVal = parseInt(row.querySelector('.student-rating').value, 10);
            const heightVal = parseFloat(row.querySelector('.student-height').value);
            const weightVal = parseFloat(row.querySelector('.student-weight').value);

            if (!nameInput && isNaN(ratingVal) && isNaN(heightVal) && isNaN(weightVal)) {
                return;
            }

            const studentNum = idx + 1;
            const name = nameInput || `Ученик ${studentNum}`;

            if (isNaN(ratingVal) || ratingVal < 1 || ratingVal > 10) {
                errors.push(`Ученик №${studentNum} (${name}): балл в футболе должен быть от 1 до 10.`);
                return;
            }

            if (isNaN(heightVal) || heightVal < 50 || heightVal > 250) {
                errors.push(`Ученик №${studentNum} (${name}): рост от 50 до 250 см.`);
                return;
            }

            if (isNaN(weightVal) || weightVal < 20 || weightVal > 300) {
                errors.push(`Ученик №${studentNum} (${name}): вес от 20 до 300 кг.`);
                return;
            }

            const heightM = heightVal / 100;
            const bmi = weightVal / (heightM * heightM);

            players.push({
                id: idx,
                name: name,
                rating: ratingVal,
                height: heightVal,
                weight: weightVal,
                bmi: bmi
            });
        });

        return { players, errors };
    }

    function shuffle(array) {
        const arr = [...array];
        for (let i = arr.length - 1; i > 0; i--) {
            const j = Math.floor(Math.random() * (i + 1));
            [arr[i], arr[j]] = [arr[j], arr[i]];
        }
        return arr;
    }

    function evaluateTeams(teams, criterion) {
        const teamAvgRatings = teams.map(t => t.players.reduce((s, p) => s + p.rating, 0) / t.players.length);
        const teamAvgBMIs = teams.map(t => t.players.reduce((s, p) => s + p.bmi, 0) / t.players.length);

        const ratingDiff = Math.max(...teamAvgRatings) - Math.min(...teamAvgRatings);
        const bmiDiff = Math.max(...teamAvgBMIs) - Math.min(...teamAvgBMIs);

        let score = 0;
        if (criterion === 'football') {
            score = ratingDiff;
        } else if (criterion === 'bmi') {
            score = bmiDiff;
        } else {
            score = (ratingDiff / 9.0) + (bmiDiff / 15.0);
        }

        return {
            score: score,
            ratingDiff: ratingDiff,
            bmiDiff: bmiDiff,
            teamAvgRatings: teamAvgRatings,
            teamAvgBMIs: teamAvgBMIs
        };
    }

    function getVariantKey(teams) {
        return teams
            .map(t => t.players.map(p => p.name).sort().join('|'))
            .sort()
            .join('||');
    }

    function deepCopyTeams(teams) {
        return teams.map(t => ({
            id: t.id,
            maxSize: t.maxSize,
            players: [...t.players]
        }));
    }

    function generateVariants() {
        const criterion = document.getElementById('balanceCriterion').value;
        const teamsCount = parseInt(document.getElementById('teamsCount').value);
        const variantsCount = parseInt(document.getElementById('variantsCount').value);
        const errorDiv = document.getElementById('error');
        const resultsDiv = document.getElementById('results');

        errorDiv.innerText = '';
        errorDiv.style.display = 'none';
        resultsDiv.innerHTML = '';

        const { players, errors } = getStudentsData();

        if (errors.length > 0) {
            errorDiv.innerText = errors.join('\n');
            errorDiv.style.display = 'block';
            return;
        }

        if (players.length === 0) {
            errorDiv.innerText = 'Добавьте хотя бы одного ученика!';
            errorDiv.style.display = 'block';
            return;
        }

        if (isNaN(teamsCount) || teamsCount < 1) {
            errorDiv.innerText = 'Некорректное количество команд.';
            errorDiv.style.display = 'block';
            return;
        }

        if (teamsCount > players.length) {
            errorDiv.innerText = `Количество команд (${teamsCount}) больше числа учеников (${players.length}).`;
            errorDiv.style.display = 'block';
            return;
        }

        if (isNaN(variantsCount) || variantsCount < 1 || variantsCount > 10) {
            errorDiv.innerText = 'Варианты от 1 до 10.';
            errorDiv.style.display = 'block';
            return;
        }

        const N = players.length;
        const baseSize = Math.floor(N / teamsCount);
        const remainder = N % teamsCount;
        const targetSizes = Array.from({ length: teamsCount }, (_, i) => baseSize + (i < remainder ? 1 : 0));

        const candidatesMap = new Map();

        // Optimization search loop
        for (let attempt = 0; attempt < 500; attempt++) {
            let shuffled = shuffle(players);
            let teams = Array.from({ length: teamsCount }, (_, i) => ({
                id: i + 1,
                maxSize: targetSizes[i],
                players: []
            }));

            let playerIdx = 0;
            teams.forEach(t => {
                for (let i = 0; i < t.maxSize; i++) {
                    t.players.push(shuffled[playerIdx++]);
                }
            });

            let steps = Math.floor(Math.random() * 80) + 20;
            let currentEval = evaluateTeams(teams, criterion);

            for (let s = 0; s < steps; s++) {
                let t1Idx = Math.floor(Math.random() * teamsCount);
                let t2Idx = Math.floor(Math.random() * teamsCount);
                if (t1Idx === t2Idx) continue;

                let t1 = teams[t1Idx];
                let t2 = teams[t2Idx];
                if (t1.players.length === 0 || t2.players.length === 0) continue;

                let p1Idx = Math.floor(Math.random() * t1.players.length);
                let p2Idx = Math.floor(Math.random() * t2.players.length);

                let p1 = t1.players[p1Idx];
                let p2 = t2.players[p2Idx];

                t1.players[p1Idx] = p2;
                t2.players[p2Idx] = p1;

                let newEval = evaluateTeams(teams, criterion);
                if (newEval.score <= currentEval.score) {
                    currentEval = newEval;
                } else {
                    t1.players[p1Idx] = p1;
                    t2.players[p2Idx] = p2;
                }
            }

            const key = getVariantKey(teams);
            const evalResult = evaluateTeams(teams, criterion);

            if (!candidatesMap.has(key) || evalResult.score < candidatesMap.get(key).evalResult.score) {
                candidatesMap.set(key, { teams: deepCopyTeams(teams), evalResult });
            }
        }

        const sortedVariants = Array.from(candidatesMap.values()).sort((a, b) => a.evalResult.score - b.evalResult.score);
        const selectedVariants = sortedVariants.slice(0, variantsCount);

        selectedVariants.forEach((variantObj, variantIndex) => {
            const teams = variantObj.teams;
            const evalResult = variantObj.evalResult;
            
            const variantBlock = document.createElement('div');
            variantBlock.className = 'variant-block';

            let criterionBadge = '';
            if (criterion === 'football') criterionBadge = `Разница ср. балла: ${evalResult.ratingDiff.toFixed(2)}`;
            else if (criterion === 'bmi') criterionBadge = `Разница ср. ИМТ: ${evalResult.bmiDiff.toFixed(2)}`;
            else criterionBadge = `Балл разницы: ${evalResult.ratingDiff.toFixed(2)} | ИМТ разницы: ${evalResult.bmiDiff.toFixed(2)}`;

            variantBlock.innerHTML = `
                <div class="variant-header">
                    <h2>Вариант ${variantIndex + 1}</h2>
                    <span class="variant-stats">${criterionBadge}</span>
                </div>
                <div class="teams-grid">
                    ${teams.map((team, idx) => {
                        const avgRating = evalResult.teamAvgRatings[idx].toFixed(1);
                        const avgBMI = evalResult.teamAvgBMIs[idx].toFixed(1);
                        return `
                            <div class="team-card">
                                <div class="team-header">
                                    <div class="team-title-row">
                                        <h3>Команда ${team.id} (${team.players.length})</h3>
                                    </div>
                                    <div class="team-metrics-row">
                                        <span class="metric-badge yellow">⚽ Ср. балл: ${avgRating}/10</span>
                                        <span class="metric-badge">⚖️ Ср. ИМТ: ${avgBMI}</span>
                                    </div>
                                </div>
                                <ul class="player-list">
                                    ${team.players.map(p => `
                                        <li class="player-item">
                                            <div class="player-info">
                                                <span class="player-name">${p.name}</span>
                                                <span class="player-details">${p.height} см / ${p.weight} кг</span>
                                            </div>
                                            <div class="player-badges">
                                                <span class="football-badge">⚽ ${p.rating}/10</span>
                                                <span class="bmi-badge-small">ИМТ ${p.bmi.toFixed(1)}</span>
                                            </div>
                                        </li>
                                    `).join('')}
                                </ul>
                            </div>
                        `;
                    }).join('')}
                </div>
            `;

            resultsDiv.appendChild(variantBlock);
        });
    }

    window.onload = function() {
        fillExample();
    };
</script>

</body>
</html>
