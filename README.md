<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CSE Department Students</title>
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
            padding: 20px;
            position: relative;
            overflow-x: hidden;
        }

        /* Animated background shapes */
        .bg-shape {
            position: fixed;
            border-radius: 50%;
            opacity: 0.1;
            animation: float 20s infinite;
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
            max-width: 1200px;
            margin: 0 auto;
            background: white;
            border-radius: 20px;
            box-shadow: 0 20px 60px rgba(0,0,0,0.3);
            overflow: hidden;
            position: relative;
        }

        header {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            text-align: center;
            padding: 50px 20px;
            position: relative;
            overflow: hidden;
        }

        /* Header decorative elements */
        header::before {
            content: '';
            position: absolute;
            width: 500px;
            height: 500px;
            background: rgba(255,255,255,0.1);
            border-radius: 50%;
            top: -200px;
            right: -200px;
        }

        header::after {
            content: '';
            position: absolute;
            width: 300px;
            height: 300px;
            background: rgba(255,255,255,0.05);
            border-radius: 50%;
            bottom: -100px;
            left: -100px;
        }

        .logo-container {
            position: relative;
            display: inline-block;
            margin-bottom: 25px;
        }

        .logo {
            width: 140px;
            height: 140px;
            border-radius: 50%;
            object-fit: cover;
            border: 6px solid white;
            box-shadow: 0 10px 30px rgba(0,0,0,0.3);
            position: relative;
            z-index: 2;
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

        .logo-ring {
            position: absolute;
            top: -10px;
            left: -10px;
            right: -10px;
            bottom: -10px;
            border: 3px solid rgba(255,255,255,0.3);
            border-radius: 50%;
            animation: rotate 10s linear infinite;
        }

        @keyframes rotate {
            from {
                transform: rotate(0deg);
            }
            to {
                transform: rotate(360deg);
            }
        }

        h1 {
            font-size: 2.8em;
            margin-bottom: 15px;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.2);
            position: relative;
            z-index: 2;
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

        .subtitle {
            font-size: 1.3em;
            opacity: 0.95;
            margin-bottom: 30px;
            position: relative;
            z-index: 2;
            animation: slideUp 0.8s ease-out;
        }

        @keyframes slideUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .session-info {
            background: rgba(255,255,255,0.25);
            padding: 18px 40px;
            border-radius: 50px;
            display: inline-block;
            backdrop-filter: blur(10px);
            position: relative;
            z-index: 2;
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
            animation: fadeIn 1s ease-out;
        }

        @keyframes fadeIn {
            from {
                opacity: 0;
            }
            to {
                opacity: 1;
            }
        }

        .content {
            padding: 50px 20px;
        }

        .stats {
            text-align: center;
            margin-bottom: 50px;
            padding: 30px;
            background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
            border-radius: 20px;
            color: white;
            position: relative;
            overflow: hidden;
            box-shadow: 0 10px 30px rgba(245,87,108,0.3);
        }

        .stats::before {
            content: '🎓';
            position: absolute;
            font-size: 150px;
            opacity: 0.1;
            top: -30px;
            right: -30px;
            animation: rotate 20s linear infinite;
        }

        .stats h2 {
            font-size: 3em;
            margin-bottom: 10px;
            position: relative;
            z-index: 2;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.2);
        }

        .stats p {
            font-size: 1.3em;
            position: relative;
            z-index: 2;
        }

        .decorative-line {
            height: 4px;
            background: linear-gradient(90deg, transparent, #667eea, #764ba2, transparent);
            margin: 40px 0;
            border-radius: 2px;
        }

        .student-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 30px;
            margin-bottom: 40px;
        }

        .student-card {
            background: white;
            border-radius: 20px;
            box-shadow: 0 8px 25px rgba(0,0,0,0.1);
            overflow: hidden;
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            position: relative;
            animation: cardFadeIn 0.6s ease-out backwards;
        }

        .student-card:nth-child(1) { animation-delay: 0.1s; }
        .student-card:nth-child(2) { animation-delay: 0.15s; }
        .student-card:nth-child(3) { animation-delay: 0.2s; }
        .student-card:nth-child(4) { animation-delay: 0.25s; }
        .student-card:nth-child(5) { animation-delay: 0.3s; }
        .student-card:nth-child(6) { animation-delay: 0.35s; }

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
            transform: translateY(-15px) scale(1.02);
            box-shadow: 0 20px 50px rgba(0,0,0,0.2);
        }

        .student-photo {
            width: 100%;
            height: 300px;
            object-fit: cover;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            transition: transform 0.4s;
        }

        .student-card:hover .student-photo {
            transform: scale(1.1);
        }

        .photo-overlay {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 300px;
            background: linear-gradient(to bottom, transparent, rgba(0,0,0,0.3));
            opacity: 0;
            transition: opacity 0.4s;
        }

        .student-card:hover .photo-overlay {
            opacity: 1;
        }

        .student-info {
            padding: 25px;
            position: relative;
        }

        .student-name {
            font-size: 1.4em;
            font-weight: bold;
            color: #333;
            margin-bottom: 10px;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .student-name::before {
            content: '👤';
            font-size: 0.8em;
        }

        .student-id {
            color: #666;
            font-size: 1em;
            margin-bottom: 15px;
            padding: 8px 15px;
            background: linear-gradient(135deg, #f0f0f0, #e0e0e0);
            border-radius: 20px;
            display: inline-block;
            font-weight: 600;
        }

        .student-contact {
            color: #764ba2;
            font-size: 0.95em;
            margin-top: 8px;
            display: flex;
            align-items: center;
            gap: 8px;
            padding: 5px 0;
            transition: transform 0.3s;
        }

        .student-contact:hover {
            transform: translateX(5px);
        }

        footer {
            background: linear-gradient(135deg, #2c3e50 0%, #34495e 100%);
            color: white;
            text-align: center;
            padding: 40px 20px;
            position: relative;
            overflow: hidden;
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
            width: 60px;
            height: 3px;
            background: white;
            margin: 15px auto;
            border-radius: 2px;
        }

        @media (max-width: 768px) {
            h1 {
                font-size: 2em;
            }

            .student-grid {
                grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
                gap: 20px;
            }

            .stats h2 {
                font-size: 2.5em;
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
            <div class="logo-container">
                <div class="logo-ring"></div>
                <img src="https://i.ibb.co/p6ZSf9Yn/photo-2025-03-12-12-06-01.jpg" alt="CSE Logo" class="logo">
            </div>
            <h1>Computer Science & Engineering</h1>
            <p class="subtitle">Pabna University of Science & Technology</p>
            <div class="session-info">
                <strong>Session:</strong> 2024-2025
            </div>
        </header>

        <div class="content">
            <div class="stats">
                <h2 id="totalCount">36</h2>
                <p>Total Students</p>
            </div>

            <div class="decorative-line"></div>

            <div class="student-grid" id="studentGrid"></div>
        </div>

        <footer>
            <p>&copy; 2025 Pabna University of Science & Technology. All rights reserved.</p>
            <div class="footer-divider"></div>
            <p>Computer Science & Engineering Department</p>
        </footer>
    </div>

    <script>
        const students = [
            {
                id: 1,
                name: "Akhi Akter Mim",
                studentId: "250101",
                email: "",
                phone: "01612036386",
                photo: "https://via.placeholder.com/300x300/667eea/ffffff?text=Akhi+Akter+Mim"
            },
            {
                id: 2,
                name: "Md. Nasir Uddin Nafiz",
                studentId: "250103",
                email: "",
                phone: "01723541919",
                photo: "https://via.placeholder.com/300x300/764ba2/ffffff?text=Nasir+Uddin"
            },
            {
                id: 3,
                name: "Amit Kumar Dhali",
                studentId: "250104",
                email: "",
                phone: "01533878366",
                photo: "https://via.placeholder.com/300x300/667eea/ffffff?text=Amit+Kumar"
            },
            {
                id: 4,
                name: "Md. Shafayat Ahmed",
                studentId: "250105",
                email: "",
                phone: "01559704798",
                photo: "https://via.placeholder.com/300x300/764ba2/ffffff?text=Shafayat+Ahmed"
            },
            {
                id: 5,
                name: "Toufique Al Imran",
                studentId: "250106",
                email: "",
                phone: "01721798790",
                photo: "https://via.placeholder.com/300x300/667eea/ffffff?text=Toufique+Imran"
            },
            {
                id: 6,
                name: "Apurba Kumar",
                studentId: "250107",
                email: "",
                phone: "01771076379",
                photo: "https://via.placeholder.com/300x300/764ba2/ffffff?text=Apurba+Kumar"
            },
            {
                id: 7,
                name: "Md. Muhibur Rahman Bhuiyan",
                studentId: "250108",
                email: "",
                phone: "01670749248",
                photo: "https://via.placeholder.com/300x300/667eea/ffffff?text=Muhibur+Rahman"
            },
            {
                id: 8,
                name: "Md. Faruk Hossain",
                studentId: "250109",
                email: "",
                phone: "01723914033",
                photo: "https://via.placeholder.com/300x300/764ba2/ffffff?text=Faruk+Hossain"
            },
            {
                id: 9,
                name: "Upama Saha",
                studentId: "250110",
                email: "",
                phone: "01327221457",
                photo: "https://via.placeholder.com/300x300/667eea/ffffff?text=Upama+Saha"
            },
            {
                id: 10,
                name: "Md. Mahfil Akter",
                studentId: "250111",
                email: "",
                phone: "01716175548",
                photo: "https://via.placeholder.com/300x300/764ba2/ffffff?text=Mahfil+Akter"
            },
            {
                id: 11,
                name: "Md. Asadullah Atik",
                studentId: "250112",
                email: "",
                phone: "01874175415",
                photo: "https://via.placeholder.com/300x300/667eea/ffffff?text=Asadullah+Atik"
            },
            {
                id: 12,
                name: "Avijit Biswas",
                studentId: "250113",
                email: "",
                phone: "01902340202",
                photo: "https://via.placeholder.com/300x300/764ba2/ffffff?text=Avijit+Biswas"
            },
            {
                id: 13,
                name: "Mst. Sumaiya Islam",
                studentId: "250114",
                email: "",
                phone: "01924465889",
                photo: "https://via.placeholder.com/300x300/667eea/ffffff?text=Sumaiya+Islam"
            },
            {
                id: 14,
                name: "Rima Jahan",
                studentId: "250115",
                email: "",
                phone: "01909197188",
                photo: "https://via.placeholder.com/300x300/764ba2/ffffff?text=Rima+Jahan"
            },
            {
                id: 15,
                name: "Mst. Urmila Khatun",
                studentId: "250116",
                email: "",
                phone: "01612482547",
                photo: "https://via.placeholder.com/300x300/667eea/ffffff?text=Urmila+Khatun"
            },
            {
                id: 16,
                name: "Md. Forhad Zaman",
                studentId: "250117",
                email: "",
                phone: "01630743003",
                photo: "https://via.placeholder.com/300x300/764ba2/ffffff?text=Forhad+Zaman"
            },
            {
                id: 17,
                name: "Md. Soyab Hossain",
                studentId: "250119",
                email: "",
                phone: "01571054693",
                photo: "https://via.placeholder.com/300x300/667eea/ffffff?text=Soyab+Hossain"
            },
            {
                id: 18,
                name: "Asmaul Husna",
                studentId: "250120",
                email: "",
                phone: "01743253000",
                photo: "https://via.placeholder.com/300x300/764ba2/ffffff?text=Asmaul+Husna"
            },
            {
                id: 19,
                name: "Md. Nahidul Islam",
                studentId: "250121",
                email: "",
                phone: "01834145283",
                photo: "https://via.placeholder.com/300x300/667eea/ffffff?text=Nahidul+Islam"
            },
            {
                id: 20,
                name: "Salauddin",
                studentId: "250122",
                email: "",
                phone: "01318856637",
                photo: "https://via.placeholder.com/300x300/764ba2/ffffff?text=Salauddin"
            },
            {
                id: 21,
                name: "Zahin Mahmud Daiyan",
                studentId: "250123",
                email: "",
                phone: "01701299258",
                photo: "https://via.placeholder.com/300x300/667eea/ffffff?text=Zahin+Mahmud"
            },
            {
                id: 22,
                name: "Mst. Khandakar Jahida",
                studentId: "250124",
                email: "",
                phone: "01303341680",
                photo: "https://via.placeholder.com/300x300/764ba2/ffffff?text=Khandakar+Jahida"
            },
            {
                id: 23,
                name: "Shahid Hasan Fahim",
                studentId: "250125",
                email: "",
                phone: "01720988987",
                photo: "https://via.placeholder.com/300x300/667eea/ffffff?text=Shahid+Hasan"
            },
            {
                id: 24,
                name: "Fatema",
                studentId: "250127",
                email: "",
                phone: "01605991240",
                photo: "https://via.placeholder.com/300x300/764ba2/ffffff?text=Fatema"
            },
            {
                id: 25,
                name: "Mst. Soheli Aktar Akhi",
                studentId: "250128",
                email: "",
                phone: "01817552561",
                photo: "https://via.placeholder.com/300x300/667eea/ffffff?text=Soheli+Aktar"
            },
            {
                id: 26,
                name: "Khandaker Saiful Islam Tanvir",
                studentId: "250130",
                email: "",
                phone: "01819822010",
                photo: "https://via.placeholder.com/300x300/764ba2/ffffff?text=Saiful+Islam"
            },
            {
                id: 27,
                name: "Md. Riyaz Ali",
                studentId: "250132",
                email: "",
                phone: "01751812046",
                photo: "https://via.placeholder.com/300x300/667eea/ffffff?text=Riyaz+Ali"
            },
            {
                id: 28,
                name: "Md. Sahadat Hossain",
                studentId: "250133",
                email: "",
                phone: "01994728770",
                photo: "https://via.placeholder.com/300x300/764ba2/ffffff?text=Sahadat+Hossain"
            },
            {
                id: 29,
                name: "Jagojit Chandro Barmon",
                studentId: "250134",
                email: "",
                phone: "01737232248",
                photo: "https://via.placeholder.com/300x300/667eea/ffffff?text=Jagojit+Chandro"
            },
            {
                id: 30,
                name: "Nuruzzaman Nahid",
                studentId: "250135",
                email: "",
                phone: "01865935058",
                photo: "https://via.placeholder.com/300x300/764ba2/ffffff?text=Nuruzzaman+Nahid"
            },
            {
                id: 31,
                name: "Sameeha Zahan Mridula",
                studentId: "250136",
                email: "",
                phone: "01950377978",
                photo: "https://via.placeholder.com/300x300/667eea/ffffff?text=Sameeha+Zahan"
            },
            {
                id: 32,
                name: "Mohd. Atiquzzaman Atiq",
                studentId: "250137",
                email: "",
                phone: "01331945616",
                photo: "https://via.placeholder.com/300x300/764ba2/ffffff?text=Atiquzzaman"
            },
            {
                id: 33,
                name: "Samin Yesar Tousib",
                studentId: "250138",
                email: "",
                phone: "01318009252",
                photo: "https://via.placeholder.com/300x300/667eea/ffffff?text=Samin+Yesar"
            },
            {
                id: 34,
                name: "Md. Iftekar Rahman",
                studentId: "250139",
                email: "riadraj009@gmail.com",
                phone: "01610077278",
                photo: "https://res.cloudinary.com/dcwnn9c0u/image/upload/v1766127478/d2guywowhf2g2qdntkli.jpg"
            },
            {
                id: 35,
                name: "Azizul Hoque Emon",
                studentId: "250140",
                email: "",
                phone: "01576688477",
                photo: "https://via.placeholder.com/300x300/667eea/ffffff?text=Azizul+Hoque"
            },
            {
                id: 36,
                name: "Mst. Johura Khatun",
                studentId: "250141",
                email: "",
                phone: "01752403522",
                photo: "https://via.placeholder.com/300x300/764ba2/ffffff?text=Johura+Khatun"
            }
        ];

        function renderStudents() {
            const grid = document.getElementById('studentGrid');
            grid.innerHTML = '';

            students.forEach(student => {
                const card = document.createElement('div');
                card.className = 'student-card';
                card.innerHTML = `
                    <div style="position: relative; overflow: hidden;">
                        <img src="${student.photo}" alt="${student.name}" class="student-photo" onerror="this.src='https://via.placeholder.com/300x300/667eea/ffffff?text=Student'">
                        <div class="photo-overlay"></div>
                    </div>
                    <div class="student-info">
                        <div class="student-name">${student.name}</div>
                        <div class="student-id">ID: ${student.studentId}</div>
                        ${student.phone ? `<div class="student-contact">📱 ${student.phone}</div>` : ''}
                        ${student.email ? `<div class="student-contact">📧 ${student.email}</div>` : ''}
                    </div>
                `;
                grid.appendChild(card);
            });
        }

        renderStudents();
    </script>
</body>
</html>
