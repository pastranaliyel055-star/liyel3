# liyel3<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>❤️ 8-BIT LOVE LETTER ❤️</title>
  <!-- Pixel font & minimal style -->
  <link href="https://fonts.googleapis.com/css2?family=Press+Start+2P&display=swap" rel="stylesheet">
  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      user-select: none;
    }

    body {
      background: #0b0e1a;
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      font-family: 'Press Start 2P', 'Courier New', monospace;
      image-rendering: pixelated;
      image-rendering: crisp-edges;
      padding: 16px;
    }

    /* main canvas – pixel art bedroom + stars */
    .pixel-world {
      position: relative;
      width: 780px;
      max-width: 100%;
      background: #1a1f33;
      border: 6px solid #4a3f5c;
      box-shadow: 0 0 0 4px #2a1f3a, 0 0 0 8px #0f0a18;
      border-radius: 24px;
      padding: 20px 20px 30px;
      image-rendering: pixelated;
      transition: all 0.2s;
    }

    /* pixel background: bedroom + starry night */
    .pixel-bg {
      position: relative;
      width: 100%;
      aspect-ratio: 16 / 10;
      background: #1b1f3b;
      background-image: 
        /* stars */
        radial-gradient(circle at 10% 15%, #f8f0c0 2px, transparent 2px),
        radial-gradient(circle at 28% 8%, #f8f0c0 1.5px, transparent 2px),
        radial-gradient(circle at 45% 22%, #f8f0c0 2px, transparent 2px),
        radial-gradient(circle at 70% 12%, #f8f0c0 2.5px, transparent 2.5px),
        radial-gradient(circle at 85% 30%, #f8f0c0 1.5px, transparent 2px),
        radial-gradient(circle at 15% 40%, #f8f0c0 1.5px, transparent 2px),
        radial-gradient(circle at 55% 35%, #f8f0c0 2px, transparent 2px),
        radial-gradient(circle at 92% 55%, #f8f0c0 2px, transparent 2px),
        radial-gradient(circle at 5% 70%, #f8f0c0 1px, transparent 2px),
        radial-gradient(circle at 38% 60%, #f8f0c0 1.5px, transparent 2px),
        radial-gradient(circle at 65% 70%, #f8f0c0 2px, transparent 2px),
        /* window / cozy glow */
        radial-gradient(ellipse at 75% 25%, #f7e6b0 30px, transparent 50px),
        /* pixel bed */
        linear-gradient(180deg, #3b2e4a 0%, #2f2340 100%);
      background-size: 100% 100%;
      border-radius: 18px;
      border: 4px solid #322a47;
      box-shadow: inset 0 0 0 4px #241e33;
      image-rendering: pixelated;
      overflow: hidden;
      transition: all 0.2s;
    }

    /* pixel art furniture (bed, lamp, window) */
    .pixel-bg::before {
      content: "";
      position: absolute;
      bottom: 8%;
      left: 8%;
      width: 50%;
      height: 28%;
      background: #3d2e4e;
      border-radius: 40px 40px 12px 12px;
      box-shadow: 0 8px 0 #251b30, 0 12px 0 #1d1425;
      border: 2px solid #241c30;
    }

    .pixel-bg::after {
      content: "🛏️";
      position: absolute;
      bottom: 12%;
      left: 15%;
      font-size: 42px;
      filter: drop-shadow(0 6px 0 #1f172a);
      transform: scaleX(-1);
    }

    /* lamp + window */
    .lamp {
      position: absolute;
      top: 18%;
      right: 12%;
      font-size: 36px;
      filter: drop-shadow(0 0 8px #f7e394);
      transform: rotate(-10deg);
      text-shadow: 0 4px 0 #2f263b;
    }

    .window {
      position: absolute;
      top: 12%;
      left: 12%;
      width: 60px;
      height: 50px;
      background: #2d354f;
      border: 6px solid #3d314b;
      border-radius: 16px 16px 6px 6px;
      box-shadow: inset 0 0 0 4px #201b30, 0 0 20px #b8a7d0;
    }
    .window::after {
      content: "🌙";
      position: absolute;
      top: 6px;
      left: 12px;
      font-size: 28px;
      filter: drop-shadow(0 0 8px #fceeb5);
    }

    /* UI overlay */
    .ui-overlay {
      position: relative;
      margin-top: -8px;
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 18px;
    }

    /* arcade dialogue box */
    .dialogue-box {
      background: #0d0b1a;
      border: 6px solid #574b6e;
      border-radius: 32px;
      padding: 18px 22px;
      width: 100%;
      max-width: 600px;
      margin: 0 auto;
      box-shadow: 0 8px 0 #281f36, inset 0 0 0 4px #1f1830;
      color: #f2e9c7;
      text-shadow: 0 2px 0 #3f2f4e;
      font-size: 14px;
      line-height: 1.8;
      transition: 0.2s;
    }

    .dialogue-box .title {
      color: #f7d98c;
      letter-spacing: 2px;
      font-size: 15px;
    }

    .btn-start {
      background: #2b1f3d;
      border: 4px solid #6d5a85;
      color: #f7eac1;
      padding: 12px 28px;
      border-radius: 60px;
      font-family: 'Press Start 2P', monospace;
      font-size: 18px;
      text-shadow: 0 2px 0 #1b1228;
      box-shadow: 0 6px 0 #1a1225, inset 0 -2px 0 #4b3a5e;
      cursor: pointer;
      transition: all 0.08s linear;
      margin-top: 6px;
      width: fit-content;
      letter-spacing: 2px;
    }

    .btn-start:active {
      transform: translateY(6px);
      box-shadow: 0 0px 0 #1a1225;
    }

    /* letter area – typewriter */
    .letter-area {
      background: #15102a;
      border: 6px solid #3f3457;
      border-radius: 24px;
      padding: 24px 20px;
      width: 100%;
      max-width: 620px;
      min-height: 120px;
      color: #fbefcf;
      font-size: 14px;
      line-height: 2;
      box-shadow: inset 0 0 0 4px #0b0818;
      transition: all 0.2s;
      margin-top: 6px;
      position: relative;
    }

    .letter-content {
      min-height: 80px;
      word-break: break-word;
    }

    .cursor-blink {
      display: inline-block;
      width: 10px;
      height: 20px;
      background: #f7d98c;
      animation: blink 0.8s step-end infinite;
      vertical-align: middle;
      margin-left: 4px;
    }

    @keyframes blink {
      0%, 100% { opacity: 1; }
      50% { opacity: 0; }
    }

    /* mini game: catch hearts */
    .heart-game {
      background: #1b1630;
      border: 4px solid #56466e;
      border-radius: 40px;
      padding: 14px 18px;
      display: flex;
      flex-wrap: wrap;
      align-items: center;
      justify-content: center;
      gap: 20px;
      width: 100%;
      max-width: 400px;
      margin: 4px auto 0;
      box-shadow: inset 0 0 0 4px #120f22;
    }

    .game-area {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 12px;
    }

    .heart-btn {
      background: #30244a;
      border: 4px solid #745a8a;
      color: #fdd9b5;
      font-size: 28px;
      padding: 8px 20px;
      border-radius: 60px;
      font-family: 'Press Start 2P', monospace;
      cursor: pointer;
      box-shadow: 0 4px 0 #1f1730;
      transition: all 0.08s;
      text-shadow: 0 2px 0 #261d36;
      display: inline-flex;
      align-items: center;
      gap: 6px;
    }

    .heart-btn:active {
      transform: translateY(4px);
      box-shadow: 0 0px 0 #1f1730;
    }

    .heart-btn .heart-icon {
      font-size: 26px;
      line-height: 1;
    }

    .score-badge {
      background: #0d0b1a;
      border: 3px solid #5c4c72;
      border-radius: 30px;
      padding: 6px 18px;
      color: #f7e3b0;
      font-size: 15px;
      display: inline-block;
      box-shadow: inset 0 0 0 2px #251e34;
    }

    .hidden-letter-part {
      display: none;
      margin-top: 10px;
      border-top: 3px dashed #6d5a82;
      padding-top: 14px;
      color: #f5dba8;
    }

    .unlocked {
      display: block !important;
    }

    /* responsive */
    @media (max-width: 600px) {
      .dialogue-box { font-size: 11px; padding: 14px; }
      .btn-start { font-size: 14px; padding: 10px 18px; }
      .letter-area { font-size: 11px; padding: 16px; }
    }

    .footer-note {
      color: #7b6a8f;
      font-size: 10px;
      margin-top: 12px;
      text-align: center;
      letter-spacing: 1px;
    }
  </style>
</head>
<body>

<div class="pixel-world">
  <!-- pixel bg with bedroom & stars -->
  <div class="pixel-bg">
    <div class="lamp">🪔</div>
    <div class="window"></div>
    <!-- extra pixel details -->
    <div style="position:absolute; bottom:6%; right:10%; font-size:20px; filter:drop-shadow(0 4px 0 #2f2340);">🧸</div>
  </div>

  <!-- UI overlay -->
  <div class="ui-overlay">

    <!-- dialogue box -->
    <div class="dialogue-box" id="dialogueBox">
      <div class="title">📟 TERMINAL · LOVE 1.0</div>
      <div style="margin: 8px 0 4px;">'Player 1 has left you a message. Open?'</div>
      <button class="btn-start" id="startBtn">▶ START</button>
    </div>

    <!-- letter with typewriter effect -->
    <div class="letter-area" id="letterArea">
      <div class="letter-content" id="letterContent">
        <span id="typewriterTarget"></span><span class="cursor-blink" id="cursorBlink"></span>
      </div>
      <!-- hidden part (unlocked by game) -->
      <div class="hidden-letter-part" id="hiddenPart">
        ❤️ <span style="color:#f7d98c;">… and every heartbeat echoes your name.</span> ❤️
      </div>
    </div>

    <!-- mini game: catch hearts -->
    <div class="heart-game">
      <div class="game-area">
        <span class="score-badge" id="heartScore">❤️ 0</span>
        <button class="heart-btn" id="catchHeartBtn">
          <span class="heart-icon">💖</span> CATCH
        </button>
        <span style="color:#b8a0c9; font-size:11px; align-self:center;">♥ click to grow love</span>
      </div>
    </div>
    <div class="footer-note">⬆️ catch 3 hearts to unlock secret verse</div>
  </div>
</div>

<script>
  (function() {
    "use strict";

    // DOM elements
    const startBtn = document.getElementById('startBtn');
    const typewriterTarget = document.getElementById('typewriterTarget');
    const cursorBlink = document.getElementById('cursorBlink');
    const hiddenPart = document.getElementById('hiddenPart');
    const heartScoreSpan = document.getElementById('heartScore');
    const catchBtn = document.getElementById('catchHeartBtn');

    // Letter content (full, with a hidden part marker)
    const fullLetter = 
`My dearest Player 1,

Every pixel of this world was drawn with you in mind.
Your laughter is the 8-bit melody that loops in my heart.

I've hidden a secret in this letter...
Catch the floating hearts to reveal it.

Yours, in every frame,
Player 2 💾`;

    // Hidden extra verse (will be appended after game unlock)
    const hiddenVerse = `\n\n❤️ P.S. In every starry night, I see your face. ❤️`;

    let letterIndex = 0;
    let isTyping = false;
    let typeInterval = null;
    let isLetterRevealed = false;
    let heartCount = 0;
    const HEARTS_TO_UNLOCK = 3;
    let hiddenUnlocked = false;

    // Sound effects (chiptune style via Web Audio)
    let audioCtx = null;

    function initAudio() {
      if (!audioCtx) {
        audioCtx = new (window.AudioContext || window.webkitAudioContext)();
      }
    }

    function playTone(freq, duration, type = 'square', volume = 0.15) {
      try {
        initAudio();
        const osc = audioCtx.createOscillator();
        const gain = audioCtx.createGain();
        osc.type = type;
        osc.frequency.value = freq;
        gain.gain.value = volume;
        gain.gain.exponentialRampToValueAtTime(0.001, audioCtx.currentTime + duration);
        osc.connect(gain);
        gain.connect(audioCtx.destination);
        osc.start();
        osc.stop(audioCtx.currentTime + duration);
      } catch (_) { /* silent fail */ }
    }

    function playKeyClick() {
      playTone(600 + Math.random() * 200, 0.06, 'square', 0.07);
    }

    function playUnlockSound() {
      playTone(523, 0.12, 'square', 0.12);
      setTimeout(() => playTone(659, 0.12, 'square', 0.12), 130);
      setTimeout(() => playTone(784, 0.18, 'square', 0.15), 260);
    }

    function playHeartCatch() {
      playTone(880, 0.1, 'square', 0.09);
      setTimeout(() => playTone(1100, 0.1, 'square', 0.07), 80);
    }

    // Typewriter effect
    function typeLetter() {
      if (isTyping) return;
      if (letterIndex >= fullLetter.length) {
        // if letter fully typed, show cursor but no more typing
        if (cursorBlink) cursorBlink.style.display = 'inline-block';
        return;
      }

      isTyping = true;
      if (cursorBlink) cursorBlink.style.display = 'inline-block';

      // clear any existing interval
      if (typeInterval) clearInterval(typeInterval);

      typeInterval = setInterval(() => {
        if (letterIndex < fullLetter.length) {
          const char = fullLetter.charAt(letterIndex);
          typewriterTarget.textContent += char;
          letterIndex++;
          playKeyClick(); // subtle chiptune

          // if we reach end, show cursor and stop
          if (letterIndex === fullLetter.length) {
            clearInterval(typeInterval);
            typeInterval = null;
            isTyping = false;
            if (cursorBlink) cursorBlink.style.display = 'inline-block';
          }
        } else {
          clearInterval(typeInterval);
          typeInterval = null;
          isTyping = false;
        }
      }, 38); // retro speed
    }

    // Reset letter (for replay)
    function resetLetter() {
      if (typeInterval) {
        clearInterval(typeInterval);
        typeInterval = null;
      }
      isTyping = false;
      letterIndex = 0;
      typewriterTarget.textContent = '';
      if (cursorBlink) cursorBlink.style.display = 'inline-block';
      // hide hidden part if not unlocked, but if unlocked keep it
      if (!hiddenUnlocked) {
        hiddenPart.classList.remove('unlocked');
      } else {
        // if already unlocked, we keep it visible
      }
    }

    // Start sequence
    function startLoveLetter() {
      initAudio();
      resetLetter();
      // small delay then type
      setTimeout(() => {
        typeLetter();
        isLetterRevealed = true;
        // if hidden already unlocked, show it after typing finishes? but we handle separately
      }, 200);
      // change button text
      startBtn.textContent = '📖 OPENING...';
      startBtn.disabled = true;
      setTimeout(() => {
        startBtn.textContent = '❤️ READ AGAIN';
        startBtn.disabled = false;
      }, 800);
    }

    // Catch heart game: increment counter & unlock hidden part
    function catchHeart() {
      initAudio();
      if (!isLetterRevealed) {
        // if letter not started, start it!
        startLoveLetter();
        // then increment after a moment
        setTimeout(() => {
          heartCount = Math.min(heartCount + 1, 10);
          updateHeartScore();
          playHeartCatch();
          checkUnlock();
        }, 300);
        return;
      }

      heartCount = Math.min(heartCount + 1, 10);
      updateHeartScore();
      playHeartCatch();
      checkUnlock();

      // visual feedback: button pop
      catchBtn.style.transform = 'scale(0.94)';
      setTimeout(() => catchBtn.style.transform = 'scale(1)', 100);
    }

    function updateHeartScore() {
      heartScoreSpan.textContent = `❤️ ${heartCount}`;
    }

    function checkUnlock() {
      if (heartCount >= HEARTS_TO_UNLOCK && !hiddenUnlocked) {
        hiddenUnlocked = true;
        // unlock hidden part: show it and append extra text to letter?
        hiddenPart.classList.add('unlocked');
        // also add hidden verse to typewriter if letter fully typed, else append after finish?
        // we can append to fullLetter? but we use static.  we'll just show hiddenPart.
        playUnlockSound();
        // also add extra text to typewriter target if letter already finished
        if (letterIndex >= fullLetter.length) {
          // append extra line with typewriter effect?
          // but we want it to appear as part of letter, we'll add to hiddenPart
          // but hiddenPart already has extra text
          // we can also add a little animation
          const extraSpan = document.createElement('span');
          extraSpan.textContent = ' ✨ secret unlocked!';
          extraSpan.style.color = '#f7d98c';
          typewriterTarget.appendChild(extraSpan);
        } else {
          // if typing still in progress, we'll just show hidden part when done
          // but we want to make sure it appears at end
          // we'll add a listener? but we can check periodically
          const checkDone = setInterval(() => {
            if (letterIndex >= fullLetter.length) {
              clearInterval(checkDone);
              const extraSpan = document.createElement('span');
              extraSpan.textContent = ' ✨ secret unlocked!';
              extraSpan.style.color = '#f7d98c';
              typewriterTarget.appendChild(extraSpan);
            }
          }, 200);
        }
      }
    }

    // Event listeners
    startBtn.addEventListener('click', function(e) {
      e.preventDefault();
      initAudio();
      if (!isLetterRevealed) {
        startLoveLetter();
      } else {
        // re-read: reset and type again
        resetLetter();
        // keep hidden if unlocked
        if (hiddenUnlocked) {
          hiddenPart.classList.add('unlocked');
        } else {
          hiddenPart.classList.remove('unlocked');
        }
        startLoveLetter();
      }
    });

    catchBtn.addEventListener('click', function(e) {
      e.preventDefault();
      catchHeart();
    });

    // also click on heart icon in game
    document.querySelector('.heart-icon')?.addEventListener('click', function(e) {
      e.stopPropagation();
      catchHeart();
    });

    // initial setup: cursor visible
    if (cursorBlink) cursorBlink.style.display = 'inline-block';

    // extra: click on 'catch' also triggers game
    // prefill heart count from localStorage? not needed.

    // if user clicks anywhere on letter area, maybe start? no, only start button.
    console.log('❤️ 8-bit love letter ready. Press START.');
  })();
</script>
</body>
</html>
