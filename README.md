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

// ============================================================
//  SMART CITY — SPA Router & Page Renderers
// ============================================================

let currentPage = 'dashboard';
let complaintsList = [...CITY_DATA.complaints];
let filterStatus = 'All';

// ── Router ──────────────────────────────────────────────────
function navigateTo(page) {
  currentPage = page;

  // Update nav active state
  document.querySelectorAll('.nav-item').forEach(item => {
    item.classList.toggle('active', item.dataset.page === page);
  });

  // Update navbar title
  const titles = {
    dashboard:  '🏠 Dashboard',
    progress:   '📊 City Progress',
    complaints: '📋 Complaints Tracker',
    settings:   '⚙️ Settings'
  };
  document.querySelector('.navbar-title').innerHTML =
    `<span>NeoVista</span> — ${titles[page] || page}`;

  // Render page
  const app = document.getElementById('app');
  app.classList.remove('page-enter');
  void app.offsetWidth; // reflow trigger
  app.classList.add('page-enter');

  switch (page) {
    case 'dashboard':  renderDashboard();  break;
    case 'progress':   renderProgress();   break;
    case 'complaints': renderComplaints(); break;
    case 'settings':   renderSettings();   break;
  }
}

// ── Clock ───────────────────────────────────────────────────
function startClock() {
  const el = document.querySelector('.navbar-clock');
  if (!el) return;
  const tick = () => {
    const now = new Date();
    el.textContent = now.toLocaleTimeString('en-IN', { hour: '2-digit', minute: '2-digit', second: '2-digit' });
  };
  tick();
  setInterval(tick, 1000);
}

// ── Animate Progress Bars ────────────────────────────────────
function animateBars() {
  setTimeout(() => {
    document.querySelectorAll('.progress-fill[data-width]').forEach(bar => {
      bar.style.width = bar.dataset.width + '%';
    });
  }, 100);
}

// ── Toast ────────────────────────────────────────────────────
function showToast(msg) {
  const t = document.getElementById('toast');
  if (!t) return;
  t.textContent = msg;
  t.classList.add('show');
  setTimeout(() => t.classList.remove('show'), 3200);
}

// ── Sidebar Mobile ───────────────────────────────────────────
function initSidebar() {
  const hamburger = document.querySelector('.hamburger');
  const sidebar   = document.querySelector('.sidebar');
  const overlay   = document.getElementById('overlay');

  hamburger?.addEventListener('click', () => {
    sidebar.classList.toggle('open');
    overlay.classList.toggle('show');
  });
  overlay?.addEventListener('click', () => {
    sidebar.classList.remove('open');
    overlay.classList.remove('show');
  });
}

// ============================================================
//  PAGE: Dashboard
// ============================================================
function renderDashboard() {
  const { kpis, statusFeed, announcements, charts } = CITY_DATA;

  // --- Announcement Ticker ---
  const tickerItems = [...announcements, ...announcements].map(a => `<span>${a}</span>`).join('');

  // --- KPI Cards ---
  const kpiCards = Object.values(kpis).map(k => {
    const isDown = k.trend.startsWith('-');
    return `
    <div class="kpi-card">
      <div class="kpi-header">
        <span class="kpi-icon">${k.icon}</span>
        <span class="kpi-trend ${isDown ? 'trend-down' : 'trend-up'}">${k.trend}</span>
      </div>
      <div class="kpi-value">${k.value}<small style="font-size:16px;color:#94a3b8">${k.unit}</small></div>
      <div class="kpi-label">${k.label}</div>
    </div>`;
  }).join('');

  // --- City Metrics Progress Bars ---
  const metrics = [
    { label: 'Cleanliness Index',    val: kpis.cleanliness.value },
    { label: 'Traffic Flow Score',   val: kpis.traffic.value     },
    { label: 'Public Safety Rating', val: kpis.safety.value      },
    { label: 'Energy Efficiency',    val: kpis.energy.value      }
  ];
  const bars = metrics.map(m => `
    <div class="progress-bar-wrap">
      <div class="progress-meta">
        <span class="prog-label">${m.label}</span>
        <span class="prog-val">${m.val}%</span>
      </div>
      <div class="progress-track">
        <div class="progress-fill" data-width="${m.val}" style="width:0"></div>
      </div>
    </div>`).join('');

  // --- Feed ---
  const feedItems = statusFeed.map(f => `
    <div class="feed-item ${f.type}">
      <span class="feed-icon">${f.icon}</span>
      <span class="feed-msg">${f.msg}</span>
      <span class="feed-time">${f.time}</span>
    </div>`).join('');

  document.getElementById('app').innerHTML = `
    <div class="page-content">
      <div class="page-header">
        <h1>City Command Center</h1>
        <p>Real-time overview of NeoVista City — Last updated: ${CITY_DATA.lastUpdated}</p>
      </div>

      <div class="ticker-wrap">
        <span class="ticker-label">📢 Live</span>
        <div class="ticker-track">
          <div class="ticker-inner">${tickerItems}</div>
        </div>
      </div>

      <div class="kpi-grid">${kpiCards}</div>

      <div class="grid-2" style="margin-bottom:24px">
        <div class="card">
          <div class="section-title">Monthly Traffic Flow</div>
          <div class="chart-wrap"><canvas id="trafficChart"></canvas></div>
        </div>
        <div class="card">
          <div class="section-title">City Metrics Overview</div>
          <div style="display:flex;flex-direction:column;gap:22px;margin-top:8px">${bars}</div>
        </div>
      </div>

      <div class="grid-2" style="margin-bottom:24px">
        <div class="card">
          <div class="section-title">Energy Sources Breakdown</div>
          <div class="chart-wrap"><canvas id="energyDonut"></canvas></div>
        </div>
        <div class="card">
          <div class="section-title">Complaints by Category</div>
          <div class="chart-wrap"><canvas id="complaintsBar"></canvas></div>
        </div>
      </div>

      <div class="card" style="margin-bottom:24px">
        <div class="section-title">6-Month City Trends</div>
        <div class="chart-wrap" style="height:260px"><canvas id="multiLineChart"></canvas></div>
      </div>

      <div class="card">
        <div class="section-title">Live City Status Feed</div>
        <div class="feed-list">${feedItems}</div>
      </div>
    </div>`;

  animateBars();
  setTimeout(renderAllCharts, 50);
}

// ============================================================
//  PAGE: City Progress
// ============================================================
function renderProgress() {
  const cards = CITY_DATA.progressUpdates.map(p => `
    <div class="prog-card">
      <div class="prog-card-header">
        <div class="prog-card-icon">${p.icon}</div>
        <div class="prog-card-meta">
          <h3>${p.title}</h3>
          <div class="category">${p.category}</div>
        </div>
        <span class="status-badge ${p.statusClass}">${p.status}</span>
      </div>
      <p class="prog-desc">${p.description}</p>
      <div class="progress-bar-wrap" style="margin-bottom:14px">
        <div class="progress-meta">
          <span class="prog-label">Completion</span>
          <span class="prog-val">${p.completion}%</span>
        </div>
        <div class="progress-track">
          <div class="progress-fill" data-width="${p.completion}" style="width:0"></div>
        </div>
      </div>
      <div class="prog-footer">
        <span>🗓️ ${p.date}</span>
        <span style="font-family:'JetBrains Mono',monospace;color:var(--neon-cyan);font-size:11px">${p.completion < 100 ? p.completion + '% done' : '✅ Complete'}</span>
      </div>
    </div>`).join('');

  // Summary stats
  const total    = CITY_DATA.progressUpdates.length;
  const done     = CITY_DATA.progressUpdates.filter(p => p.status === 'Completed').length;
  const ongoing  = CITY_DATA.progressUpdates.filter(p => p.status === 'In Progress').length;
  const planned  = CITY_DATA.progressUpdates.filter(p => p.status === 'Planning').length;

  document.getElementById('app').innerHTML = `
    <div class="page-content">
      <div class="page-header">
        <h1>City Development Progress</h1>
        <p>Track all ongoing, planned, and completed city projects in NeoVista.</p>
      </div>

      <div class="kpi-grid" style="margin-bottom:28px">
        <div class="kpi-card">
          <div class="kpi-header"><span class="kpi-icon">🏗️</span></div>
          <div class="kpi-value">${total}</div>
          <div class="kpi-label">Total Projects</div>
        </div>
        <div class="kpi-card">
          <div class="kpi-header"><span class="kpi-icon">✅</span></div>
          <div class="kpi-value">${done}</div>
          <div class="kpi-label">Completed</div>
        </div>
        <div class="kpi-card">
          <div class="kpi-header"><span class="kpi-icon">⚙️</span></div>
          <div class="kpi-value">${ongoing}</div>
          <div class="kpi-label">In Progress</div>
        </div>
        <div class="kpi-card">
          <div class="kpi-header"><span class="kpi-icon">📋</span></div>
          <div class="kpi-value">${planned}</div>
          <div class="kpi-label">Planned</div>
        </div>
      </div>

      <div class="section-title">All Projects</div>
      <div class="progress-grid">${cards}</div>
    </div>`;

  animateBars();
}

// ============================================================
//  PAGE: Complaints Tracker
// ============================================================
function renderComplaints() {
  document.getElementById('app').innerHTML = `
    <div class="page-content">
      <div class="page-header">
        <h1>Community Complaints Tracker</h1>
        <p>Submit and track civic complaints. All issues are addressed within 48–72 hours.</p>
      </div>

      <div class="complaints-layout">
        <!-- Form -->
        <div class="card">
          <div class="section-title">File a Complaint</div>
          <form id="complaintForm" onsubmit="submitComplaint(event)">
            <div class="form-group">
              <label>Full Name</label>
              <input class="form-input" id="cmpName" placeholder="Your full name" required>
            </div>
            <div class="form-row">
              <div class="form-group">
                <label>Category</label>
                <select class="form-select" id="cmpCategory" required>
                  <option value="">Select...</option>
                  <option>Roads</option><option>Water</option><option>Power</option>
                  <option>Sanitation</option><option>Noise</option><option>Other</option>
                </select>
              </div>
              <div class="form-group">
                <label>Priority</label>
                <select class="form-select" id="cmpPriority">
                  <option>High</option><option>Medium</option><option>Low</option>
                </select>
              </div>
            </div>
            <div class="form-group">
              <label>Description</label>
              <textarea class="form-textarea" id="cmpDesc" placeholder="Describe the issue in detail..." required></textarea>
            </div>
            <button type="submit" class="btn btn-primary">🚀 Submit Complaint</button>
          </form>
        </div>

        <!-- List -->
        <div>
          <div class="card">
            <div style="display:flex;align-items:center;justify-content:space-between;margin-bottom:16px">
              <div class="section-title" style="margin-bottom:0">Recent Complaints</div>
              <span style="font-size:12px;color:var(--text-muted)" id="complaintCount"></span>
            </div>
            <div class="complaints-filters" id="filterBtns">
              ${['All','Pending','In Progress','Resolved'].map(f =>
                `<button class="filter-btn ${f === filterStatus ? 'active' : ''}" onclick="filterComplaints('${f}')">${f}</button>`
              ).join('')}
            </div>
            <div style="overflow-x:auto">
              <table class="complaint-table">
                <thead>
                  <tr>
                    <th>ID</th><th>Name</th><th>Category</th>
                    <th>Priority</th><th>Status</th><th>Date</th>
                  </tr>
                </thead>
                <tbody id="complaintBody"></tbody>
              </table>
            </div>
          </div>
        </div>
      </div>
    </div>`;

  renderComplaintTable();
}

function submitComplaint(e) {
  e.preventDefault();
  const name     = document.getElementById('cmpName').value.trim();
  const category = document.getElementById('cmpCategory').value;
  const priority = document.getElementById('cmpPriority').value;
  const desc     = document.getElementById('cmpDesc').value.trim();
  const id       = 'CMP-' + (1042 + complaintsList.length);
  const date     = new Date().toISOString().split('T')[0];

  complaintsList.unshift({ id, name, category, status: 'Pending', date, description: desc, priority });
  document.getElementById('complaintForm').reset();
  renderComplaintTable();
  showToast(`✅ Complaint ${id} submitted successfully!`);
}

function filterComplaints(status) {
  filterStatus = status;
  document.querySelectorAll('.filter-btn').forEach(b => {
    b.classList.toggle('active', b.textContent === status);
  });
  renderComplaintTable();
}

function renderComplaintTable() {
  const filtered = filterStatus === 'All' ? complaintsList : complaintsList.filter(c => c.status === filterStatus);
  const count = document.getElementById('complaintCount');
  if (count) count.textContent = `${filtered.length} record${filtered.length !== 1 ? 's' : ''}`;

  const body = document.getElementById('complaintBody');
  if (!body) return;
  if (filtered.length === 0) {
    body.innerHTML = `<tr><td colspan="6" style="text-align:center;padding:24px;color:var(--text-muted)">No complaints found.</td></tr>`;
    return;
  }
  const statusColors = { 'Resolved': 'var(--green)', 'In Progress': 'var(--yellow)', 'Pending': 'var(--red)' };
  body.innerHTML = filtered.map(c => `
    <tr>
      <td><span class="complaint-id">${c.id}</span></td>
      <td style="color:var(--text-primary);font-weight:500">${c.name}</td>
      <td>${c.category}</td>
      <td><span class="priority-badge priority-${c.priority}">${c.priority}</span></td>
      <td><span style="color:${statusColors[c.status]||'#94a3b8'};font-size:12px;font-weight:600">● ${c.status}</span></td>
      <td style="font-family:'JetBrains Mono',monospace;font-size:11px">${c.date}</td>
    </tr>`).join('');
}

// ============================================================
//  PAGE: Settings
// ============================================================
function renderSettings() {
  document.getElementById('app').innerHTML = `
    <div class="page-content">
      <div class="page-header">
        <h1>Settings & Preferences</h1>
        <p>Customize your NeoVista dashboard experience.</p>
      </div>

      <div class="settings-grid">
        <!-- Appearance -->
        <div class="card">
          <div class="section-title">Appearance</div>
          <div class="setting-row">
            <div class="setting-info"><h4>Dark Mode</h4><p>Use dark futuristic theme</p></div>
            <button class="toggle on" onclick="this.classList.toggle('on')" title="Toggle dark mode"></button>
          </div>
          <div class="setting-row">
            <div class="setting-info"><h4>Neon Animations</h4><p>Glow effects & micro-animations</p></div>
            <button class="toggle on" onclick="this.classList.toggle('on')"></button>
          </div>
          <div class="setting-row">
            <div class="setting-info"><h4>Compact Sidebar</h4><p>Show icons only</p></div>
            <button class="toggle" onclick="toggleCompactSidebar(this)"></button>
          </div>
          <div class="setting-row">
            <div class="setting-info"><h4>Accent Color</h4><p>Dashboard highlight color</p></div>
            <div class="color-swatches">
              <div class="swatch active" style="background:#00f0ff" onclick="setAccent('#00f0ff','#a855f7',this)" title="Cyan"></div>
              <div class="swatch" style="background:#f59e0b" onclick="setAccent('#f59e0b','#f43f5e',this)" title="Amber"></div>
              <div class="swatch" style="background:#10b981" onclick="setAccent('#10b981','#3b82f6',this)" title="Green"></div>
              <div class="swatch" style="background:#f43f5e" onclick="setAccent('#f43f5e','#a855f7',this)" title="Red"></div>
              <div class="swatch" style="background:#f59e0b" onclick="setAccent('#f59e0b','#10b981',this)" title="Gold"></div>
            </div>
          </div>
        </div>

        <!-- Accessibility -->
        <div class="card">
          <div class="section-title">Accessibility</div>
          <div class="setting-row">
            <div class="setting-info"><h4>Font Size</h4><p>Adjust base text size</p></div>
            <input type="range" class="range-slider" min="12" max="20" value="14"
              oninput="document.body.style.fontSize=this.value+'px'">
          </div>
          <div class="setting-row">
            <div class="setting-info"><h4>High Contrast</h4><p>Increase text contrast</p></div>
            <button class="toggle" onclick="toggleHighContrast(this)"></button>
          </div>
          <div class="setting-row">
            <div class="setting-info"><h4>Reduce Motion</h4><p>Disable animations</p></div>
            <button class="toggle" onclick="toggleMotion(this)"></button>
          </div>
          <div class="setting-row">
            <div class="setting-info"><h4>Large Cursor</h4><p>Increase cursor visibility</p></div>
            <button class="toggle" onclick="this.classList.toggle('on');document.body.style.cursor=this.classList.contains('on')?'none url(data:image/svg+xml,<svg xmlns=\\'http://www.w3.org/2000/svg\\' width=\\'32\\' height=\\'32\\'/>),auto':'auto'"></button>
          </div>
        </div>

        <!-- Notifications -->
        <div class="card">
          <div class="section-title">Notifications</div>
          <div class="setting-row">
            <div class="setting-info"><h4>Alert Feed</h4><p>City alerts & emergencies</p></div>
            <button class="toggle on" onclick="this.classList.toggle('on')"></button>
          </div>
          <div class="setting-row">
            <div class="setting-info"><h4>Complaint Updates</h4><p>Status changes on your complaints</p></div>
            <button class="toggle on" onclick="this.classList.toggle('on')"></button>
          </div>
          <div class="setting-row">
            <div class="setting-info"><h4>Announcements</h4><p>City news & events</p></div>
            <button class="toggle on" onclick="this.classList.toggle('on')"></button>
          </div>
        </div>

        <!-- Dashboard -->
        <div class="card">
          <div class="section-title">Dashboard</div>
          <div class="setting-row">
            <div class="setting-info"><h4>Auto-Refresh</h4><p>Refresh data every 30s</p></div>
            <button class="toggle" onclick="this.classList.toggle('on')"></button>
          </div>
          <div class="setting-row">
            <div class="setting-info"><h4>Chart Animations</h4><p>Animate chart rendering</p></div>
            <button class="toggle on" onclick="this.classList.toggle('on')"></button>
          </div>
          <div class="setting-row">
            <div class="setting-info"><h4>Ticker Bar</h4><p>Show announcements ticker</p></div>
            <button class="toggle on" onclick="this.classList.toggle('on')"></button>
          </div>
          <div class="setting-row" style="margin-top:8px">
            <button class="btn btn-primary" onclick="showToast('✅ Settings saved!')" style="width:100%;justify-content:center">💾 Save Preferences</button>
          </div>
        </div>
      </div>
    </div>`;
}

// ── Settings Helpers ─────────────────────────────────────────
function setAccent(cyan, purple, el) {
  document.documentElement.style.setProperty('--neon-cyan', cyan);
  document.documentElement.style.setProperty('--neon-purple', purple);
  document.querySelectorAll('.swatch').forEach(s => s.classList.remove('active'));
  el.classList.add('active');
  showToast('🎨 Accent color updated!');
}
function toggleHighContrast(btn) {
  btn.classList.toggle('on');
  document.documentElement.style.setProperty('--text-secondary', btn.classList.contains('on') ? '#e2e8f0' : '#94a3b8');
}
function toggleMotion(btn) {
  btn.classList.toggle('on');
  document.documentElement.style.setProperty('--transition', btn.classList.contains('on') ? 'none' : 'all 0.3s cubic-bezier(0.4,0,0.2,1)');
}
function toggleCompactSidebar(btn) {
  btn.classList.toggle('on');
  const sidebar = document.querySelector('.sidebar');
  if (btn.classList.contains('on')) {
    sidebar.style.width = '68px';
    document.querySelector('.main-content').style.marginLeft = '68px';
    sidebar.querySelectorAll('.nav-item span:not(.nav-icon),.logo-text,.nav-section-label,.city-status-pill span:not(.pulse)').forEach(e => e.style.display = 'none');
  } else {
    sidebar.style.width = '';
    document.querySelector('.main-content').style.marginLeft = '';
    sidebar.querySelectorAll('.nav-item span,.logo-text,.nav-section-label,.city-status-pill span').forEach(e => e.style.display = '');
  }
}

// ── Init ─────────────────────────────────────────────────────
document.addEventListener('DOMContentLoaded', () => {
  startClock();
  initSidebar();
  navigateTo('dashboard');
  initChatbot();
});


</body>
</html>

// ============================================================
//  SMART CITY — Chart.js Renderers (Local Data Only)
// ============================================================

function renderAllCharts() {
  renderTrafficChart();
  renderEnergyDonut();
  renderComplaintsBar();
  renderMultiLineChart();
}

// ── Shared Defaults ─────────────────────────────────────────
const CHART_DEFAULTS = {
  responsive: true,
  maintainAspectRatio: false,
  plugins: {
    legend: { labels: { color: '#94a3b8', font: { family: 'Outfit', size: 12 }, boxWidth: 12, padding: 16 } },
    tooltip: {
      backgroundColor: 'rgba(10,10,28,0.95)',
      borderColor: 'rgba(0,240,255,0.3)',
      borderWidth: 1,
      titleColor: '#00f0ff',
      bodyColor: '#e2e8f0',
      padding: 12,
      cornerRadius: 8
    }
  },
  scales: {
    x: { grid: { color: 'rgba(255,255,255,0.04)' }, ticks: { color: '#475569', font: { family: 'Outfit' } } },
    y: { grid: { color: 'rgba(255,255,255,0.04)' }, ticks: { color: '#475569', font: { family: 'Outfit' } } }
  }
};

// Active chart instances map (so we can destroy before re-render)
const CHARTS = {};

function destroyChart(id) {
  if (CHARTS[id]) { CHARTS[id].destroy(); delete CHARTS[id]; }
}

// ── 1. Traffic Line Chart ───────────────────────────────────
function renderTrafficChart() {
  const el = document.getElementById('trafficChart');
  if (!el) return;
  destroyChart('traffic');

  const gradient = el.getContext('2d').createLinearGradient(0, 0, 0, 220);
  gradient.addColorStop(0,   'rgba(0,240,255,0.3)');
  gradient.addColorStop(1,   'rgba(0,240,255,0)');

  CHARTS['traffic'] = new Chart(el, {
    type: 'line',
    data: {
      labels: CITY_DATA.charts.months,
      datasets: [{
        label: 'Traffic Flow %',
        data: CITY_DATA.charts.traffic,
        borderColor: '#00f0ff',
        backgroundColor: gradient,
        borderWidth: 2.5,
        pointBackgroundColor: '#00f0ff',
        pointRadius: 4,
        pointHoverRadius: 7,
        tension: 0.45,
        fill: true
      }]
    },
    options: {
      ...CHART_DEFAULTS,
      plugins: { ...CHART_DEFAULTS.plugins, legend: { display: false } },
      scales: {
        ...CHART_DEFAULTS.scales,
        y: { ...CHART_DEFAULTS.scales.y, min: 50, max: 100 }
      }
    }
  });
}

// ── 2. Energy Doughnut ──────────────────────────────────────
function renderEnergyDonut() {
  const el = document.getElementById('energyDonut');
  if (!el) return;
  destroyChart('energy');

  const { labels, values, colors } = CITY_DATA.charts.energySources;
  CHARTS['energy'] = new Chart(el, {
    type: 'doughnut',
    data: {
      labels,
      datasets: [{
        data: values,
        backgroundColor: colors.map(c => c + '99'),
        borderColor: colors,
        borderWidth: 2,
        hoverOffset: 10
      }]
    },
    options: {
      responsive: true,
      maintainAspectRatio: false,
      cutout: '68%',
      plugins: {
        legend: {
          position: 'right',
          labels: { color: '#94a3b8', font: { family: 'Outfit', size: 12 }, boxWidth: 10, padding: 12 }
        },
        tooltip: CHART_DEFAULTS.plugins.tooltip
      }
    }
  });
}

// ── 3. Complaints Bar Chart ─────────────────────────────────
function renderComplaintsBar() {
  const el = document.getElementById('complaintsBar');
  if (!el) return;
  destroyChart('complaints');

  const { labels, values, colors } = CITY_DATA.charts.complaintCategories;
  CHARTS['complaints'] = new Chart(el, {
    type: 'bar',
    data: {
      labels,
      datasets: [{
        label: 'Complaints',
        data: values,
        backgroundColor: colors.map(c => c + '66'),
        borderColor: colors,
        borderWidth: 2,
        borderRadius: 6,
        hoverBackgroundColor: colors.map(c => c + 'aa')
      }]
    },
    options: {
      ...CHART_DEFAULTS,
      plugins: { ...CHART_DEFAULTS.plugins, legend: { display: false } },
      scales: {
        ...CHART_DEFAULTS.scales,
        y: { ...CHART_DEFAULTS.scales.y, beginAtZero: true }
      }
    }
  });
}

// ── 4. Multi-Line Progress Chart ────────────────────────────
function renderMultiLineChart() {
  const el = document.getElementById('multiLineChart');
  if (!el) return;
  destroyChart('multi');

  const mkGrad = (ctx, color) => {
    const g = ctx.createLinearGradient(0, 0, 0, 200);
    g.addColorStop(0, color + '44'); g.addColorStop(1, color + '00'); return g;
  };
  const ctx = el.getContext('2d');

  CHARTS['multi'] = new Chart(el, {
    type: 'line',
    data: {
      labels: CITY_DATA.charts.months,
      datasets: [
        {
          label: 'Cleanliness',
          data: CITY_DATA.charts.cleanliness,
          borderColor: '#10b981', backgroundColor: mkGrad(ctx,'#10b981'),
          borderWidth: 2, pointRadius: 3, tension: 0.45, fill: true
        },
        {
          label: 'Energy Efficiency',
          data: CITY_DATA.charts.energy,
          borderColor: '#a855f7', backgroundColor: mkGrad(ctx,'#a855f7'),
          borderWidth: 2, pointRadius: 3, tension: 0.45, fill: true
        },
        {
          label: 'Traffic Flow',
          data: CITY_DATA.charts.traffic,
          borderColor: '#00f0ff', backgroundColor: mkGrad(ctx,'#00f0ff'),
          borderWidth: 2, pointRadius: 3, tension: 0.45, fill: true
        }
      ]
    },
    options: {
      ...CHART_DEFAULTS,
      scales: {
        ...CHART_DEFAULTS.scales,
        y: { ...CHART_DEFAULTS.scales.y, min: 40, max: 100 }
      }
    }
  });
}

