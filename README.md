<!DOCTYPE html>
<html lang="km">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>គេហទំព័របក្ស</title>
    <style>
        /* CSS Reset */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Khmer OS', 'Arial', sans-serif;
        }

        body {
            background-color: #f5f5f5;
            color: #333;
        }

        /* Header Styles */
        header {
            background-color: #1a5276;
            color: white;
            padding: 1rem 0;
            position: relative;
            box-shadow: 0 2px 5px rgba(0,0,0,0.2);
        }

        .header-container {
            display: flex;
            justify-content: space-between; /* Changed to space-between to push toggle right */
            align-items: center;
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        .logo-container { /* This container might not be strictly necessary anymore but keep for structure */
            display: flex;
            align-items: center;
        }

        .logo {
            display: flex;
            align-items: center;
        }

        .logo img {
            height: 60px;
            margin-right: 15px;
        }

        .logo-text h1 {
            font-size: 24px;
            margin-bottom: 5px;
        }

        .logo-text p {
            font-size: 14px;
        }

        /* Date Time Display - Styles remain, but position changes */
        .datetime-display {
            text-align: left;
            padding: 5px 10px;
            background-color: rgba(255, 255, 255, 0.1);
            border-radius: 5px;
            min-width: 220px;
            color: white; /* Ensure color is white for nav bar */
        }

        .datetime-display .date {
            font-size: 16px;
            font-weight: bold;
            margin-bottom: 3px;
        }

        .datetime-display .time {
            font-size: 14px;
        }
        /* *** ADDED STYLE FOR MINUTES AND SECONDS *** */
        .time-minutes-seconds {
            color: #f6fa05; /* Light blue color for better visibility */
        }


        /* Navigation Styles */
        nav {
            background-color: #2874a6;
            position: relative;
        }

        .nav-container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .menu {
            list-style: none;
            display: flex;
            position: relative; /* Needed for absolute positioning of mobile menu */
            flex-grow: 1; /* Allow menu to take available space if needed */
        }

        .menu li {
            position: relative;
        }

        .menu > li > a {
            display: block;
            color: white;
            text-decoration: none;
            padding: 15px 20px;
            transition: all 0.3s ease;
        }

        .menu > li > a:hover {
            background-color: #1a5276;
        }

        .submenu {
            position: absolute;
            top: 100%;
            left: 0;
            background-color: white;
            width: 220px;
            list-style: none;
            box-shadow: 0 2px 5px rgba(0,0,0,0.2);
            opacity: 0;
            visibility: hidden;
            transition: all 0.3s ease;
            z-index: 100;
        }

        .menu li:hover .submenu {
            opacity: 1;
            visibility: visible;
        }

        .submenu a {
            display: block;
            padding: 10px 15px;
            color: #333;
            text-decoration: none;
            border-bottom: 1px solid #eee;
            transition: all 0.2s ease;
        }

        .submenu a:hover {
            background-color: #f0f0f0;
            color: #1a5276;
            padding-left: 20px;
        }

        /* Container for right-aligned items in nav */
        .nav-right-items {
            display: flex;
            align-items: center;
            gap: 20px; /* Adds space between date/time and counter */
        }

        /* Visitor Counter */
        .visitor-counter { /* Style for the container (used on desktop) */
            display: flex;
            align-items: center;
            color: white;
            font-size: 14px;
        }

        .visitor-counter i, /* Target icon in both desktop and mobile */
        .mobile-visitor-counter i {
            margin-right: 8px;
            font-size: 16px;
        }

        /* Moving Text and Images */
        .marquee-container {
            background-color: #d4e6f1;
            padding: 10px 0;
            overflow: hidden; /* Keep this */
            border-bottom: 1px solid #aed6f1;
        }

        .marquee-content {
            display: flex; /* Keep this */
            align-items: center; /* Keep this */
            white-space: nowrap; /* Keep this */
            /* Default animation for desktop */
            animation: marquee 15s linear infinite;
        }

        .marquee-content img.marquee-logo {
            height: 30px;
            margin-right: 20px;
            border-radius: 3px;
            flex-shrink: 0;
        }

        .marquee-text {
            font-size: 14px;
            color: #1a5276;
        }

        /* Default Keyframes for Desktop */
        @keyframes marquee {
            0% { transform: translateX(100%); }
            100% { transform: translateX(-100%); } /* Standard scroll */
        }


        /* Mobile Menu Toggle */
        .menu-toggle {
            display: none;
            cursor: pointer;
            font-size: 24px;
            color: white;
             position: absolute;
             top: 50%;
             right: 20px;
             transform: translateY(-50%);
             z-index: 101; /* Ensure toggle is above menu */
        }

        /* Main Content Styles */
        .main-content {
            max-width: 1200px;
            margin: 20px auto;
            padding: 0 20px;
        }

        .report-section {
            background-color: white;
            border-radius: 5px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
            padding: 20px;
            margin-bottom: 20px;
        }

        .report-section h2 {
            color: #1a5276;
            border-bottom: 2px solid #d4e6f1;
            padding-bottom: 10px;
            margin-bottom: 15px;
        }

        .report-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 20px;
        }

        .report-card {
            background-color: #f9f9f9;
            border-radius: 5px;
            padding: 15px;
            box-shadow: 0 1px 3px rgba(0,0,0,0.1);
            transition: transform 0.3s ease;
        }

        .report-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
        }

        .report-card h3 {
            color: #2874a6;
            margin-bottom: 10px;
        }

        .report-card p {
            margin-bottom: 15px;
            color: #555;
        }

        .report-card a {
            display: inline-block;
            background-color: #1a5276;
            color: white;
            padding: 8px 15px;
            border-radius: 4px;
            text-decoration: none;
            transition: background-color 0.3s ease;
        }

        .report-card a:hover {
            background-color: #154360;
        }

        .statistics {
            display: flex;
            flex-wrap: wrap;
            gap: 15px;
            margin-bottom: 20px;
        }

        .stat-item {
            flex: 1;
            min-width: 200px;
            background-color: white;
            padding: 15px;
            border-radius: 5px;
            box-shadow: 0 1px 3px rgba(0,0,0,0.1);
            text-align: center;
        }

        .stat-item h3 {
            color: #2874a6;
            margin-bottom: 10px;
        }

        .stat-item .number {
            font-size: 24px;
            font-weight: bold;
            color: #1a5276;
        }

        /* Style for Mobile Visitor Counter Item (within the dropdown) */
        .mobile-visitor-counter {
            display: none; /* Hide by default (on desktop) */
            color: white;
            padding: 15px 20px; /* Match other menu items */
            font-size: 14px;
            align-items: center; /* Align icon and text */
            gap: 8px; /* Space between icon and text */
            cursor: default; /* Indicate it's not clickable like a link */
        }
        /* No hover effect needed, or match menu item */
        .mobile-visitor-counter:hover {
             background-color: #2874a6; /* Keep same background on hover */
        }


        /* Responsive Styles */
        @media (max-width: 768px) {
            .header-container {
                flex-direction: row;
                justify-content: space-between;
                text-align: left;
                position: relative;
            }

            .logo {
                justify-content: flex-start;
                margin-bottom: 0;
            }

            .menu-toggle {
                display: block;
            }

            .nav-container {
                position: relative; /* Keep relative positioning */
            }

            .menu {
                flex-direction: column;
                display: none; /* Hidden until toggled */
                width: 100%;
                position: absolute; /* Position below the nav bar */
                top: 100%; /* Start right below the nav bar */
                left: 0;
                background-color: #2874a6;
                z-index: 99; /* Below toggle but above content */
                box-shadow: 0 4px 6px rgba(0,0,0,0.1);
                 padding-bottom: 5px; /* Optional: space at the bottom */
            }

            .menu.active {
                display: flex; /* Show the menu when active class is added */
            }

            .submenu {
                position: static; /* Submenu behaves normally within column */
                width: 100%;
                opacity: 1;
                visibility: visible;
                display: none; /* Still hidden until parent is hovered */
                box-shadow: none;
                background-color: #1a5276; /* Darker background for submenu */
            }
            .submenu a {
                color: white;
                padding-left: 30px; /* Indent submenu items */
            }
             .submenu a:hover {
                background-color: #154360;
                color: #fff;
                padding-left: 35px; /* Indent further on hover */
            }

            .menu li:hover .submenu {
                display: block; /* Show submenu on hover */
            }

             /* Hide the original right-aligned group (date/time, desktop counter) */
             .nav-right-items {
                display: none;
             }

             /* Show the mobile counter LI only WHEN the menu is active */
             .menu.active .mobile-visitor-counter {
                 display: flex; /* Display it as a flex item */
             }

            /* Explicitly hide the desktop counter div on mobile */
            .desktop-counter {
                display: none !important; /* Use !important to be sure */
            }

            .report-grid {
                grid-template-columns: 1fr; /* Stack report cards */
            }

            .statistics {
                flex-direction: column; /* Stack stat items */
            }

            /* --- START: Mobile Marquee Adjustments --- */
            .marquee-content {
                /* Apply a mobile-specific animation name */
                animation-name: marquee-mobile;
                /* Optional: Adjust duration for potentially longer travel distance if needed */
                /* animation-duration: 20s; */ /* Uncomment and adjust if you want it slower */
            }

            /* Define the keyframes specifically for mobile */
            @keyframes marquee-mobile {
                0% {
                    transform: translateX(100%); /* Start off-screen right */
                }
                100% {
                    /* Move further left - adjust value as needed */
                    transform: translateX(-180%);
                }
            }
            /* --- END: Mobile Marquee Adjustments --- */

        } /* Closing brace of the @media query */
    </style>
    <!-- Font Awesome for visitor icon -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
</head>
<body>
    <header>
        <div class="header-container">
            <!-- Logo remains here -->
            <div class="logo">
                <img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjBjpfSAupXhYfjPw1B2-K-Dw-oZSh6XMuipoY0cU9yP83ktiegUrg6Cz_F4puViXHwUiw9-q6GXORhA2AM7boVk9sZGfWfX2azautOIqiXliu7a5_gYWnm7evegUzWJvkbzqUCfKFlHwWvGQ4UBACnVFmmLj60Cr-KTUYzMvbyTpOkZwUuogPIHNPoe0od/s320/photo_2024-10-08_12-24-15-removebg-preview%20%281%29.png" alt="ឡូហ្គោបក្ស" id="logo-img">
                <div class="logo-text">
                    <h1>គេហទំព័ររដ្ឋបាលឃុំទួលពង្រ</h1>
                    <p>ស្ថាប័នរដ្ឋបាលថ្នាក់ក្រោមជាតិ</p>
                </div>
            </div>
            <!-- Menu Toggle Button -->
            <div class="menu-toggle" id="menu-toggle">☰</div>
        </div>

        <nav>
            <div class="nav-container">
                <!-- Main Menu -->
                <ul class="menu" id="main-menu">
                    <li><a href="#">ទំព័រដើម</a></li>
                    <li>
                        <a href="#">បញ្ជីសមាជិក</a>
                        <ul class="submenu">
                            <li><a href="https://script.google.com/macros/s/AKfycbx02Q4w_TUgUZ6fR6Di05FmwdPoTq0t0Fd7Fl3T9WUrB0T42pRkiSo-_WXFbU716kdQ/exec">បញ្ជីឈ្មោះតាមគ្រួសារ</a></li>
                            <li><a href="https://script.google.com/macros/s/AKfycbyAjHXq9Zvffi8i1yBstJBS442x-oxxj8KZrOT5LUuAJiiyKVFZ-tfn5lhBshTTqFRqHw/exec">សមាជិកបក្សក្នុងឃុំទួលពង្រ</a></li>
                            <li><a href="#">សមាជិកយុវជនបក្សឃុំ</a></li>
                        </ul>
                    </li>
                    <li><a href="https://script.google.com/macros/s/AKfycbyS2gwxXs36X3kI7TmhQAisTkgd-4L1MwppIO0Vas0prVYwTvwcpndmme2ZSsONKtWoQA/exec">សមាគមមនុស្សចាស់</a></li>
                    <li><a href="#">បញ្ជូលទិន្នន័យសមាជិកបក្ស</a></li>
                    <li><a href="https://t.me/CTPBMC">ព័ត៌មានថ្មី</a></li>

                    <!-- Visitor Counter for Mobile View -->
                    <li class="mobile-visitor-counter">
                         <i class="fas fa-users"></i>
                         <span class="visitor-count-display">កំពុងគណនា...</span>
                    </li>
                </ul>

                <!-- Group for Date/Time and Visitor Counter (Desktop) -->
                <div class="nav-right-items">
                    <div class="datetime-display">
                        <div class="date" id="current-date">ថ្ងៃ... ទី... ខែ... ឆ្នាំ...</div>
                        <div class="time" id="current-time">ម៉ោង...</div>
                    </div>
                    <div class="visitor-counter desktop-counter">
                        <i class="fas fa-users"></i>
                        <span class="visitor-count-display">កំពុងគណនា...</span>
                    </div>
                </div>
            </div>
        </nav>
    </header>

    <div class="marquee-container">
        <div class="marquee-content">
            <img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjBjpfSAupXhYfjPw1B2-K-Dw-oZSh6XMuipoY0cU9yP83ktiegUrg6Cz_F4puViXHwUiw9-q6GXORhA2AM7boVk9sZGfWfX2azautOIqiXliu7a5_gYWnm7evegUzWJvkbzqUCfKFlHwWvGQ4UBACnVFmmLj60Cr-KTUYzMvbyTpOkZwUuogPIHNPoe0od/s320/photo_2024-10-08_12-24-15-removebg-preview%20%281%29.png" alt="រដ្ឋបាលឃុំទួលពង្រ" class="marquee-logo">
            <span class="marquee-text">
                <span style="color: red;">រដ្ឋបាលឃុំទួលពង្រ</span>
                <span style="color:#2b00fe;">សូមជំរាបថា រាល់ទិន្នន័យទាំងអស់ដែលមាននៅក្នុងគេហទំព័រផ្លូវការរបស់</span>
                <span style="color:red;">រដ្ឋបាលឃុំទួលពង្រ</span>
                <span style="color:#2b00fe;">គឺជាទិន្នន័យផ្លូវការចុងក្រោយក្នុងឆ្នាំ២០២៥ ។ សូមទំនាក់ទំនង</span>
                <span style="color:red;">(Facebook Page: រដ្ឋបាលឃុំទួលពង្រ ឃុំទួលពង្រ ស្រុកម៉ាឡៃ ខេត្តបន្ទាយមានជ័យ)</span>
            </span>
        </div>
    </div>

    <!-- Main Content Section -->
    <div class="main-content">
        <!-- Statistics Section -->
        <div class="report-section">
            <h2>ស្ថិតិប្រជាលរដ្ឋក្នុងឃុំទួលពង្រ</h2>
            <div class="statistics">
                <div class="stat-item">
                    <h3>ចំនួនគ្រួសារសរុប</h3>
                    <div class="number" id="total-families">0</div>
                    <p>គ្រួសារ</p>
                </div>
                <div class="stat-item">
                    <h3>ប្រជាពលរដ្ឋសរុប</h3>
                    <div class="number" id="total-members">0</div>
                    <p>នាក់</p>
                </div>
                <div class="stat-item">
                    <h3>ប្រជាពលរដ្ឋសរុបស្រី</h3>
                    <div class="number" id="male-members">0</div>
                    <p>នាក់</p>
                </div>
                <div class="stat-item">
                    <h3>ចំនួនខ្នងផ្ទះ</h3>
                    <div class="number" id="female-members">0</div>
                    <p>នាក់</p>
                </div>
                <div class="stat-item">
                    <h3>ប្រជាពលរដ្ឋអាយុ១៨ឆ្នាំឡើង</h3>
                    <div class="number" id="youth-members">0</div>
                    <p>នាក់</p>
                </div>
                <div class="stat-item">
                    <h3>ប្រជាពលរដ្ឋមានឈ្មោះក្នុងបញ្ជីបោះឆ្នោត</h3>
                    <div class="number" id="total-party-members">0</div>
                    <p>នាក់</p>
                </div>
                <div class="stat-item">
                    <h3>សមាជិកក្នុងប្រព័ន្ធ</h3>
                    <div class="number" id="young-members">0</div>
                    <p>នាក់</p>
                </div>
            </div>
        </div>

        <!-- Reports Section -->
        <div class="report-section">
            <h2>របាយការណ៍ប្រជាពលរដ្ឋ</h2>
            <div class="report-grid">
                <div class="report-card">
                    <h3>បញ្ជីឈ្មោះតាមគ្រួសារ</h3>
                    <a href="https://script.google.com/macros/s/AKfycbx02Q4w_TUgUZ6fR6Di05FmwdPoTq0t0Fd7Fl3T9WUrB0T42pRkiSo-_WXFbU716kdQ/exec">មើលរបាយការណ៍</a>
                </div>
                <div class="report-card">
                    <h3>សមាជិកគណបក្សក្នុងឃុំទួលពង្រ ឆ្នាំ២០២៥</h3>
                    <a href="https://script.google.com/macros/s/AKfycbyAjHXq9Zvffi8i1yBstJBS442x-oxxj8KZrOT5LUuAJiiyKVFZ-tfn5lhBshTTqFRqHw/exec">មើលរបាយការណ៍</a>
                </div>
                <div class="report-card">
                    <h3>សមាជិកយុវជនបក្សឃុំ</h3>
                    <a href="#">មើលរបាយការណ៍</a>
                </div>
                <div class="report-card">
                    <h3>សមាគមមនុស្សចាស់ ២០២៤-២០២៥</h3>
                    <a href="https://script.google.com/macros/s/AKfycbyS2gwxXs36X3kI7TmhQAisTkgd-4L1MwppIO0Vas0prVYwTvwcpndmme2ZSsONKtWoQA/exec">មើលរបាយការណ៍</a>
                </div>
            </div>
        </div>
    </div>

    <!-- JavaScript Section -->
    <script>
        // Mobile Menu Toggle
        document.getElementById('menu-toggle').addEventListener('click', function() {
            const menu = document.getElementById('main-menu');
            menu.classList.toggle('active');
        });

        // Logo animation (Non-Greeting part)
        const logoImgElement = document.getElementById('logo-img'); // Renamed variable to avoid conflict
        if (logoImgElement) {
            logoImgElement.addEventListener('mouseover', function() {
                this.style.transform = 'scale(1.1)';
                this.style.transition = 'transform 0.3s ease';
            });
            logoImgElement.addEventListener('mouseout', function() {
                this.style.transform = 'scale(1)';
            });
        } else {
            console.error("Logo image element not found.");
        }


        // Marquee animation element check
        const marqueeContent = document.querySelector('.marquee-content');
        if (!marqueeContent) {
            console.error("Marquee content element not found.");
        }


        // --- START: MODIFIED VISITOR COUNTER FUNCTION ---
        function updateVisitorCounter() {
            const counterWebAppUrl = "https://script.google.com/macros/s/AKfycbxC7uFl2X96AbTYYCTPmO0x1T4it6-Jj_TWBqBqj9Vbvjp1WqPaYHM1lSFfMZ0JuVNK/exec";
            const countElements = document.querySelectorAll('.visitor-count-display');
            if (countElements.length === 0) {
                console.error("Element with class 'visitor-count-display' not found.");
                return;
            }
            countElements.forEach(el => el.textContent = 'កំពុង​ផ្ទុក...');
            const sessionKey = 'sessionVisitedCounter';
            let apiUrl;
            if (!sessionStorage.getItem(sessionKey)) {
                sessionStorage.setItem(sessionKey, 'true');
                apiUrl = counterWebAppUrl + '?action=increment';
                console.log("First visit this session. Incrementing count.");
            } else {
                apiUrl = counterWebAppUrl + '?action=getCount';
                console.log("Subsequent visit this session. Getting count only.");
            }
            fetch(apiUrl)
                .then(response => {
                    if (!response.ok) throw new Error(`Network response was not ok: ${response.statusText}`);
                    return response.json();
                })
                .then(data => {
                    if (data.error) {
                        console.error("Error from Counter Script:", data.error);
                        countElements.forEach(el => el.textContent = 'បរាជ័យ');
                    } else if (data.visitorCount !== undefined && data.visitorCount !== -1) {
                        const count = Number(data.visitorCount);
                        if (!isNaN(count)) {
                            countElements.forEach(el => el.textContent = count.toLocaleString('km-KH'));
                        } else {
                            countElements.forEach(el => el.textContent = 'ទិន្នន័យ​ខុស');
                        }
                    } else {
                        console.error("Unexpected data format received:", data);
                        countElements.forEach(el => el.textContent = 'ទម្រង់​ខុស');
                    }
                })
                .catch(error => {
                    console.error('Error fetching visitor count:', error);
                    countElements.forEach(el => el.textContent = 'បរាជ័យ');
                });
        }
        // --- END: MODIFIED VISITOR COUNTER FUNCTION ---


        // --- START: FETCH STATISTICS FUNCTION ---
        function fetchMemberStatistics() {
            const webAppUrl = "https://script.google.com/macros/s/AKfycbymzOB1xSDowUX6sLbrFX5HjMSM0B6k1VA59qmOmGAqsqyxvFFwhcnZPyxDNzQKKpv2ug/exec";
            const statElements = document.querySelectorAll('.statistics .number');
            statElements.forEach(el => el.textContent = 'កំពុង​ផ្ទុក...');
            fetch(webAppUrl)
                .then(response => {
                    if (!response.ok) throw new Error(`Network response was not ok: ${response.statusText}`);
                    return response.json();
                })
                .then(data => {
                    console.log("Data received:", data);
                    if (data.error) {
                        console.error("Error from Google Apps Script:", data.error);
                        statElements.forEach(el => el.textContent = 'Error');
                        return;
                    }
                    for (const id in data) {
                        const element = document.getElementById(id);
                        if (element) {
                            const value = Number(data[id]);
                            element.textContent = !isNaN(value) ? value.toLocaleString('km-KH') : data[id];
                        } else {
                            console.warn(`HTML element with ID '${id}' not found.`);
                        }
                    }
                    statElements.forEach(el => {
                        if (el.textContent === 'កំពុង​ផ្ទុក...') el.textContent = 'N/A';
                    });
                })
                .catch(error => {
                    console.error('Error fetching or processing statistics:', error);
                    statElements.forEach(el => el.textContent = 'បរាជ័យ');
                });
        }
        // --- END: FETCH STATISTICS FUNCTION ---


        // --- START: DATE/TIME UPDATE FUNCTION (MODIFIED YEAR FORMAT) ---
        function updateDateTime() {
            const now = new Date();
            const days = ['ថ្ងៃអាទិត្យ', 'ថ្ងៃច័ន្ទ', 'ថ្ងៃអង្គារ', 'ថ្ងៃពុធ', 'ថ្ងៃព្រហស្បតិ៍', 'ថ្ងៃសុក្រ', 'ថ្ងៃសៅរ៍'];
            const months = ['មករា', 'កុម្ភៈ', 'មីនា', 'មេសា', 'ឧសភា', 'មិថុនា', 'កក្កដា', 'សីហា', 'កញ្ញា', 'តុលា', 'វិច្ឆិកា', 'ធ្នូ'];
            const dayName = days[now.getDay()];
            const monthName = months[now.getMonth()];

            // *** MODIFICATION HERE: Removed .toLocaleString('km-KH') from getFullYear() ***
            const dateStr = `${dayName} ទី${now.getDate().toLocaleString('km-KH')} ខែ${monthName} ឆ្នាំ${now.getFullYear()}`; // Get year directly

            let hours = now.getHours();
            let minutes = now.getMinutes();
            let seconds = now.getSeconds();
            let ampm = hours >= 12 ? 'ល្ងាច' : 'ព្រឹក';
            hours = hours % 12;
            hours = hours ? hours : 12;
            minutes = minutes < 10 ? '0' + minutes : minutes;
            seconds = seconds < 10 ? '0' + seconds : seconds;
            const hourStr = hours.toLocaleString('km-KH'); // Keep localeString for time parts
            const minuteStr = minutes.toLocaleString('km-KH'); // Keep localeString for time parts
            const secondStr = seconds.toLocaleString('km-KH'); // Keep localeString for time parts
            const timeHTML = `ម៉ោង ${hourStr}<span class="time-minutes-seconds">:${minuteStr}:${secondStr}</span> ${ampm}`;

            const dateElement = document.getElementById('current-date');
            const timeElement = document.getElementById('current-time');
            if (dateElement) dateElement.textContent = dateStr;
            if (timeElement) timeElement.innerHTML = timeHTML;
            setTimeout(updateDateTime, 1000);
        }
        // --- END: DATE/TIME UPDATE FUNCTION ---


        // --- Initialize page functions ---
        updateVisitorCounter();
        fetchMemberStatistics();
        updateDateTime();


        // --- START: LOGO ANIMATION SCRIPT (Greeting Text + Stars) ---
        document.addEventListener('DOMContentLoaded', function() {
             const logo = document.getElementById('logo-img');
             const logoTextContainer = document.querySelector('.logo-text');
             if (!logo) console.error("រកមិនឃើញឡូហ្គោ! ពិនិត្យ ID ឡូហ្គោអ្នក។");
             if (!logoTextContainer) console.error("រកមិនឃើញ .logo-text container!");

             let starAnimationContainer = null;
             if (logo) {
                 starAnimationContainer = document.createElement('div');
                 starAnimationContainer.style.position = 'relative';
                 starAnimationContainer.style.display = 'inline-block';
                 logo.parentNode.insertBefore(starAnimationContainer, logo);
                 starAnimationContainer.appendChild(logo);
             }

             let greetingText = null;
             if (logoTextContainer) {
                 logoTextContainer.style.position = 'relative';
                 logoTextContainer.style.overflow = 'visible';
                 greetingText = document.createElement('div');
                 greetingText.textContent = 'សួស្ដីឆ្នាំថ្មី';
                 Object.assign(greetingText.style, {
                    position: 'absolute', left: '100%', marginLeft: '15px', top: '50%',
                    transform: 'translateY(-50%)', color: '#ecf0f1', fontSize: '16px',
                    fontWeight: 'bold', fontFamily: "'Khmer OS Muol Light', sans-serif",
                    opacity: '0.8', transition: 'all 1.5s ease-in-out', pointerEvents: 'none',
                    zIndex: '100', textShadow: '0 0 5px #e74c3c', whiteSpace: 'nowrap'
                 });
                 logoTextContainer.appendChild(greetingText);
             }

             function animateGreetingText() {
                 if (!greetingText) return;
                Object.assign(greetingText.style, { opacity: '0.8', top: '50%', left: '100%', marginLeft: '15px' });
                setTimeout(() => { if(greetingText) Object.assign(greetingText.style, { top: '120%', marginLeft: '35px' }); }, 1600);
                setTimeout(() => { if(greetingText) Object.assign(greetingText.style, { top: '-20%', marginLeft: '-5px' }); }, 3100);
                setTimeout(() => { if(greetingText) greetingText.style.opacity = '0'; }, 4600);
                setTimeout(() => { if(greetingText) Object.assign(greetingText.style, { top: '50%', left: '100%', marginLeft: '-50px', opacity: '0' }); }, 4800);
                setTimeout(animateGreetingText, 7000);
             }

             function createFallingStar() {
                 if (!starAnimationContainer) return;
                 const star = document.createElement('div');
                 star.innerHTML = '★';
                 Object.assign(star.style, {
                     position: 'absolute',
                     color: ['#FFD700', '#FF0000', '#00FF00', '#FFFFFF', '#FFA500', '#FF69B4', '#00FFFF', '#FF00FF'][Math.floor(Math.random() * 8)],
                     fontSize: Math.random() * 15 + 10 + 'px', top: '-30px',
                     left: Math.random() * (starAnimationContainer.offsetWidth + 40) - 20 + 'px',
                     opacity: '0', transition: `all ${Math.random() * 1.5 + 1}s linear`,
                     pointerEvents: 'none', zIndex: '90',
                     transform: `rotate(${Math.random() * 360}deg)`,
                     filter: 'drop-shadow(0 0 3px currentColor)'
                 });
                 starAnimationContainer.appendChild(star);
                 setTimeout(() => {
                    star.style.opacity = '1';
                    star.style.transform = `translateY(${starAnimationContainer.offsetHeight + 50}px) rotate(${Math.random() * 720 + 360}deg)`;
                    star.style.opacity = '0';
                 }, 10);
                 setTimeout(() => star.remove(), 3000);
             }

             function autoDropStars() {
                  if (!starAnimationContainer) return;
                 setInterval(() => { for (let i = 0; i < 2; i++) setTimeout(createFallingStar, i * 150); }, 800);
             }

            if (greetingText) setTimeout(animateGreetingText, 1000);
            if (starAnimationContainer) setTimeout(autoDropStars, 500);

             if (logo) {
                 logo.addEventListener('click', function() {
                     if (!starAnimationContainer) return;
                     for (let i = 0; i < 30; i++) setTimeout(createFallingStar, i * 20);
                 });
             }
         });
         // --- END: LOGO ANIMATION SCRIPT ---

    </script>
    <!-- The closing </body> and </html> tags -->
</body>
</html>
