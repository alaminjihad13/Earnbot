<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Earn Master</title>
<style>
@import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@500&family=Raleway:wght@400;600&display=swap');

* { box-sizing:border-box; margin:0; padding:0; font-family:'Raleway', sans-serif; }

body {
    height:100vh;
    display:flex;
    justify-content:center;
    align-items:center;
    background: linear-gradient(135deg, #0f0c29, #302b63, #24243e);
    background-size: 400% 400%;
    animation: gradientBG 15s ease infinite;
    color:#fff;
}

@keyframes gradientBG{
    0%{background-position:0% 50%;}
    50%{background-position:100% 50%;}
    100%{background-position:0% 50%;}
}

.container {
    background: rgba(20,20,20,0.85);
    padding:30px;
    border-radius:20px;
    width:360px;
    box-shadow:0 10px 30px rgba(0,0,0,0.7);
    text-align:center;
}

h1 {
    font-family:'Orbitron', sans-serif;
    font-size:28px;
    color:#00ffcc;
    margin-bottom:15px;
}

.developer {
    display:inline-block;
    padding:8px 15px;
    border-radius:10px;
    text-decoration:none;
    font-weight:600;
    color:#fff;
    background: linear-gradient(90deg,#ff5f6d,#ffc371);
    transition:0.3s;
    margin-bottom:20px;
}
.developer:hover{
    background: linear-gradient(90deg,#ffc371,#ff5f6d);
}

/* Stats */
.stats p{
    font-size:15px;
    margin:6px 0;
}

/* Progress Circle */
.progress-circle {
    width:100px;
    height:100px;
    border-radius:50%;
    background: conic-gradient(#00ffcc 0%, #00ffcc 0%, rgba(0,255,204,0.1) 100%);
    margin:15px auto;
    display:flex;
    align-items:center;
    justify-content:center;
    font-weight:bold;
    font-size:18px;
    color:#00ffcc;
}

/* Buttons */
.buttons button {
    width:95%;
    padding:12px;
    margin:8px 0;
    border:none;
    border-radius:12px;
    font-size:16px;
    font-weight:600;
    cursor:pointer;
    color:#fff;
    background: linear-gradient(45deg,#ff512f,#dd2476);
    transition:0.3s;
}
.buttons button:hover{
    background: linear-gradient(45deg,#dd2476,#ff512f);
}

/* Withdraw Section */
.withdraw-section{
    margin-top:20px;
    display:none;
    background: rgba(30,30,30,0.9);
    padding:20px;
    border-radius:15px;
}
.withdraw-section input, .withdraw-section select{
    width:100%;
    padding:12px;
    margin:8px 0;
    border-radius:10px;
    border:none;
    background:#111;
    color:#fff;
}
.withdraw-section button{
    width:100%;
    padding:12px;
    margin-top:10px;
    font-weight:bold;
    font-size:16px;
    border:none;
    border-radius:12px;
    background: linear-gradient(45deg,#1FA2FF,#12D8FA,#A6FFCB);
    color:#111;
    cursor:pointer;
    transition:0.3s;
}
.withdraw-section button:hover{
    background: linear-gradient(45deg,#A6FFCB,#12D8FA,#1FA2FF);
}
#withdraw-status{
    margin-top:10px;
    font-size:14px;
    color:#ff4d4d;
}

/* Links */
.links a{
    display:block;
    margin:8px 0;
    padding:10px;
    border-radius:12px;
    font-weight:bold;
    text-decoration:none;
    background: linear-gradient(90deg,#f7971e,#ffd200);
    color:#111;
    transition:0.3s;
}
.links a:hover{
    background: linear-gradient(90deg,#ffd200,#f7971e);
}

</style>
</head>
<body>

<div class="container">
    <h1>Earn Master</h1>
    <a href="https://www.youtube.com/@onlinehelp360-bd" target="_blank" class="developer">Online Help 360</a>

    <div class="stats">
        <p>Watched Ads: <span id="watched-ads">0</span></p>
        <p>Earned Points: <span id="earned-points">0</span></p>
    </div>

    <div class="progress-circle" id="progress-circle"><span id="ads-progress">0%</span></div>

    <div class="buttons">
        <button id="watch-ad-btn">Watch Ad</button>
        <button id="auto-ad-btn" onclick="startAutoAds()">Auto Ads</button>
        <button id="stop-auto-btn" onclick="stopAutoAds()" disabled>Stop Auto</button>
        <button onclick="toggleWithdraw()">Withdraw</button>
    </div>

    <div class="withdraw-section" id="withdraw-section">
        <input type="number" id="withdraw-amount" placeholder="Enter Points">
        <select id="payment-method">
            <option value="bkash">Bkash</option>
            <option value="nagad">Nagad</option>
            <option value="manual">Manual</option>
        </select>
        <input type="text" id="withdraw-phone" placeholder="Enter Phone Number">
        <button onclick="withdrawPoints()">Submit Withdrawal</button>
        <p id="withdraw-status"></p>
    </div>

    <div class="links">
        <a href="https://t.me/bestearningmethod" target="_blank">Telegram Support Group</a>
    </div>
</div>

<!-- Monetag SDK -->
<script src='//libtl.com/sdk.js' data-zone='11978289' data-sdk='show_11978289'></script>

<script>
let watchedAdsCount = parseInt(localStorage.getItem('watchedAdsCount')) || 0;
let earnedPoints = parseFloat(localStorage.getItem('earnedPoints')) || 0;
let autoAdInterval;
let monetagLoaded = false;

// Initialize stats
document.getElementById('watched-ads').textContent = watchedAdsCount;
document.getElementById('earned-points').textContent = earnedPoints.toFixed(2);
updateProgressCircle();

// Disable watch button until SDK loads
document.getElementById('watch-ad-btn').disabled = true;

// Check SDK
function checkSDK(){
    if(typeof window.show_ 11978289=== 'function'){
        monetagLoaded = true;
        document.getElementById('watch-ad-btn').disabled = false;
        console.log('Monetag SDK Loaded');
    } else setTimeout(checkSDK, 500);
}
window.addEventListener('DOMContentLoaded', checkSDK);

function updateProgressCircle(){
    let percent = Math.min((watchedAdsCount/10)*100,100);
    document.getElementById('ads-progress').textContent = percent + '%';
    document.getElementById('progress-circle').style.background = `conic-gradient(#00ffcc ${percent}%, rgba(0,255,204,0.1) ${percent}%)`;
}

// Watch Ad
document.getElementById('watch-ad-btn').addEventListener('click', ()=>{
    if(!monetagLoaded){ alert('Ad service not loaded yet!'); return; }
    show_10081091().then(()=>{
        watchedAdsCount++;
        earnedPoints += 0.5;
        document.getElementById('watched-ads').textContent = watchedAdsCount;
        document.getElementById('earned-points').textContent = earnedPoints.toFixed(2);
        localStorage.setItem('watchedAdsCount', watchedAdsCount);
        localStorage.setItem('earnedPoints', earnedPoints.toFixed(2));
        updateProgressCircle();
    }).catch(e=>{ console.error(e); alert('Ad failed!'); });
});

// Auto Ads
function startAutoAds(){
    autoAdInterval = setInterval(()=>{ document.getElementById('watch-ad-btn').click(); }, 5000);
    document.getElementById('auto-ad-btn').disabled = true;
    document.getElementById('stop-auto-btn').disabled = false;
}
function stopAutoAds(){
    clearInterval(autoAdInterval);
    document.getElementById('auto-ad-btn').disabled = false;
    document.getElementById('stop-auto-btn').disabled = true;
}

// Withdraw
function toggleWithdraw(){ document.getElementById('withdraw-section').style.display = 'block'; }

function withdrawPoints(){
    const amount = parseFloat(document.getElementById('withdraw-amount').value);
    const payment = document.getElementById('payment-method').value;
    const phone = document.getElementById('withdraw-phone').value;
    if(amount<5){ document.getElementById('withdraw-status').textContent="Minimum 5 points"; return; }
    if(amount>earnedPoints){ document.getElementById('withdraw-status').textContent="Insufficient points"; return; }
    earnedPoints-=amount;
    document.getElementById('earned-points').textContent=earnedPoints.toFixed(2);
    localStorage.setItem('earnedPoints',earnedPoints.toFixed(2));
    document.getElementById('withdraw-status').textContent="Withdrawal request submitted!";
    document.getElementById('withdraw-amount').value='';
    document.getElementById('withdraw-phone').value='';
}
</script>

</body>
</html>
