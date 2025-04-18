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
            position: relative;
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
        .visitor-counter {
            display: flex;
            align-items: center;
            color: white;
            font-size: 14px;
        }

        .visitor-counter i {
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
            animation: marquee 30s linear infinite; /* Keep this */
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

        @keyframes marquee {
            0% { transform: translateX(100%); }
            100% { transform: translateX(-100%); } /* Adjust as needed */
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
                position: relative;
            }

            .menu {
                flex-direction: column;
                display: none;
                width: 100%;
                position: absolute;
                top: 100%;
                left: 0;
                background-color: #2874a6;
                z-index: 99;
                box-shadow: 0 4px 6px rgba(0,0,0,0.1);
            }

            .menu.active {
                display: flex;
            }

            .submenu {
                position: static;
                width: 100%;
                opacity: 1;
                visibility: visible;
                display: none;
                box-shadow: none;
                background-color: #1a5276;
            }
            .submenu a {
                color: white;
                padding-left: 30px;
            }
             .submenu a:hover {
                background-color: #154360;
                color: #fff;
                padding-left: 35px;
            }

            .menu li:hover .submenu {
                display: block;
            }

             .nav-right-items {
                display: none; /* Hide date/time and counter when menu is collapsed */
             }


            .report-grid {
                grid-template-columns: 1fr;
            }

            .statistics {
                flex-direction: column;
            }
        }
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
                </ul>

                <!-- Group for Date/Time and Visitor Counter -->
                <div class="nav-right-items">
                    <!-- Date/Time Moved Here -->
                    <div class="datetime-display">
                        <div class="date" id="current-date">ថ្ងៃ... ទី... ខែ... ឆ្នាំ...</div>
                        <div class="time" id="current-time">ម៉ោង...</div>
                    </div>

                    <!-- Visitor Counter -->
                    <div class="visitor-counter">
                        <i class="fas fa-users"></i>
                        <span id="visitor-count">កំពុងគណនា...</span>
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

        // Logo animation
        const logo = document.getElementById('logo-img');
        if (logo) {
            logo.addEventListener('mouseover', function() {
                this.style.transform = 'scale(1.1)';
                this.style.transition = 'transform 0.3s ease';
            });
            logo.addEventListener('mouseout', function() {
                this.style.transform = 'scale(1)';
            });
        } else {
            console.error("Logo element not found.");
        }


        // Marquee animation
        const marqueeContent = document.querySelector('.marquee-content');
        if (marqueeContent) {
           // Potentially clone content if very short, but often the animation handles it
           // if (marqueeContent.scrollWidth > marqueeContent.offsetWidth) {
           //     // Clone if content wider than container
           // }
        }


            // --- START: VISITOR COUNTER FUNCTION (INCREMENTS ONCE PER SESSION) ---
    function updateVisitorCounter() {
        // *** សំខាន់! សូមដាក់ URL នៃ Web App របស់អ្នកនៅទីនេះ ***
        const counterWebAppUrl = "https://script.google.com/macros/s/AKfycbxC7uFl2X96AbTYYCTPmO0x1T4it6-Jj_TWBqBqj9Vbvjp1WqPaYHM1lSFfMZ0JuVNK/exec"; // <--- សូមប្តូរ URL នេះ!

        const countElement = document.getElementById('visitor-count');
        countElement.textContent = 'កំពុង​ផ្ទុក...'; // Loading text

        const sessionKey = 'sessionVisitedCounter';
        let apiUrl;

        // Check if this session has already visited
        if (!sessionStorage.getItem(sessionKey)) {
            // First visit in this session: Mark as visited and call API to increment
            sessionStorage.setItem(sessionKey, 'true');
            apiUrl = counterWebAppUrl + '?action=increment'; // Add action parameter
            console.log("First visit this session. Incrementing count.");
        } else {
            // Subsequent visit in this session: Just get the current count
            apiUrl = counterWebAppUrl + '?action=getCount'; // Add different action parameter (or just base URL if script defaults to getCount)
            console.log("Subsequent visit this session. Getting count only.");
        }

        // Fetch the count from the API (either incrementing or just getting)
        fetch(apiUrl)
            .then(response => {
                if (!response.ok) {
                    throw new Error(`Network response was not ok: ${response.statusText}`);
                }
                return response.json();
            })
            .then(data => {
                if (data.error) {
                    console.error("Error from Counter Script:", data.error);
                    countElement.textContent = 'បរាជ័យ'; // Failed text
                } else if (data.visitorCount !== undefined && data.visitorCount !== -1) {
                    const count = Number(data.visitorCount);
                    if (!isNaN(count)) {
                        countElement.textContent = count.toLocaleString('km-KH');
                    } else {
                        countElement.textContent = 'ទិន្នន័យ​ខុស'; // Invalid data text
                    }
                } else {
                    console.error("Unexpected data format received:", data);
                    countElement.textContent = 'ទម្រង់​ខុស'; // Wrong format text
                }
            })
            .catch(error => {
                console.error('Error fetching visitor count:', error);
                countElement.textContent = 'បរាជ័យ'; // Failed text
            });
    }
    // --- END: VISITOR COUNTER FUNCTION ---


        // --- START: FETCH STATISTICS FUNCTION ---
        function fetchMemberStatistics() {
            // *** PASTE YOUR DEPLOYED WEB APP URL FOR STATISTICS HERE ***
            const webAppUrl = "https://script.google.com/macros/s/AKfycbymzOB1xSDowUX6sLbrFX5HjMSM0B6k1VA59qmOmGAqsqyxvFFwhcnZPyxDNzQKKpv2ug/exec";

            // Select all stat elements initially to set loading text
            const statElements = document.querySelectorAll('.statistics .number');
            statElements.forEach(el => el.textContent = 'កំពុង​ផ្ទុក...'); // Loading text

            fetch(webAppUrl)
                .then(response => {
                    if (!response.ok) {
                        throw new Error(`Network response was not ok: ${response.statusText}`);
                    }
                    return response.json();
                })
                .then(data => {
                    console.log("Data received:", data); // For debugging

                    if (data.error) {
                        console.error("Error from Google Apps Script:", data.error);
                        statElements.forEach(el => el.textContent = 'Error');
                        return;
                    }

                    // Update each statistic element based on the ID from the sheet
                    for (const id in data) {
                        const element = document.getElementById(id);
                        if (element) {
                            const value = Number(data[id]);
                            if (!isNaN(value)) {
                                element.textContent = value.toLocaleString('km-KH');
                            } else {
                                element.textContent = data[id]; // Keep as string if not a number
                            }
                        } else {
                            console.warn(`HTML element with ID '${id}' not found.`);
                        }
                    }

                    // Handle cases where an ID might exist in HTML but not in sheet data
                    statElements.forEach(el => {
                        if (el.textContent === 'កំពុង​ផ្ទុក...') {
                            el.textContent = 'N/A';
                        }
                    });
                })
                .catch(error => {
                    console.error('Error fetching or processing statistics:', error);
                    statElements.forEach(el => el.textContent = 'បរាជ័យ'); // Failed text
                });
        }
        // --- END: FETCH STATISTICS FUNCTION ---


        // --- START: DATE/TIME UPDATE FUNCTION ---
        function updateDateTime() {
            const now = new Date();
            const days = ['ថ្ងៃអាទិត្យ', 'ថ្ងៃច័ន្ទ', 'ថ្ងៃអង្គារ', 'ថ្ងៃពុធ', 'ថ្ងៃព្រហស្បតិ៍', 'ថ្ងៃសុក្រ', 'ថ្ងៃសៅរ៍'];
            const months = ['មករា', 'កុម្ភៈ', 'មីនា', 'មេសា', 'ឧសភា', 'មិថុនា', 'កក្កដា', 'សីហា', 'កញ្ញា', 'តុលា', 'វិច្ឆិកា', 'ធ្នូ'];
            const dayName = days[now.getDay()];
            const monthName = months[now.getMonth()];
            const dateStr = `${dayName} ទី${now.getDate().toLocaleString('km-KH')} ខែ${monthName} ឆ្នាំ${now.getFullYear().toLocaleString('km-KH')}`;

            let hours = now.getHours();
            let minutes = now.getMinutes();
            let seconds = now.getSeconds();
            let ampm = hours >= 12 ? 'ល្ងាច' : 'ព្រឹក';
            hours = hours % 12;
            hours = hours ? hours : 12; // Handle midnight (0 becomes 12)
            minutes = minutes < 10 ? '0' + minutes : minutes;
            seconds = seconds < 10 ? '0' + seconds : seconds;

            const hourStr = hours.toLocaleString('km-KH');
            const minuteStr = minutes.toLocaleString('km-KH');
            const secondStr = seconds.toLocaleString('km-KH');

            const timeHTML = `ម៉ោង ${hourStr}<span class="time-minutes-seconds">:${minuteStr}:${secondStr}</span> ${ampm}`;

            document.getElementById('current-date').textContent = dateStr;
            document.getElementById('current-time').innerHTML = timeHTML;

            setTimeout(updateDateTime, 1000);
        }
        // --- END: DATE/TIME UPDATE FUNCTION ---


        // --- Initialize page functions ---
        updateVisitorCounter(); // Update counter on page load (fetches from server)
        fetchMemberStatistics(); // Fetch stats from Google Sheet on page load
        updateDateTime(); // Start the date/time update loop


        // --- START: LOGO ANIMATION SCRIPT ---
         document.addEventListener('DOMContentLoaded', function() {
             const logo = document.getElementById('logo-img');

             if (!logo) {
                 console.error("រកមិនឃើញឡូហ្គោ! ពិនិត្យ ID ឡូហ្គោអ្នក។");
                 return;
             }
             const animationContainer = document.createElement('div');
             animationContainer.style.position = 'relative';
             animationContainer.style.display = 'inline-block'; // Important for positioning children
             logo.parentNode.insertBefore(animationContainer, logo);
             animationContainer.appendChild(logo);

             const greetingText = document.createElement('div');
             greetingText.textContent = 'សួស្ដីឆ្នាំថ្មី';
             greetingText.style.position = 'absolute';
             greetingText.style.left = '-120px';
             greetingText.style.top = '50%';
             greetingText.style.transform = 'translateY(-50%)';
             greetingText.style.color = '#ecf0f1';
             greetingText.style.fontSize = '16px';
             greetingText.style.fontWeight = 'bold';
             greetingText.style.fontFamily = "'Khmer OS Muol Light', sans-serif";
             greetingText.style.opacity = '0.8';
             greetingText.style.transition = 'all 1.5s ease-in-out';
             greetingText.style.pointerEvents = 'none';
             greetingText.style.zIndex = '100';
             greetingText.style.textShadow = '0 0 5px #e74c3c';
             greetingText.style.whiteSpace = 'nowrap';
             animationContainer.appendChild(greetingText);

             function animateGreetingText() {
                greetingText.style.opacity = '0.8';
                greetingText.style.top = '120%';
                greetingText.style.left = '-100px';

                setTimeout(() => {
                    greetingText.style.top = '-20%';
                    greetingText.style.left = '-140px';
                }, 1600);

                setTimeout(() => {
                    greetingText.style.opacity = '0';
                }, 3100);

                setTimeout(() => {
                    greetingText.style.top = '50%';
                    greetingText.style.left = '-200px';
                    greetingText.style.opacity = '0';
                }, 3300);

                setTimeout(() => {
                     greetingText.style.left = '-120px';
                     greetingText.style.opacity = '0.8';
                 }, 3500);

                setTimeout(animateGreetingText, 7000);
             }

             function createFallingStar() {
                 const star = document.createElement('div');
                 star.innerHTML = '★';
                 star.style.position = 'absolute';
                 star.style.color = ['#FFD700', '#FF0000', '#00FF00', '#FFFFFF', '#FFA500', '#FF69B4', '#00FFFF', '#FF00FF'][Math.floor(Math.random() * 8)];
                 star.style.fontSize = Math.random() * 15 + 10 + 'px';
                 star.style.top = '-30px';
                 star.style.left = Math.random() * (animationContainer.offsetWidth + 40) - 20 + 'px';
                 star.style.opacity = '0';
                 star.style.transition = `all ${Math.random() * 1.5 + 1}s linear`;
                 star.style.pointerEvents = 'none';
                 star.style.zIndex = '90';
                 star.style.transform = `rotate(${Math.random() * 360}deg)`;
                 star.style.filter = 'drop-shadow(0 0 3px currentColor)';

                 animationContainer.appendChild(star);

                 setTimeout(() => {
                     star.style.opacity = '1';
                     star.style.transform = `translateY(${animationContainer.offsetHeight + 50}px) rotate(${Math.random() * 720 + 360}deg)`;
                     star.style.opacity = '0';
                 }, 10);

                 setTimeout(() => star.remove(), 3000);
             }

             function autoDropStars() {
                 setInterval(() => {
                     for (let i = 0; i < 2; i++) {
                         setTimeout(createFallingStar, i * 150);
                     }
                 }, 800);
             }

             setTimeout(animateGreetingText, 1000);
             setTimeout(autoDropStars, 500);

             logo.addEventListener('click', function() {
                 for (let i = 0; i < 30; i++) {
                     setTimeout(createFallingStar, i * 20);
                 }
             });
         });
         // --- END: LOGO ANIMATION SCRIPT ---

    </script>
    <!-- The closing </body> and </html> tags -->
</body>
</html>
