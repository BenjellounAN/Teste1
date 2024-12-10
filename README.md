<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>أزرار مع صورة وأزرار عمودية</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <style>
        body {
            background-color: #ffffff; /* خلفية بيضاء للصفحة */
            margin: 0;
            font-family: Arial, sans-serif;
        }

        .image-container img {
            width: 100%; /* تغيير الحجم حسب رغبتك */
            max-width: 800px;
            height: auto;
            margin-top: 20px;
        }

        .button-container {
            display: flex;
            flex-direction: column;
            gap: 20px;
            align-items: center;
            margin-top: 20px;
        }

        .button-row {
            display: flex;
            gap: 20px;
        }

        .btn {
            width: 180px;
            height: 50px;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 18px;
            font-weight: bold;
            color: #00cc66;
            border: 2px solid #00cc66;
            border-radius: 8px;
            text-align: center;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.2);
            position: relative;
            text-decoration: none;
        }

        .btn:hover {
            background-color: #00cc66;
            color: #fff;
            box-shadow: 0px 8px 16px rgba(0, 0, 0, 0.3);
            transform: translateY(-4px);
        }

        .btn i {
            margin-right: 6px;
            font-size: 20px;
        }

        .btn img {
            width: 24px;
            height: auto;
            margin-right: 6px;
            animation: vibrate 0.3s infinite;
        }

        @keyframes vibrate {
            0% { transform: translate(0); }
            25% { transform: translate(-2px, 0); }
            50% { transform: translate(2px, 0); }
            75% { transform: translate(-2px, 0); }
            100% { transform: translate(0); }
        }

        .new-label {
            position: absolute;
            top: -10px;
            right: -10px;
            background-color: #ff0000;
            color: #fff;
            padding: 4px 8px;
            border-radius: 12px;
            font-size: 12px;
            font-weight: bold;
            z-index: 1;
            box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.3);
        }

        /* الجزء الثاني */
        .button-container-vertical {
            display: flex;
            flex-direction: column; /* ترتيب الأزرار عمودياً */
            width: 100%;
            max-width: 400px; /* تحديد عرض الأزرار */
            margin: 40px auto; /* مركز الأزرار العمودية */
        }

        .btn-vertical {
            padding: 40px; /* زيادة الحشو لجعل الزر أكبر */
            font-size: 24px; /* تكبير حجم الخط */
            font-weight: bold;
            color: #00cc66; /* لون الكتابة أخضر */
            background-color: #fff; /* خلفية الزر بيضاء */
            border: none;
            border-radius: 8px;
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.2); /* تأثير الظل */
            margin: 10px 0; /* مسافة بين الأزرار */
            cursor: pointer;
            transition: all 0.3s ease;
            position: relative; /* لجعل الظل يعمل بشكل جيد */
            text-align: center; /* لتوسيع النص بشكل مركزي */
        }

        .btn-vertical:hover {
            background-color: rgba(255, 255, 255, 0.9); /* لون خلفية الزر عند التمرير */
            box-shadow: 0 12px 40px rgba(0, 0, 0, 0.3); /* زيادة الظل عند التمرير */
            transform: translateY(-4px); /* رفع الزر عند التمرير */
        }

        .btn-vertical:active {
            transform: translateY(2px); /* تأثير الطفو عند النقر */
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.3); /* تقليل الظل عند النقر */
        }

        .icon {
            font-size: 30px; /* حجم الشعار */
            display: block; /* جعل الشعار يظهر في سطر منفصل */
            margin-bottom: 10px; /* مسافة بين الشعار والنص */
            color: #00cc66; /* لون الشعار */
        }

        .time {
            font-size: 14px; /* حجم الخط الأسود */
            color: black; /* لون الخط الأسود */
            margin: 5px 0; /* مسافة بين النص */
        }

        .show-pharmacy {
            font-size: 12px; /* حجم الخط الرمادي */
            color: gray; /* لون الخط الرمادي */
            margin: 5px 0; /* مسافة بين النص */
        }

        .section-title {
            font-size: 24px; /* حجم الخط */
            color: black; /* لون الخط */
            font-weight: bold; /* سمك الخط */
            text-align: center; /* محاذاة النص في الوسط */
            margin: 20px 0; /* مسافة حول العنوان */
        }

        .divider {
            width: 80%; /* عرض الخط */
            height: 2px; /* ارتفاع الخط */
            background-color: #00cc66; /* لون الخط الأخضر */
            margin: 20px auto; /* مركز الخط */
            position: relative;
        }

        .divider::after {
            content: "";
            display: block;
            height: 20px; /* ارتفاع المساحة الفارغة في نهاية الخط */
        }

        .mode-message {
            font-size: 20px;
            color: #00cc66;
            text-align: center;
            margin-top: 20px;
        }

        /* نمط الوضع الليلي */
        .night-mode {
            background-color: #333;
            color: #fff;
        }
    </style>
    <script>
        function setNightMode() {
            const times = document.querySelectorAll('.time');
            times.forEach(time => {
                time.textContent = 'De 22h A 09h sans Interruption';
            });
            document.body.classList.add('night-mode');
            document.getElementById('mode-message').textContent = "PHARMACIE GARDE NUIT MARRAKECH";
        }

        function setDayMode() {
            const times = document.querySelectorAll('.time');
            times.forEach(time => {
                time.textContent = 'De 09h A 22h sans Interruption';
            });
            document.body.classList.remove('night-mode');
            document.getElementById('mode-message').textContent = "PHARMACIE GARDE JOUR A MARRAKECH";
        }

        function navigateTo(page) {
            window.location.href = page;
        }
    </script>
</head>
<body>
    <!-- حمل صورتك الخاصة في هذا القسم -->
    <div class="image-container">
        <img src="https://www.timeskipper.co/wp-content/uploads/2023/02/Les-grands-enjeux-de-la-pharmacie-de-demain.jpg" alt="صورة">
    </div>

    <div class="button-container">
        <div class="button-row">
            <!-- زر garde jour مع إعادة توجيه JavaScript -->
            <div class="btn" onclick="setDayMode()">
                <i class="fas fa-sun"></i> garde jour
            </div>
            <!-- زر garde nuit لتغيير نص الأزرار في الأسفل -->
            <div class="btn" onclick="setNightMode()">
                <i class="fas fa-moon"></i> garde nuit
            </div>
        </div>
        <!-- زر واتساب للـ livraison -->
        <a href="https://wa.me/+212709191563" target="_blank" class="btn">
            <img src="https://upload.wikimedia.org/wikipedia/commons/6/6b/WhatsApp.svg" alt="WhatsApp Logo"> livraison 24h 
            <span class="new-label">New</span>
        </a>
    </div>

    <!-- عنوان القسم الثاني -->
    <div class="section-title">SÉLECTIONNEZ VOTRE RÉGION</div>

    <!-- الخط -->
    <div class="divider"></div>

    <!-- الرسالة حول الوضع -->
    <div id="mode-message" class="mode-message">PHARMACIE GARDE JOUR MARRAKECH</div>

    <!-- قسم الأزرار العمودية -->
    <div class="button-container-vertical">
        <button class="btn-vertical" onclick="navigateTo('teste2.html')">
            <span class="icon fas fa-map-marker-alt"></span>
            Grand guéliz
            <div class="time">De 09h A 22h sans Interruption</div>
            <div class="show-pharmacy">6 PHARMACIES DE GARDE</div>
        </button>

        <!-- الزر المعدل -->
        <button class="btn-vertical" onclick="navigateTo('izdihar.html')">
            <span class="icon fas fa-map-marker-alt"></span>
            izdihar
            <div class="time">De 09h A 22h sans Interruption</div>
            <div class="show-pharmacy">4 PHARMACIES DE GARDE</div>
        </button>

        <!-- زر Hy hassani -->
        <button class="btn-vertical" onclick="navigateTo('Hyhassani.html')">
            <span class="icon fas fa-map-marker-alt"></span>
            Hy hassani
            <div class="time">De 09h A 22h sans Interruption</div>
            <div class="show-pharmacy">5 PHARMACIES DE GARDE</div>
        </button>
    </div>
</body>
</html>
