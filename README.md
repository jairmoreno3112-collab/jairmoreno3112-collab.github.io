<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Finanzas Personales Móvil</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary: #4361ee;
            --primary-light: #6b7dee;
            --secondary: #3f37c9;
            --success: #4cc9f0;
            --danger: #f72585;
            --warning: #f8961e;
            --light: #f8f9fa;
            --dark: #212529;
            --gray: #6c757d;
            --light-gray: #e9ecef;
            --card-shadow: 0 4px 12px rgba(0,0,0,0.08);
        }
        
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            -webkit-tap-highlight-color: transparent;
        }
        
        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, sans-serif;
            background: linear-gradient(135deg, #f5f7fa 0%, #e6e9f0 100%);
            margin: 0;
            padding: 0;
            color: var(--dark);
            line-height: 1.5;
            overflow-x: hidden;
        }
        
        /* Header fijo para móviles */
        .header-container {
            position: sticky;
            top: 0;
            z-index: 100;
            background: white;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
            padding: 15px;
        }
        
        header {
            max-width: 1200px;
            margin: 0 auto;
            text-align: center;
        }
        
        h1 {
            color: var(--primary);
            font-size: 1.5rem;
            margin-bottom: 5px;
            font-weight: 700;
        }
        
        .subtitle {
            color: var(--gray);
            font-size: 0.9rem;
        }
        
        .container {
            max-width: 100%;
            padding: 15px;
            margin: 0 auto;
        }
        
        /* Navegación con pestañas para móviles */
        .nav-tabs {
            display: flex;
            background: white;
            border-radius: 12px;
            margin-bottom: 15px;
            overflow: hidden;
            box-shadow: var(--card-shadow);
        }
        
        .nav-tab {
            flex: 1;
            text-align: center;
            padding: 12px 5px;
            font-size: 0.85rem;
            font-weight: 600;
            color: var(--gray);
            border-bottom: 3px solid transparent;
            transition: all 0.2s ease;
        }
        
        .nav-tab.active {
            color: var(--primary);
            border-bottom: 3px solid var(--primary);
        }
        
        .nav-tab i {
            display: block;
            margin: 0 auto 5px;
            font-size: 1.2rem;
        }
        
        /* Contenido de las pestañas */
        .tab-content {
            display: none;
            animation: fadeIn 0.3s ease;
        }
        
        .tab-content.active {
            display: block;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        /* Tarjetas para formularios */
        .card {
            background: white;
            padding: 20px 15px;
            border-radius: 14px;
            margin-bottom: 20px;
            box-shadow: var(--card-shadow);
        }
        
        .card h2 {
            color: var(--primary);
            font-size: 1.2rem;
            margin-bottom: 15px;
            padding-bottom: 10px;
            border-bottom: 1px solid var(--light-gray);
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .card h2 i {
            font-size: 1.3rem;
        }
        
        .input-group {
            margin-bottom: 15px;
        }
        
        label {
            display: block;
            margin-bottom: 6px;
            font-weight: 500;
            color: var(--dark);
            font-size: 0.9rem;
        }
        
        input, select, button {
            width: 100%;
            padding: 14px 15px;
            border: 1px solid var(--light-gray);
            border-radius: 10px;
            font-size: 1rem;
            -webkit-appearance: none;
            appearance: none;
        }
        
        input:focus, select:focus {
            outline: none;
            border-color: var(--primary);
            box-shadow: 0 0 0 3px rgba(67, 97, 238, 0.15);
        }
        
        button {
            background: var(--primary);
            color: white;
            border: none;
            cursor: pointer;
            font-weight: 600;
            transition: all 0.2s ease;
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 8px;
            margin-top: 10px;
        }
        
        button:active {
            background: var(--secondary);
            transform: scale(0.98);
        }
        
        button.delete {
            background: var(--danger);
            padding: 8px 12px;
            font-size: 0.85rem;
        }
        
        /* Dashboard y estadísticas */
        .dashboard {
            background: white;
            padding: 20px 15px;
            border-radius: 14px;
            margin-bottom: 20px;
            box-shadow: var(--card-shadow);
        }
        
        .stats {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 12px;
            margin-bottom: 20px;
        }
        
        .stat-card {
            background: var(--light);
            padding: 15px 10px;
            border-radius: 10px;
            text-align: center;
        }
        
        .stat-card h3 {
            font-size: 0.8rem;
            color: var(--gray);
            margin-bottom: 8px;
        }
        
        .stat-card p {
            font-size: 1.3rem;
            font-weight: bold;
        }
        
        .income {
            color: #28a745;
        }
        
        .expense {
            color: #dc3545;
        }
        
        .saving {
            color: #ffc107;
        }
        
        .balance {
            color: var(--primary);
        }
        
        /* Listas */
        .list {
            list-style: none;
            margin-top: 15px;
            max-height: 300px;
            overflow-y: auto;
            -webkit-overflow-scrolling: touch;
        }
        
        .list-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 12px 10px;
            background: var(--light);
            border-radius: 10px;
            margin-bottom: 8px;
            transition: transform 0.2s ease;
        }
        
        .list-item:active {
            transform: scale(0.98);
        }
        
        .list-item span {
            flex: 1;
            font-size: 0.9rem;
        }
        
        .list-item .amount {
            font-weight: bold;
            margin: 0 8px;
            font-size: 0.95rem;
        }
        
        .list-item .date {
            font-size: 0.8rem;
            color: var(--gray);
            margin: 0 8px;
        }
        
        .income-item .amount {
            color: #28a745;
        }
        
        .expense-item .amount {
            color: #dc3545;
        }
        
        .priority-high {
            border-left: 4px solid var(--danger);
        }
        
        .priority-medium {
            border-left: 4px solid var(--warning);
        }
        
        .priority-low {
            border-left: 4px solid var(--success);
        }
        
        /* Gráfico */
        .chart-container {
            position: relative;
            height: 250px;
            margin-top: 15px;
        }
        
        /* Notificaciones */
        .notification {
            position: fixed;
            bottom: 20px;
            left: 50%;
            transform: translateX(-50%) translateY(100px);
            padding: 12px 20px;
            background: var(--success);
            color: white;
            border-radius: 50px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
            opacity: 0;
            transition: all 0.3s ease;
            z-index: 1000;
            text-align: center;
            max-width: 80%;
        }
        
        .notification.show {
            transform: translateX(-50%) translateY(0);
            opacity: 1;
        }
        
        /* Selector de mes */
        .month-selector {
            margin-bottom: 15px;
        }
        
        /* Mejoras para tablets */
        @media (min-width: 768px) {
            .container {
                padding: 20px;
                max-width: 750px;
            }
            
            h1 {
                font-size: 1.8rem;
            }
            
            .nav-tab {
                font-size: 0.9rem;
                padding: 15px 5px;
            }
            
            .nav-tab i {
                font-size: 1.4rem;
                margin-bottom: 8px;
            }
            
            .card {
                padding: 25px 20px;
            }
            
            .stats {
                grid-template-columns: repeat(4, 1fr);
                gap: 15px;
            }
            
            .stat-card {
                padding: 20px 15px;
            }
            
            .stat-card h3 {
                font-size: 0.9rem;
            }
            
            .stat-card p {
                font-size: 1.5rem;
            }
        }
        
        /* Mejoras para escritorio */
        @media (min-width: 1024px) {
            .container {
                max-width: 1000px;
            }
            
            .grid-layout {
                display: grid;
                grid-template-columns: 1fr 1fr;
                gap: 20px;
            }
            
            .dashboard {
                grid-column: 1 / -1;
            }
        }
        
        /* Scroll personalizado */
        ::-webkit-scrollbar {
            width: 6px;
        }
        
        ::-webkit-scrollbar-track {
            background: #f1f1f1;
            border-radius: 10px;
        }
        
        ::-webkit-scrollbar-thumb {
            background: var(--primary-light);
            border-radius: 10px;
        }
        
        ::-webkit-scrollbar-thumb:hover {
            background: var(--primary);
        }
    </style>
</head>
<body>
    <div class="header-container">
        <header>
            <h1><i class="fas fa-chart-pie"></i> Finanzas Personales</h1>
            <p class="subtitle">Controla tus ingresos, gastos y ahorros</p>
        </header>
    </div>

    <div class="container">
        <!-- Navegación por pestañas -->
        <div class="nav-tabs">
            <div class="nav-tab active" onclick="switchTab('ingresosTab', this)">
                <i class="fas fa-money-bill-wave"></i>
                <span>Ingresos</span>
            </div>
            <div class="nav-tab" onclick="switchTab('gastosTab', this)">
                <i class="fas fa-shopping-cart"></i>
                <span>Gastos</span>
            </div>
            <div class="nav-tab" onclick="switchTab('fijosTab', this)">
                <i class="fas fa-file-invoice-dollar"></i>
                <span>Fijos</span>
            </div>
            <div class="nav-tab" onclick="switchTab('dashboardTab', this)">
                <i class="fas fa-chart-bar"></i>
                <span>Dashboard</span>
            </div>
        </div>
        
        <!-- Pestaña de Ingresos -->
        <div id="ingresosTab" class="tab-content active">
            <div class="card">
                <h2><i class="fas fa-money-bill-wave"></i> Agregar Ingreso</h2>
                <div class="input-group">
                    <label for="incomeDesc">Descripción</label>
                    <input type="text" id="incomeDesc" placeholder="Salario, venta, etc.">
                </div>
                <div class="input-group">
                    <label for="incomeAmount">Monto ($)</label>
                    <input type="number" id="incomeAmount" placeholder="0.00" min="0" step="0.01">
                </div>
                <div class="input-group">
                    <label for="incomeDate">Fecha de ingreso</label>
                    <input type="date" id="incomeDate">
                </div>
                <button onclick="addIncome()">
                    <i class="fas fa-plus-circle"></i> Agregar Ingreso
                </button>
            </div>
            
            <div class="card">
                <h2><i class="fas fa-list"></i> Últimos Ingresos</h2>
                <ul id="incomesList" class="list"></ul>
            </div>
        </div>
        
        <!-- Pestaña de Gastos -->
        <div id="gastosTab" class="tab-content">
            <div class="card">
                <h2><i class="fas fa-shopping-cart"></i> Agregar Gasto</h2>
                <div class="input-group">
                    <label for="expenseDesc">Descripción</label>
                    <input type="text" id="expenseDesc" placeholder="Comida, transporte, etc.">
                </div>
                <div class="input-group">
                    <label for="expenseAmount">Monto ($)</label>
                    <input type="number" id="expenseAmount" placeholder="0.00" min="0" step="0.01">
                </div>
                <div class="input-group">
                    <label for="expenseDate">Fecha</label>
                    <input type="date" id="expenseDate">
                </div>
                <button onclick="addExpense()">
                    <i class="fas fa-minus-circle"></i> Agregar Gasto
                </button>
            </div>
            
            <div class="card">
                <h2><i class="fas fa-list"></i> Últimos Gastos</h2>
                <ul id="expensesList" class="list"></ul>
            </div>
        </div>
        
        <!-- Pestaña de Gastos Fijos -->
        <div id="fijosTab" class="tab-content">
            <div class="card">
                <h2><i class="fas fa-file-invoice-dollar"></i> Agregar Gasto Fijo</h2>
                <div class="input-group">
                    <label for="fixedDesc">Descripción</label>
                    <input type="text" id="fixedDesc" placeholder="Alquiler, servicios, etc.">
                </div>
                <div class="input-group">
                    <label for="fixedAmount">Monto ($)</label>
                    <input type="number" id="fixedAmount" placeholder="0.00" min="0" step="0.01">
                </div>
                <div class="input-group">
                    <label for="fixedDueDate">Día de pago</label>
                    <input type="date" id="fixedDueDate">
                </div>
                <button onclick="addFixed()">
                    <i class="fas fa-plus"></i> Agregar Gasto Fijo
                </button>
            </div>
            
            <div class="card">
                <h2><i class="fas fa-calendar-check"></i> Próximos Pagos</h2>
                <ul id="fixedList" class="list"></ul>
            </div>
        </div>
        
        <!-- Pestaña de Dashboard -->
        <div id="dashboardTab" class="tab-content">
            <div class="dashboard">
                <h2><i class="fas fa-chart-bar"></i> Dashboard Mensual</h2>
                
                <div class="input-group month-selector">
                    <label for="monthSelector">Seleccionar mes</label>
                    <select id="monthSelector" onchange="updateChart()"></select>
                </div>
                
                <div class="stats">
                    <div class="stat-card">
                        <h3>Ingresos</h3>
                        <p id="totalIncome" class="income">$0.00</p>
                    </div>
                    <div class="stat-card">
                        <h3>Gastos</h3>
                        <p id="totalExpense" class="expense">$0.00</p>
                    </div>
                    <div class="stat-card">
                        <h3>Ahorro (25%)</h3>
                        <p id="totalSaving" class="saving">$0.00</p>
                    </div>
                    <div class="stat-card">
                        <h3>Balance</h3>
                        <p id="totalBalance" class="balance">$0.00</p>
                    </div>
                </div>
                
                <div class="chart-container">
                    <canvas id="financeChart"></canvas>
                </div>
            </div>
        </div>
    </div>

    <div id="notification" class="notification"></div>

    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <script>
        // Datos
        let incomes = JSON.parse(localStorage.getItem("incomes")) || [];
        let expenses = JSON.parse(localStorage.getItem("expenses")) || [];
        let fixedExpenses = JSON.parse(localStorage.getItem("fixedExpenses")) || [];

        // Elementos del DOM
        const ctx = document.getElementById("financeChart").getContext("2d");
        let financeChart;
        const notification = document.getElementById("notification");

        // Cambiar pestañas
        function switchTab(tabId, element) {
            // Desactivar todas las pestañas
            document.querySelectorAll('.nav-tab').forEach(tab => {
                tab.classList.remove('active');
            });
            
            // Desactivar todos los contenidos
            document.querySelectorAll('.tab-content').forEach(content => {
                content.classList.remove('active');
            });
            
            // Activar la pestaña seleccionada
            element.classList.add('active');
            document.getElementById(tabId).classList.add('active');
            
            // Si es el dashboard, actualizar el gráfico
            if (tabId === 'dashboardTab') {
                setTimeout(updateChart, 100);
            }
        }

        // Inicializar selector de meses
        function initMonthSelector() {
            const selector = document.getElementById("monthSelector");
            selector.innerHTML = "";
            
            // Obtener todos los meses únicos de los datos
            const allMonths = new Set();
            
            // Agregar meses de ingresos
            incomes.forEach(income => {
                if (income.date) {
                    allMonths.add(income.date.substring(0, 7));
                }
            });
            
            // Agregar meses de gastos
            expenses.forEach(expense => {
                if (expense.date) {
                    allMonths.add(expense.date.substring(0, 7));
                }
            });
            
            // Convertir a array y ordenar
            const sortedMonths = Array.from(allMonths).sort();
            
            // Si no hay meses, agregar el mes actual
            if (sortedMonths.length === 0) {
                const now = new Date();
                const currentMonth = `${now.getFullYear()}-${String(now.getMonth() + 1).padStart(2, "0")}`;
                sortedMonths.push(currentMonth);
            }
            
            // Crear opciones
            sortedMonths.forEach(month => {
                const [year, monthNum] = month.split('-');
                const date = new Date(year, monthNum - 1);
                const monthName = date.toLocaleString("es-ES", { month: "long", year: "numeric" });
                
                const option = document.createElement("option");
                option.value = month;
                option.textContent = monthName.charAt(0).toUpperCase() + monthName.slice(1);
                selector.appendChild(option);
            });
            
            // Seleccionar el último mes
            selector.value = sortedMonths[sortedMonths.length - 1];
        }

        // Mostrar notificación
        function showNotification(message, isSuccess = true) {
            notification.textContent = message;
            notification.style.background = isSuccess ? '#28a745' : '#dc3545';
            notification.classList.add('show');
            
            setTimeout(() => {
                notification.classList.remove('show');
            }, 3000);
        }

        // Calcular prioridad según la fecha de vencimiento
        function calculatePriority(dueDate) {
            const today = new Date();
            today.setHours(0, 0, 0, 0);
            
            const due = new Date(dueDate);
            due.setHours(0, 0, 0, 0);
            
            const diffTime = due - today;
            const diffDays = Math.ceil(diffTime / (1000 * 60 * 60 * 24));
            
            if (diffDays <= 0) return "high"; // Vencido
            if (diffDays <= 3) return "high";
            if (diffDays <= 7) return "medium";
            return "low";
        }

        // Agregar ingreso
        function addIncome() {
            const desc = document.getElementById("incomeDesc").value;
            const amount = parseFloat(document.getElementById("incomeAmount").value);
            const date = document.getElementById("incomeDate").value;

            if (!desc || isNaN(amount) || amount <= 0 || !date) {
                showNotification("Completa todos los campos correctamente.", false);
                return;
            }

            incomes.push({ desc, amount, date });
            localStorage.setItem("incomes", JSON.stringify(incomes));
            
            // Limpiar campos
            document.getElementById("incomeDesc").value = "";
            document.getElementById("incomeAmount").value = "";
            
            showNotification("Ingreso agregado correctamente!");
            initMonthSelector();
            renderIncomesList();
            updateChart();
            
            // Cambiar a la pestaña de dashboard
            switchTab('dashboardTab', document.querySelector('.nav-tab:nth-child(4)'));
        }

        // Agregar gasto
        function addExpense() {
            const desc = document.getElementById("expenseDesc").value;
            const amount = parseFloat(document.getElementById("expenseAmount").value);
            const date = document.getElementById("expenseDate").value;

            if (!desc || isNaN(amount) || amount <= 0 || !date) {
                showNotification("Completa todos los campos correctamente.", false);
                return;
            }

            expenses.push({ desc, amount, date });
            localStorage.setItem("expenses", JSON.stringify(expenses));
            
            // Limpiar campos
            document.getElementById("expenseDesc").value = "";
            document.getElementById("expenseAmount").value = "";
            
            showNotification("Gasto agregado correctamente!");
            initMonthSelector();
            renderExpensesList();
            updateChart();
            
            // Cambiar a la pestaña de dashboard
            switchTab('dashboardTab', document.querySelector('.nav-tab:nth-child(4)'));
        }

        // Agregar gasto fijo
        function addFixed() {
            const desc = document.getElementById("fixedDesc").value;
            const amount = parseFloat(document.getElementById("fixedAmount").value);
            const dueDate = document.getElementById("fixedDueDate").value;

            if (!desc || isNaN(amount) || amount <= 0 || !dueDate) {
                showNotification("Completa todos los campos correctamente.", false);
                return;
            }

            const priority = calculatePriority(dueDate);
            
            fixedExpenses.push({ desc, amount, dueDate, priority });
            localStorage.setItem("fixedExpenses", JSON.stringify(fixedExpenses));
            
            // Limpiar campos
            document.getElementById("fixedDesc").value = "";
            document.getElementById("fixedAmount").value = "";
            
            showNotification("Gasto fijo agregado correctamente!");
            renderFixedExpenses();
            updateChart();
            
            // Cambiar a la pestaña de dashboard
            switchTab('dashboardTab', document.querySelector('.nav-tab:nth-child(4)'));
        }

        // Renderizar lista de ingresos
        function renderIncomesList() {
            const list = document.getElementById("incomesList");
            list.innerHTML = "";
            
            if (incomes.length === 0) {
                list.innerHTML = "<p style='padding: 15px; text-align: center; color: var(--gray);'>No hay ingresos registrados.</p>";
                return;
            }
            
            // Ordenar ingresos por fecha (más recientes primero)
            const sortedIncomes = [...incomes].sort((a, b) => new Date(b.date) - new Date(a.date));
            
            sortedIncomes.forEach((income, i) => {
                const li = document.createElement("li");
                li.className = "list-item income-item";
                
                const incomeDate = new Date(income.date);
                const formattedDate = incomeDate.toLocaleDateString("es-ES");
                
                li.innerHTML = `
                    <span>${income.desc}</span>
                    <span class="amount">$${income.amount.toFixed(2)}</span>
                    <span class="date">${formattedDate}</span>
                    <button class="delete" onclick="deleteIncome(${i})">
                        <i class="fas fa-trash"></i>
                    </button>
                `;
                list.appendChild(li);
            });
        }

        // Renderizar lista de gastos
        function renderExpensesList() {
            const list = document.getElementById("expensesList");
            list.innerHTML = "";
            
            if (expenses.length === 0) {
                list.innerHTML = "<p style='padding: 15px; text-align: center; color: var(--gray);'>No hay gastos registrados.</p>";
                return;
            }
            
            // Ordenar gastos por fecha (más recientes primero)
            const sortedExpenses = [...expenses].sort((a, b) => new Date(b.date) - new Date(a.date));
            
            sortedExpenses.forEach((expense, i) => {
                const li = document.createElement("li");
                li.className = "list-item expense-item";
                
                const expenseDate = new Date(expense.date);
                const formattedDate = expenseDate.toLocaleDateString("es-ES");
                
                li.innerHTML = `
                    <span>${expense.desc}</span>
                    <span class="amount">$${expense.amount.toFixed(2)}</span>
                    <span class="date">${formattedDate}</span>
                    <button class="delete" onclick="deleteExpense(${i})">
                        <i class="fas fa-trash"></i>
                    </button>
                `;
                list.appendChild(li);
            });
        }

        // Renderizar gastos fijos
        function renderFixedExpenses() {
            const list = document.getElementById("fixedList");
            list.innerHTML = "";
            
            if (fixedExpenses.length === 0) {
                list.innerHTML = "<p style='padding: 15px; text-align: center; color: var(--gray);'>No hay gastos fijos registrados.</p>";
                return;
            }
            
            // Ordenar gastos fijos por prioridad (alta primero) y fecha de vencimiento
            const sortedFixed = [...fixedExpenses].sort((a, b) => {
                const priorityOrder = { high: 1, medium: 2, low: 3 };
                if (priorityOrder[a.priority] !== priorityOrder[b.priority]) {
                    return priorityOrder[a.priority] - priorityOrder[b.priority];
                }
                return new Date(a.dueDate) - new Date(b.dueDate);
            });
            
            sortedFixed.forEach((f, i) => {
                const li = document.createElement("li");
                li.className = `list-item priority-${f.priority}`;
                
                const dueDate = new Date(f.dueDate);
                const formattedDate = dueDate.toLocaleDateString("es-ES", {
                    day: "numeric",
                    month: "short"
                });
                
                // Calcular días restantes
                const today = new Date();
                today.setHours(0, 0, 0, 0);
                dueDate.setHours(0, 0, 0, 0);
                const diffTime = dueDate - today;
                const diffDays = Math.ceil(diffTime / (1000 * 60 * 60 * 24));
                
                let daysText = "";
                if (diffDays < 0) {
                    daysText = `(Vencido)`;
                } else if (diffDays === 0) {
                    daysText = "(Hoy)";
                } else if (diffDays === 1) {
                    daysText = "(Mañana)";
                } else {
                    daysText = `(${diffDays} días)`;
                }
                
                li.innerHTML = `
                    <span>${f.desc}</span>
                    <span class="amount">$${f.amount.toFixed(2)}</span>
                    <span class="date">${formattedDate} ${daysText}</span>
                    <button class="delete" onclick="deleteFixed(${i})">
                        <i class="fas fa-trash"></i>
                    </button>
                `;
                list.appendChild(li);
            });
        }

        // Eliminar ingreso
        function deleteIncome(index) {
            if (confirm("¿Eliminar este ingreso?")) {
                incomes.splice(index, 1);
                localStorage.setItem("incomes", JSON.stringify(incomes));
                renderIncomesList();
                updateChart();
                showNotification("Ingreso eliminado.");
            }
        }

        // Eliminar gasto
        function deleteExpense(index) {
            if (confirm("¿Eliminar este gasto?")) {
                expenses.splice(index, 1);
                localStorage.setItem("expenses", JSON.stringify(expenses));
                renderExpensesList();
                updateChart();
                showNotification("Gasto eliminado.");
            }
        }

        // Eliminar gasto fijo
        function deleteFixed(index) {
            if (confirm("¿Eliminar este gasto fijo?")) {
                fixedExpenses.splice(index, 1);
                localStorage.setItem("fixedExpenses", JSON.stringify(fixedExpenses));
                renderFixedExpenses();
                updateChart();
                showNotification("Gasto fijo eliminado.");
            }
        }

        // Actualizar gráfico y estadísticas
        function updateChart() {
            const month = document.getElementById("monthSelector").value;
            
            // Filtrar datos por mes seleccionado
            const monthIncomes = incomes.filter(i => i.date && i.date.startsWith(month));
            const monthExpenses = expenses.filter(e => e.date && e.date.startsWith(month));
            
            // Calcular totales
            const totalIncome = monthIncomes.reduce((sum, i) => sum + i.amount, 0);
            const totalVariableExpenses = monthExpenses.reduce((sum, e) => sum + e.amount, 0);
            const totalFixedExpenses = fixedExpenses.reduce((sum, f) => sum + f.amount, 0);
            const totalExpenses = totalVariableExpenses + totalFixedExpenses;
            const saving = totalIncome * 0.25;
            const balance = totalIncome - totalExpenses - saving;
            
            // Actualizar estadísticas
            document.getElementById("totalIncome").textContent = `$${totalIncome.toFixed(2)}`;
            document.getElementById("totalExpense").textContent = `$${totalExpenses.toFixed(2)}`;
            document.getElementById("totalSaving").textContent = `$${saving.toFixed(2)}`;
            document.getElementById("totalBalance").textContent = `$${balance.toFixed(2)}`;
            
            // Colores para el balance
            const balanceElement = document.getElementById("totalBalance");
            balanceElement.className = balance >= 0 ? "balance" : "expense";
            
            // Destruir gráfico anterior si existe
            if (financeChart) {
                financeChart.destroy();
            }
            
            // Crear nuevo gráfico
            financeChart = new Chart(ctx, {
                type: "bar",
                data: {
                    labels: ["Ingresos", "Gastos", "Ahorro (25%)", "Balance"],
                    datasets: [{
                        label: "Cantidad ($)",
                        data: [totalIncome, totalExpenses, saving, balance],
                        backgroundColor: [
                            "rgba(40, 167, 69, 0.7)",
                            "rgba(220, 53, 69, 0.7)",
                            "rgba(255, 193, 7, 0.7)",
                            balance >= 0 ? "rgba(67, 97, 238, 0.7)" : "rgba(220, 53, 69, 0.7)"
                        ],
                        borderColor: [
                            "rgba(40, 167, 69, 1)",
                            "rgba(220, 53, 69, 1)",
                            "rgba(255, 193, 7, 1)",
                            balance >= 0 ? "rgba(67, 97, 238, 1)" : "rgba(220, 53, 69, 1)"
                        ],
                        borderWidth: 1
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    scales: {
                        y: {
                            beginAtZero: true,
                            ticks: {
                                callback: function(value) {
                                    return '$' + value;
                                }
                            }
                        }
                    },
                    plugins: {
                        legend: {
                            display: false
                        }
                    }
                }
            });
        }

        // Inicialización
        function init() {
            // Establecer fecha actual por defecto
            const now = new Date();
            const year = now.getFullYear();
            const month = String(now.getMonth() + 1).padStart(2, '0');
            const day = String(now.getDate()).padStart(2, '0');
            
            document.getElementById("incomeDate").value = `${year}-${month}-${day}`;
            document.getElementById("expenseDate").value = `${year}-${month}-${day}`;
            
            // Establecer fecha de vencimiento por defecto (5 días a partir de hoy)
            const dueDate = new Date();
            dueDate.setDate(dueDate.getDate() + 5);
            const dueYear = dueDate.getFullYear();
            const dueMonth = String(dueDate.getMonth() + 1).padStart(2, '0');
            const dueDay = String(dueDate.getDate()).padStart(2, '0');
            document.getElementById("fixedDueDate").value = `${dueYear}-${dueMonth}-${dueDay}`;
            
            initMonthSelector();
            renderIncomesList();
            renderExpensesList();
            renderFixedExpenses();
            updateChart();
        }

        // Ejecutar inicialización cuando se carga la página
        window.onload = init;
    </script>
</body>
</html>
