<!DOCTYPE html>  
<html lang="tr">  
<head>  
<meta charset="UTF-8">  
<title>Doğum Günü Daveti 🎉</title>  
  
<style>  
body {  
    margin: 0;  
    height: 100vh;  
    background: linear-gradient(135deg, #ff9a9e, #fad0c4);  
    display: flex;  
    justify-content: center;  
    align-items: center;  
    font-family: 'Comic Sans MS', 'Poppins', sans-serif;  
    color: #fff;  
}  
  
/* Ziyaretçi sayacı */  
.counter {  
    position: fixed;  
    top: 15px;  
    left: 15px;  
    background: rgba(0,0,0,0.4);  
    padding: 10px 15px;  
    border-radius: 12px;  
    font-size: 0.9rem;  
}  
  
.card {  
    background: rgba(0, 0, 0, 0.25);  
    padding: 40px 50px;  
    border-radius: 25px;  
    box-shadow: 0 10px 30px rgba(0,0,0,0.3);  
    text-align: center;  
    max-width: 500px;  
    width: 90%;  
}  
  
h1 {  
    font-size: 2.6rem;  
    margin-bottom: 25px;  
}  
  
.countdown {  
    display: grid;  
    grid-template-columns: repeat(3, 1fr);  
    gap: 15px;  
    margin-bottom: 30px;  
}  
  
.box {  
    background: rgba(255,255,255,0.2);  
    padding: 15px;  
    border-radius: 15px;  
}  
  
.number {  
    font-size: 1.8rem;  
    font-weight: bold;  
    display: block;  
}  
  
.full {  
    grid-column: span 3;  
}  
  
/* Butonlar */  
.buttons {  
    display: flex;  
    gap: 20px;  
    justify-content: center;  
    margin-bottom: 20px;  
}  
  
button {  
    padding: 12px 25px;  
    font-size: 1.1rem;  
    border: none;  
    border-radius: 20px;  
    cursor: pointer;  
    transition: 0.3s;  
}  
  
.yes {  
    background: #4CAF50;  
    color: white;  
}  
  
.no {  
    background: #f44336;  
    color: white;  
}  
  
button:hover {  
    transform: scale(1.08);  
    opacity: 0.9;  
}  
  
.result {  
    font-size: 1.2rem;  
    margin-bottom: 25px;  
}  
  
/* Adres */  
.address {  
    font-size: 1rem;  
    opacity: 0.9;  
    border-top: 1px dashed rgba(255,255,255,0.4);  
    padding-top: 15px;  
}  
</style>  
</head>  
  
<body>  
  
<div class="counter">  
    👀 Ziyaretçi: <span id="visitCount">0</span>  
</div>  
  
<div class="card">  
    <h1>🎉 Doğum günüme gelir misin? 🎂</h1>  
  
    <div class="countdown">  
        <div class="box">Ay<span class="number" id="months">0</span></div>  
        <div class="box">Gün<span class="number" id="days">0</span></div>  
        <div class="box">Saat<span class="number" id="hours">0</span></div>  
        <div class="box">Dakika<span class="number" id="minutes">0</span></div>  
        <div class="box full">Saniye<span class="number" id="seconds">0</span></div>  
    </div>  
  
    <div class="buttons">  
        <button class="yes" onclick="answer('yes')">🎉 Geliyorum</button>  
        <button class="no" onclick="answer('no')">😢 Gelemiyorum</button>  
    </div>  
  
    <div class="result" id="result"></div>  
  
    <div class="address">  
        📍 Adres: <strong>Edirne Keşan Macera Parkı</strong>  
    </div>  
</div>  
  
<script>  
/* 🔢 Ziyaretçi Sayacı */  
let visits = localStorage.getItem("visits");  
if (!visits) visits = 0;  
visits++;  
localStorage.setItem("visits", visits);  
document.getElementById("visitCount").innerText = visits;  
  
/* ⏳ Geri Sayım */  
const targetDate = new Date("February 25, 2026 19:30:00").getTime();  
  
function updateCountdown() {  
    const now = new Date().getTime();  
    let distance = targetDate - now;  
  
    if (distance < 0) {  
        document.querySelector(".card").innerHTML = "<h1>🎉 İyi ki doğdun! 🎂</h1>";  
        return;  
    }  
  
    const monthMs = 30 * 24 * 60 * 60 * 1000;  
  
    const months = Math.floor(distance / monthMs);  
    distance %= monthMs;  
  
    const days = Math.floor(distance / (1000 * 60 * 60 * 24));  
    const hours = Math.floor((distance / (1000 * 60 * 60)) % 24);  
    const minutes = Math.floor((distance / (1000 * 60)) % 60);  
    const seconds = Math.floor((distance / 1000) % 60);  
  
    monthsEl.innerText = months;  
    daysEl.innerText = days;  
    hoursEl.innerText = hours;  
    minutesEl.innerText = minutes;  
    secondsEl.innerText = seconds;  
}  
  
const monthsEl = document.getElementById("months");  
const daysEl = document.getElementById("days");  
const hoursEl = document.getElementById("hours");  
const minutesEl = document.getElementById("minutes");  
const secondsEl = document.getElementById("seconds");  
  
updateCountdown();  
setInterval(updateCountdown, 1000);  
  
/* ✅ ❌ Buton Cevapları */  
function answer(type) {  
    const result = document.getElementById("result");  
    if (type === "yes") {  
        result.innerHTML = "🥳 Harika! Seni bekliyorum 🎂🎉";  
    } else {  
        result.innerHTML = "😔 Canın sağ olsun, başka zaman kutlarız 💙";  
    }  
}  
</script>  
  
</body>  
</html>  
