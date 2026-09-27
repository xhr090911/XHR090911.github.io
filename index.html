<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>随便一下</title>
<style>
  * { margin: 0; padding: 0; box-sizing: border-box; }
  body {
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: -apple-system, "PingFang SC", "Microsoft YaHei", sans-serif;
    background: linear-gradient(135deg, #1a1a2e 0%, #16213e 50%, #0f3460 100%);
    transition: background 0.8s ease;
    padding: 24px;
  }
  .card {
    width: 100%;
    max-width: 480px;
    background: rgba(255,255,255,0.08);
    backdrop-filter: blur(16px);
    -webkit-backdrop-filter: blur(16px);
    border: 1px solid rgba(255,255,255,0.15);
    border-radius: 24px;
    padding: 48px 36px;
    text-align: center;
    color: #fff;
    box-shadow: 0 20px 60px rgba(0,0,0,0.3);
  }
  .tag {
    display: inline-block;
    font-size: 13px;
    letter-spacing: 2px;
    padding: 6px 14px;
    border-radius: 999px;
    background: rgba(255,255,255,0.12);
    margin-bottom: 28px;
    opacity: 0.9;
  }
  .content {
    font-size: 26px;
    line-height: 1.6;
    min-height: 120px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-weight: 300;
    transition: opacity 0.3s;
  }
  .content.fade { opacity: 0; }
  .color-swatch {
    width: 88px; height: 88px;
    border-radius: 50%;
    margin: 0 auto 20px;
    border: 3px solid rgba(255,255,255,0.4);
    box-shadow: 0 8px 24px rgba(0,0,0,0.25);
    transition: background 0.5s;
  }
  .color-code {
    font-family: "SF Mono", Consolas, monospace;
    font-size: 15px;
    opacity: 0.8;
    margin-top: 8px;
    letter-spacing: 1px;
  }
  button {
    margin-top: 36px;
    padding: 14px 40px;
    font-size: 16px;
    color: #1a1a2e;
    background: #fff;
    border: none;
    border-radius: 999px;
    cursor: pointer;
    font-weight: 600;
    letter-spacing: 1px;
    transition: transform 0.15s, box-shadow 0.2s;
    box-shadow: 0 6px 20px rgba(255,255,255,0.25);
  }
  button:hover { transform: translateY(-2px); box-shadow: 0 10px 28px rgba(255,255,255,0.35); }
  button:active { transform: translateY(0); }
  .footer { margin-top: 28px; font-size: 12px; opacity: 0.4; }
</style>
</head>
<body>
  <div class="card">
    <div class="tag" id="tag">今日一言</div>
    <div class="content" id="content">点击下方，随便来点什么 ✨</div>
    <button onclick="next()">随 便 一 下</button>
    <div class="footer">每次点击随机切换：一句话 · 一首诗 · 一种颜色</div>
  </div>

<script>
  const quotes = [
    "生活就像一盒巧克力，你永远不知道下一颗是什么味道。",
    "保持好奇心的人，永远都不会老。",
    "今天也要好好吃饭、好好睡觉、好好开心。",
    "别慌，月亮也一直在绕着圈子走。",
    "你不需要很厉害才能开始，但你需要开始才能很厉害。",
    "风很自由，所以它能去任何地方。",
    "慢慢来，比较快。",
    "把今天过好，就是对未来最好的承诺。"
  ];

  const poems = [
    { t: "床前明月光，疑是地上霜。举头望明月，低头思故乡。", a: "—— 李白《静夜思》" },
    { t: "海内存知己，天涯若比邻。", a: "—— 王勃《送杜少府之任蜀州》" },
    { t: "大漠孤烟直，长河落日圆。", a: "—— 王维《使至塞上》" },
    { t: "落霞与孤鹜齐飞，秋水共长天一色。", a: "—— 王勃《滕王阁序》" },
    { t: "竹外桃花三两枝，春江水暖鸭先知。", a: "—— 苏轼《惠崇春江晚景》" },
    { t: "会当凌绝顶，一览众山小。", a: "—— 杜甫《望岳》" }
  ];

  const palettes = [
    ["#ff9a9e","#fad0c4"], ["#a18cd1","#fbc2eb"], ["#84fab0","#8fd3f4"],
    ["#ffecd2","#fcb69f"], ["#667eea","#764ba2"], ["#fccb90","#d57eeb"],
    ["#43e97b","#38f9d7"], ["#fa709a","#fee140"], ["#4facfe","#00f2fe"],
    ["#43cea2","#185a9d"], ["#f83600","#f9d423"], ["#c471f5","#fa71cd"]
  ];

  function rand(n){ return Math.floor(Math.random()*n); }

  function next() {
    const el = document.getElementById('content');
    const tag = document.getElementById('tag');
    el.classList.add('fade');

    setTimeout(() => {
      const r = Math.random();
      if (r < 0.4) {
        tag.textContent = '随机一言';
        el.innerHTML = quotes[rand(quotes.length)];
      } else if (r < 0.7) {
        const p = poems[rand(poems.length)];
        tag.textContent = '随机诗词';
        el.innerHTML = p.t + '<br><span style="font-size:15px;opacity:.6">' + p.a + '</span>';
      } else {
        const c = palettes[rand(palettes.length)];
        tag.textContent = '随机配色';
        el.innerHTML = '<div><div class="color-swatch" style="background:' + c[0] + '"></div>' +
          '<div class="color-code">' + c[0] + ' · ' + c[1] + '</div></div>';
        document.body.style.background = 'linear-gradient(135deg,' + c[0] + ',' + c[1] + ')';
      }
      el.classList.remove('fade');
    }, 250);
  }
</script>
</body>
</html>
