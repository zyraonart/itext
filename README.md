<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <meta - AI Stylish Text Generator
  <link href="https://fonts.googleapis.com/css2?family=Dancing+Script&family=Lobster&family=Pacifico&family=Rubik+Glitch&family=Rubik+Wet+Paint&family=Secular+One&display=swap" rel="stylesheet"/>
  <style>
    body {
      background: linear-gradient(45deg, #2b1055, #7597de);
      min-height: 100vh;
      color: white;
      font-family: 'Arial', sans-serif;
      padding: 20px;
    }
/* Desktop default */
body {
  font-size: 16px;
  padding: 20px;
}
    h1 {
      font-family: 'Rubik Wet Paint', cursive;
      color: #ff6b6b;
      text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
      font-size: 2.5em;
    }

    .input-section {
      margin: 30px 0;
    }

    textarea {
      width: 80%;
      height: 100px;
      padding: 15px;
      border-radius: 15px;
      border: 3px solid #ff6b6b;
      background: rgba(255,255,255,0.9);
      font-size: 1.2em;
    }

    .style-selector {
      margin: 20px 0;
    }

    select {
      padding: 10px 20px;
      border-radius: 25px;
      background: #ff6b6b;
      color: white;
      border: none;
      font-weight: bold;
      cursor: pointer;
    }

    .output-section {
      background: rgba(255,255,255,0.1);
      padding: 20px;
      border-radius: 20px;
      margin: 20px 0;
      min-height: 100px;
    }

    .styled-text {
      font-size: 1.5em;
      margin: 20px 0;
      padding: 15px;
      word-wrap: break-word;
    }

    .copy-btn {
      background: #4CAF50;
      color: white;
      border: none;
      padding: 12px 25px;
      border-radius: 25px;
      cursor: pointer;
      font-size: 1.1em;
      transition: transform 0.3s, background-color 0.3s, opacity 0.3s;
      margin-top: 15px;
    }

    .copy-btn:hover {
      transform: scale(1.05);
    }

    .credit {
      margin-top: 30px;
      font-family: 'Dancing Script', cursive;
      font-size: 1.4em;
      color: #ffd93d;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>iText ✨</h1>
    <div class="input-section">
      <textarea id="inputText" placeholder="Enter your text here..."></textarea>
      <div class="style-selector">
        <select id="styleSelect">
          <option value="handwriting">Handwriting Style</option>
          <option value="roman">Roman Style</option>
          <option value="bold-style">Bold Style</option>
          <option value="aesthetic">Aesthetic Style</option>
          <option value="cyber">Cyber Style</option>
          <option value="graffiti">Graffiti Style</option>
          <option value="modern">Modern Style</option>
          <option value="shadow">Shadow Style</option>
          <option value="gradient-text">Gradient Style</option>
        </select>
      </div>
      <button class="copy-btn" onclick="copyText()">Copy Text 📋</button>
    </div>

    <div class="output-section">
      <div id="output" class="styled-text"></div>
    </div>

    <div class="credit">
      Created with ❤️ by <a href="https://www.instagram.com/zyraon.art/" target="_blank" style="color: #ffd93d;">Zyraon</a>
    </div>
  </div>

  <audio id="copySound" src="https://www.myinstants.com/media/sounds/click-clasic.mp3"></audio>

  <script>
    const inputText = document.getElementById('inputText');
    const styleSelect = document.getElementById('styleSelect');
    const output = document.getElementById('output');
    const copyBtn = document.querySelector('.copy-btn');
    const copySound = document.getElementById('copySound');

    const styles = {
      'handwriting': text => toScript(text),
      'roman': text => text.split('').map(toItalic).join(''),
      'bold-style': text => text.replace(/[a-z]/gi, c =>
        String.fromCodePoint(
          c >= 'A' && c <= 'Z' ? c.charCodeAt(0) + 119743 :
          c >= 'a' && c <= 'z' ? c.charCodeAt(0) + 119737 :
          c.charCodeAt(0)
        )
      ),
      'aesthetic': text => text.split('').join(' '),
      'cyber': text => toGlitch(text),
      'graffiti': text => toBubble(text),
      'modern': text => text.toUpperCase().split('').join(' '),
      'shadow': text => text + ' ' + text,
      'gradient-text': text => text.split('').map((c, i) => i % 2 === 0 ? c.toUpperCase() : c.toLowerCase()).join('')
    };

    function updateText() {
      const text = inputText.value;
      const style = styleSelect.value;
      const styled = styles[style] ? styles[style](text) : text;
      output.className = 'styled-text';
      output.textContent = styled;
    }

    function copyText() {
      updateText();
      const text = output.textContent.trim();

      if (!text) {
        showCopyMessage("Please enter text!", "#e74c3c");
        return;
      }

      navigator.clipboard.writeText(text)
        .then(() => {
          if (copySound) copySound.play();
          showCopyMessage("Copied!", "#2ecc71");
        })
        .catch(err => {
          console.error('Copy failed:', err);
        });
    }

    function showCopyMessage(message, bgColor) {
      const originalText = copyBtn.textContent;
      copyBtn.textContent = message;
      copyBtn.style.backgroundColor = bgColor;
      copyBtn.style.opacity = 0.8;

      setTimeout(() => {
        copyBtn.textContent = originalText;
        copyBtn.style.backgroundColor = "#4CAF50";
        copyBtn.style.opacity = 1;
      }, 2000);
    }

    // Helpers
    function toScript(text) {
      const map = {'A':'𝒜','B':'ℬ','C':'𝒞','D':'𝒟','E':'ℰ','F':'ℱ','G':'𝒢','H':'ℋ','I':'ℐ','J':'𝒥','K':'𝒦','L':'ℒ','M':'ℳ','N':'𝒩','O':'𝒪','P':'𝒫','Q':'𝒬','R':'ℛ','S':'𝒮','T':'𝒯','U':'𝒰','V':'𝒱','W':'𝒲','X':'𝒳','Y':'𝒴','Z':'𝒵','a':'𝒶','b':'𝒷','c':'𝒸','d':'𝒹','e':'ℯ','f':'𝒻','g':'ℊ','h':'𝒽','i':'𝒾','j':'𝒿','k':'𝓀','l':'𝓁','m':'𝓂','n':'𝓃','o':'ℴ','p':'𝓅','q':'𝓆','r':'𝓇','s':'𝓈','t':'𝓉','u':'𝓊','v':'𝓋','w':'𝓌','x':'𝓍','y':'𝓎','z':'𝓏'};
      return text.split('').map(c => map[c] || c).join('');
    }

    function toItalic(c) {
      const code = c.charCodeAt(0);
      if (c >= 'A' && c <= 'Z') return String.fromCodePoint(0x1D434 + (code - 65));
      if (c >= 'a' && c <= 'z') return String.fromCodePoint(0x1D44E + (code - 97));
      return c;
    }

    function toGlitch(text) {
      const glitch = {'A':'ꓮ','B':'𐊂','C':'Ͼ','D':'ꓷ','E':'Ɛ','F':'Ϝ','G':'ꓖ','H':'ʜ','I':'Ι','J':'Ϳ','K':'Ҝ','L':'ᒪ','M':'Ⲙ','N':'Ͷ','O':'Ⲟ','P':'ꓑ','Q':'Ⴓ','R':'ꓣ','S':'Ϛ','T':'Ͳ','U':'Ս','V':'Ѵ','W':'ꓪ','X':'ϰ','Y':'Ƴ','Z':'ꓜ'};
      return text.toUpperCase().split('').map(c => glitch[c] || c).join('');
    }

    function toBubble(text) {
      return text.split('').map(c => {
        const code = c.charCodeAt(0);
        if (c >= 'a' && c <= 'z') return String.fromCodePoint(0x24D0 + (code - 97));
        if (c >= 'A' && c <= 'Z') return String.fromCodePoint(0x24B6 + (code - 65));
        return c;
      }).join('');
    }

    inputText.addEventListener('input', updateText);
    styleSelect.addEventListener('change', updateText);
    updateText(); // initial
  </script>
<script async="async" data-cfasync="false" src="//pl26656079.profitableratecpm.com/81e933a9338de5fd7090b71aeda2c6f7/invoke.js"></script>
  <div id="container-81e933a9338de5fd7090b71aeda2c6f7"></div>
</body>
</html>
<script>
  function isLikelyInApp() {
    const ua = navigator.userAgent.toLowerCase();
    return (
      ua.includes("wv") || 
      ua.includes("webview") || 
      ua.includes("version/") && ua.includes("chrome/") && !ua.includes("safari") ||
      (window.navigator.standalone === false) || 
      (window.matchMedia('(display-mode: standalone)').matches) ||
      (typeof window.ReactNativeWebView !== "undefined") ||
      (window.location !== window.parent.location)
    );
  }

  window.addEventListener('DOMContentLoaded', function () {
    var btn = document.getElementById("download-btn");
    if (isLikelyInApp() && btn) {
      btn.style.display = "none";
    }
  });
</script>

<a href="https://drive.google.com/file/d/1-AbWgsLF7t5YRKmWoXJ5V7tdIT_A-L82/view" download>
  <button id="download-btn" style="padding: 12px 24px; background-color: #28a745; color: white; font-size: 16px; border: none; border-radius: 8px; cursor: pointer;">
    Download itext App
  </button>
</a>
<div id="loading" style="display:none;">Loading, please wait...</div>
<div id="result"></div>
