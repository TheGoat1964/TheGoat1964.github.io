# TheGoat1964.github.io
quote-generator
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Random Unknown Quotes</title>
  <style>
    :root {
      --bg-color: #f4f4f4;
      --text-color: #333;
      --box-bg: #fff;
      --button-bg: #007BFF;
      --button-hover: #0056b3;
    }

    body.dark-mode {
      --bg-color: #121212;
      --text-color: #f1f1f1;
      --box-bg: #1e1e1e;
      --button-bg: #1a73e8;
      --button-hover: #135ab8;
    }

    body {
      font-family: Arial, sans-serif;
      background: var(--bg-color);
      color: var(--text-color);
      text-align: center;
      padding: 100px 20px;
      transition: background 0.4s, color 0.4s;
    }

    #quote-box {
      font-size: 1.5em;
      margin: 30px auto;
      max-width: 600px;
      background: var(--box-bg);
      padding: 30px;
      border-radius: 10px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
      opacity: 1;
      transition: opacity 0.5s ease;
    }

    .buttons {
      margin-top: 20px;
    }

    button {
      background-color: var(--button-bg);
      border: none;
      color: white;
      padding: 12px 24px;
      font-size: 1em;
      border-radius: 5px;
      cursor: pointer;
      margin: 5px;
      transition: background-color 0.3s ease;
    }

    button:hover {
      background-color: var(--button-hover);
    }

    #copy-status {
      margin-top: 10px;
      color: green;
      font-size: 0.9em;
    }
  </style>
</head>
<body>

  <h1>Random Unknown Quote Generator</h1>
  <div id="quote-box">Click the button to get a quote...</div>

  <div class="buttons">
    <button onclick="generateQuote()">New Quote</button>
    <button onclick="copyToClipboard()">Copy</button>
    <button onclick="shareOnTwitter()">Tweet</button>
    <button onclick="toggleDarkMode()">Toggle Dark Mode</button>
  </div>

  <div id="copy-status"></div>

  <script>
    const quotes = [
      "Some paths can’t be found until you’re lost.",
      "Even the smallest shadow needs light to exist.",
      "Waves don’t ask the shore for permission.",
      "The silence you fear may hold your answer.",
      "Unknown roads often lead to the truest destinations.",
      "Not all storms come to destroy; some clear the sky.",
      "Truth doesn’t need a name to be heard.",
      "A cracked mirror still reflects light.",
      "Sometimes, the pause is the loudest part of the song.",
      "The leaf never questions the wind’s direction."
    ];

    let currentQuote = "";

    function fadeOutIn(callback) {
      const box = document.getElementById("quote-box");
      box.style.opacity = 0;
      setTimeout(() => {
        callback();
        box.style.opacity = 1;
      }, 400);
    }

    function generateQuote() {
      fadeOutIn(() => {
        const randomIndex = Math.floor(Math.random() * quotes.length);
        currentQuote = quotes[randomIndex];
        document.getElementById("quote-box").textContent = currentQuote;
        document.getElementById("copy-status").textContent = "";
      });
    }

    function copyToClipboard() {
      if (!currentQuote) return;
      navigator.clipboard.writeText(currentQuote).then(() => {
        document.getElementById("copy-status").textContent = "Copied to clipboard!";
      }).catch(() => {
        document.getElementById("copy-status").textContent = "Failed to copy.";
      });
    }

    function shareOnTwitter() {
      if (!currentQuote) return;
      const tweetText = encodeURIComponent(currentQuote + " #quotes");
      const twitterUrl = `https://twitter.com/intent/tweet?text=${tweetText}`;
      window.open(twitterUrl, '_blank');
    }

    function toggleDarkMode() {
      document.body.classList.toggle("dark-mode");
    }
  </script>

</body>
</html>
