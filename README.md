<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>حروف مع أحمد</title>

  <style>
    * {
      box-sizing: border-box;
    }

    body {
      margin: 0;
      min-height: 100vh;
      background: #ececec;
      font-family: "Tahoma", "Arial", sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      padding: 30px;
    }

    .page {
      width: min(1200px, 95vw);
      position: relative;
    }

    .title {
      text-align: right;
      font-size: 30px;
      font-weight: 700;
      color: #2f2f2f;
      margin-bottom: 14px;
      padding-right: 10px;
    }

    .frame {
      background:
        linear-gradient(to right,
          #f5a300 0%,
          #f5a300 10%,
          #0a9400 10%,
          #0a9400 90%,
          #f5a300 90%,
          #f5a300 100%);
      padding: 18px;
      border-radius: 34px;
      box-shadow: 0 10px 25px rgba(0, 0, 0, 0.12);
    }

    .container {
      background: #fdfdfd;
      border-radius: 26px;
      padding: 34px 30px 40px;
      min-height: 680px;
      position: relative;
      overflow: hidden;
    }

    .board {
      width: fit-content;
      margin: 0 auto;
      display: flex;
      flex-direction: column;
      gap: 8px;
      direction: ltr; /* مهم حتى لا تنقلب الصفوف بصريًا */
    }

    .row {
      display: flex;
      justify-content: center;
      gap: 10px;
    }

    .row.offset {
      margin-left: 45px;
    }

    .hex {
      width: 86px;
      height: 96px;
      clip-path: polygon(
        50% 0%,
        100% 25%,
        100% 75%,
        50% 100%,
        0% 75%,
        0% 25%
      );
      background: #ffffff;
      border: 2px solid #d7d7d7;
      display: flex;
      justify-content: center;
      align-items: center;
      font-size: 22px;
      font-weight: 700;
      color: purple;
      cursor: pointer;
      user-select: none;
      transition: transform 0.18s ease, box-shadow 0.18s ease;
      box-shadow: 0 4px 10px rgba(0, 0, 0, 0.06);
    }

    .hex:hover {
      transform: translateY(-2px);
      box-shadow: 0 8px 16px rgba(0, 0, 0, 0.10);
    }

    .hex.white  { background: #ffffff; color: purple; }
    .hex.yellow { background: #f3c623; color: #222; border-color: #e0b100; }
    .hex.green  { background: #38a169; color: #fff; border-color: #2f855a; }
    .hex.orange { background: #f59e0b; color: #fff; border-color: #d97706; }

    @media (max-width: 900px) {
      .container {
        min-height: auto;
        padding: 24px 16px 30px;
      }

      .hex {
        width: 68px;
        height: 78px;
        font-size: 19px;
      }

      .row {
        gap: 8px;
      }

      .row.offset {
        margin-left: 36px;
      }

      .title {
        font-size: 24px;
      }
    }

    @media (max-width: 600px) {
      .hex {
        width: 54px;
        height: 62px;
        font-size: 16px;
      }

      .row.offset {
        margin-left: 28px;
      }

      .frame {
        padding: 12px;
      }

      .container {
        border-radius: 20px;
      }
    }
  </style>
</head>
<body>

  <div class="page">
    <div class="title">حروف مع أحمد</div>

    <div class="frame">
      <div class="container">
        <div class="board" id="board"></div>
      </div>
    </div>
  </div>

  <script>
    const letters = [
      "م","ا","ق","س","هـ",
      "ة","ط","ع","و","ل",
      "ف","ن","ص","د","ي",
      "ر","ب","ت","ث","ج",
      "ح","خ","ذ","ز","ش"
    ];

    function shuffle(array) {
      const arr = [...array];
      for (let i = arr.length - 1; i > 0; i--) {
        const j = Math.floor(Math.random() * (i + 1));
        [arr[i], arr[j]] = [arr[j], arr[i]];
      }
      return arr;
    }

    const shuffled = shuffle(letters);

    const rows = [
      shuffled.slice(0, 5),
      shuffled.slice(5, 10),
      shuffled.slice(10, 15),
      shuffled.slice(15, 20),
      shuffled.slice(20, 25)
    ];

    const board = document.getElementById("board");

    rows.forEach((rowLetters, rowIndex) => {
      const row = document.createElement("div");
      row.className = rowIndex % 2 === 1 ? "row offset" : "row";

      rowLetters.forEach(letter => {
        const hex = document.createElement("div");
        hex.className = "hex white";
        hex.textContent = letter;

        const colors = ["white", "yellow", "green", "orange"];
        let index = 0;

        hex.addEventListener("click", () => {
          hex.classList.remove(colors[index]);
          index = (index + 1) % colors.length;
          hex.classList.add(colors[index]);
        });

        row.appendChild(hex);
      });

      board.appendChild(row);
    });
  </script>

</body>
</html>
