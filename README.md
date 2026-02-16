here<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>منصة صحة - الاستعلام عن الإجازات المرضية</title>
  <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;500;600;700&display=swap" rel="stylesheet" />
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css" />
  <style>
    :root {
      --primary-blue: #2e6fb3;
      --primary-dark-blue: #1a4a7a;
      --primary-light-blue: #67b3f5;
      --accent-blue: #e0f0ff;
      --text-dark: #333333;
      --text-gray: #6d7781;
      --bg-gray: #f5f9fd;
      --error-red: #dc3545;
      --success-green: #28a745;
      --warning-yellow: #ffc107;
      --shadow-light: 0 4px 12px rgba(0, 0, 0, 0.08);
      --shadow-medium: 0 6px 20px rgba(0, 0, 0, 0.1);
    }
    
    * {
      font-family: 'Cairo', sans-serif !important;
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }
    
    body {
      background-color: var(--bg-gray);
      margin: 0;
      padding: 0;
      direction: rtl;
      min-height: 100vh;
      display: flex;
      flex-direction: column;
    }
    
    /* Header Styles */
    .header {
      background-color: white;
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 12px 20px;
      box-shadow: var(--shadow-light);
      position: sticky;
      top: 0;
      z-index: 1000;
      animation: slideDown 0.5s ease-out;
    }
    
    @keyframes slideDown {
      from { transform: translateY(-100%); opacity: 0; }
      to { transform: translateY(0); opacity: 1; }
    }
    
    .menu-icon {
      font-size: 28px;
      color: var(--primary-blue);
      cursor: pointer;
      transition: transform 0.3s ease;
      padding: 5px;
      border-radius: 4px;
    }
    
    .menu-icon:hover {
      transform: scale(1.1);
      background-color: var(--accent-blue);
    }
    
    .logo {
      height: 65px;
      object-fit: contain;
      transition: transform 0.3s ease;
    }
    
    .logo:hover {
      transform: scale(1.05);
    }
    
    /* Main Content */
    .main-content {
      flex: 1;
      padding: 20px;
      max-width: 800px;
      margin: 0 auto;
      width: 100%;
    }
    
    .page-title-container {
      text-align: center;
      margin: 30px 0 20px;
      position: relative;
    }
    
    .page-title {
      color: var(--primary-blue);
      font-weight: 800;
      font-size: 42px;
      display: inline-block;
      position: relative;
      padding: 0 15px;
      z-index: 1;
    }
    
    .page-title::before {
      content: "";
      position: absolute;
      top: 50%;
      left: 0;
      width: 100%;
      height: 18px;
      background-color: var(--accent-blue);
      transform: translateY(-50%);
      z-index: -1;
      border-radius: 4px;
      box-shadow: 0 3px 6px rgba(0, 0, 0, 0.05);
    }
    
    .page-description {
      color: var(--text-gray);
      text-align: center;
      font-size: 18px;
      line-height: 1.7;
      margin: 15px auto 35px;
      max-width: 700px;
      padding: 0 15px;
      text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.05);
    }
    
    /* Form Styles */
    .form-container {
      background-color: white;
      border-radius: 12px;
      padding: 30px;
      box-shadow: var(--shadow-medium);
      margin-bottom: 30px;
      transition: transform 0.3s ease;
    }
    
    .form-container:hover {
      transform: translateY(-5px);
    }
    
    .input-container {
      position: relative;
      margin-bottom: 24px;
    }
    
    .input-label {
      display: block;
      margin-bottom: 8px;
      color: var(--primary-dark-blue);
      font-weight: 600;
      font-size: 16px;
    }
    
    .input-field {
      width: 100%;
      padding: 14px 16px;
      font-size: 16px;
      border: 2px solid #e1e8f0;
      border-radius: 10px;
      background-color: white;
      text-align: right;
      transition: all 0.3s ease;
      color: var(--text-dark);
    }
    
    .input-field:focus {
      border-color: var(--primary-light-blue);
      outline: none;
      box-shadow: 0 0 0 3px rgba(103, 179, 245, 0.2);
    }
    
    .input-field::placeholder {
      color: #a0aec0;
    }
    
    /* Button Styles */
    .button-container {
      display: flex;
      justify-content: center;
      gap: 15px;
      margin-top: 25px;
      flex-wrap: wrap;
    }
    
    .btn {
      padding: 14px 28px;
      border: none;
      border-radius: 10px;
      font-size: 16px;
      font-weight: 600;
      cursor: pointer;
      transition: all 0.3s ease;
      display: flex;
      align-items: center;
      justify-content: center;
      min-width: 160px;
      text-decoration: none;
    }
    
    .btn-primary {
      background-color: var(--primary-blue);
      color: white;
    }
    
    .btn-primary:hover {
      background-color: var(--primary-dark-blue);
      transform: translateY(-3px);
      box-shadow: 0 6px 12px rgba(46, 111, 179, 0.3);
    }
    
    .btn-primary:active {
      transform: translateY(-1px);
    }
    
    .btn-primary.loading {
      background-color: var(--primary-dark-blue);
      cursor: wait;
    }
    
    .btn-secondary {
      background-color: white;
      color: var(--primary-blue);
      border: 2px solid var(--primary-blue);
    }
    
    .btn-secondary:hover {
      background-color: var(--accent-blue);
      transform: translateY(-3px);
    }
    
    .btn-tertiary {
      background-color: #f8f9fa;
      color: var(--text-gray);
      border: 2px solid #e1e8f0;
    }
    
    .btn-tertiary:hover {
      background-color: #e9ecef;
      transform: translateY(-3px);
    }
    
    /* Loading Spinner */
    .loading-spinner {
      display: inline-block;
      width: 18px;
      height: 18px;
      border: 3px solid rgba(255, 255, 255, 0.3);
      border-radius: 50%;
      border-top-color: white;
      animation: spin 1s ease-in-out infinite;
      margin-left: 10px;
      vertical-align: middle;
      display: none;
    }
    
    @keyframes spin {
      to { transform: rotate(360deg); }
    }
    
    /* Messages */
    .message-box {
      padding: 16px;
      margin: 20px 0;
      border-radius: 10px;
      text-align: center;
      font-weight: 500;
      display: none;
      animation: fadeIn 0.5s ease;
    }
    
    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(-10px); }
      to { opacity: 1; transform: translateY(0); }
    }
    
    .message-error {
      background-color: #fee;
      color: var(--error-red);
      border: 1px solid #fcc;
    }
    
    .message-empty {
      background-color: #fff9e6;
      color: #856404;
      border: 1px solid #ffeaa7;
      font-weight: normal;
    }
    
    /* Result Box */
    .result-box {
      background-color: white;
      padding: 30px;
      margin: 30px auto;
      border-radius: 12px;
      box-shadow: var(--shadow-medium);
      display: none;
      animation: slideUp 0.5s ease;
    }
    
    @keyframes slideUp {
      from { opacity: 0; transform: translateY(20px); }
      to { opacity: 1; transform: translateY(0); }
    }
    
    .result-title {
      color: var(--primary-blue);
      font-weight: 700;
      font-size: 24px;
      margin-bottom: 25px;
      text-align: center;
      padding-bottom: 10px;
      border-bottom: 2px solid var(--accent-blue);
    }
    
    .result-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
      gap: 20px;
      margin-top: 20px;
    }
    
    .result-item {
      padding: 15px;
      background-color: var(--bg-gray);
      border-radius: 8px;
      transition: transform 0.3s ease;
    }
    
    .result-item:hover {
      transform: translateY(-3px);
      background-color: #edf5ff;
    }
    
    .result-label {
      font-weight: 700;
      color: var(--primary-dark-blue);
      margin-bottom: 8px;
      font-size: 15px;
    }
    
    .result-value {
      color: var(--text-dark);
      font-size: 17px;
      line-height: 1.5;
    }
    
    /* Footer */
    .footer {
      background-color: var(--primary-dark-blue);
      color: white;
      padding: 40px 20px 30px;
      text-align: center;
      margin-top: auto;
    }
    
    .footer-content {
      max-width: 1200px;
      margin: 0 auto;
    }
    
    .footer-logo {
      height: 70px;
      margin-bottom: 20px;
    }
    
    .footer-description {
      font-size: 15px;
      line-height: 1.7;
      max-width: 800px;
      margin: 0 auto 25px;
      color: rgba(255, 255, 255, 0.9);
    }
    
    .footer-sections {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 40px;
      margin: 30px 0;
    }
    
    .footer-section {
      flex: 1;
      min-width: 250px;
      text-align: right;
    }
    
    .footer-title {
      font-weight: 700;
      font-size: 18px;
      margin-bottom: 15px;
      position: relative;
      display: inline-block;
      color: white;
    }
    
    .footer-title::after {
      content: "";
      position: absolute;
      bottom: -8px;
      right: 0;
      width: 100%;
      height: 3px;
      background-color: var(--primary-light-blue);
      border-radius: 2px;
    }
    
    .footer-links {
      margin-top: 15px;
    }
    
    .footer-link {
      display: block;
      color: rgba(255, 255, 255, 0.85);
      margin-bottom: 10px;
      text-decoration: none;
      transition: color 0.3s ease;
      padding: 5px 0;
    }
    
    .footer-link:hover {
      color: white;
      text-decoration: underline;
    }
    
    .contact-info {
      font-size: 15px;
      line-height: 1.8;
      color: rgba(255, 255, 255, 0.9);
    }
    
    .contact-item {
      margin-bottom: 10px;
      display: flex;
      align-items: center;
      justify-content: flex-end;
      gap: 10px;
    }
    
    .contact-icon {
      width: 24px;
      text-align: center;
    }
    
    .footer-partners {
      display: flex;
      justify-content: center;
      align-items: center;
      gap: 30px;
      margin: 30px 0;
      flex-wrap: wrap;
    }
    
    .partner-logo {
      height: 50px;
    }
    
    .divider {
      height: 50px;
      width: 2px;
      background-color: rgba(255, 255, 255, 0.3);
    }
    
    .footer-bottom {
      margin-top: 30px;
      padding-top: 20px;
      border-top: 1px solid rgba(255, 255, 255, 0.2);
      color: rgba(255, 255, 255, 0.8);
      font-size: 14px;
      line-height: 1.6;
    }
    
    /* Popup Menu */
    .popup-menu {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100vh;
      background-color: rgba(0, 0, 0, 0.7);
      display: none;
      flex-direction: column;
      justify-content: flex-start;
      align-items: center;
      padding-top: 80px;
      z-index: 2000;
      backdrop-filter: blur(5px);
      animation: fadeInBg 0.3s ease;
    }
    
    @keyframes fadeInBg {
      from { opacity: 0; }
      to { opacity: 1; }
    }
    
    .menu-content {
      background-color: white;
      width: 90%;
      max-width: 400px;
      border-radius: 12px;
      padding: 30px;
      box-shadow: 0 10px 40px rgba(0, 0, 0, 0.2);
      animation: slideInMenu 0.4s ease;
    }
    
    @keyframes slideInMenu {
      from { transform: translateY(-30px); opacity: 0; }
      to { transform: translateY(0); opacity: 1; }
    }
    
    .menu-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 25px;
      padding-bottom: 15px;
      border-bottom: 2px solid var(--accent-blue);
    }
    
    .menu-title {
      color: var(--primary-blue);
      font-weight: 700;
      font-size: 22px;
    }
    
    .close-btn {
      font-size: 28px;
      color: var(--text-gray);
      cursor: pointer;
      padding: 5px;
      border-radius: 50%;
      width: 40px;
      height: 40px;
      display: flex;
      align-items: center;
      justify-content: center;
      transition: all 0.3s ease;
    }
    
    .close-btn:hover {
      background-color: var(--accent-blue);
      color: var(--primary-blue);
    }
    
    .menu-items {
      display: flex;
      flex-direction: column;
      gap: 15px;
    }
    
    .menu-item {
      font-size: 17px;
      color: var(--primary-blue);
      padding: 15px;
      border-radius: 8px;
      text-decoration: none;
      transition: all 0.3s ease;
      display: flex;
      align-items: center;
      gap: 12px;
    }
    
    .menu-item:hover {
      background-color: var(--accent-blue);
      transform: translateX(-5px);
    }
    
    .menu-icon-item {
      width: 24px;
      text-align: center;
      font-size: 18px;
    }
    
    .menu-login {
      background-color: var(--primary-blue);
      color: white;
      padding: 16px;
      border-radius: 10px;
      margin-top: 20px;
      font-size: 17px;
      font-weight: 600;
      cursor: pointer;
      display: flex;
      align-items: center;
      justify-content: center;
      text-decoration: none;
      transition: all 0.3s ease;
    }
    
    .menu-login:hover {
      background-color: var(--primary-dark-blue);
      transform: translateY(-3px);
    }
    
    /* Responsive */
    @media (max-width: 768px) {
      .page-title {
        font-size: 34px;
      }
      
      .page-description {
        font-size: 16px;
      }
      
      .form-container {
        padding: 20px;
      }
      
      .button-container {
        flex-direction: column;
        align-items: center;
      }
      
      .btn {
        width: 100%;
        max-width: 300px;
      }
      
      .result-grid {
        grid-template-columns: 1fr;
      }
      
      .footer-sections {
        flex-direction: column;
        gap: 30px;
      }
      
      .footer-section {
        text-align: center;
      }
      
      .footer-title::after {
        right: 50%;
        transform: translateX(50%);
        width: 80%;
      }
      
      .contact-item {
        justify-content: center;
      }
    }
    
    @media (max-width: 480px) {
      .page-title {
        font-size: 28px;
      }
      
      .header {
        padding: 10px 15px;
      }
      
      .logo {
        height: 55px;
      }
      
      .menu-content {
        padding: 20px;
      }
    }
    
    /* Print Styles */
    @media print {
      .header, .footer, .button-container, .popup-menu {
        display: none !important;
      }
      
      .result-box {
        box-shadow: none;
        border: 1px solid #ccc;
        page-break-inside: avoid;
      }
      
      body {
        background-color: white;
      }
    }
  </style>
</head>
<body>
  <!-- Header -->
  <header class="header">
    <img src="https://www.elsob7.com/wp-content/uploads/2025/03/%D8%A7%D9%84%D8%A7%D8%B3%D8%AA%D8%B9%D9%84%D8%A7%D9%85-%D8%B9%D9%86-%D8%A5%D8%AC%D8%A7%D8%B2%D8%A9-%D9%85%D8%B1%D8%B6%D9%8A%D8%A9-%D8%B9%D8%A8%D8%B1-%D9%85%D9%86%D8%B5%D8%A9-%D8%B5%D8%AD%D8%A9.png" 
         alt="شعار منصة صحة" 
         class="logo" 
         onerror="this.onerror=null; this.src='https://via.placeholder.com/200x65/2e6fb3/ffffff?text=شعار+صحة';" />
    <div class="menu-icon" id="menuIcon" onclick="toggleMenu()">
      <i class="fas fa-bars"></i>
    </div>
  </header>

  <!-- Popup Menu -->
  <div class="popup-menu" id="popupMenu">
    <div class="menu-content">
      <div class="menu-header">
        <div class="menu-title">القائمة الرئيسية</div>
        <div class="close-btn" onclick="toggleMenu()">
          <i class="fas fa-times"></i>
        </div>
      </div>
      <div class="menu-items">
        <a href="https://www.seha.sa/ui#/services" class="menu-item" onclick="toggleMenu()">
          <span class="menu-icon-item"><i class="fas fa-concierge-bell"></i></span>
          <span>الخدمات</span>
        </a>
        <a href="https://www.seha.sa/ui#/inquiries" class="menu-item" onclick="toggleMenu()">
          <span class="menu-icon-item"><i class="fas fa-search"></i></span>
          <span>الاستعلامات</span>
        </a>
        <a href="https://www.seha.sa/ui#/iamredirection/1" class="menu-item" onclick="toggleMenu()">
          <span class="menu-icon-item"><i class="fas fa-user-plus"></i></span>
          <span>إنشاء حساب</span>
        </a>
        <a href="https://www.seha.sa/ui#/faq" class="menu-item" onclick="toggleMenu()">
          <span class="menu-icon-item"><i class="fas fa-question-circle"></i></span>
          <span>الأسئلة الشائعة</span>
        </a>
        <a href="https://www.seha.sa/ui#/ContactUs" class="menu-item" onclick="toggleMenu()">
          <span class="menu-icon-item"><i class="fas fa-envelope"></i></span>
          <span>تواصل معنا</span>
        </a>
        <a href="https://www.seha.sa/ui#/account/login" class="menu-login" onclick="toggleMenu()">
          <span class="menu-icon-item"><i class="fas fa-user"></i></span>
          <span>تسجيل الدخول</span>
        </a>
      </div>
    </div>
  </div>

  <!-- Main Content -->
  <main class="main-content">
    <div class="page-title-container">
      <h1 class="page-title">الإجازات المرضية</h1>
    </div>
    
    <p class="page-description">
      خدمة الاستعلام عن الإجازات المرضية تتيح لك الاستعلام عن حالة طلبك للإجازة ويمكنك طباعتها عن طريق تطبيق صحتي
    </p>

    <!-- Form Container -->
    <div class="form-container">
      <!-- Empty Field Error Message -->
      <div id="emptyFieldsError" class="message-box message-empty">الرجاء إدخال رمز الخدمة ورقم الهوية/الإقامة</div>
      
      <!-- General Error Message -->
      <div id="errorMessage" class="message-box message-error">رمز الخدمة أو رقم الهوية غير صحيح. يرجى التحقق والمحاولة مرة أخرى.</div>
      
      <!-- Input Fields -->
      <div class="input-container">
        <label for="leaveCode" class="input-label">رمز الخدمة</label>
        <input id="leaveCode" type="text" class="input-field" placeholder="أدخل رمز الخدمة المكون من 14 حرفاً" maxlength="14" oninput="hideErrorMessages()" />
      </div>
      
      <div class="input-container">
        <label for="idNumber" class="input-label">رقم الهوية / الإقامة</label>
        <input id="idNumber" type="text" class="input-field" placeholder="أدخل رقم الهوية أو الإقامة" maxlength="11" inputmode="numeric" oninput="hideErrorMessages()" />
      </div>
      
      <!-- Buttons -->
      <div class="button-container">
        <button class="btn btn-primary" id="searchBtn" onclick="checkData()">
          <span id="searchBtnText">استعلام</span>
          <span id="loadingSpinner" class="loading-spinner"></span>
        </button>
        
        <a href="https://www.seha.sa/ui#/inquiries" class="btn btn-secondary" id="backBtn">
          رجوع للاستعلامات
        </a>
      </div>
    </div>

    <!-- Result Box -->
    <div id="resultBox" class="result-box">
      <div class="result-title">تفاصيل الإجازة المرضية</div>
      <div class="result-grid" id="resultContent">
        <!-- Results will be populated here by JavaScript -->
      </div>
      
      <!-- Action Buttons after Results -->
      <div class="button-container" id="resultActions" style="display: none; margin-top: 30px;">
        <button class="btn btn-primary" onclick="newSearch()">
          <i class="fas fa-search" style="margin-left: 8px;"></i>
          استعلام جديد
        </button>
        
        <button class="btn btn-tertiary" id="printBtn" onclick="window.print()">
          <i class="fas fa-print" style="margin-left: 8px;"></i>
          طباعة النتيجة
        </button>
        
        <a href="https://www.seha.sa/ui#/inquiries" class="btn btn-secondary" id="backListBtn">
          <i class="fas fa-list" style="margin-left: 8px;"></i>
          رجوع للاستعلامات
        </a>
      </div>
    </div>
  </main>

  <!-- Footer -->
  <footer class="footer">
    <div class="footer-content">
      <img src="https://www.seha.sa/assets/logo-white-CKxLEirV.svg" 
           alt="شعار منصة صحة" 
           class="footer-logo"
           onerror="this.onerror=null; this.src='https://via.placeholder.com/200x70/ffffff/2e6fb3?text=شعار+صحة+أبيض';" />
      
      <p class="footer-description">
        منصة صحة تخدم جميع المنشآت الطبية من خلال تقديم الخدمات الصحية إلكترونياً لجميع المنشآت الطبية وتسعى إلى توحيد وأتمتة الإجراءات والخدمات بما في ذلك رفع جودة الأداء وخفض التكاليف.
      </p>
      
      <div class="footer-sections">
        <!-- Main Menu Section -->
        <div class="footer-section">
          <div class="footer-title">القائمة الرئيسية</div>
          <div class="footer-links">
            <a href="https://www.seha.sa/ui#/services" class="footer-link">الخدمات</a>
            <a href="https://www.seha.sa/ui#/inquiries" class="footer-link">الاستعلامات</a>
            <a href="https://www.seha.sa/ui#/faq" class="footer-link">الأسئلة الشائعة</a>
            <a href="https://www.seha.sa/ui#/ContactUs" class="footer-link">تواصل معنا</a>
          </div>
        </div>
        
        <!-- Contact Section -->
        <div class="footer-section">
          <div class="footer-title">تواصل معنا</div>
          <div class="contact-info">
            <div class="contact-item">
              <span>📞 اتصال: 920002005</span>
              <span class="contact-icon"></span>
            </div>
            <div class="contact-item">
              <span>✉ البريد الإلكتروني: support@seha.sa</span>
              <span class="contact-icon"></span>
            </div>
            <div class="contact-item">
              <span>📱 واتساب: 920002005</span>
              <span class="contact-icon"></span>
            </div>
            <div class="contact-item">
              <span>🕘 أوقات العمل: الأحد حتى الخميس 8 ص - 11 م</span>
              <span class="contact-icon"></span>
            </div>
          </div>
        </div>
      </div>
      
      <!-- Partners -->
      <div class="footer-partners">
        <img src="https://www.seha.sa/assets/lean-logo-De0NEeoI.svg" 
             alt="شعار لين" 
             class="partner-logo"
             onerror="this.onerror=null; this.src='https://via.placeholder.com/150x50/ffffff/2e6fb3?text=شعار+لين';" />
        <div class="divider"></div>
        <img src="https://www.seha.sa/assets/MOH-logo-DYiHZCSg.svg" 
             alt="شعار وزارة الصحة" 
             class="partner-logo"
             onerror="this.onerror=null; this.src='https://via.placeholder.com/150x50/ffffff/2e6fb3?text=وزارة+الصحة';" />
      </div>
      
      <!-- Footer Bottom -->
      <div class="footer-bottom">
        منصة صحة معتمدة من قبل وزارة الصحة © 2026<br />
        <a href="#" style="color: rgba(255, 255, 255, 0.9); text-decoration: underline;">سياسة الخصوصية وشروط الاستخدام</a> | 
        <a href="#" style="color: rgba(255, 255, 255, 0.9); text-decoration: underline;">دليل الاستخدام</a>
      </div>
    </div>
  </footer>

  <script>
    // Initialize data on page load
    function initializeData() {
      const data = [
        {
          leaveCode: "GSL24427523854",
          idNumber: "1104060254",
          name: "لمياء صالح راشد المغير",
          from: "2025-07-27",
          to: "2025-07-27",
          days: "1",
          doctor: "منيرة سالم صالح الصياد",
          title: "طبيب عام",
          date: "2025-07-27",
          status: "مفعلة",
          hospital: "مستشفى الملك فهد العام"
        },
        {
          leaveCode: "GSL24427523854",
          idNumber: "1044713145",
          name: "بندر محمد بن محمد صالح الحربي",
          from: "2025-08-23",
          to: "2025-08-23",
          days: "1",
          doctor: "فادي محسن مهدي الشهري",
          title: "طبيب عام",
          date: "2025-08-23",
          status: "مفعلة",
          hospital: "مستشفى الملك عبدالعزيز"
        },
        {
          leaveCode: "GSL55886151331",
          idNumber: "2133546982",
          name: "إبراهيم علي محمد الزرقاني",
          from: "2025-06-11",
          to: "2025-06-17",
          days: "7",
          doctor: "محمد الشهراني",
          title: "طب بشري",
          date: "2025-06-11",
          status: "منتهية",
          hospital: "مستشفى الملك خالد"
        },
        {
          leaveCode: "GSL25060111760",
          idNumber: "1097131021",
          name: "هيف ظافر آل سليم",
          from: "2025-06-12",
          to: "2025-06-12",
          days: "1",
          doctor: "محمد جمال خلف",
          title: "طب بشري",
          date: "2025-06-12",
          status: "مفعلة",
          hospital: "مستشفى الملك فيصل التخصصي"
        },
        {
          leaveCode: "GSL25060111760",
          idNumber: "1122828492",
          name: "عماد جمعان علي جيزاني",
          from: "2025-06-13",
          to: "2025-06-13",
          days: "1",
          doctor: "علي فتح",
          title: "طب بشري",
          date: "2025-06-13",
          status: "مفعلة",
          hospital: "مستشفى الملك عبدالله"
        },
        {
          leaveCode: "GSL25060111760",
          idNumber: "1093345757",
          name: "منى علي جابر جعفري",
          from: "2025-06-13",
          to: "2025-06-13",
          days: "1",
          doctor: "محمد جمال خلف",
          title: "طب بشري",
          date: "2025-06-13",
          status: "مفعلة",
          hospital: "مستشفى الملك فهد العام"
        },
        {
          leaveCode: "PSL25060111760",
          idNumber: "1121388159",
          name: "فهد خالد سعد الطليحي",
          from: "2025-11-09",
          to: "2025-11-09",
          days: "1",
          doctor: "عبدالله صالح الغامدي",
          title: "طبيب عام",
          date: "2025-11-09",
          status: "مفعلة",
          hospital: "مستشفى الملك سعود"
        },
        {
          leaveCode: "PSL59953212832",
          idNumber: "1121388159",
          name: "فهد خالد سعد الطليحي",
          from: "2025-11-09",
          to: "2025-11-10",
          days: "2",
          doctor: "عبدالله صالح الغامدي",
          title: "طبيب عام",
          date: "2025-11-10",
          status: "مفعلة",
          hospital: "مستشفى الملك سعود"
        }
      ];
      
      // Add more sample data with additional fields
      for (let i = 0; i < 20; i++) {
        const randomId = Math.floor(1000000000 + Math.random() * 9000000000).toString();
        const randomCode = "GSL" + Math.floor(10000000000 + Math.random() * 90000000000).toString();
        const hospitals = ["مستشفى الملك فهد العام", "مستشفى الملك عبدالعزيز", "مستشفى الملك خالد", "مستشفى الملك فيصل التخصصي", "مستشفى الملك عبدالله", "مستشفى الملك سعود"];
        const statuses = ["مفعلة", "منتهية", "قيد المراجعة"];
        
        data.push({
          leaveCode: randomCode,
          idNumber: randomId,
          name: "مستخدم تجريبي " + (i+9),
          from: "2025-" + (Math.floor(Math.random() * 2) + 10) + "-" + (Math.floor(Math.random() * 28) + 1),
          to: "2025-" + (Math.floor(Math.random() * 2) + 10) + "-" + (Math.floor(Math.random() * 28) + 1),
          days: (Math.floor(Math.random() * 10) + 1).toString(),
          doctor: "طبيب تجريبي " + (i+1),
          title: ["طبيب عام", "طب بشري", "أخصائي باطنية", "أخصائي عظام"][Math.floor(Math.random() * 4)],
          date: "2025-" + (Math.floor(Math.random() * 2) + 10) + "-" + (Math.floor(Math.random() * 28) + 1),
          status: statuses[Math.floor(Math.random() * 3)],
          hospital: hospitals[Math.floor(Math.random() * hospitals.length)]
        });
      }
      
      localStorage.setItem("leaveData", JSON.stringify(data));
    }
    
    // Toggle menu function
    function toggleMenu() {
      const menu = document.getElementById('popupMenu');
      if (menu.style.display === 'flex') {
        menu.style.display = 'none';
      } else {
        menu.style.display = 'flex';
      }
    }
    
    // Hide error messages when user starts typing
    function hideErrorMessages() {
      document.getElementById('emptyFieldsError').style.display = 'none';
      document.getElementById('errorMessage').style.display = 'none';
    }
    
    // Main function to check data
    function checkData() {
      const idNumberInput = document.getElementById('idNumber');
      const leaveCodeInput = document.getElementById('leaveCode');
      const idNumber = idNumberInput.value.trim();
      const leaveCode = leaveCodeInput.value.trim();
      
      const emptyFieldsError = document.getElementById('emptyFieldsError');
      const errorMessage = document.getElementById('errorMessage');
      const searchBtn = document.getElementById('searchBtn');
      const loadingSpinner = document.getElementById('loadingSpinner');
      const resultBox = document.getElementById('resultBox');
      const resultContent = document.getElementById('resultContent');
      const resultActions = document.getElementById('resultActions');
      
      // Check for empty fields first
      if (!idNumber || !leaveCode) {
        emptyFieldsError.style.display = 'block';
        errorMessage.style.display = 'none';
        resultBox.style.display = 'none';
        return;
      }
      
      // Validate ID number (should be 10 digits for Saudi ID or 11 for residency)
      if (!/^\d{10,11}$/.test(idNumber)) {
        errorMessage.textContent = "رقم الهوية/الإقامة يجب أن يكون 10 أو 11 رقمًا";
        errorMessage.style.display = 'block';
        emptyFieldsError.style.display = 'none';
        resultBox.style.display = 'none';
        return;
      }
      
      // Validate leave code format
      if (!/^[A-Z0-9]{14}$/.test(leaveCode)) {
        errorMessage.textContent = "رمز الخدمة يجب أن يكون 14 حرفاً من الأرقام والحروف الإنجليزية الكبيرة";
        errorMessage.style.display = 'block';
        emptyFieldsError.style.display = 'none';
        resultBox.style.display = 'none';
        return;
      }
      
      // Start loading state
      loadingSpinner.style.display = 'inline-block';
      searchBtn.classList.add('loading');
      searchBtn.disabled = true;
      errorMessage.style.display = 'none';
      
      // Simulate API call with 1.5 second delay
      setTimeout(() => {
        const storedData = JSON.parse(localStorage.getItem("leaveData")) || [];
        const result = storedData.find(d => d.leaveCode === leaveCode && d.idNumber === idNumber);
        
        // End loading state
        loadingSpinner.style.display = 'none';
        searchBtn.classList.remove('loading');
        searchBtn.disabled = false;
        
        if (result) {
          // Format dates for display
          const formatDate = (dateStr) => {
            const date = new Date(dateStr);
            return date.toLocaleDateString('ar-SA', { 
              weekday: 'long', 
              year: 'numeric', 
              month: 'long', 
              day: 'numeric' 
            });
          };
          
          // Create status badge with color
          let statusBadge = '';
          if (result.status === "مفعلة") {
            statusBadge = '<span style="color: #28a745; font-weight: bold;">● ' + result.status + '</span>';
          } else if (result.status === "منتهية") {
            statusBadge = '<span style="color: #6c757d; font-weight: bold;">● ' + result.status + '</span>';
          } else {
            statusBadge = '<span style="color: #ffc107; font-weight: bold;">● ' + result.status + '</span>';
          }
          
          // Populate result content
          resultContent.innerHTML = `
            <div class="result-item">
              <div class="result-label">الاسم الكامل</div>
              <div class="result-value">${result.name}</div>
            </div>
            <div class="result-item">
              <div class="result-label">رمز الخدمة</div>
              <div class="result-value">${result.leaveCode}</div>
            </div>
            <div class="result-item">
              <div class="result-label">حالة الإجازة</div>
              <div class="result-value">${statusBadge}</div>
            </div>
            <div class="result-item">
              <div class="result-label">تاريخ الإصدار</div>
              <div class="result-value">${formatDate(result.date)}</div>
            </div>
            <div class="result-item">
              <div class="result-label">تبدأ من</div>
              <div class="result-value">${formatDate(result.from)}</div>
            </div>
            <div class="result-item">
              <div class="result-label">تنتهي في</div>
              <div class="result-value">${formatDate(result.to)}</div>
            </div>
            <div class="result-item">
              <div class="result-label">المدة بالأيام</div>
              <div class="result-value">${result.days} يوم</div>
            </div>
            <div class="result-item">
              <div class="result-label">اسم الطبيب</div>
              <div class="result-value">${result.doctor}</div>
            </div>
            <div class="result-item">
              <div class="result-label">المسمى الوظيفي</div>
              <div class="result-value">${result.title}</div>
            </div>
            <div class="result-item">
              <div class="result-label">المستشفى/المركز</div>
              <div class="result-value">${result.hospital || "غير محدد"}</div>
            </div>
          `;
          
          // Show result box and actions
          resultBox.style.display = 'block';
          resultActions.style.display = 'flex';
          
          // Hide search button, show new search button
          document.getElementById('searchBtn').style.display = 'none';
          document.getElementById('backBtn').style.display = 'none';
          
          // Scroll to results for better UX
          resultBox.scrollIntoView({ behavior: 'smooth', block: 'start' });
        } else {
          errorMessage.textContent = "رمز الخدمة أو رقم الهوية غير صحيح. يرجى التحقق والمحاولة مرة أخرى.";
          errorMessage.style.display = 'block';
          resultBox.style.display = 'none';
          resultActions.style.display = 'none';
          
          // Keep search button visible
          document.getElementById('searchBtn').style.display = 'block';
          document.getElementById('backBtn').style.display = 'block';
        }
      }, 1500);
    }
    
    // Start new search
    function newSearch() {
      // Clear input fields
      document.getElementById('idNumber').value = '';
      document.getElementById('leaveCode').value = '';
      
      // Hide messages and results
      document.getElementById('emptyFieldsError').style.display = 'none';
      document.getElementById('errorMessage').style.display = 'none';
      document.getElementById('resultBox').style.display = 'none';
      document.getElementById('resultActions').style.display = 'none';
      
      // Show search button and back button
      document.getElementById('searchBtn').style.display = 'block';
      document.getElementById('backBtn').style.display = 'block';
      
      // Focus on first input field
      document.getElementById('leaveCode').focus();
      
      // Scroll to top of form
      document.querySelector('.form-container').scrollIntoView({ behavior: 'smooth' });
    }
    
    // Initialize on page load
    window.addEventListener('load', () => {
      initializeData();
      newSearch(); // Set initial state
      
      // Add animation to form container
      const formContainer = document.querySelector('.form-container');
      formContainer.style.animation = 'fadeIn 0.8s ease';
      
      // Add click outside to close menu
      document.addEventListener('click', (e) => {
        const menu = document.getElementById('popupMenu');
        const menuIcon = document.getElementById('menuIcon');
        
        if (menu.style.display === 'flex' && !menu.contains(e.target) && e.target !== menuIcon) {
          menu.style.display = 'none';
        }
      });
    });
  </script>
</body>
</html>
