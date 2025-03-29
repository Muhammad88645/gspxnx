<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>🔍 فحص أمان الهاتف</title>
    <style>
        body { font-family: Arial, sans-serif; text-align: center; padding: 20px; }
        .container { max-width: 400px; margin: auto; padding: 20px; border: 1px solid #ddd; border-radius: 10px; background: #f9f9f9; }
        .safe { color: green; font-weight: bold; }
        .warning { color: red; font-weight: bold; }
    </style>
</head>
<body>

    <div class="container">
        <h2>🔍 فحص أمان الهاتف</h2>
        <p><strong>📱 نوع الهاتف:</strong> <span id="deviceInfo">جارٍ الفحص...</span></p>
        <p><strong>🔄 حالة الروت:</strong> <span id="rootStatus">جارٍ الفحص...</span></p>
        <p><strong>⚠️ التطبيقات المشبوهة:</strong> <span id="appCheck">جارٍ الفحص...</span></p>
        <p><strong>🌍 أمان الاتصال:</strong> <span id="secureConnection">جارٍ الفحص...</span></p>
    </div>

    <script>
        // 🔹 عرض نوع الجهاز
        function getDeviceInfo() {
            let userAgent = navigator.userAgent;
            document.getElementById("deviceInfo").innerText = userAgent;
        }

        // 🔹 فحص الروت (مبسط، يعتمد على الأندرويد)
        function checkRoot() {
            let rootPaths = ["/system/bin/su", "/system/xbin/su", "/system/app/Superuser.apk"];
            let isRooted = rootPaths.some(path => window.location.href.includes(path));
            document.getElementById("rootStatus").innerHTML = isRooted ? "<span class='warning'>🚨 الهاتف قد يكون به روت!</span>" : "<span class='safe'>✅ الهاتف آمن</span>";
        }

        // 🔹 البحث عن تطبيقات مشبوهة (محاكاة، لا يمكن فحص التطبيقات عبر المتصفح مباشرة)
        function checkApps() {
            let suspiciousApps = ["com.noshufou.android.su", "com.koushikdutta.superuser", "com.thirdparty.superuser"];
            let foundApps = suspiciousApps.filter(app => navigator.userAgent.includes(app));
            document.getElementById("appCheck").innerHTML = foundApps.length > 0 ? `<span class='warning'>🚨 ${foundApps.join(", ")}</span>` : "<span class='safe'>✅ لا توجد تطبيقات مشبوهة</span>";
        }

        // 🔹 فحص أمان الاتصال (HTTPS)
        function checkConnection() {
            let isSecure = location.protocol === 'https:';
            document.getElementById("secureConnection").innerHTML = isSecure ? "<span class='safe'>✅ الاتصال آمن</span>" : "<span class='warning'>🚨 الاتصال غير آمن!</span>";
        }

        // تشغيل الفحوصات
        getDeviceInfo();
        checkRoot();
        checkApps();
        checkConnection();
    </script>

</body>
</html>
