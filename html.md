<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">
    <title>Aplikasi Kas | Manajemen Keuangan</title>
    <!-- Font Awesome 6 (Free) -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <!-- Google Fonts: Inter -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,300;14..32,400;14..32,500;14..32,600;14..32,700&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Inter', sans-serif;
            background: #f4f7fc;
            color: #1e293b;
            line-height: 1.5;
        }

        /* Layout Utama */
        .app-container {
            display: flex;
            min-height: 100vh;
        }

        /* ========= SIDEBAR ========= */
        .sidebar {
            width: 280px;
            background: linear-gradient(180deg, #0f2b3d 0%, #0a1e2c 100%);
            color: #e2e8f0;
            flex-shrink: 0;
            transition: all 0.2s;
            box-shadow: 2px 0 12px rgba(0,0,0,0.05);
        }

        .logo-area {
            padding: 28px 24px;
            border-bottom: 1px solid #2d4a6e;
        }

        .logo-area h2 {
            font-size: 1.6rem;
            font-weight: 600;
            letter-spacing: -0.3px;
            color: white;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .logo-area h2 i {
            color: #3b82f6;
            font-size: 1.8rem;
        }

        .nav-menu {
            padding: 24px 16px;
            display: flex;
            flex-direction: column;
            gap: 8px;
        }

        .nav-group {
            margin-bottom: 8px;
        }

        .nav-group-title {
            font-size: 0.75rem;
            text-transform: uppercase;
            letter-spacing: 1px;
            font-weight: 600;
            color: #7e9cb0;
            padding: 8px 12px;
            margin-top: 12px;
        }

        .nav-item {
            display: flex;
            align-items: center;
            gap: 12px;
            padding: 10px 16px;
            border-radius: 12px;
            color: #cbd5e1;
            font-weight: 500;
            transition: all 0.2s;
            cursor: pointer;
        }

        .nav-item i {
            width: 24px;
            font-size: 1.2rem;
            text-align: center;
        }

        .nav-item:hover {
            background: #1f3e55;
            color: white;
        }

        .nav-item.active {
            background: #2563eb;
            color: white;
            box-shadow: 0 6px 12px -6px rgba(37,99,235,0.3);
        }

        /* ========= MAIN PANEL ========= */
        .main-content {
            flex: 1;
            display: flex;
            flex-direction: column;
            overflow-x: auto;
        }

        .topbar {
            background: white;
            padding: 16px 32px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-bottom: 1px solid #e2edf2;
            box-shadow: 0 1px 2px rgba(0,0,0,0.02);
        }

        .page-title {
            font-size: 1.5rem;
            font-weight: 600;
            color: #0f2b3d;
        }

        .user-badge {
            display: flex;
            align-items: center;
            gap: 12px;
            background: #f1f5f9;
            padding: 6px 16px;
            border-radius: 40px;
        }

        .user-badge i {
            font-size: 1.2rem;
            color: #3b82f6;
        }

        /* konten dinamis */
        .content-pane {
            padding: 28px 32px;
            background: #f4f7fc;
            flex: 1;
        }

        /* kartu & tabel */
        .card {
            background: white;
            border-radius: 24px;
            box-shadow: 0 8px 20px rgba(0,0,0,0.03), 0 2px 4px rgba(0,0,0,0.05);
            padding: 20px 24px;
            margin-bottom: 28px;
        }

        .card-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
            flex-wrap: wrap;
            gap: 12px;
            border-bottom: 1px solid #eef2f6;
            padding-bottom: 12px;
        }

        .card-header h3 {
            font-size: 1.3rem;
            font-weight: 600;
        }

        .btn {
            border: none;
            background: #2563eb;
            color: white;
            padding: 8px 18px;
            border-radius: 40px;
            font-weight: 500;
            font-size: 0.85rem;
            display: inline-flex;
            align-items: center;
            gap: 8px;
            cursor: pointer;
            transition: 0.2s;
        }

        .btn-outline {
            background: transparent;
            border: 1px solid #cbd5e1;
            color: #1e293b;
        }

        .btn-outline:hover {
            background: #f1f5f9;
        }

        .btn-danger {
            background: #dc2626;
        }

        table {
            width: 100%;
            border-collapse: collapse;
        }

        th, td {
            text-align: left;
            padding: 12px 8px;
            border-bottom: 1px solid #eef2f6;
        }

        th {
            font-weight: 600;
            color: #475569;
            font-size: 0.85rem;
        }

        .badge-admin {
            background: #dbeafe;
            color: #1e40af;
            padding: 4px 12px;
            border-radius: 40px;
            font-size: 0.75rem;
            font-weight: 600;
        }

        .badge-user {
            background: #e2e8f0;
            color: #334155;
        }

        .pagination-info {
            margin-top: 20px;
            font-size: 0.85rem;
            color: #475569;
        }

        .form-row {
            display: flex;
            flex-wrap: wrap;
            gap: 16px;
            margin-bottom: 18px;
        }

        .form-group {
            flex: 1;
            min-width: 180px;
        }

        label {
            font-weight: 500;
            font-size: 0.8rem;
            display: block;
            margin-bottom: 6px;
            color: #334155;
        }

        input, select {
            width: 100%;
            padding: 10px 14px;
            border-radius: 14px;
            border: 1px solid #cbd5e6;
            background: white;
            font-family: inherit;
        }

        .alert {
            background: #e6f7e6;
            border-left: 4px solid #22c55e;
            padding: 12px 16px;
            border-radius: 16px;
            margin-bottom: 24px;
        }

        /* statistik ringkasan dashboard */
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
            gap: 20px;
            margin-bottom: 30px;
        }

        .stat-card {
            background: white;
            border-radius: 24px;
            padding: 20px;
            box-shadow: 0 2px 6px rgba(0,0,0,0.03);
            border: 1px solid #e9edf2;
        }

        .stat-title {
            font-size: 0.8rem;
            text-transform: uppercase;
            color: #5b6e8c;
        }

        .stat-value {
            font-size: 1.9rem;
            font-weight: 700;
            margin-top: 8px;
        }

        hr {
            margin: 16px 0;
        }

        @media (max-width: 768px) {
            .sidebar {
                width: 80px;
                overflow-x: hidden;
            }
            .sidebar .logo-area h2 span, .sidebar .nav-item span {
                display: none;
            }
            .sidebar .nav-item i {
                margin-right: 0;
            }
            .content-pane {
                padding: 20px;
            }
        }
    </style>
</head>
<body>
<div class="app-container">
    <!-- SIDEBAR -->
    <div class="sidebar">
        <div class="logo-area">
            <h2><i class="fas fa-wallet"></i> <span>KasApp</span></h2>
        </div>
        <div class="nav-menu">
            <div class="nav-group">
                <div class="nav-group-title">DASHBOARD</div>
                <div class="nav-item active" data-module="dashboard">
                    <i class="fas fa-chart-line"></i> <span>Dashboard</span>
                </div>
            </div>
            <div class="nav-group">
                <div class="nav-group-title">TRANSAKSI</div>
                <div class="nav-item" data-module="pemasukan">
                    <i class="fas fa-arrow-down"></i> <span>Pemasukan</span>
                </div>
                <div class="nav-item" data-module="pengeluaran">
                    <i class="fas fa-arrow-up"></i> <span>Pengeluaran</span>
                </div>
            </div>
            <div class="nav-group">
                <div class="nav-group-title">REFERENSI</div>
                <div class="nav-item" data-module="kategori">
                    <i class="fas fa-tags"></i> <span>Kategori</span>
                </div>
            </div>
            <div class="nav-group">
                <div class="nav-group-title">LAPORAN</div>
                <div class="nav-item" data-module="laporan-pemasukan">
                    <i class="fas fa-file-invoice"></i> <span>Laporan Pemasukan</span>
                </div>
                <div class="nav-item" data-module="laporan-pengeluaran">
                    <i class="fas fa-file-invoice-dollar"></i> <span>Laporan Pengeluaran</span>
                </div>
                <div class="nav-item" data-module="laporan-rekap">
                    <i class="fas fa-chart-pie"></i> <span>Rekapitulasi</span>
                </div>
            </div>
            <div class="nav-group">
                <div class="nav-group-title">PENGATURAN</div>
                <div class="nav-item" data-module="user">
                    <i class="fas fa-users-gear"></i> <span>Manajemen User</span>
                </div>
            </div>
        </div>
    </div>

    <!-- MAIN RIGHT -->
    <div class="main-content">
        <div class="topbar">
            <div class="page-title" id="pageTitle">Dashboard</div>
            <div class="user-badge">
                <i class="fas fa-user-circle"></i>
                <span>Admin</span>
            </div>
        </div>
        <div class="content-pane" id="dynamicContent">
            <!-- konten akan diisi JS -->
            <div style="text-align:center; padding: 40px;">Memuat...</div>
        </div>
    </div>
</div>

<script>
    // ----------------------------- DATA DUMMY (seperti database) -------------------------
    // Data Kategori (Referensi)
    let categories = [
        { id: 1, name: "Gaji" },
        { id: 2, name: "Bonus" },
        { id: 3, name: "Investasi" },
        { id: 4, name: "Makanan" },
        { id: 5, name: "Transport" },
        { id: 6, name: "Tagihan" }
    ];

    // Data Transaksi pemasukan & pengeluaran
    let transactions = {
        income: [
            { id: 1, date: "2025-05-01", description: "Gaji bulan Mei", amount: 5500000, category: "Gaji" },
            { id: 2, date: "2025-05-10", description: "Freelance", amount: 1200000, category: "Bonus" },
            { id: 3, date: "2025-05-15", description: "Dividen", amount: 300000, category: "Investasi" }
        ],
        expense: [
            { id: 1, date: "2025-05-02", description: "Makan Siang", amount: 75000, category: "Makanan" },
            { id: 2, date: "2025-05-05", description: "Bensin", amount: 100000, category: "Transport" },
            { id: 3, date: "2025-05-12", description: "Listrik", amount: 250000, category: "Tagihan" }
        ]
    };

    // Data User (Manajemen User) sesuai contoh: test, User, Admin
    let users = [
        { id: 1, nama: "test", username: "test", role: "User" },
        { id: 2, nama: "User", username: "user", role: "User" },
        { id: 3, nama: "Admin", username: "admin", role: "Admin" }
    ];

    let nextUserId = 4;

    // Helper render: update UI berdasarkan module
    function renderModule(moduleId) {
        const container = document.getElementById('dynamicContent');
        const titleElem = document.getElementById('pageTitle');

        // update aktif sidebar
        document.querySelectorAll('.nav-item').forEach(item => {
            if(item.getAttribute('data-module') === moduleId) {
                item.classList.add('active');
            } else {
                item.classList.remove('active');
            }
        });

        if(moduleId === 'dashboard') {
            titleElem.innerText = 'Dashboard';
            renderDashboard(container);
        }
        else if(moduleId === 'pemasukan') {
            titleElem.innerText = 'Transaksi Pemasukan';
            renderIncome(container);
        }
        else if(moduleId === 'pengeluaran') {
            titleElem.innerText = 'Transaksi Pengeluaran';
            renderExpense(container);
        }
        else if(moduleId === 'kategori') {
            titleElem.innerText = 'Referensi Kategori';
            renderCategories(container);
        }
        else if(moduleId === 'laporan-pemasukan') {
            titleElem.innerText = 'Laporan Pemasukan';
            renderReportIncome(container);
        }
        else if(moduleId === 'laporan-pengeluaran') {
            titleElem.innerText = 'Laporan Pengeluaran';
            renderReportExpense(container);
        }
        else if(moduleId === 'laporan-rekap') {
            titleElem.innerText = 'Laporan Rekapitulasi';
            renderRecap(container);
        }
        else if(moduleId === 'user') {
            titleElem.innerText = 'Manajemen User';
            renderUserManagement(container);
        }
    }

    // ---------- DASHBOARD (Ringkasan) ----------
    function renderDashboard(container) {
        let totalIncome = transactions.income.reduce((sum, t) => sum + t.amount, 0);
        let totalExpense = transactions.expense.reduce((sum, t) => sum + t.amount, 0);
        let balance = totalIncome - totalExpense;
        let recentInc = [...transactions.income].reverse().slice(0,3);
        let recentExp = [...transactions.expense].reverse().slice(0,3);
        container.innerHTML = `
            <div class="stats-grid">
                <div class="stat-card"><div class="stat-title">Total Pemasukan</div><div class="stat-value">Rp ${formatRupiah(totalIncome)}</div></div>
                <div class="stat-card"><div class="stat-title">Total Pengeluaran</div><div class="stat-value">Rp ${formatRupiah(totalExpense)}</div></div>
                <div class="stat-card"><div class="stat-title">Saldo Kas</div><div class="stat-value" style="color:${balance>=0?'#16a34a':'#dc2626'}">Rp ${formatRupiah(balance)}</div></div>
            </div>
            <div class="card">
                <div class="card-header"><h3>📥 Transaksi Pemasukan Terbaru</h3></div>
                ${renderMiniTable(recentInc, 'income')}
            </div>
            <div class="card">
                <div class="card-header"><h3>📤 Transaksi Pengeluaran Terbaru</h3></div>
                ${renderMiniTable(recentExp, 'expense')}
            </div>
        `;
    }

    function renderMiniTable(data, type) {
        if(data.length===0) return '<p>Tidak ada transaksi.</p>';
        return `<table><thead><tr><th>Tanggal</th><th>Deskripsi</th><th>Kategori</th><th>Jumlah</th></tr></thead><tbody>
            ${data.map(t => `<tr><td>${t.date}</td><td>${t.description}</td><td>${t.category}</td><td class="${type==='income'?'':'text-danger'}" style="color:${type==='income'?'#16a34a':'#dc2626'}">${type==='income'?'+':'-'} Rp ${formatRupiah(t.amount)}</td></tr>`).join('')}
        </tbody></table>`;
    }

    // ---------- PEMASUKAN ----------
    function renderIncome(container) {
        let incomeList = [...transactions.income];
        container.innerHTML = `
            <div class="card">
                <div class="card-header"><h3>📥 Data Pemasukan</h3><button class="btn" id="btnTambahIncome"><i class="fas fa-plus"></i> Tambah Pemasukan</button></div>
                <div id="incomeFormContainer" style="display:none; margin-bottom:20px;"></div>
                <table id="incomeTable">
                    <thead><tr><th>Tanggal</th><th>Deskripsi</th><th>Kategori</th><th>Jumlah</th><th>Aksi</th></tr></thead>
                    <tbody>${incomeList.map(inc => `<tr><td>${inc.date}</td><td>${inc.description}</td><td>${inc.category}</td><td>Rp ${formatRupiah(inc.amount)}</td><td><button class="btn-outline btn-sm" data-delete-income="${inc.id}">Hapus</button></td></tr>`).join('')}</tbody>
                </table>
            </div>
        `;
        document.getElementById('btnTambahIncome')?.addEventListener('click', () => {
            const formDiv = document.getElementById('incomeFormContainer');
            formDiv.style.display = 'block';
            formDiv.innerHTML = getIncomeFormHtml();
            document.getElementById('saveIncomeBtn')?.addEventListener('click', () => {
                const date = document.getElementById('incDate').value;
                const desc = document.getElementById('incDesc').value;
                const amount = parseInt(document.getElementById('incAmount').value);
                const cat = document.getElementById('incCategory').value;
                if(date && desc && amount && cat) {
                    const newId = transactions.income.length+1;
                    transactions.income.push({ id: newId, date, description: desc, amount, category: cat });
                    renderIncome(container);
                } else alert("Isi semua data!");
            });
        });
        document.querySelectorAll('[data-delete-income]').forEach(btn => {
            btn.addEventListener('click', (e) => {
                let id = parseInt(btn.getAttribute('data-delete-income'));
                transactions.income = transactions.income.filter(i => i.id !== id);
                renderIncome(container);
            });
        });
    }

    function getIncomeFormHtml() {
        const catOptions = categories.map(c => `<option value="${c.name}">${c.name}</option>`).join('');
        return `<div class="form-row"><div class="form-group"><label>Tanggal</label><input type="date" id="incDate" value="${new Date().toISOString().slice(0,10)}"></div>
        <div class="form-group"><label>Deskripsi</label><input id="incDesc" placeholder="Deskripsi"></div>
        <div class="form-group"><label>Kategori</label><select id="incCategory">${catOptions}</select></div>
        <div class="form-group"><label>Jumlah (Rp)</label><input type="number" id="incAmount" placeholder="0"></div></div>
        <div><button class="btn" id="saveIncomeBtn">Simpan</button> <button class="btn-outline" id="cancelIncome">Batal</button></div>`;
    }

    // ---------- PENGELUARAN ----------
    function renderExpense(container) {
        let expenseList = [...transactions.expense];
        container.innerHTML = `<div class="card"><div class="card-header"><h3>📤 Data Pengeluaran</h3><button class="btn" id="btnTambahExpense"><i class="fas fa-plus"></i> Tambah Pengeluaran</button></div>
        <div id="expenseFormContainer" style="display:none;"></div><table><thead><tr><th>Tanggal</th><th>Deskripsi</th><th>Kategori</th><th>Jumlah</th><th>Aksi</th></tr></thead>
        <tbody>${expenseList.map(exp => `<tr><td>${exp.date}</td><td>${exp.description}</td><td>${exp.category}</td><td>Rp ${formatRupiah(exp.amount)}</td><td><button class="btn-outline" data-delete-exp="${exp.id}">Hapus</button></td></tr>`).join('')}</tbody></table></div>`;
        document.getElementById('btnTambahExpense')?.addEventListener('click', () => {
            const formDiv = document.getElementById('expenseFormContainer');
            formDiv.style.display = 'block';
            formDiv.innerHTML = getExpenseFormHtml();
            document.getElementById('saveExpenseBtn')?.addEventListener('click', () => {
                const date = document.getElementById('expDate').value;
                const desc = document.getElementById('expDesc').value;
                const amount = parseInt(document.getElementById('expAmount').value);
                const cat = document.getElementById('expCategory').value;
                if(date && desc && amount && cat) {
                    const newId = transactions.expense.length+1;
                    transactions.expense.push({ id: newId, date, description: desc, amount, category: cat });
                    renderExpense(container);
                } else alert("Isi lengkap!");
            });
        });
        document.querySelectorAll('[data-delete-exp]').forEach(btn => {
            btn.addEventListener('click', (e) => {
                let id = parseInt(btn.getAttribute('data-delete-exp'));
                transactions.expense = transactions.expense.filter(e => e.id !== id);
                renderExpense(container);
            });
        });
    }

    function getExpenseFormHtml() {
        const catOptions = categories.map(c => `<option value="${c.name}">${c.name}</option>`).join('');
        return `<div class="form-row"><div class="form-group"><label>Tanggal</label><input type="date" id="expDate" value="${new Date().toISOString().slice(0,10)}"></div>
        <div class="form-group"><label>Deskripsi</label><input id="expDesc" placeholder="Deskripsi"></div>
        <div class="form-group"><label>Kategori</label><select id="expCategory">${catOptions}</select></div>
        <div class="form-group"><label>Jumlah (Rp)</label><input type="number" id="expAmount" placeholder="0"></div></div>
        <div><button class="btn" id="saveExpenseBtn">Simpan</button><button class="btn-outline" id="cancelExpense">Batal</button></div>`;
    }

    // Kategori
    function renderCategories(container) {
        container.innerHTML = `<div class="card"><div class="card-header"><h3>📋 Daftar Kategori</h3><button class="btn" id="addCategoryBtn"><i class="fas fa-plus"></i> Kategori Baru</button></div>
        <div id="newCategoryForm" style="display:none;"></div><table><thead><tr><th>ID</th><th>Nama Kategori</th><th>Aksi</th></tr></thead><tbody>
        ${categories.map(cat => `<tr><td>${cat.id}</td><td>${cat.name}</td><td><button class="btn-outline" data-del-cat="${cat.id}">Hapus</button></td></tr>`).join('')}</tbody></table></div>`;
        document.getElementById('addCategoryBtn')?.addEventListener('click', () => {
            const formDiv = document.getElementById('newCategoryForm');
            formDiv.style.display = 'block';
            formDiv.innerHTML = `<div class="form-row"><div class="form-group"><label>Nama Kategori</label><input id="newCatName" placeholder="Contoh: Belanja"></div></div><button class="btn" id="confirmAddCat">Simpan</button>`;
            document.getElementById('confirmAddCat')?.addEventListener('click', () => {
                let name = document.getElementById('newCatName').value.trim();
                if(name) {
                    let newId = categories.length+1;
                    categories.push({ id: newId, name });
                    renderCategories(container);
                } else alert("Nama kategori harus diisi");
            });
        });
        document.querySelectorAll('[data-del-cat]').forEach(btn => {
            btn.addEventListener('click', (e) => {
                let id = parseInt(btn.getAttribute('data-del-cat'));
                categories = categories.filter(c => c.id !== id);
                renderCategories(container);
            });
        });
    }

    // Laporan Pemasukan
    function renderReportIncome(container) {
        let list = [...transactions.income];
        container.innerHTML = `<div class="card"><h3>📄 Laporan Pemasukan</h3>${generateReportTable(list, 'pemasukan')}</div>`;
    }
    function renderReportExpense(container) {
        let list = [...transactions.expense];
        container.innerHTML = `<div class="card"><h3>📄 Laporan Pengeluaran</h3>${generateReportTable(list, 'pengeluaran')}</div>`;
    }
    function generateReportTable(data, type) {
        if(data.length===0) return "<p>Tidak ada data</p>";
        let total = data.reduce((s, t) => s + t.amount, 0);
        return `<table><thead><tr><th>Tanggal</th><th>Deskripsi</th><th>Kategori</th><th>Jumlah</th></tr></thead><tbody>
        ${data.map(d => `<tr><td>${d.date}</td><td>${d.description}</td><td>${d.category}</td><td>Rp ${formatRupiah(d.amount)}</td></tr>`).join('')}
        <tr style="font-weight:bold; background:#f8fafc;"><td colspan="3">Total ${type}</td><td>Rp ${formatRupiah(total)}</td></tr></tbody></table>`;
    }

    // Rekapitulasi
    function renderRecap(container) {
        let totalInc = transactions.income.reduce((a,b)=>a+b.amount,0);
        let totalExp = transactions.expense.reduce((a,b)=>a+b.amount,0);
        let balance = totalInc - totalExp;
        container.innerHTML = `<div class="card"><h3>📊 Rekapitulasi Keuangan</h3><div class="stats-grid" style="grid-template-columns:1fr 1fr 1fr;">
        <div class="stat-card"><div class="stat-title">Total Pemasukan</div><div class="stat-value">Rp ${formatRupiah(totalInc)}</div></div>
        <div class="stat-card"><div class="stat-title">Total Pengeluaran</div><div class="stat-value">Rp ${formatRupiah(totalExp)}</div></div>
        <div class="stat-card"><div class="stat-title">Saldo Akhir</div><div class="stat-value">Rp ${formatRupiah(balance)}</div></div></div>
        <hr><h4>Ringkasan per Kategori (Pemasukan)</h4>${generateCategorySummary(transactions.income, 'income')}
        <h4 style="margin-top:16px">Ringkasan per Kategori (Pengeluaran)</h4>${generateCategorySummary(transactions.expense, 'expense')}</div>`;
    }

    function generateCategorySummary(trans, type) {
        let map = new Map();
        trans.forEach(t => { map.set(t.category, (map.get(t.category)||0) + t.amount); });
        if(map.size===0) return '<p>Tidak ada data</p>';
        let rows = '';
        for(let [cat, amt] of map.entries()) {
            rows += `<tr><td>${cat}</td><td>Rp ${formatRupiah(amt)}</td></tr>`;
        }
        return `<table><thead><tr><th>Kategori</th><th>Total</th></tr></thead><tbody>${rows}</tbody></table>`;
    }

    // MANAJEMEN USER (sesuai contoh data user)
    function renderUserManagement(container) {
        container.innerHTML = `
            <div class="card">
                <div class="card-header"><h3><i class="fas fa-users"></i> Data User</h3><button class="btn" id="btnTambahUser"><i class="fas fa-user-plus"></i> Tambah User</button></div>
                <div id="userFormContainer" style="display:none; margin-bottom:20px;"></div>
                <table>
                    <thead><tr><th>No.</th><th>Nama User</th><th>Username</th><th>Hak Akses</th><th>Aksi</th></tr></thead>
                    <tbody id="userTableBody"></tbody>
                </table>
                <div class="pagination-info">Menampilkan 1 sampai ${users.length} dari ${users.length} data</div>
            </div>
        `;
        refreshUserTable();
        document.getElementById('btnTambahUser')?.addEventListener('click', () => {
            const formDiv = document.getElementById('userFormContainer');
            formDiv.style.display = 'block';
            formDiv.innerHTML = `<div class="form-row"><div class="form-group"><label>Nama Lengkap</label><input id="userNama" placeholder="Nama User"></div>
            <div class="form-group"><label>Username</label><input id="userUsername" placeholder="username"></div>
            <div class="form-group"><label>Hak Akses</label><select id="userRole"><option>User</option><option>Admin</option></select></div></div>
            <button class="btn" id="saveUserBtn">Simpan</button> <button class="btn-outline" id="cancelUser">Batal</button>`;
            document.getElementById('saveUserBtn')?.addEventListener('click', () => {
                let nama = document.getElementById('userNama').value.trim();
                let username = document.getElementById('userUsername').value.trim();
                let role = document.getElementById('userRole').value;
                if(nama && username) {
                    users.push({ id: nextUserId++, nama, username, role });
                    renderUserManagement(container);
                } else alert("Lengkapi data");
            });
            document.getElementById('cancelUser')?.addEventListener('click', () => { formDiv.style.display='none'; });
        });
    }

    function refreshUserTable() {
        const tbody = document.getElementById('userTableBody');
        if(!tbody) return;
        tbody.innerHTML = users.map((user, idx) => `
            <tr><td>${idx+1}</td><td>${user.nama}</td><td>${user.username}</td><td><span class="badge-admin ${user.role==='User'?'badge-user':'badge-admin'}">${user.role}</span></td>
            <td><button class="btn-outline btn-sm" data-del-user="${user.id}">Hapus</button></td></tr>
        `).join('');
        document.querySelectorAll('[data-del-user]').forEach(btn => {
            btn.addEventListener('click', (e) => {
                let id = parseInt(btn.getAttribute('data-del-user'));
                users = users.filter(u => u.id !== id);
                renderUserManagement(document.getElementById('dynamicContent'));
            });
        });
    }

    function formatRupiah(angka) {
        return new Intl.NumberFormat('id-ID').format(angka);
    }

    // Event listener navigasi
    document.querySelectorAll('.nav-item').forEach(item => {
        item.addEventListener('click', () => {
            const mod = item.getAttribute('data-module');
            if(mod) renderModule(mod);
        });
    });
    // default load dashboard
    renderModule('dashboard');
</script>
</body>
</html>
