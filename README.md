<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<title>حروف مع أحمد</title>

<style>
body {
  margin: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background: #f3f4f6;
  font-family: "Tahoma", Arial;
}

/* العنوان */
.title {
  position: absolute;
  top: 20px;
  right: 30px;
  font-size: 24px;
  font-weight: bold;
  color: #333;
}

/* الإطار الخارجي */
.frame {
  padding: 30px;
  border-radius: 30px;
  background:
    linear-gradient(to right, orange 10%, transparent 10%, transparent 90%, orange 90%),
    linear-gradient(to bottom, green 10%, transparent 10%, transparent 90%, green 90%);
}

/* الحاوية */
.container {
  background: white;
  padding: 25px;
  border-radius: 20px;
  box-shadow: 0 10px 25px rgba(0,0,0,0.1);
}

/* الشبكة */
.grid {
  display: grid;
  grid-template-columns: repeat(5, 80px);
  gap: 10px;
}

/* إزاحة الصفوف */
.row-offset {
  margin-right: 45px;
}

/* الشكل السداسي */
.hex {
  width: 80px;
  height: 90px;
  clip-path: polygon(
    50% 0%,
    100% 25%,
    100% 75%,
    50% 100%,
    0% 75%,
    0% 25%
  );
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 22px;
  font-weight: bold;
  border: 2px solid #ddd;
  cursor: pointer;
  transition: 0.2s;
}

.hex:hover {
  transform: scale(1.05);
}

/* الألوان */
.hex.white { background: white; color: purple; }
.hex.yellow { background: gold; color: black; }
.hex.green { background: #4CAF50; color: white; }
.hex.orange { background: orange; color: white; }

</style>
</head>

<body>

<div class="title">حروف مع أحمد</div>

<div class="frame">
  <div class="container">

    <!-- صف 1 -->
    <div class="grid">
      <div class="hex">ا</div>
      <div class="hex">ب</div>
      <div class="hex">ت</div>
      <div class="hex">ث</div>
      <div class="hex">ج</div>
    </div>

    <!-- صف 2 -->
    <div class="grid row-offset">
      <div class="hex">ح</div>
      <div class="hex">خ</div>
      <div class="hex">د</div>
      <div class="hex">ذ</div>
      <div class="hex">ر</div>
    </div>

    <!-- صف 3 -->
    <div class="grid">
      <div class="hex">ز</div>
      <div class="hex">س</div>
      <div class="hex">ش</div>
      <div class="hex">ص</div>
      <div class="hex">ض</div>
    </div>

    <!-- صف 4 -->
    <div class="grid row-offset">
      <div class="hex">ط</div>
      <div class="hex">ظ</div>
      <div class="hex">ع</div>
      <div class="hex">غ</div>
      <div class="hex">ف</div>
    </div>

    <!-- صف 5 -->
    <div class="grid">
      <div class="hex">ق</div>
      <div class="hex">ك</div>
      <div class="hex">ل</div>
      <div class="hex">م</div>
      <div class="hex">ن</div>
    </div>

  </div>
</div>

<script>
const colors = ["white", "yellow", "green", "orange"];

document.querySelectorAll(".hex").forEach(hex => {
  let index = 0;

  hex.classList.add(colors[index]);

  hex.addEventListener("click", () => {
    hex.classList.remove(colors[index]);
    index = (index + 1) % colors.length;
    hex.classList.add(colors[index]);
  });
});
</script>

</body>
</html>
