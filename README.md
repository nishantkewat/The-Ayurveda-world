<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>The Ayurveda World | Official</title>
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; }
        body { 
            font-family: 'Arial', sans-serif; 
            background: #f5f5f5; 
            line-height: 1.6;
        }
        .header {
            background: linear-gradient(135deg, #059669, #10b981);
            color: white;
            padding: 30px 20px;
            text-align: center;
            box-shadow: 0 4px 12px rgba(0,0,0,0.1);
        }
        .header h1 {
            font-size: 2.5rem;
            margin-bottom: 10px;
        }
        .header p {
            font-size: 1.2rem;
            opacity: 0.9;
        }
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }
        .main-content {
            background: white;
            border-radius: 15px;
            padding: 40px;
            margin: 40px auto;
            box-shadow: 0 4px 20px rgba(0,0,0,0.08);
            max-width: 800px;
        }
        .owner-card {
            background: linear-gradient(135deg, #d1fae5, #a7f3d0);
            border: 2px solid #10b981;
            border-radius: 12px;
            padding: 25px;
            margin: 25px 0;
        }
        .owner-card h3 {
            color: #065f46;
            margin-bottom: 15px;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        .features-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin: 30px 0;
        }
        .feature {
            background: #f8fafc;
            padding: 25px;
            border-radius: 12px;
            text-align: center;
            border: 1px solid #e2e8f0;
            transition: transform 0.3s ease;
        }
        .feature:hover {
            transform: translateY(-5px);
        }
        .feature h4 {
            color: #059669;
            margin-bottom: 10px;
            font-size: 1.3rem;
        }
        .cta-button {
            background: linear-gradient(135deg, #059669, #10b981);
            color: white;
            border: none;
            padding: 18px 40px;
            font-size: 1.2rem;
            border-radius: 50px;
            cursor: pointer;
            width: 100%;
            margin-top: 20px;
            transition: all 0.3s ease;
            box-shadow: 0 4px 15px rgba(5, 150, 105, 0.3);
        }
        .cta-button:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(5, 150, 105, 0.4);
        }
        .footer {
            text-align: center;
            padding: 30px;
            color: #64748b;
            margin-top: 50px;
        }
        @media (max-width: 768px) {
            .header h1 { font-size: 2rem; }
            .main-content { padding: 25px; margin: 20px; }
            .features-grid { grid-template-columns: 1fr; }
        }
    </style>
</head>
<body>
    <!-- Header -->
    <header class="header">
        <h1>🌿 The Ayurveda World</h1>
        <p>Ancient Wisdom for Modern Wellness</p>
    </header>

    <!-- Main Content -->
    <div class="container">
        <div class="main-content">
            <h2 style="color: #059669; border-bottom: 3px solid #10b981; padding-bottom: 15px; margin-bottom: 25px;">
                Welcome to Our Ayurvedic Store
            </h2>
            
            <!-- Owner Information -->
            <div class="owner-card">
                <h3>👑 Official Owner</h3>
                <p><strong>Email:</strong> theayurvedaworldofficial@gmail.com</p>
                <p><strong>Role:</strong> Supreme Administrator</p>
                <p><strong>Status:</strong> 🟢 Verified & Active</p>
            </div>

            <!-- Features -->
            <div class="features-grid">
                <div class="feature">
                    <h4>🛍️ Ayurvedic Products</h4>
                    <p>Authentic Herbs, Oils, Supplements & Personal Care</p>
                </div>
                <div class="feature">
                    <h4>🚚 Free Shipping</h4>
                    <p>Fast Delivery Across India</p>
                </div>
                <div class="feature">
                    <h4>📞 Expert Support</h4>
                    <p>24/7 Customer Care & Ayurvedic Guidance</p>
                </div>
                <div class="feature">
                    <h4>🌱 Pure & Natural</h4>
                    <p>100% Authentic Ayurvedic Formulations</p>
                </div>
            </div>

            <!-- Call to Action -->
            <button class="cta-button">
                🛒 Start Your Ayurvedic Journey Now
            </button>
        </div>
    </div>

    <!-- Footer -->
    <footer class="footer">
        <p>© 2024 The Ayurveda World. All rights reserved.</p>
        <p style="margin-top: 10px; font-size: 0.9rem;">
            Empowering Wellness Through Ancient Ayurvedic Wisdom
        </p>
    </footer>
</body>
</html>
