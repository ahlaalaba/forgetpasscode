<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=5.0">
    <title>مضيف أهل العباء</title>
    
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- FontAwesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Google Fonts Arabic (Cairo & Amiri) -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Amiri:ital,wght@0,400;0,700;1,400&family=Cairo:wght@300;400;600;700;800;900&display=swap" rel="stylesheet">
    
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        emeraldCustom: {
                            800: '#064e3b',
                            900: '#022c22',
                            950: '#011c16',
                        },
                        amberCustom: {
                            400: '#fbbf24',
                            500: '#f59e0b',
                            600: '#d97706',
                        }
                    },
                    fontFamily: {
                        cairo: ['Cairo', 'sans-serif'],
                        amiri: ['Amiri', 'serif'],
                    },
                    screens: {
                        'tv': '1920px', // Optimization for Large Smart TVs & PS5 output
                    }
                }
            }
        }
    </script>
    <style>
        body {
            font-family: 'Cairo', sans-serif;
            background-color: #01140f;
            color: #f1f5f9;
            background-image: 
                radial-gradient(circle at 50% 0%, rgba(21, 128, 61, 0.25) 0%, transparent 65%),
                radial-gradient(circle at 100% 100%, rgba(245, 158, 11, 0.08) 0%, transparent 50%);
            background-attachment: fixed;
            min-height: 100vh;
            overflow-x: hidden;
        }

        .amiri-font {
            font-family: 'Amiri', serif;
        }

        .gold-gradient-text {
            background: linear-gradient(135deg, #fef08a 0%, #f59e0b 50%, #b45309 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .gold-border-glow {
            border: 1px solid rgba(245, 158, 11, 0.35);
            box-shadow: 0 0 25px rgba(245, 158, 11, 0.12);
        }

        .glass-panel {
            background: rgba(4, 30, 23, 0.82);
            backdrop-filter: blur(16px);
            -webkit-backdrop-filter: blur(16px);
            border: 1px solid rgba(255, 255, 255, 0.08);
        }

        /* Enhanced Navigation Focus for TV & PlayStation Controllers */
        *:focus-visible {
            outline: 3px solid #f59e0b !important;
            outline-offset: 3px !important;
            box-shadow: 0 0 20px rgba(245, 158, 11, 0.8) !important;
            transition: all 0.15s ease-in-out;
        }

        .pattern-overlay {
            background-image: url("data:image/svg+xml,%3Csvg width='60' height='60' viewBox='0 0 60 60' xmlns='http://www.w3.org/2000/svg'%3E%3Cg fill='%23f59e0b' fill-opacity='0.03' fill-rule='evenodd'%3E%3Cpath d='M30 30L0 0h60L30 30zM0 60l30-30 30 30H0z'/%3E%3C/g%3E%3C/svg%3E");
        }

        /* Custom Scrollbars */
        ::-webkit-scrollbar {
            width: 8px;
        }
        ::-webkit-scrollbar-track {
            background: #01140f;
        }
        ::-webkit-scrollbar-thumb {
            background: #0f5132;
            border-radius: 4px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #f59e0b;
        }
    </style>
</head>
<body class="pattern-overlay flex flex-col justify-between min-h-screen text-slate-100 antialiased selection:bg-amber-500 selection:text-slate-950">

    <header class="border-b border-amber-500/20 glass-panel sticky top-0 z-40 shadow-xl">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 h-20 flex items-center justify-between">
            
            <!-- Brand Logo and Title -->
            <div class="flex items-center gap-3.5">
                <div class="w-12 h-12 rounded-2xl bg-gradient-to-br from-amber-400 via-amber-500 to-amber-700 flex items-center justify-center shadow-lg shadow-amber-900/40 text-emerald-950 text-2xl font-black">
                    <i class="fa-solid fa-hands-praying"></i>
                </div>
                <div>
                    <h1 class="text-2xl sm:text-3xl font-black amiri-font gold-gradient-text tracking-wide">مضيف أهل العباء</h1>
                    <p class="text-[10px] sm:text-xs text-emerald-300/80 font-bold tracking-widest">عليهم أفضل الصلاة والسلام</p>
                </div>
            </div>

            <!-- Device Compatibility Indicator & User Logout Area -->
            <div class="flex items-center gap-4">
                <div class="hidden lg:flex items-center gap-2 px-3 py-1.5 rounded-full bg-emerald-950/80 border border-emerald-800/60 text-xs text-emerald-300">
                    <i class="fa-solid fa-tv text-amber-400"></i>
                    <i class="fa-solid fa-laptop text-amber-400"></i>
                    <i class="fa-solid fa-tablet-screen-button text-amber-400"></i>
                    <i class="fa-solid fa-mobile-screen-button text-amber-400"></i>
                    <i class="fa-gamepad text-amber-400"></i>
                    <span class="mr-1 text-[11px] font-semibold text-slate-300">متوافق مع كل الأجهزة</span>
                </div>

                <div id="navUserArea" class="hidden flex items-center gap-3">
                    <span id="navWelcomeMsg" class="text-sm font-semibold text-emerald-200 hidden sm:inline"></span>
                    <button tabindex="0" onclick="logout()" class="px-4 py-2 text-xs sm:text-sm bg-red-600/20 hover:bg-red-600/40 focus:bg-red-600 text-red-300 hover:text-white rounded-xl border border-red-500/30 transition flex items-center gap-2 font-bold cursor-pointer">
                        <i class="fa-solid fa-right-from-bracket"></i>
                        <span>خروج</span>
                    </button>
                </div>
            </div>
        </div>
    </header>

    <main class="flex-grow flex items-center justify-center p-4 sm:p-6 lg:p-10">
        
        <!-- ================= Login Section ================= -->
        <div id="loginSection" class="w-full max-w-md sm:max-w-lg glass-panel gold-border-glow rounded-3xl p-6 sm:p-10 shadow-2xl transition-all duration-300">
            
            <div class="text-center mb-8">
                <div class="inline-flex p-4 rounded-2xl bg-emerald-900/60 border border-amber-500/30 mb-4 text-amber-400 text-3xl shadow-inner">
                    <i class="fa-solid fa-user-shield"></i>
                </div>
                <h2 class="text-2xl sm:text-3xl font-black text-white mb-2">بوابة الأعضاء</h2>
                <p class="text-xs sm:text-sm text-emerald-200/70">أهلاً وسهلاً بكم في الموقع الرسمي لـ <span class="text-amber-400 font-bold">مضيف أهل العباء</span></p>
            </div>

            <!-- Login Alert Box -->
            <div id="loginAlert" class="hidden mb-5 p-3.5 rounded-xl text-xs sm:text-sm flex items-center gap-2.5"></div>

            <form onsubmit="handleLogin(event)" class="space-y-5">
                <div>
                    <label class="block text-xs font-bold text-emerald-200 mb-2">اسم المستخدم</label>
                    <div class="relative">
                        <span class="absolute inset-y-0 right-0 flex items-center pr-3.5 text-emerald-400/60">
                            <i class="fa-solid fa-at"></i>
                        </span>
                        <input tabindex="0" type="text" id="loginUsername" required placeholder="مثال: abbas@2013" 
                            class="w-full pl-4 pr-11 py-3.5 bg-emerald-950/80 border border-emerald-800/80 rounded-xl text-white placeholder-emerald-600/60 focus:outline-none focus:border-amber-400 transition text-sm dir-ltr text-right font-mono">
                    </div>
                </div>

                <div>
                    <label class="block text-xs font-bold text-emerald-200 mb-2">كلمة السر</label>
                    <div class="relative">
                        <span class="absolute inset-y-0 right-0 flex items-center pr-3.5 text-emerald-400/60">
                            <i class="fa-solid fa-lock"></i>
                        </span>
                        <input tabindex="0" type="password" id="loginPassword" required placeholder="••••••••" 
                            class="w-full pl-11 pr-11 py-3.5 bg-emerald-950/80 border border-emerald-800/80 rounded-xl text-white placeholder-emerald-600/60 focus:outline-none focus:border-amber-400 transition text-sm dir-ltr text-right font-mono">
                        <button type="button" tabindex="0" onclick="togglePasswordVisibility('loginPassword', 'eyeIcon1')" class="absolute inset-y-0 left-0 flex items-center pl-3.5 text-emerald-400/60 hover:text-amber-400 focus:text-amber-400">
                            <i id="eyeIcon1" class="fa-solid fa-eye"></i>
                        </button>
                    </div>
                </div>

                <div class="flex items-center justify-between text-xs pt-1">
                    <label class="flex items-center gap-2 cursor-pointer text-emerald-300">
                        <input type="checkbox" id="rememberMe" class="w-4 h-4 rounded bg-emerald-950 border-emerald-700 text-amber-500 focus:ring-amber-500">
                        <span>تذكر الحساب</span>
                    </label>
                    <button type="button" tabindex="0" onclick="showForgotPasswordModal()" class="text-amber-400 hover:text-amber-300 font-bold underline underline-offset-4 transition focus:outline-none">
                        هل نسيت كلمة السر؟
                    </button>
                </div>

                <button tabindex="0" type="submit" class="w-full py-4 px-6 bg-gradient-to-r from-amber-500 via-amber-600 to-amber-700 hover:from-amber-600 hover:to-amber-800 text-emerald-950 font-black rounded-xl shadow-lg shadow-amber-500/20 transition transform active:scale-98 flex items-center justify-center gap-2 text-base cursor-pointer">
                    <i class="fa-solid fa-right-to-bracket"></i>
                    <span>تسجيل الدخول</span>
                </button>
            </form>

            <div class="mt-8 pt-6 border-t border-emerald-800/40 text-center">
                <p class="text-xs text-emerald-400/60">نظام الخدمات التفاعلي لـ مضيف أهل العباء</p>
            </div>
        </div>

        <!-- ================= Member Dashboard ================= -->
        <div id="dashboardSection" class="hidden w-full max-w-6xl space-y-6">
            
            <!-- Dashboard Welcome Header -->
            <div class="glass-panel gold-border-glow rounded-3xl p-6 sm:p-8 flex flex-col md:flex-row items-center justify-between gap-6 shadow-2xl">
                <div class="flex items-center gap-5 text-center md:text-right flex-col md:flex-row">
                    <div class="w-20 h-20 rounded-2xl bg-gradient-to-tr from-amber-500 to-amber-300 flex items-center justify-center text-emerald-950 text-4xl font-bold shadow-xl">
                        <i class="fa-solid fa-user-check"></i>
                    </div>
                    <div>
                        <div class="flex items-center gap-2 justify-center md:justify-start flex-wrap">
                            <span class="px-3 py-1 rounded-full text-xs bg-amber-500/20 text-amber-300 border border-amber-500/40 font-bold">عضو خادم معتمد</span>
                            <span id="userPhoneBadge" class="px-3 py-1 rounded-full text-xs bg-emerald-900/80 text-emerald-300 border border-emerald-700/50 font-mono"></span>
                        </div>
                        <h2 id="dashWelcomeTitle" class="text-2xl sm:text-3xl font-black text-white mt-2">مرحباً بك!</h2>
                        <p class="text-emerald-200/70 text-xs sm:text-sm mt-1">أهلاً بك في اللوحة الخاصة بأعضاء مضيف أهل العباء</p>
                    </div>
                </div>

                <div class="flex gap-3 w-full md:w-auto">
                    <button tabindex="0" onclick="logout()" class="flex-1 md:flex-none px-6 py-3 bg-red-600/20 hover:bg-red-600/40 text-red-300 border border-red-500/30 rounded-xl transition text-sm font-bold flex items-center justify-center gap-2 cursor-pointer">
                        <i class="fa-solid fa-power-off"></i>
                        <span>تسجيل الخروج</span>
                    </button>
                </div>
            </div>

            <!-- Dashboard Content Cards -->
            <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
                <!-- Card 1: Schedule -->
                <div class="glass-panel rounded-2xl p-6 border border-emerald-800/50 hover:border-amber-500/40 transition group">
                    <div class="w-12 h-12 rounded-xl bg-amber-500/10 text-amber-400 flex items-center justify-center text-2xl mb-4 group-hover:scale-110 transition">
                        <i class="fa-solid fa-calendar-days"></i>
                    </div>
                    <h3 class="text-lg font-bold text-white mb-2">جدول الفعاليات والبرك</h3>
                    <p class="text-xs text-emerald-200/70 leading-relaxed mb-4">استعراض المواعيد القادمة للخدمة وتوزيع البركات والبرامج الخاصة بالمضيف.</p>
                    <span class="text-xs text-amber-400 font-bold flex items-center gap-1">
                        <span>الجدول مكتمل ومحدث</span>
                        <i class="fa-solid fa-angle-left"></i>
                    </span>
                </div>

                <!-- Card 2: Services -->
                <div class="glass-panel rounded-2xl p-6 border border-emerald-800/50 hover:border-amber-500/40 transition group">
                    <div class="w-12 h-12 rounded-xl bg-emerald-500/10 text-emerald-400 flex items-center justify-center text-2xl mb-4 group-hover:scale-110 transition">
                        <i class="fa-solid fa-hand-holding-heart"></i>
                    </div>
                    <h3 class="text-lg font-bold text-white mb-2">سجل المساهمات والخدمة</h3>
                    <p class="text-xs text-emerald-200/70 leading-relaxed mb-4">متابعة المساهمات العينية والميدانية لخدام مضيف أهل العباء.</p>
                    <span class="text-xs text-emerald-400 font-bold flex items-center gap-1">
                        <span>حالة الحساب: نشط</span>
                        <i class="fa-solid fa-angle-left"></i>
                    </span>
                </div>

                <!-- Card 3: Account Info -->
                <div class="glass-panel rounded-2xl p-6 border border-emerald-800/50 hover:border-amber-500/40 transition group">
                    <div class="w-12 h-12 rounded-xl bg-amber-500/10 text-amber-400 flex items-center justify-center text-2xl mb-4 group-hover:scale-110 transition">
                        <i class="fa-solid fa-id-card"></i>
                    </div>
                    <h3 class="text-lg font-bold text-white mb-2">بيانات العضوية</h3>
                    <div class="space-y-2 text-xs text-emerald-200/90 bg-emerald-950/60 p-3.5 rounded-xl border border-emerald-800/40 font-mono">
                        <p><span class="text-emerald-400 font-sans">اسم المستخدم:</span> <span id="dashUsernameVal" class="text-amber-300 font-bold"></span></p>
                        <p><span class="text-emerald-400 font-sans">رقم الهاتف:</span> <span id="dashPhoneVal" class="text-amber-300 font-bold"></span></p>
                        <p><span class="text-emerald-400 font-sans">التوثيق:</span> <span class="text-emerald-300 font-bold font-sans">حساب معتمد</span></p>
                    </div>
                </div>
            </div>

            <!-- Announcements Banner -->
            <div class="glass-panel rounded-2xl p-6 border border-emerald-800/50">
                <h3 class="text-lg font-bold text-white mb-3 flex items-center gap-2">
                    <i class="fa-solid fa-bullhorn text-amber-400"></i>
                    <span>إعلانات وملاحظات خُدّام المضيف</span>
                </h3>
                <div class="bg-emerald-950/60 rounded-xl p-4 border border-emerald-800/50 text-xs sm:text-sm text-emerald-200/90 leading-relaxed">
                    نُرحب بجميع الخدام الكرام في <strong class="text-amber-400">مضيف أهل العباء (عليهم السلام)</strong>. نود التذكير بضرورة التنسيق المسبق مع إدارة المضيف وتنظيم نوبات الخدمة اليومية.
                </div>
            </div>
        </div>

    </main>

    <!-- ================= Forgot Password Modal ================= -->
    <div id="forgotPasswordModal" class="fixed inset-0 bg-black/85 backdrop-blur-md hidden flex items-center justify-center p-4 z-50">
        <div class="glass-panel gold-border-glow rounded-3xl w-full max-w-lg p-6 sm:p-8 relative shadow-2xl transition-all">
            
            <!-- Close Button -->
            <button tabindex="0" onclick="closeForgotPasswordModal()" class="absolute top-4 left-4 w-10 h-10 rounded-xl bg-emerald-900/60 hover:bg-emerald-800 focus:bg-amber-500 focus:text-slate-950 text-emerald-300 flex items-center justify-center transition cursor-pointer">
                <i class="fa-solid fa-xmark text-lg"></i>
            </button>

            <div class="text-center mb-6">
                <div class="inline-flex p-3.5 rounded-2xl bg-amber-500/10 text-amber-400 text-2xl mb-2 border border-amber-500/20">
                    <i class="fa-solid fa-key"></i>
                </div>
                <h3 class="text-xl sm:text-2xl font-black text-white">استعادة كلمة السر للأعضاء</h3>
                <p class="text-xs sm:text-sm text-emerald-200/70 mt-1">أدخل رقم الهاتف المسجل لاسترجاع بيانات الدخول فوراً</p>
            </div>

            <form onsubmit="handleForgotPassword(event)" class="space-y-4">
                <div>
                    <label class="block text-xs font-bold text-emerald-200 mb-2">رقم الهاتف المسجل</label>
                    <div class="relative">
                        <span class="absolute inset-y-0 right-0 flex items-center pr-3.5 text-emerald-400/60">
                            <i class="fa-solid fa-phone"></i>
                        </span>
                        <input tabindex="0" type="tel" id="recoveryPhone" required placeholder="مثال: 38121180" 
                            class="w-full pl-4 pr-11 py-3.5 bg-emerald-950/80 border border-emerald-800/80 rounded-xl text-white placeholder-emerald-600/60 focus:outline-none focus:border-amber-400 transition text-sm dir-ltr text-right font-mono">
                    </div>
                </div>

                <button tabindex="0" type="submit" class="w-full py-3.5 px-5 bg-gradient-to-r from-amber-500 to-amber-600 hover:from-amber-600 hover:to-amber-700 text-emerald-950 font-black rounded-xl shadow-lg transition flex items-center justify-center gap-2 text-sm cursor-pointer">
                    <i class="fa-solid fa-magnifying-glass"></i>
                    <span>البحث عن البيانات</span>
                </button>
            </form>

            <!-- Recovery Result Area -->
            <div id="recoveryResult" class="hidden mt-6 p-4 rounded-2xl border text-sm"></div>
        </div>
    </div>

    <!-- Footer -->
    <footer class="border-t border-emerald-900/60 glass-panel py-6 text-center text-xs text-emerald-400/60">
        <div class="max-w-7xl mx-auto px-4">
            <p class="amiri-font text-lg text-amber-300/90 mb-1">مضيف أهل العباء</p>
            <p>جميع الحقوق محفوظة &copy; 2026</p>
        </div>
    </footer>

    <script>
        // Database of registered members for M
        const usersDatabase = [
            {
                phone: "38121180",
                username: "abbas@2013",
                password: "abbas@38121180",
                name: "عباس"
            },
            {
                phone: "33184684",
                username: "majeed@1983",
                password: "majeed@33184684",
                name: "مجيد"
            },
            {
                phone: "39541014",
                username: "mohd@1986",
                password: "mohd@39541014",
                name: "محمد"
            },
            {
                phone: "33793910",
                username: "zuhair@1988",
                password: "zuhair@33793910",
                name: "زهير"
            }
        ];

        // Toggle Password Visibility
        function togglePasswordVisibility(inputId, iconId) {
            const input = document.getElementById(inputId);
            const icon = document.getElementById(iconId);
            if (input.type === "password") {
                input.type = "text";
                icon.classList.remove("fa-eye");
                icon.classList.add("fa-eye-slash");
            } else {
                input.type = "password";
                icon.classList.remove("fa-eye-slash");
                icon.classList.add("fa-eye");
            }
        }

        // Display Notification Alerts
        function showAlert(elementId, message, type = "error") {
            const alertEl = document.getElementById(elementId);
            alertEl.classList.remove("hidden", "bg-red-950/90", "border-red-600", "text-red-200", "bg-emerald-950/90", "border-emerald-600", "text-emerald-200");
            
            if (type === "error") {
                alertEl.classList.add("bg-red-950/90", "border", "border-red-600", "text-red-200");
                alertEl.innerHTML = `<i class="fa-solid fa-circle-exclamation text-red-400 text-base"></i> <span>${message}</span>`;
            } else {
                alertEl.classList.add("bg-emerald-950/90", "border", "border-emerald-600", "text-emerald-200");
                alertEl.innerHTML = `<i class="fa-solid fa-circle-check text-emerald-400 text-base"></i> <span>${message}</span>`;
            }
        }

        // Handle User Login
        function handleLogin(event) {
            event.preventDefault();
            const usernameInput = document.getElementById("loginUsername").value.trim();
            const passwordInput = document.getElementById("loginPassword").value.trim();

            const user = usersDatabase.find(u => u.username === usernameInput && u.password === passwordInput);

            if (user) {
                sessionStorage.setItem("currentUser", JSON.stringify(user));
                displayDashboard(user);
            } else {
                showAlert("loginAlert", "اسم المستخدم أو كلمة السر غير صحيحة. يرجى التثبت والمحاولة مجدداً.", "error");
            }
        }

        // Display Dashboard for Logged In User
        function displayDashboard(user) {
            document.getElementById("loginSection").classList.add("hidden");
            document.getElementById("dashboardSection").classList.remove("hidden");
            document.getElementById("navUserArea").classList.remove("hidden");
            
            document.getElementById("navWelcomeMsg").textContent = `أهلاً بك، ${user.name}`;
            document.getElementById("dashWelcomeTitle").textContent = `مرحباً بك، الأخ ${user.name}`;
            document.getElementById("userPhoneBadge").textContent = `هاتف: ${user.phone}`;
            document.getElementById("dashUsernameVal").textContent = user.username;
            document.getElementById("dashPhoneVal").textContent = user.phone;
        }

        // Logout Functionality
        function logout() {
            sessionStorage.removeItem("currentUser");
            document.getElementById("dashboardSection").classList.add("hidden");
            document.getElementById("navUserArea").classList.add("hidden");
            document.getElementById("loginSection").classList.remove("hidden");
            document.getElementById("loginUsername").value = "";
            document.getElementById("loginPassword").value = "";
            document.getElementById("loginAlert").classList.add("hidden");
        }

        // Modal Controls
        function showForgotPasswordModal() {
            document.getElementById("forgotPasswordModal").classList.remove("hidden");
            document.getElementById("recoveryPhone").value = "";
            document.getElementById("recoveryResult").classList.add("hidden");
            setTimeout(() => {
                document.getElementById("recoveryPhone").focus();
            }, 100);
        }

        function closeForgotPasswordModal() {
            document.getElementById("forgotPasswordModal").classList.add("hidden");
        }

        // Handle Forgot Password Search by Phone
        function handleForgotPassword(event) {
            event.preventDefault();
            const phoneInput = document.getElementById("recoveryPhone").value.trim();
            const resultBox = document.getElementById("recoveryResult");

            // Strip non-digits
            const sanitizedPhone = phoneInput.replace(/[^0-9]/g, '');

            const user = usersDatabase.find(u => u.phone === sanitizedPhone);

            resultBox.classList.remove("hidden");

            if (user) {
                resultBox.className = "mt-6 p-4 rounded-2xl border border-amber-500/50 bg-emerald-950/90 text-emerald-100 space-y-3";
                resultBox.innerHTML = `
                    <div class="flex items-center gap-2 text-amber-400 font-bold border-b border-amber-500/20 pb-2">
                        <i class="fa-solid fa-circle-check text-emerald-400"></i>
                        <span>تم العثور على حسابك بنجاح!</span>
                    </div>
                    <div class="space-y-1.5 text-xs text-emerald-200">
                        <p><strong class="text-white">الاسم:</strong> ${user.name}</p>
                        <p><strong class="text-white">اسم المستخدم:</strong> <span class="font-mono text-amber-300 font-bold">${user.username}</span></p>
                        <p><strong class="text-white">كلمة السر:</strong> <span class="font-mono text-amber-300 font-bold">${user.password}</span></p>
                    </div>
                    <button tabindex="0" onclick="fillLoginFromRecovery('${user.username}', '${user.password}')" class="w-full mt-2 py-2.5 bg-amber-500/20 hover:bg-amber-500/30 text-amber-300 border border-amber-500/40 rounded-xl text-xs font-bold transition flex items-center justify-center gap-2 cursor-pointer">
                        <i class="fa-solid fa-arrow-right-to-bracket"></i>
                        <span>تعبئة البيانات تلقائياً والتوجيه للدخول</span>
                    </button>
                `;
            } else {
                resultBox.className = "mt-6 p-4 rounded-2xl border border-red-500/50 bg-red-950/90 text-red-200";
                resultBox.innerHTML = `
                    <div class="flex items-center gap-2 font-bold mb-1 text-red-300">
                        <i class="fa-solid fa-triangle-exclamation text-red-400"></i>
                        <span>رقم الهاتف غير مسجل!</span>
                    </div>
                    <p class="text-xs text-red-300/80">لم نجد أي حساب مرتبط برقم الهاتف (${phoneInput}). يرجى التأكد من الرقم والبحث مجدداً.</p>
                `;
            }
        }

        // Fill Login From Recovery Helper
        function fillLoginFromRecovery(username, password) {
            closeForgotPasswordModal();
            document.getElementById("loginUsername").value = username;
            document.getElementById("loginPassword").value = password;
            showAlert("loginAlert", "تمت تعبئة بيانات الدخول بنجاح! انقر على زر تسجيل الدخول.", "success");
        }

        // Check active session on load
        window.onload = function() {
            const savedUser = sessionStorage.getItem("currentUser");
            if (savedUser) {
                displayDashboard(JSON.parse(savedUser));
            }
        };
    </script>
</body>
</html>
