# ```html
<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Kuis Game Agama Islam</title>
  <!-- Tailwind CSS CDN -->
  <script src="https://cdn.tailwindcss.com"></script>
  <!-- Google Fonts & FontAwesome Icons -->
  <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;500;600;700;800&family=Amiri:wght@700&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
  
  <script>
    tailwind.config = {
      theme: {
        extend: {
          fontFamily: {
            sans: ['"Plus Jakarta Sans"', 'sans-serif'],
            arabic: ['Amiri', 'serif'],
          },
          colors: {
            emerald: {
              850: '#064e3b',
              900: '#022c22',
            }
          }
        }
      }
    }
  </script>

  <style>
    .glass-card {
      background: rgba(255, 255, 255, 0.96);
      backdrop-filter: blur(12px);
    }
    @keyframes pulse-subtle {
      0%, 100% { transform: scale(1); }
      50% { transform: scale(1.03); }
    }
    .animate-pulse-subtle {
      animation: pulse-subtle 3s infinite ease-in-out;
    }
  </style>
</head>
<body class="bg-gradient-to-br from-emerald-900 via-emerald-800 to-teal-950 min-h-screen font-sans text-slate-800 antialiased flex flex-col justify-between selection:bg-emerald-500 selection:text-white">

  <header class="w-full max-w-4xl mx-auto px-4 pt-6 flex justify-between items-center text-white">
    <div class="flex items-center space-x-3">
      <div class="w-11 h-11 rounded-2xl bg-amber-400/20 border border-amber-400/30 flex items-center justify-center text-amber-300 shadow-inner">
        <i class="fa-solid fa-kaaba text-2xl"></i>
      </div>
      <div>
        <h1 class="font-extrabold text-lg sm:text-xl leading-tight tracking-wide">Kuis Cerdas Islam</h1>
        <p class="text-xs text-emerald-200/80">Uji Wawasan & Pengetahuan Agama</p>
      </div>
    </div>
    <div class="flex items-center space-x-2">
      <button id="soundToggleBtn" onclick="toggleSound()" class="p-2.5 px-3.5 rounded-xl bg-white/10 hover:bg-white/20 border border-white/10 transition-all text-xs sm:text-sm font-semibold flex items-center space-x-2 backdrop-blur-md cursor-pointer">
        <i id="soundIcon" class="fa-solid fa-volume-high text-amber-300"></i>
        <span id="soundText" class="hidden sm:inline">Suara On</span>
      </button>
    </div>
  </header>

  <!-- Main Container -->
  <main class="w-full max-w-3xl mx-auto px-4 py-6 flex-1 flex items-center justify-center">

    <!-- 1. START SCREEN -->
    <div id="startScreen" class="w-full glass-card rounded-3xl p-6 sm:p-10 shadow-2xl border border-white/20 text-center">
      <div class="w-20 h-20 mx-auto mb-6 rounded-full bg-emerald-100 border-4 border-emerald-500/30 flex items-center justify-center text-emerald-700 shadow-lg animate-pulse-subtle">
        <i class="fa-solid fa-book-quran text-4xl"></i>
      </div>
      <h2 class="text-2xl sm:text-3xl font-extrabold text-slate-900 mb-2">Selamat Datang di Kuis Islami</h2>
      <p class="text-slate-600 max-w-md mx-auto mb-6 text-sm sm:text-base leading-relaxed">
        Uji pemahaman Anda mengenai Al-Qur'an, Rukun Islam & Iman, Sejarah Nabi, dan Fiqih Dasar.
      </p>

      <!-- Info Badges -->
      <div class="grid grid-cols-3 gap-3 max-w-sm mx-auto mb-6 text-xs sm:text-sm">
        <div class="p-3 rounded-2xl bg-emerald-50 border border-emerald-100 flex flex-col items-center">
          <i class="fa-solid fa-list-check text-emerald-600 mb-1 text-base"></i>
          <span class="font-bold text-slate-800">15 Soal</span>
          <span class="text-slate-500 text-[11px]">Pilihan Ganda</span>
        </div>
        <div class="p-3 rounded-2xl bg-amber-50 border border-amber-100 flex flex-col items-center">
          <i class="fa-solid fa-star text-amber-500 mb-1 text-base"></i>
          <span class="font-bold text-slate-800">+10 Poin</span>
          <span class="text-slate-500 text-[11px]">Per Soal Benar</span>
        </div>
        <div class="p-3 rounded-2xl bg-teal-50 border border-teal-100 flex flex-col items-center">
          <i class="fa-solid fa-trophy text-teal-600 mb-1 text-base"></i>
          <span class="font-bold text-slate-800" id="highScoreText">0</span>
          <span class="text-slate-500 text-[11px]">Skor Tertinggi</span>
        </div>
      </div>

      <!-- Input Nama Peserta -->
      <div class="max-w-sm mx-auto mb-8 text-left">
        <label for="playerNameInput" class="block text-xs font-bold text-slate-700 uppercase tracking-wider mb-2">Nama Peserta</label>
        <div class="relative">
          <i class="fa-solid fa-user-pen absolute left-3.5 top-1/2 -translate-y-1/2 text-emerald-600"></i>
          <input type="text" id="playerNameInput" placeholder="Masukkan nama Anda..." class="w-full pl-10 pr-4 py-3 bg-white border border-slate-200 rounded-2xl text-slate-800 text-sm focus:outline-none focus:ring-2 focus:ring-emerald-500 font-semibold transition-all shadow-sm">
        </div>
      </div>

      <button onclick="startQuiz()" class="w-full sm:w-auto px-10 py-4 bg-gradient-to-r from-emerald-600 to-teal-600 hover:from-emerald-700 hover:to-teal-700 text-white font-bold rounded-2xl shadow-xl shadow-emerald-900/20 hover:shadow-2xl transition-all hover:-translate-y-0.5 active:translate-y-0 flex items-center justify-center space-x-2 mx-auto cursor-pointer">
        <span>Mulai Kuis Sekarang</span>
        <i class="fa-solid fa-arrow-right text-sm"></i>
      </button>
    </div>

    <!-- 2. QUIZ SCREEN -->
    <div id="quizScreen" class="w-full glass-card rounded-3xl p-5 sm:p-8 shadow-2xl border border-white/20 hidden">
      <!-- Quiz Header Stats -->
      <div class="flex flex-col sm:flex-row justify-between items-start sm:items-center gap-4 mb-6 pb-4 border-b border-slate-100">
        <div>
          <!-- Display Player Name -->
          <div class="flex items-center space-x-2 mb-1.5">
            <span class="px-2.5 py-0.5 rounded-md bg-emerald-100 text-emerald-800 text-xs font-bold flex items-center gap-1.5 border border-emerald-200">
              <i class="fa-solid fa-user text-[10px]"></i>
              <span id="displayPlayerName">Peserta</span>
            </span>
          </div>
          <span class="text-xs font-bold tracking-wider uppercase text-emerald-700 bg-emerald-100/80 px-3 py-1 rounded-full border border-emerald-200">
            Soal <span id="currentQuestionNum">1</span> dari <span id="totalQuestionsNum">15</span>
          </span>
          <h3 class="text-xs text-slate-400 mt-1.5 font-medium">Pengetahuan Agama Islam</h3>
        </div>
        
        <div class="flex items-center space-x-4 w-full sm:w-auto justify-between sm:justify-end">
          <!-- Timer -->
          <div class="flex items-center space-x-2 bg-amber-50 border border-amber-200 px-3.5 py-1.5 rounded-xl text-amber-800 font-bold text-sm">
            <i class="fa-solid fa-stopwatch text-amber-600"></i>
            <span id="timerText">20s</span>
          </div>
          <!-- Current Score & Animated Point Badge -->
          <div class="relative flex items-center space-x-2 bg-emerald-50 border border-emerald-200 px-3.5 py-1.5 rounded-xl text-emerald-800 font-bold text-sm">
            <i class="fa-solid fa-star text-amber-500"></i>
            <span id="scoreText">Skor: 0 Poin</span>
            <span id="pointBadge" class="absolute -top-3 -right-2 bg-amber-400 text-amber-950 text-[10px] font-extrabold px-2 py-0.5 rounded-full shadow-md transition-all duration-300 opacity-0 transform translate-y-2 pointer-events-none">+10 Poin</span>
          </div>
        </div>
      </div>

      <!-- Progress Bar -->
      <div class="w-full bg-slate-100 h-2.5 rounded-full overflow-hidden mb-6">
        <div id="progressBar" class="bg-gradient-to-r from-emerald-500 to-teal-500 h-full w-0 transition-all duration-300 ease-out rounded-full"></div>
      </div>

      <!-- Question Box -->
      <div class="mb-6">
        <h2 id="questionText" class="text-lg sm:text-xl font-bold text-slate-900 leading-snug min-h-[56px]">
          Pertanyaan akan muncul di sini...
        </h2>
      </div>

      <!-- Options Container -->
      <div id="optionsContainer" class="space-y-3 mb-6">
        <!-- Dynamic Options -->
      </div>

      <!-- Explanation Box -->
      <div id="explanationBox" class="hidden mb-6 p-4 rounded-2xl bg-emerald-50 border border-emerald-200 text-slate-800 text-sm">
        <div class="flex items-start space-x-2.5">
          <i class="fa-solid fa-circle-info text-emerald-600 text-base mt-0.5"></i>
          <div>
            <span class="font-bold text-emerald-900">Penjelasan:</span>
            <p id="explanationText" class="mt-0.5 text-slate-700 leading-relaxed"></p>
          </div>
        </div>
      </div>

      <!-- Next Button -->
      <div class="flex justify-end">
        <button id="nextBtn" onclick="nextQuestion()" disabled class="px-6 py-3 rounded-xl font-bold text-white bg-slate-300 cursor-not-allowed transition-all flex items-center space-x-2">
          <span>Soal Berikutnya</span>
          <i class="fa-solid fa-chevron-right text-xs"></i>
        </button>
      </div>
    </div>

    <!-- 3. RESULT SCREEN -->
    <div id="resultScreen" class="w-full glass-card rounded-3xl p-6 sm:p-10 shadow-2xl border border-white/20 text-center hidden">
      <div class="w-20 h-20 mx-auto mb-4 rounded-full bg-amber-100 border-4 border-amber-400/40 flex items-center justify-center text-amber-600 shadow-lg">
        <i id="resultIcon" class="fa-solid fa-trophy text-3xl"></i>
      </div>
      <h2 id="resultTitle" class="text-2xl sm:text-3xl font-extrabold text-slate-900 mb-1">Kuis Selesai!</h2>
      <p id="resultSubtitle" class="text-slate-600 text-sm mb-2">Berikut ringkasan hasil pencapaian Anda</p>
      
      <!-- Player Name Badge in Result -->
      <div class="inline-block bg-emerald-100 text-emerald-900 font-bold px-4 py-1.5 rounded-full text-xs sm:text-sm mb-6 border border-emerald-200">
        <i class="fa-solid fa-user-check mr-1.5 text-emerald-700"></i>
        <span>Peserta: </span><span id="resultPlayerName">Peserta</span>
      </div>

      <!-- Score Circle Display -->
      <div class="bg-gradient-to-br from-slate-900 to-emerald-950 text-white p-6 rounded-3xl max-w-md mx-auto mb-6 border border-emerald-500/20 shadow-xl">
        <div class="text-xs uppercase tracking-widest text-emerald-400 font-semibold mb-1">Total Poin Akhir Anda</div>
        <div class="text-5xl font-black text-amber-400 mb-2"><span id="finalScoreText">0</span> <span class="text-2xl font-bold text-amber-300">Poin</span></div>
        <div class="text-xs text-slate-300" id="correctSummary">Menjawab 0 dari 15 soal dengan benar</div>
        <div class="text-[11px] text-emerald-300/80 mt-1 font-medium" id="pointCalculationDetail">10 Poin per jawaban benar</div>
      </div>

      <!-- Accuracy Stats -->
      <div class="grid grid-cols-2 gap-3 max-w-md mx-auto mb-8 text-sm">
        <div class="p-3.5 rounded-2xl bg-emerald-50 border border-emerald-100 text-left">
          <div class="text-xs text-emerald-700 font-semibold">Jawaban Benar</div>
          <div class="text-xl font-bold text-emerald-900" id="correctCountText">0</div>
        </div>
        <div class="p-3.5 rounded-2xl bg-rose-50 border border-rose-100 text-left">
          <div class="text-xs text-rose-700 font-semibold">Jawaban Salah</div>
          <div class="text-xl font-bold text-rose-900" id="wrongCountText">0</div>
        </div>
      </div>

      <div class="flex flex-col sm:flex-row justify-center gap-3">
        <button onclick="reviewAnswers()" class="px-6 py-3.5 bg-slate-100 hover:bg-slate-200 text-slate-800 font-bold rounded-2xl transition-all flex items-center justify-center space-x-2 cursor-pointer">
          <i class="fa-solid fa-magnifying-glass"></i>
          <span>Tinjau Jawaban</span>
        </button>
        <button onclick="restartQuiz()" class="px-8 py-3.5 bg-gradient-to-r from-emerald-600 to-teal-600 hover:from-emerald-700 hover:to-teal-700 text-white font-bold rounded-2xl shadow-lg transition-all flex items-center justify-center space-x-2 cursor-pointer">
          <i class="fa-solid fa-rotate-right"></i>
          <span>Main Lagi</span>
        </button>
      </div>
    </div>

    <!-- 4. REVIEW SCREEN -->
    <div id="reviewScreen" class="w-full glass-card rounded-3xl p-5 sm:p-8 shadow-2xl border border-white/20 hidden max-h-[80vh] flex flex-col">
      <div class="flex justify-between items-center pb-4 mb-4 border-b border-slate-100">
        <h2 class="text-xl font-bold text-slate-900 flex items-center space-x-2">
          <i class="fa-solid fa-list-check text-emerald-600"></i>
          <span>Tinjauan Jawaban</span>
        </h2>
        <button onclick="backToResult()" class="text-slate-400 hover:text-slate-600 text-sm font-semibold p-2 cursor-pointer">
          <i class="fa-solid fa-xmark text-lg"></i>
        </button>
      </div>

      <div id="reviewContainer" class="overflow-y-auto space-y-4 pr-1 flex-1">
        <!-- Dynamic Review Items -->
      </div>

      <div class="pt-4 border-t border-slate-100 mt-4 flex justify-end">
        <button onclick="restartQuiz()" class="px-6 py-3 bg-emerald-600 hover:bg-emerald-700 text-white font-bold rounded-xl text-sm transition-all cursor-pointer">
          Main Lagi
        </button>
      </div>
    </div>

  </main>

  <footer class="w-full text-center py-4 text-xs text-emerald-200/60">
    Kuis Agama Islam &copy; 2026 - Dilengkapi Pertanyaan & Kunci Jawaban Lengkap
  </footer>

  <script>
    // Data Soal Kuis Agama Islam
    const quizData = [
      {
        id: 1,
        question: "Kitab suci Al-Qur'an diturunkan kepada Nabi Muhammad SAW melalui perantara malaikat...",
        options: ["Malaikat Jibril", "Malaikat Mikail", "Malaikat Izrail", "Malaikat Israfil"],
        answer: 0,
        explanation: "Malaikat Jibril bertugas menyampaikan wahyu Allah SWT kepada para nabi dan rasul."
      },
      {
        id: 2,
        question: "Surah pertama yang diturunkan kepada Nabi Muhammad SAW di Gua Hira adalah...",
        options: ["Surah Al-Baqarah ayat 1-5", "Surah Al-Fatihah ayat 1-7", "Surah Al-'Alaq ayat 1-5", "Surah Al-Ikhlas ayat 1-4"],
        answer: 2,
        explanation: "Wahyu pertama yang diterima Nabi Muhammad SAW di Gua Hira adalah Surah Al-'Alaq ayat 1-5."
      },
      {
        id: 3,
        question: "Urutan rukun Islam yang ketiga adalah...",
        options: ["Menunaikan zakat", "Mendirikan shalat", "Berpuasa di bulan Ramadhan", "Menunaikan haji bagi yang mampu"],
        answer: 0,
        explanation: "Rukun Islam ketiga adalah Menunaikan Zakat (1. Syahadat, 2. Shalat, 3. Zakat, 4. Puasa, 5. Haji)."
      },
      {
        id: 4,
        question: "Nabi yang mendapat julukan Khatamul Anbiya (Penutup Para Nabi) adalah...",
        options: ["Nabi Ibrahim a.s.", "Nabi Muhammad SAW", "Nabi Isa a.s.", "Nabi Musa a.s."],
        answer: 1,
        explanation: "Nabi Muhammad SAW adalah penutup para nabi dan rasul (Khatamul Anbiya)."
      },
      {
        id: 5,
        question: "Shalat wajib lima waktu yang memiliki jumlah rakaat paling sedikit adalah...",
        options: ["Shalat Dzuhur", "Shalat Isya", "Shalat Subuh", "Shalat Maghrib"],
        answer: 2,
        explanation: "Shalat Subuh berjumlah 2 rakaat, merupakan shalat fardhu dengan jumlah rakaat paling sedikit."
      },
      {
        id: 6,
        question: "Peristiwa perjalanan malam hari Nabi Muhammad SAW dari Masjidil Haram ke Masjidil Aqsha lalu naik ke Sidratul Muntaha disebut...",
        options: ["Isra Mi'raj", "Fathu Makkah", "Perjanjian Hudaibiyah", "Peristiwa Hijrah"],
        answer: 0,
        explanation: "Isra Mi'raj adalah perjalanan mukjizat Rasulullah SAW dari Makkah ke Palestina lalu naik ke Sidratul Muntaha."
      },
      {
        id: 7,
        question: "Malaikat yang bertugas mencatat amal buruk manusia adalah...",
        options: ["Malaikat Munkar", "Malaikat Nakir", "Malaikat 'Atid", "Malaikat Raqib"],
        answer: 2,
        explanation: "Malaikat 'Atid bertugas mencatat amal buruk, sedangkan Malaikat Raqib mencatat amal baik."
      },
      {
        id: 8,
        question: "Jumlah juz yang terdapat di dalam Al-Qur'an secara keseluruhan adalah...",
        options: ["20 Juz", "30 Juz", "25 Juz", "40 Juz"],
        answer: 1,
        explanation: "Al-Qur'an terdiri dari 30 juz, 114 surah, dan 6.236 ayat."
      },
      {
        id: 9,
        question: "Khalifah pertama dari Khulafaur Rasyidin yang menggantikan kepemimpinan setelah Nabi Muhammad SAW wafat adalah...",
        options: ["Ali bin Abi Thalib", "Abu Bakar Ash-Shiddiq", "Umar bin Khattab", "Utsman bin Affan"],
        answer: 1,
        explanation: "Abu Bakar Ash-Shiddiq r.a. adalah khalifah pertama umat Islam dalam Khulafaur Rasyidin."
      },
      {
        id: 10,
        question: "Bersuci menggunakan debu atau tanah yang bersih sebagai pengganti wudhu dinamakan...",
        options: ["Mandi Wajib", "Istinja", "Tayamum", "Tazkiyah"],
        answer: 2,
        explanation: "Tayamum adalah cara bersuci menggunakan debu yang suci jika tidak ada air atau dalam kondisi darurat/sakit."
      },
      {
        id: 11,
        question: "Puasa yang hukumnya wajib dilakukan oleh setiap umat Islam yang memenuhi syarat selama satu bulan penuh adalah...",
        options: ["Puasa Syawwal", "Puasa 'Arafah", "Puasa Ramadhan", "Puasa Senin-Kamis"],
        answer: 2,
        explanation: "Puasa Ramadhan hukumnya fardhu 'ain (wajib) dilakukan selama satu bulan penuh di bulan Ramadhan."
      },
      {
        id: 12,
        question: "Rukun Iman yang kelima menurut ajaran Islam adalah percaya kepada...",
        options: ["Malaikat-malaikat Allah", "Hari Kiamat", "Kitab-kitab Allah", "Qada dan Qadar"],
        answer: 1,
        explanation: "Rukun Iman ke-5 adalah percaya kepada Hari Kiamat (Hari Akhir)."
      },
      {
        id: 13,
        question: "Kitab suci Injil diturunkan oleh Allah SWT kepada Nabi...",
        options: ["Nabi Daud a.s.", "Nabi Ibrahim a.s.", "Nabi Isa a.s.", "Nabi Musa a.s."],
        answer: 2,
        explanation: "Kitab Injil diturunkan kepada Nabi Isa a.s., Taurat kepada Nabi Musa a.s., Zabur kepada Nabi Daud a.s., dan Al-Qur'an kepada Nabi Muhammad SAW."
      },
      {
        id: 14,
        question: "Gelar Al-Amin yang diberikan masyarakat Makkah kepada Nabi Muhammad SAW berarti...",
        options: ["Orang yang penyabar", "Orang yang cerdas", "Orang yang pemurah", "Orang yang dapat dipercaya"],
        answer: 3,
        explanation: "Gelar Al-Amin artinya orang yang jujur dan dapat dipercaya."
      },
      {
        id: 15,
        question: "Jumlah Rukun Iman ada...",
        options: ["Lima", "Enam", "Tiga", "Dua"],
        answer: 1,
        explanation: "Rukun Iman ada 6 perkara: Iman kepada Allah, Malaikat, Kitab, Rasul, Hari Kiamat, serta Qada & Qadar."
      }
    ];

    // State Variables
    let currentQuestionIndex = 0;
    let score = 0;
    let userAnswers = [];
    let timer = null;
    let timeLeft = 20;
    let isSoundOn = true;
    let audioCtx = null;
    let playerName = "Peserta";

    // Web Audio Synthesizer for SFX
    function playSound(type) {
      if (!isSoundOn) return;
      try {
        if (!audioCtx) audioCtx = new (window.AudioContext || window.webkitAudioContext)();
        if (audioCtx.state === 'suspended') audioCtx.resume();

        const osc = audioCtx.createOscillator();
        const gain = audioCtx.createGain();
        osc.connect(gain);
        gain.connect(audioCtx.destination);

        const now = audioCtx.currentTime;

        if (type === 'correct') {
          osc.type = 'sine';
          osc.frequency.setValueAtTime(523.25, now);
          osc.frequency.exponentialRampToValueAtTime(659.25, now + 0.15);
          gain.gain.setValueAtTime(0.2, now);
          gain.gain.exponentialRampToValueAtTime(0.01, now + 0.3);
          osc.start(now);
          osc.stop(now + 0.3);
        } else if (type === 'wrong') {
          osc.type = 'sawtooth';
          osc.frequency.setValueAtTime(220, now);
          osc.frequency.exponentialRampToValueAtTime(164.81, now + 0.2);
          gain.gain.setValueAtTime(0.2, now);
          gain.gain.exponentialRampToValueAtTime(0.01, now + 0.3);
          osc.start(now);
          osc.stop(now + 0.3);
        } else if (type === 'click') {
          osc.type = 'sine';
          osc.frequency.setValueAtTime(400, now);
          gain.gain.setValueAtTime(0.05, now);
          gain.gain.exponentialRampToValueAtTime(0.01, now + 0.05);
          osc.start(now);
          osc.stop(now + 0.05);
        }
      } catch (e) {
        console.log("Audio play error");
      }
    }

    function toggleSound() {
      isSoundOn = !isSoundOn;
      const icon = document.getElementById('soundIcon');
      const text = document.getElementById('soundText');
      if (isSoundOn) {
        icon.className = 'fa-solid fa-volume-high text-amber-300';
        text.textContent = 'Suara On';
      } else {
        icon.className = 'fa-solid fa-volume-xmark text-slate-400';
        text.textContent = 'Mute';
      }
    }

    function loadHighScore() {
      const savedScore = localStorage.getItem('islamic_quiz_high_score') || 0;
      document.getElementById('highScoreText').textContent = savedScore;
    }

    function startQuiz() {
      playSound('click');

      // Ambil Nama Peserta
      const inputName = document.getElementById('playerNameInput').value.trim();
      playerName = inputName !== "" ? inputName : "Peserta";

      document.getElementById('displayPlayerName').textContent = playerName;
      document.getElementById('resultPlayerName').textContent = playerName;

      currentQuestionIndex = 0;
      score = 0;
      userAnswers = [];
      
      document.getElementById('startScreen').classList.add('hidden');
      document.getElementById('resultScreen').classList.add('hidden');
      document.getElementById('reviewScreen').classList.add('hidden');
      document.getElementById('quizScreen').classList.remove('hidden');

      document.getElementById('totalQuestionsNum').textContent = quizData.length;
      loadQuestion();
    }

    function loadQuestion() {
      clearInterval(timer);
      const q = quizData[currentQuestionIndex];
      
      document.getElementById('currentQuestionNum').textContent = currentQuestionIndex + 1;
      document.getElementById('scoreText').textContent = `Skor: ${score} Poin`;
      document.getElementById('questionText').textContent = q.question;
      
      const progressPercent = ((currentQuestionIndex) / quizData.length) * 100;
      document.getElementById('progressBar').style.width = `${progressPercent}%`;

      document.getElementById('explanationBox').classList.add('hidden');

      const nextBtn = document.getElementById('nextBtn');
      nextBtn.disabled = true;
      nextBtn.className = "px-6 py-3 rounded-xl font-bold text-white bg-slate-300 cursor-not-allowed transition-all flex items-center space-x-2";

      const optionsContainer = document.getElementById('optionsContainer');
      optionsContainer.innerHTML = '';

      const labels = ['A', 'B', 'C', 'D'];

      q.options.forEach((opt, idx) => {
        const btn = document.createElement('button');
        btn.onclick = () => selectOption(idx);
        btn.id = `option-${idx}`;
        btn.className = `w-full text-left p-4 rounded-2xl border border-slate-200 bg-white hover:border-emerald-500 hover:bg-emerald-50/50 transition-all flex items-center justify-between group shadow-sm cursor-pointer`;

        btn.innerHTML = `
          <div class="flex items-center space-x-3">
            <span class="w-8 h-8 rounded-xl bg-slate-100 group-hover:bg-emerald-500 group-hover:text-white text-slate-600 font-bold flex items-center justify-center text-xs transition-colors border border-slate-200 group-hover:border-emerald-500">
              ${labels[idx]}
            </span>
            <span class="font-medium text-slate-800 text-sm sm:text-base">${opt}</span>
          </div>
          <div class="status-icon text-lg"></div>
        `;
        optionsContainer.appendChild(btn);
      });

      startTimer();
    }

    function startTimer() {
      timeLeft = 20;
      document.getElementById('timerText').textContent = `${timeLeft}s`;
      
      timer = setInterval(() => {
        timeLeft--;
        document.getElementById('timerText').textContent = `${timeLeft}s`;
        
        if (timeLeft <= 0) {
          clearInterval(timer);
          selectOption(-1);
        }
      }, 1000);
    }

    function selectOption(selectedIndex) {
      clearInterval(timer);

      const q = quizData[currentQuestionIndex];
      const isCorrect = selectedIndex === q.answer;

      userAnswers.push({
        questionIndex: currentQuestionIndex,
        selected: selectedIndex,
        correct: q.answer,
        isCorrect: isCorrect
      });

      if (isCorrect) {
        score += 10;
        playSound('correct');

        // Tampilkan animasi pop-up +10 Poin pada counter skor
        const pointBadge = document.getElementById('pointBadge');
        if (pointBadge) {
          pointBadge.classList.remove('opacity-0', 'translate-y-2');
          pointBadge.classList.add('opacity-100', 'translate-y-0', 'scale-110');
          setTimeout(() => {
            pointBadge.classList.remove('opacity-100', 'translate-y-0', 'scale-110');
            pointBadge.classList.add('opacity-0', 'translate-y-2');
          }, 1200);
        }
      } else {
        playSound('wrong');
      }

      const buttons = document.querySelectorAll('#optionsContainer button');
      buttons.forEach((btn, idx) => {
        btn.disabled = true;
        btn.classList.remove('hover:border-emerald-500', 'hover:bg-emerald-50/50', 'cursor-pointer');

        const statusIcon = btn.querySelector('.status-icon');

        if (idx === q.answer) {
          btn.className = "w-full text-left p-4 rounded-2xl border-2 border-emerald-500 bg-emerald-50/90 flex items-center justify-between shadow-md transition-all";
          statusIcon.innerHTML = `<i class="fa-solid fa-circle-check text-emerald-600"></i>`;
        } else if (idx === selectedIndex) {
          btn.className = "w-full text-left p-4 rounded-2xl border-2 border-rose-500 bg-rose-50/90 flex items-center justify-between shadow-md transition-all";
          statusIcon.innerHTML = `<i class="fa-solid fa-circle-xmark text-rose-600"></i>`;
        } else {
          btn.classList.add('opacity-50');
        }
      });

      document.getElementById('explanationText').textContent = q.explanation;
      document.getElementById('explanationBox').classList.remove('hidden');

      document.getElementById('scoreText').textContent = `Skor: ${score} Poin`;

      const nextBtn = document.getElementById('nextBtn');
      nextBtn.disabled = false;
      nextBtn.className = "px-6 py-3 rounded-xl font-bold text-white bg-gradient-to-r from-emerald-600 to-teal-600 hover:from-emerald-700 hover:to-teal-700 shadow-lg cursor-pointer transition-all flex items-center space-x-2";
    }

    function nextQuestion() {
      playSound('click');
      currentQuestionIndex++;

      if (currentQuestionIndex < quizData.length) {
        loadQuestion();
      } else {
        showResults();
      }
    }

    function showResults() {
      document.getElementById('quizScreen').classList.add('hidden');
      document.getElementById('resultScreen').classList.remove('hidden');

      const correctCount = userAnswers.filter(a => a.isCorrect).length;
      const wrongCount = quizData.length - correctCount;

      document.getElementById('finalScoreText').textContent = score;
      document.getElementById('correctSummary').textContent = `Menjawab ${correctCount} dari ${quizData.length} soal dengan benar`;
      document.getElementById('pointCalculationDetail').textContent = `Rincian: ${correctCount} Jawaban Benar × 10 Poin = ${score} Poin`;
      document.getElementById('correctCountText').textContent = `${correctCount} (${correctCount * 10} Poin)`;
      document.getElementById('wrongCountText').textContent = `${wrongCount} (0 Poin)`;

      const resultTitle = document.getElementById('resultTitle');
      const resultSubtitle = document.getElementById('resultSubtitle');
      const resultIcon = document.getElementById('resultIcon');

      if (correctCount === quizData.length) {
        resultTitle.textContent = "Mumtaz! (Sempurna)";
        resultSubtitle.textContent = "Luar biasa! Anda menjawab semua pertanyaan dengan sempurna.";
        resultIcon.className = "fa-solid fa-crown text-amber-500 text-3xl";
      } else if (correctCount >= 10) {
        resultTitle.textContent = "Jayyid Jiddan! (Sangat Baik)";
        resultSubtitle.textContent = "Pengetahuan pemahaman agama Anda sudah sangat baik.";
        resultIcon.className = "fa-solid fa-star text-amber-500 text-3xl";
      } else {
        resultTitle.textContent = "Tetap Semangat!";
        resultSubtitle.textContent = "Terus tingkatkan pemahaman pengetahuan agama Islam Anda.";
        resultIcon.className = "fa-solid fa-book-open text-emerald-600 text-3xl";
      }

      const savedScore = localStorage.getItem('islamic_quiz_high_score') || 0;
      if (score > savedScore) {
        localStorage.setItem('islamic_quiz_high_score', score);
        document.getElementById('highScoreText').textContent = score;
      }
    }

    function reviewAnswers() {
      playSound('click');
      document.getElementById('resultScreen').classList.add('hidden');
      document.getElementById('reviewScreen').classList.remove('hidden');

      const container = document.getElementById('reviewContainer');
      container.innerHTML = '';

      quizData.forEach((q, idx) => {
        const uAns = userAnswers[idx];
        const isCorrect = uAns ? uAns.isCorrect : false;
        const selectedOptText = uAns && uAns.selected !== -1 ? q.options[uAns.selected] : "Waktu Habis / Tidak Dijawab";
        const correctOptText = q.options[q.answer];

        const card = document.createElement('div');
        card.className = `p-4 rounded-2xl border ${isCorrect ? 'bg-emerald-50/60 border-emerald-200' : 'bg-rose-50/60 border-rose-200'} text-left text-sm space-y-2`;

        card.innerHTML = `
          <div class="flex justify-between items-start gap-2">
            <span class="font-bold text-slate-900">${idx + 1}. ${q.question}</span>
            <span class="px-2.5 py-0.5 rounded-full text-[11px] font-bold ${isCorrect ? 'bg-emerald-200 text-emerald-800' : 'bg-rose-200 text-rose-800'} whitespace-nowrap">
              ${isCorrect ? 'Benar' : 'Salah'}
            </span>
          </div>
          <div class="text-xs space-y-1">
            <div><span class="text-slate-500">Jawaban Anda:</span> <span class="font-semibold ${isCorrect ? 'text-emerald-700' : 'text-rose-700'}">${selectedOptText}</span></div>
            ${!isCorrect ? `<div><span class="text-slate-500">Jawaban Benar:</span> <span class="font-semibold text-emerald-800">${correctOptText}</span></div>` : ''}
          </div>
          <div class="text-xs text-slate-600 pt-1 border-t border-slate-200/60 italic">
            ${q.explanation}
          </div>
        `;
        container.appendChild(card);
      });
    }

    function backToResult() {
      playSound('click');
      document.getElementById('reviewScreen').classList.add('hidden');
      document.getElementById('resultScreen').classList.remove('hidden');
    }

    function restartQuiz() {
      startQuiz();
    }

    window.onload = loadHighScore;
  </script>
</body>
</html>
```-quiz-tentang-islam-coding-Al
