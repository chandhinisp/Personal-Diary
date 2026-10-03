# Personal-Diary

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>My Pastel Diary 🌸</title>
  <!-- Tailwind CSS CDN -->
  <script src="https://cdn.tailwindcss.com"></script>
  <!-- Google Fonts: Quicksand & Gaegu for a cute handwriting feel -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Gaegu:wght@400;700&family=Quicksand:wght@400;500;600;700&display=swap" rel="stylesheet">
  <!-- Lucide Icons -->
  <script src="https://unpkg.com/lucide@latest"></script>

  <script>
    tailwind.config = {
      theme: {
        extend: {
          colors: {
            cream: '#FFF9F5',
            softPink: '#FFE5EC',
            vibrantPink: '#FFB3C6',
            deepPink: '#FB6F92',
            peach: '#FFE5D9',
            lavender: '#E8DFF5',
            mint: '#E0F4EE',
            butter: '#FFF3B0',
            softText: '#5A4A58',
          },
          fontFamily: {
            sans: ['Quicksand', 'sans-serif'],
            hand: ['Gaegu', 'cursive'],
          },
          boxShadow: {
            'cute': '0 8px 24px -4px rgba(251, 111, 146, 0.18), 0 4px 8px -2px rgba(232, 223, 245, 0.3)',
            'card': '0 10px 25px -5px rgba(216, 180, 254, 0.25), 0 8px 10px -6px rgba(255, 179, 198, 0.2)',
            'inner-soft': 'inset 0 2px 6px rgba(0, 0, 0, 0.04)',
          }
        }
      }
    }
  </script>

  <style>
    body {
      background-color: #FFF9F5;
      background-image: 
        radial-gradient(#FFCCD5 1.2px, transparent 1.2px), 
        radial-gradient(#E8DFF5 1.2px, #FFF9F5 1.2px);
      background-size: 32px 32px;
      background-position: 0 0, 16px 16px;
      color: #5A4A58;
    }

    /* Custom cute scrollbars */
    ::-webkit-scrollbar {
      width: 8px;
      height: 8px;
    }
    ::-webkit-scrollbar-track {
      background: #FFF0F5;
      border-radius: 9999px;
    }
    ::-webkit-scrollbar-thumb {
      background: #FFB3C6;
      border-radius: 9999px;
      border: 2px solid #FFF0F5;
    }
    ::-webkit-scrollbar-thumb:hover {
      background: #FB6F92;
    }

    /* Polaroid and Washi Tape effect */
    .washi-tape {
      background: rgba(255, 230, 109, 0.7);
      background-image: repeating-linear-gradient(45deg, transparent, transparent 10px, rgba(255, 255, 255, 0.5) 10px, rgba(255, 255, 255, 0.5) 20px);
      box-shadow: 0 1px 3px rgba(0,0,0,0.1);
    }
    .washi-tape-pink {
      background: rgba(255, 179, 198, 0.75);
      background-image: repeating-linear-gradient(-45deg, transparent, transparent 8px, rgba(255, 255, 255, 0.4) 8px, rgba(255, 255, 255, 0.4) 16px);
    }

    .lined-paper {
      background-color: #FFFFFF;
      background-image: linear-gradient(#f7eef2 1px, transparent 1px);
      background-size: 100% 2rem;
      line-height: 2rem;
    }

    @keyframes floaty {
      0%, 100% { transform: translateY(0px) rotate(0deg); }
      50% { transform: translateY(-5px) rotate(1.5deg); }
    }
    .animate-float {
      animation: floaty 4s ease-in-out infinite;
    }
  </style>
</head>
<body class="min-h-screen flex flex-col antialiased selection:bg-pink-200 selection:text-pink-900">

  <header class="sticky top-0 z-30 bg-white/80 backdrop-blur-md border-b border-pink-100 shadow-sm transition-all duration-300">
    <div class="max-w-5xl mx-auto px-4 sm:px-6 py-3.5 flex items-center justify-between">
      <div class="flex items-center gap-3">
        <div class="w-11 h-11 rounded-2xl bg-gradient-to-tr from-pink-300 via-rose-200 to-purple-200 flex items-center justify-center shadow-cute text-2xl animate-float">
          ✨
        </div>
        <div>
          <h1 class="text-xl sm:text-2xl font-bold font-sans tracking-wide bg-gradient-to-r from-deepPink to-purple-500 bg-clip-text text-transparent">
            Dear Diary
          </h1>
          <p class="text-xs text-softText/70 font-medium">Capture soft thoughts & magical memories 🌸</p>
        </div>
      </div>

      <div class="flex items-center gap-2 sm:gap-3">
        <button id="openNewEntryBtn" onclick="scrollToForm()" class="px-4 py-2 sm:py-2.5 rounded-full bg-gradient-to-r from-deepPink to-pink-400 hover:from-pink-500 hover:to-rose-400 text-white font-semibold text-sm shadow-cute hover:shadow-lg transition-all duration-200 active:scale-95 flex items-center gap-2">
          <i data-lucide="plus" class="w-4 h-4 stroke-[2.5]"></i>
          <span class="hidden sm:inline">Write Page</span>
        </button>
      </div>
    </div>
  </header>

  <main class="flex-grow max-w-5xl w-full mx-auto px-4 sm:px-6 py-6 space-y-8">
    
    <!-- Top Highlights & Stats Cards -->
    <section class="grid grid-cols-2 sm:grid-cols-4 gap-3 sm:gap-4">
      <div class="bg-white/90 backdrop-blur-sm p-4 rounded-3xl border border-pink-100/80 shadow-cute flex items-center gap-3.5 transition-all hover:scale-[1.02]">
        <div class="w-12 h-12 rounded-2xl bg-softPink flex items-center justify-center text-2xl">
          📖
        </div>
        <div>
          <p class="text-xs font-semibold text-softText/60">Pages Written</p>
          <p id="statTotalEntries" class="text-xl font-bold text-softText font-sans">0</p>
        </div>
      </div>

      <div class="bg-white/90 backdrop-blur-sm p-4 rounded-3xl border border-peach/80 shadow-cute flex items-center gap-3.5 transition-all hover:scale-[1.02]">
        <div class="w-12 h-12 rounded-2xl bg-peach flex items-center justify-center text-2xl">
          💖
        </div>
        <div>
          <p class="text-xs font-semibold text-softText/60">Favorites</p>
          <p id="statFavorites" class="text-xl font-bold text-softText font-sans">0</p>
        </div>
      </div>

      <div class="bg-white/90 backdrop-blur-sm p-4 rounded-3xl border border-lavender/80 shadow-cute flex items-center gap-3.5 transition-all hover:scale-[1.02]">
        <div class="w-12 h-12 rounded-2xl bg-lavender flex items-center justify-center text-2xl">
          🎀
        </div>
        <div>
          <p class="text-xs font-semibold text-softText/60">Top Mood</p>
          <p id="statTopMood" class="text-lg font-bold text-softText truncate font-sans">🌸 Joy</p>
        </div>
      </div>

      <div class="bg-white/90 backdrop-blur-sm p-4 rounded-3xl border border-butter/80 shadow-cute flex items-center gap-3.5 transition-all hover:scale-[1.02]">
        <div class="w-12 h-12 rounded-2xl bg-butter/60 flex items-center justify-center text-2xl">
          🧁
        </div>
        <div>
          <p class="text-xs font-semibold text-softText/60">Words Today</p>
          <p id="statWordsToday" class="text-xl font-bold text-softText font-sans">0</p>
        </div>
      </div>
    </section>

    <section id="diaryFormSection" class="relative bg-white rounded-3xl p-5 sm:p-8 border-2 border-pink-100 shadow-card transition-all duration-300">
      
      <!-- Cute Washi Tape Decor on Top of Card -->
      <div class="absolute -top-3.5 left-1/2 -translate-x-1/2 washi-tape-pink w-32 h-7 rounded-sm shadow-sm opacity-90 rotate-[-1deg] pointer-events-none"></div>

      <div class="flex flex-wrap items-center justify-between border-b border-pink-100/80 pb-4 gap-3">
        <div class="flex items-center gap-2">
          <span class="text-2xl" id="editorHeaderIcon">✍️</span>
          <div>
            <h2 id="formTitle" class="text-lg sm:text-xl font-bold text-softText">New Diary Entry</h2>
            <p class="text-xs text-softText/60">Pour your thoughts, stickers, and little sparkles</p>
          </div>
        </div>
        <div class="flex items-center gap-2">
          <input type="date" id="entryDate" class="text-xs sm:text-sm font-medium px-3.5 py-1.5 rounded-full bg-softPink/60 text-softText border border-pink-200 outline-none focus:ring-2 focus:ring-deepPink/50 cursor-pointer">
          <button id="cancelEditBtn" onclick="resetDiaryForm()" class="hidden text-xs px-3 py-1.5 rounded-full bg-gray-100 hover:bg-gray-200 text-gray-600 font-semibold transition">
            Cancel
          </button>
        </div>
      </div>

      <!-- Editor Form -->
      <form id="diaryForm" onsubmit="handleSaveEntry(event)" class="mt-6 space-y-5">
        <input type="hidden" id="editingEntryId" value="">

        <!-- Title & Weather Row -->
        <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
          <div class="md:col-span-2">
            <label class="block text-xs font-bold text-softText/80 uppercase tracking-wider mb-1.5">Title of the day</label>
            <input type="text" id="entryTitle" placeholder="A cozy afternoon with warm tea & sweets..." required 
              class="w-full px-4 py-2.5 rounded-2xl bg-cream border border-pink-200 focus:border-deepPink/60 focus:ring-2 focus:ring-deepPink/20 outline-none font-medium text-softText text-sm sm:text-base placeholder:text-softText/40 transition">
          </div>
          <div>
            <label class="block text-xs font-bold text-softText/80 uppercase tracking-wider mb-1.5">Weather</label>
            <div class="flex items-center gap-1.5 p-1 bg-cream rounded-2xl border border-pink-200 justify-around">
              <button type="button" onclick="setWeather('☀️️ Sunny')" class="weather-btn px-2.5 py-1.5 rounded-xl text-lg hover:bg-white transition" title="Sunny">☀️</button>
              <button type="button" onclick="setWeather('⛅ Mild')" class="weather-btn px-2.5 py-1.5 rounded-xl text-lg hover:bg-white transition" title="Mild">⛅</button>
              <button type="button" onclick="setWeather('🌧️ Rainy')" class="weather-btn px-2.5 py-1.5 rounded-xl text-lg hover:bg-white transition" title="Rainy">🌧️</button>
              <button type="button" onclick="setWeather('🌸 Breezy')" class="weather-btn px-2.5 py-1.5 rounded-xl text-lg hover:bg-white transition" title="Breezy">🌸</button>
              <button type="button" onclick="setWeather('🌙 Night')" class="weather-btn px-2.5 py-1.5 rounded-xl text-lg hover:bg-white transition" title="Starry Night">🌙</button>
            </div>
            <input type="hidden" id="entryWeather" value="☀️ Sunny">
          </div>
        </div>

        <!-- Mood Selector Pill Matrix -->
        <div>
          <label class="block text-xs font-bold text-softText/80 uppercase tracking-wider mb-2">How are you feeling today?</label>
          <div class="flex flex-wrap gap-2" id="moodPicker">
            <!-- Mood items populated dynamically -->
          </div>
          <input type="hidden" id="entryMood" value="🌸 Happy">
        </div>

        <!-- Stickers and Badge Chooser -->
        <div>
          <label class="block text-xs font-bold text-softText/80 uppercase tracking-wider mb-2">Pick cute scrapbook stickers</label>
          <div class="flex flex-wrap gap-2.5 items-center p-3 rounded-2xl bg-cream border border-pink-200/80" id="stickersContainer">
            <!-- Stickers rendered via JS -->
          </div>
        </div>

        <div>
          <div class="flex flex-wrap items-center justify-between mb-2 gap-2">
            <label class="text-xs font-bold text-softText/80 uppercase tracking-wider">Dear Diary Journal Lines</label>
            <div class="flex items-center gap-1 bg-softPink/60 p-1 rounded-full">
              <span class="text-xs font-semibold px-2 text-deepPink">Quick Insert:</span>
              <div class="flex items-center gap-0.5 overflow-x-auto max-w-[280px] sm:max-w-none py-0.5" id="quickEmojiBar">
                <!-- Emoji bar populated via script -->
              </div>
            </div>
          </div>

          <!-- Lined Aesthetic Textarea -->
          <div class="relative">
            <textarea id="entryContent" rows="7" required placeholder="Today was very special because... (Click emojis above or anywhere to decorate your story ✨)" 
              class="w-full px-4 py-3 rounded-2xl border border-pink-200 lined-paper text-softText focus:border-deepPink/60 focus:ring-2 focus:ring-deepPink/20 outline-none text-base placeholder:text-softText/40 transition resize-y"></textarea>
          </div>
          
          <div class="flex justify-between items-center text-xs text-softText/60 mt-1.5 px-1">
            <span id="editorWordCount">0 words written</span>
            <span>Made with cute love 💖</span>
          </div>
        </div>

        <!-- Bottom Action Buttons -->
        <div class="pt-2 flex flex-col sm:flex-row items-center justify-end gap-3">
          <button type="button" onclick="clearEditorDraft()" class="w-full sm:w-auto px-5 py-2.5 rounded-2xl border border-pink-200 text-softText/80 hover:bg-pink-50 font-semibold text-sm transition">
            Clear Draft
          </button>
          <button type="submit" class="w-full sm:w-auto px-7 py-3 rounded-2xl bg-gradient-to-r from-deepPink via-rose-400 to-vibrantPink text-white font-bold text-sm shadow-cute hover:shadow-lg transition transform active:scale-95 flex items-center justify-center gap-2">
            <i data-lucide="sparkles" class="w-4 h-4"></i>
            <span id="saveBtnText">Save to My Diary</span>
          </button>
        </div>
      </form>
    </section>

    <section class="space-y-4">
      <div class="flex flex-col sm:flex-row items-stretch sm:items-center justify-between gap-3">
        <div class="flex items-center gap-2">
          <h3 class="text-xl font-bold text-softText flex items-center gap-2">
            <span>My Memories</span>
            <span id="diaryCountBadge" class="text-xs px-2.5 py-0.5 rounded-full bg-softPink text-deepPink font-semibold border border-pink-200">0</span>
          </h3>
        </div>

        <!-- Search Bar and Filter Pills -->
        <div class="flex flex-wrap items-center gap-2 sm:gap-3">
          <div class="relative flex-grow sm:flex-grow-0 sm:w-60">
            <i data-lucide="search" class="w-4 h-4 text-softText/40 absolute left-3.5 top-1/2 -translate-y-1/2"></i>
            <input type="text" id="searchInput" oninput="handleSearchFilter()" placeholder="Search sweet notes..." 
              class="w-full pl-9 pr-4 py-2 rounded-2xl bg-white border border-pink-200 focus:ring-2 focus:ring-deepPink/20 text-xs sm:text-sm outline-none text-softText placeholder:text-softText/40">
          </div>

          <select id="moodFilterSelect" onchange="handleSearchFilter()" class="px-3 py-2 rounded-2xl bg-white border border-pink-200 text-xs sm:text-sm text-softText outline-none focus:ring-2 focus:ring-deepPink/20">
            <option value="ALL">All Moods 🌈</option>
            <option value="🌸 Happy">🌸 Happy</option>
            <option value="🍓 Sweet">🍓 Sweet</option>
            <option value="🧸 Cozy">🧸 Cozy</option>
            <option value="✨ Excited">✨ Excited</option>
            <option value="🐱 Playful">🐱 Playful</option>
            <option value="☕ Relaxed">☕ Relaxed</option>
            <option value="💖 In Love">💖 In Love</option>
            <option value="🌧️ Melancholy">🌧️ Melancholy</option>
          </select>

          <button id="toggleFavoritesBtn" onclick="toggleFavoritesFilter()" class="px-3.5 py-2 rounded-2xl bg-white border border-pink-200 text-xs sm:text-sm font-semibold text-softText hover:bg-softPink/40 transition flex items-center gap-1.5">
            <span id="favFilterIcon">🤍</span>
            <span class="hidden sm:inline">Favorites</span>
          </button>
        </div>
      </div>

      <!-- Feed / Scrapbook Timeline Container -->
      <div id="entriesFeed" class="grid grid-cols-1 md:grid-cols-2 gap-5 pt-2">
        <!-- Rendered diary entry cards will appear here -->
      </div>

      <!-- Empty State -->
      <div id="emptyState" class="hidden text-center py-16 px-4 bg-white/70 rounded-3xl border border-dashed border-pink-200">
        <div class="w-20 h-20 mx-auto mb-4 rounded-full bg-softPink flex items-center justify-center text-4xl animate-bounce">
          💌
        </div>
        <h4 class="text-lg font-bold text-softText">Your diary is waiting for its first memory!</h4>
        <p class="text-sm text-softText/60 max-w-sm mx-auto mt-1 mb-4">Click "Write Page" above to jot down what made your day delightful or gentle.</p>
        <button onclick="scrollToForm()" class="px-5 py-2.5 rounded-full bg-deepPink text-white font-semibold text-xs shadow-cute hover:bg-pink-600 transition">
          Create Entry ✨
        </button>
      </div>
    </section>

  </main>

  <!-- Cute Notification Toast -->
  <div id="toastMessage" class="fixed bottom-6 right-6 z-50 transform translate-y-20 opacity-0 transition-all duration-300 pointer-events-none flex items-center gap-2.5 px-4 py-3 rounded-2xl bg-white border-2 border-pink-200 shadow-cute text-sm font-bold text-softText">
    <span id="toastIcon">🌸</span>
    <span id="toastText">Page saved to your diary!</span>
  </div>

  <script>
    // Available Moods
    const MOODS = [
      { id: '🌸 Happy', emoji: '🌸', label: 'Happy', color: 'bg-rose-50 border-rose-200 text-rose-700' },
      { id: '🍓 Sweet', emoji: '🍓', label: 'Sweet', color: 'bg-red-50 border-red-200 text-red-700' },
      { id: '🧸 Cozy', emoji: '🧸', label: 'Cozy', color: 'bg-amber-50 border-amber-200 text-amber-700' },
      { id: '✨ Excited', emoji: '✨', label: 'Excited', color: 'bg-purple-50 border-purple-200 text-purple-700' },
      { id: '🐱 Playful', emoji: '🐱', label: 'Playful', color: 'bg-orange-50 border-orange-200 text-orange-700' },
      { id: '☕ Relaxed', emoji: '☕', label: 'Relaxed', color: 'bg-emerald-50 border-emerald-200 text-emerald-700' },
      { id: '💖 In Love', emoji: '💖', label: 'In Love', color: 'bg-pink-50 border-pink-200 text-pink-700' },
      { id: '🌧️ Melancholy', emoji: '🌧️', label: 'Rainy Day', color: 'bg-sky-50 border-sky-200 text-sky-700' },
    ];

    // Available Cute Stickers / Scrapbook Badges
    const STICKERS = [
      { id: 'strawberry', icon: '🍓', label: 'Berry' },
      { id: 'sparkles', icon: '✨', label: 'Glitter' },
      { id: 'cat', icon: '🐾', label: 'Paws' },
      { id: 'cake', icon: '🍰', label: 'Cake' },
      { id: 'ribbon', icon: '🎀', label: 'Ribbon' },
      { id: 'coffee', icon: '☕', label: 'Coffee' },
      { id: 'bunny', icon: '🐰', label: 'Bunny' },
      { id: 'heart', icon: '💌', label: 'Love Note' },
      { id: 'star', icon: '⭐', label: 'Star' },
      { id: 'flower', icon: '🌷', label: 'Tulip' },
    ];

    // Quick Insert Emojis for the editor bar
    const QUICK_EMOJIS = ['🌸', '🍓', '🍰', '🧸', '💖', '✨', '🐾', '🎀', '☁️', '🍵', '🌷', '🧁', '⭐', '💌', '🥞', '🐇'];

    // State
    let diaryEntries = [];
    let selectedMood = '🌸 Happy';
    let selectedWeather = '☀️ Sunny';
    let selectedStickers = new Set(['sparkles', 'ribbon']);
    let onlyFavorites = false;

    window.addEventListener('DOMContentLoaded', () => {
      // Set today's date in form as default
      const dateInput = document.getElementById('entryDate');
      const today = new Date().toISOString().split('T')[0];
      dateInput.value = today;

      // Render static selectors
      renderMoodPicker();
      renderStickerPicker();
      renderQuickEmojiBar();

      // Load entries from localStorage
      loadEntriesFromStorage();

      // Word count listener
      const contentEl = document.getElementById('entryContent');
      contentEl.addEventListener('input', () => {
        updateWordCount(contentEl.value);
      });

      // Initialize icons
      lucide.createIcons();
    });

    function loadEntriesFromStorage() {
      try {
        const stored = localStorage.getItem('my_cute_diary_entries');
        if (stored) {
          diaryEntries = JSON.parse(stored);
        } else {
          // Pre-populate with a warm sample entry
          diaryEntries = [
            {
              id: 'sample-entry-1',
              title: 'Welcome to your pastel sanctuary! 🌸',
              content: "Today I created my new personal diary! It's so cute and peaceful here. I made a hot cup of vanilla chai tea ☕, listened to lofi beats, and decorated my page with cute little strawberries and ribbons. Remember: every small joy counts 💖✨",
              date: new Date().toISOString().split('T')[0],
              mood: '💖 In Love',
              weather: '☀️ Sunny',
              stickers: ['strawberry', 'ribbon', 'sparkles'],
              isFavorite: true,
              createdAt: Date.now()
            }
          ];
          saveToStorage();
        }
      } catch (err) {
        diaryEntries = [];
      }
      renderEntries();
      updateStatistics();
    }

    function saveToStorage() {
      localStorage.setItem('my_cute_diary_entries', JSON.stringify(diaryEntries));
    }

    function renderMoodPicker() {
      const container = document.getElementById('moodPicker');
      container.innerHTML = MOODS.map(m => {
        const isSelected = m.id === selectedMood;
        return `
          <button type="button" onclick="selectMood('${m.id}')" 
            class="px-3.5 py-1.5 rounded-full border text-xs sm:text-sm font-semibold transition-all duration-150 flex items-center gap-1.5 
            ${isSelected ? 'bg-deepPink text-white border-deepPink shadow-cute scale-105' : 'bg-white hover:bg-pink-50 border-pink-200 text-softText'}">
            <span>${m.emoji}</span>
            <span>${m.label}</span>
          </button>
        `;
      }).join('');
    }

    function selectMood(moodId) {
      selectedMood = moodId;
      document.getElementById('entryMood').value = moodId;
      renderMoodPicker();
    }

    function setWeather(weatherText) {
      selectedWeather = weatherText;
      document.getElementById('entryWeather').value = weatherText;
      
      const buttons = document.querySelectorAll('.weather-btn');
      buttons.forEach(btn => {
        if (btn.innerText.trim() === weatherText.split(' ')[0]) {
          btn.classList.add('bg-white', 'shadow-sm', 'scale-110');
        } else {
          btn.classList.remove('bg-white', 'shadow-sm', 'scale-110');
        }
      });
    }

    function renderStickerPicker() {
      const container = document.getElementById('stickersContainer');
      container.innerHTML = STICKERS.map(s => {
        const active = selectedStickers.has(s.id);
        return `
          <button type="button" onclick="toggleSticker('${s.id}')" 
            class="group px-2.5 py-1 rounded-xl text-xs font-semibold flex items-center gap-1 transition-all 
            ${active ? 'bg-pink-200/90 text-deepPink shadow-sm scale-105 border border-pink-300' : 'bg-white/80 text-softText/70 hover:bg-white border border-pink-100'}">
            <span class="text-base group-hover:scale-125 transition-transform">${s.icon}</span>
            <span>${s.label}</span>
          </button>
        `;
      }).join('');
    }

    function toggleSticker(stickerId) {
      if (selectedStickers.has(stickerId)) {
        selectedStickers.delete(stickerId);
      } else {
        selectedStickers.add(stickerId);
      }
      renderStickerPicker();
    }

    function renderQuickEmojiBar() {
      const container = document.getElementById('quickEmojiBar');
      container.innerHTML = QUICK_EMOJIS.map(emoji => `
        <button type="button" onclick="insertEmoji('${emoji}')" class="p-1 text-base hover:scale-125 hover:bg-white rounded-lg transition active:scale-95" title="Insert ${emoji}">
          ${emoji}
        </button>
      `).join('');
    }

    // In-editor emoji insertion directly at cursor position
    function insertEmoji(emoji) {
      const textarea = document.getElementById('entryContent');
      const startPos = textarea.selectionStart || textarea.value.length;
      const endPos = textarea.selectionEnd || textarea.value.length;
      const originalText = textarea.value;

      textarea.value = originalText.substring(0, startPos) + emoji + originalText.substring(endPos);
      textarea.focus();
      textarea.selectionStart = textarea.selectionEnd = startPos + emoji.length;
      updateWordCount(textarea.value);
    }

    function updateWordCount(text) {
      const words = text.trim() ? text.trim().split(/\s+/).length : 0;
      document.getElementById('editorWordCount').innerText = `${words} word${words === 1 ? '' : 's'} written`;
    }

    function handleSaveEntry(e) {
      e.preventDefault();

      const title = document.getElementById('entryTitle').value.trim();
      const content = document.getElementById('entryContent').value.trim();
      const date = document.getElementById('entryDate').value;
      const editingId = document.getElementById('editingEntryId').value;

      if (!title || !content) return;

      if (editingId) {
        // Edit existing
        const index = diaryEntries.findIndex(item => item.id === editingId);
        if (index !== -1) {
          diaryEntries[index] = {
            ...diaryEntries[index],
            title,
            content,
            date,
            mood: selectedMood,
            weather: selectedWeather,
            stickers: Array.from(selectedStickers),
            updatedAt: Date.now()
          };
          showToast('Diary page lovingly updated! ✨', '📝');
        }
      } else {
        // Create new entry
        const newEntry = {
          id: 'entry-' + Date.now(),
          title,
          content,
          date,
          mood: selectedMood,
          weather: selectedWeather,
          stickers: Array.from(selectedStickers),
          isFavorite: false,
          createdAt: Date.now()
        };
        diaryEntries.unshift(newEntry);
        showToast('New memory tucked in! 🌸', '💖');
      }

      saveToStorage();
      resetDiaryForm();
      renderEntries();
      updateStatistics();
    }

    function editEntry(id) {
      const entry = diaryEntries.find(e => e.id === id);
      if (!entry) return;

      document.getElementById('editingEntryId').value = entry.id;
      document.getElementById('entryTitle').value = entry.title;
      document.getElementById('entryContent').value = entry.content;
      document.getElementById('entryDate').value = entry.date;
      
      selectMood(entry.mood || '🌸 Happy');
      setWeather(entry.weather || '☀️️ Sunny');

      selectedStickers = new Set(entry.stickers || []);
      renderStickerPicker();

      updateWordCount(entry.content);

      document.getElementById('formTitle').innerText = 'Edit Diary Memory';
      document.getElementById('saveBtnText').innerText = 'Update Diary Memory';
      document.getElementById('cancelEditBtn').classList.remove('hidden');

      scrollToForm();
    }

    function resetDiaryForm() {
      document.getElementById('diaryForm').reset();
      document.getElementById('editingEntryId').value = '';
      document.getElementById('entryDate').value = new Date().toISOString().split('T')[0];
      selectMood('🌸 Happy');
      setWeather('☀️ Sunny');
      selectedStickers = new Set(['sparkles', 'ribbon']);
      renderStickerPicker();

      document.getElementById('formTitle').innerText = 'New Diary Entry';
      document.getElementById('saveBtnText').innerText = 'Save to My Diary';
      document.getElementById('cancelEditBtn').classList.add('hidden');
      updateWordCount('');
    }

    function clearEditorDraft() {
      resetDiaryForm();
      showToast('Form cleared ✨', '🧹');
    }

    function toggleFavorite(id, event) {
      if (event) event.stopPropagation();
      const index = diaryEntries.findIndex(e => e.id === id);
      if (index !== -1) {
        diaryEntries[index].isFavorite = !diaryEntries[index].isFavorite;
        saveToStorage();
        renderEntries();
        updateStatistics();
        showToast(diaryEntries[index].isFavorite ? 'Added to favorites! 💖' : 'Removed from favorites', '🎀');
      }
    }

    function deleteEntry(id, event) {
      if (event) event.stopPropagation();
      // Safe custom delete with UI prompt replacement: directly filter and inform
      const entry = diaryEntries.find(e => e.id === id);
      const title = entry ? entry.title : 'entry';
      diaryEntries = diaryEntries.filter(e => e.id !== id);
      saveToStorage();
      renderEntries();
      updateStatistics();
      showToast(`Removed "${title.substring(0, 15)}..."`, '🗑️');
    }

    function renderEntries() {
      const feed = document.getElementById('entriesFeed');
      const emptyState = document.getElementById('emptyState');
      const searchQuery = (document.getElementById('searchInput').value || '').toLowerCase().trim();
      const moodFilter = document.getElementById('moodFilterSelect').value;

      // Filter entries
      let filtered = diaryEntries.filter(entry => {
        const matchesQuery = entry.title.toLowerCase().includes(searchQuery) || entry.content.toLowerCase().includes(searchQuery);
        const matchesMood = (moodFilter === 'ALL') || (entry.mood === moodFilter);
        const matchesFav = onlyFavorites ? entry.isFavorite : true;
        return matchesQuery && matchesMood && matchesFav;
      });

      // Update badge
      document.getElementById('diaryCountBadge').innerText = `${filtered.length} entries`;

      if (filtered.length === 0) {
        feed.innerHTML = '';
        emptyState.classList.remove('hidden');
        return;
      }

      emptyState.classList.add('hidden');

      // Sort by date descending
      filtered.sort((a, b) => new Date(b.date) - new Date(a.date));

      feed.innerHTML = filtered.map((entry, idx) => {
        // Decorative washi rotation
        const rotations = ['rotate-[-0.7deg]', 'rotate-[0.5deg]', 'rotate-[-0.3deg]', 'rotate-[0.8deg]'];
        const cardRotation = rotations[idx % rotations.length];

        // Format nice friendly date
        const dateObj = new Date(entry.date + 'T00:00:00');
        const formattedDate = dateObj.toLocaleDateString('en-US', {
          month: 'short',
          day: 'numeric',
          year: 'numeric'
        });
        const dayOfWeek = dateObj.toLocaleDateString('en-US', { weekday: 'long' });

        // Badges for stickers
        const stickersHtml = (entry.stickers || []).map(stId => {
          const stickerObj = STICKERS.find(s => s.id === stId);
          return stickerObj ? `<span class="inline-flex items-center text-xs px-2 py-0.5 rounded-full bg-softPink/60 text-softText" title="${stickerObj.label}">${stickerObj.icon}</span>` : '';
        }).join('');

        return `
          <article class="relative bg-white rounded-3xl p-6 border border-pink-100 shadow-card hover:shadow-cute transition-all duration-300 ${cardRotation} flex flex-col justify-between group">
            
            <!-- Cute Top Washi Tape Decoration -->
            <div class="absolute -top-3 left-8 washi-tape w-20 h-5 rounded-xs shadow-xs pointer-events-none opacity-80"></div>
            
            <div>
              <!-- Header: Date, Weather & Favorite -->
              <div class="flex items-center justify-between border-b border-pink-100/70 pb-3 mb-3">
                <div class="flex items-center gap-2">
                  <div class="w-8 h-8 rounded-full bg-peach flex items-center justify-center text-sm shadow-inner-soft">
                    ${(entry.mood || '🌸').split(' ')[0]}
                  </div>
                  <div>
                    <h4 class="text-xs font-bold text-softText uppercase tracking-wider">${dayOfWeek}, ${formattedDate}</h4>
                    <span class="text-[11px] text-softText/60 flex items-center gap-1">${entry.weather || '☀️ Sunny'}</span>
                  </div>
                </div>

                <!-- Favorite Button -->
                <button onclick="toggleFavorite('${entry.id}', event)" class="p-1.5 rounded-full hover:bg-pink-50 transition active:scale-125" title="Toggle favorite">
                  <span class="text-xl">${entry.isFavorite ? '💖' : '🤍'}</span>
                </button>
              </div>

              <!-- Title & Stickers -->
              <div class="space-y-1.5 mb-3">
                <h3 class="text-lg font-bold text-softText leading-snug group-hover:text-deepPink transition-colors">
                  ${escapeHtml(entry.title)}
                </h3>
                ${stickersHtml ? `<div class="flex flex-wrap gap-1 pt-1">${stickersHtml}</div>` : ''}
              </div>

              <!-- Body with lovely reading font -->
              <p class="text-sm text-softText/80 whitespace-pre-wrap leading-relaxed font-sans mb-4">
                ${escapeHtml(entry.content)}
              </p>
            </div>

            <!-- Bottom controls -->
            <div class="pt-3 border-t border-pink-100/70 flex items-center justify-between text-xs text-softText/60">
              <span class="inline-flex items-center gap-1 font-semibold text-deepPink bg-pink-50 px-2.5 py-1 rounded-full border border-pink-100">
                ${entry.mood || '🌸 Happy'}
              </span>

              <div class="flex items-center gap-1.5">
                <button onclick="editEntry('${entry.id}')" class="px-2.5 py-1 rounded-xl hover:bg-lavender/60 text-softText font-semibold transition flex items-center gap-1">
                  <i data-lucide="edit-3" class="w-3.5 h-3.5"></i>
                  <span>Edit</span>
                </button>
                <button onclick="deleteEntry('${entry.id}', event)" class="px-2.5 py-1 rounded-xl hover:bg-rose-100 text-rose-600 font-semibold transition flex items-center gap-1">
                  <i data-lucide="trash-2" class="w-3.5 h-3.5"></i>
                  <span>Delete</span>
                </button>
              </div>
            </div>

          </article>
        `;
      }).join('');

      lucide.createIcons();
    }

    function updateStatistics() {
      // Total entries
      document.getElementById('statTotalEntries').innerText = diaryEntries.length;

      // Total favorites
      const favsCount = diaryEntries.filter(e => e.isFavorite).length;
      document.getElementById('statFavorites').innerText = favsCount;

      // Top Mood
      if (diaryEntries.length === 0) {
        document.getElementById('statTopMood').innerText = '🌸 Happy';
      } else {
        const counts = {};
        diaryEntries.forEach(e => {
          const m = e.mood || '🌸 Happy';
          counts[m] = (counts[m] || 0) + 1;
        });
        let topMood = Object.keys(counts)[0];
        for (const m in counts) {
          if (counts[m] > counts[topMood]) topMood = m;
        }
        document.getElementById('statTopMood').innerText = topMood;
      }

      // Words Today
      const todayStr = new Date().toISOString().split('T')[0];
      const todayEntries = diaryEntries.filter(e => e.date === todayStr);
      let totalWords = 0;
      todayEntries.forEach(e => {
        totalWords += (e.content || '').trim().split(/\s+/).filter(Boolean).length;
      });
      document.getElementById('statWordsToday').innerText = totalWords;
    }

    function handleSearchFilter() {
      renderEntries();
    }

    function toggleFavoritesFilter() {
      onlyFavorites = !onlyFavorites;
      const btn = document.getElementById('toggleFavoritesBtn');
      const icon = document.getElementById('favFilterIcon');
      if (onlyFavorites) {
        btn.classList.add('bg-deepPink', 'text-white', 'border-deepPink');
        icon.innerText = '💖';
      } else {
        btn.classList.remove('bg-deepPink', 'text-white', 'border-deepPink');
        icon.innerText = '🤍';
      }
      renderEntries();
    }

    function scrollToForm() {
      const form = document.getElementById('diaryFormSection');
      form.scrollIntoView({ behavior: 'smooth' });
      document.getElementById('entryTitle').focus();
    }

    let toastTimer;
    function showToast(message, icon = '🌸') {
      const toast = document.getElementById('toastMessage');
      document.getElementById('toastText').innerText = message;
      document.getElementById('toastIcon').innerText = icon;

      clearTimeout(toastTimer);
      toast.classList.remove('translate-y-20', 'opacity-0');
      toast.classList.add('translate-y-0', 'opacity-100');

      toastTimer = setTimeout(() => {
        toast.classList.add('translate-y-20', 'opacity-0');
        toast.classList.remove('translate-y-0', 'opacity-100');
      }, 2600);
    }

    // Escape helper to prevent raw HTML insertion
    function escapeHtml(str) {
      if (!str) return '';
      return str
        .replace(/&/g, '&amp;')
        .replace(/</g, '&lt;')
        .replace(/>/g, '&gt;')
        .replace(/"/g, '&quot;')
        .replace(/'/g, '&#039;');
    }
  </script>
</body>
</html>
