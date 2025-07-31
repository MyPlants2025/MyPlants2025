<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <meta name="theme-color" content="#2c3e50">
  <title>سجل مخزن المبيدات | Store Stock</title>
  <link rel="manifest" href="manifest.json">
  <!-- خط عربي واضح لدعم اللغة في PDF -->
  <link href="https://fonts.googleapis.com/css2?family=Amiri&display=swap" rel="stylesheet">
  <style>
    :root {
      --primary: #2c3e50;
      --secondary: #3498db;
      --success: #2ecc71;
      --danger: #e74c3c;
      --warning: #f39c12;
      --light: #f4f4f9;
      --shadow: 0 4px 12px rgba(0,0,0,0.1);
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: 'Segoe UI', 'Tahoma', sans-serif;
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
    }

    .language-button:hover {
      background-color: #1a252f;
    }

    .input-group {
      margin: 20px 0;
      text-align: center;
    }

    .input-group input {
      padding: 12px;
      font-size: 16px;
      width: 280px;
      border: 1px solid #ddd;
      border-radius: 8px;
      outline: none;
      margin: 5px;
    }

    button {
      padding: 10px 20px;
      font-size: 16px;
      cursor: pointer;
      border: none;
      border-radius: 8px;
      margin: 5px;
      transition: background 0.3s;
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
    }

    th, td {
      border: 1px solid #ddd;
      padding: 14px;
      text-align: center;
    }

    th {
      background-color: var(--secondary);
      color: white;
    }

    tbody tr:nth-child(even) {
      background-color: #f9f9f9;
    }

    .current-date {
      font-size: 18px;
      margin: 15px 0;
      color: var(--dark);
      font-weight: bold;
    }

    .past-date {
      color: var(--secondary);
      text-decoration: underline;
      cursor: pointer;
      font-weight: bold;
    }

    .person-info {
      font-size: 14px;
      color: #555;
      margin-top: 5px;
    }

    .actions {
      display: flex;
      justify-content: center;
      gap: 10px;
      margin-top: 20px;
    }

    footer {
      text-align: center;
      margin-top: 60px;
      padding: 20px;
      background-color: var(--primary);
      color: white;
      font-size: 14px;
      border-top: 3px solid var(--secondary);
    }

    footer a {
      color: var(--secondary);
      text-decoration: none;
    }

    footer a:hover {
      text-decoration: underline;
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
    <h2 data-ar="إدارة المبيدات" data-en="Pesticide Management" style="text-align:center; margin:20px 0; color:var(--primary);">إدارة المبيدات</h2>
    <div class="input-group">
      <input type="text" id="pesticideName" placeholder="أدخل اسم المبيد" data-ar-placeholder="أدخل اسم المبيد" data-en-placeholder="Enter pesticide name" />
      <button class="add-button" onclick="addPesticide()">➕ إضافة مبيد</button>
      <button class="delete-button" onclick="deletePesticideByName()">🗑️ حذف مبيد</button>
    </div>
  </div>

  <!-- صفحة الجرد -->
  <div id="inventoryPage" class="container hidden">
    <button class="button" onclick="goBack()">↩️ رجوع</button>
    <h1 id="storeTitle" style="text-align:center; color:var(--primary); margin:20px 0;"></h1>

    <div class="actions">
      <button class="button" onclick="newInventory()">🆕 جرد جديد</button>
      <button class="button" onclick="viewPastInventories()">📋 عمليات جرد سابقة</button>
    </div>

    <!-- قسم الجرد الجديد -->
    <div id="newInventorySection" class="hidden">
      <h2 data-ar="جرد جديد" data-en="New Inventory" style="text-align:center; margin:20px 0;">جرد جديد</h2>
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

      <button class="button" onclick="saveInventory()">💾 حفظ الجرد</button>
    </div>

    <!-- قسم عمليات الجرد السابقة -->
    <div id="pastInventoriesSection" class="hidden">
      <h2 data-ar="عمليات جرد سابقة" data-en="History" style="text-align:center; margin:20px 0;">عمليات جرد سابقة</h2>
      <ul id="pastInventoriesList" style="list-style:none; padding:0;"></ul>
    </div>
  </div>

  <!-- الفوتر -->
  <footer>
    تم التطوير بواسطة <a href="mailto:example@example.com" target="_blank">م.أحمد المعشني</a> &copy; 2025
  </footer>

  <!-- تحميل المكتبات -->
  <script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf-autotable/3.5.25/jspdf.plugin.autotable.min.js"></script>

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
    ];
    let currentStore = '';
    let inventories = JSON.parse(localStorage.getItem('inventories')) || [];
    let currentDate = '';
    let isEnglish = false;

    // حفظ البيانات
    function saveData() {
      try {
        localStorage.setItem('pesticides', JSON.stringify(pesticides));
        localStorage.setItem('inventories', JSON.stringify(inventories));
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

    // إضافة مبيد
    function addPesticide() {
      const name = document.getElementById('pesticideName').value.trim();
      if (!name) return alert(isEnglish ? 'Enter a valid name.' : 'أدخل اسمًا صالحًا.');
      if (pesticides.includes(name)) return alert(isEnglish ? 'Already exists.' : 'المبيد موجود مسبقًا.');
      pesticides.push(name);
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
      const storeButton = document.createElement('button');
      storeButton.textContent = name;
      storeButton.className = 'store-button';
      storeButton.onclick = () => showInventoryPage(name);
      document.getElementById('storesList').appendChild(storeButton);
      document.getElementById('storeName').value = '';
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
    }

    // جرد جديد
    function newInventory() {
      document.getElementById('newInventorySection').classList.remove('hidden');
      document.getElementById('pastInventoriesSection').classList.add('hidden');
      document.getElementById('personName').value = '';
      populateInventoryTable();
    }

    // تسجيل التاريخ
    function recordTodayDate() {
      const today = new Date().toLocaleDateString();
      currentDate = today;
      document.getElementById('currentDateDisplay').textContent = isEnglish ? `التاريخ: ${today}` : `التاريخ: ${today}`;
    }

    // عرض الجرد السابق
    function viewPastInventories() {
      document.getElementById('newInventorySection').classList.add('hidden');
      document.getElementById('pastInventoriesSection').classList.remove('hidden');
      displayPastInventories();
    }

    // تعبئة الجدول
    function populateInventoryTable() {
      const tbody = document.getElementById('inventoryTable').getElementsByTagName('tbody')[0];
      tbody.innerHTML = '';
      pesticides.forEach(pesticide => {
        const row = tbody.insertRow();
        row.innerHTML = `
          <td>${pesticide}</td>
          <td><input type="number" value="0" min="0" style="width:80px; padding:5px; text-align:center;" /></td>
        `;
      });
    }

    // حفظ الجرد
    function saveInventory() {
      if (!currentDate) recordTodayDate();
      const personName = document.getElementById('personName').value.trim() || 'غير محدد';
      const rows = document.querySelectorAll('#inventoryTable tbody tr');
      const items = Array.from(rows).map(row => ({
        pesticide: row.cells[0].textContent,
        quantity: row.cells[1].querySelector('input').value
      }));
      inventories.push({ date: currentDate, store: currentStore, items, person: personName });
      saveData();
      alert(isEnglish ? 'Saved successfully!' : 'تم الحفظ بنجاح!');
    }

    // عرض الجرد السابق
    function displayPastInventories() {
      const list = document.getElementById('pastInventoriesList');
      list.innerHTML = '';
      const filtered = inventories.filter(inv => inv.store === currentStore);
      filtered.forEach((inv, index) => {
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
        dateSpan.onclick = () => downloadInventoryPDF(index);

        const personSpan = document.createElement('span');
        personSpan.className = 'person-info';
        personSpan.textContent = isEnglish ? `المسؤول: ${inv.person}` : `المسؤول: ${inv.person}`;

        const buttonsDiv = document.createElement('div');
        buttonsDiv.style.display = 'flex';
        buttonsDiv.style.gap = '10px';

        const editBtn = document.createElement('button');
        editBtn.textContent = isEnglish ? 'Edit' : 'تعديل';
        editBtn.className = 'edit-button';
        editBtn.onclick = () => editInventory(index);

        const deleteBtn = document.createElement('button');
        deleteBtn.textContent = isEnglish ? 'Delete' : 'حذف';
        deleteBtn.className = 'delete-inventory-button';
        deleteBtn.onclick = () => deleteInventory(index);

        const pdfBtn = document.createElement('button');
        pdfBtn.textContent = isEnglish ? 'PDF' : 'تنزيل PDF';
        pdfBtn.className = 'pdf-button';
        pdfBtn.onclick = () => downloadInventoryPDF(index);

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
      const inv = inventories.filter(i => i.store === currentStore)[index];
      if (!inv) return;
      currentDate = inv.date;
      document.getElementById('currentDateDisplay').textContent = isEnglish ? `التاريخ: ${currentDate}` : `التاريخ: ${currentDate}`;
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
      const inv = inventories.filter(i => i.store === currentStore)[index];
      inventories = inventories.filter(i => !(i.store === inv.store && i.date === inv.date && i.person === inv.person));
      saveData();
      displayPastInventories();
      alert(isEnglish ? 'Deleted!' : 'تم الحذف!');
    }

    // تنزيل PDF (يدعم العربية بشكل واضح)
    function downloadInventoryPDF(index) {
      const inv = inventories.filter(i => i.store === currentStore)[index];
      const { jsPDF } = window.jspdf;
      const doc = new jsPDF({
        orientation: 'portrait',
        unit: 'mm',
        format: 'a4'
      });

      // تضمين خط عربي واضح
      doc.setFont('Amiri', 'normal');
      doc.setFontSize(20);

      const title = isEnglish ? `Inventory Report - ${inv.date}` : `تقرير الجرد - ${inv.date}`;
      const storeText = isEnglish ? `المخزن: ${inv.store}` : `المخزن: ${inv.store}`;
      const personText = isEnglish ? `المسؤول: ${inv.person}` : `المسؤول: ${inv.person}`;
      const headers = isEnglish ? [['Pesticide', 'Quantity']] : [['اسم المبيد', 'الكمية']];
      const data = inv.items.map(item => [item.pesticide, item.quantity]);

      doc.text(title, 14, 15);
      doc.setFontSize(16);
      doc.text(storeText, 14, 25);
      doc.text(personText, 14, 32);

      doc.autoTable({
        head: headers,
        body: data,
        startY: 40,
        theme: 'grid',
        styles: {
          font: 'Amiri',
          halign: 'right',
          rtl: true,
          fontSize: 12,
          cellPadding: 4
        },
        headStyles: {
          fillColor: [52, 152, 219],
          textColor: 255,
          halign: 'center'
        },
        columnStyles: {
          0: { cellWidth: 'auto' },
          1: { halign: 'center' }
        }
      });

      doc.save(isEnglish ? `Inventory_${inv.date}.pdf` : `جرد_${inv.date}.pdf`);
    }

    // تحميل البيانات
    window.onload = () => {
      updateLanguage();
      if (inventories.length > 0) viewPastInventories();
    };
  </script>
</body>
</html>
