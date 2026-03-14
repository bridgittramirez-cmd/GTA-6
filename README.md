<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GTA VI | Los Santos & Blaine County</title>
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; font-family: 'Inter', sans-serif; }
        body { background-color: #0b0b0b; color: #fff; overflow-x: hidden; }

        /* Background Styling */
        .hero {
            height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            background: linear-gradient(rgba(0,0,0,0.6), rgba(0,0,0,0.6)), 
                        url('https://images.alphacoders.com'); /* Los Santos Placeholder */
            background-size: cover;
            background-position: center;
            text-align: center;
        }

        .logo-vi {
            font-size: clamp(5rem, 15vw, 12rem);
            font-weight: 900;
            background: linear-gradient(45deg, #f093fb 0%, #f5576c 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            filter: drop-shadow(0 0 20px rgba(245, 87, 108, 0.4));
        }

        .subtitle { font-size: 1.2rem; letter-spacing: 5px; text-transform: uppercase; margin-top: -20px; }

        /* Protagonist Section */
        .protagonists {
            display: flex;
            justify-content: center;
            gap: 20px;
            padding: 50px;
            background: #111;
        }

        .char-card {
            flex: 1;
            max-width: 300px;
            padding: 20px;
            border-top: 4px solid #ff758c;
            background: #1a1a1a;
            transition: transform 0.3s;
        }

        .char-card:hover { transform: translateY(-10px); background: #222; }
        .char-name { font-weight: bold; color: #ff758c; margin-bottom: 10px; }
        .char-desc { font-size: 0.9rem; line-height: 1.5; opacity: 0.8; }

        /* Launch Info */
        .launch-footer {
            padding: 40px;
            text-align: center;
            background: #000;
            border-top: 1px solid #333;
        }

        .btn-preorder {
            display: inline-block;
            padding: 15px 40px;
            background: #fff;
            color: #000;
            text-decoration: none;
            font-weight: bold;
            border-radius: 5px;
            margin-top: 20px;
        }
    </style>
</head>
<body>

    <section class="hero">
        <h1 class="logo-vi">VI</h1>
        <p class="subtitle">Return to Los Santos</p>
    </section>

    <section class="protagonists">
        <div class="char-card">
            <div class="char-name">MICHAEL</div>
            <p class="char-desc">The retired bank robber living a hollow luxury life in Rockford Hills.</p>
        </div>
        <div class="char-card">
            <div class="char-name">FRANKLIN</div>
            <p class="char-desc">The street hustler looking for real opportunities in a city of dreams.</p>
        </div>
        <div class="char-card">
            <div class="char-name">TREVOR</div>
            <p class="char-desc">The unpredictable loose cannon ruling the deserts of Blaine County.</p>
        </div>
    </section>

    <footer class="launch-footer">
        <h2>NOVEMBER 19, 2026</h2>
        <p>Experience the ultimate criminal playground.</p>
        <a href="#" class="btn-preorder">WATCH TRAILER</a>
    </footer>

</body>
</html>

