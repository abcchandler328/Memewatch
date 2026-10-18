
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>MemeWatch | Token Intelligence</title>
<style>
:root{color-scheme:dark;--bg:#0b1020;--panel:#141c2e;--line:#27344a;--muted:#91a2bb;--text:#edf3ff;--purple:#9185ff;--green:#4adea2;--red:#ff777f;--yellow:#ffd166}
*{box-sizing:border-box}
body{margin:0;background:var(--bg);color:var(--text);font:14px/1.5 system-ui,-apple-system,Segoe UI,sans-serif}
header{padding:22px max(20px,calc((100% - 1180px)/2));border-bottom:1px solid var(--line);display:flex;align-items:center;justify-content:space-between;gap:15px;flex-wrap:wrap}
.brand{font-size:22px;font-weight:850;letter-spacing:1px}.brand span{color:var(--purple)}
.pill{border:1px solid #62562d;background:#302b1a;color:var(--yellow);border-radius:30px;padding:5px 10px;font-size:11px;font-weight:700}
main{max-width:1180px;margin:auto;padding:26px 20px 60px}
h1{font-size:29px;line-height:1.2;margin:0 0 8px}h2{font-size:17px;margin:0 0 15px}
.muted{color:var(--muted)}.notice{padding:13px 15px;border:1px solid #51452a;background:#211f1b;border-radius:10px;color:#f5dca1;margin:20px 0}
.grid{display:grid;grid-template-columns:repeat(4,minmax(0,1fr));gap:13px;margin:22px 0}
.card{background:var(--panel);border:1px solid var(--line);border-radius:13px;padding:17px;min-width:0}
.metric{font-size:27px;font-weight:800;margin:8px 0 2px}.green{color:var(--green)}.red{color:var(--red)}.purple{color:var(--purple)}.yellow{color:var(--yellow)}
.controls{display:grid;grid-template-columns:2fr 1fr 1fr;gap:10px;margin-bottom:14px}
input,select,button{font:inherit;color:var(--text);background:#0c1425;border:1px solid var(--line);padding:11px 12px;border-radius:8px;min-width:0}
button{cursor:pointer}button:hover{border-color:var(--purple)}
table{width:100%;border-collapse:collapse;min-width:730px}
th,td{text-align:left;padding:14px 12px;border-bottom:1px solid var(--line)}
th{font-size:11px;color:var(--muted);text-transform:uppercase;letter-spacing:.6px}
tbody tr:hover{background:#1b263a}
.scroll{overflow-x:auto}
.token{font-weight:750}.sub{display:block;color:var(--muted);font-size:12px;font-weight:400}
.tag{display:inline-block;padding:3px 8px;border-radius:5px;font-size:11px;font-weight:700;background:#26334a}
.tag.high{color:var(--red);background:#3b202b}.tag.medium{color:var(--yellow);background:#39311d}.tag.low{color:var(--green);background:#17382f}
.bottom{display:grid;grid-template-columns:1fr 1fr;gap:14px;margin-top:17px}
.event{padding:12px 0;border-bottom:1px solid var(--line)}
.event:last-child{border:0}
.bar{height:6px;background:#29344a;border-radius:10px;overflow:hidden;margin-top:7px}
.bar span{display:block;height:100%;background:var(--purple)}
footer{color:var(--muted);font-size:12px;text-align:center;margin-top:28px}
@media(max-width:750px){.grid{grid-template-columns:repeat(2,minmax(0,1fr))}.controls{grid-template-columns:1fr}.bottom{grid-template-columns:1fr}main{padding:22px 13px}}
</style>
</head>
<body>
<header>
  <div class="brand">◈ MEME<span>WATCH</span></div>
  <span class="pill">● MONITOR ONLY</span>
</header>
<main>
  <h1>Token intelligence</h1>
  <div class="muted">Cross-chain discovery · Risk monitoring · Narrative tracking</div>
  <div class="notice"><strong>DEMO MODE:</strong> Example tokens and scores only. No live blockchain, news, security or Telegram connections are enabled yet. Do not use these figures for investment decisions.</div>

  <div class="grid">
    <div class="card"><div class="muted">Demo candidates</div><div class="metric">6</div><div class="muted">Example token records</div></div>
    <div class="card"><div class="muted">High-risk examples</div><div class="metric red" id="highCount">2</div><div class="muted">Require investigation</div></div>
    <div class="card"><div class="muted">Strong momentum</div><div class="metric green" id="momentumCount">3</div><div class="muted">Score ≥ 70</div></div>
    <div class="card"><div class="muted">Connected chains</div><div class="metric">0</div><div class="muted">Live integrations</div></div>
  </div>

  <section class="card">
    <h2>New token radar</h2>
    <div class="controls">
      <input id="search" placeholder="Search token, ticker or chain..." aria-label="Search tokens">
      <select id="chain" aria-label="Filter blockchain">
        <option value="">All blockchains</option>
        <option>Solana</option><option>Base</option><option>Ethereum</option>
        <option>BNB Chain</option><option>Arbitrum</option>
      </select>
      <select id="sort" aria-label="Sort tokens">
        <option value="momentum">Sort: Momentum</option>
        <option value="risk">Sort: Highest risk</option>
        <option value="liquidity">Sort: Liquidity</option>
      </select>
    </div>
    <div class="scroll">
      <table>
        <thead><tr><th>Token</th><th>Chain</th><th>Liquidity</th><th>Momentum</th><th>Risk</th><th>Watch</th></tr></thead>
        <tbody id="tokens"></tbody>
      </table>
    </div>
    <div class="muted" id="count" style="margin-top:12px"></div>
  </section>

  <div class="bottom">
    <section class="card">
      <h2>Safety monitor</h2>
      <div class="event"><strong class="red">High priority</strong><div class="muted">Example: concentrated holders and liquidity concerns</div></div>
      <div class="event"><strong class="yellow">Incomplete checks</strong><div class="muted">Contract permissions and sellability require verification</div></div>
      <div class="event"><strong class="green">Safety policy</strong><div class="muted">Unknown checks are never treated as safe</div></div>
    </section>
    <section class="card">
      <h2>News & narrative monitor</h2>
      <div class="event"><strong>Viral meme narratives</strong><div class="bar"><span style="width:82%"></span></div><div class="muted">Illustrative momentum: 82/100</div></div>
      <div class="event"><strong>Community discussion</strong><div class="bar"><span style="width:61%"></span></div><div class="muted">Illustrative momentum: 61/100</div></div>
      <div class="event"><strong>News connections</strong><div class="muted">No news providers connected</div></div>
    </section>
  </div>

  <section class="card" style="margin-top:17px">
    <h2>Telegram alerts</h2>
    <p class="muted">Alert types planned: new token discovery, critical safety findings, momentum spikes and liquidity drops.</p>
    <span class="pill">NOT CONNECTED</span>
    <p class="muted">A Telegram bot token and authorized destination will be needed to deliver real alerts securely.</p>
  </section>
  <footer>MemeWatch · Read-only monitoring · Example data is not a security audit or investment advice.</footer>
</main>
<script>
const data=[
 {s:"PEPEX",n:"Pepe X",c:"Base",l:18400,m:94,r:78,a:"4m"},
 {s:"SOLCAT",n:"Solana Cat",c:"Solana",l:76200,m:86,r:24,a:"12m"},
 {s:"NFROG",n:"News Frog",c:"Ethereum",l:142000,m:71,r:16,a:"28m"},
 {s:"MOONB",n:"Moon Bean",c:"BNB Chain",l:9100,m:63,r:88,a:"46m"},
 {s:"BASEDOG",n:"Base Dog",c:"Base",l:33500,m:57,r:35,a:"1h"},
 {s:"ARBPEPE",n:"Arb Pepe",c:"Arbitrum",l:51000,m:42,r:52,a:"2h"}
];
const watched=new Set();
const $=id=>document.getElementById(id);
function render(){
 let q=$("search").value.toLowerCase(), c=$("chain").value, sort=$("sort").value;
 let rows=data.filter(t=>(!c||t.c===c)&&(`${t.s} ${t.n} ${t.c}`).toLowerCase().includes(q));
 rows.sort((a,b)=>sort==="risk"?b.r-a.r:sort==="liquidity"?b.l-a.l:b.m-a.m);
 $("tokens").innerHTML=rows.map(t=>`<tr>
 <td><span class="token">${t.s}</span><span class="sub">${t.n} · ${t.a}</span></td>
 <td>${t.c}</td><td>$${t.l.toLocaleString("en-US")}</td>
 <td class="purple"><strong>${t.m}/100</strong></td>
 <td><span class="tag ${t.r>=60?"high":t.r>=30?"medium":"low"}">${t.r}/100</span></td>
 <td><button data-watch="${t.s}">${watched.has(t.s)?"★ Saved":"☆ Save"}</button></td>
 </tr>`).join("");
 $("count").textContent=`Showing ${rows.length} example tokens · Not live data`;
 document.querySelectorAll("[data-watch]").forEach(b=>b.onclick=()=>{
  let s=b.dataset.watch;watched.has(s)?watched.delete(s):watched.add(s);render();
 });
}
["search","chain","sort"].forEach(id=>$(id).addEventListener(id==="search"?"input":"change",render));
render();
</script>
</body>
</html>
