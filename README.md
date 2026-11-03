<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Oyaya Bet - Agent Portal</title>
  <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css" rel="stylesheet">
  <style>
    :root {
      --primary: #1e3a8a;
      --primary-dark: #172554;
      --secondary: #2563eb;
      --bg-light: #f8fafc;
      --card-bg: #ffffff;
      --text-main: #0f172a;
      --text-muted: #64748b;
      --border-color: #e2e8f0;
      --success: #16a34a;
      --warning: #d97706;
      --danger: #dc2626;
      --radius-sm: 6px;
      --radius-md: 10px;
      --radius-lg: 16px;
      --shadow-sm: 0 1px 2px 0 rgb(0 0 0 / 0.05);
      --shadow-md: 0 4px 6px -1px rgb(0 0 0 / 0.1);
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
    }

    body {
      background-color: var(--bg-light);
      color: var(--text-main);
      padding-bottom: 60px;
    }

    /* Top App Header */
    .app-header {
      background-color: var(--card-bg);
      border-bottom: 1px solid var(--border-color);
      position: sticky;
      top: 0;
      z-index: 50;
      box-shadow: var(--shadow-sm);
    }

    .header-content {
      max-width: 600px;
      margin: 0 auto;
      padding: 12px 16px;
      display: flex;
      align-items: center;
      justify-content: space-between;
    }

    .header-left {
      display: flex;
      align-items: center;
      gap: 12px;
    }

    .icon-btn {
      background: transparent;
      border: none;
      font-size: 20px;
      color: var(--text-main);
      cursor: pointer;
      padding: 4px;
      display: flex;
      align-items: center;
      justify-content: center;
    }

    .portal-title {
      font-size: 16px;
      font-weight: 600;
      color: var(--text-muted);
    }

    .header-right {
      display: flex;
      align-items: center;
      gap: 12px;
    }

    .balance-pill {
      display: flex;
      align-items: center;
      gap: 6px;
      background: #f1f5f9;
      padding: 6px 12px;
      border-radius: 20px;
      font-weight: 700;
      font-size: 14px;
      border: 1px solid var(--border-color);
    }

    .status-badge {
      display: flex;
      align-items: center;
      gap: 6px;
      font-size: 13px;
      font-weight: 600;
      color: var(--success);
      background: #dcfce7;
      padding: 4px 10px;
      border-radius: 14px;
    }

    .status-dot {
      width: 8px;
      height: 8px;
      background-color: var(--success);
      border-radius: 50%;
    }

    /* Drawer Menu */
    .drawer-overlay {
      position: fixed;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      background: rgba(0,0,0,0.5);
      z-index: 100;
      opacity: 0;
      pointer-events: none;
      transition: opacity 0.3s ease;
    }

    .drawer-overlay.active {
      opacity: 1;
      pointer-events: auto;
    }

    .drawer {
      position: fixed;
      top: 0;
      left: -280px;
      width: 280px;
      height: 100%;
      background: var(--card-bg);
      z-index: 101;
      transition: left 0.3s ease;
      display: flex;
      flex-direction: column;
      box-shadow: 4px 0 15px rgba(0,0,0,0.15);
    }

    .drawer.active {
      left: 0;
    }

    .drawer-header {
      padding: 20px 16px;
      border-bottom: 1px solid var(--border-color);
      display: flex;
      align-items: center;
      justify-content: space-between;
    }

    .drawer-brand {
      font-size: 20px;
      font-weight: 800;
      color: var(--primary);
    }

    .drawer-nav {
      padding: 12px 0;
      flex: 1;
      overflow-y: auto;
    }

    .drawer-item {
      display: flex;
      align-items: center;
      gap: 14px;
      padding: 14px 20px;
      color: #334155;
      font-weight: 500;
      font-size: 15px;
      cursor: pointer;
      text-decoration: none;
      transition: background 0.15s;
    }

    .drawer-item:hover, .drawer-item.active {
      background: #eff6ff;
      color: var(--secondary);
    }

    .drawer-item i {
      width: 20px;
      text-align: center;
      font-size: 18px;
    }

    .drawer-footer {
      padding: 16px;
      border-top: 1px solid var(--border-color);
    }

    /* Container */
    .container {
      max-width: 600px;
      margin: 0 auto;
      padding: 16px;
    }

    /* Tabs View */
    .tab-content {
      display: none;
    }

    .tab-content.active {
      display: block;
    }

    /* Card Component */
    .card {
      background: var(--card-bg);
      border-radius: var(--radius-md);
      border: 1px solid var(--border-color);
      padding: 16px;
      margin-bottom: 16px;
      box-shadow: var(--shadow-sm);
    }

    .card-header {
      display: flex;
      align-items: center;
      justify-content: space-between;
      margin-bottom: 14px;
    }

    .card-title {
      font-size: 16px;
      font-weight: 700;
      color: var(--text-main);
    }

    /* Controls & Forms */
    .form-group {
      margin-bottom: 14px;
    }

    .form-label {
      display: block;
      font-size: 13px;
      font-weight: 600;
      color: var(--text-muted);
      margin-bottom: 6px;
    }

    .form-control {
      width: 100%;
      padding: 10px 12px;
      border: 1px solid var(--border-color);
      border-radius: var(--radius-sm);
      font-size: 14px;
      background-color: #fff;
    }

    .form-control:focus {
      outline: none;
      border-color: var(--secondary);
    }

    .btn {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 8px;
      padding: 10px 16px;
      border-radius: var(--radius-sm);
      font-weight: 600;
      font-size: 14px;
      cursor: pointer;
      border: none;
      transition: opacity 0.2s;
      width: 100%;
    }

    .btn:hover {
      opacity: 0.9;
    }

    .btn-primary {
      background-color: var(--primary);
      color: white;
    }

    .btn-secondary {
      background-color: #e2e8f0;
      color: var(--text-main);
    }

    .btn-danger {
      background-color: var(--danger);
      color: white;
    }

    .btn-sm {
      padding: 6px 10px;
      font-size: 12px;
      width: auto;
    }

    /* Status cards & Stats */
    .stat-card {
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 14px;
      background: #ffffff;
      border: 1px solid var(--border-color);
      border-radius: var(--radius-md);
      margin-bottom: 12px;
    }

    .stat-info {
      display: flex;
      flex-direction: column;
    }

    .stat-label {
      font-size: 13px;
      color: var(--text-muted);
      font-weight: 500;
    }

    .stat-value {
      font-size: 18px;
      font-weight: 700;
      color: var(--text-main);
      margin-top: 2px;
    }

    .stat-sub {
      font-size: 12px;
      color: var(--text-muted);
    }

    .stat-icon {
      font-size: 22px;
    }

    /* Tables */
    .table-container {
      overflow-x: auto;
    }

    table {
      width: 100%;
      border-collapse: collapse;
      text-align: left;
      font-size: 13px;
    }

    th {
      background: #f8fafc;
      padding: 10px 12px;
      color: var(--text-muted);
      font-weight: 600;
      border-bottom: 1px solid var(--border-color);
      white-space: nowrap;
    }

    td {
      padding: 12px;
      border-bottom: 1px solid var(--border-color);
      white-space: nowrap;
    }

    .badge-status {
      padding: 3px 8px;
      border-radius: 12px;
      font-size: 11px;
      font-weight: 700;
    }

    .badge-active { background: #dcfce7; color: #15803d; }
    .badge-inactive { background: #fee2e2; color: #b91c1c; }

    /* Modal */
    .modal-backdrop {
      position: fixed;
      top: 0; left: 0; right: 0; bottom: 0;
      background: rgba(0,0,0,0.5);
      z-index: 200;
      display: none;
      align-items: center;
      justify-content: center;
      padding: 16px;
    }

    .modal-backdrop.active {
      display: flex;
    }

    .modal {
      background: white;
      border-radius: var(--radius-md);
      width: 100%;
      max-width: 440px;
      box-shadow: 0 10px 25px rgba(0,0,0,0.2);
      overflow: hidden;
    }

    .modal-header {
      padding: 14px 16px;
      border-bottom: 1px solid var(--border-color);
      display: flex;
      justify-content: space-between;
      align-items: center;
    }

    .modal-title { font-weight: 700; font-size: 16px; }

    .modal-body { padding: 16px; }
    
    .modal-footer {
      padding: 12px 16px;
      background: #f8fafc;
      border-top: 1px solid var(--border-color);
      display: flex;
      gap: 10px;
      justify-content: flex-end;
    }

    .empty-state {
      text-align: center;
      padding: 32px 16px;
      color: var(--text-muted);
    }
  </style>
</head>
<body>

  <!-- Top Navigation Header -->
  <header class="app-header">
    <div class="header-content">
      <div class="header-left">
        <button class="icon-btn" id="menuToggle"><i class="fa-solid fa-bars"></i></button>
        <span class="portal-title">agent-portal</span>
      </div>
      <div class="header-right">
        <div class="balance-pill">
          <i class="fa-regular fa-envelope" style="color:#64748b;"></i>
          <span>ETB 0.00</span>
          <i class="fa-solid fa-caret-down" style="font-size: 10px; color:#64748b;"></i>
        </div>
        <div class="status-badge">
          <span class="status-dot"></span>
          <span>Active</span>
        </div>
      </div>
    </div>
  </header>

  <!-- Navigation Drawer -->
  <div class="drawer-overlay" id="drawerOverlay"></div>
  <aside class="drawer" id="drawer">
    <div class="drawer-header">
      <span class="drawer-brand">Oyaya Bet</span>
      <button class="icon-btn" id="drawerClose"><i class="fa-solid fa-xmark"></i></button>
    </div>
    <nav class="drawer-nav">
      <a class="drawer-item active" data-target="payment-requests">
        <i class="fa-solid fa-credit-card"></i>
        <span>Payment Requests</span>
      </a>
      <a class="drawer-item" data-target="sms-verification">
        <i class="fa-solid fa-message"></i>
        <span>SMS Verification</span>
      </a>
      <a class="drawer-item" data-target="banks">
        <i class="fa-solid fa-building-columns"></i>
        <span>Banks</span>
      </a>
      <a class="drawer-item" data-target="achievements">
        <i class="fa-solid fa-trophy"></i>
        <span>Achievements</span>
      </a>
      <a class="drawer-item" data-target="reports">
        <i class="fa-solid fa-chart-line"></i>
        <span>Reports</span>
      </a>
      <a class="drawer-item" data-target="account">
        <i class="fa-regular fa-user"></i>
        <span>Account</span>
      </a>
    </nav>
    <div class="drawer-footer">
      <a class="drawer-item" style="color: var(--danger);">
        <i class="fa-solid fa-right-from-bracket"></i>
        <span>Logout</span>
      </a>
    </div>
  </aside>

  <!-- Main Content Container -->
  <main class="container">

    <!-- TAB 1: PAYMENT REQUESTS -->
    <section id="payment-requests" class="tab-content active">
      <div class="card">
        <div class="card-header">
          <span class="card-title">Payment Requests</span>
        </div>
        <div class="form-group">
          <input type="text" class="form-control" placeholder="Player / phone">
        </div>
        <div class="form-group">
          <select class="form-control">
            <option>All methods</option>
          </select>
        </div>
        <div class="form-group">
          <select class="form-control">
            <option>Select payment method first</option>
          </select>
        </div>
        <div class="form-group">
          <select class="form-control">
            <option>All types</option>
            <option>Deposit</option>
            <option>Withdraw</option>
          </select>
        </div>
        <div class="form-group">
          <select class="form-control">
            <option>All request statuses</option>
            <option>Pending</option>
            <option>Successful</option>
            <option>Failed</option>
          </select>
        </div>
        <div class="form-group" style="display: flex; gap: 8px;">
          <input type="text" class="form-control" value="11/03/2026">
          <input type="text" class="form-control" value="11/03/2026">
        </div>
        <div class="form-group">
          <select class="form-control">
            <option>Today</option>
            <option>This Week</option>
            <option>Last Week</option>
            <option>This Month</option>
          </select>
        </div>
        <div style="display: flex; gap: 10px;">
          <button class="btn btn-primary"><i class="fa-solid fa-magnifying-glass"></i> Search</button>
          <button class="btn btn-secondary" style="width: auto;"><i class="fa-solid fa-rotate"></i></button>
        </div>
      </div>

      <!-- Summary Section -->
      <div class="card">
        <div class="card-header">
          <span class="card-title">Summary</span>
          <i class="fa-solid fa-angle-up"></i>
        </div>
        
        <div class="stat-card">
          <div class="stat-info">
            <span class="stat-label">Successful</span>
            <span class="stat-value">0</span>
            <span class="stat-sub"># 0.00</span>
          </div>
          <i class="fa-solid fa-check stat-icon" style="color: var(--success);"></i>
        </div>

        <div class="stat-card">
          <div class="stat-info">
            <span class="stat-label">Pending</span>
            <span class="stat-value">0</span>
            <span class="stat-sub"># 0.00</span>
          </div>
          <i class="fa-regular fa-circle stat-icon" style="color: var(--warning);"></i>
        </div>

        <div class="stat-card">
          <div class="stat-info">
            <span class="stat-label">Failed</span>
            <span class="stat-value">0</span>
            <span class="stat-sub"># 0.00</span>
          </div>
          <i class="fa-solid fa-xmark stat-icon" style="color: var(--danger);"></i>
        </div>
      </div>

      <div class="empty-state card">
        No transactions found
      </div>
    </section>

    <!-- TAB 2: SMS VERIFICATION -->
    <section id="sms-verification" class="tab-content">
      <div class="card">
        <div class="card-header">
          <span class="card-title">SMS Verification</span>
        </div>
        <div class="form-group">
          <label class="form-label">SMS content</label>
          <textarea class="form-control" rows="4" placeholder="Paste your bank SMS notification here..."></textarea>
        </div>
        <div class="form-group" style="display: flex; align-items: center; justify-content: space-between;">
          <span class="form-label" style="margin: 0;">Auto-approve if amount matches</span>
          <input type="checkbox" checked style="width: 18px; height: 18px;">
        </div>
        <button class="btn btn-primary">Verify SMS</button>
      </div>
    </section>

    <!-- TAB 3: BANKS & WALLETS -->
    <section id="banks" class="tab-content">
      <div class="card">
        <div class="card-header">
          <span class="card-title">Banks & Wallets</span>
          <button class="btn btn-primary btn-sm" id="openAttachBankModal">
            <i class="fa-solid fa-plus"></i> Attach Bank
          </button>
        </div>
        <div class="table-container">
          <table>
            <thead>
              <tr>
                <th>PAYMENT METHOD</th>
                <th>ACCOUNT NUMBER</th>
                <th>ACCOUNT NAME</th>
                <th>DIRECTION</th>
                <th>STATUS</th>
                <th>BALANCE</th>
                <th>ACTIONS</th>
              </tr>
            </thead>
            <tbody id="bankTableBody">
              <!-- Dynamically rendered -->
            </tbody>
          </table>
        </div>
      </div>
    </section>

    <!-- TAB 4: ACHIEVEMENTS -->
    <section id="achievements" class="tab-content">
      <div class="card">
        <div class="card-header">
          <span class="card-title">Achievements</span>
        </div>
        <div style="display: flex; gap: 8px; border-bottom: 1px solid var(--border-color); padding-bottom: 10px; margin-bottom: 16px;">
          <button class="btn btn-secondary btn-sm" style="background:#e2e8f0;">Statistics</button>
          <button class="btn btn-secondary btn-sm" style="background:transparent;">Available</button>
          <button class="btn btn-secondary btn-sm" style="background:transparent;">Unlocked</button>
        </div>
        <div class="empty-state">
          <i class="fa-solid fa-trophy" style="font-size: 40px; color: #cbd5e1; margin-bottom: 12px;"></i>
          <p style="font-weight: 600; color: #475569;">Achievements are not enabled</p>
        </div>
      </div>
    </section>

    <!-- TAB 5: REPORTS -->
    <section id="reports" class="tab-content">
      <div class="card">
        <div class="card-header">
          <span class="card-title">Summary by period</span>
        </div>
        <div class="form-group">
          <label class="form-label">Start Date</label>
          <input type="text" class="form-control" value="11/01/2026">
        </div>
        <div class="form-group">
          <label class="form-label">End Date</label>
          <input type="text" class="form-control" value="11/03/2026">
        </div>
        <div class="form-group">
          <label class="form-label">Quick Range</label>
          <select class="form-control">
            <option>Quick Date Range</option>
            <option>Today</option>
            <option>This Week</option>
            <option>Last Month</option>
          </select>
        </div>
        <button class="btn btn-primary"><i class="fa-solid fa-magnifying-glass"></i> Search</button>
      </div>

      <div class="card">
        <div class="stat-card">
          <div class="stat-info">
            <span class="stat-label">Successful Deposits</span>
            <span class="stat-value">0</span>
            <span class="stat-sub"># 0.00</span>
          </div>
          <i class="fa-solid fa-circle-arrow-down stat-icon" style="color: var(--success);"></i>
        </div>

        <div class="stat-card">
          <div class="stat-info">
            <span class="stat-label">Successful Withdrawals</span>
            <span class="stat-value">0</span>
            <span class="stat-sub"># 0.00</span>
          </div>
          <i class="fa-solid fa-circle-arrow-up stat-icon" style="color: var(--secondary);"></i>
        </div>

        <div class="stat-card">
          <div class="stat-info">
            <span class="stat-label">Total Commission</span>
            <span class="stat-value"># 0.00</span>
          </div>
          <i class="fa-solid fa-money-bill-wave stat-icon" style="color: var(--primary);"></i>
        </div>
      </div>
    </section>

    <!-- TAB 6: ACCOUNT -->
    <section id="account" class="tab-content">
      <div class="card">
        <div class="card-header">
          <span class="card-title"><i class="fa-regular fa-clock"></i> Attendance</span>
        </div>
        <div style="background: #f0fdf4; border: 1px solid #bbf7d0; padding: 12px; border-radius: 8px; margin-bottom: 12px;">
          <span style="font-size: 11px; text-transform: uppercase; color: #166534; font-weight: 700;">CURRENT STATUS</span>
          <div style="font-weight: 700; color: #15803d; font-size: 16px; margin-top: 2px;">Clocked in</div>
        </div>
        <div style="font-size: 12px; color: var(--text-muted); margin-bottom: 12px;">
          <div>Last clocked in at: 10/28/26, 6:01 PM</div>
          <div>Last clocked out at: 10/28/26, 5:48 PM</div>
        </div>
        <div style="display: flex; gap: 8px;">
          <button class="btn btn-secondary btn-sm"><i class="fa-solid fa-right-from-bracket"></i> Clock Out</button>
          <button class="btn btn-secondary btn-sm"><i class="fa-solid fa-rotate"></i> Refresh</button>
        </div>
      </div>

      <div class="card">
        <div class="card-header">
          <span class="card-title">Wallet Balances</span>
        </div>
        <div style="font-size: 13px; color: var(--text-muted);">ETB</div>
        <div style="font-size: 22px; font-weight: 800; margin-bottom: 16px;">0.00</div>

        <div class="stat-card">
          <div class="stat-info">
            <span class="stat-label">Score</span>
            <span class="stat-value">0/100</span>
          </div>
          <i class="fa-solid fa-clipboard-list stat-icon" style="color: var(--secondary);"></i>
        </div>

        <div class="stat-card">
          <div class="stat-info">
            <span class="stat-label">Referrals</span>
            <span class="stat-value">0</span>
          </div>
          <i class="fa-solid fa-users stat-icon" style="color: var(--primary);"></i>
        </div>

        <div class="stat-card">
          <div class="stat-info">
            <span class="stat-label">Completed Requests</span>
            <span class="stat-value">0</span>
          </div>
          <i class="fa-solid fa-square-check stat-icon" style="color: var(--success);"></i>
        </div>
      </div>
    </section>

  </main>

  <!-- Modal for Attach/Edit Bank -->
  <div class="modal-backdrop" id="bankModal">
    <div class="modal">
      <div class="modal-header">
        <span class="modal-title" id="bankModalTitle">Attach Bank</span>
        <button class="icon-btn" id="closeBankModal"><i class="fa-solid fa-xmark"></i></button>
      </div>
      <div class="modal-body">
        <form id="bankForm">
          <input type="hidden" id="editIndex" value="-1">
          <div class="form-group">
            <label class="form-label">Payment Method</label>
            <select class="form-control" id="modalMethod">
              <option value="telebirr">telebirr</option>
              <option value="Commercial Bank of Ethiopia">Commercial Bank of Ethiopia</option>
              <option value="Bank of Abyssinia">Bank of Abyssinia</option>
            </select>
          </div>
          <div class="form-group">
            <label class="form-label">Account Number</label>
            <input type="text" class="form-control" id="modalAccNum" placeholder="e.g. 0912345678" required>
          </div>
          <div class="form-group">
            <label class="form-label">Account Name</label>
            <input type="text" class="form-control" id="modalAccName" placeholder="e.g. Abebe Bikila" required>
          </div>
          <div class="form-group">
            <label class="form-label">Direction</label>
            <select class="form-control" id="modalDirection">
              <option value="Deposit">Deposit</option>
              <option value="Withdrawal">Withdrawal</option>
            </select>
          </div>
          <div class="form-group">
            <label class="form-label">Status</label>
            <select class="form-control" id="modalStatus">
              <option value="Active">Active</option>
              <option value="Inactive">Inactive</option>
            </select>
          </div>
        </form>
      </div>
      <div class="modal-footer">
        <button class="btn btn-secondary btn-sm" id="cancelBankModal">Cancel</button>
        <button class="btn btn-primary btn-sm" id="saveBankBtn">Save Account</button>
      </div>
    </div>
  </div>

  <script>
    // Navigation Drawer Logic
    const menuToggle = document.getElementById('menuToggle');
    const drawer = document.getElementById('drawer');
    const drawerOverlay = document.getElementById('drawerOverlay');
    const drawerClose = document.getElementById('drawerClose');

    function openDrawer() {
      drawer.classList.add('active');
      drawerOverlay.classList.add('active');
    }

    function closeDrawer() {
      drawer.classList.remove('active');
      drawerOverlay.classList.remove('active');
    }

    menuToggle.addEventListener('click', openDrawer);
    drawerClose.addEventListener('click', closeDrawer);
    drawerOverlay.addEventListener('click', closeDrawer);

    // Tab Switching Logic
    const drawerItems = document.querySelectorAll('.drawer-item[data-target]');
    const tabContents = document.querySelectorAll('.tab-content');

    drawerItems.forEach(item => {
      item.addEventListener('click', () => {
        const target = item.getAttribute('data-target');
        
        drawerItems.forEach(i => i.classList.remove('active'));
        item.classList.add('active');

        tabContents.forEach(tab => {
          if (tab.id === target) {
            tab.classList.add('active');
          } else {
            tab.classList.remove('active');
          }
        });

        closeDrawer();
      });
    });

    // Bank Accounts Data State (Starts Completely Empty)
    let bankAccounts = [];

    const bankTableBody = document.getElementById('bankTableBody');
    const bankModal = document.getElementById('bankModal');
    const openAttachBankModal = document.getElementById('openAttachBankModal');
    const closeBankModal = document.getElementById('closeBankModal');
    const cancelBankModal = document.getElementById('cancelBankModal');
    const saveBankBtn = document.getElementById('saveBankBtn');
    const bankForm = document.getElementById('bankForm');

    function renderBankTable() {
      bankTableBody.innerHTML = '';
      if (bankAccounts.length === 0) {
        bankTableBody.innerHTML = `
          <tr>
            <td colspan="7" style="text-align: center; color: var(--text-muted); padding: 24px;">
              No bank accounts configured. Click "Attach Bank" to add one.
            </td>
          </tr>
        `;
        return;
      }

      bankAccounts.forEach((acc, idx) => {
        const tr = document.createElement('tr');
        const badgeClass = acc.status === 'Active' ? 'badge-active' : 'badge-inactive';
        
        tr.innerHTML = `
          <td><strong>${acc.method}</strong></td>
          <td>${acc.accNum}</td>
          <td>${acc.accName}</td>
          <td>${acc.direction}</td>
          <td><span class="badge-status ${badgeClass}">${acc.status}</span></td>
          <td>0.00 ETB</td>
          <td style="display: flex; gap: 6px;">
            <button class="btn btn-secondary btn-sm" onclick="editAccount(${idx})"><i class="fa-solid fa-pen"></i></button>
            <button class="btn btn-secondary btn-sm" onclick="toggleStatus(${idx})"><i class="fa-solid fa-power-off"></i></button>
            <button class="btn btn-danger btn-sm" onclick="deleteAccount(${idx})"><i class="fa-solid fa-trash"></i></button>
          </td>
        `;
        bankTableBody.appendChild(tr);
      });
    }

    function showModal(isEdit = false) {
      document.getElementById('bankModalTitle').innerText = isEdit ? 'Edit Bank Account' : 'Attach Bank';
      bankModal.classList.add('active');
    }

    function hideModal() {
      bankModal.classList.remove('active');
      bankForm.reset();
      document.getElementById('editIndex').value = "-1";
    }

    openAttachBankModal.addEventListener('click', () => {
      showModal(false);
    });

    closeBankModal.addEventListener('click', hideModal);
    cancelBankModal.addEventListener('click', hideModal);

    saveBankBtn.addEventListener('click', (e) => {
      e.preventDefault();
      const method = document.getElementById('modalMethod').value;
      const accNum = document.getElementById('modalAccNum').value;
      const accName = document.getElementById('modalAccName').value;
      const direction = document.getElementById('modalDirection').value;
      const status = document.getElementById('modalStatus').value;
      const editIndex = parseInt(document.getElementById('editIndex').value);

      if (!accNum || !accName) {
        alert('Please fill out account number and account name');
        return;
      }

      if (editIndex >= 0) {
        bankAccounts[editIndex] = { method, accNum, accName, direction, status };
      } else {
        bankAccounts.push({ method, accNum, accName, direction, status });
      }

      renderBankTable();
      hideModal();
    });

    window.editAccount = function(idx) {
      const acc = bankAccounts[idx];
      document.getElementById('modalMethod').value = acc.method;
      document.getElementById('modalAccNum').value = acc.accNum;
      document.getElementById('modalAccName').value = acc.accName;
      document.getElementById('modalDirection').value = acc.direction;
      document.getElementById('modalStatus').value = acc.status;
      document.getElementById('editIndex').value = idx;
      showModal(true);
    };

    window.toggleStatus = function(idx) {
      bankAccounts[idx].status = bankAccounts[idx].status === 'Active' ? 'Inactive' : 'Active';
      renderBankTable();
    };

    window.deleteAccount = function(idx) {
      if (confirm('Are you sure you want to remove this account?')) {
        bankAccounts.splice(idx, 1);
        renderBankTable();
      }
    };

    // Initial Render
    renderBankTable();
  </script>
</body>
</html>
