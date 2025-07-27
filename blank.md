<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <!-- 模板使用提示: 1. 修改这里的标题 -->
    <title>文章标题 - Enceladus Blog</title>
    
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;700&family=Noto+Sans+SC:wght@300;400;700&display=swap" rel="stylesheet">
    
    <!-- 如果您的文章不需要数学公式，可以移除下面这两段 script -->
    <script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>
    <script>
      MathJax = {
        tex: {
          inlineMath: [['$', '$'], ['\\(', '\\)']]
        }
      };
    </script>
    
    <style>
        /* --- 默认 (白天) 模式颜色 --- */
        :root {
            --bg-color: #f8f9fa;
            --text-color: #212529;
            --primary-color: #4a90e2;
            --secondary-color: #f5a623;
            --card-bg-color: #ffffff;
            --border-color: #dee2e6;
            --header-bg: #2c3e50;
            --header-text: #ecf0f1;
            --text-muted: #6c757d;
            --card-shadow: rgba(0,0,0,0.05);
            --article-title-color: #333;
        }

        /* --- 黑夜模式下的颜色 --- */
        body.dark-mode {
            --bg-color: #121212;
            --text-color: #e0e0e0;
            --primary-color: #58a6ff;
            --secondary-color: #f7b731;
            --card-bg-color: #1e1e1e;
            --border-color: #333;
            --header-bg: #1a202c;
            --header-text: #e2e8f0;
            --text-muted: #a0aec0;
            --card-shadow: rgba(0,0,0,0.2);
            --article-title-color: #f0f0f0;
        }

        *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
        body { 
            font-family: 'Inter', 'Noto Sans SC', sans-serif; 
            background-color: var(--bg-color); 
            color: var(--text-color); 
            line-height: 1.7; 
            overflow-x: hidden; 
            position: relative;
            transition: background-color 0.3s, color 0.3s;
        }
        body::before, body::after { content: ''; position: fixed; z-index: -1; opacity: 0.05; transition: transform 0.5s ease-out; }
        body::before { width: 50vw; height: 50vw; background: var(--primary-color); border-radius: 50%; top: -20vw; right: -20vw; transform: var(--before-transform, translateY(0)); }
        body::after { width: 0; height: 0; border-style: solid; border-width: 0 0 40vw 40vw; border-color: transparent transparent var(--secondary-color) transparent; bottom: -10vw; left: -10vw; transform: var(--after-transform, rotate(-20deg)); }
        .container { max-width: 800px; margin: 0 auto; padding: 20px; }
        .site-header { background-color: var(--header-bg); color: var(--header-text); padding: 2rem 1rem; text-align: center; margin-bottom: 3rem; border-bottom: 5px solid var(--primary-color); position: relative; overflow: hidden; transition: background-color 0.3s; }
        .site-header::before { content: ''; position: absolute; top: 0; left: 0; width: 100%; height: 100%; background: linear-gradient(45deg, rgba(255,255,255,0.05) 25%, transparent 25%, transparent 50%, rgba(255,255,255,0.05) 50%, rgba(255,255,255,0.05) 75%, transparent 75%, transparent); background-size: 40px 40px; z-index: 0; }
        .site-title { font-size: 2.5rem; font-weight: 700; margin-bottom: 0.5rem; position: relative; z-index: 1; }
        .site-nav { display: flex; justify-content: center; align-items: center; flex-wrap: wrap; }
        .site-nav a { color: var(--header-text); text-decoration: none; margin: 0 15px; font-weight: 300; transition: all 0.3s ease; opacity: 0.8; display: inline-block; }
        .site-nav a:hover { color: #fff; opacity: 1; transform: translateY(-3px); }
        .article-card { background-color: var(--card-bg-color); border: 1px solid var(--border-color); border-radius: 12px; margin-bottom: 2.5rem; padding: 2.5rem; box-shadow: 0 4px 15px var(--card-shadow); transition: background-color 0.3s, border-color 0.3s; }
        .article-title { font-size: 2.2rem; margin-bottom: 0.75rem; line-height: 1.3; color: var(--article-title-color); }
        .article-meta { color: var(--text-muted); font-size: 0.9rem; margin-bottom: 2rem; border-bottom: 1px solid var(--border-color); padding-bottom: 1rem; transition: border-color 0.3s, color 0.3s; }
        .article-content p, .article-content ul { margin-bottom: 1.5rem; font-size: 1.1rem; }
        .article-content ul { padding-left: 25px; }
        .article-content li { margin-bottom: 1rem; }
        .article-content h2, .article-content h3 { margin-top: 2rem; margin-bottom: 1rem; padding-bottom: 0.5rem; border-bottom: 1px solid var(--border-color); color: var(--article-title-color);}
        .article-content a { color: var(--primary-color); text-decoration: none; }
        .article-content a:hover { text-decoration: underline; }
        .site-footer { text-align: center; padding: 2rem 1rem; margin-top: 3rem; color: var(--text-muted); border-top: 1px solid var(--border-color); transition: border-color 0.3s, color 0.3s; }
        
        #theme-toggle {
            background: none;
            color: var(--header-text);
            border: 1px solid var(--header-text);
            padding: 6px 15px;
            border-radius: 20px;
            cursor: pointer;
            font-size: 0.9rem;
            font-family: inherit;
            font-weight: 300;
            margin-left: 15px;
            display: inline-block;
            opacity: 0.8;
            transition: all 0.3s ease;
        }
        #theme-toggle:hover {
            color: #fff;
            background-color: var(--primary-color);
            border-color: var(--primary-color);
            opacity: 1;
            transform: translateY(-3px);
        }

        @media (max-width: 768px) { 
            .article-card { padding: 1.5rem; } 
            .article-title { font-size: 1.8rem; } 
            #theme-toggle { margin-top: 1rem; }
        }
    </style>
</head>
<body>

    <header class="site-header">
        <div class="container">
            <h1 class="site-title">Enceladus的非财经空间</h1>
            <nav class="site-nav">
                <a href="./index.html">首页</a>
                <a href="./about.html">行情</a>
                <a href="#">归档</a>
                <a href="#">联系我</a>
                <button id="theme-toggle">切换模式</button>
            </nav>
        </div>
    </header>

    <main class="container">
        
        <article class="article-card">
            <!-- 模板使用提示: 2. 修改这里的文章大标题 -->
            <h1 class="article-title">这里是你的文章标题</h1>
            
            <!-- 模板使用提示: 3. 修改这里的发布日期 -->
            <p class="article-meta">发布于 <time datetime="YYYY-MM-DD">YYYY年MM月DD日</time></p>
            
            <!-- 模板使用提示: 4. 在下方 div 中撰写你的文章正文 -->
            <div class="article-content">
                <p>这里是你的第一段内容。你可以自由地使用 <code>&lt;p&gt;</code> 标签来分段。</p>
                
                <h3>这是一个二级标题</h3>
                <p>在二级标题下，你可以继续阐述观点。如果你需要一个列表：</p>
                <ul>
                    <li>这是列表项一。</li>
                    <li>这是列表项二。</li>
                </ul>

                <p>如果你需要插入一个指向外部网站的<a href="https://example.com" target="_blank">链接</a>，可以这样做。</p>

                <p>如果你需要展示数学公式，可以直接使用 LaTeX 语法，例如行内公式 $\E = mc^2$，或者像下面这样的独立公式块：</p>
                $$ \int_{-\infty}^{\infty} e^{-x^2} dx = \sqrt{\pi} $$
                <p>继续添加更多段落来丰富你的文章内容。</p>
            </div>
        </article>

    </main>

    <footer class="site-footer">
        <p>&copy; 2025 Enceladus. All Rights Reserved.</p>
    </footer>

    <script>
        (function() {
            // 页面滚动时的背景视差效果
            window.addEventListener('scroll', function() {
                window.requestAnimationFrame(function() {
                    const scrollY = window.scrollY;
                    document.body.style.setProperty('--before-transform', `translateY(${scrollY * 0.1}px)`);
                    document.body.style.setProperty('--after-transform', `translateY(${scrollY * 0.2}px) rotate(-20deg)`);
                });
            });

            // 黑夜模式切换逻辑
            const themeToggle = document.getElementById('theme-toggle');
            const body = document.body;
            
            if (themeToggle) {
                const applyTheme = (theme) => {
                    if (theme === 'dark') {
                        body.classList.add('dark-mode');
                        themeToggle.textContent = '日间模式';
                    } else {
                        body.classList.remove('dark-mode');
                        themeToggle.textContent = '黑夜模式';
                    }
                };

                themeToggle.addEventListener('click', () => {
                    const isDarkMode = body.classList.contains('dark-mode');
                    const newTheme = isDarkMode ? 'light' : 'dark';
                    applyTheme(newTheme);
                    try {
                        localStorage.setItem('theme', newTheme);
                    } catch (e) {
                        console.error("无法访问 localStorage:", e);
                    }
                });

                let initialTheme = 'light';
                try {
                    const savedTheme = localStorage.getItem('theme');
                    const prefersDark = window.matchMedia && window.matchMedia('(prefers-color-scheme: dark)').matches;
                    if (savedTheme) {
                        initialTheme = savedTheme;
                    } else if (prefersDark) {
                        initialTheme = 'dark';
                    }
                } catch (e) {
                    console.error("无法访问 localStorage:", e);
                }
                applyTheme(initialTheme);
            }
        })();
    </script>

</body>
</html>
