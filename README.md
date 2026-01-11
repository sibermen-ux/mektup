<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Sana Özel 25 Şiir 💜</title>
    <link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@600&family=Poppins:wght@300;400&display=swap" rel="stylesheet">
    <style>
        :root {
            --purple-dark: #2d1b4e;
            --purple-light: #6a4c93;
            --romantic-bg: linear-gradient(135deg, #1a0a2e 0%, #4a148c 50%, #7b1fa2 100%);
            --letter-bg: #fffcf2;
        }

        body, html {
            margin: 0; padding: 0; width: 100%; height: 100%;
            font-family: 'Poppins', sans-serif;
            background: var(--romantic-bg);
            color: white;
            background-attachment: fixed;
            overflow-x: hidden;
            -webkit-tap-highlight-color: transparent;
        }

        /* Kilit Ekranı */
        #lock-screen {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            background: var(--romantic-bg);
            display: flex; flex-direction: column; justify-content: center; align-items: center;
            z-index: 1000; transition: opacity 0.8s ease, visibility 0.8s;
        }

        .lock-container { text-align: center; padding: 20px; }
        .lock-container h2 { font-family: 'Dancing Script', cursive; font-size: 2.2rem; margin-bottom: 10px; }
        
        input[type="password"] {
            padding: 15px; border-radius: 30px; border: 1px solid rgba(255,255,255,0.3);
            text-align: center; font-size: 1.2rem; width: 180px;
            background: rgba(255,255,255,0.1); color: white; outline: none;
            backdrop-filter: blur(5px); margin-bottom: 20px;
        }

        /* Devam Butonu */
        .btn-unlock {
            padding: 12px 35px; border-radius: 30px; border: none;
            background: var(--purple-light); color: white;
            font-size: 1rem; cursor: pointer; font-family: 'Poppins';
            box-shadow: 0 4px 15px rgba(0,0,0,0.3);
            transition: 0.3s; display: block; margin: 0 auto;
        }
        .btn-unlock:active { transform: scale(0.95); background: #8e24aa; }

        /* Ana İçerik */
        #main-content {
            display: none; opacity: 0; transition: opacity 1s;
            padding: 40px 15px; max-width: 800px; margin: 0 auto; text-align: center;
        }

        h1 { font-family: 'Dancing Script', cursive; font-size: 2.3rem; margin-bottom: 40px; }

        .letters-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(130px, 1fr));
            gap: 20px; padding-bottom: 50px;
        }

        .envelope-container { cursor: pointer; }

        .envelope {
            background: #f3e5f5; height: 110px; border-radius: 12px;
            display: flex; flex-direction: column; justify-content: center; align-items: center;
            box-shadow: 0 8px 20px rgba(0,0,0,0.4); transition: 0.3s ease;
            color: var(--purple-dark);
        }

        .envelope:active { transform: scale(0.95); }
        .envelope span { font-size: 2.2rem; }
        .envelope-no { font-weight: bold; font-size: 0.8rem; margin-top: 5px; opacity: 0.7; }

        .modal {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            background: rgba(0,0,0,0.9); display: none;
            justify-content: center; align-items: center; z-index: 2000;
        }

        .kiss-emoji {
            font-size: 8rem; display: none;
            animation: kiss-anim 1.2s ease-in-out forwards;
            position: absolute;
        }

        .letter-content {
            background: var(--letter-bg); color: #333; padding: 40px 25px;
            border-radius: 15px; width: 85%; max-width: 450px;
            display: none; text-align: center; box-shadow: 0 20px 60px rgba(0,0,0,0.5);
            max-height: 80vh; overflow-y: auto;
        }

        @keyframes kiss-anim {
            0% { transform: scale(0.2); opacity: 0; }
            45% { transform: scale(1.4); opacity: 1; }
            100% { transform: scale(1.6); opacity: 0; }
        }

        .close-btn {
            margin-top: 25px; padding: 12px 30px; font-family: 'Poppins';
            background: var(--purple-light); color: white; border: none; border-radius: 25px;
            cursor: pointer;
        }

        @media (max-width: 480px) {
            .letters-grid { grid-template-columns: repeat(2, 1fr); gap: 15px; }
            h1 { font-size: 1.6rem; }
        }
    </style>
</head>
<body onload="document.getElementById('passInput').focus()">

    <div id="lock-screen">
        <div class="lock-container">
            <h2>🔒 Bu site sana özel</h2>
            <p style="margin-bottom: 25px; font-size: 0.9rem; opacity: 0.9;">Şifre: Sevgili olduğumuz gün 💜</p>
            <form onsubmit="event.preventDefault(); validatePassword();">
                <input type="password" id="passInput" placeholder="Şifre" maxlength="4" autocomplete="off">
                <button type="submit" class="btn-unlock">Giriş Yap 💜</button>
            </form>
            <p id="error-msg" style="color: #ff8a80; font-size: 0.8rem; margin-top: 15px; display: none;">Hatalı şifre, tekrar dene sevgilim..</p>
        </div>
    </div>

    <div id="main-content">
        <h1>Kalbimden Sana Yazdığım Mektuplar 💌</h1>
        <div class="letters-grid" id="lettersGrid"></div>
    </div>

    <div id="letterModal" class="modal" onclick="closeModal()">
        <div id="kiss" class="kiss-emoji">😘</div>
        <div id="letterBody" class="letter-content" onclick="event.stopPropagation()">
            <div id="letterText" style="white-space: pre-line; font-size: 1.2rem; line-height: 1.7; font-family: 'Dancing Script', cursive;"></div>
            <button class="close-btn" onclick="closeModal()">Kapat 💜</button>
        </div>
    </div>

    <script>
        const letterMessages = {
            1: "Sen gelince içime\ndünya duruyor.\nKalbim ilk kez\nyerini buluyor.",
            2: "Aşk büyük laflar değil,\nküçük anlar.\nYanında olmak\nher şeye yeter.",
            3: "Elini tuttuğumda\nzaman unutuyor.\nGelecek korkmuyor,\nkalbim biliyor.",
            4: "Adını fısıldayınca\niçim sakin.\nBu kadar huzur\ntesadüf değil.",
            5: "Yanında susmak\nen güzel cümle.\nSana bakmak\nher şeye cevap.",
            6: "Gülüşün değince\ngün aydınlanır.\nKalbim seni\nezbere tanır.",
            7: "Ben seni severken\nacele etmem.\nÇünkü aşk\nyavaş anlaşılır.",
            8: "Gözlerin bakınca\nher şey durur.\nKalbim sessizce\nsana tutulur.",
            9: "Aşk seninle\nhafif bir şey.\nKalbim yükünü\nsana bırakır.",
            10: "Yanında olmak\nyeter bana.\nDünya büyük değil,\nsen varken.",
            11: "Adın geçince\niçimde bahar.\nBu kalp\nsana karar.",
            12: "Elin elimdeyken\nyalnız değilim.\nKalbim ilk kez\nkendine emin.",
            13: "Seni sevmek\nkendimi bulmak.\nKalbimin yolunu\nsende tamamlamak.",
            14: "Aşk bazen\nhiç konuşmamak.\nSadece aynı anda\ngülümsemek.",
            15: "Sen yanımdayken\nher şey doğru.\nKalbim artık\nsana ait, olduğu gibi.",
            16: "Bir bakışın\nyeter bana.\nAşk dediğin\nbir anda anlama.",
            17: "Seni düşünmek\nsessiz bir mutluluk.\nKalbim\nsana alışık.",
            18: "Yanında olmak\ngüvende hissetmek.\nKalbimin en sakin\yerinde durmak.",
            19: "Adın kalbimde\nkırılmadan durur.\nAşk seninle\nincitmeden olur.",
            20: "Ben seni\nyük olmadan severim.\nKalbimi sana\nhafifçe veririm.",
            21: "Sen gülünce\niçim rahat.\nAşk bazen\nbu kadar basit.",
            22: "Kalbim seninle\nkendini buldu.\nAşk dediğin\nsessizce oldu.",
            23: "Yanında zaman\nacele etmez.\nKalbim senden\nbaşkasını seçmez.",
            24: "Seni sevmek\nalışmak değil.\nHer gün yeniden\nseçmek gibi.",
            25: "Kalbim sana\nyüksek sesle değil,\nusulca\n“evim” dedi."
        };

        const grid = document.getElementById('lettersGrid');
        for (let i = 1; i <= 25; i++) {
            const container = document.createElement('div');
            container.className = 'envelope-container';
            container.onclick = () => openLetter(i);
            container.innerHTML = <div class="envelope"><span>💌</span><div class="envelope-no">Mektup ${i}</div></div>;
            grid.appendChild(container);
        }

        // Şifre Doğrulama Fonksiyonu
        function validatePassword() {
            const input = document.getElementById('passInput');
            const error = document.getElementById('error-msg');
            
            if (input.value === "0325") {
                error.style.display = 'none';
                const lock = document.getElementById('lock-screen');
                const main = document.getElementById('main-content');
                lock.style.opacity = '0';
                setTimeout(() => {
                    lock.style.display = 'none';
                    main.style.display = 'block';
                    setTimeout(() => main.style.opacity = '1', 50);
                }, 800);
            } else {
                error.style.display = 'block';
                input.value = "";
                input.focus();
            }
        }

        function openLetter(num) {
            const modal = document.getElementById('letterModal');
            const kiss = document.getElementById('kiss');
            const body = document.getElementById('letterBody');
            const text = document.getElementById('letterText');

            document.body.style.overflow = 'hidden'; 
            text.innerText = letterMessages[num];
            modal.style.display = 'flex';
            kiss.style.display = 'block';
            body.style.display = 'none';

            setTimeout(() => {
                kiss.style.display = 'none';
                body.style.display = 'block';
            }, 1000);
        }

        function closeModal() {
            document.body.style.overflow = 'auto'; 
            document.getElementById('letterModal').style.display = 'none';
        }
    </script>
</body>
</html>
