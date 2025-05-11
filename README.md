<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Парные и непарные HTML-теги</title>
    <style>
        /* Общие стили */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #f8fcff, #e6f0fa);
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            padding: 20px;
            overflow: hidden;
            position: relative;
        }
        
        /* Летающие эмодзи */
        .floating-emoji {
            position: fixed;
            font-size: 24px;
            z-index: 1;
            pointer-events: none;
            opacity: 0.7;
            animation: float 15s infinite linear;
        }
        
        @keyframes float {
            0%, 100% {
                transform: translate(0, 0) rotate(0deg);
            }
            25% {
                transform: translate(20px, 20px) rotate(10deg);
            }
            50% {
                transform: translate(40px, 0) rotate(0deg);
            }
            75% {
                transform: translate(20px, -20px) rotate(-10deg);
            }
        }
        
        /* Позиции для эмодзи */
        .emoji1 { top: 10%; left: 5%; animation-duration: 18s; }
        .emoji2 { top: 20%; right: 5%; animation-duration: 22s; animation-delay: 2s; }
        .emoji3 { bottom: 15%; left: 10%; animation-duration: 20s; animation-delay: 1s; }
        .emoji4 { bottom: 25%; right: 8%; animation-duration: 25s; animation-delay: 3s; }
        .emoji5 { top: 30%; left: 8%; animation-duration: 17s; animation-delay: 4s; }
        .emoji6 { top: 15%; right: 10%; animation-duration: 19s; animation-delay: 5s; }
        
        /* Центральный контейнер */
        .main-container {
            width: 100%;
            max-width: 900px;
            background-color: white;
            border-radius: 15px;
            box-shadow: 0 5px 15px rgba(173, 216, 230, 0.3);
            overflow: hidden;
            display: flex;
            flex-direction: column;
            min-height: 600px;
            border: 1px solid #d1e3f6;
            position: relative;
            z-index: 10;
        }
        
        /* Остальные стили остаются без изменений */
        .header {
            background: linear-gradient(135deg, #a8c6fa, #e0e9ff);
            color: #2a4a7a;
            padding: 30px;
            text-align: center;
            border-bottom: 1px solid #d1e3f6;
        }
        
        .header h1 {
            font-size: 2.2rem;
            margin-bottom: 10px;
            text-shadow: 1px 1px 2px rgba(255,255,255,0.5);
        }
        
        .header p {
            color: #4a6b9b;
        }
        
        .navigation {
            display: flex;
            background-color: #f0f7ff;
            border-bottom: 1px solid #d1e3f6;
        }
        
        .nav-btn {
            flex: 1;
            text-align: center;
            padding: 15px;
            cursor: pointer;
            font-weight: 600;
            color: #4a6b9b;
            transition: all 0.3s;
            border-bottom: 3px solid transparent;
        }
        
        .nav-btn:hover {
            background-color: #e0e9ff;
            color: #2a4a7a;
        }
        
        .nav-btn.active {
            color: #2a4a7a;
            border-bottom: 3px solid #7aa1f7;
            background-color: white;
        }
        
        .content-area {
            flex: 1;
            padding: 30px;
            overflow-y: auto;
            display: none;
            background-color: white;
        }
        
        .content-area.active {
            display: block;
            animation: fadeIn 0.5s ease;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        
        h2 {
            color: #3a7bd5;
            margin-bottom: 20px;
            font-size: 1.6rem;
            border-bottom: 1px solid #e0e9ff;
            padding-bottom: 10px;
        }
        
        h3 {
            color: #4a6b9b;
            margin: 20px 0 10px;
            font-size: 1.3rem;
        }
        
        p {
            margin-bottom: 15px;
            line-height: 1.6;
            color: #555;
        }
        
        .code-example {
            background-color: #f8faff;
            border-left: 4px solid #a8c6fa;
            padding: 15px;
            margin: 15px 0;
            border-radius: 0 4px 4px 0;
            overflow-x: auto;
            border: 1px solid #e0e9ff;
        }
        
        code {
            font-family: 'Courier New', Courier, monospace;
            background-color: #f0f7ff;
            padding: 2px 5px;
            border-radius: 3px;
            color: #3a7bd5;
            border: 1px solid #d1e3f6;
        }
        
        table {
            width: 100%;
            border-collapse: collapse;
            margin: 20px 0;
            background-color: white;
            box-shadow: 0 2px 5px rgba(173, 216, 230, 0.2);
            border: 1px solid #e0e9ff;
        }
        
        th, td {
            border: 1px solid #e0e9ff;
            padding: 12px;
            text-align: left;
        }
        
        th {
            background-color: #f0f7ff;
            color: #3a7bd5;
        }
        
        tr:nth-child(even) {
            background-color: #f8faff;
        }
        
        tr:hover {
            background-color: #e6f0fa;
        }
        
        .highlight {
            background-color: #e6f0fa;
            padding: 2px 5px;
            border-radius: 3px;
            color: #3a7bd5;
            border: 1px dashed #a8c6fa;
        }
        
        .footer {
            text-align: center;
            padding: 15px;
            background-color: #f0f7ff;
            color: #7aa1f7;
            font-size: 0.9rem;
            border-top: 1px solid #d1e3f6;
        }
        
        @media (max-width: 768px) {
            .main-container {
                min-height: auto;
            }
            
            .header h1 {
                font-size: 1.8rem;
            }
            
            .navigation {
                flex-direction: column;
            }
            
            .nav-btn {
                padding: 12px;
                border-bottom: 1px solid #d1e3f6;
                border-left: 3px solid transparent;
                text-align: left;
            }
            
            .nav-btn.active {
                border-bottom: 1px solid #d1e3f6;
                border-left: 3px solid #7aa1f7;
            }
            
            .floating-emoji {
                font-size: 18px;
            }
        }
    </style>
</head>
<body>
    <!-- Летающие эмодзи -->
    <div class="floating-emoji emoji1">✨</div>
    <div class="floating-emoji emoji2">💻</div>
    <div class="floating-emoji emoji3">🔗</div>
    <div class="floating-emoji emoji4">📄</div>
    <div class="floating-emoji emoji5">🖥️</div>
    <div class="floating-emoji emoji6">🌐</div>
    
    <!-- Главный контейнер -->
    <div class="main-container">
        <!-- Шапка -->
        <div class="header">
            <h1>Парные и непарные HTML-теги</h1>
            <p>Интерактивное руководство по основам HTML</p>
        </div>
        
        <!-- Навигация -->
        <div class="navigation">
            <div class="nav-btn active" data-target="paired">Парные теги</div>
            <div class="nav-btn" data-target="unpaired">Непарные теги</div>
            <div class="nav-btn" data-target="difference">Различия</div>
            <div class="nav-btn" data-target="examples">Примеры</div>
        </div>
        
        <!-- Область контента -->
        <div id="paired" class="content-area active">
            <h2>Парные теги</h2>
            <p>Парные теги (или контейнерные теги) состоят из <strong>открывающего</strong> и <strong>закрывающего</strong> тегов, между которыми размещается содержимое.</p>
            
            <div class="code-example">
                &lt;открывающий_тег&gt;Содержимое&lt;/закрывающий_тег&gt;
            </div>
            
            <h3>Основные парные теги:</h3>
            
            <table>
                <tr>
                    <th>Тег</th>
                    <th>Описание</th>
                    <th>Пример</th>
                </tr>
                <tr>
                    <td><code>&lt;html&gt;&lt;/html&gt;</code></td>
                    <td>Корневой элемент HTML-документа</td>
                    <td><code>&lt;html&gt;...весь документ...&lt;/html&gt;</code></td>
                </tr>
                <tr>
                    <td><code>&lt;head&gt;&lt;/head&gt;</code></td>
                    <td>Содержит метаинформацию о документе</td>
                    <td><code>&lt;head&gt;&lt;title&gt;Заголовок&lt;/title&gt;&lt;/head&gt;</code></td>
                </tr>
                <tr>
                    <td><code>&lt;body&gt;&lt;/body&gt;</code></td>
                    <td>Содержит видимое содержимое страницы</td>
                    <td><code>&lt;body&gt;&lt;h1&gt;Заголовок&lt;/h1&gt;&lt;/body&gt;</code></td>
                </tr>
                <tr>
                    <td><code>&lt;div&gt;&lt;/div&gt;</code></td>
                    <td>Блочный контейнер для элементов</td>
                    <td><code>&lt;div&gt;Группа элементов&lt;/div&gt;</code></td>
                </tr>
                <tr>
                    <td><code>&lt;p&gt;&lt;/p&gt;</code></td>
                    <td>Абзац текста</td>
                    <td><code>&lt;p&gt;Это абзац.&lt;/p&gt;</code></td>
                </tr>
            </table>
            
            <p class="highlight">Важно: Закрывающий тег обычно совпадает с открывающим, но с добавлением слэша <code>/</code> перед именем тега.</p>
        </div>
        
        <div id="unpaired" class="content-area">
            <h2>Непарные теги</h2>
            <p>Непарные теги (или одиночные теги) не имеют закрывающего тега и обычно используются для вставки отдельных элементов или метаинформации.</p>
            
            <div class="code-example">
                &lt;тег&gt;  или  &lt;тег /&gt;
            </div>
            
            <h3>Основные непарные теги:</h3>
            
            <table>
                <tr>
                    <th>Тег</th>
                    <th>Описание</th>
                    <th>Пример</th>
                </tr>
                <tr>
                    <td><code>&lt;img&gt;</code></td>
                    <td>Вставка изображения</td>
                    <td><code>&lt;img src="image.jpg" alt="Описание"&gt;</code></td>
                </tr>
                <tr>
                    <td><code>&lt;br&gt;</code></td>
                    <td>Перенос строки</td>
                    <td><code>Текст&lt;br&gt;на новой строке</code></td>
                </tr>
                <tr>
                    <td><code>&lt;hr&gt;</code></td>
                    <td>Горизонтальная линия</td>
                    <td><code>&lt;hr&gt;</code></td>
                </tr>
                <tr>
                    <td><code>&lt;input&gt;</code></td>
                    <td>Поле ввода формы</td>
                    <td><code>&lt;input type="text"&gt;</code></td>
                </tr>
                <tr>
                    <td><code>&lt;meta&gt;</code></td>
                    <td>Метаинформация о документе</td>
                    <td><code>&lt;meta charset="UTF-8"&gt;</code></td>
                </tr>
            </table>
            
            <p>В XHTML одиночные теги записываются с закрывающим слэшем: <code>&lt;img /&gt;</code>, <code>&lt;br /&gt;</code>, но в HTML5 это необязательно.</p>
        </div>
        
        <div id="difference" class="content-area">
            <h2>Различия между парными и непарными тегами</h2>
            
            <table>
                <tr>
                    <th>Характеристика</th>
                    <th>Парные теги</th>
                    <th>Непарные теги</th>
                </tr>
                <tr>
                    <td>Синтаксис</td>
                    <td>Имеют открывающий и закрывающий тег</td>
                    <td>Состоят только из одного тега</td>
                </tr>
                <tr>
                    <td>Содержимое</td>
                    <td>Могут содержать текст или другие элементы</td>
                    <td>Не содержат содержимого</td>
                </tr>
                <tr>
                    <td>Назначение</td>
                    <td>Для структурирования и группировки контента</td>
                    <td>Для вставки отдельных элементов или метаинформации</td>
                </tr>
                <tr>
                    <td>Примеры</td>
                    <td><code>&lt;div&gt;</code>, <code>&lt;p&gt;</code>, <code>&lt;span&gt;</code></td>
                    <td><code>&lt;img&gt;</code>, <code>&lt;br&gt;</code>, <code>&lt;input&gt;</code></td>
                </tr>
            </table>
        </div>
        
        <div id="examples" class="content-area">
            <h2>Примеры использования</h2>
            
            <h3>Пример с парными тегами:</h3>
            <div class="code-example">
                &lt;!DOCTYPE html&gt;<br>
                &lt;html&gt;<br>
                &nbsp;&nbsp;&lt;head&gt;<br>
                &nbsp;&nbsp;&nbsp;&nbsp;&lt;title&gt;Моя страница&lt;/title&gt;<br>
                &nbsp;&nbsp;&lt;/head&gt;<br>
                &nbsp;&nbsp;&lt;body&gt;<br>
                &nbsp;&nbsp;&nbsp;&nbsp;&lt;h1&gt;Заголовок&lt;/h1&gt;<br>
                &nbsp;&nbsp;&nbsp;&nbsp;&lt;p&gt;Это абзац текста.&lt;/p&gt;<br>
                &nbsp;&nbsp;&lt;/body&gt;<br>
                &lt;/html&gt;
            </div>
            
            <h3>Пример с непарными тегами:</h3>
            <div class="code-example">
                &lt;!DOCTYPE html&gt;<br>
                &lt;html&gt;<br>
                &nbsp;&nbsp;&lt;head&gt;<br>
                &nbsp;&nbsp;&nbsp;&nbsp;&lt;meta charset="UTF-8"&gt;<br>
                &nbsp;&nbsp;&nbsp;&nbsp;&lt;title&gt;Страница с изображением&lt;/title&gt;<br>
                &nbsp;&nbsp;&lt;/head&gt;<br>
                &nbsp;&nbsp;&lt;body&gt;<br>
                &nbsp;&nbsp;&nbsp;&nbsp;&lt;h1&gt;Фотография&lt;/h1&gt;<br>
                &nbsp;&nbsp;&nbsp;&nbsp;&lt;img src="photo.jpg" alt="Мое фото"&gt;<br>
                &nbsp;&nbsp;&nbsp;&nbsp;&lt;p&gt;Первая строка&lt;br&gt;Вторая строка&lt;/p&gt;<br>
                &nbsp;&nbsp;&lt;/body&gt;<br>
                &lt;/html&gt;
            </div>
        </div>
        
        <!-- Подвал -->
        <div class="footer">
            © 2023 Руководство по HTML-тегам | Все права защищены
        </div>
    </div>

    <script>
        // JavaScript для переключения между разделами
        document.addEventListener('DOMContentLoaded', function() {
            const buttons = document.querySelectorAll('.nav-btn');
            const sections = document.querySelectorAll('.content-area');
            
            buttons.forEach(button => {
                button.addEventListener('click', function() {
                    // Удаляем активный класс у всех кнопок и секций
                    buttons.forEach(btn => btn.classList.remove('active'));
                    sections.forEach(section => section.classList.remove('active'));
                    
                    // Добавляем активный класс к текущей кнопке
                    this.classList.add('active');
                    
                    // Находим и показываем соответствующую секцию
                    const targetId = this.getAttribute('data-target');
                    document.getElementById(targetId).classList.add('active');
                });
            });
            
            // Дополнительная анимация для эмодзи
            const emojis = ['✨', '💻', '🔗', '📄', '🖥️', '🌐', '📝', '🔍', '💡', '🚀'];
            const floatingElements = document.querySelectorAll('.floating-emoji');
            
            floatingElements.forEach(el => {
                // Случайный эмодзи
                const randomEmoji = emojis[Math.floor(Math.random() * emojis.length)];
                el.textContent = randomEmoji;
                
                // Случайные параметры анимации
                const size = 20 + Math.random() * 15;
                const opacity = 0.5 + Math.random() * 0.4;
                const duration = 10 + Math.random() * 20;
                const delay = Math.random() * 5;
                
                el.style.fontSize = `${size}px`;
                el.style.opacity = opacity;
                el.style.animation = `float ${duration}s infinite ${delay}s linear`;
            });
        });
    </script>
</body>
</html>
