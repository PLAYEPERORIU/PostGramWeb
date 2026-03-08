<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>PostGram Web · небо, ветер, языки</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    html, body {
      height: 100%;
    }

    body {
      background: linear-gradient(145deg, #b0e0ff 0%, #4a90e2 100%);
      font-family: 'Segoe UI', Roboto, system-ui, sans-serif;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: flex-start;
      padding: 0 16px;
    }

    h1 {
      margin-top: 2.2rem;
      font-size: 2.4rem;
      font-weight: 500;
      letter-spacing: 1px;
      color: white;
      text-shadow: 0 4px 12px rgba(0, 20, 30, 0.5);
    }

    .lang-switcher {
      margin-top: 1.2rem;
      display: flex;
      flex-wrap: wrap;
      gap: 0.6rem;
      justify-content: center;
      padding: 0 8px;
      max-width: 700px;
    }

    .lang-switcher button {
      background: rgba(255, 255, 255, 0.2);
      backdrop-filter: blur(4px);
      -webkit-backdrop-filter: blur(4px);
      border: 1px solid rgba(255, 255, 255, 0.4);
      border-radius: 40px;
      padding: 0.5rem 1.2rem;
      font-size: 1rem;
      font-weight: 500;
      color: white;
      cursor: pointer;
      transition: background 0.2s, transform 0.1s, box-shadow 0.2s;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
      min-width: 90px;
      flex: 0 1 auto;
    }

    .lang-switcher button:hover {
      background: rgba(255, 255, 255, 0.35);
      box-shadow: 0 6px 12px rgba(0, 0, 0, 0.15);
    }

    .lang-switcher button:active {
      transform: scale(0.96);
    }

    .start-btn {
      margin-top: auto;
      margin-bottom: 3rem;
      background: #2ecc71;
      border: none;
      border-radius: 60px;
      padding: 1.2rem 3.8rem;
      font-size: 2.2rem;
      font-weight: 600;
      color: white;
      letter-spacing: 2px;
      cursor: pointer;
      box-shadow: 0 12px 24px rgba(0, 0, 0, 0.25), 0 4px 0 #1b7943;
      transition: all 0.15s ease;
      border: 1px solid rgba(255, 255, 255, 0.3);
      min-width: 240px;
      will-change: transform;
    }

    .start-btn:hover {
      background: #27ae60;
      transform: translateY(-3px);
      box-shadow: 0 18px 30px rgba(0, 0, 0, 0.3), 0 6px 0 #1b7943;
    }

    .start-btn:active {
      transform: translateY(4px);
      box-shadow: 0 6px 12px rgba(0, 0, 0, 0.2), 0 2px 0 #1b7943;
    }

    /* усиленный эффект ветра */
    .wind-effect {
      animation: strongWind 0.4s ease-out;
    }

    @keyframes strongWind {
      0% { transform: translateX(0) rotate(0deg); }
      15% { transform: translateX(8px) rotate(2deg); }
      30% { transform: translateX(-8px) rotate(-2deg); }
      45% { transform: translateX(6px) rotate(1.5deg); }
      60% { transform: translateX(-5px) rotate(-1.2deg); }
      75% { transform: translateX(3px) rotate(0.8deg); }
      90% { transform: translateX(-2px) rotate(-0.4deg); }
      100% { transform: translateX(0) rotate(0deg); }
    }

    @media (max-width: 600px) {
      h1 { font-size: 2rem; margin-top: 1.5rem; }
      .start-btn { font-size: 1.8rem; padding: 1rem 2.5rem; min-width: 200px; }
      .lang-switcher button { min-width: 70px; padding: 0.4rem 0.8rem; font-size: 0.9rem; }
    }
  </style>
</head>
<body>

  <h1>PostGram Web</h1>

  <!-- переключатель языков (7 языков) -->
  <div class="lang-switcher">
    <button data-i18n="lang_en" data-lang="en">English</button>
    <button data-i18n="lang_ru" data-lang="ru">Русский</button>
    <button data-i18n="lang_ua" data-lang="ua">Українська</button>
    <button data-i18n="lang_es" data-lang="es">Español</button>
    <button data-i18n="lang_de" data-lang="de">Deutsch</button>
    <button data-i18n="lang_fr" data-lang="fr">Français</button>
    <button data-i18n="lang_it" data-lang="it">Italiano</button>
  </div>

  <!-- большая зелёная кнопка START (внизу) -->
  <button class="start-btn" data-i18n="start">Start</button>

  <script>
    (function() {
      // ---------- переводы для 7 языков ----------
      const translations = {
        en: {
          lang_en: "English",
          lang_ru: "Russian",
          lang_ua: "Ukrainian",
          lang_es: "Spanish",
          lang_de: "German",
          lang_fr: "French",
          lang_it: "Italian",
          start: "Start"
        },
        ru: {
          lang_en: "Английский",
          lang_ru: "Русский",
          lang_ua: "Украинский",
          lang_es: "Испанский",
          lang_de: "Немецкий",
          lang_fr: "Французский",
          lang_it: "Итальянский",
          start: "Старт"
        },
        ua: {
          lang_en: "Англійська",
          lang_ru: "Російська",
          lang_ua: "Українська",
          lang_es: "Іспанська",
          lang_de: "Німецька",
          lang_fr: "Французька",
          lang_it: "Італійська",
          start: "Почати"
        },
        es: {
          lang_en: "Inglés",
          lang_ru: "Ruso",
          lang_ua: "Ucraniano",
          lang_es: "Español",
          lang_de: "Alemán",
          lang_fr: "Francés",
          lang_it: "Italiano",
          start: "Iniciar"
        },
        de: {
          lang_en: "Englisch",
          lang_ru: "Russisch",
          lang_ua: "Ukrainisch",
          lang_es: "Spanisch",
          lang_de: "Deutsch",
          lang_fr: "Französisch",
          lang_it: "Italienisch",
          start: "Start"
        },
        fr: {
          lang_en: "Anglais",
          lang_ru: "Russe",
          lang_ua: "Ukrainien",
          lang_es: "Espagnol",
          lang_de: "Allemand",
          lang_fr: "Français",
          lang_it: "Italien",
          start: "Démarrer"
        },
        it: {
          lang_en: "Inglese",
          lang_ru: "Russo",
          lang_ua: "Ucraino",
          lang_es: "Spagnolo",
          lang_de: "Tedesco",
          lang_fr: "Francese",
          lang_it: "Italiano",
          start: "Avvia"
        }
      };

      let currentLang = localStorage.getItem('pg_lang') || 'en';

      function setLanguage(lang) {
        if (!translations[lang]) return;
        currentLang = lang;
        localStorage.setItem('pg_lang', lang);

        document.querySelectorAll('[data-i18n]').forEach(el => {
          const key = el.getAttribute('data-i18n');
          if (translations[lang][key]) {
            el.textContent = translations[lang][key];
          }
        });
      }

      // установка языка при загрузке
      setLanguage(currentLang);

      // обработчик клика по кнопкам языков
      document.querySelector('.lang-switcher').addEventListener('click', (e) => {
        const langBtn = e.target.closest('button[data-lang]');
        if (langBtn) {
          setLanguage(langBtn.getAttribute('data-lang'));
        }
      });

      // усиленный эффект ветра на кнопке Start
      const startBtn = document.querySelector('.start-btn');
      startBtn.addEventListener('click', function() {
        this.classList.add('wind-effect');
        setTimeout(() => {
          this.classList.remove('wind-effect');
        }, 400);
      });
    })();
  </script>
</body>
</html>
