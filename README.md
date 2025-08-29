<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>App Finanzas Personales</title>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
  <style>
    :root {
      --primary: #4361ee;
      --secondary: #3f37c9;
      --success: #4cc9f0;
      --danger: #f72585;
      --warning: #f8961e;
      --light: #f8f9fa;
      --dark: #212529;
      --gray: #6c757d;
      --light-gray: #e9ecef;
    }
    
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }
    
    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
      margin: 0;
      padding: 20px;
      min-height: 100vh;
      color: var(--dark);
    }
    
    .container {
      max-width: 1200px;
      margin: 0 auto;
    }
    
    header {
      text-align: center;
      margin-bottom: 30px;
      background: white;
      padding: 20px;
      border-radius: 15px;
      box-shadow: 0 5px 15px rgba(0,0,0,0.1);
    }
    
    h1 {
      color: var(--primary);
      font-size: 2.5rem;
      margin-bottom: 10px;
    }
    
    .subtitle {
      color: var(--gray);
      font-size: 1.2rem;
    }
    
    .grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
      gap: 20px;
      margin-bottom: 30px;
    }
    
    .card {
      background: white;
      padding: 20px;
      border-radius: 15px;
      box-shadow: 0 5px 15px rgba(0,0,0,0.1);
      transition: transform 0.3s ease;
    }
    
    .card:hover {
      transform: translateY(-5px);
    }
    
    .card h2 {
      color: var(--primary);
      margin-bottom: 15px;
      padding-bottom: 10px;
      border-bottom: 2px solid var(--light-gray);
      display: flex;
      align-items: center;
      gap: 10px;
    }
    
    .card h2 i {
      font-size: 1.5rem;
    }
    
    .input-group {
      margin-bottom: 15px;
    }
    
    label {
      display: block;
      margin-bottom: 5px;
      font-weight: 500;
      color: var(--gray);
    }
    
    input, select, button {
      width: 100%;
      padding: 12px 15px;
      border: 1px solid var(--light-gray);
      border-radius: 8px;
      font-size: 16px;
    }
    
    input:focus, select:focus {
      outline: none;
      border-color: var(--primary);
      box-shadow: 0 0 0 3px rgba(67, 97, 238, 0.2);
    }
    
    button {
      background: var(--primary);
      color: white;
      border: none;
      cursor: pointer;
      font-weight: 600;
      transition: background 0.3s ease;
      display: flex;
      justify-content: center;
      align-items: center;
      gap: 8px;
    }
    
    button:hover {
      background: var(--secondary);
    }
    
    button.delete {
      background: var(--danger);
    }
    
    button.delete:hover {
      background: #d1146a;
    }
    
    .dashboard {
      grid-column: 1 / -1;
      background: white;
      padding: 25px;
      border-radius: 15px;
      box-shadow: 0 5px 15px rgba(0,0,0,0.1);
    }
    
    .stats {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
      gap: 15px;
      margin-bottom: 20px;
    }
    
    .stat-card {
      background: var(--light);
      padding: 15px;
      border-radius: 10px;
      text-align: center;
    }
    
    .stat-card h3 {
      font-size: 1rem;
      color: var(--gray);
      margin-bottom: 10px;
    }
    
    .stat-card p {
      font-size: 1.8rem;
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
    
    .list {
      list-style: none;
      margin-top: 15px;
      max-height: 300px;
      overflow-y: auto;
    }
    
    .list-item {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 10px;
      background: var(--light);
      border-radius: 8px;
      margin-bottom: 8px;
    }
    
    .list-item span {
      flex: 1;
    }
    
    .list-item .amount {
      font-weight: bold;
      margin: 0 10px;
    }
    
    .list-item .date {
      font-size: 0.9rem;
      color: var(--gray);
      margin: 0 10px;
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
    
    .chart-container {
      position: relative;
      height: 300px;
      margin-top: 20px;
    }
    
    .notification {
      position: fixed;
      top: 20px;
      right: 20px;
      padding: 15px 20px;
      background: var(--success);
      color: white;
      border-radius: 8px;
      box-shadow: 0 5px 15px rgba(0,0,0,0.2);
      transform: translateX(100%);
      opacity: 0;
      transition: all 0.3s ease;
      z-index: 1000;
    }
    
    .notification.show {
      transform: translateX(0);
      opacity: 1;
    }
    
    .tabs {
      display: flex;
      margin-bottom: 15px;
      border-bottom: 1px solid var(--light-gray);
    }
    
    .tab {
      padding: 10px 20px;
      cursor: pointer;
      border-bottom: 3px solid transparent;
    }
    
    .tab.active {
      border-bottom: 3px solid var(--primary);
      color: var(--primary);
      font-weight: bold;
    }
    
    .tab-content {
      display: none;
    }
    
    .tab-content.active {
      display: block;
    }
    
    @media (max-width: 768px) {
      .grid {
        grid-template-columns: 1fr;
      }
      
      .stats {
        grid-template-columns: 1fr 1fr;
      }
      
      .list-item {
        flex-direction: column;
        align-items: flex-start;
      }
      
      .list-item .amount, .list-item .date {
        margin: 5px 0;
      }
    }
  </style>
</head>
<body>
  <div class="container">
    <header>
      <h1><i class="fas fa-chart-pie"></i> Finanzas Personales</h1>
      <p class="subtitle">Controla tus ingresos, gastos y ahorros mensuales</p>
    </header>
    
    <div class="grid">
      <!-- Ingresos -->
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

        <div class="tabs">
          <div class="tab active" onclick="switchTab('incomesTab', this)">Ingresos</div>
          <div class="tab" onclick="switchTab('expensesTab', this)">Gastos</div>
        </div>
        
        <div id="incomesTab" class="tab-content active">
          <h3>Últimos ingresos</h3>
          <ul id="incomesList" class="list"></ul>
        </div>
        
        <div id="expensesTab" class="tab-content">
          <h3>Últimos gastos</h3>
          <ul id="expensesList" class="list"></ul>
        </div>
      </div>
      
      <!-- Gastos diarios -->
      <div class="card">
        <h2><i class="fas fa-shopping-cart"></i> Agregar Gasto Diario</h2>
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
      
      <!-- Gastos fijos -->
      <div class="card">
        <h2><i class="fas fa-file-invoice-dollar"></i> Gastos Fijos Mensuales</h2>
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
        
        <h3 style="margin-top: 20px;">Próximos pagos (ordenados por prioridad)</h3>
        <ul id="fixedList" class="list"></ul>
      </div>
      
      <!-- Dashboard -->
      <div class="dashboard">
        <h2><i class="fas fa-chart-bar"></i> Dashboard Mensual</h2>
        
        <div class="input-group">
          <label for="monthSelector">Seleccionar mes</label>
          <select id="monthSelector" onchange="updateChart()"></select>
        </div>
        
        <div class="stats">
          <div class="stat-card">
            <h3>Total Ingresos</h3>
            <p id="totalIncome" class="income">$0.00</p>
          </div>
          <div class="stat-card">
            <h3>Total Gastos</h3>
            <p id="totalExpense" class="expense">$0.00</p>
          </div>
          <div class="stat-card">
            <h3>Ahorro (25%)</h3>
            <p id="totalSaving" class="saving">$0.00</p>
          </div>
          <div class="stat-card">
            <h3>Balance Final</h3>
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
      document.querySelectorAll('.tab').forEach(tab => {
        tab.classList.remove('active');
      });
      
      // Desactivar todos los contenidos
      document.querySelectorAll('.tab-content').forEach(content => {
        content.classList.remove('active');
      });
      
      // Activar la pestaña seleccionada
      element.classList.add('active');
      document.getElementById(tabId).classList.add('active');
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
        showNotification("Por favor, completa todos los campos correctamente.", false);
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
    }

    // Agregar gasto
    function addExpense() {
      const desc = document.getElementById("expenseDesc").value;
      const amount = parseFloat(document.getElementById("expenseAmount").value);
      const date = document.getElementById("expenseDate").value;

      if (!desc || isNaN(amount) || amount <= 0 || !date) {
        showNotification("Por favor, completa todos los campos correctamente.", false);
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
    }

    // Agregar gasto fijo
    function addFixed() {
      const desc = document.getElementById("fixedDesc").value;
      const amount = parseFloat(document.getElementById("fixedAmount").value);
      const dueDate = document.getElementById("fixedDueDate").value;

      if (!desc || isNaN(amount) || amount <= 0 || !dueDate) {
        showNotification("Por favor, completa todos los campos correctamente.", false);
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
    }

    // Renderizar lista de ingresos
    function renderIncomesList() {
      const list = document.getElementById("incomesList");
      list.innerHTML = "";
      
      if (incomes.length === 0) {
        list.innerHTML = "<p>No hay ingresos registrados.</p>";
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
        list.innerHTML = "<p>No hay gastos registrados.</p>";
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
        list.innerHTML = "<p>No hay gastos fijos registrados.</p>";
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
          month: "long",
          year: "numeric"
        });
        
        // Calcular días restantes
        const today = new Date();
        today.setHours(0, 0, 0, 0);
        dueDate.setHours(0, 0, 0, 0);
        const diffTime = dueDate - today;
        const diffDays = Math.ceil(diffTime / (1000 * 60 * 60 * 24));
        
        let daysText = "";
        if (diffDays < 0) {
          daysText = `(Vencido hace ${Math.abs(diffDays)} días)`;
        } else if (diffDays === 0) {
          daysText = "(Vence hoy)";
        } else {
          daysText = `(En ${diffDays} días)`;
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
      if (confirm("¿Estás seguro de que quieres eliminar este ingreso?")) {
        incomes.splice(index, 1);
        localStorage.setItem("incomes", JSON.stringify(incomes));
        renderIncomesList();
        updateChart();
        showNotification("Ingreso eliminado.");
      }
    }

    // Eliminar gasto
    function deleteExpense(index) {
      if (confirm("¿Estás seguro de que quieres eliminar este gasto?")) {
        expenses.splice(index, 1);
        localStorage.setItem("expenses", JSON.stringify(expenses));
        renderExpensesList();
        updateChart();
        showNotification("Gasto eliminado.");
      }
    }

    // Eliminar gasto fijo
    function deleteFixed(index) {
      if (confirm("¿Estás seguro de que quieres eliminar este gasto fijo?")) {
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
              beginAtZero: true
            }
          },
          plugins: {
            title: {
              display: true,
              text: `Resumen Financiero - ${document.getElementById("monthSelector").selectedOptions[0].text}`,
              font: {
                size: 16
              }
            },
            legend: {
              position: 'bottom'
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