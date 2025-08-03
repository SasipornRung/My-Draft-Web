<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PropDecoded - แพลตฟอร์มวิเคราะห์อสังหาฯ ด้วย AI</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
            color: #333;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        /* Navigation */
        nav {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            position: fixed;
            top: 0;
            width: 100%;
            z-index: 1000;
            box-shadow: 0 2px 20px rgba(0,0,0,0.1);
        }

        .nav-container {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 1rem 2rem;
        }

        .logo {
            font-size: 1.8rem;
            font-weight: bold;
            color: #4c63d2;
            text-decoration: none;
        }

        .nav-menu {
            display: flex;
            list-style: none;
            gap: 2rem;
        }

        .nav-menu a {
            text-decoration: none;
            color: #333;
            font-weight: 500;
            transition: color 0.3s ease;
            cursor: pointer;
        }

        .nav-menu a:hover {
            color: #4c63d2;
        }

        /* Hero Section */
        .hero {
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            color: white;
            position: relative;
            overflow: hidden;
        }

        .hero::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: rgba(0,0,0,0.3);
        }

        .hero-content {
            position: relative;
            z-index: 2;
            max-width: 800px;
            animation: fadeInUp 1s ease-out;
        }

        .hero h1 {
            font-size: 3.5rem;
            margin-bottom: 1rem;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
        }

        .hero p {
            font-size: 1.3rem;
            margin-bottom: 2rem;
            opacity: 0.9;
        }

        .cta-button {
            display: inline-block;
            background: linear-gradient(45deg, #ff6b6b, #ee5a24);
            color: white;
            padding: 15px 40px;
            border-radius: 50px;
            text-decoration: none;
            font-weight: bold;
            font-size: 1.1rem;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            box-shadow: 0 5px 15px rgba(255, 107, 107, 0.4);
        }

        .cta-button:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 25px rgba(255, 107, 107, 0.6);
        }

        /* Sections */
        .section {
            padding: 80px 0;
            background: white;
        }

        .section:nth-child(even) {
            background: #f8f9ff;
        }

        .section h2 {
            text-align: center;
            font-size: 2.5rem;
            margin-bottom: 3rem;
            color: #4c63d2;
        }

        .features-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
            margin-top: 3rem;
        }

        .feature-card {
            background: white;
            padding: 2rem;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.1);
            text-align: center;
            transition: transform 0.3s ease;
        }

        .feature-card:hover {
            transform: translateY(-10px);
        }

        .feature-icon {
            width: 80px;
            height: 80px;
            background: linear-gradient(45deg, #4c63d2, #764ba2);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 0 auto 1rem;
            font-size: 2rem;
            color: white;
        }

        .analysis-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 2rem;
            margin-top: 2rem;
        }

        .analysis-item {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 2rem;
            border-radius: 15px;
            text-align: center;
        }

        .analysis-item h4 {
            font-size: 1.3rem;
            margin-bottom: 1rem;
        }

        .system-features {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 2rem;
            margin-top: 2rem;
        }

        .system-card {
            background: white;
            border: 2px solid #e1e8ff;
            border-radius: 15px;
            padding: 2rem;
            transition: border-color 0.3s ease, transform 0.3s ease;
        }

        .system-card:hover {
            border-color: #4c63d2;
            transform: translateY(-5px);
        }

        .system-card h4 {
            color: #4c63d2;
            font-size: 1.4rem;
            margin-bottom: 1rem;
        }

        /* Contact Form */
        .contact-form {
            max-width: 600px;
            margin: 0 auto;
            background: white;
            padding: 3rem;
            border-radius: 20px;
            box-shadow: 0 15px 40px rgba(0,0,0,0.1);
        }

        .form-group {
            margin-bottom: 1.5rem;
        }

        .form-group label {
            display: block;
            margin-bottom: 0.5rem;
            color: #4c63d2;
            font-weight: bold;
        }

        .form-group input,
        .form-group textarea {
            width: 100%;
            padding: 12px;
            border: 2px solid #e1e8ff;
            border-radius: 10px;
            font-size: 1rem;
            transition: border-color 0.3s ease;
        }

        .form-group input:focus,
        .form-group textarea:focus {
            outline: none;
            border-color: #4c63d2;
        }

        .submit-btn {
            background: linear-gradient(45deg, #4c63d2, #764ba2);
            color: white;
            padding: 15px 40px;
            border: none;
            border-radius: 50px;
            font-size: 1.1rem;
            font-weight: bold;
            cursor: pointer;
            transition: transform 0.3s ease;
            width: 100%;
        }

        .submit-btn:hover {
            transform: translateY(-2px);
        }

        /* Footer */
        footer {
            background: #2c3e50;
            color: white;
            text-align: center;
            padding: 2rem 0;
        }

        /* Animations */
        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .fade-in {
            opacity: 0;
            transform: translateY(30px);
            transition: all 0.6s ease;
        }

        .fade-in.visible {
            opacity: 1;
            transform: translateY(0);
        }

        /* Responsive */
        @media (max-width: 768px) {
            .nav-menu {
                display: none;
            }
            
            .hero h1 {
                font-size: 2.5rem;
            }
            
            .hero p {
                font-size: 1.1rem;
            }
        }
    </style>
</head>
<body>
    <!-- Navigation -->
    <nav>
        <div class="nav-container">
            <a href="#home" class="logo">PropDecoded</a>
            <ul class="nav-menu">
                <li><a href="#home">หน้าแรก</a></li>
                <li><a href="#about">เกี่ยวกับเรา</a></li>
                <li><a href="#analysis">บทวิเคราะห์</a></li>
                <li><a href="#system">ระบบวิเคราะห์</a></li>
                <li><a href="#contact">ติดต่อเรา</a></li>
            </ul>
        </div>
    </nav>

    <!-- Hero Section -->
    <section id="home" class="hero">
        <div class="hero-content">
            <h1>PropDecoded</h1>
            <p>แพลตฟอร์มวิเคราะห์อสังหาริมทรัพย์ด้วย AI<br>
            ช่วยให้นักลงทุนหาห้องที่ "น่าลงทุน" และคาดการณ์ ROI หลังรีโนเวทได้อย่างแม่นยำ</p>
            <a href="#system" class="cta-button">เริ่มวิเคราะห์เลย</a>
        </div>
    </section>

    <!-- About Section -->
    <section id="about" class="section">
        <div class="container">
            <h2>เกี่ยวกับเรา</h2>
            <div class="features-grid">
                <div class="feature-card fade-in">
                    <div class="feature-icon">🎯</div>
                    <h3>วิสัยทัศน์</h3>
                    <p>สร้างระบบที่เปิดเผยความเสี่ยงและโอกาสอย่างโปร่งใส เพื่อให้นักลงทุนตัดสินใจได้อย่างมีข้อมูล โดยไม่ชี้นำผิดกฎหมาย</p>
                </div>
                <div class="feature-card fade-in">
                    <div class="feature-icon">💡</div>
                    <h3>ที่มา</h3>
                    <p>เกิดจากความต้องการในตลาดอสังหาฯ ที่ขาดเครื่องมือวิเคราะห์ที่แม่นยำ เราจึงพัฒนา AI ที่สามารถวิเคราะห์ข้อมูลหลากหลายมิติ</p>
                </div>
                <div class="feature-card fade-in">
                    <div class="feature-icon">👥</div>
                    <h3>ทีมงาน</h3>
                    <p>ทีมผู้เชี่ยวชาญด้าน AI, Data Science และอสังหาฯ ที่มีประสบการณ์รวมกันกว่า 20 ปี ในการวิเคราะห์และลงทุน</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Analysis Section -->
    <section id="analysis" class="section">
        <div class="container">
            <h2>บทวิเคราะห์</h2>
            <p style="text-align: center; font-size: 1.2rem; margin-bottom: 2rem;">
                ตัวอย่างการวิเคราะห์และอินไซต์ที่คุณจะได้รับ
            </p>
            <div class="analysis-grid">
                <div class="analysis-item fade-in">
                    <h4>🏢 วิเคราะห์รีวิว</h4>
                    <p>AI อ่านและวิเคราะห์รีวิวจากผู้อยู่อาศัยจริง เพื่อหาจุดแข็ง-จุดอ่อนของอาคาร สิ่งอำนวยความสะดวก และปัญหาที่อาจเกิดขึ้น</p>
                </div>
                <div class="analysis-item fade-in">
                    <h4>📊 ข้อมูลราคา</h4>
                    <p>ติดตามและวิเคราะห์แนวโน้มราคาย้อนหลัง 5 ปี พร้อมคาดการณ์การเปลี่ยนแปลงในอนาคต</p>
                </div>
                <div class="analysis-item fade-in">
                    <h4>🗺️ ทำเลและผังเมือง</h4>
                    <p>วิเคราะห์ทำเลจากผังเมือง แผนการพัฒนาเมือง การคมนาคม และโครงสร้างพื้นฐานในอนาคต</p>
                </div>
                <div class="analysis-item fade-in">
                    <h4>💰 ROI Prediction</h4>
                    <p>คาดการณ์ผลตอบแทนหลังรีโนเวท โดยพิจารณาต้นทุนการปรับปรุง และมูลค่าที่เพิ่มขึ้น</p>
                </div>
            </div>
        </div>
    </section>

    <!-- System Section -->
    <section id="system" class="section">
        <div class="container">
            <h2>ระบบวิเคราะห์</h2>
            <div class="system-features">
                <div class="system-card fade-in">
                    <h4>📈 ประเมิน ROI</h4>
                    <p>คำนวณผลตอบแทนการลงทุนที่คาดหวัง โดยพิจารณาจากราคาปัจจุบัน ต้นทุนรีโนเวท และแนวโน้มตลาด</p>
                    <button style="margin-top: 1rem; background: #4c63d2; color: white; border: none; padding: 10px 20px; border-radius: 20px; cursor: pointer;">ทดลองใช้</button>
                </div>
                <div class="system-card fade-in">
                    <h4>⚠️ วิเคราะห์ความเสี่ยง</h4>
                    <p>ประเมินความเสี่ยงด้านต่างๆ เช่น การขาดสภาพคล่อง ปัญหาโครงสร้าง หรือการเปลี่ยนแปลงของทำเล</p>
                    <button style="margin-top: 1rem; background: #4c63d2; color: white; border: none; padding: 10px 20px; border-radius: 20px; cursor: pointer;">ดูรายละเอียด</button>
                </div>
                <div class="system-card fade-in">
                    <h4>🌊 วัดระยะใกล้คลอง</h4>
                    <p>วิเคราะห์ระยะห่างและความเสี่ยงจากแหล่งน้ำ รวมถึงผลกระทบต่อราคาและความน่าอยู่</p>
                    <button style="margin-top: 1rem; background: #4c63d2; color: white; border: none; padding: 10px 20px; border-radius: 20px; cursor: pointer;">เช็คทำเล</button>
                </div>
                <div class="system-card fade-in">
                    <h4>🚇 ความใกล้ชิดขนส่งสาธารณะ</h4>
                    <p>วิเคราะห์การเข้าถึงระบบขนส่งสาธารณะ และผลกระทบต่อมูลค่าอสังหาริมทรัพย์</p>
                    <button style="margin-top: 1rem; background: #4c63d2; color: white; border: none; padding: 10px 20px; border-radius: 20px; cursor: pointer;">หาเส้นทาง</button>
                </div>
                <div class="system-card fade-in">
                    <h4>🏗️ แผนการพัฒนา</h4>
                    <p>ติดตามโครงการพัฒนาในอนาคตที่อาจส่งผลต่อมูลค่าอสังหาฯ ในบริเวณใกล้เคียง</p>
                    <button style="margin-top: 1rem; background: #4c63d2; color: white; border: none; padding: 10px 20px; border-radius: 20px; cursor: pointer;">ดูแผนที่</button>
                </div>
                <div class="system-card fade-in">
                    <h4>🔮 AI Insights</h4>
                    <p>ข้อมูลเชิงลึกจาก AI ที่วิเคราะห์ปัจจัยหลากหลายมิติ เพื่อให้คำแนะนำที่ครอบคลุม</p>
                    <button style="margin-top: 1rem; background: #4c63d2; color: white; border: none; padding: 10px 20px; border-radius: 20px; cursor: pointer;">ดู AI Report</button>
                </div>
            </div>
        </div>
    </section>

    <!-- Contact Section -->
    <section id="contact" class="section">
        <div class="container">
            <h2>ติดต่อเรา</h2>
            <div class="contact-form fade-in">
                <form>
                    <div class="form-group">
                        <label for="name">ชื่อ-นามสกุล</label>
                        <input type="text" id="name" name="name" required>
                    </div>
                    <div class="form-group">
                        <label for="email">อีเมล</label>
                        <input type="email" id="email" name="email" required>
                    </div>
                    <div class="form-group">
                        <label for="phone">เบอร์โทรศัพท์</label>
                        <input type="tel" id="phone" name="phone">
                    </div>
                    <div class="form-group">
                        <label for="interest">ความสนใจ</label>
                        <select id="interest" name="interest" style="width: 100%; padding: 12px; border: 2px solid #e1e8ff; border-radius: 10px;">
                            <option value="">เลือกความสนใจ</option>
                            <option value="individual">นักลงทุนรายบุคคล</option>
                            <option value="business">ธุรกิจ/องค์กร</option>
                            <option value="partner">ความร่วมมือ</option>
                            <option value="other">อื่นๆ</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label for="message">ข้อความ</label>
                        <textarea id="message" name="message" rows="5" placeholder="บอกเราถึงความต้องการของคุณ..."></textarea>
                    </div>
                    <button type="submit" class="submit-btn">ส่งข้อความ</button>
                </form>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer>
        <div class="container">
            <p>&copy; 2025 PropDecoded. All rights reserved. | ระบบวิเคราะห์อสังหาฯ ด้วย AI</p>
        </div>
    </footer>

    <script>
        // Smooth scrolling
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({
                        behavior: 'smooth',
                        block: 'start'
                    });
                }
            });
        });

        // Fade in animation on scroll
        const observerOptions = {
            threshold: 0.1,
            rootMargin: '0px 0px -50px 0px'
        };

        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('visible');
                }
            });
        }, observerOptions);

        document.querySelectorAll('.fade-in').forEach(el => {
            observer.observe(el);
        });

        // Form submission
        document.querySelector('form').addEventListener('submit', function(e) {
            e.preventDefault();
            alert('ขอบคุณสำหรับข้อความของคุณ! เราจะติดต่อกลับภายใน 24 ชั่วโมง');
            this.reset();
        });

        // Button interactions
        document.querySelectorAll('button').forEach(button => {
            button.addEventListener('click', function() {
                if (this.textContent.includes('ทดลองใช้')) {
                    alert('ฟีเจอร์ประเมิน ROI กำลังจะเปิดให้บริการเร็วๆนี้!');
                } else if (this.textContent.includes('ดูรายละเอียด')) {
                    alert('ระบบวิเคราะห์ความเสี่ยงจะช่วยให้คุณเห็นปัจจัยเสี่ยงทั้งหมด');
                } else if (this.textContent.includes('เช็คทำเล')) {
                    alert('ระบบจะแสดงแผนที่และระยะห่างจากแหล่งน้ำ');
                } else if (this.textContent.includes('หาเส้นทาง')) {
                    alert('ระบบจะแสดงเส้นทางและเวลาเดินทางไปยังสถานีขนส่งสาธารณะ');
                } else if (this.textContent.includes('ดูแผนที่')) {
                    alert('แสดงโครงการพัฒนาทั้งหมดในรัศมี 5 กิโลเมตร');
                } else if (this.textContent.includes('ดู AI Report')) {
                    alert('รายงานสรุปจาก AI พร้อมคำแนะนำการลงทุน');
                }
            });
        });
    </script>
</body>
</html>
