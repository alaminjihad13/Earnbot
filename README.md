# Earnbot

<!DOCTYPE html>
<html lang="bn">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Earn Master - Ultra Edition</title>
<script src="https://cdn.tailwindcss.com"></script>
<link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@500;700;900&family=Plus+Jakarta+Sans:wght@400;500;600;700&display=swap" rel="stylesheet">
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">

<style>
  body {
    font-family: 'Plus Jakarta Sans', sans-serif;
    background: #04060c;
    color: #f3f4f6;
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    overflow-x: hidden;
  }

  .font-orbitron {
    font-family: 'Orbitron', sans-serif;
  }

  /* Animated Glowing Ambient Dynamic Orbs */
  .orb {
    position: fixed;
    border-radius: 50%;
    filter: blur(80px);
    z-index: 0;
    pointer-events: none;
  }
  .orb-1 {
    top: 10%;
    left: 15%;
    width: 320px;
    height: 320px;
    background: rgba(0, 255, 204, 0.22);
    animation: floatOrb 8s infinite alternate ease-in-out;
  }
  .orb-2 {
    bottom: 10%;
    right: 15%;
    width: 380px;
    height: 380px;
    background: rgba(99, 102, 241, 0.22);
    animation: floatOrb 10s infinite alternate-reverse ease-in-out;
  }
  .orb-3 {
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    width: 250px;
    height: 250px;
    background: rgba(236, 72, 153, 0.12);
    animation: floatOrb 12s infinite alternate ease-in-out;
  }

  @keyframes floatOrb {
    0% { transform: translateY(0px) scale(1); opacity: 0.7; }
    100% { transform: translateY(-30px) scale(1.15); opacity: 1; }
  }

  /* Ultra Cyber Glass Card */
  .glass-card {
    background: rgba(10, 15, 28, 0.75);
    backdrop-filter: blur(25px);
    -webkit-backdrop-filter: blur(25px);
    border: 1px solid rgba(0, 255, 204, 0.25);
    box-shadow: 0 20px 60px rgba(0, 0, 0, 0.8), 0 0 30px rgba(0, 255, 204, 0.15), inset 0 1px 2px rgba(255, 255, 255, 0.15);
  }

  /* Custom Glow Buttons */
  .btn-primary {
    background: linear-gradient(135deg, #00ffcc 0%, #00b894 100%);
    color: #031412;
    box-shadow: 0 0 20px rgba(0, 255, 204, 0.35);
    transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  }
  .btn-primary:hover:not(:disabled) {
    box-shadow: 0 0 35px rgba(0, 255, 204, 0.65);
    transform: translateY(-2px) scale(1.01);
  }

  .btn-secondary {
    background: linear-gradient(135deg, #6366f1 0%, #4f46e5 100%);
    color: #ffffff;
    box-shadow: 0 0 20px rgba(99, 102, 241, 0.35);
    transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  }
  .btn-secondary:hover:not(:disabled) {
    box-shadow: 0 0 35px rgba(99, 102, 241, 0.65);
    transform: translateY(-2px) scale(1.01);
  }

  .btn-danger {
    background: linear-gradient(135deg, #f43f5e 0%, #e11d48 100%);
    color: #ffffff;
    box-shadow: 0 0 20px rgba(244, 63, 94, 0.35);
    transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  }
  .btn-danger:hover:not(:disabled) {
    box-shadow: 0 0 35px rgba(244, 63, 94, 0.65);
    transform: translateY(-2px) scale(1.01);
  }

  button:disabled {
    opacity: 0.3;
    cursor: not-allowed;
    transform: none !important;
    box-shadow: none !important;
  }

  /* Custom Ring Progress Transition */
  .progress-ring-circle {
    transition: stroke-dashoffset 0.6s cubic-bezier(0.4, 0, 0.2, 1);
    transform: rotate(-90deg);
    transform-origin: 50% 50%;
  }
</style>
</head>
<body class="p-4 relative">

<!-- Glowing Background Effects -->
<div class="orb orb-1"></div>
<div class="orb orb-2"></div>
<div class="orb orb-3"></div>

<main class="w-full max-w-md glass-card rounded-[32px] p-6 md:p-8 relative z-10 my-6">
  
  <!-- Top Bar Badges -->
  <div class="flex items-center justify-between mb-6">
    <div class="inline-flex items-center gap-1.5 px-3 py-1 rounded-full bg-cyan-950/80 border border-cyan-500/40 text-cyan-300 text-[11px] font-semibold tracking-wider shadow-[0_0_12px_rgba(0,255,204,0.2)]">
      <span class="w-2 h-2 rounded-full bg-cyan-400 animate-ping"></span>
      অনলাইন রিওয়ার্ডস
    </div>
    <div class="px-3 py-1 rounded-full bg-purple-950/80 border border-purple-500/40 text-purple-300 text-[11px] font-bold tracking-wider">
      <i class="fa-solid fa-crown text-amber-400 mr-1"></i> VIP ৩.০
    </div>
  </div>

  <!-- Header -->
  <header class="text-center mb-6">
    <h1 class="font-orbitron text-4xl font-black text-transparent bg-clip-text bg-gradient-to-r from-cyan-400 via-teal-200 to-indigo-400 tracking-wider drop-shadow-[0_0_15px_rgba(0,255,204,0.4)]">
      EARN MASTER
    </h1>
    <p class="text-xs text-gray-400 mt-1.5">বিজ্ঞাপন দেখুন, পয়েন্ট অর্জন করুন এবং ইন্সট্যান্ট টাকা তুলুন</p>
  </header>

  <!-- Stats Cards Grid -->
  <div class="grid grid-cols-2 gap-3.5 mb-6">
    <div class="bg-gray-900/90 border border-cyan-500/25 rounded-2xl p-4 text-center hover:border-cyan-500/50 transition duration-300 shadow-inner">
      <div class="text-gray-400 text-xs font-medium mb-1 flex items-center justify-center gap-1.5">
        <i class="fa-solid fa-tv text-cyan-400"></i> মোট অ্যাড
      </div>
      <div class="font-orbitron text-2xl font-bold text-white tracking-wider" id="watched-ads">0</div>
    </div>
    
    <div class="bg-gray-900/90 border border-amber-500/25 rounded-2xl p-4 text-center hover:border-amber-500/50 transition duration-300 shadow-inner">
      <div class="text-gray-400 text-xs font-medium mb-1 flex items-center justify-center gap-1.5">
        <i class="fa-solid fa-coins text-amber-400"></i> আপনার পয়েন্ট
      </div>
      <div class="font-orbitron text-2xl font-bold text-amber-400 tracking-wider drop-shadow-[0_0_10px_rgba(251,191,36,0.3)]" id="earned-points">0.00</div>
    </div>
  </div>

  <!-- Circular Progress Ring Chart -->
  <div class="flex flex-col items-center justify-center mb-6 relative">
    <div class="relative w-44 h-44 flex items-center justify-center">
      <svg class="w-full h-full drop-shadow-[0_0_12px_rgba(0,255,204,0.3)]" viewBox="0 0 100 100">
        <!-- Background Circle Track -->
        <circle 
          cx="50" cy="50" r="42" 
          stroke="rgba(255, 255, 255, 0.06)" 
          stroke-width="7" 
          fill="transparent" 
        />
        <!-- Animated Dynamic Progress Line -->
        <circle 
          id="progress-circle-bar"
          class="progress-ring-circle" 
          cx="50" cy="50" r="42" 
          stroke="url(#neon-gradient)" 
          stroke-width="7" 
          stroke-linecap="round"
          stroke-dasharray="263.89" 
          stroke-dashoffset="263.89" 
          fill="transparent" 
        />
        <defs>
          <linearGradient id="neon-gradient" x1="0%" y1="0%" x2="100%" y2="100%">
            <stop offset="0%" stop-color="#00ffcc" />
            <stop offset="50%" stop-color="#3b82f6" />
            <stop offset="100%" stop-color="#8b5cf6" />
          </linearGradient>
        </defs>
      </svg>
      <!-- Center Progress Details -->
      <div class="absolute inset-0 flex flex-col items-center justify-center text-center">
        <span class="font-orbitron text-3xl font-black text-cyan-400 drop-shadow-[0_0_10px_rgba(0,255,204,0.5)]" id="ads-progress">0%</span>
        <span class="text-[10px] uppercase tracking-widest text-gray-400 font-bold mt-1">দৈনিক লক্ষ্য</span>
      </div>
    </div>
    <span class="text-xs text-gray-400 mt-2 font-medium bg-gray-900/60 px-3 py-1 rounded-full border border-gray-800">টার্গেট: ১০ অ্যাড প্রতি সাইকেল</span>
  </div>

  <!-- SDK Network Status Badge -->
  <div id="sdk-status-container" class="mb-6 text-center">
    <div id="sdk-status" class="inline-flex items-center gap-2 text-xs font-semibold px-4 py-2 rounded-xl bg-amber-950/60 text-amber-400 border border-amber-700/50 shadow-lg">
      <i class="fa-solid fa-circle-notch fa-spin"></i> অ্যাড নেটওয়ার্ক সংযুক্ত হচ্ছে...
    </div>
  </div>

  <!-- Primary Controls -->
  <div class="space-y-3 mb-6">
    <button id="watch-ad-btn" disabled class="btn-primary w-full py-4 px-4 rounded-2xl font-bold flex items-center justify-center gap-2.5 text-base tracking-wide">
      <i class="fa-solid fa-circle-play text-lg"></i> অ্যাড দেখুন (+০.৫ পয়েন্ট)
    </button>
    
    <div class="grid grid-cols-2 gap-3">
      <button id="auto-ad-btn" onclick="startAutoAds()" class="btn-secondary py-3.5 px-4 rounded-xl font-bold text-sm flex items-center justify-center gap-2">
        <i class="fa-solid fa-bolt-lightning"></i> অটো অ্যাড
      </button>
      <button id="stop-auto-btn" onclick="stopAutoAds()" disabled class="btn-danger py-3.5 px-4 rounded-xl font-bold text-sm flex items-center justify-center gap-2">
        <i class="fa-solid fa-circle-stop"></i> বন্ধ করুন
      </button>
    </div>

    <button onclick="toggleWithdraw()" class="w-full bg-gray-900/90 hover:bg-gray-800 text-white border border-cyan-500/30 hover:border-cyan-400 py-3.5 px-4 rounded-2xl font-bold flex items-center justify-center gap-2 transition duration-300 shadow-lg">
      <i class="fa-solid fa-wallet text-teal-400"></i> টাকা তুলুন (Withdraw)
    </button>
  </div>

  <!-- Cashout Overlay Section -->
  <div id="withdraw-section" class="hidden bg-gray-950/95 border border-cyan-500/30 p-5 rounded-2xl mb-6 shadow-2xl backdrop-blur-md">
    <div class="flex items-center justify-between mb-4 pb-2 border-b border-gray-800">
      <h3 class="font-orbitron font-bold text-white text-base flex items-center gap-2">
        <i class="fa-solid fa-money-bill-transfer text-cyan-400"></i> ক্যাশআউট রিকোয়েস্ট
      </h3>
      <span class="text-xs text-cyan-400 font-semibold bg-cyan-950/60 px-2 py-0.5 rounded-md border border-cyan-800/50">মিন: ৫.০ পয়েন্ট</span>
    </div>

    <div class="space-y-3.5">
      <div>
        <label class="block text-xs font-semibold text-gray-400 mb-1.5">পেমেন্ট মেথড বেছে নিন</label>
        <select id="payment-method" class="w-full bg-gray-900 border border-gray-800 rounded-xl px-3.5 py-2.5 text-sm text-gray-200 focus:outline-none focus:border-cyan-500 transition">
          <option value="bkash">bKash Personal</option>
          <option value="nagad">Nagad Personal</option>
          <option value="manual">Manual Transfer</option>
        </select>
      </div>

      <div>
        <label class="block text-xs font-semibold text-gray-400 mb-1.5">উইথড্র পয়েন্টের পরিমাণ</label>
        <input type="number" id="withdraw-amount" placeholder="যেমন: 10" class="w-full bg-gray-900 border border-gray-800 rounded-xl px-3.5 py-2.5 text-sm text-gray-200 placeholder-gray-600 focus:outline-none focus:border-cyan-500 transition">
      </div>

      <div>
        <label class="block text-xs font-semibold text-gray-400 mb-1.5">অ্যাকাউন্ট / মোবাইল নাম্বার</label>
        <input type="text" id="withdraw-phone" placeholder="017XXXXXXXX" class="w-full bg-gray-900 border border-gray-800 rounded-xl px-3.5 py-2.5 text-sm text-gray-200 placeholder-gray-600 focus:outline-none focus:border-cyan-500 transition">
      </div>

      <button onclick="withdrawPoints()" class="btn-primary w-full py-3.5 rounded-xl font-extrabold mt-2 text-sm tracking-wide">
        রিকোয়েস্ট কনফার্ম করুন
      </button>

      <p id="withdraw-status" class="text-xs text-center font-medium mt-2 min-h-[16px]"></p>
    </div>
  </div>

  <!-- Bottom System Status Bar -->
  <div class="border-t border-gray-800/80 pt-4">
    <div class="flex items-center justify-between mb-2">
      <span class="text-xs text-gray-400 font-medium">সিস্টেম সিকিউরিটি</span>
      <span class="text-xs text-emerald-400 flex items-center gap-1.5 font-bold">
        <span class="w-2 h-2 rounded-full bg-emerald-400 animate-pulse"></span> সুরক্ষিত
      </span>
    </div>
    <div class="text-[11px] text-gray-500 text-center font-medium">
      Earn Master &copy; 2026. All rights reserved.
    </div>
  </div>

</main>

<!-- Monetag SDK Script -->
<script src='//libtl.com/sdk.js' data-zone='11978289' data-sdk='show_11978289'></script>

<script>
let watchedAdsCount = parseInt(localStorage.getItem('watchedAdsCount')) || 0;
let earnedPoints = parseFloat(localStorage.getItem('earnedPoints')) || 0;
let isAutoRunning = false;
let autoTimeoutId = null;
let monetagLoaded = false;

const maxProgressTarget = 10; 
const strokeDashArrayTotal = 263.89;

// DOM Elements
const watchedAdsEl = document.getElementById('watched-ads');
const earnedPointsEl = document.getElementById('earned-points');
const adsProgressEl = document.getElementById('ads-progress');
const progressCircleBar = document.getElementById('progress-circle-bar');
const watchAdBtn = document.getElementById('watch-ad-btn');
const autoAdBtn = document.getElementById('auto-ad-btn');
const stopAutoBtn = document.getElementById('stop-auto-btn');
const sdkStatus = document.getElementById('sdk-status');

// Initialize Dashboard UI
function initDashboard() {
  watchedAdsEl.textContent = watchedAdsCount;
  earnedPointsEl.textContent = earnedPoints.toFixed(2);
  updateProgressCircle();
}

// Update Circular Progress Bar
function updateProgressCircle() {
  let percent = ((watchedAdsCount % maxProgressTarget) / maxProgressTarget) * 100;
  if (watchedAdsCount > 0 && watchedAdsCount % maxProgressTarget === 0) {
    percent = 100;
  }
  
  adsProgressEl.textContent = `${Math.round(percent)}%`;
  const offset = strokeDashArrayTotal - (strokeDashArrayTotal * percent) / 100;
  progressCircleBar.style.strokeDashoffset = offset;
}

// Check Monetag SDK Readiness
function checkSDK() {
  if (typeof window.show_11978289 === 'function') {
    monetagLoaded = true;
    watchAdBtn.disabled = false;
    sdkStatus.className = "inline-flex items-center gap-2 text-xs font-semibold px-4 py-2 rounded-xl bg-emerald-950/70 text-emerald-400 border border-emerald-700/50 shadow-lg";
    sdkStatus.innerHTML = '<i class="fa-solid fa-circle-check"></i> নেটওয়ার্ক কানেক্টেড';
  } else {
    setTimeout(checkSDK, 500);
  }
}

window.addEventListener('DOMContentLoaded', () => {
  initDashboard();
  checkSDK();
});

// Trigger Monetag Ad Function
function triggerAd() {
  if (!monetagLoaded) {
    return Promise.reject('SDK not ready');
  }

  return show_11978289()
    .then(() => {
      watchedAdsCount++;
      earnedPoints += 0.5;

      watchedAdsEl.textContent = watchedAdsCount;
      earnedPointsEl.textContent = earnedPoints.toFixed(2);
      localStorage.setItem('watchedAdsCount', watchedAdsCount);
      localStorage.setItem('earnedPoints', earnedPoints.toFixed(2));
      updateProgressCircle();
    })
    .catch((err) => {
      console.error('Monetag Ad Error:', err);
      throw err;
    });
}

// Watch Single Ad Button
watchAdBtn.addEventListener('click', () => {
  watchAdBtn.disabled = true;
  triggerAd()
    .catch(() => {
      alert('অ্যাড দেখানো সম্ভব হয়নি। AdBlocker বন্ধ করুন অথবা কিছুক্ষণ পর চেষ্টা করুন।');
    })
    .finally(() => {
      if (monetagLoaded && !isAutoRunning) watchAdBtn.disabled = false;
    });
});

// Auto Ads Loop Handler
function startAutoAds() {
  if (!monetagLoaded) {
    alert('অ্যাড নেটওয়ার্ক কানেক্ট হচ্ছে, দয়া করে অপেক্ষা করুন!');
    return;
  }

  isAutoRunning = true;
  autoAdBtn.disabled = true;
  stopAutoBtn.disabled = false;
  watchAdBtn.disabled = true;

  function autoLoop() {
    if (!isAutoRunning) return;

    triggerAd()
      .catch((e) => console.log('Skipped auto ad iteration:', e))
      .finally(() => {
        if (isAutoRunning) {
          autoTimeoutId = setTimeout(autoLoop, 7000);
        }
      });
  }

  autoLoop();
}

function stopAutoAds() {
  isAutoRunning = false;
  if (autoTimeoutId) {
    clearTimeout(autoTimeoutId);
    autoTimeoutId = null;
  }
  autoAdBtn.disabled = false;
  stopAutoBtn.disabled = true;
  watchAdBtn.disabled = false;
}

// Toggle Withdrawal Box
function toggleWithdraw() {
  const section = document.getElementById('withdraw-section');
  section.classList.toggle('hidden');
}

// Process Withdrawal Submission
function withdrawPoints() {
  const amountInput = document.getElementById('withdraw-amount');
  const phoneInput = document.getElementById('withdraw-phone');
  const statusEl = document.getElementById('withdraw-status');
  
  const amount = parseFloat(amountInput.value);
  const phone = phoneInput.value.trim();

  statusEl.className = "text-xs text-center font-semibold mt-2 text-rose-400";

  if (isNaN(amount) || amount < 5) {
    statusEl.textContent = "সর্বনিম্ন ক্যাশআউট ৫.০ পয়েন্ট";
    return;
  }

  if (amount > earnedPoints) {
    statusEl.textContent = "পর্যাপ্ত পয়েন্ট নেই!";
    return;
  }

  if (!phone || phone.length < 8) {
    statusEl.textContent = "সঠিক ফোন নম্বর দিন";
    return;
  }

  earnedPoints -= amount;
  earnedPointsEl.textContent = earnedPoints.toFixed(2);
  localStorage.setItem('earnedPoints', earnedPoints.toFixed(2));

  statusEl.className = "text-xs text-center font-semibold mt-2 text-emerald-400";
  statusEl.textContent = "ক্যাশআউট রিকোয়েস্ট সফলভাবে জমা হয়েছে!";

  amountInput.value = '';
  phoneInput.value = '';
}
</script>
</body>
</html>
