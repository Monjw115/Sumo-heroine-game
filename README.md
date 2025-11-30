# Sumo-heroine-game
<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8" />
  <title>스모부 육성 프로젝트 - 메인 메뉴</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <style>
    :root {
      --bg: #060716;
      --bg-soft: #101322;
      --bg-softer: #171a2a;
      --accent: #ff6b9c;
      --accent-soft: #ff9fbd;
      --text: #f7f7ff;
      --muted: #9496b8;
      --border: #2a2d45;
      --btn-bg: #1e2235;
      --btn-bg-hover: #292d45;
    }

    * {
      box-sizing: border-box;
    }

    body {
      margin: 0;
      font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI",
        sans-serif;
      background: radial-gradient(circle at top, #1e2240 0, #060716 55%);
      color: var(--text);
    }

    #app {
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      align-items: center;
      padding: 16px;
    }

    .main-header {
      text-align: center;
      margin-bottom: 16px;
    }

    .main-header h1 {
      margin: 8px 0;
      font-size: 1.8rem;
      letter-spacing: 0.08em;
    }

    .subtitle {
      margin: 0;
      font-size: 0.9rem;
      color: var(--muted);
    }

    .badge-row {
      margin-top: 8px;
      display: flex;
      justify-content: center;
      gap: 8px;
      flex-wrap: wrap;
      font-size: 0.75rem;
    }

    .badge {
      padding: 2px 8px;
      border-radius: 999px;
      border: 1px solid var(--border);
      background: rgba(255, 255, 255, 0.03);
      color: var(--muted);
    }

    .main-menu {
      width: 100%;
      max-width: 1080px;
      display: grid;
      grid-template-columns: minmax(0, 260px) minmax(0, 1.2fr) minmax(0, 1fr);
      gap: 16px;
    }

    @media (max-width: 900px) {
      .main-menu {
        grid-template-columns: minmax(0, 1fr);
      }
    }

    .card {
      background: linear-gradient(135deg, #101322aa, #181b2aee);
      border-radius: 14px;
      border: 1px solid var(--border);
      box-shadow: 0 0 40px rgba(0, 0, 0, 0.45);
      padding: 12px 14px;
    }

    .card h2 {
      margin: 0 0 8px;
      font-size: 1rem;
      display: flex;
      align-items: center;
      justify-content: space-between;
    }

    .card h2 span.right {
      font-size: 0.75rem;
      color: var(--muted);
      font-weight: 400;
    }

    /* 메뉴 버튼들 */

    .menu-buttons {
      display: flex;
      flex-direction: column;
      gap: 8px;
    }

    .menu-buttons button {
      width: 100%;
      padding: 10px 12px;
      border-radius: 10px;
      border: 1px solid var(--border);
      background: var(--btn-bg);
      color: var(--text);
      font-size: 0.95rem;
      cursor: pointer;
      text-align: left;
      display: flex;
      justify-content: space-between;
      align-items: center;
      transition: background 0.15s ease, transform 0.1s ease,
        border-color 0.15s ease;
    }

    .menu-buttons button:hover {
      background: var(--btn-bg-hover);
      border-color: var(--accent-soft);
      transform: translateY(-1px);
    }

    .menu-buttons button.primary {
      background: linear-gradient(135deg, #ff6b9c, #ff8fb2);
      border-color: #ff9fbd;
      color: #1a1020;
      font-weight: 600;
    }

    .menu-buttons button.primary:hover {
      background: linear-gradient(135deg, #ff7aa7, #ffadca);
      transform: translateY(-1px);
    }

    .menu-buttons button.secondary {
      border-style: dashed;
    }

    .menu-buttons button[disabled] {
      opacity: 0.45;
      cursor: not-allowed;
      border-style: dotted;
    }

    .menu-buttons small {
      font-size: 0.7rem;
      color: var(--muted);
    }

    /* 히로인 리스트 */

    .heroine-list {
      margin: 0;
      padding: 0;
      list-style: none;
      display: flex;
      flex-direction: column;
      gap: 6px;
      max-height: 260px;
      overflow-y: auto;
    }

    .heroine-item {
      border-radius: 8px;
      border: 1px solid var(--border);
      padding: 6px 8px;
      background: rgba(10, 12, 24, 0.85);
      display: flex;
      justify-content: space-between;
      align-items: center;
      cursor: pointer;
      transition: background 0.15s ease, border-color 0.15s ease,
        transform 0.1s ease;
    }

    .heroine-item:hover {
      background: rgba(20, 24, 46, 0.95);
      border-color: var(--accent-soft);
      transform: translateY(-1px);
    }

    .heroine-item.active {
      border-color: var(--accent);
      background: radial-gradient(
        circle at left,
        rgba(255, 107, 156, 0.16),
        rgba(17, 19, 36, 0.98)
      );
    }

    .heroine-name {
      font-size: 0.9rem;
    }

    .heroine-meta {
      font-size: 0.75rem;
      color: var(--muted);
    }

    .heroine-detail {
      margin-top: 10px;
      border-radius: 10px;
      border: 1px solid var(--border);
      padding: 8px 10px;
      background: rgba(6, 8, 20, 0.9);
      min-height: 110px;
      font-size: 0.85rem;
    }

    .heroine-detail-row {
      display: flex;
      justify-content: space-between;
      margin-bottom: 4px;
    }

    .heroine-detail-row span.label {
      color: var(--muted);
    }

    .heroine-detail-row span.value {
      font-weight: 500;
    }

    .heroine-tags {
      margin-top: 4px;
      display: flex;
      flex-wrap: wrap;
      gap: 4px;
      font-size: 0.7rem;
    }

    .heroine-tag {
      padding: 2px 6px;
      border-radius: 999px;
      border: 1px solid var(--border);
      color: var(--muted);
    }

    .heroine-desc {
      margin-top: 6px;
      font-size: 0.8rem;
      color: var(--muted);
      line-height: 1.4;
    }

    /* 로그 패널 */

    .log-panel-body {
      font-size: 0.78rem;
      max-height: 260px;
      overflow-y: auto;
      border-radius: 8px;
      border: 1px solid var(--border);
      background: rgba(4, 5, 16, 0.9);
      padding: 6px 8px;
    }

    .log-line {
      margin-bottom: 4px;
      color: var(--muted);
    }

    .log-line strong {
      color: var(--accent-soft);
    }
  </style>
</head>
<body>
  <div id="app">
    <header class="main-header">
      <h1>스모부 육성 프로젝트</h1>
      <p class="subtitle">텍스트 기반 스모부 육성 시뮬레이션 (프로토타입)</p>
      <div class="badge-row">
        <span class="badge">Ver 0.1.0 Prototype</span>
        <span class="badge">JS / HTML만으로 동작</span>
        <span class="badge">주인공: 동갑 고등학생 매니저</span>
      </div>
    </header>

    <main class="main-menu">
      <!-- 왼쪽: 메인 메뉴 버튼 -->
      <section class="card">
        <h2>메인 메뉴 <span class="right">Game Menu</span></h2>
        <div class="menu-buttons">
          <button class="primary" data-action="start">
            <span>새 게임 시작</span>
            <span>▶</span>
          </button>
          <button class="secondary" data-action="continue" disabled>
            <span>이어하기 (준비 중)</span>
            <span>…</span>
          </button>
          <button data-action="settings" disabled>
            <span>설정 (준비 중)</span>
            <span>⚙</span>
          </button>
          <button data-action="gallery" disabled>
            <span>갤러리 / CG (준비 중)</span>
            <span>★</span>
          </button>
          <button data-action="about">
            <span>세계관 / 조작 설명</span>
            <span>?</span>
          </button>
          <small>※ 지금은 메인 메뉴 / 히로인 DB 보기만 구현된 프로토타입입니다.</small>
        </div>
      </section>

      <!-- 가운데: 히로인 리스트 + 상세 -->
      <section class="card">
        <h2>히로인 목록 <span class="right">Heroine Database (샘플)</span></h2>
        <ul class="heroine-list" id="heroine-list"></ul>
        <div class="heroine-detail" id="heroine-detail">
          히로인을 선택하면 상세 정보가 여기에 표시됩니다.
        </div>
      </section>

      <!-- 오른쪽: 로그 -->
      <section class="card">
        <h2>시스템 로그 <span class="right">System Log</span></h2>
        <div class="log-panel-body" id="log-output"></div>
      </section>
    </main>
  </div>

  <script>
    // ===============================
    // 1. 히로인 DB (간단 버전)
    // ===============================
    // 이후에 heroineDB.json으로 분리해도 되지만,
    // 지금은 index.html 안에 모두 넣어서 한 번에 관리
    const heroineDB = [
      {
        id: "nagisa",
        name: "나기사",
        club: "스모부",
        heightCm: 170,
        startWeightKg: 70,
        maxWeightKg: 220,
        archetype: "Muscular Power",
        note: "전통 스모 가문 출신. 부담과 즐거움 사이에서 자신의 스모를 찾는 에이스.",
      },
      {
        id: "yuzuru",
        name: "유즈루",
        club: "축구부",
        heightCm: 160,
        startWeightKg: 52,
        maxWeightKg: 170,
        archetype: "Speed Star",
        note: "전국구 스프린터급 스피드. 괴롭힘 트라우마를 딛고 스피드 스모를 개척.",
      },
      {
        id: "misaki",
        name: "미사키",
        club: "체조부",
        heightCm: 158,
        startWeightKg: 48,
        maxWeightKg: 165,
        archetype: "Perfect Technician",
        note: "완벽주의 + 체중 강박. 체형 변화를 받아들이며 기술 스모의 정점을 향해 간다.",
      },
      {
        id: "hinata",
        name: "히나타",
        club: "육상부",
        heightCm: 162,
        startWeightKg: 50,
        maxWeightKg: 169,
        archetype: "Sunshine Sprinter",
        note: "밝고 모험심 강한 스프린터. 과한 폭주를 조절하며 균형 잡힌 스모 천재로 성장.",
      },
      {
        id: "koharu",
        name: "코하루",
        club: "배드민턴부",
        heightCm: 168,
        startWeightKg: 60,
        maxWeightKg: 175,
        archetype: "Balanced Ace",
        note: "교과서적인 만능형 에이스. ‘가짜 천재’ 의혹을 스스로의 경기로 부정해 나간다.",
      },
      {
        id: "akane",
        name: "아카네",
        club: "유도부",
        heightCm: 165,
        startWeightKg: 58,
        maxWeightKg: 172,
        archetype: "Soft Judo Power",
        note: "유도 베이스의 부드러운 힘. ‘위협적’이라는 편견을 넘어 전략적인 스모를 완성.",
      },
      {
        id: "kaede",
        name: "카에데",
        club: "역도부",
        heightCm: 172,
        startWeightKg: 65,
        maxWeightKg: 210,
        archetype: "Heavy Lifter",
        note: "압도적인 힘을 가진 역도 소녀. 도핑 의혹을 넘어 근육 미학을 증명해 나간다.",
      },
    ];

    // BMI 계산 유틸
    function calcBMI(heightCm, weightKg) {
      const h = heightCm / 100;
      return weightKg / (h * h);
    }

    // 로그 출력 유틸
    const logEl = document.getElementById("log-output");
    function addLog(message, type = "info") {
      const line = document.createElement("div");
      line.className = "log-line";
      const time = new Date().toLocaleTimeString("ko-KR", {
        hour12: false,
      });
      if (type === "system") {
        line.innerHTML = `<strong>[${time}]</strong> ${message}`;
      } else {
        line.textContent = `[${time}] ${message}`;
      }
      logEl.prepend(line); // 최근 로그 위로 쌓이게
    }

    // ===============================
    // 2. 히로인 리스트 렌더링
    // ===============================
    const heroineListEl = document.getElementById("heroine-list");
    const heroineDetailEl = document.getElementById("heroine-detail");
    let currentHeroineId = null;

    function renderHeroineList() {
      heroineListEl.innerHTML = "";
      heroineDB.forEach((h) => {
        const li = document.createElement("li");
        li.className = "heroine-item";
        li.dataset.id = h.id;

        const left = document.createElement("div");
        left.innerHTML = `
          <div class="heroine-name">${h.name}</div>
          <div class="heroine-meta">${h.club} · ${h.heightCm}cm</div>
        `;

        const right = document.createElement("div");
        right.className = "heroine-meta";
        const startBMI = calcBMI(h.heightCm, h.startWeightKg).toFixed(1);
        const maxBMI = calcBMI(h.heightCm, h.maxWeightKg).toFixed(1);
        right.textContent = `시작 ${h.startWeightKg}kg (BMI ${startBMI}) → 최대 ${h.maxWeightKg}kg (BMI ${maxBMI})`;

        li.appendChild(left);
        li.appendChild(right);

        li.addEventListener("click", () => {
          selectHeroine(h.id);
        });

        heroineListEl.appendChild(li);
      });
    }

    function selectHeroine(id) {
      currentHeroineId = id;
      // 활성화 표시
      document.querySelectorAll(".heroine-item").forEach((item) => {
        item.classList.toggle("active", item.dataset.id === id);
      });

      const h = heroineDB.find((x) => x.id === id);
      if (!h) return;

      const startBMI = calcBMI(h.heightCm, h.startWeightKg).toFixed(1);
      const maxBMI = calcBMI(h.heightCm, h.maxWeightKg).toFixed(1);

      heroineDetailEl.innerHTML = `
        <div class="heroine-detail-row">
          <span class="label">이름</span>
          <span class="value">${h.name}</span>
        </div>
        <div class="heroine-detail-row">
          <span class="label">운동부 / 포지션</span>
          <span class="value">${h.club} · ${h.archetype}</span>
        </div>
        <div class="heroine-detail-row">
          <span class="label">키</span>
          <span class="value">${h.heightCm}cm</span>
        </div>
        <div class="heroine-detail-row">
          <span class="label">시작 체중 / BMI</span>
          <span class="value">${h.startWeightKg}kg / ${startBMI}</span>
        </div>
        <div class="heroine-detail-row">
          <span class="label">이론상 최대 체중 / BMI</span>
          <span class="value">${h.maxWeightKg}kg / ${maxBMI}</span>
        </div>
        <div class="heroine-tags">
          <span class="heroine-tag">스토리: ${h.archetype}</span>
          <span class="heroine-tag">개별 루트: D 루트 예정</span>
          <span class="heroine-tag">대회 C 루트 연동</span>
        </div>
        <div class="heroine-desc">
          ${h.note}
        </div>
      `;

      addLog(`히로인 [${h.name}] 상세를 열었습니다.`, "system");
    }

    // ===============================
    // 3. 메뉴 버튼 처리
    // ===============================
    const menuButtons = document.querySelectorAll(".menu-buttons button");

    menuButtons.forEach((btn) => {
      btn.addEventListener("click", () => {
        const action = btn.dataset.action;
        switch (action) {
          case "start":
            onStartGame();
            break;
          case "about":
            onShowAbout();
            break;
          default:
            addLog(`아직 준비되지 않은 메뉴입니다: ${action}`);
        }
      });
    });

    function onStartGame() {
      if (!currentHeroineId) {
        addLog("※ 히로인을 한 명 선택하면, 해당 히로인 기준으로 테스트 시작 가능 (앞으로 구현 예정).");
      }
      addLog(
        "새 게임 시작: 아직은 메인 메뉴 / DB만 있는 프로토타입입니다. 이후 A/B/C/D 루트, 전투·식사·체형 로직이 여기서 시작됩니다.",
        "system"
      );
      alert(
        "지금은 프로토타입입니다.\n\n메인 메뉴와 히로인 DB까지만 구현되어 있고,\n실제 육성/전투 루프는 이후에 JS로 추가하게 될 거야!"
      );
    }

    function onShowAbout() {
      const msg = [
        "◆ 스모부 육성 프로젝트 (프로토타입)",
        "",
        "- 플레이어는 스모부를 맡은 동갑 고등학생 매니저.",
        "- 3년(33개월) 동안 7명의 히로인을 전국 체전 우승급 선수로 육성.",
        "- A 루트: 일상/육성, B 루트: 히로인×히로인 관계,",
        "  C 루트: 대회 전후 이벤트, D 루트: 각 히로인 엔딩.",
        "",
        "지금 화면은:",
        "- 메인 메뉴(향후 세이브/갤러리 추가 예정)",
        "- 히로인 7명 DB(기본 신상/체형 정보)입니다.",
      ].join("\n");
      alert(msg);
      addLog("세계관 / 조작 설명을 열었습니다.", "system");
    }

    // ===============================
    // 4. 초기화
    // ===============================
    window.addEventListener("DOMContentLoaded", () => {
      renderHeroineList();
      addLog("게임이 초기화되었습니다. 히로인 목록에서 한 명 선택해보세요.", "system");
    });
  </script>
</body>
</html>
