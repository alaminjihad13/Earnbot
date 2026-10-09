# Earnbot
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Earn Master</title>
<style>
@import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@500;700&family=Raleway:wght@400;600&display=swap');

* { 
    box-sizing: border-box; 
    margin: 0; 
    padding: 0; 
    font-family: 'Raleway', sans-serif; 
}

body {
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    background: linear-gradient(135deg, #0f0c29, #302b63, #24243e);
    background-size: 400% 400%;
    animation: gradientBG 15s ease infinite;
    color: #fff;
    padding: 20px 10px;
}

@keyframes gradientBG {
    0% { background-position: 0% 50%; }
    50% { background-position: 100% 50%; }
    100% { background-position: 0% 50%; }
}

.container {
    background: rgba(20, 20, 20, 0.85);
    backdrop-filter: blur(10px);
    padding: 30px 25px;
    border-radius: 20px;
    width: 100%;
    max-width: 380px;
    box-shadow: 0 10px 30px rgba(0, 0, 0, 0.7);
    text-align: center;
    border: 1px solid rgba(255, 255, 255, 0.1);
}

h1 {
    font-family: 'Orbitron', sans-serif;
    font-size: 28px;
    color: #00ffcc;
    margin-bottom: 20px;
    text-shadow: 0 0 10px rgba(0, 255, 204, 0.4);
}

/* Stats */
.stats {
    background: rgba(255, 255, 255, 0.05);
    padding: 15px;
    border-radius: 12px;
    margin-bottom: 20px;
}

.stats p {
    font-size: 15px;
    margin: 6px 0;
    display: flex;
    justify-content: space-between;
}

.stats span {
    font-weight: bold;
    color: #00ffcc;
}

/* Progress Circle */
.progress-circle {
    width: 110px;
    height: 110px;
    border-radius: 50%;
    background: conic-gradient(#00ffcc 0%, rgba(0,255,204,0.1) 0%);
    margin: 20px auto;
    display: flex;
    align-items: center;
    justify-content: center;
    font-weight: bold;
    font-size: 20px;
    color: #00ffcc;
    position: relative;
    box-shadow: 0 0 15px rgba(0, 255, 204, 0.2);
}

.progress-circle::before {
    content: '';
    position: absolute;
    width: 90px;
    height: 90px;
    border-radius: 50%;
    background: #141414;
}

.progress-circle span {
    position: relative;
    z-index: 1;
}

/* Buttons */
.buttons {
    display: flex;
    flex-direction: column;
    gap: 10px;
}

.buttons button {
    width: 100%;
    padding: 12px;
    border: none;
    border-radius: 12px;
    font-size: 16px;
    font-weight: 600;
    cursor: pointer;
    color: #fff;
    background: linear-gradient(45deg, #ff512f, #dd2476);
    transition: all 0.3s ease;
}

.buttons button:hover:not(:disabled) {
    background: linear-gradient(45deg, #dd2476, #ff512f);
    transform: translateY(-2px);
}

.buttons button:disabled {
    opacity: 0.5;
    cursor: not-allowed;
    transform: none;
}

/* Withdraw Section */
.withdraw-section {
    margin-top: 20px;
    display: none;
    background: rgba(30, 30, 30, 0.95);
    padding: 20px;
    border-radius: 15px;
    border: 1px solid rgba(0, 255, 204, 0.2);
    text-align: left;
}

.withdraw-section h3 {
    text-align: center;
    margin-bottom: 12px;
    color: #00ffcc;
    font-size: 18px;
}

.withdraw-section input, 
.withdraw-section select {
    width: 100%;
    padding: 12px;
    margin: 8px 0;
    border-radius: 10px;
    border: 1px solid rgba(255, 255, 255, 0.1);
    background: #111;
    color: #fff;
    font-size: 14px;
    outline: none;
}

.withdraw-section button {
    width: 100%;
    padding: 12px;
    margin-top: 10px;
    font-weight: bold;
    font-size: 16px;
    border: none;
    border-radius: 12px;
    background: linear-gradient(45deg, #1FA2FF, #12D8FA, #A6FFCB);
    color: #111;
    cursor: pointer;
    transition: 0.3s;
}

.withdraw-section button:hover {
    background: linear-gradient(45deg, #A6FFCB, #12D8FA, #1FA2FF);
}

#withdraw-status {
    margin-top: 10px;
    font-size: 14px;
    text-align: center;
    color: #ff4d4d;
}
</style>
</head>
<body>

<div class="container">
    <h1>Earn Master</h1>

    <div class="stats">
        <p>Watched Ads: <span id="watched-ads">0</span></p>
        <p>Earned Points: <span id="earned-points">0</span></p>
    </div>

    <div class="progress-circle" id="progress-circle">
        <span id="ads-progress">0%</span>
    </div>

    <div class="buttons">
        <button id="watch-ad-btn" disabled>Watch Ad</button>
        <button id="auto-ad-btn" onclick="startAutoAds()">Auto Ads</button>
        <button id="stop-auto-btn" onclick="stopAutoAds()" disabled>Stop Auto</button>
        <button onclick="toggleWithdraw()">Withdraw</button>
    </div>

    <div class="withdraw-section" id="withdraw-section">
        <h3>Withdraw Rewards</h3>
        <input type="number" id="withdraw-amount" placeholder="Enter Points (Min: 5)">
        <select id="payment-method">
            <option value="bkash">Bkash</option>
            <option value="nagad">Nagad</option>
            <option value="manual">Manual Transfer</option>
        </select>
        <input type="text" id="withdraw-phone" placeholder="Enter Account/Phone Number">
        <button onclick="withdrawPoints()">Submit Request</button>
        <p id="withdraw-status"></p>
    </div>
</div>

<!-- Monetag SDK Script -->
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

// Check SDK Status
function checkSDK() {
    if (typeof window.show_11978289 === 'function') {
        monetagLoaded = true;
        document.getElementById('watch-ad-btn').disabled = false;
        console.log('Monetag SDK Loaded Successfully');
    } else {
        setTimeout(checkSDK, 500);
    }
}
window.addEventListener('DOMContentLoaded', checkSDK);

function updateProgressCircle() {
    let percent = Math.min((watchedAdsCount / 10) * 100, 100);
    document.getElementById('ads-progress').textContent = Math.round(percent) + '%';
    document.getElementById('progress-circle').style.background = `conic-gradient(#00ffcc ${percent}%, rgba(0,255,204,0.1) ${percent}%)`;
}

// Trigger Monetag Ad Function
function triggerAd() {
    if (!monetagLoaded) { 
        alert('Ad service is not ready yet! Please wait a moment.'); 
        return Promise.reject('SDK not loaded'); 
    }
    
    return show_11978289().then(() => {
        watchedAdsCount++;
        earnedPoints += 0.5;
        document.getElementById('watched-ads').textContent = watchedAdsCount;
        document.getElementById('earned-points').textContent = earnedPoints.toFixed(2);
        localStorage.setItem('watchedAdsCount', watchedAdsCount);
        localStorage.setItem('earnedPoints', earnedPoints.toFixed(2));
        updateProgressCircle();
    }).catch(e => { 
        console.error('Ad Error:', e); 
    });
}

// Manual Ad Watch Button Listener
document.getElementById('watch-ad-btn').addEventListener('click', () => {
    triggerAd().catch(() => alert('Ad failed to load. Check AdBlocker or connection.'));
});

// Auto Ads Handlers
function startAutoAds() {
    if (!monetagLoaded) {
        alert('Ad service is not ready yet!');
        return;
    }
    
    document.getElementById('auto-ad-btn').disabled = true;
    document.getElementById('stop-auto-btn').disabled = false;
    
    triggerAd();
    autoAdInterval = setInterval(() => {
        triggerAd();
    }, 7000);
}

function stopAutoAds() {
    clearInterval(autoAdInterval);
    document.getElementById('auto-ad-btn').disabled = false;
    document.getElementById('stop-auto-btn').disabled = true;
}

// Withdrawal Handlers
function toggleWithdraw() { 
    const section = document.getElementById('withdraw-section');
    section.style.display = section.style.display === 'block' ? 'none' : 'block';
}

function withdrawPoints() {
    const amount = parseFloat(document.getElementById('withdraw-amount').value);
    const payment = document.getElementById('payment-method').value;
    const phone = document.getElementById('withdraw-phone').value;
    const status = document.getElementById('withdraw-status');
    
    if (isNaN(amount) || amount < 5) { 
        status.style.color = '#ff4d4d';
        status.textContent = "Minimum withdrawal is 5 points"; 
        return; 
    }
    if (amount > earnedPoints) { 
        status.style.color = '#ff4d4d';
        status.textContent = "Insufficient points balance"; 
        return; 
    }
    if (!phone.trim()) {
        status.style.color = '#ff4d4d';
        status.textContent = "Please enter phone number";
        return;
    }
    
    earnedPoints -= amount;
    document.getElementById('earned-points').textContent = earnedPoints.toFixed(2);
    localStorage.setItem('earnedPoints', earnedPoints.toFixed(2));
    
    status.style.color = '#00ffcc';
    status.textContent = "Withdrawal request submitted successfully!";
    document.getElementById('withdraw-amount').value = '';
    document.getElementById('withdraw-phone').value = '';
}
</script>

</body>
</html>
