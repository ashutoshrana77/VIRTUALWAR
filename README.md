# VIRTUALWAR 
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>NeoVista Smart City Dashboard</title>
  <meta name="description" content="NeoVista Smart City — Real-time city management dashboard tracking cleanliness, traffic, energy, safety, and civic complaints." />
  <meta name="theme-color" content="#080818" />

  <!-- Fonts -->
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Outfit:wght@300;400;500;600;700;900&family=JetBrains+Mono:wght@400;600&display=swap" rel="stylesheet" />

  <!-- Chart.js CDN (local data only) -->
  <script src="https://cdn.jsdelivr.net/npm/chart.js@4.4.2/dist/chart.umd.min.js"></script>

  <!-- Styles -->
  <link rel="stylesheet" href="css/style.css" />
</head>
<body>

<!-- Mobile overlay -->
<div id="overlay" class="overlay"></div>

<!-- Toast -->
<div id="toast" class="toast"></div>

<!-- ── App Layout ──────────────────────────────────────────── -->
<div class="app-layout">

  <!-- ── Sidebar ─────────────────────────────────────────── -->
  <aside class="sidebar" id="sidebar">
    <a class="sidebar-logo" href="#" onclick="navigateTo('dashboard');return false;">
      <div class="logo-icon">🌆</div>
      <div class="logo-text">NeoVista City<span>Smart City Hub</span></div>
    </a>

    <nav class="sidebar-nav">
      <div class="nav-section-label">Overview</div>

      <div class="nav-item active" data-page="dashboard" id="nav-dashboard"
           onclick="navigateTo('dashboard');closeMobileSidebar()">
        <span class="nav-icon">🏠</span>
        <span>Dashboard</span>
      </div>

      <div class="nav-item" data-page="progress" id="nav-progress"
           onclick="navigateTo('progress');closeMobileSidebar()">
        <span class="nav-icon">📊</span>
        <span>City Progress</span>
        <span class="nav-badge">24</span>
      </div>

      <div class="nav-section-label">Community</div>

      <div class="nav-item" data-page="complaints" id="nav-complaints"
           onclick="navigateTo('complaints');closeMobileSidebar()">
        <span class="nav-icon">📋</span>
        <span>Complaints</span>
        <span class="nav-badge" style="background:var(--red);color:#fff">3</span>
      </div>

      <div class="nav-section-label">System</div>

      <div class="nav-item" data-page="settings" id="nav-settings"
           onclick="navigateTo('settings');closeMobileSidebar()">
        <span class="nav-icon">⚙️</span>
        <span>Settings</span>
      </div>
    </nav>

    <div class="sidebar-footer">
      <div class="city-status-pill">
        <div class="pulse"></div>
        <span>All Systems Operational</span>
      </div>
    </div>
  </aside>

  <!-- ── Main Content ────────────────────────────────────── -->
  <div class="main-content">

    <!-- Navbar -->
    <header class="navbar">
      <button class="hamburger" id="hamburger" aria-label="Toggle sidebar">☰</button>
      <div class="navbar-title"><span>NeoVista</span> — 🏠 Dashboard</div>
      <div class="navbar-clock" id="clock">--:--:--</div>
      <div class="navbar-actions">
        <div class="icon-btn" title="Notifications" onclick="showToast('📢 6 new city announcements!')">
          🔔<span class="notif-dot"></span>
        </div>
        <div class="icon-btn" title="Map view" onclick="showToast('🗺️ Map view coming soon!')">🗺️</div>
        <div class="icon-btn" title="Profile" onclick="showToast('👤 Citizen profile portal coming soon!')">👤</div>
      </div>
    </header>

    <!-- Page Content (injected by router) -->
    <main id="app"></main>

  </div>
</div>

<!-- ── Chatbot Widget ──────────────────────────────────────── -->
<div class="chatbot-widget" id="chatbot-widget">
  <div class="chatbot-panel" id="chatbot-panel">
    <div class="chatbot-header">
      <div class="chatbot-avatar">🤖</div>
      <div class="chatbot-header-text">
        <h4>NeoBot</h4>
        <p>● Online — City AI Assistant</p>
      </div>
      <button class="chatbot-close" title="Close chat">✕</button>
    </div>

    <div class="chatbot-messages">
      <div class="msg bot">
        <div class="msg-avatar">🤖</div>
        <div class="msg-bubble">👋 Hi! I'm <strong>NeoBot</strong>, your NeoVista City assistant.<br>Ask me about traffic, complaints, energy, or city news!</div>
      </div>
    </div>

    <div class="quick-replies"></div>

    <div class="chatbot-input-row">
      <input class="chatbot-input" type="text" placeholder="Ask about the city..." maxlength="200" />
      <button class="chatbot-send" title="Send">➤</button>
    </div>
  </div>

  <button class="chatbot-toggle" title="Open NeoBot">🤖</button>
</div>

<!-- ── Scripts ─────────────────────────────────────────────── -->
<script src="js/data.js"></script>
<script src="js/chatbot.js"></script>
<script src="js/charts.js"></script>
<script src="js/main.js"></script>

<script>
  // Mobile sidebar helper
  function closeMobileSidebar() {
    document.querySelector('.sidebar').classList.remove('open');
    document.getElementById('overlay').classList.remove('show');
  }
</script>

</body>
</html>
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>NeoVista Smart City Dashboard</title>
  <meta name="description" content="NeoVista Smart City — Real-time city management dashboard tracking cleanliness, traffic, energy, safety, and civic complaints." />
  <meta name="theme-color" content="#080818" />

  <!-- Fonts -->
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Outfit:wght@300;400;500;600;700;900&family=JetBrains+Mono:wght@400;600&display=swap" rel="stylesheet" />

  <!-- Chart.js CDN (local data only) -->
  <script src="https://cdn.jsdelivr.net/npm/chart.js@4.4.2/dist/chart.umd.min.js"></script>

  <!-- Styles -->
  <link rel="stylesheet" href="css/style.css" />
</head>
<body>

<!-- Mobile overlay -->
<div id="overlay" class="overlay"></div>

<!-- Toast -->
<div id="toast" class="toast"></div>

<!-- ── App Layout ──────────────────────────────────────────── -->
<div class="app-layout">

  <!-- ── Sidebar ─────────────────────────────────────────── -->
  <aside class="sidebar" id="sidebar">
    <a class="sidebar-logo" href="#" onclick="navigateTo('dashboard');return false;">
      <div class="logo-icon">🌆</div>
      <div class="logo-text">NeoVista City<span>Smart City Hub</span></div>
    </a>

    <nav class="sidebar-nav">
      <div class="nav-section-label">Overview</div>

      <div class="nav-item active" data-page="dashboard" id="nav-dashboard"
           onclick="navigateTo('dashboard');closeMobileSidebar()">
        <span class="nav-icon">🏠</span>
        <span>Dashboard</span>
      </div>

      <div class="nav-item" data-page="progress" id="nav-progress"
           onclick="navigateTo('progress');closeMobileSidebar()">
        <span class="nav-icon">📊</span>
        <span>City Progress</span>
        <span class="nav-badge">24</span>
      </div>

      <div class="nav-section-label">Community</div>

      <div class="nav-item" data-page="complaints" id="nav-complaints"
           onclick="navigateTo('complaints');closeMobileSidebar()">
        <span class="nav-icon">📋</span>
        <span>Complaints</span>
        <span class="nav-badge" style="background:var(--red);color:#fff">3</span>
      </div>

      <div class="nav-section-label">System</div>

      <div class="nav-item" data-page="settings" id="nav-settings"
           onclick="navigateTo('settings');closeMobileSidebar()">
        <span class="nav-icon">⚙️</span>
        <span>Settings</span>
      </div>
    </nav>

    <div class="sidebar-footer">
      <div class="city-status-pill">
        <div class="pulse"></div>
        <span>All Systems Operational</span>
      </div>
    </div>
  </aside>

  <!-- ── Main Content ────────────────────────────────────── -->
  <div class="main-content">

    <!-- Navbar -->
    <header class="navbar">
      <button class="hamburger" id="hamburger" aria-label="Toggle sidebar">☰</button>
      <div class="navbar-title"><span>NeoVista</span> — 🏠 Dashboard</div>
      <div class="navbar-clock" id="clock">--:--:--</div>
      <div class="navbar-actions">
        <div class="icon-btn" title="Notifications" onclick="showToast('📢 6 new city announcements!')">
          🔔<span class="notif-dot"></span>
        </div>
        <div class="icon-btn" title="Map view" onclick="showToast('🗺️ Map view coming soon!')">🗺️</div>
        <div class="icon-btn" title="Profile" onclick="showToast('👤 Citizen profile portal coming soon!')">👤</div>
      </div>
    </header>

    <!-- Page Content (injected by router) -->
    <main id="app"></main>

  </div>
</div>

<!-- ── Chatbot Widget ──────────────────────────────────────── -->
<div class="chatbot-widget" id="chatbot-widget">
  <div class="chatbot-panel" id="chatbot-panel">
    <div class="chatbot-header">
      <div class="chatbot-avatar">🤖</div>
      <div class="chatbot-header-text">
        <h4>NeoBot</h4>
        <p>● Online — City AI Assistant</p>
      </div>
      <button class="chatbot-close" title="Close chat">✕</button>
    </div>

    <div class="chatbot-messages">
      <div class="msg bot">
        <div class="msg-avatar">🤖</div>
        <div class="msg-bubble">👋 Hi! I'm <strong>NeoBot</strong>, your NeoVista City assistant.<br>Ask me about traffic, complaints, energy, or city news!</div>
      </div>
    </div>

    <div class="quick-replies"></div>

    <div class="chatbot-input-row">
      <input class="chatbot-input" type="text" placeholder="Ask about the city..." maxlength="200" />
      <button class="chatbot-send" title="Send">➤</button>
    </div>
  </div>

  <button class="chatbot-toggle" title="Open NeoBot">🤖</button>
</div>

<!-- ── Scripts ─────────────────────────────────────────────── -->
<script src="js/data.js"></script>
<script src="js/chatbot.js"></script>
<script src="js/charts.js"></script>
<script src="js/main.js"></script>

<script>
  // Mobile sidebar helper
  function closeMobileSidebar() {
    document.querySelector('.sidebar').classList.remove('open');
    document.getElementById('overlay').classList.remove('show');
  }
</script>

</body>
</html>
