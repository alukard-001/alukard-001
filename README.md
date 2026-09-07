* { margin:0; padding:0; box-sizing:border-box; }
  body {
    background:radial-gradient(circle at 50% 30%, #14161c 0%, #090a0d 70%);
    display:flex;
    justify-content:center;
    align-items:center;
    min-height:100vh;
    padding:40px 20px;
    font-family:"JetBrains Mono", ui-monospace, monospace;
  }

  .banner {
    position:relative;
    width:100%;
    max-width:920px;
    height:460px;
    border-radius:12px;
    overflow:hidden;
    box-shadow:
      0 30px 70px rgba(0,0,0,0.65),
      0 0 0 1px rgba(255,255,255,0.08),
      0 0 90px rgba(60,90,180,0.10);
  }

  /* ---------- SCENE 1: video ---------- */
  .scene-video {
    position:absolute; inset:0;
    animation: fadeVideo 12s ease-in-out infinite;
  }
  .scene-video video {
    width:100%; height:100%;
    object-fit:cover;
    display:block;
    filter:contrast(1.05) saturate(1.08) brightness(1.02);
  }
  .scene-video::after{
    content:"";
    position:absolute; inset:0;
    background:linear-gradient(180deg, rgba(0,0,0,0) 55%, rgba(0,0,0,0.6) 100%);
  }
  @keyframes fadeVideo {
    0%    { opacity:1; }
    20%   { opacity:1; }
    27%   { opacity:0; }
    92%   { opacity:0; }
    100%  { opacity:1; }
  }

  /* ---------- SCENE 2: black transition ---------- */
  .scene-black{
    position:absolute; inset:0;
    background:#000;
    opacity:0;
    animation: fadeBlack 12s ease-in-out infinite;
  }
  @keyframes fadeBlack {
    0%   { opacity:0; }
    20%  { opacity:0; }
    27%  { opacity:1; }
    33%  { opacity:0; }
    100% { opacity:0; }
  }

  /* ---------- SCENE 3: code editor ---------- */
  .scene-code{
    position:absolute; inset:0;
    background:linear-gradient(160deg, #1a1b21 0%, #131418 100%);
    opacity:0;
    animation: fadeCode 12s ease-in-out infinite;
    display:flex;
    flex-direction:column;
  }
  @keyframes fadeCode {
    0%   { opacity:0; }
    28%  { opacity:0; }
    34%  { opacity:1; }
    90%  { opacity:1; }
    94%  { opacity:0; }
    100% { opacity:0; }
  }

  .titlebar{
    height:38px; flex:0 0 auto;
    background:linear-gradient(180deg,#2b2c33,#232429);
    display:flex; align-items:center;
    padding:0 16px;
    border-bottom:1px solid #0f1013;
    position:relative;
  }
  .traffic{ display:flex; gap:8px; }
  .dot{ width:12px; height:12px; border-radius:50%; box-shadow:inset 0 0 0 0.5px rgba(0,0,0,0.2); }
  .dot.red{ background:#ff5f57; }
  .dot.yellow{ background:#febc2e; }
  .dot.green{ background:#28c840; }
  .titlebar .fname{
    position:absolute; left:50%; transform:translateX(-50%);
    color:#8b8d94; font-size:12.5px; letter-spacing:.2px;
  }

  .body-row{ flex:1; display:flex; min-height:0; overflow:hidden; }

  .sidebar{
    width:48px; flex:0 0 auto;
    background:#1a1b1f;
    display:flex; flex-direction:column; align-items:center;
    padding-top:16px; gap:24px;
    border-right:1px solid #0f1013;
  }
  .sidebar svg{ width:20px; height:20px; }
  .sidebar .ico{ opacity:.45; }
  .sidebar .ico.active{ opacity:1; position:relative; }
  .sidebar .ico.active::before{
    content:"";
    position:absolute; left:-16px; top:-2px; bottom:-2px;
    width:2px; background:#fff;
  }

  .editor-area{
    flex:1; min-width:0; min-height:0;
    background:#181920;
    display:flex; flex-direction:column;
    overflow:hidden;
  }
  .tabs{
    height:34px; flex:0 0 auto;
    background:#151116;
    background:#151519;
    display:flex; align-items:stretch;
    border-bottom:1px solid #0f1013;
  }
  .tab{
    display:flex; align-items:center; gap:8px;
    padding:0 18px;
    font-size:12.5px; color:#75767e;
    background:#151519;
    border-right:1px solid #0f1013;
  }
  .tab.active{
    background:#181920; color:#e8e8ea;
    box-shadow: inset 0 -2px 0 #4e9eff;
  }
  .tab svg{ width:13px; height:13px; opacity:.9; }

  .code{
    padding:16px 0 0 0;
    display:flex;
    font-size:13px;
    line-height:20.5px;
    flex:1;
  }
  .gutter{
    color:#4b4d55; text-align:right; padding-right:20px; width:38px;
    user-select:none; font-size:13px;
  }
  .lines{ position:relative; padding-right:20px; }

  .kw{ color:#c586c0; }
  .fn{ color:#dcdcaa; }
  .str{ color:#ce9178; }
  .punc{ color:#c9c9cd; }
  .com{ color:#6a9955; font-style:italic; }
  .var{ color:#9cdcfe; }
  .num{ color:#b5cea8; }
  .prop{ color:#4fc1ff; }

  .fadein{
    opacity:0;
    animation: fadeInLine 12s ease-in-out infinite;
  }
  @keyframes fadeInLine{
    0%{opacity:0} 32%{opacity:0} 36%{opacity:1} 90%{opacity:1} 94%{opacity:0} 100%{opacity:0}
  }

  .typewrap{
    display:inline-block;
    overflow:hidden;
    white-space:nowrap;
    width:0;
    vertical-align:bottom;
    animation: typeLine 12s steps(30,end) infinite;
  }
  @keyframes typeLine {
    0%   { width:0; }
    37%  { width:0; }
    46%  { width:52ch; }
    90%  { width:52ch; }
    93%  { width:0; }
    100% { width:0; }
  }

  .cursor{
    display:inline-block; width:2px; height:17px; background:#e8e8ea;
    margin-left:1px; vertical-align:-4px;
    animation: blinkCursor 1s steps(1) infinite;
  }
  @keyframes blinkCursor {
    0%,49%{ opacity:1; } 50%,100%{ opacity:0; }
  }

  .comments{
    opacity:0;
    animation: fadeComments 12s ease-in-out infinite;
  }
  @keyframes fadeComments {
    0%   { opacity:0; }
    55%  { opacity:0; }
    60%  { opacity:1; }
    90%  { opacity:1; }
    93%  { opacity:0; }
    100% { opacity:0; }
  }

  .statusbar{
    height:26px; flex:0 0 auto;
    background:linear-gradient(180deg,#1f4f8f,#193f73);
    border-top:1px solid rgba(255,255,255,0.06);
    display:flex; align-items:center; justify-content:space-between;
    padding:0 12px;
    font-size:11.5px; color:#dce6f5;
  }
  .statusbar .grp{ display:flex; align-items:center; gap:14px; opacity:.95; white-space:nowrap; }
  .statusbar .grp span{ display:flex; align-items:center; gap:5px; white-space:nowrap; }
  .statusbar svg{ width:13px; height:13px; }
</style>
</head>
<body>

<div class="banner">

  <div class="scene-video">
    <video src="blink.mp4" autoplay loop muted playsinline></video>
  </div>

  <div class="scene-black"></div>

  <div class="scene-code">

    <div class="titlebar">
      <div class="traffic">
        <span class="dot red"></span>
        <span class="dot yellow"></span>
        <span class="dot green"></span>
      </div>
      <div class="fname">portfolio — profile.js</div>
    </div>

    <div class="body-row">
      <div class="sidebar">
        <svg class="ico active" viewBox="0 0 24 24" fill="none" stroke="#e8e8ea" stroke-width="1.6"><path d="M4 4h8l2 3h6v11a1 1 0 0 1-1 1H4a1 1 0 0 1-1-1V5a1 1 0 0 1 1-1z"/></svg>
        <svg class="ico" viewBox="0 0 24 24" fill="none" stroke="#c9c9cd" stroke-width="1.6"><circle cx="10.5" cy="10.5" r="6"/><line x1="15" y1="15" x2="21" y2="21"/></svg>
        <svg class="ico" viewBox="0 0 24 24" fill="none" stroke="#c9c9cd" stroke-width="1.6"><circle cx="6" cy="6" r="2.2"/><circle cx="6" cy="18" r="2.2"/><circle cx="18" cy="12" r="2.2"/><path d="M6 8.2V15.8M8 6.8h4a4 4 0 0 1 4 4v0"/></svg>
        <svg class="ico" viewBox="0 0 24 24" fill="none" stroke="#c9c9cd" stroke-width="1.6"><rect x="3" y="3" width="8" height="8" rx="1"/><rect x="13" y="3" width="8" height="8" rx="1"/><rect x="3" y="13" width="8" height="8" rx="1"/><rect x="13" y="13" width="8" height="8" rx="1"/></svg>
      </div>

      <div class="editor-area">
        <div class="tabs">
          <div class="tab active">
            <svg viewBox="0 0 24 24" fill="#f0dc4e"><path d="M4 4h16v16H4z" opacity="0"/><text x="2" y="18" font-size="18" font-weight="700">JS</text></svg>
            profile.js
          </div>
        </div>

        <div class="code">
          <div class="gutter">1<br>2<br>3<br>4<br>5<br>6<br>7<br>8<br>9<br>10<br>11<br>12</div>
          <div class="lines">
            <div class="fadein"><span class="kw">import</span> <span class="punc">{</span> <span class="var">Developer</span> <span class="punc">}</span> <span class="kw">from</span> <span class="str">'./me'</span><span class="punc">;</span></div>
            <div>&nbsp;</div>
            <div>
              <span class="typewrap"><span class="kw">const</span> <span class="var">dev</span> <span class="punc">=</span> <span class="kw">new</span> <span class="fn">Developer</span><span class="punc">(</span><span class="str">"Senior Full-Stack"</span><span class="punc">);</span></span><span class="cursor"></span>
            </div>
            <div>&nbsp;</div>
            <div class="comments">
              <div><span class="kw">const</span> <span class="var">skills</span> <span class="punc">=</span> <span class="punc">[</span></div>
              <div>&nbsp;&nbsp;<span class="str">'JavaScript'</span><span class="punc">,</span> <span class="str">'TypeScript'</span><span class="punc">,</span> <span class="str">'Python'</span><span class="punc">,</span> <span class="str">'C'</span><span class="punc">,</span></div>
              <div>&nbsp;&nbsp;<span class="str">'C++'</span><span class="punc">,</span> <span class="str">'C#'</span><span class="punc">,</span> <span class="str">'Java'</span><span class="punc">,</span> <span class="str">'Go'</span><span class="punc">,</span></div>
              <div>&nbsp;&nbsp;<span class="str">'Rust'</span><span class="punc">,</span> <span class="str">'PHP'</span><span class="punc">,</span> <span class="str">'Kotlin'</span><span class="punc">,</span> <span class="str">'Swift'</span><span class="punc">,</span></div>
              <div>&nbsp;&nbsp;<span class="str">'Dart'</span><span class="punc">,</span> <span class="str">'Ruby'</span></div>
              <div><span class="punc">];</span></div>
              <div>&nbsp;</div>
              <div class="com">// 6.5+ years of commercial experience — in each</div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div class="statusbar">
      <div class="grp">
        <span>
          <svg viewBox="0 0 24 24" fill="none" stroke="#fff" stroke-width="2"><path d="M6 3v12M6 15a3 3 0 1 0 0 6 3 3 0 0 0 0-6zM18 6a3 3 0 1 0 0-6 3 3 0 0 0 0 6zM18 6v6a6 6 0 0 1-6 6"/></svg>
          main
        </span>
        <span>14 languages</span>
      </div>
      <div class="grp">
        <span>Senior Full-Stack Developer</span>
      </div>
    </div>

  </div>

</div>

</body>
</html>
