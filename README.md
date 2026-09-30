# USM Perfumes

A single-page perfume brand website for **USM**. It is one HTML file with no frameworks and no build step. Orders are sent to the seller through WhatsApp.

## Features

- Hero section with a CSS-drawn perfume bottle
- Product collection with 4 perfumes (name, notes, price)
- About section
- Order form that opens WhatsApp with a ready-made message
- Fully responsive (mobile and desktop)
- Respects reduced-motion settings

## How to run

1. Copy the code from the section below into a file named `index.html`.
2. Open the file in any browser.

No installation needed.

## Customize

| What to change | Where |
| --- | --- |
| WhatsApp number | `var WA="923000000000"` in the script (start with `92`, no `+`) |
| Footer number | The `<footer>` text |
| Perfumes, notes, prices | The `items` array in the script |
| Colors | The CSS variables in `:root` |

## Code

<details>
<summary>Click to view index.html</summary>

```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>USM Perfumes</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,400;0,600;1,400&family=Jost:wght@300;400;500&display=swap">
<style>
:root{--bg:#10282b;--bg2:#17363a;--ink:#efe8dc;--mute:#a9b8b3;--gold:#d9a441;--line:#2f4f52}
html{scroll-behavior:smooth}
*{box-sizing:border-box;margin:0}
body{background:var(--bg);color:var(--ink);font-family:Jost,system-ui,sans-serif;font-weight:300;line-height:1.6}
a{color:inherit}
:focus-visible{outline:2px solid var(--gold);outline-offset:3px}
header{display:flex;justify-content:space-between;align-items:center;padding:20px 6vw;border-bottom:1px solid var(--line)}
.logo{font-family:"Cormorant Garamond",serif;font-size:1.6rem;letter-spacing:.3em;text-decoration:none;font-weight:600}
nav a{margin-left:24px;text-decoration:none;color:var(--mute);font-size:.95rem}
nav a:hover{color:var(--gold)}
.hero{padding:9vh 6vw 8vh;display:grid;grid-template-columns:1.2fr 1fr;gap:5vw;align-items:center;min-height:78vh}
.hero h1{font-family:"Cormorant Garamond",serif;font-weight:400;font-size:clamp(2.6rem,6.5vw,5.6rem);line-height:1.02;letter-spacing:-.01em}
.hero h1 em{color:var(--gold)}
.hero p{margin:24px 0 32px;max-width:44ch;color:var(--mute);font-size:1.08rem}
.btn{display:inline-block;padding:14px 32px;border:1px solid var(--gold);background:var(--gold);color:#10282b;text-decoration:none;font-weight:500;letter-spacing:.04em;cursor:pointer}
.btn.ghost{background:none;color:var(--ink);margin-left:12px;border-color:var(--line)}
.btn:hover{filter:brightness(1.1)}
.bottle{justify-self:center;position:relative;width:min(280px,70vw);aspect-ratio:3/4.2;animation:rise 1.4s ease-out both}
.bottle .cap{position:absolute;left:36%;width:28%;height:16%;top:0;background:var(--gold);border-radius:4px 4px 0 0}
.bottle .neck{position:absolute;left:42%;width:16%;height:8%;top:16%;background:#b98a30}
.bottle .body{position:absolute;left:0;right:0;top:24%;bottom:0;border:2px solid var(--gold);border-radius:14px;background:linear-gradient(180deg,rgba(217,164,65,.08),rgba(217,164,65,.35));display:grid;place-items:center}
.bottle .body span{font-family:"Cormorant Garamond",serif;font-size:3.2rem;letter-spacing:.2em;padding-left:.2em;color:var(--gold)}
@keyframes rise{from{opacity:0;transform:translateY(24px)}to{opacity:1;transform:none}}
@media (prefers-reduced-motion:reduce){.bottle{animation:none}html{scroll-behavior:auto}}
section{padding:9vh 6vw}
h2{font-family:"Cormorant Garamond",serif;font-weight:400;font-size:clamp(2rem,4vw,3rem);margin-bottom:12px}
.sub{color:var(--mute);max-width:52ch;margin-bottom:44px}
.grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(230px,1fr));gap:24px}
.item{background:var(--bg2);padding:28px 24px 24px;display:flex;flex-direction:column}
.item .swatch{height:120px;margin-bottom:20px;display:grid;place-items:center;font-family:"Cormorant Garamond",serif;font-size:2.6rem}
.item h3{font-family:"Cormorant Garamond",serif;font-size:1.6rem;font-weight:600}
.item .notes{color:var(--mute);font-size:.92rem;margin:6px 0 16px;flex:1}
.item .row{display:flex;justify-content:space-between;align-items:center}
.price{color:var(--gold);font-size:1.1rem}
.item a.buy{font-size:.9rem;border-bottom:1px solid var(--gold);text-decoration:none;padding-bottom:2px}
.story{background:var(--bg2);display:grid;grid-template-columns:1fr 1fr;gap:6vw}
.story p{color:var(--mute);margin-bottom:16px;max-width:52ch}
.vals{display:grid;gap:18px}
.vals div{border-left:2px solid var(--gold);padding-left:16px}
.vals b{font-weight:500;display:block}
.vals span{color:var(--mute);font-size:.95rem}
form{display:grid;gap:14px;max-width:520px}
label{font-size:.9rem;color:var(--mute)}
input,select,textarea{width:100%;padding:12px 14px;background:transparent;border:1px solid var(--line);color:var(--ink);font:inherit;margin-top:4px}
select option{color:#10282b}
footer{padding:32px 6vw;border-top:1px solid var(--line);color:var(--mute);font-size:.9rem;display:flex;justify-content:space-between;flex-wrap:wrap;gap:8px}
@media (max-width:760px){.hero,.story{grid-template-columns:1fr}.hero{min-height:0}.bottle{order:-1;width:170px}nav a{margin-left:14px}.btn.ghost{margin:12px 0 0}}
</style>
</head>
<body>
<header>
  <a class="logo" href="#top">USM</a>
  <nav><a href="#collection">Collection</a><a href="#story">About</a><a href="#order">Order</a></nav>
</header>

<main id="top">
<div class="hero">
  <div>
    <h1>Khushbu jo aap ki <em>pehchan</em> banay.</h1>
    <p>USM ke perfumes oud, amber aur phoolon ki purani attar ki riwayat ko naye andaz mein pesh karte hain. Har bottle, din bhar ki mehak.</p>
    <a class="btn" href="#collection">Collection dekhein</a><a class="btn ghost" href="#order">Order karein</a>
  </div>
  <div class="bottle" aria-hidden="true"><div class="cap"></div><div class="neck"></div><div class="body"><span>USM</span></div></div>
</div>

<section id="collection">
  <h2>Collection</h2>
  <p class="sub">Chaar khushbuen, har mausam aur mauqe ke liye. Sab 50 ml Eau de Parfum.</p>
  <div class="grid" id="products"></div>
</section>

<section id="story" class="story">
  <div>
    <h2>USM ki kahani</h2>
    <p>USM ek chhota perfume brand hai jo khushbu ko sirf lagane ki cheez nahi, yaad banane ka zariya samajhta hai.</p>
    <p>Hum aisi mehak banate hain jo shaadi ki raat se le kar rozana ke office tak, har jagah acchi lage aur der tak rukay.</p>
  </div>
  <div class="vals">
    <div><b>Der tak qaim</b><span>8 se 10 ghantay ki performance.</span></div>
    <div><b>Asal ingredients</b><span>Oud, amber, musk aur gulab ka behtareen mix.</span></div>
    <div><b>Pure Pakistan mein delivery</b><span>Cash on delivery ki sahulat.</span></div>
  </div>
</section>

<section id="order">
  <h2>Order karein</h2>
  <p class="sub">Form bharein, aap ka order WhatsApp par hum tak pohanch jayega.</p>
  <form id="f">
    <label>Naam<input id="n" required></label>
    <label>Perfume<select id="p"></select></label>
    <label>Tadad<input id="q" type="number" min="1" value="1" required></label>
    <label>Pata aur shehar<textarea id="a" rows="2" required></textarea></label>
    <button class="btn" type="submit">WhatsApp par bhejein</button>
  </form>
</section>
</main>

<footer><span>© 2026 USM Perfumes</span><span>WhatsApp: +92 300 0000000</span></footer>

<script>
var WA="923000000000"; // apna WhatsApp number yahan likhein (92 se shuru, bina +)
var items=[
 {n:"USM Oud Noir",t:"Oud, black amber, saffron",p:8500,c:"#3b2a1f"},
 {n:"USM Gulab Raat",t:"Damask rose, musk, sandalwood",p:7200,c:"#5a2a3a"},
 {n:"USM Sehra",t:"Vetiver, cardamom, cedar",p:6800,c:"#5c5230"},
 {n:"USM Safed",t:"Jasmine, white musk, vanilla",p:6500,c:"#3d5559"}
];
var g=document.getElementById("products"),s=document.getElementById("p");
items.forEach(function(i){
  g.insertAdjacentHTML("beforeend",'<article class="item"><div class="swatch" style="background:'+i.c+';color:#d9a441">USM</div><h3>'+i.n+'</h3><p class="notes">'+i.t+'</p><div class="row"><span class="price">Rs '+i.p.toLocaleString()+'</span><a class="buy" href="#order" data-n="'+i.n+'">Order karein</a></div></article>');
  s.insertAdjacentHTML("beforeend","<option>"+i.n+"</option>");
});
g.addEventListener("click",function(e){var n=e.target.getAttribute("data-n");if(n)s.value=n;});
document.getElementById("f").addEventListener("submit",function(e){
  e.preventDefault();
  var it=items.filter(function(i){return i.n===s.value})[0],q=+document.getElementById("q").value;
  var m="Assalam o Alaikum, USM order:\nNaam: "+document.getElementById("n").value+"\nPerfume: "+it.n+" x "+q+"\nTotal: Rs "+(it.p*q).toLocaleString()+"\nPata: "+document.getElementById("a").value;
  window.open("https://wa.me/"+WA+"?text="+encodeURIComponent(m),"_blank");
});
</script>
</body>
</html>
```

</details>

## License

Free to use and modify for your own brand.
