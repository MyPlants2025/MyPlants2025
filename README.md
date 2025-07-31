<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <meta name="theme-color" content="#2c3e50">
  <title>سجل مخزن المبيدات | Store Stock</title>
  <link rel="manifest" href="manifest.json">
  <link href="https://fonts.googleapis.com/css2?family=Tajawal:wght@400;700&family=Amiri:wght@400;700&display=swap" rel="stylesheet">
  <style>
    :root {
      --primary: #2c3e50;
      --secondary: #3498db;
      --success: #2ecc71;
      --danger: #e74c3c;
      --warning: #f39c12;
      --light: #f4f4f9;
      --dark: #333;
      --shadow: 0 4px 12px rgba(0,0,0,0.1);
    }
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: 'Tajawal', 'Amiri', 'Segoe UI', sans-serif;
    }
    body {
      background-color: var(--light);
      color: var(--dark);
      line-height: 1.7;
      direction: rtl;
    }
    .container {
      max-width: 1200px;
      margin: 0 auto;
      padding: 20px;
    }
    header {
      text-align: center;
      margin-bottom: 30px;
    }
    header h1 {
      color: var(--primary);
      font-size: 1.8rem;
      margin-bottom: 10px;
      font-family: 'Amiri', sans-serif;
      font-weight: 700;
    }
    .language-button {
      position: fixed;
      top: 20px;
      left: 20px;
      padding: 10px 20px;
      font-size: 16px;
      cursor: pointer;
      background-color: var(--primary);
      color: white;
      border: none;
      border-radius: 8px;
      transition: background 0.3s;
      font-family: 'Tajawal', sans-serif;
      z-index: 1000;
    }
    .language-button:hover {
      background-color: #1a252f;
    }
    .input-group {
      margin: 20px 0;
      text-align: center;
    }
    .input-group input, .input-group select {
      padding: 12px;
      font-size: 16px;
      width: 280px;
      border: 1px solid #ddd;
      border-radius: 8px;
      outline: none;
      margin: 5px;
      font-family: 'Tajawal', sans-serif;
    }
    button {
      padding: 10px 20px;
      font-size: 16px;
      cursor: pointer;
      border: none;
      border-radius: 8px;
      margin: 5px;
      transition: background 0.3s;
      font-family: 'Tajawal', sans-serif;
    }
    .store-button {
      background-color: var(--secondary);
      color: white;
    }
    .store-button:hover {
      background-color: #2980b9;
    }
    .add-button {
      background-color: var(--success);
      color: white;
    }
    .add-button:hover {
      background-color: #27ae60;
    }
    .delete-button {
      background-color: var(--danger);
      color: white;
    }
    .delete-button:hover {
      background-color: #c0392b;
    }
    .date-button {
      background-color: #9b59b6;
      color: white;
    }
    .date-button:hover {
      background-color: #8e44ad;
    }
    .button {
      background-color: var(--success);
      color: white;
    }
    .button:hover {
      background-color: #27ae60;
    }
    .edit-button {
      background-color: var(--warning);
      color: white;
    }
    .edit-button:hover {
      background-color: #e67e22;
    }
    .delete-inventory-button {
      background-color: #c0392b;
      color: white;
    }
    .delete-inventory-button:hover {
      background-color: #a93226;
    }
    .pdf-button {
      background-color: #8e44ad;
      color: white;
    }
    .pdf-button:hover {
      background-color: #7d3c98;
    }
    .hidden {
      display: none !important;
    }
    table {
      width: 100%;
      margin: 20px auto;
      border-collapse: collapse;
      background-color: white;
      box-shadow: var(--shadow);
      border-radius: 12px;
      overflow: hidden;
      font-family: 'Tajawal', sans-serif;
    }
    th, td {
      border: 1px solid #ddd;
      padding: 14px;
      text-align: center;
    }
    th {
      background-color: var(--primary);
      color: white;
      font-weight: 700;
    }
    tbody tr:nth-child(even) {
      background-color: #f9f9f9;
    }
    .current-date {
      font-size: 18px;
      margin: 15px 0;
      color: var(--dark);
      font-weight: bold;
      font-family: 'Amiri', sans-serif;
    }
    .past-date {
      color: var(--secondary);
      text-decoration: underline;
      cursor: pointer;
      font-weight: bold;
      font-family: 'Amiri', sans-serif;
    }
    .person-info {
      font-size: 14px;
      color: #555;
      margin-top: 5px;
      font-family: 'Tajawal', sans-serif;
    }
    .actions {
      display: flex;
      justify-content: center;
      gap: 10px;
      margin-top: 20px;
      flex-wrap: wrap;
    }
    .download-all-btn {
      background-color: #8e44ad;
      color: white;
      font-size: 16px;
      padding: 12px 20px;
      margin: 20px auto;
      display: block;
      width: fit-content;
      border-radius: 8px;
      font-family: 'Tajawal', sans-serif;
    }
    .search-container {
      margin: 20px auto;
      text-align: center;
    }
    .search-input {
      padding: 12px;
      width: 300px;
      border: 1px solid #ddd;
      border-radius: 8px;
      font-size: 16px;
      font-family: 'Tajawal', sans-serif;
    }
    footer {
      text-align: center;
      margin-top: 60px;
      padding: 20px;
      background-color: var(--primary);
      color: white;
      font-size: 14px;
      border-top: 3px solid var(--secondary);
      font-family: 'Tajawal', sans-serif;
    }
    footer a {
      color: var(--secondary);
      text-decoration: none;
    }
    footer a:hover {
      text-decoration: underline;
    }
    @media (max-width: 768px) {
      .container {
        padding: 10px;
      }
      .input-group input, .search-input {
        width: 100%;
      }
      button {
        width: 100%;
        margin: 5px 0;
      }
      .actions {
        flex-direction: column;
        align-items: center;
      }
    }
  </style>
</head>
<body>
  <!-- زر تبديل اللغة -->
  <button class="language-button" id="languageButton">English</button>

  <!-- الصفحة الرئيسية -->
  <div id="mainPage" class="container">
    <header>
      <h1 data-ar="سجل مخزن المبيدات" data-en="Store Stock">سجل مخزن المبيدات</h1>
      <p data-ar="نظام إدارة جرد المخازن الذكي" data-en="Smart Store Inventory System">نظام إدارة جرد المخازن الذكي</p>
    </header>

    <div class="input-group">
      <input type="text" id="storeName" placeholder="أدخل اسم المخزن" data-ar-placeholder="أدخل اسم المخزن" data-en-placeholder="Enter store name" />
      <button class="add-button" onclick="addStore()">➕ إضافة مخزن</button>
    </div>
    <div id="storesList"></div>

    <!-- إدارة المبيدات -->
    <h2 data-ar="إدارة المبيدات" data-en="Pesticide Management" style="text-align:center; margin:20px 0; color:var(--primary); font-family: 'Amiri', sans-serif;">إدارة المبيدات</h2>
    <div class="search-container">
      <input type="text" id="searchPesticide" class="search-input" placeholder="ابحث عن مبيد..." data-ar-placeholder="ابحث عن مبيد..." data-en-placeholder="Search pesticide...">
    </div>
    <div class="input-group">
      <input type="text" id="pesticideName" placeholder="أدخل اسم المبيد" data-ar-placeholder="أدخل اسم المبيد" data-en-placeholder="Enter pesticide name" />
      <button class="add-button" onclick="addPesticide()">➕ إضافة مبيد</button>
      <button class="delete-button" onclick="deletePesticideByName()">🗑️ حذف مبيد</button>
    </div>

    <!-- زر تنزيل جميع المبيدات -->
    <button class="download-all-btn" onclick="downloadAllPesticidesPDF()">
      📥 تنزيل جميع المبيدات كـ PDF
    </button>
  </div>

  <!-- صفحة الجرد -->
  <div id="inventoryPage" class="container hidden">
    <button class="button" onclick="goBack()">↩️ رجوع</button>
    <h1 id="storeTitle" style="text-align:center; color:var(--primary); margin:20px 0; font-family: 'Amiri', sans-serif;"></h1>
    <div class="actions">
      <button class="button" onclick="newInventory()">🆕 جرد جديد</button>
      <button class="button" onclick="viewPastInventories()">📋 عمليات جرد سابقة</button>
      <button class="pdf-button" onclick="downloadStoreSummaryPDF()">📄 تقرير المخزن</button>
    </div>

    <!-- قسم الجرد الجديد -->
    <div id="newInventorySection" class="hidden">
      <h2 data-ar="جرد جديد" data-en="New Inventory" style="text-align:center; margin:20px 0; font-family: 'Amiri', sans-serif;">جرد جديد</h2>
      <div class="input-group">
        <input type="text" id="personName" placeholder="اسم المسؤول عن الجرد" data-ar-placeholder="اسم المسؤول عن الجرد" data-en-placeholder="Person in charge" />
      </div>
      <button class="date-button" onclick="recordTodayDate()">📅 تسجيل تاريخ اليوم</button>
      <div id="currentDateDisplay" class="current-date"></div>
      <table id="inventoryTable">
        <thead>
          <tr>
            <th data-ar="اسم المبيد" data-en="Pesticide Name">اسم المبيد</th>
            <th data-ar="الكمية الحالية" data-en="Current Quantity">الكمية الحالية</th>
          </tr>
        </thead>
        <tbody></tbody>
      </table>
      <div class="actions">
        <button class="button" onclick="saveInventory()">💾 حفظ الجرد</button>
        <button class="edit-button" onclick="cancelInventory()">❌ إلغاء</button>
      </div>
    </div>

    <!-- قسم عمليات الجرد السابقة -->
    <div id="pastInventoriesSection" class="hidden">
      <h2 data-ar="عمليات جرد سابقة" data-en="History" style="text-align:center; margin:20px 0; font-family: 'Amiri', sans-serif;">عمليات جرد سابقة</h2>
      <div class="search-container">
        <input type="text" id="searchInventory" class="search-input" placeholder="ابحث في الجرد..." data-ar-placeholder="ابحث في الجرد..." data-en-placeholder="Search inventory...">
      </div>
      <ul id="pastInventoriesList" style="list-style:none; padding:0;"></ul>
    </div>
  </div>

  <!-- الفوتر -->
  <footer>
    تم التطوير بواسطة <a href="mailto:example@example.com" target="_blank">م.أحمد المعشني</a> &copy; <span id="currentYear"></span>
  </footer>

  <!-- مكتبات JavaScript -->
  <script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js"></script>
  <script>
    // التحقق من دعم localStorage
    if (typeof localStorage === 'undefined') {
      alert('متصفحك لا يدعم التخزين المحلي.');
    }

    // المتغيرات
    let pesticides = JSON.parse(localStorage.getItem('pesticides')) || [
      "Actara", "Avaunt", "Benevia", "Cal-Ex Avance", "Coragen", "Decis Expert", "Evisect", "Floramite",
      "Green Lambada", "Karate Zeon", "Milbeknock", "Mospilan", "Movento", "Ortus", "Plesiva Pro", "Radiant",
      "Sivanto Prime", "Starkle", "Sumi Alpha", "Tracer", "Trebon", "Tripsol", "Vertimec", "Voliam Flexi",
      "Vydate", "Hallmark", "Triclopyer", "Amistar Top", "Armetil C", "Curenox", "Equation", "Kocide",
      "Luna Sensation", "Miravise", "Ortiva", "Previcur Energy", "Score", "Top Guard", "Uniform",
      "Bio Cure-B", "Bio Cure-F", "Bio Catch", "Bio Power", "Mustard Oil", "Nimbecidine", "Xen Tari", "Dome Soap", "Sluge Killer"
    ].sort((a, b) => a.localeCompare(b, 'ar')); // ترتيب أبجدي دقيق

    let currentStore = '';
    let inventories = JSON.parse(localStorage.getItem('inventories')) || [];
    let stores = JSON.parse(localStorage.getItem('stores')) || [];
    let currentDate = '';
    let isEnglish = false;
    let currentInventory = null;

    // حفظ البيانات
    function saveData() {
      try {
        localStorage.setItem('pesticides', JSON.stringify(pesticides));
        localStorage.setItem('inventories', JSON.stringify(inventories));
        localStorage.setItem('stores', JSON.stringify(stores));
      } catch (e) {
        alert('فشل حفظ البيانات. الجهاز ممتلئ أو المتصفح قديم.');
      }
    }

    // تحويل اللغة
    document.getElementById('languageButton').addEventListener('click', () => {
      isEnglish = !isEnglish;
      updateLanguage();
      document.getElementById('languageButton').textContent = isEnglish ? 'العربية' : 'English';
    });

    // تحديث النصوص
    function updateLanguage() {
      document.querySelectorAll('[data-ar], [data-en]').forEach(el => {
        el.textContent = isEnglish ? el.getAttribute('data-en') : el.getAttribute('data-ar');
      });
      document.querySelectorAll('[data-ar-placeholder], [data-en-placeholder]').forEach(el => {
        el.placeholder = isEnglish ? el.getAttribute('data-en-placeholder') : el.getAttribute('data-ar-placeholder');
      });
    }

    // البحث الفوري عن المبيدات
    document.getElementById('searchPesticide').addEventListener('input', function() {
      const searchTerm = this.value.toLowerCase();
      const filtered = pesticides.filter(p => p.toLowerCase().includes(searchTerm));
      if (filtered.length === 0 && searchTerm) {
        alert(isEnglish ? 'No pesticides found' : 'لا توجد مبيدات مطابقة للبحث');
      }
    });

    // إضافة مبيد
    function addPesticide() {
      const name = document.getElementById('pesticideName').value.trim();
      if (!name) return alert(isEnglish ? 'Enter a valid name.' : 'أدخل اسمًا صالحًا.');
      if (pesticides.includes(name)) return alert(isEnglish ? 'Already exists.' : 'المبيد موجود مسبقًا.');
      pesticides.push(name);
      pesticides.sort((a, b) => a.localeCompare(b, 'ar'));
      saveData();
      alert(isEnglish ? `Added: ${name}` : `تمت الإضافة: ${name}`);
      document.getElementById('pesticideName').value = '';
    }

    // حذف مبيد
    function deletePesticideByName() {
      const name = document.getElementById('pesticideName').value.trim();
      if (!name) return alert(isEnglish ? 'Enter a name to delete.' : 'أدخل اسمًا للحذف.');
      if (!pesticides.includes(name)) return alert(isEnglish ? 'Not found.' : 'غير موجود.');
      if (!confirm(isEnglish ? `Delete ${name}?` : `حذف ${name}؟`)) return;
      pesticides = pesticides.filter(p => p !== name);
      saveData();
      alert(isEnglish ? `Deleted: ${name}` : `تم الحذف: ${name}`);
      document.getElementById('pesticideName').value = '';
    }

    // إضافة مخزن
    function addStore() {
      const name = document.getElementById('storeName').value.trim();
      if (!name) return alert(isEnglish ? 'Enter store name.' : 'أدخل اسم المخزن.');
      if (stores.includes(name)) return alert(isEnglish ? 'Store already exists.' : 'المخزن موجود مسبقًا.');
      stores.push(name);
      saveData();
      const storeButton = document.createElement('button');
      storeButton.textContent = name;
      storeButton.className = 'store-button';
      storeButton.onclick = () => showInventoryPage(name);
      document.getElementById('storesList').appendChild(storeButton);
      document.getElementById('storeName').value = '';
      alert(isEnglish ? `Store ${name} added successfully!` : `تمت إضافة المخزن ${name} بنجاح!`);
    }

    // فتح صفحة الجرد
    function showInventoryPage(storeName) {
      currentStore = storeName;
      document.getElementById('mainPage').classList.add('hidden');
      document.getElementById('inventoryPage').classList.remove('hidden');
      document.getElementById('storeTitle').textContent = isEnglish ? `Store: ${storeName}` : `جرد المخزن: ${storeName}`;
    }

    // الرجوع
    function goBack() {
      document.getElementById('inventoryPage').classList.add('hidden');
      document.getElementById('mainPage').classList.remove('hidden');
      currentInventory = null;
    }

    // جرد جديد
    function newInventory() {
      document.getElementById('newInventorySection').classList.remove('hidden');
      document.getElementById('pastInventoriesSection').classList.add('hidden');
      document.getElementById('personName').value = '';
      currentInventory = null;
      populateInventoryTable();
    }

    // إلغاء الجرد
    function cancelInventory() {
      if (currentInventory === null) {
        document.getElementById('newInventorySection').classList.add('hidden');
      } else {
        editInventory(currentInventory);
      }
    }

    // تسجيل التاريخ
    function recordTodayDate() {
      const today = new Date();
      const day = String(today.getDate()).padStart(2, '0');
      const month = String(today.getMonth() + 1).padStart(2, '0');
      const year = today.getFullYear();
      currentDate = `${year}/${month}/${day}`;
      document.getElementById('currentDateDisplay').textContent = isEnglish ? 
        `Date: ${currentDate}` : `التاريخ: ${currentDate}`;
    }

    // عرض الجرد السابق
    function viewPastInventories() {
      document.getElementById('newInventorySection').classList.add('hidden');
      document.getElementById('pastInventoriesSection').classList.remove('hidden');
      displayPastInventories();
    }

    // البحث في الجرد السابق
    document.getElementById('searchInventory').addEventListener('input', function() {
      const searchTerm = this.value.toLowerCase();
      const items = document.querySelectorAll('#pastInventoriesList li');
      items.forEach(item => {
        const text = item.textContent.toLowerCase();
        item.style.display = text.includes(searchTerm) ? '' : 'none';
      });
    });

    // تعبئة الجدول
    function populateInventoryTable() {
      const tbody = document.getElementById('inventoryTable').getElementsByTagName('tbody')[0];
      tbody.innerHTML = '';
      pesticides.forEach(pesticide => {
        const row = tbody.insertRow();
        row.innerHTML = `
          <td style="text-align: right; font-weight: 600;">${pesticide}</td>
          <td><input type="number" value="0" min="0" style="width:80px; padding:5px; text-align:center;" /></td>
        `;
      });
    }

    // حفظ الجرد
    function saveInventory() {
      if (!currentDate) {
        alert(isEnglish ? 'Please select a date first.' : 'الرجاء تحديد تاريخ أولاً.');
        return;
      }
      const personName = document.getElementById('personName').value.trim() || (isEnglish ? 'Unspecified' : 'غير محدد');
      const rows = document.querySelectorAll('#inventoryTable tbody tr');
      const items = Array.from(rows).map(row => ({
        pesticide: row.cells[0].textContent,
        quantity: row.cells[1].querySelector('input').value
      }));

      if (currentInventory !== null) {
        inventories[currentInventory] = { date: currentDate, store: currentStore, items, person: personName };
      } else {
        inventories.push({ date: currentDate, store: currentStore, items, person: personName });
      }
      saveData();
      alert(isEnglish ? 'Saved successfully!' : 'تم الحفظ بنجاح!');
      viewPastInventories();
    }

    // عرض الجرد السابق
    function displayPastInventories() {
      const list = document.getElementById('pastInventoriesList');
      list.innerHTML = '';
      const filtered = inventories.filter(inv => inv.store === currentStore);
      if (filtered.length === 0) {
        const li = document.createElement('li');
        li.textContent = isEnglish ? 'No previous inventories found' : 'لا توجد عمليات جرد سابقة';
        li.style.textAlign = 'center';
        li.style.padding = '20px';
        li.style.color = '#777';
        list.appendChild(li);
        return;
      }

      filtered.sort((a, b) => new Date(b.date) - new Date(a.date)).forEach((inv, index) => {
        const originalIndex = inventories.findIndex(i => 
          i.date === inv.date && i.store === inv.store && i.person === inv.person
        );
        const li = document.createElement('li');
        li.style.margin = '10px 0';
        li.style.padding = '15px';
        li.style.border = '1px solid #ddd';
        li.style.borderRadius = '10px';
        li.style.backgroundColor = 'white';
        li.style.display = 'flex';
        li.style.flexDirection = 'column';
        li.style.alignItems = 'center';
        li.style.gap = '10px';

        const dateSpan = document.createElement('span');
        dateSpan.textContent = inv.date;
        dateSpan.className = 'past-date';
        dateSpan.onclick = () => downloadInventoryPDF(originalIndex);

        const personSpan = document.createElement('span');
        personSpan.className = 'person-info';
        personSpan.textContent = isEnglish ? `Person in charge: ${inv.person}` : `المسؤول: ${inv.person}`;

        const buttonsDiv = document.createElement('div');
        buttonsDiv.style.display = 'flex';
        buttonsDiv.style.gap = '10px';
        buttonsDiv.style.flexWrap = 'wrap';
        buttonsDiv.style.justifyContent = 'center';

        const editBtn = document.createElement('button');
        editBtn.textContent = isEnglish ? 'Edit' : 'تعديل';
        editBtn.className = 'edit-button';
        editBtn.onclick = () => editInventory(originalIndex);

        const deleteBtn = document.createElement('button');
        deleteBtn.textContent = isEnglish ? 'Delete' : 'حذف';
        deleteBtn.className = 'delete-inventory-button';
        deleteBtn.onclick = () => deleteInventory(originalIndex);

        const pdfBtn = document.createElement('button');
        pdfBtn.textContent = isEnglish ? 'PDF' : 'تنزيل PDF';
        pdfBtn.className = 'pdf-button';
        pdfBtn.onclick = () => downloadInventoryPDF(originalIndex);

        buttonsDiv.appendChild(editBtn);
        buttonsDiv.appendChild(deleteBtn);
        buttonsDiv.appendChild(pdfBtn);
        li.appendChild(dateSpan);
        li.appendChild(personSpan);
        li.appendChild(buttonsDiv);
        list.appendChild(li);
      });
    }

    // تعديل الجرد
    function editInventory(index) {
      const inv = inventories[index];
      if (!inv) return;
      currentInventory = index;
      currentDate = inv.date;
      document.getElementById('currentDateDisplay').textContent = isEnglish ? 
        `Date: ${currentDate}` : `التاريخ: ${currentDate}`;
      document.getElementById('personName').value = inv.person;
      populateInventoryTable();
      const rows = document.querySelectorAll('#inventoryTable tbody tr');
      inv.items.forEach(item => {
        const row = Array.from(rows).find(r => r.cells[0].textContent === item.pesticide);
        if (row) row.cells[1].querySelector('input').value = item.quantity;
      });
      document.getElementById('newInventorySection').classList.remove('hidden');
      document.getElementById('pastInventoriesSection').classList.add('hidden');
    }

    // حذف الجرد
    function deleteInventory(index) {
      if (!confirm(isEnglish ? 'Delete this inventory?' : 'هل تريد حذف هذا الجرد؟')) return;
      inventories.splice(index, 1);
      saveData();
      displayPastInventories();
      alert(isEnglish ? 'Deleted!' : 'تم الحذف!');
    }

    // تنزيل تقرير الجرد كـ PDF (مُحسّن)
    async function downloadInventoryPDF(index) {
      const inv = inventories[index];
      const { jsPDF } = window.jspdf;

      // ترتيب المبيدات أبجديًا
      const sortedItems = [...inv.items].sort((a, b) => a.pesticide.localeCompare(b.pesticide, 'ar'));

      const tempDiv = document.createElement('div');
      tempDiv.style.position = 'absolute';
      tempDiv.style.left = '-9999px';
      tempDiv.style.width = '210mm';
      tempDiv.style.padding = '15px';
      tempDiv.style.fontFamily = "'Amiri', 'Tajawal', sans-serif";
      tempDiv.style.direction = 'rtl';
      tempDiv.style.backgroundColor = 'white';
      tempDiv.style.color = '#333';
      tempDiv.style.fontSize = '14px';

      let tableHtml = '';
      const rowsPerPage = 28; // عدد مناسب لحجم الصفحة

      for (let i = 0; i < sortedItems.length; i += rowsPerPage) {
        const pageItems = sortedItems.slice(i, i + rowsPerPage);
        tableHtml += `
          <table style="width: 100%; border-collapse: collapse; margin: 10px 0; font-size: 13px;">
            <thead>
              <tr style="background-color: #2c3e50; color: white;">
                <th style="border: 1px solid #ddd; padding: 8px; text-align: center; font-weight: bold;">اسم المبيد</th>
                <th style="border: 1px solid #ddd; padding: 8px; text-align: center; font-weight: bold;">الكمية</th>
              </tr>
            </thead>
            <tbody>
              ${pageItems.map(item => `
                <tr>
                  <td style="border: 1px solid #ddd; padding: 6px; text-align: right; white-space: nowrap; font-weight: 600;">${item.pesticide}</td>
                  <td style="border: 1px solid #ddd; padding: 6px; text-align: center; font-weight: 600;">${item.quantity}</td>
                </tr>
              `).join('')}
            </tbody>
          </table>
        `;
        if (i + rowsPerPage < sortedItems.length) {
          tableHtml += '<div style="page-break-before: always;"></div>';
        }
      }

      tempDiv.innerHTML = `
        <div style="text-align: center; margin-bottom: 15px;">
          <h1 style="color: #2c3e50; font-size: 22px; margin-bottom: 5px; font-weight: 700; font-family: 'Amiri', sans-serif;">تقرير جرد المخزن</h1>
          <h2 style="font-size: 18px; color: #555; font-family: 'Tajawal', sans-serif;">${inv.date}</h2>
        </div>
        <div style="margin-bottom: 20px; font-size: 15px; line-height: 1.8;">
          <p><strong style="color: #2c3e50;">اسم المخزن:</strong> ${inv.store}</p>
          <p><strong style="color: #2c3e50;">المسؤول عن الجرد:</strong> ${inv.person}</p>
          <p><strong style="color: #2c3e50;">إجمالي المبيدات:</strong> ${sortedItems.length}</p>
        </div>
        ${tableHtml}
        <div style="text-align: center; margin-top: 30px; font-size: 12px; color: #777; border-top: 1px solid #eee; padding-top: 15px;">
          تم إنشاء التقرير في: ${new Date().toLocaleString('ar-SA')}
        </div>
      `;

      document.body.appendChild(tempDiv);

      try {
        const canvas = await html2canvas(tempDiv, {
          scale: 2,
          useCORS: true,
          allowTaint: true,
          logging: false,
          backgroundColor: 'white'
        });

        const pdf = new jsPDF({
          orientation: 'portrait',
          unit: 'mm',
          format: 'a4'
        });

        const imgData = canvas.toDataURL('image/jpeg', 0.95);
        const pdfWidth = pdf.internal.pageSize.getWidth();
        const pdfHeight = (canvas.height * pdfWidth) / canvas.width;

        pdf.addImage(imgData, 'JPEG', 0, 0, pdfWidth, pdfHeight);
        pdf.save(`تقرير_جرد_${inv.store}_${inv.date}.pdf`);
      } catch (error) {
        console.error('خطأ في إنشاء PDF:', error);
        alert('حدث خطأ أثناء إنشاء الملف. يرجى المحاولة مرة أخرى.');
      } finally {
        document.body.removeChild(tempDiv);
      }
    }

    // تنزيل جميع المبيدات كـ PDF
    async function downloadAllPesticidesPDF() {
      if (pesticides.length === 0) {
        alert(isEnglish ? 'No pesticides to export.' : 'لا توجد مبيدات لتصديرها.');
        return;
      }

      const { jsPDF } = window.jspdf;
      const tempDiv = document.createElement('div');
      tempDiv.style.position = 'absolute';
      tempDiv.style.left = '-9999px';
      tempDiv.style.width = '210mm';
      tempDiv.style.padding = '20px';
      tempDiv.style.fontFamily = "'Amiri', sans-serif";
      tempDiv.style.direction = 'rtl';
      tempDiv.style.backgroundColor = 'white';

      const sortedPesticides = [...pesticides].sort((a, b) => a.localeCompare(b, 'ar'));

      tempDiv.innerHTML = `
        <div style="text-align: center; margin-bottom: 20px;">
          <h1 style="color: #2c3e50; font-size: 26px; margin-bottom: 8px; font-weight: 700;">قائمة جميع المبيدات</h1>
          <p style="font-size: 16px; color: #555;">تاريخ التصدير: ${new Date().toLocaleDateString()}</p>
        </div>
        <div style="column-count: 2; column-gap: 30px; font-size: 16px; line-height: 2;">
          ${sortedPesticides.map((p, i) => `<div style="margin-bottom: 8px;"><strong>${i+1}.</strong> ${p}</div>`).join('')}
        </div>
        <div style="text-align: center; margin-top: 30px; font-size: 14px; color: #777;">
          <strong>إجمالي العدد:</strong> ${sortedPesticides.length} مبيد
        </div>
      `;

      document.body.appendChild(tempDiv);

      try {
        const canvas = await html2canvas(tempDiv, {
          scale: 2,
          useCORS: true,
          allowTaint: true,
          logging: false,
          backgroundColor: 'white'
        });

        const pdf = new jsPDF({
          orientation: 'portrait',
          unit: 'mm',
          format: 'a4'
        });

        const imgData = canvas.toDataURL('image/jpeg', 0.95);
        const pdfWidth = pdf.internal.pageSize.getWidth();
        const pdfHeight = (canvas.height * pdfWidth) / canvas.width;

        pdf.addImage(imgData, 'JPEG', 0, 0, pdfWidth, pdfHeight);
        pdf.save('جميع_المبيدات.pdf');
      } catch (error) {
        console.error('خطأ في إنشاء PDF:', error);
        alert('حدث خطأ أثناء إنشاء الملف.');
      } finally {
        document.body.removeChild(tempDiv);
      }
    }

    // تنزيل ملخص المخزن كـ PDF
    async function downloadStoreSummaryPDF() {
      const storeInventories = inventories.filter(inv => inv.store === currentStore);
      if (storeInventories.length === 0) {
        alert(isEnglish ? 'No inventory data for this store.' : 'لا توجد بيانات جرد لهذا المخزن.');
        return;
      }

      const { jsPDF } = window.jspdf;
      const tempDiv = document.createElement('div');
      tempDiv.style.position = 'absolute';
      tempDiv.style.left = '-9999px';
      tempDiv.style.width = '210mm';
      tempDiv.style.padding = '20px';
      tempDiv.style.fontFamily = "'Amiri', sans-serif";
      tempDiv.style.direction = 'rtl';
      tempDiv.style.backgroundColor = 'white';

      const sorted = storeInventories.sort((a, b) => new Date(b.date) - new Date(a.date));
      const latest = sorted[0];
      const count = storeInventories.length;
      const first = sorted[sorted.length - 1].date;

      tempDiv.innerHTML = `
        <div style="text-align: center; margin-bottom: 20px;">
          <h1 style="color: #2c3e50; font-size: 26px; margin-bottom: 8px; font-weight: 700;">ملخص المخزن</h1>
          <h2 style="font-size: 20px; color: #555;">${currentStore}</h2>
        </div>
        <div style="margin-bottom: 30px; font-size: 16px; line-height: 1.8;">
          <p><strong>عدد عمليات الجرد:</strong> ${count}</p>
          <p><strong>أول عملية جرد:</strong> ${first}</p>
          <p><strong>آخر عملية جرد:</strong> ${latest.date}</p>
          <p><strong>المسؤول عن آخر جرد:</strong> ${latest.person}</p>
        </div>
        <div style="text-align: center; margin-top: 40px; font-size: 12px; color: #777; border-top: 1px solid #eee; padding-top: 15px;">
          تم إنشاء هذا التقرير باستخدام نظام إدارة مخزن المبيدات
        </div>
      `;

      document.body.appendChild(tempDiv);

      try {
        const canvas = await html2canvas(tempDiv, {
          scale: 2,
          useCORS: true,
          allowTaint: true,
          logging: false,
          backgroundColor: 'white'
        });

        const pdf = new jsPDF({
          orientation: 'portrait',
          unit: 'mm',
          format: 'a4'
        });

        const imgData = canvas.toDataURL('image/jpeg', 0.95);
        const pdfWidth = pdf.internal.pageSize.getWidth();
        const pdfHeight = (canvas.height * pdfWidth) / canvas.width;

        pdf.addImage(imgData, 'JPEG', 0, 0, pdfWidth, pdfHeight);
        pdf.save(`ملخص_${currentStore}.pdf`);
      } catch (error) {
        console.error('خطأ في إنشاء PDF:', error);
        alert('حدث خطأ أثناء إنشاء الملف.');
      } finally {
        document.body.removeChild(tempDiv);
      }
    }

    // تحميل البيانات عند بدء التشغيل
    window.onload = () => {
      document.getElementById('currentYear').textContent = new Date().getFullYear();
      stores = JSON.parse(localStorage.getItem('stores')) || [];
      stores.forEach(store => {
        const storeButton = document.createElement('button');
        storeButton.textContent = store;
        storeButton.className = 'store-button';
        storeButton.onclick = () => showInventoryPage(store);
        document.getElementById('storesList').appendChild(storeButton);
      });
      updateLanguage();
    };
  </script>
</body>
</html>
