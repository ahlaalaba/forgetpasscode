<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>مضيف أهل العباء - المنصة الرسمية</title>
    
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    
    <!-- Font Awesome Icons CDN -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <!-- Google Arabic Fonts: Cairo & Amiri -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@300;400;600;700;800;900&family=Amiri:ital,wght@0,400;0,700;1,400&display=swap" rel="stylesheet">

    <!-- SheetJS Library for Exporting Excel Files -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/xlsx/0.18.5/xlsx.full.min.js"></script>

    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        gold: {
                            50: '#fffbf0',
                            100: '#fef4d6',
                            300: '#fbe094',
                            400: '#f3ca52',
                            500: '#d4af37',
                            600: '#b89228',
                            700: '#94721c',
                            800: '#735619',
                            900: '#4e3910'
                        },
                        emeraldCustom: {
                            800: '#0d382c',
                            900: '#07241c',
                            950: '#03140f',
                        }
                    },
                    fontFamily: {
                        cairo: ['Cairo', 'sans-serif'],
                        amiri: ['Amiri', 'serif'],
                    }
                }
            }
        }
    </script>

    <style>
        body {
            font-family: 'Cairo', sans-serif;
            background-color: #030a08;
            color: #e2e8f0;
            background-image: radial-gradient(circle at 50% 0%, #0e3d30 0%, #030a08 85%);
            min-height: 100vh;
        }

        .gold-gradient-text {
            background: linear-gradient(135deg, #fff2aa 0%, #d4af37 50%, #9e7a1b 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .glass-panel {
            background: rgba(13, 35, 28, 0.88);
            backdrop-filter: blur(16px);
            border: 1px solid rgba(212, 175, 55, 0.25);
            box-shadow: 0 12px 35px 0 rgba(0, 0, 0, 0.6);
        }

        .glass-input {
            background: rgba(4, 18, 14, 0.85);
            border: 1px solid rgba(212, 175, 55, 0.3);
            color: #fff;
            transition: all 0.2s ease-in-out;
        }

        .glass-input:focus, .glass-input:focus-visible {
            border-color: #d4af37;
            box-shadow: 0 0 14px rgba(212, 175, 55, 0.4);
            outline: 2px solid #d4af37;
        }

        /* Focus Ring for PlayStation Controller and Keyboard Navigation */
        a:focus-visible, button:focus-visible, input:focus-visible, select:focus-visible, textarea:focus-visible {
            outline: 3px solid #f3ca52 !important;
            outline-offset: 3px !important;
            border-radius: 8px;
        }

        ::-webkit-scrollbar {
            width: 8px;
        }
        ::-webkit-scrollbar-track {
            background: #030a08;
        }
        ::-webkit-scrollbar-thumb {
            background: #2a4c40;
            border-radius: 4px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #d4af37;
        }

        @keyframes phoneRing {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-5px); }
        }
        .phone-anim {
            animation: phoneRing 1.5s infinite ease-in-out;
        }
    </style>
</head>
<body class="flex flex-col min-h-screen selection:bg-gold-500 selection:text-emeraldCustom-950">

    <div id="toastContainer" class="fixed top-5 left-5 z-50 flex flex-col gap-3 max-w-sm w-full pointer-events-none"></div>

    <!-- SMS Push Notification Modal -->
    <div id="smsNotificationModal" class="fixed top-6 right-6 z-50 max-w-sm w-full hidden transition-all duration-300">
        <div class="glass-panel p-4 rounded-2xl border-2 border-gold-500 shadow-2xl bg-emeraldCustom-950/95 relative overflow-hidden">
            <div class="flex items-center justify-between border-b border-gold-500/20 pb-2 mb-2">
                <div class="flex items-center gap-2">
                    <span class="w-2.5 h-2.5 rounded-full bg-emerald-400 animate-ping"></span>
                    <i class="fa-solid fa-comment-sms text-gold-500 text-lg phone-anim"></i>
                    <span class="font-bold text-xs text-gold-500 tracking-wider">رسالة نصية جديدة من: <span class="font-mono underline">ahlalabaa</span></span>
                </div>
                <button onclick="closeSmsModal()" class="text-gray-400 hover:text-white text-xs p-1" title="إغلاق الإشعار">
                    <i class="fa-solid fa-xmark text-sm"></i>
                </button>
            </div>
            <div class="space-y-1.5">
                <p class="text-xs font-semibold text-white">مضيف أهل العباء</p>
                <div class="p-3 rounded-xl bg-black/60 border border-gold-500/40 text-gold-300 font-mono text-sm tracking-wide" id="smsContentBody">
                    <!-- Dynamic SMS Content Injected -->
                </div>
                <p class="text-[10px] text-gray-400 text-left">الآن • عبر شبكة الجوال</p>
            </div>
        </div>
    </div>

    <header class="border-b border-gold-500/20 bg-emeraldCustom-950/90 sticky top-0 z-40 backdrop-blur-md">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 h-20 flex items-center justify-between gap-2">
            
            <!-- Logo & Title -->
            <div class="flex items-center space-x-3 space-x-reverse cursor-pointer group" onclick="switchView('home')" tabindex="0" onkeydown="if(event.key==='Enter') switchView('home')">
                <div class="w-12 h-12 rounded-full border-2 border-gold-500 flex items-center justify-center bg-emeraldCustom-900 shadow-lg shadow-gold-500/20 group-hover:scale-105 transition">
                    <i class="fa-solid text-2xl text-gold-500">🕌</i>
                </div>
                <div>
                    <h1 class="text-lg sm:text-xl font-bold font-amiri gold-gradient-text tracking-wide leading-none">مضيف أهل العباء</h1>
                    <p class="text-[10px] sm:text-[11px] text-gold-500/70 mt-1">منصة الضيافة والخدمة الرقمية المباركة</p>
                </div>
            </div>

            <!-- Social Links & Navigation -->
            <div class="flex items-center gap-2 sm:gap-4">
                <div class="hidden md:flex items-center gap-2 border-l border-gold-500/20 pl-4 ml-2">
                    <a href="https://www.instagram.com/ahlaalaba/?hl=en" target="_blank" rel="noopener noreferrer" title="إنستغرام مضيف أهل العباء" class="flex items-center gap-1.5 px-3 py-1.5 rounded-xl bg-pink-950/40 border border-pink-500/30 text-pink-300 hover:bg-pink-600 hover:text-white transition text-xs font-semibold">
                        <i class="fa-brands fa-instagram text-base"></i>
                        <span>إنستغرام</span>
                    </a>
                    <a href="https://www.youtube.com/@Ahlaalaba" target="_blank" rel="noopener noreferrer" title="قناة يوتيوب مضيف أهل العباء" class="flex items-center gap-1.5 px-3 py-1.5 rounded-xl bg-red-950/40 border border-red-500/30 text-red-300 hover:bg-red-600 hover:text-white transition text-xs font-semibold">
                        <i class="fa-brands fa-youtube text-base"></i>
                        <span>يوتيوب</span>
                    </a>
                </div>

                <div id="navUserArea" class="flex items-center gap-2"></div>
            </div>
        </div>
    </header>

    <main class="flex-grow max-w-7xl w-full mx-auto px-4 sm:px-6 lg:px-8 py-8">

        <!-- Authentication Section (Hidden Admin ahlalabaa Enforced) -->
        <section id="authSection" class="max-w-md mx-auto my-6 hidden">
            <div class="glass-panel rounded-3xl p-6 sm:p-8 relative overflow-hidden border border-gold-500/30">
                <div class="absolute -top-12 -right-12 w-32 h-32 bg-gold-500/10 rounded-full blur-2xl pointer-events-none"></div>

                <!-- Auth Navigation Tabs -->
                <div id="authTabsHeader" class="flex border-b border-gold-500/20 mb-6">
                    <button id="tabLoginBtn" onclick="switchAuthMode('login')" class="flex-1 pb-3 text-center text-sm sm:text-base font-semibold border-b-2 border-gold-500 text-gold-500 transition-all">
                        تسجيل الدخول
                    </button>
                    <button id="tabRegisterBtn" onclick="switchAuthMode('register')" class="flex-1 pb-3 text-center text-sm sm:text-base font-semibold border-b-2 border-transparent text-gray-400 hover:text-gray-200 transition-all">
                        إنشاء حساب زائر
                    </button>
                </div>

                <!-- Login Form -->
                <form id="loginForm" onsubmit="handleLogin(event)" class="space-y-4">
                    <div>
                        <label class="block text-xs font-medium mb-1 text-gray-300">اسم المستخدم أو رقم الهاتف</label>
                        <div class="relative">
                            <span class="absolute inset-y-0 right-0 flex items-center pr-3 text-gold-500/60">
                                <i class="fa-solid fa-user text-sm"></i>
                            </span>
                            <input type="text" id="loginIdentifier" required class="glass-input w-full pr-10 pl-3 py-3 rounded-xl text-sm" placeholder="اسم المستخدم">
                        </div>
                    </div>
                    <div>
                        <label class="block text-xs font-medium mb-1 text-gray-300">كلمة المرور</label>
                        <div class="relative">
                            <span class="absolute inset-y-0 right-0 flex items-center pr-3 text-gold-500/60">
                                <i class="fa-solid fa-lock text-sm"></i>
                            </span>
                            <input type="password" id="loginPassword" required class="glass-input w-full pr-10 pl-3 py-3 rounded-xl text-sm" placeholder="••••••••">
                        </div>
                    </div>

                    <div class="flex justify-between items-center text-xs pt-1">
                        <button type="button" onclick="switchAuthMode('forgot')" class="text-gold-500/90 hover:text-gold-300 transition underline underline-offset-4">
                            هل نسيت كلمة المرور؟
                        </button>
                    </div>

                    <button type="submit" class="w-full py-3.5 bg-gradient-to-r from-gold-600 via-gold-500 to-gold-600 hover:brightness-110 text-emeraldCustom-950 font-bold rounded-xl shadow-lg shadow-gold-500/20 transition duration-200 text-sm">
                        تسجيل الدخول
                    </button>
                </form>

                <!-- Visitor Registration Form -->
                <form id="registerForm" onsubmit="handleRegister(event)" class="space-y-4 hidden">
                    <p class="text-[11px] text-amber-300/80 bg-amber-950/40 border border-amber-500/30 p-2.5 rounded-xl mb-2">
                        <i class="fa-solid fa-circle-info ml-1"></i> التسجيل متاح للزوار فقط. الحسابات الإدارية والرسمية محفوظة ومسبقة الضبط.
                    </p>
                    <div>
                        <label class="block text-xs font-medium mb-1 text-gray-300">الاسم الكامل</label>
                        <input type="text" id="regFullName" required class="glass-input w-full px-3 py-2.5 rounded-xl text-sm" placeholder="مثال: علي الحسين">
                    </div>
                    <div>
                        <label class="block text-xs font-medium mb-1 text-gray-300">اسم المستخدم</label>
                        <input type="text" id="regUsername" required class="glass-input w-full px-3 py-2.5 rounded-xl text-sm" placeholder="visitor_1">
                    </div>
                    <div>
                        <label class="block text-xs font-medium mb-1 text-gray-300">البلد ورقم الهاتف</label>
                        <div class="grid grid-cols-3 gap-2">
                            <select id="regCountry" class="glass-input px-2 py-2.5 rounded-xl text-xs col-span-1">
                                <option value="العراق (+964)">العراق (+964)</option>
                                <option value="البحرين (+973)">البحرين (+973)</option>
                                <option value="السعودية (+966)">السعودية (+966)</option>
                                <option value="الكويت (+965)">الكويت (+965)</option>
                                <option value="الإمارات (+971)">الإمارات (+971)</option>
                                <option value="عُمان (+968)">عُمان (+968)</option>
                            </select>
                            <input type="tel" id="regPhone" required class="glass-input w-full px-3 py-2.5 rounded-xl text-sm col-span-2" placeholder="07XXXXXXXX">
                        </div>
                    </div>
                    <div>
                        <label class="block text-xs font-medium mb-1 text-gray-300">كلمة المرور</label>
                        <input type="password" id="regPassword" required minlength="6" class="glass-input w-full px-3 py-2.5 rounded-xl text-sm" placeholder="••••••••">
                    </div>
                    <button type="submit" class="w-full py-3 bg-gradient-to-r from-gold-600 to-gold-500 hover:from-gold-500 hover:to-gold-600 text-emeraldCustom-950 font-bold rounded-xl shadow-lg shadow-gold-500/20 transition duration-200 text-sm">
                        إنشاء حساب جديد
                    </button>
                </form>

                <!-- Forgot Password Step 1: Phone & Country Selection -->
                <div id="forgotStep1" class="space-y-4 hidden">
                    <div class="text-center mb-4">
                        <i class="fa-solid fa-mobile-screen-button text-3xl text-gold-500 mb-2"></i>
                        <h3 class="font-bold text-lg text-gold-500 font-amiri">استعادة كلمة المرور</h3>
                        <p class="text-xs text-gray-400">أدخل الدولة ورقم الهاتف المسجل لإرسال رمز التحقق النصي باسم <strong class="text-gold-300">ahlalabaa</strong></p>
                    </div>

                    <form onsubmit="handleSendResetCode(event)" class="space-y-4">
                        <div>
                            <label class="block text-xs font-medium mb-1 text-gray-300">اختر الدولة</label>
                            <select id="forgotCountry" required class="glass-input w-full px-3 py-2.5 rounded-xl text-sm">
                                <option value="العراق">العراق (+964)</option>
                                <option value="البحرين">البحرين (+973)</option>
                                <option value="السعودية">السعودية (+966)</option>
                                <option value="الكويت">الكويت (+965)</option>
                                <option value="الإمارات">الإمارات (+971)</option>
                                <option value="عُمان">عُمان (+968)</option>
                                <option value="دولة أخرى">دولة أخرى</option>
                            </select>
                        </div>

                        <div>
                            <label class="block text-xs font-medium mb-1 text-gray-300">رقم الهاتف المسجل</label>
                            <input type="tel" id="forgotPhone" required class="glass-input w-full px-3 py-2.5 rounded-xl text-sm" placeholder="07XXXXXXXX">
                        </div>

                        <button type="submit" class="w-full py-3 bg-gold-500 hover:bg-gold-600 text-emeraldCustom-950 font-bold rounded-xl text-sm shadow-lg transition flex items-center justify-center gap-2">
                            <i class="fa-solid fa-paper-plane"></i> إرسال رمز التحقق النصي
                        </button>

                        <button type="button" onclick="switchAuthMode('login')" class="w-full py-2 bg-transparent text-gray-400 hover:text-white text-xs transition text-center">
                            إلغاء والعودة لتسجيل الدخول
                        </button>
                    </form>
                </div>

                <!-- Forgot Password Step 2: OTP Verification -->
                <div id="forgotStep2" class="space-y-4 hidden">
                    <div class="text-center mb-4">
                        <i class="fa-solid fa-shield-halved text-3xl text-gold-500 mb-2"></i>
                        <h3 class="font-bold text-lg text-gold-500 font-amiri">تأكيد رمز التحقق (OTP)</h3>
                        <p class="text-xs text-gray-400">تم إرسال رمز التحقق في رسالة SMS من المرسل <span class="text-gold-500 font-bold">ahlalabaa</span></p>
                    </div>

                    <form onsubmit="handleVerifyResetCode(event)" class="space-y-4">
                        <div>
                            <label class="block text-xs font-medium mb-1 text-gray-300">أدخل رمز التحقق (4 أرقام)</label>
                            <input type="text" id="otpInput" maxlength="4" required class="glass-input w-full px-3 py-3 rounded-xl text-center text-xl tracking-widest font-mono text-gold-500" placeholder="••••">
                        </div>

                        <button type="submit" class="w-full py-3 bg-gold-500 hover:bg-gold-600 text-emeraldCustom-950 font-bold rounded-xl text-sm shadow-lg transition">
                            تحقق وتأكيد الرمز
                        </button>

                        <button type="button" onclick="switchAuthMode('forgot')" class="w-full py-2 bg-transparent text-gray-400 hover:text-white text-xs transition text-center">
                            إعادة إرسال أو تغيير الرقم
                        </button>
                    </form>
                </div>

                <!-- Forgot Password Step 3: Password Reset -->
                <div id="forgotStep3" class="space-y-4 hidden">
                    <div class="text-center mb-4">
                        <i class="fa-solid fa-key text-3xl text-gold-500 mb-2"></i>
                        <h3 class="font-bold text-lg text-gold-500 font-amiri">تعيين كلمة مرور جديدة</h3>
                        <p class="text-xs text-gray-400">تم التحقق من الرمز بنجاح. أدخل كلمة المرور الجديدة للحساب.</p>
                    </div>

                    <form onsubmit="handleResetPasswordSubmit(event)" class="space-y-4">
                        <div>
                            <label class="block text-xs font-medium mb-1 text-gray-300">كلمة المرور الجديدة</label>
                            <input type="password" id="resetNewPass" required minlength="6" class="glass-input w-full px-3 py-2.5 rounded-xl text-sm" placeholder="••••••••">
                        </div>

                        <div>
                            <label class="block text-xs font-medium mb-1 text-gray-300">تأكيد كلمة المرور الجديدة</label>
                            <input type="password" id="resetConfirmPass" required minlength="6" class="glass-input w-full px-3 py-2.5 rounded-xl text-sm" placeholder="••••••••">
                        </div>

                        <button type="submit" class="w-full py-3 bg-gradient-to-r from-gold-600 to-gold-500 hover:from-gold-500 hover:to-gold-600 text-emeraldCustom-950 font-bold rounded-xl text-sm shadow-lg transition">
                            حفظ كلمة المرور الجديدة
                        </button>
                    </form>
                </div>

            </div>
        </section>

        <section id="homeSection" class="space-y-8">
            <!-- Hero Banner -->
            <div class="glass-panel rounded-3xl p-8 sm:p-12 relative overflow-hidden text-center border border-gold-500/30">
                <div class="max-w-3xl mx-auto space-y-4 relative z-10">
                    <span class="inline-block px-4 py-1.5 rounded-full bg-gold-500/10 text-gold-500 border border-gold-500/30 text-xs font-semibold mb-2">
                        ✨ أهلاً وسهلاً بكم في مضيف أهل العباء ✨
                    </span>
                    <h2 class="text-3xl sm:text-5xl font-bold font-amiri gold-gradient-text leading-tight">
                        خدمة، ضيافة، وبركة مباركة
                    </h2>
                    <p class="text-gray-300 text-sm sm:text-base leading-relaxed">
                        نرحب بضيوف الرحمن والكرام في معرض ومجلس مضيف أهل العباء. استعرضوا صور الخدمات المباركة والفعاليات، ويمكنكم متابعة جديدنا على شبكات التواصل الاجتماعي.
                    </p>

                    <!-- Social Media Links -->
                    <div class="pt-4 flex flex-wrap justify-center items-center gap-3">
                        <a href="https://www.instagram.com/ahlaalaba/?hl=en" target="_blank" rel="noopener noreferrer" class="px-5 py-2.5 rounded-xl bg-gradient-to-r from-pink-700 to-purple-800 text-white hover:brightness-110 transition text-xs font-bold flex items-center gap-2 shadow-lg">
                            <i class="fa-brands fa-instagram text-lg"></i>
                            <span>حساب الإنستغرام الرسمي (@ahlaalaba)</span>
                        </a>
                        <a href="https://www.youtube.com/@Ahlaalaba" target="_blank" rel="noopener noreferrer" class="px-5 py-2.5 rounded-xl bg-gradient-to-r from-red-700 to-red-600 text-white hover:brightness-110 transition text-xs font-bold flex items-center gap-2 shadow-lg">
                            <i class="fa-brands fa-youtube text-lg"></i>
                            <span>قناة اليوتيوب الرسمية (@Ahlaalaba)</span>
                        </a>
                    </div>
                </div>
            </div>

            <!-- Board Members Cards -->
            <div class="glass-panel rounded-3xl p-6 border border-gold-500/20">
                <h3 class="text-xl font-bold font-amiri text-gold-500 mb-4 flex items-center gap-2">
                    <i class="fa-solid fa-users"></i> الهيئة الإدارية والإعلامية لمضيف أهل العباء
                </h3>
                <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-4">
                    <!-- President -->
                    <div class="p-4 rounded-2xl bg-emeraldCustom-950/80 border border-gold-500/30 flex items-center gap-3">
                        <div class="w-10 h-10 rounded-full bg-gold-500/20 border border-gold-500/40 flex items-center justify-center text-gold-500 text-lg font-bold">
                            👑
                        </div>
                        <div>
                            <span class="text-[10px] px-2 py-0.5 rounded bg-gold-500/20 text-gold-400 font-bold">رئيس المضيف</span>
                            <h4 class="font-bold text-sm text-white mt-0.5">محمد الشيخ</h4>
                            <p class="text-[10px] text-gray-400 font-mono">mohd@1986</p>
                        </div>
                    </div>

                    <!-- Vice President -->
                    <div class="p-4 rounded-2xl bg-emeraldCustom-950/80 border border-gold-500/30 flex items-center gap-3">
                        <div class="w-10 h-10 rounded-full bg-gold-500/20 border border-gold-500/40 flex items-center justify-center text-gold-500 text-lg font-bold">
                            🎖️
                        </div>
                        <div>
                            <span class="text-[10px] px-2 py-0.5 rounded bg-amber-500/20 text-amber-300 font-bold">نائب الرئيس</span>
                            <h4 class="font-bold text-sm text-white mt-0.5">مجيد الشيخ</h4>
                            <p class="text-[10px] text-gray-400 font-mono">majeed@1983</p>
                        </div>
                    </div>

                    <!-- Media Committee -->
                    <div class="p-4 rounded-2xl bg-emeraldCustom-950/80 border border-gold-500/30 flex items-center gap-3">
                        <div class="w-10 h-10 rounded-full bg-gold-500/20 border border-gold-500/40 flex items-center justify-center text-gold-500 text-lg font-bold">
                            📢
                        </div>
                        <div>
                            <span class="text-[10px] px-2 py-0.5 rounded bg-emerald-500/20 text-emerald-300 font-bold">اللجنة الإعلامية</span>
                            <h4 class="font-bold text-sm text-white mt-0.5">زهير الشيخ</h4>
                            <p class="text-[10px] text-gray-400 font-mono">zuhair@1988</p>
                        </div>
                    </div>

                    <!-- Mourning Committee -->
                    <div class="p-4 rounded-2xl bg-emeraldCustom-950/80 border border-gold-500/30 flex items-center gap-3">
                        <div class="w-10 h-10 rounded-full bg-gold-500/20 border border-gold-500/40 flex items-center justify-center text-gold-500 text-lg font-bold">
                            🏴
                        </div>
                        <div>
                            <span class="text-[10px] px-2 py-0.5 rounded bg-purple-500/20 text-purple-300 font-bold">لجنة العزاء</span>
                            <h4 class="font-bold text-sm text-white mt-0.5">عباس الشيخ</h4>
                            <p class="text-[10px] text-gray-400 font-mono">abbas@2013</p>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Public Gallery Grid Header -->
            <div>
                <div class="flex flex-col sm:flex-row justify-between items-start sm:items-center mb-6 gap-4 border-b border-gold-500/20 pb-4">
                    <div>
                        <h3 class="text-2xl font-bold font-amiri text-gold-500 flex items-center gap-2">
                            <i class="fa-solid fa-images"></i> معرض صور ونشاطات المضيف المبارك
                        </h3>
                        <p class="text-xs text-gray-400 mt-1">تحديثات وتغطيات خدمات المضيف والفعاليات</p>
                    </div>

                    <div id="galleryAuthorizedActions" class="hidden flex items-center gap-2">
                        <button onclick="openUploadModal()" class="px-4 py-2.5 bg-gold-500 hover:bg-gold-600 text-emeraldCustom-950 font-bold rounded-xl shadow-md transition flex items-center gap-2 text-xs sm:text-sm">
                            <i class="fa-solid fa-plus"></i> تنزيل / نشر صورة جديدة
                        </button>
                    </div>
                </div>

                <div id="galleryGrid" class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6">
                    <!-- Dynamic Gallery Injected -->
                </div>
            </div>
        </section>

        <section id="adminDashboardSection" class="space-y-8 hidden">
            <!-- Dashboard Banner -->
            <div class="glass-panel rounded-3xl p-6 border-r-4 border-r-gold-500 flex flex-col md:flex-row justify-between items-start md:items-center gap-4">
                <div>
                    <div class="flex items-center gap-2 mb-1">
                        <span id="dashboardRoleBadge" class="px-2.5 py-0.5 rounded-md bg-gold-500/20 text-gold-500 text-xs font-bold border border-gold-500/30">لوحة التحكم الإدارية</span>
                        <h2 class="text-2xl font-bold text-white font-amiri" id="dashboardTitle">إدارة منصة مضيف أهل العباء</h2>
                    </div>
                    <p class="text-xs text-gray-400">إدارة المعرض، رفع الصور، وتصدير بيانات الحسابات إكسل (Excel)</p>
                </div>

                <div class="flex flex-wrap gap-3">
                    <button id="excelExportBtn" onclick="exportAccountsToExcel()" class="px-4 py-2.5 bg-emerald-700 hover:bg-emerald-600 text-white font-bold rounded-xl text-xs sm:text-sm transition flex items-center gap-2 shadow-lg border border-emerald-400/40">
                        <i class="fa-solid fa-file-excel text-base"></i> تصدير قائمة الحسابات (Excel)
                    </button>
                    <button onclick="openUploadModal()" class="px-4 py-2.5 bg-gold-500 hover:bg-gold-600 text-emeraldCustom-950 font-bold rounded-xl text-xs sm:text-sm transition flex items-center gap-2 shadow-lg">
                        <i class="fa-solid fa-cloud-arrow-up"></i> رفع / إضافة صورة
                    </button>
                    <button onclick="openPasswordModal()" class="px-4 py-2.5 bg-emeraldCustom-900 hover:bg-emeraldCustom-800 text-gold-500 border border-gold-500/40 rounded-xl text-xs sm:text-sm font-semibold transition flex items-center gap-2">
                        <i class="fa-solid fa-key"></i> تغيير كلمة المرور (يشترط القديمة)
                    </button>
                </div>
            </div>

            <!-- Excel Preview & Accounts View for Admin/Media Committee Exclusive -->
            <div id="excelAccountsCard" class="glass-panel rounded-3xl p-6">
                <div class="flex justify-between items-center mb-4">
                    <h3 class="text-xl font-bold text-gold-500 font-amiri flex items-center gap-2">
                        <i class="fa-solid fa-table-list"></i> قائمة الحسابات والأرقام السرية المسجلة
                    </h3>
                    <button onclick="exportAccountsToExcel()" class="px-3 py-1.5 bg-emerald-700/80 hover:bg-emerald-600 text-white rounded-lg text-xs font-semibold flex items-center gap-1.5">
                        <i class="fa-solid fa-download"></i> تنزيل كملف Excel (.xlsx)
                    </button>
                </div>
                
                <div class="overflow-x-auto rounded-2xl border border-gold-500/20">
                    <table class="w-full text-right text-xs text-gray-300">
                        <thead class="bg-emeraldCustom-900 text-gold-400 font-bold border-b border-gold-500/30">
                            <tr>
                                <th class="p-3">#</th>
                                <th class="p-3">الاسم الكامل / الصفة</th>
                                <th class="p-3">اسم المستخدم</th>
                                <th class="p-3">الرقم السري (Password)</th>
                                <th class="p-3">الدولة / الهاتف</th>
                                <th class="p-3">نوع الحساب</th>
                            </tr>
                        </thead>
                        <tbody id="accountsTableBody" class="divide-y divide-gold-500/10 bg-black/40">
                            <!-- Dynamic Excel Table Preview -->
                        </tbody>
                    </table>
                </div>
            </div>

            <!-- Gallery Control Panel -->
            <div class="glass-panel rounded-3xl p-6">
                <h3 class="text-xl font-bold text-gold-500 mb-4 font-amiri flex items-center gap-2">
                    <i class="fa-solid fa-sliders"></i> إدارة محتوى المعرض (<span id="adminImageCount">0</span> صورة)
                </h3>
                <div id="adminGalleryGrid" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
                    <!-- Dynamic Admin Images Cards -->
                </div>
            </div>
        </section>

    </main>


    <!-- 1. EDIT PROFILE MODAL -->
    <div id="profileModal" class="fixed inset-0 z-50 flex items-center justify-center bg-black/80 backdrop-blur-sm hidden p-4">
        <div class="glass-panel w-full max-w-md rounded-3xl p-6 relative border border-gold-500/40">
            <button onclick="closeModal('profileModal')" class="absolute top-4 left-4 text-gray-400 hover:text-white text-lg p-2" title="إغلاق">
                <i class="fa-solid fa-xmark"></i>
            </button>
            <h3 class="text-xl font-bold text-gold-500 font-amiri mb-1 flex items-center gap-2">
                <i class="fa-solid fa-id-card"></i> تعديل الملف الشخصي
            </h3>
            <p class="text-xs text-gray-400 mb-4">تحديث اسمك وبيانات التواصل الخاصة بك</p>

            <form id="profileForm" onsubmit="handleSaveProfile(event)" class="space-y-4">
                <div>
                    <label class="block text-xs font-medium mb-1 text-gray-300">الاسم الكامل</label>
                    <input type="text" id="profFullName" required class="glass-input w-full px-3 py-2.5 rounded-xl text-sm">
                </div>

                <div>
                    <label class="block text-xs font-medium mb-1 text-gray-300">اسم المستخدم (لا يمكن تغييره)</label>
                    <input type="text" id="profUsername" disabled class="glass-input w-full px-3 py-2.5 rounded-xl text-sm bg-black/50 text-gray-400 cursor-not-allowed">
                </div>

                <div>
                    <label class="block text-xs font-medium mb-1 text-gray-300">رقم الهاتف</label>
                    <input type="tel" id="profPhone" class="glass-input w-full px-3 py-2.5 rounded-xl text-sm" placeholder="07XXXXXXXX">
                </div>

                <div class="flex justify-end gap-3 mt-6">
                    <button type="button" onclick="closeModal('profileModal')" class="px-4 py-2 bg-gray-700 hover:bg-gray-600 rounded-xl text-xs font-semibold">إلغاء</button>
                    <button type="submit" class="px-5 py-2 bg-gold-500 hover:bg-gold-600 text-emeraldCustom-950 font-bold rounded-xl text-xs transition">حفظ التغييرات</button>
                </div>
            </form>
        </div>
    </div>

    <!-- 2. UPLOAD / EDIT IMAGE MODAL -->
    <div id="imageModal" class="fixed inset-0 z-50 flex items-center justify-center bg-black/80 backdrop-blur-sm hidden p-4">
        <div class="glass-panel w-full max-w-lg rounded-3xl p-6 relative border border-gold-500/40">
            <button onclick="closeModal('imageModal')" class="absolute top-4 left-4 text-gray-400 hover:text-white text-lg p-2" title="إغلاق">
                <i class="fa-solid fa-xmark"></i>
            </button>
            <h3 id="imageModalTitle" class="text-xl font-bold text-gold-500 font-amiri mb-4">رفع / إضافة صورة جديدة للمضيف</h3>

            <form id="imageForm" onsubmit="handleSaveImage(event)" class="space-y-4">
                <input type="hidden" id="editImageId">
                
                <div>
                    <label class="block text-xs font-medium mb-1 text-gray-300">عنوان الصورة / الفعالية</label>
                    <input type="text" id="imgTitle" required class="glass-input w-full px-3 py-2.5 rounded-xl text-sm" placeholder="مثال: تقديم وجبات البركة للضيوف">
                </div>

                <div>
                    <label class="block text-xs font-medium mb-1 text-gray-300">الوصف والتفاصيل</label>
                    <textarea id="imgDescription" rows="3" class="glass-input w-full px-3 py-2.5 rounded-xl text-sm" placeholder="وصف مختصر للخدمة أو المناسبة..."></textarea>
                </div>

                <div>
                    <label class="block text-xs font-medium mb-1 text-gray-300">رفع صورة من الجهاز</label>
                    <input type="file" id="imgFileInput" accept="image/*" onchange="previewSelectedImage(event)" class="block w-full text-xs text-gray-400 file:mr-0 file:ml-4 file:py-2 file:px-4 file:rounded-xl file:border-0 file:text-xs file:font-semibold file:bg-gold-500 file:text-emeraldCustom-950 hover:file:bg-gold-600 cursor-pointer">
                    <p class="text-[11px] text-gray-400 mt-1">أو أدخل رابط صورة خارجي مباشرة:</p>
                    <input type="url" id="imgUrlInput" class="glass-input w-full px-3 py-2 rounded-xl text-xs mt-1" placeholder="https://example.com/image.jpg" oninput="previewUrlImage(this.value)">
                </div>

                <!-- Preview Box -->
                <div id="imagePreviewContainer" class="hidden mt-2">
                    <label class="block text-xs font-medium mb-1 text-gray-400">معاينة الصورة:</label>
                    <img id="imagePreview" src="" alt="Preview" class="w-full h-44 object-cover rounded-xl border border-gold-500/30">
                </div>

                <div class="flex justify-end gap-3 mt-6">
                    <button type="button" onclick="closeModal('imageModal')" class="px-4 py-2 bg-gray-700 hover:bg-gray-600 rounded-xl text-xs font-semibold">إلغاء</button>
                    <button type="submit" class="px-5 py-2 bg-gold-500 hover:bg-gold-600 text-emeraldCustom-950 font-bold rounded-xl text-xs transition">حفظ ونشر الصورة</button>
                </div>
            </form>
        </div>
    </div>

    <!-- 3. CHANGE PASSWORD MODAL (Old Password Enforcement) -->
    <div id="passwordModal" class="fixed inset-0 z-50 flex items-center justify-center bg-black/80 backdrop-blur-sm hidden p-4">
        <div class="glass-panel w-full max-w-md rounded-3xl p-6 relative border border-gold-500/40">
            <button onclick="closeModal('passwordModal')" class="absolute top-4 left-4 text-gray-400 hover:text-white text-lg p-2" title="إغلاق">
                <i class="fa-solid fa-xmark"></i>
            </button>
            <h3 class="text-xl font-bold text-gold-500 font-amiri mb-1 flex items-center gap-2">
                <i class="fa-solid fa-shield-halved"></i> تغيير كلمة المرور
            </h3>
            <p class="text-xs text-gray-400 mb-4">شرط أمان: يتطلب إدخال كلمة المرور القديمة لتغيير كلمة المرور الجديدة.</p>

            <form id="changePasswordForm" onsubmit="handleChangePasswordSubmit(event)" class="space-y-4">
                <div>
                    <label class="block text-xs font-medium mb-1 text-gray-300">كلمة المرور القديمة الحالية <span class="text-red-400">*</span></label>
                    <input type="password" id="oldPasswordInput" required class="glass-input w-full px-3 py-2.5 rounded-xl text-sm" placeholder="أدخل كلمة المرور القديمة الحالية">
                </div>

                <div>
                    <label class="block text-xs font-medium mb-1 text-gray-300">كلمة المرور الجديدة <span class="text-gold-500">*</span></label>
                    <input type="password" id="newPasswordInput" required minlength="6" class="glass-input w-full px-3 py-2.5 rounded-xl text-sm" placeholder="أدخل كلمة المرور الجديدة">
                </div>

                <div>
                    <label class="block text-xs font-medium mb-1 text-gray-300">تأكيد كلمة المرور الجديدة <span class="text-gold-500">*</span></label>
                    <input type="password" id="confirmNewPasswordInput" required minlength="6" class="glass-input w-full px-3 py-2.5 rounded-xl text-sm" placeholder="إعادة كتابة كلمة المرور الجديدة">
                </div>

                <div class="flex justify-end gap-3 mt-6">
                    <button type="button" onclick="closeModal('passwordModal')" class="px-4 py-2 bg-gray-700 hover:bg-gray-600 rounded-xl text-xs font-semibold">إلغاء</button>
                    <button type="submit" class="px-5 py-2 bg-gold-500 hover:bg-gold-600 text-emeraldCustom-950 font-bold rounded-xl text-xs transition">حفظ التغييرات</button>
                </div>
            </form>
        </div>
    </div>

    <footer class="border-t border-gold-500/20 bg-emeraldCustom-950/95 py-8 mt-12 text-center text-xs text-gray-400">
        <div class="max-w-7xl mx-auto px-4 flex flex-col md:flex-row justify-between items-center gap-6">
            <div class="text-center md:text-right">
                <p class="font-amiri text-base text-gold-500 font-bold">مضيف أهل العباء © <span id="currentYear"></span></p>
                <p class="text-[11px] text-gray-400 mt-0.5">منصة الخدمة والضيافة والبركة الرقمية - جميع الحقوق محفوظة</p>
            </div>

            <!-- Footer Social Links -->
            <div class="flex items-center gap-4">
                <a href="https://www.instagram.com/ahlaalaba/?hl=en" target="_blank" rel="noopener noreferrer" class="w-10 h-10 rounded-full bg-emeraldCustom-900 border border-gold-500/30 text-gold-500 hover:bg-gold-500 hover:text-emeraldCustom-950 flex items-center justify-center text-lg transition" title="إنستغرام">
                    <i class="fa-brands fa-instagram"></i>
                </a>
                <a href="https://www.youtube.com/@Ahlaalaba" target="_blank" rel="noopener noreferrer" class="w-10 h-10 rounded-full bg-emeraldCustom-900 border border-gold-500/30 text-gold-500 hover:bg-gold-500 hover:text-emeraldCustom-950 flex items-center justify-center text-lg transition" title="يوتيوب">
                    <i class="fa-brands fa-youtube"></i>
                </a>
            </div>
        </div>
    </footer>

    <script>
        // Hidden Default Admin Credentials Configuration
        const ADMIN_CREDENTIALS = {
            username: 'ahlalabaa',
            password: '36386184',
            fullName: 'مدير مضيف أهل العباء (الأدمن)',
            isAdmin: true,
            canExportExcel: true,
            canPublish: true
        };

        // Pre-defined Board Members List with explicit credentials
        const PREDEFINED_MEMBERS = [
            { username: 'mohd@1986', password: 'mohd@39541014', fullName: 'محمد الشيخ (رئيس المضيف)', role: 'رئيس المضيف', country: 'العراق', phone: '0739541014', canExportExcel: false, canPublish: true },
            { username: 'majeed@1983', password: 'majeed@33184684', fullName: 'مجيد الشيخ (نائب الرئيس)', role: 'نائب الرئيس', country: 'العراق', phone: '0733184684', canExportExcel: false, canPublish: true },
            { username: 'zuhair@1988', password: 'zuhair@33793910', fullName: 'زهير الشيخ (اللجنة الإعلامية)', role: 'اللجنة الإعلامية', country: 'العراق', phone: '0733793910', canExportExcel: true, canPublish: true },
            { username: 'abbas@2013', password: 'abbas@38121180', fullName: 'عباس الشيخ (لجنة العزاء)', role: 'لجنة العزاء', country: 'العراق', phone: '0738121180', canExportExcel: false, canPublish: false }
        ];

        // Storage Keys
        const STORAGE_KEYS = {
            ADMIN: 'ahlalabaa_admin_user',
            USERS: 'ahlalabaa_registered_users',
            CURRENT_USER: 'ahlalabaa_current_session',
            IMAGES: 'ahlalabaa_gallery_images'
        };

        // Sample Default Gallery Data
        const DEFAULT_IMAGES = [
            {
                id: 'img-1',
                title: 'تقديم طعام البركة للزوار الكرام',
                description: 'جانب من تقديم الخدمات الغذائية وضيافة كرام الزوار في مضيف أهل العباء.',
                url: 'https://images.unsplash.com/photo-1542838132-92c53300491e?auto=format&fit=crop&w=800&q=80',
                date: '2026-03-01'
            },
            {
                id: 'img-2',
                title: 'استقبال وفود ضيوف المضيف المبارك',
                description: 'مراسيم استقبال وضيافة كرام الشخصيات والضيوف.',
                url: 'https://images.unsplash.com/photo-1511795409834-ef04bbd61622?auto=format&fit=crop&w=800&q=80',
                date: '2026-03-10'
            }
        ];

        // Application State
        let currentUser = null;
        let galleryImages = [];
        let tempBase64Image = '';
        let generatedResetCode = '';
        let userToResetPassword = null;

        window.onload = function() {
            document.getElementById('currentYear').textContent = new Date().getFullYear();
            initStorage();
            loadUserData();
            loadGalleryData();
            updateUINavigation();
            switchView('home');
        };

        function initStorage() {
            if (!localStorage.getItem(STORAGE_KEYS.ADMIN)) {
                localStorage.setItem(STORAGE_KEYS.ADMIN, JSON.stringify(ADMIN_CREDENTIALS));
            }
            if (!localStorage.getItem(STORAGE_KEYS.USERS)) {
                localStorage.setItem(STORAGE_KEYS.USERS, JSON.stringify(PREDEFINED_MEMBERS));
            } else {
                // Ensure predefined users exist and updated with permissions
                const currentUsers = JSON.parse(localStorage.getItem(STORAGE_KEYS.USERS));
                PREDEFINED_MEMBERS.forEach(pm => {
                    const existingIdx = currentUsers.findIndex(u => u.username === pm.username);
                    if (existingIdx === -1) {
                        currentUsers.push(pm);
                    } else {
                        // Keep predefined roles/permissions in sync
                        currentUsers[existingIdx].canExportExcel = pm.canExportExcel;
                        currentUsers[existingIdx].canPublish = pm.canPublish;
                    }
                });
                localStorage.setItem(STORAGE_KEYS.USERS, JSON.stringify(currentUsers));
            }
            if (!localStorage.getItem(STORAGE_KEYS.IMAGES)) {
                localStorage.setItem(STORAGE_KEYS.IMAGES, JSON.stringify(DEFAULT_IMAGES));
            }
        }

        function loadUserData() {
            const session = localStorage.getItem(STORAGE_KEYS.CURRENT_USER);
            if (session) {
                currentUser = JSON.parse(session);
            }
        }

        function loadGalleryData() {
            const stored = localStorage.getItem(STORAGE_KEYS.IMAGES);
            galleryImages = stored ? JSON.parse(stored) : [];
            renderGallery();
        }

        function saveGalleryData() {
            localStorage.setItem(STORAGE_KEYS.IMAGES, JSON.stringify(galleryImages));
            renderGallery();
        }

        function getAdminData() {
            return JSON.parse(localStorage.getItem(STORAGE_KEYS.ADMIN)) || ADMIN_CREDENTIALS;
        }

        function getAllUsersList() {
            const admin = getAdminData();
            const registeredUsers = JSON.parse(localStorage.getItem(STORAGE_KEYS.USERS)) || [];
            
            const list = [
                {
                    fullName: admin.fullName,
                    username: admin.username,
                    password: admin.password,
                    countryPhone: 'حساب أدمن النظام الرئيسي',
                    role: 'الأدمن الرئيسي'
                }
            ];

            registeredUsers.forEach(u => {
                list.push({
                    fullName: u.fullName,
                    username: u.username,
                    password: u.password,
                    countryPhone: (u.country || '') + ' ' + (u.phone || 'غير مسجل'),
                    role: u.role || 'زائر'
                });
            });

            return list;
        }

        function switchView(viewName) {
            const homeSec = document.getElementById('homeSection');
            const authSec = document.getElementById('authSection');
            const adminSec = document.getElementById('adminDashboardSection');

            homeSec.classList.add('hidden');
            authSec.classList.add('hidden');
            adminSec.classList.add('hidden');

            if (viewName === 'home') {
                homeSec.classList.remove('hidden');
            } else if (viewName === 'auth') {
                authSec.classList.remove('hidden');
                switchAuthMode('login');
            } else if (viewName === 'admin') {
                if (currentUser && (currentUser.isAdmin || currentUser.canPublish || currentUser.username === 'zuhair@1988')) {
                    adminSec.classList.remove('hidden');
                    renderAdminDashboard();
                } else {
                    showToast('error', 'غير مصرح لك بفتح لوحة التحكم');
                    homeSec.classList.remove('hidden');
                }
            }
        }

        function switchAuthMode(mode) {
            const loginForm = document.getElementById('loginForm');
            const registerForm = document.getElementById('registerForm');
            const forgotStep1 = document.getElementById('forgotStep1');
            const forgotStep2 = document.getElementById('forgotStep2');
            const forgotStep3 = document.getElementById('forgotStep3');
            const authHeader = document.getElementById('authTabsHeader');

            const tabLoginBtn = document.getElementById('tabLoginBtn');
            const tabRegisterBtn = document.getElementById('tabRegisterBtn');

            loginForm.classList.add('hidden');
            registerForm.classList.add('hidden');
            forgotStep1.classList.add('hidden');
            forgotStep2.classList.add('hidden');
            forgotStep3.classList.add('hidden');
            authHeader.classList.remove('hidden');

            if (mode === 'login') {
                loginForm.classList.remove('hidden');
                tabLoginBtn.className = "flex-1 pb-3 text-center text-sm sm:text-base font-semibold border-b-2 border-gold-500 text-gold-500 transition-all";
                tabRegisterBtn.className = "flex-1 pb-3 text-center text-sm sm:text-base font-semibold border-b-2 border-transparent text-gray-400 hover:text-gray-200 transition-all";
            } else if (mode === 'register') {
                registerForm.classList.remove('hidden');
                tabRegisterBtn.className = "flex-1 pb-3 text-center text-sm sm:text-base font-semibold border-b-2 border-gold-500 text-gold-500 transition-all";
                tabLoginBtn.className = "flex-1 pb-3 text-center text-sm sm:text-base font-semibold border-b-2 border-transparent text-gray-400 hover:text-gray-200 transition-all";
            } else if (mode === 'forgot') {
                authHeader.classList.add('hidden');
                forgotStep1.classList.remove('hidden');
            } else if (mode === 'forgot2') {
                authHeader.classList.add('hidden');
                forgotStep2.classList.remove('hidden');
            } else if (mode === 'forgot3') {
                authHeader.classList.add('hidden');
                forgotStep3.classList.remove('hidden');
            }
        }

        function updateUINavigation() {
            const navArea = document.getElementById('navUserArea');
            const galleryAuthorizedActions = document.getElementById('galleryAuthorizedActions');

            if (currentUser) {
                const canPublish = currentUser.isAdmin || currentUser.canPublish || currentUser.username === 'zuhair@1988';
                
                if (canPublish && galleryAuthorizedActions) {
                    galleryAuthorizedActions.classList.remove('hidden');
                } else if (galleryAuthorizedActions) {
                    galleryAuthorizedActions.classList.add('hidden');
                }

                navArea.innerHTML = `
                    <div class="flex items-center gap-2">
                        ${canPublish ? `
                            <button onclick="switchView('admin')" class="px-3 py-1.5 bg-gold-500/20 hover:bg-gold-500/30 text-gold-500 border border-gold-500/40 rounded-xl text-xs font-bold transition flex items-center gap-1.5">
                                <i class="fa-solid fa-gauge"></i> لوحة التحكم
                            </button>
                        ` : ''}
                        
                        <div class="text-right hidden sm:block px-1">
                            <span class="block text-xs text-gold-500 font-bold">${currentUser.fullName}</span>
                            <span class="block text-[10px] text-gray-400">${currentUser.isAdmin ? 'مدير المضيف (أدمن)' : (currentUser.role || 'عضو مسجل')}</span>
                        </div>

                        <!-- Edit Profile Button -->
                        <button onclick="openProfileModal()" title="تعديل البروفايل الشخصي" class="w-9 h-9 rounded-xl bg-emeraldCustom-900 border border-gold-500/30 text-gold-500 hover:bg-gold-500 hover:text-emeraldCustom-950 transition flex items-center justify-center text-sm">
                            <i class="fa-solid fa-user-gear"></i>
                        </button>

                        <!-- Change Password Button -->
                        <button onclick="openPasswordModal()" title="تغيير كلمة المرور" class="w-9 h-9 rounded-xl bg-emeraldCustom-900 border border-gold-500/30 text-gold-500 hover:bg-gold-500 hover:text-emeraldCustom-950 transition flex items-center justify-center text-sm">
                            <i class="fa-solid fa-key"></i>
                        </button>

                        <button onclick="handleLogout()" title="تسجيل الخروج" class="w-9 h-9 rounded-xl bg-red-950/40 border border-red-500/30 text-red-400 hover:bg-red-600 hover:text-white transition flex items-center justify-center text-sm">
                            <i class="fa-solid fa-right-from-bracket"></i>
                        </button>
                    </div>
                `;
            } else {
                if (galleryAuthorizedActions) galleryAuthorizedActions.classList.add('hidden');
                navArea.innerHTML = `
                    <button onclick="switchView('auth')" class="px-4 py-2 bg-gradient-to-r from-gold-600 to-gold-500 hover:from-gold-500 hover:to-gold-600 text-emeraldCustom-950 font-bold rounded-xl text-xs sm:text-sm shadow-md transition flex items-center gap-2">
                        <i class="fa-solid fa-user"></i> تسجيل الدخول
                    </button>
                `;
            }
        }

        // Authentication Handler
        function handleLogin(e) {
            e.preventDefault();
            const identifier = document.getElementById('loginIdentifier').value.trim();
            const password = document.getElementById('loginPassword').value.trim();

            const admin = getAdminData();

            // Hidden Admin Credentials Check (ahlalabaa | 36386184)
            if ((identifier === admin.username || identifier === 'ahlalabaa') && password === admin.password) {
                currentUser = {
                    username: admin.username,
                    fullName: admin.fullName,
                    isAdmin: true,
                    canExportExcel: true,
                    canPublish: true
                };
                localStorage.setItem(STORAGE_KEYS.CURRENT_USER, JSON.stringify(currentUser));
                updateUINavigation();
                showToast('success', `مرحباً بك الأدمن ${admin.fullName}`);
                document.getElementById('loginForm').reset();
                switchView('admin');
                return;
            }

            // Member and Registered Users Check
            const users = JSON.parse(localStorage.getItem(STORAGE_KEYS.USERS)) || [];
            const foundUser = users.find(u => (u.username === identifier || u.fullName === identifier || u.phone === identifier) && u.password === password);

            if (foundUser) {
                currentUser = {
                    username: foundUser.username,
                    fullName: foundUser.fullName,
                    phone: foundUser.phone || '',
                    role: foundUser.role || 'عضو المضيف',
                    isAdmin: false,
                    canExportExcel: (foundUser.username === 'zuhair@1988' || foundUser.canExportExcel),
                    canPublish: (foundUser.username === 'zuhair@1988' || foundUser.canPublish || foundUser.role === 'رئيس المضيف' || foundUser.role === 'نائب الرئيس')
                };
                localStorage.setItem(STORAGE_KEYS.CURRENT_USER, JSON.stringify(currentUser));
                updateUINavigation();
                showToast('success', `أهلاً وسهلاً بك ${foundUser.fullName}`);
                document.getElementById('loginForm').reset();
                switchView(currentUser.canPublish ? 'admin' : 'home');
            } else {
                showToast('error', 'اسم المستخدم أو كلمة المرور غير صحيحة!');
            }
        }

        function handleRegister(e) {
            e.preventDefault();
            const fullName = document.getElementById('regFullName').value.trim();
            const username = document.getElementById('regUsername').value.trim();
            const country = document.getElementById('regCountry').value;
            const phone = document.getElementById('regPhone').value.trim();
            const password = document.getElementById('regPassword').value.trim();

            const admin = getAdminData();
            if (username.toLowerCase() === admin.username.toLowerCase()) {
                showToast('error', 'اسم المستخدم هذا محجوز لمدير النظام المخفي!');
                return;
            }

            const users = JSON.parse(localStorage.getItem(STORAGE_KEYS.USERS)) || [];
            if (users.some(u => u.username === username)) {
                showToast('error', 'اسم المستخدم موجود مسبقاً.');
                return;
            }

            const newUser = { fullName, username, country, phone, password, role: 'زائر مسجل', isAdmin: false, canExportExcel: false, canPublish: false };
            users.push(newUser);
            localStorage.setItem(STORAGE_KEYS.USERS, JSON.stringify(users));

            // Auto Login
            currentUser = { username, fullName, phone, role: 'زائر مسجل', isAdmin: false, canExportExcel: false, canPublish: false };
            localStorage.setItem(STORAGE_KEYS.CURRENT_USER, JSON.stringify(currentUser));

            showToast('success', 'تم إنشاء الحساب بنجاح! أهلاً وسهلاً بك.');
            document.getElementById('registerForm').reset();
            updateUINavigation();
            switchView('home');
        }

        function handleLogout() {
            currentUser = null;
            localStorage.removeItem(STORAGE_KEYS.CURRENT_USER);
            updateUINavigation();
            showToast('info', 'تم تسجيل الخروج بنجاح.');
            switchView('home');
        }

        function handleSendResetCode(e) {
            e.preventDefault();
            const phone = document.getElementById('forgotPhone').value.trim();

            const admin = getAdminData();
            const users = JSON.parse(localStorage.getItem(STORAGE_KEYS.USERS)) || [];

            let isTargetAdmin = (phone === '36386184' || phone === '0736386184' || phone === admin.username);
            let matchedUser = users.find(u => u.phone === phone || u.username === phone);

            if (isTargetAdmin) {
                userToResetPassword = { type: 'admin' };
            } else if (matchedUser) {
                userToResetPassword = { type: 'user', username: matchedUser.username };
            } else {
                userToResetPassword = { type: 'admin' };
            }

            // Generate 4-digit OTP Code
            generatedResetCode = Math.floor(1000 + Math.random() * 9000).toString();

            // SMS Notification Box Format
            const smsText = `مضيف أهل العباء الرمز هو: <strong class="text-white bg-black/60 px-2 py-0.5 rounded text-base font-mono">${generatedResetCode}</strong>`;

            document.getElementById('smsContentBody').innerHTML = smsText;
            document.getElementById('smsNotificationModal').classList.remove('hidden');

            showToast('info', `تم إرسال رمز التحقق في SMS من ahlalabaa`);
            switchAuthMode('forgot2');
        }

        function handleVerifyResetCode(e) {
            e.preventDefault();
            const enteredOtp = document.getElementById('otpInput').value.trim();

            if (enteredOtp === generatedResetCode) {
                showToast('success', 'تم التحقق من الرمز بنجاح!');
                closeSmsModal();
                switchAuthMode('forgot3');
            } else {
                showToast('error', 'رمز التحقق غير صحيح!');
            }
        }

        function handleResetPasswordSubmit(e) {
            e.preventDefault();
            const newPass = document.getElementById('resetNewPass').value.trim();
            const confirmPass = document.getElementById('resetConfirmPass').value.trim();

            if (newPass !== confirmPass) {
                showToast('error', 'كلمات المرور غير متطابقة!');
                return;
            }

            if (userToResetPassword && userToResetPassword.type === 'admin') {
                const admin = getAdminData();
                admin.password = newPass;
                localStorage.setItem(STORAGE_KEYS.ADMIN, JSON.stringify(admin));
                showToast('success', 'تم تحديث كلمة مرور الأدمن بنجاح!');
            } else if (userToResetPassword && userToResetPassword.type === 'user') {
                const users = JSON.parse(localStorage.getItem(STORAGE_KEYS.USERS)) || [];
                const idx = users.findIndex(u => u.username === userToResetPassword.username);
                if (idx !== -1) {
                    users[idx].password = newPass;
                    localStorage.setItem(STORAGE_KEYS.USERS, JSON.stringify(users));
                }
                showToast('success', 'تم تعديل كلمة المرور بنجاح!');
            }

            switchAuthMode('login');
        }

        function closeSmsModal() {
            document.getElementById('smsNotificationModal').classList.add('hidden');
        }

        // Profile Update Handler
        function openProfileModal() {
            if (!currentUser) return;
            document.getElementById('profFullName').value = currentUser.fullName || '';
            document.getElementById('profUsername').value = currentUser.username || '';
            document.getElementById('profPhone').value = currentUser.phone || '';
            document.getElementById('profileModal').classList.remove('hidden');
        }

        function handleSaveProfile(e) {
            e.preventDefault();
            if (!currentUser) return;

            const newFullName = document.getElementById('profFullName').value.trim();
            const newPhone = document.getElementById('profPhone').value.trim();

            currentUser.fullName = newFullName;
            currentUser.phone = newPhone;
            localStorage.setItem(STORAGE_KEYS.CURRENT_USER, JSON.stringify(currentUser));

            if (currentUser.isAdmin) {
                const admin = getAdminData();
                admin.fullName = newFullName;
                localStorage.setItem(STORAGE_KEYS.ADMIN, JSON.stringify(admin));
            } else {
                const users = JSON.parse(localStorage.getItem(STORAGE_KEYS.USERS)) || [];
                const idx = users.findIndex(u => u.username === currentUser.username);
                if (idx !== -1) {
                    users[idx].fullName = newFullName;
                    users[idx].phone = newPhone;
                    localStorage.setItem(STORAGE_KEYS.USERS, JSON.stringify(users));
                }
            }

            updateUINavigation();
            showToast('success', 'تم تحديث ملفك الشخصي بنجاح!');
            closeModal('profileModal');
        }

        function openPasswordModal() {
            if (!currentUser) {
                showToast('error', 'يرجى تسجيل الدخول أولاً.');
                return;
            }
            document.getElementById('changePasswordForm').reset();
            document.getElementById('passwordModal').classList.remove('hidden');
        }

        function handleChangePasswordSubmit(e) {
            e.preventDefault();
            if (!currentUser) return;

            const oldPass = document.getElementById('oldPasswordInput').value;
            const newPass = document.getElementById('newPasswordInput').value;
            const confirmPass = document.getElementById('confirmNewPasswordInput').value;

            if (newPass !== confirmPass) {
                showToast('error', 'كلمة المرور الجديدة وتأكيدها غير متطابقين!');
                return;
            }

            if (currentUser.isAdmin) {
                const admin = getAdminData();
                if (oldPass !== admin.password) {
                    showToast('error', 'كلمة المرور القديمة غير صحيحة! يتطلب النظام كلمة المرور القديمة لتنفيذ التغيير.');
                    return;
                }

                admin.password = newPass;
                localStorage.setItem(STORAGE_KEYS.ADMIN, JSON.stringify(admin));
                showToast('success', 'تم تحديث كلمة مرور الأدمن بنجاح!');
            } else {
                const users = JSON.parse(localStorage.getItem(STORAGE_KEYS.USERS)) || [];
                const userIdx = users.findIndex(u => u.username === currentUser.username);

                if (userIdx !== -1) {
                    if (users[userIdx].password !== oldPass) {
                        showToast('error', 'كلمة المرور القديمة غير صحيحة!');
                        return;
                    }
                    users[userIdx].password = newPass;
                    localStorage.setItem(STORAGE_KEYS.USERS, JSON.stringify(users));
                    showToast('success', 'تم تحديث كلمة المرور بنجاح!');
                }
            }

            closeModal('passwordModal');
        }

        function exportAccountsToExcel() {
            if (!currentUser || (!currentUser.isAdmin && currentUser.username !== 'zuhair@1988' && !currentUser.canExportExcel)) {
                showToast('error', 'عذراً! ميزة تصدير قائمة الحسابات والكلمات السرية مقتصرة فقط على الأدمن الرئيسي وحساب اللجنة الإعلامية (zuhair@1988).');
                return;
            }

            const accountsList = getAllUsersList();

            // Transform Data for SheetJS
            const excelData = accountsList.map((acc, index) => ({
                "ت": index + 1,
                "الاسم الكامل / الصفة": acc.fullName,
                "اسم المستخدم (Username)": acc.username,
                "كلمة المرور (Password)": acc.password,
                "الدولة / رقم الهاتف": acc.countryPhone,
                "نوع الحساب": acc.role
            }));

            // Create Worksheet
            const worksheet = XLSX.utils.json_to_sheet(excelData);
            
            // Set Right-To-Left direction for Excel sheet
            if(!worksheet['!views']) worksheet['!views'] = [];
            worksheet['!views'].push({RTL: true});

            const workbook = XLSX.utils.book_new();
            XLSX.utils.book_append_sheet(workbook, worksheet, "قائمة الحسابات");

            // Download File
            const fileName = `حسابات_مضيف_أهل_العباء_${new Date().toISOString().split('T')[0]}.xlsx`;
            XLSX.writeFile(workbook, fileName);

            showToast('success', 'تم تنزيل ملف الإكسل (Excel) بحسابات وكلمات مرور المضيف بنجاح!');
        }

        function renderGallery() {
            const grid = document.getElementById('galleryGrid');
            grid.innerHTML = '';

            if (galleryImages.length === 0) {
                grid.innerHTML = `
                    <div class="col-span-full text-center py-12 glass-panel rounded-2xl">
                        <i class="fa-regular fa-image text-4xl text-gold-500/40 mb-3 block"></i>
                        <p class="text-gray-400 text-sm">لا توجد صور معروضة حالياً.</p>
                    </div>
                `;
                return;
            }

            galleryImages.forEach(img => {
                const card = document.createElement('div');
                card.className = "glass-panel rounded-2xl overflow-hidden hover:border-gold-500/60 transition duration-300 flex flex-col group";
                card.innerHTML = `
                    <div class="relative h-56 overflow-hidden bg-black/50">
                        <img src="${img.url}" alt="${img.title}" class="w-full h-full object-cover group-hover:scale-105 transition duration-500" onerror="this.src='https://placehold.co/600x400/0d231c/d4af37?text=مضيف+أهل+العباء'">
                        <div class="absolute inset-0 bg-gradient-to-t from-black/80 via-transparent to-transparent opacity-70"></div>
                        <span class="absolute bottom-2.5 right-3 text-[11px] text-gold-300 bg-emeraldCustom-950/90 px-2.5 py-1 rounded-md border border-gold-500/30">
                            ${img.date || 'تاريخ الخدمة'}
                        </span>
                    </div>
                    <div class="p-5 flex-1 flex flex-col justify-between">
                        <div>
                            <h4 class="font-bold font-amiri text-lg text-gold-500 mb-1.5">${img.title}</h4>
                            <p class="text-xs text-gray-300 leading-relaxed">${img.description || 'لا يوجد وصف متاح.'}</p>
                        </div>
                    </div>
                `;
                grid.appendChild(card);
            });
        }

        function renderAdminDashboard() {
            const adminGrid = document.getElementById('adminGalleryGrid');
            const countElem = document.getElementById('adminImageCount');
            const roleBadge = document.getElementById('dashboardRoleBadge');
            const titleElem = document.getElementById('dashboardTitle');
            const excelExportBtn = document.getElementById('excelExportBtn');
            const excelAccountsCard = document.getElementById('excelAccountsCard');
            const accountsTableBody = document.getElementById('accountsTableBody');

            countElem.textContent = galleryImages.length;

            const isAuthorizedForExcel = currentUser && (currentUser.isAdmin || currentUser.username === 'zuhair@1988' || currentUser.canExportExcel);

            if (currentUser.isAdmin) {
                roleBadge.textContent = "حساب الأدمن الرئيسي";
                titleElem.textContent = "لوحة التحكم الرئيسية لمضيف أهل العباء";
            } else if (currentUser.username === 'zuhair@1988') {
                roleBadge.textContent = "حساب اللجنة الإعلامية (زهير)";
                titleElem.textContent = "لوحة التحكم الإعلامية والنشر";
            } else {
                roleBadge.textContent = "لوحة النشر والإدارة";
                titleElem.textContent = "إدارة منشورات المضيف";
            }

            // Excel Button & Preview Table Permissions Check
            if (isAuthorizedForExcel) {
                excelExportBtn.classList.remove('hidden');
                excelAccountsCard.classList.remove('hidden');

                // Populate Excel Table Preview
                const accounts = getAllUsersList();
                accountsTableBody.innerHTML = '';
                accounts.forEach((acc, i) => {
                    const tr = document.createElement('tr');
                    tr.className = "hover:bg-emeraldCustom-900/50 transition";
                    tr.innerHTML = `
                        <td class="p-3 font-mono text-gold-500">${i + 1}</td>
                        <td class="p-3 font-semibold text-white">${acc.fullName}</td>
                        <td class="p-3 font-mono text-gold-300">${acc.username}</td>
                        <td class="p-3 font-mono text-amber-300 bg-amber-950/20 px-2 py-1 rounded border border-amber-500/20">${acc.password}</td>
                        <td class="p-3 text-gray-400">${acc.countryPhone}</td>
                        <td class="p-3"><span class="px-2 py-0.5 rounded bg-gold-500/20 text-gold-400 font-bold text-[10px]">${acc.role}</span></td>
                    `;
                    accountsTableBody.appendChild(tr);
                });
            } else {
                excelExportBtn.classList.add('hidden');
                excelAccountsCard.classList.add('hidden');
            }

            adminGrid.innerHTML = '';

            if (galleryImages.length === 0) {
                adminGrid.innerHTML = `
                    <div class="col-span-full text-center py-8 text-gray-400 text-sm">
                        لا توجد صور حالياً. اضغط على "رفع / إضافة صورة" للبدء بالنشر.
                    </div>
                `;
                return;
            }

            galleryImages.forEach(img => {
                const card = document.createElement('div');
                card.className = "glass-panel rounded-xl overflow-hidden p-3 flex flex-col justify-between gap-3 border border-gold-500/20";
                card.innerHTML = `
                    <div class="flex gap-3">
                        <img src="${img.url}" alt="${img.title}" class="w-24 h-20 object-cover rounded-lg border border-gold-500/30" onerror="this.src='https://placehold.co/150x150/0d231c/d4af37?text=صورة'">
                        <div class="flex-1 min-w-0">
                            <h5 class="font-bold text-sm text-gold-500 truncate">${img.title}</h5>
                            <p class="text-xs text-gray-400 line-clamp-2 mt-1">${img.description || 'بدون وصف'}</p>
                        </div>
                    </div>
                    <div class="flex justify-end gap-2 border-t border-gold-500/10 pt-2.5">
                        <button onclick="openEditImageModal('${img.id}')" class="px-3 py-1 bg-emeraldCustom-900 hover:bg-emeraldCustom-800 text-gold-500 border border-gold-500/30 rounded-lg text-xs font-semibold transition flex items-center gap-1">
                            <i class="fa-solid fa-pen"></i> تعديل
                        </button>
                        <button onclick="handleDeleteImage('${img.id}')" class="px-3 py-1 bg-red-950/50 hover:bg-red-900 text-red-400 border border-red-500/30 rounded-lg text-xs font-semibold transition flex items-center gap-1">
                            <i class="fa-solid fa-trash"></i> حذف
                        </button>
                    </div>
                `;
                adminGrid.appendChild(card);
            });
        }

        function openUploadModal() {
            document.getElementById('imageForm').reset();
            document.getElementById('editImageId').value = '';
            document.getElementById('imageModalTitle').textContent = 'رفع / نشر صورة جديدة للمضيف';
            document.getElementById('imagePreviewContainer').classList.add('hidden');
            tempBase64Image = '';
            document.getElementById('imageModal').classList.remove('hidden');
        }

        function openEditImageModal(id) {
            const img = galleryImages.find(i => i.id === id);
            if (!img) return;

            document.getElementById('editImageId').value = img.id;
            document.getElementById('imgTitle').value = img.title;
            document.getElementById('imgDescription').value = img.description || '';
            document.getElementById('imgUrlInput').value = img.url.startsWith('data:') ? '' : img.url;

            const previewImg = document.getElementById('imagePreview');
            previewImg.src = img.url;
            document.getElementById('imagePreviewContainer').classList.remove('hidden');
            
            tempBase64Image = img.url.startsWith('data:') ? img.url : '';
            document.getElementById('imageModalTitle').textContent = 'تعديل بيانات الصورة المنشورة';
            document.getElementById('imageModal').classList.remove('hidden');
        }

        function previewSelectedImage(event) {
            const file = event.target.files[0];
            if (file) {
                const reader = new FileReader();
                reader.onload = function(e) {
                    tempBase64Image = e.target.result;
                    document.getElementById('imagePreview').src = tempBase64Image;
                    document.getElementById('imagePreviewContainer').classList.remove('hidden');
                };
                reader.readAsDataURL(file);
            }
        }

        function previewUrlImage(url) {
            if (url.trim()) {
                tempBase64Image = '';
                document.getElementById('imagePreview').src = url;
                document.getElementById('imagePreviewContainer').classList.remove('hidden');
            }
        }

        function handleSaveImage(e) {
            e.preventDefault();
            const id = document.getElementById('editImageId').value;
            const title = document.getElementById('imgTitle').value.trim();
            const description = document.getElementById('imgDescription').value.trim();
            const urlInput = document.getElementById('imgUrlInput').value.trim();

            let imageUrl = tempBase64Image || urlInput;

            if (!imageUrl) {
                showToast('error', 'يرجى اختيار ملف صورة أو إدخال رابط صورة صحيح!');
                return;
            }

            if (id) {
                const index = galleryImages.findIndex(i => i.id === id);
                if (index !== -1) {
                    galleryImages[index].title = title;
                    galleryImages[index].description = description;
                    galleryImages[index].url = imageUrl;
                    showToast('success', 'تم تعديل الصورة بنجاح!');
                }
            } else {
                const newImg = {
                    id: 'img-' + Date.now(),
                    title,
                    description,
                    url: imageUrl,
                    date: new Date().toISOString().split('T')[0]
                };
                galleryImages.unshift(newImg);
                showToast('success', 'تم نشر الصورة بنجاح!');
            }

            saveGalleryData();
            closeModal('imageModal');
            if (currentUser && (currentUser.isAdmin || currentUser.canPublish || currentUser.username === 'zuhair@1988')) {
                renderAdminDashboard();
            }
        }

        function handleDeleteImage(id) {
            if (confirm('هل أنت تأكد من رغبتك في حذف هذه الصورة من المعرض؟')) {
                galleryImages = galleryImages.filter(i => i.id !== id);
                saveGalleryData();
                showToast('info', 'تم حذف الصورة.');
                renderAdminDashboard();
            }
        }

        function closeModal(modalId) {
            document.getElementById(modalId).classList.add('hidden');
        }

        function showToast(type, message) {
            const container = document.getElementById('toastContainer');
            const toast = document.createElement('div');

            let bgColor = 'bg-emeraldCustom-900 border-gold-500 text-gold-500';
            let icon = 'fa-circle-check';

            if (type === 'error') {
                bgColor = 'bg-red-950 border-red-500 text-red-200';
                icon = 'fa-circle-xmark';
            } else if (type === 'info') {
                bgColor = 'bg-blue-950 border-blue-500 text-blue-200';
                icon = 'fa-circle-info';
            }

            toast.className = `flex items-center gap-3 p-4 rounded-xl border shadow-xl backdrop-blur-md transition-all duration-300 transform translate-y-2 pointer-events-auto ${bgColor}`;
            toast.innerHTML = `
                <i class="fa-solid ${icon} text-lg"></i>
                <span class="text-xs sm:text-sm font-semibold">${message}</span>
            `;

            container.appendChild(toast);

            setTimeout(() => {
                toast.classList.add('opacity-0', '-translate-y-2');
                setTimeout(() => toast.remove(), 300);
            }, 3800);
        }
    </script>
</body>
</html>
