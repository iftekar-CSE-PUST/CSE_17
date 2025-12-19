<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CSE Department Students</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            position: relative;
            overflow-x: hidden;
        }

        /* Animated background shapes */
        .bg-shape {
            position: fixed;
            border-radius: 50%;
            opacity: 0.1;
            animation: float 20s infinite;
            z-index: 0;
        }

        .shape1 {
            width: 300px;
            height: 300px;
            background: white;
            top: -100px;
            left: -100px;
            animation-delay: 0s;
        }

        .shape2 {
            width: 200px;
            height: 200px;
            background: white;
            bottom: -50px;
            right: -50px;
            animation-delay: 5s;
        }

        .shape3 {
            width: 150px;
            height: 150px;
            background: white;
            top: 50%;
            right: 10%;
            animation-delay: 10s;
        }

        @keyframes float {
            0%, 100% {
                transform: translate(0, 0) rotate(0deg);
            }
            25% {
                transform: translate(30px, -30px) rotate(90deg);
            }
            50% {
                transform: translate(-30px, 30px) rotate(180deg);
            }
            75% {
                transform: translate(30px, 30px) rotate(270deg);
            }
        }

        .container {
            max-width: 1400px;
            margin: 0 auto;
            position: relative;
            z-index: 1;
        }

        header {
            display: flex;
            flex-wrap: wrap;
            justify-content: space-between;
            align-items: center;
            background: white;
            padding: 20px 30px;
            box-shadow: 0 5px 20px rgba(0,0,0,0.15);
        }

        .logo-section {
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .logo-container {
            position: relative;
        }

        .logo {
            width: 60px;
            height: 60px;
            border-radius: 50%;
            object-fit: cover;
            border: 3px solid #667eea;
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
            animation: pulse 2s infinite;
        }

        @keyframes pulse {
            0%, 100% {
                transform: scale(1);
            }
            50% {
                transform: scale(1.05);
            }
        }

        .header-text h2 {
            font-size: 1.3em;
            color: #333;
            margin-bottom: 5px;
        }

        .header-text small {
            color: #666;
            font-size: 0.9em;
        }

        .time {
            text-align: right;
            font-weight: bold;
            color: #667eea;
            font-size: 1em;
            line-height: 1.4;
        }

        .hero-section {
            text-align: center;
            padding: 40px 20px 30px;
            color: white;
        }

        .hero-section h1 {
            font-size: 2.8em;
            margin-bottom: 15px;
            text-shadow: 2px 2px 8px rgba(0,0,0,0.3);
            animation: slideDown 0.8s ease-out;
        }

        @keyframes slideDown {
            from {
                opacity: 0;
                transform: translateY(-30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .session-info {
            background: rgba(255,255,255,0.25);
            padding: 15px 35px;
            border-radius: 50px;
            display: inline-block;
            backdrop-filter: blur(10px);
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
            font-size: 1.1em;
            margin-bottom: 25px;
        }

        .search-box {
            max-width: 500px;
            margin: 0 auto 30px;
            position: relative;
        }

        .search-box input {
            width: 100%;
            padding: 15px 50px 15px 20px;
            border-radius: 50px;
            border: none;
            font-size: 16px;
            box-shadow: 0 5px 20px rgba(0,0,0,0.2);
            transition: transform 0.3s;
        }

        .search-box input:focus {
            outline: none;
            transform: scale(1.02);
        }

        .search-box i {
            position: absolute;
            right: 20px;
            top: 50%;
            transform: translateY(-50%);
            color: #667eea;
            font-size: 1.2em;
        }

        .stats {
            text-align: center;
            margin: 20px auto 40px;
            padding: 30px;
            background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
            border-radius: 20px;
            color: white;
            max-width: 400px;
            box-shadow: 0 10px 30px rgba(245,87,108,0.3);
            position: relative;
            overflow: hidden;
        }

        .stats::before {
            content: '🎓';
            position: absolute;
            font-size: 120px;
            opacity: 0.15;
            top: -20px;
            right: -20px;
            animation: rotate 20s linear infinite;
        }

        @keyframes rotate {
            from { transform: rotate(0deg); }
            to { transform: rotate(360deg); }
        }

        .stats h2 {
            font-size: 3.5em;
            margin-bottom: 10px;
            position: relative;
            z-index: 2;
        }

        .stats p {
            font-size: 1.2em;
            position: relative;
            z-index: 2;
        }

        .student-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
            gap: 30px;
            padding: 20px;
            margin-bottom: 40px;
        }

        .student-card {
            background: white;
            border-radius: 20px;
            box-shadow: 0 8px 25px rgba(0,0,0,0.15);
            overflow: hidden;
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            position: relative;
            animation: cardFadeIn 0.6s ease-out backwards;
        }

        .student-card:nth-child(odd) { animation-delay: 0.1s; }
        .student-card:nth-child(even) { animation-delay: 0.2s; }

        @keyframes cardFadeIn {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .student-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 5px;
            background: linear-gradient(90deg, #667eea, #764ba2);
            transform: scaleX(0);
            transition: transform 0.4s;
        }

        .student-card:hover::before {
            transform: scaleX(1);
        }

        .student-card:hover {
            transform: translateY(-10px) scale(1.02);
            box-shadow: 0 20px 40px rgba(0,0,0,0.25);
        }

        .photo-container {
            position: relative;
            overflow: hidden;
            height: 280px;
        }

        .student-photo, .initials {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.4s;
        }

        .initials {
            background: linear-gradient(135deg, #667eea, #764ba2);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 4em;
            font-weight: bold;
            color: white;
        }

        .student-card:hover .student-photo {
            transform: scale(1.1);
        }

        .photo-overlay {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(to bottom, transparent, rgba(0,0,0,0.4));
            opacity: 0;
            transition: opacity 0.4s;
        }

        .student-card:hover .photo-overlay {
            opacity: 1;
        }

        .student-info {
            padding: 25px;
        }

        .student-name {
            font-size: 1.3em;
            font-weight: bold;
            color: #333;
            margin-bottom: 12px;
            text-align: center;
            text-transform: uppercase;
        }

        .student-id {
            color: #666;
            font-size: 0.95em;
            margin-bottom: 15px;
            padding: 8px 15px;
            background: linear-gradient(135deg, #f0f0f0, #e0e0e0);
            border-radius: 20px;
            display: inline-block;
            font-weight: 600;
        }

        .info-item {
            display: flex;
            align-items: center;
            gap: 8px;
            margin: 8px 0;
            font-size: 0.9em;
            color: #555;
            flex-wrap: wrap;
        }

        .info-item i {
            width: 18px;
            font-size: 1em;
        }

        .icon-session { color: #ff9900; }
        .icon-current { color: #33cc33; }
        .icon-permanent { color: #ff33cc; }
        .icon-phone { color: #0066cc; }
        .icon-facebook { color: #1877f2; }
        .icon-email { color: #ff6600; }
        .icon-blood { color: #cc0000; }

        .copy-btn {
            border: none;
            background: none;
            cursor: pointer;
            color: #667eea;
            padding: 4px 6px;
            border-radius: 5px;
            transition: all 0.3s;
        }

        .copy-btn:hover {
            background: #f0f0f0;
            transform: scale(1.1);
        }

        .toast {
            visibility: hidden;
            min-width: 250px;
            background-color: #333;
            color: #fff;
            text-align: center;
            border-radius: 10px;
            padding: 15px 20px;
            position: fixed;
            left: 50%;
            bottom: 30px;
            transform: translateX(-50%);
            font-size: 14px;
            z-index: 9999;
            opacity: 0;
            transition: opacity 0.4s, bottom 0.4s;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
            box-shadow: 0 5px 20px rgba(0,0,0,0.3);
        }

        .toast.show {
            visibility: visible;
            opacity: 1;
            bottom: 50px;
        }

        footer {
            background: linear-gradient(135deg, #2c3e50 0%, #34495e 100%);
            color: white;
            text-align: center;
            padding: 30px 20px;
            position: relative;
            overflow: hidden;
            margin-top: 40px;
        }

        footer::before {
            content: '💻';
            position: absolute;
            font-size: 100px;
            opacity: 0.05;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
        }

        footer p {
            margin: 8px 0;
            opacity: 0.9;
            position: relative;
            z-index: 2;
        }

        .footer-divider {
            width: 80px;
            height: 3px;
            background: white;
            margin: 12px auto;
            border-radius: 2px;
        }

        @media (max-width: 768px) {
            .hero-section h1 {
                font-size: 2em;
            }

            .student-grid {
                grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
                gap: 20px;
            }

            header {
                flex-direction: column;
                align-items: flex-start;
                gap: 15px;
            }

            .time {
                text-align: left;
            }
        }
    </style>
</head>
<body>
    <div class="bg-shape shape1"></div>
    <div class="bg-shape shape2"></div>
    <div class="bg-shape shape3"></div>

    <div class="container">
        <header>
            <div class="logo-section">
                <div class="logo-container">
                    <img src="https://res.cloudinary.com/dcwnn9c0u/image/upload/v1766143395/ntbvvksdjnpcvvpq6itt.jpg" alt="CSE Logo" class="logo">
                </div>
                <div class="header-text">
                    <h2>Computer Science & Engineering</h2>
                    <small>Pabna University of Science & Technology</small>
                </div>
            </div>
            <div class="time" id="time"></div>
        </header>

        <div class="hero-section">
            <h1>CSE Department Students</h1>
            <div class="session-info">
                <strong>Session:</strong> 2024-2025
            </div>
            
            <div class="search-box">
                <input type="text" id="search" placeholder="Search by name or student ID...">
                <i class="fa-solid fa-search"></i>
            </div>

            <div class="stats">
                <h2 id="totalCount">36</h2>
                <p>Total Students</p>
            </div>
        </div>

        <div class="student-grid" id="studentGrid"></div>

        <footer>
            <p>&copy; <span id="year"></span> Pabna University of Science & Technology. All rights reserved.</p>
            <div class="footer-divider"></div>
            <p>Computer Science & Engineering Department</p>
        </footer>
    </div>

    <div id="toast" class="toast">
        <i class="fa-solid fa-check"></i>
        <span id="toast-text"></span>
    </div>

    <script>
        const students = [
            { id: 1, name: "Akhi Akter Mim", studentId: "250101",currentAddress: "", permanentAddress: "", phone: "01612036386", facebook: "", email: "", bloodGroup: "", photo: "" },
            { id: 2, name: "Md. Masir Uddin Nafiz ", studentId: "250103",currentAddress: "Mohisher Dipo, Pabna", permanentAddress: "Shariakandi,  Bogura", phone: "01723541919", facebook: "https://www.facebook.com/share/17iXMSgbvs/", email: "nasiruddin.nfz21@gmail.com", bloodGroup: "A+", photo: "https://res.cloudinary.com/dcwnn9c0u/image/upload/v1766156267/id6cyo4wmyw0o6hlfyzm.jpg"},
            { id: 3, name: "Amit Kumar Dhali", studentId: "250104",currentAddress: "", permanentAddress: "", phone: "01533878366", facebook: "", email: "", bloodGroup: "", photo: "" },
            { id: 4, name: "Md. Shafayat Ahmed", studentId: "250105",currentAddress: "", permanentAddress: "", phone: "01559704798", facebook: "", email: "", bloodGroup: "", photo: "" },
            { id: 5, name: "Toufique Al Imran", studentId: "250106",currentAddress: "", permanentAddress: "", phone: "01721798790", facebook: "", email: "", bloodGroup: "", photo: "" },
            { id: 6, name: "Apurba Kumar", studentId: "250107",currentAddress: "", permanentAddress: "", phone: "01771076379", facebook: "", email: "", bloodGroup: "", photo: "" },
            { id: 7, name: "Md. Muhibur Rahman Bhuiyan", studentId: "250108",currentAddress: "", permanentAddress: "", phone: "01670749248", facebook: "", email: "", bloodGroup: "", photo: "" },
            { id: 8, name: "Md. Faruk Hossain", studentId: "250109",currentAddress: "", permanentAddress: "", phone: "01723914033", facebook: "", email: "", bloodGroup: "", photo: "" },
            { id: 9, name: "Upama Saha", studentId: "250110",currentAddress: "Munsurabad, Pabna", permanentAddress: "Sarishabari, Jamalpur", phone: "01327221457", facebook: "https://www.facebook.com/share/16kouSyzwK/?mibextid=wwXIfr", email: "uparnasaha0@gmail.com", bloodGroup: "B+", photo: "https://res.cloudinary.com/dcwnn9c0u/image/upload/v1766148102/gwedorv2cy2yqpe4tggj.jpg" },
            { id: 10, name: "Md. Mahfil Akter", studentId: "250111",currentAddress: "Mohisher Dipo", permanentAddress: "Naogaon", phone: "01716175548", facebook: "https://www.facebook.com/share/1HtVvXPhgA/", email: "mdmahfilakter@gmail.com", bloodGroup: "B+", photo: "https://res.cloudinary.com/dcwnn9c0u/image/upload/v1766155646/sjksqvk6m9mppgcey4zr.jpg"},
            { id: 11, name: "Md. Asadullah Atik", studentId: "250112",currentAddress: "", permanentAddress: "", phone: "01874175415", facebook: "", email: "", bloodGroup: "", photo: "" },
            { id: 12, name: "Avijit Biswas", studentId: "250113",currentAddress: "", permanentAddress: "", phone: "01902340202", facebook: "", email: "", bloodGroup: "", photo: "" },
            { id: 13, name: "Mst. Sumaiya Islam", studentId: "250114",currentAddress: "", permanentAddress: "", phone: "01924465889", facebook: "", email: "", bloodGroup: "", photo: "" },
            { id: 14, name: "Rima Jahan", studentId: "250115",currentAddress: "", permanentAddress: "", phone: "01909197188", facebook: "", email: "", bloodGroup: "", photo: "" },
            { id: 15, name: "Mst. Urmila Khatun", studentId: "250116",currentAddress: "", permanentAddress: "", phone: "01612482547", facebook: "", email: "", bloodGroup: "", photo: "" },
            { id: 16, name: "Md. Forhad Zaman", studentId: "250117",currentAddress: "", permanentAddress: "", phone: "01630743003", facebook: "", email: "", bloodGroup: "", photo: "" },
            { id: 17, name: "Md. Soyab Hossain", studentId: "250119",currentAddress: "", permanentAddress: "", phone: "01571054693", facebook: "", email: "", bloodGroup: "", photo: "" },
            { id: 18, name: "Asmaul Husna", studentId: "250120",currentAddress: "", permanentAddress: "", phone: "01743253000", facebook: "", email: "", bloodGroup: "", photo: "" },
            { id: 19, name: "Md. Nahidul Islam", studentId: "250121",currentAddress: "", permanentAddress: "", phone: "01834145283", facebook: "", email: "", bloodGroup: "", photo: "" },
            { id: 20, name:"Salauddin Ayyuve", studentId:"250122",currentAddress:"Mujahid Club", permanentAddress: "Bashuriya, Shajadpure,Sirajganj ", phone: "01318856637", facebook: "https://www.facebook.com/share/17agXG6z6T/ ", email: "salauddinaiuve@gmail.com", bloodGroup: "B-", photo: "https://res.cloudinary.com/dcwnn9c0u/image/upload/v1766151639/eogujcllokxq90igrvqg.jpg"},
            {id : 21, name : "Zahin Mahmud Daiyan", studentId : "250123", currentAddress : "Mahtab Tower, Rajapur, Pabna", permanentAddress : "Mohonpur Road, Mohonpur, Natore", phone : "01701299258", facebook : "https://www.facebook.com/zahin.mahmud.daiyan.CSE.PUST", email : "zahinmahmuddaiyan271@gmail.com", bloodGroup : "O+", photo : "https://res.cloudinary.com/dcwnn9c0u/image/upload/v1766153355/dyaa4sw21ku0noarts5q.jpg"},            { id: 22, name: "Mst. Khandakar Jahida", studentId: "250124",currentAddress: "", permanentAddress: "", phone: "01303341680", facebook: "", email: "", bloodGroup: "", photo: "" },
            { id: 23, name: "SHAHID-HASAN-FAHIM", studentId: "250125",currentAddress: "MOJAHID CLUB", permanentAddress: "NILPHAMARI", phone: "01720988987", facebook: "https://www.facebook.com/share/1HLGbwMiFn/", email: "shfahimf@gmail.com", bloodGroup: "o+", photo: "https://res.cloudinary.com/dcwnn9c0u/image/upload/v1766153186/wz3dqceu1zvyyp8oyftl.jpg"},
            { id: 24, name: "Fatema", studentId: "250127",currentAddress: "", permanentAddress: "", phone: "01605991240", facebook: "", email: "", bloodGroup: "", photo: "" },
            { id: 25, name: "Mst. Soheli Aktar Akhi", studentId: "250128",currentAddress: "", permanentAddress: "", phone: "01817552561", facebook: "", email: "", bloodGroup: "", photo: "" },
            { id: 26, name: "Khandaker Saiful Islam Tanvir", studentId: "250130",currentAddress: "Mujahid Club", permanentAddress: "Muradnagar, Cumilla", phone: "01602032209", facebook: "https://www.facebook.com/share/1AXbodyPma/", email: "Khandakertanvir151@gmail ", bloodGroup: "B+", photo: "https://res.cloudinary.com/dcwnn9c0u/image/upload/v1766150081/ihvsrpvfrqmvhuhwwu9p.jpg"},
            { id: 27, name: "Md. Riyaz Ali", studentId: " 250132",currentAddress: " Mujahid Club", permanentAddress: "Rajshahi", phone: "01751812046", facebook: " https://www.facebook.com/share/17wXYyanuL/", email: "mdriyazali531@gmail.com", bloodGroup: "O+", photo: "https://res.cloudinary.com/dcwnn9c0u/image/upload/v1766151474/gzbochse0bez3q1dxqk3.jpg"},
            { id: 28, name: "Md. Sahadat Hossain", studentId: "250133",currentAddress: "", permanentAddress: "", phone: "01994728770", facebook: "", email: "", bloodGroup: "", photo: "" },
            { id: 29, name: "Jagojit Chandro Barmon", studentId: "250134",currentAddress: "", permanentAddress: "", phone: "01737232248", facebook: "", email: "", bloodGroup: "", photo: "" },
            { id: 30, name: "Nuruzzaman Nahid", studentId: "250135",currentAddress: "", permanentAddress: "", phone: "01865935058", facebook: "", email: "", bloodGroup: "", photo: "" },
            { id: 31, name: "Sameeha Zahan Mridula", studentId: "250136",currentAddress: "", permanentAddress: "", phone: "01950377978", facebook: "", email: "", bloodGroup: "", photo: "" },
            { id: 32, name: "Mohd. Atiquzzaman Atiq", studentId: "250137",currentAddress: "", permanentAddress: "", phone: "01331945616", facebook: "", email: "", bloodGroup: "", photo: "" },
            { id: 33, name: "Samin Yesar Tousib", studentId: "250138",currentAddress: "", permanentAddress: "", phone: "01318009252", facebook: "", email: "", bloodGroup: "", photo: "" },
            { id: 34, name: "Md. Iftekar Rahman", studentId: "250139",currentAddress: "Mujahid Club, Pabna", permanentAddress: "Rajshahi", phone: "01610077278", facebook: "", email: "riadraj009@gmail.com", bloodGroup: "A+", photo: "https://res.cloudinary.com/dcwnn9c0u/image/upload/v1766141000/veq9zourcsiwknwmoiyo.jpg" },
            { id: 35, name: "Azizul Hoque Emon", studentId: "250140",currentAddress: "", permanentAddress: "", phone: "01576688477", facebook: "", email: "", bloodGroup: "", photo: "" },
            { id: 36, name: "Mst. Johura Khatun", studentId: "250141",currentAddress: "", permanentAddress: "", phone: "01752403522", facebook: "", email: "", bloodGroup: "", photo: "" }
        ];

        function getInitials(name) {
            return name.split(" ").map(w => w[0]).join("").toUpperCase();
        }

        function copyText(text) {
            navigator.clipboard.writeText(text).then(() => showToast(`${text} copied!`));
        }

        function showToast(message) {
            const toast = document.getElementById("toast");
            document.getElementById("toast-text").textContent = message;
            toast.className = "toast show";
            setTimeout(() => {
                toast.className = toast.className.replace("show", "");
            }, 2500);
        }

        function renderStudents(filter = "") {
            const grid = document.getElementById('studentGrid');
            grid.innerHTML = '';
            let count = 0;

            students.forEach(student => {
                if (student.name.toLowerCase().includes(filter) || 
                    student.studentId.toLowerCase().includes(filter)) {
                    
                    const card = document.createElement('div');
                    card.className = 'student-card';
                    
                    const photoHTML = student.photo 
                        ? `<img src="${student.photo}" alt="${student.name}" class="student-photo" onerror="this.parentElement.innerHTML='<div class=\\'initials\\'>${getInitials(student.name)}</div>'">`
                        : `<div class="initials">${getInitials(student.name)}</div>`;
                    
                    card.innerHTML = `
                        <div class="photo-container">
                            ${photoHTML}
                            <div class="photo-overlay"></div>
                        </div>
                        <div class="student-info">
                            <div class="student-name">${student.name}</div>
                            <div class="student-id"><i class="fa-solid fa-id-card"></i> ${student.studentId}</div>
                            ${student.session ? `
                                <div class="info-item">
                                    <i class="fa-solid fa-graduation-cap icon-session"></i>
                                    <span>Session: ${student.session}</span>
                                </div>
                            ` : ''}
                            ${student.currentAddress ? `
                                <div class="info-item">
                                    <i class="fa-solid fa-location-dot icon-current"></i>
                                    <span>Current: ${student.currentAddress}</span>
                                </div>
                            ` : ''}
                            ${student.permanentAddress ? `
                                <div class="info-item">
                                    <i class="fa-solid fa-house icon-permanent"></i>
                                    <span>Permanent: ${student.permanentAddress}</span>
                                </div>
                            ` : ''}
                            ${student.phone ? `
                                <div class="info-item">
                                    <i class="fa-solid fa-phone icon-phone"></i>
                                    <span>${student.phone}</span>
                                    <button class="copy-btn" onclick="copyText('${student.phone}')">
                                        <i class="fa-regular fa-copy"></i>
                                    </button>
                                </div>
                            ` : ''}
                            ${student.facebook ? `
                                <div class="info-item">
                                    <i class="fa-brands fa-facebook icon-facebook"></i>
                                    <a href="${student.facebook}" target="_blank" style="color: #1877f2; text-decoration: none;">Facebook</a>
                                    <button class="copy-btn" onclick="copyText('${student.facebook}')">
                                        <i class="fa-regular fa-copy"></i>
                                    </button>
                                </div>
                            ` : ''}
                            ${student.email ? `
                                <div class="info-item">
                                    <i class="fa-solid fa-envelope icon-email"></i>
                                    <span>${student.email}</span>
                                    <button class="copy-btn" onclick="copyText('${student.email}')">
                                        <i class="fa-regular fa-copy"></i>
                                    </button>
                                </div>
                            ` : ''}
                            ${student.bloodGroup ? `
                                <div class="info-item">
                                    <i class="fa-solid fa-tint icon-blood"></i>
                                    <span>Blood: ${student.bloodGroup}</span>
                                </div>
                            ` : ''}
                        </div>
                    `;
                    grid.appendChild(card);
                    count++;
                }
            });
            
            document.getElementById('totalCount').textContent = count;
        }

        document.getElementById('search').addEventListener('input', (e) => {
            renderStudents(e.target.value.toLowerCase());
        });

        function updateTime() {
            const now = new Date();
            document.getElementById('time').innerHTML = 
                now.toLocaleTimeString() + "<br>" + 
                now.toLocaleDateString(undefined, {
                    weekday: 'short',
                    month: 'short',
                    day: 'numeric',
                    year: 'numeric'
                });
        }

        setInterval(updateTime, 1000);
        updateTime();
        renderStudents();
        document.getElementById("year").textContent = new Date().getFullYear();
    </script>
</body>
</html>
