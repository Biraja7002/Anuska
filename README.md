<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="theme-color" content="#090708">
<title>For Kyuutu — A Little World Made For You</title>

<style>
@import url('https://fonts.googleapis.com/css2?family=Cormorant+Garamond:wght@300;400;500;600;700&family=DM+Sans:wght@300;400;500&family=Parisienne&display=swap');

:root{
  --bg:#080607;
  --bg2:#11090c;
  --wine:#3d111d;
  --wine2:#6e2035;
  --gold:#d9b56d;
  --gold2:#f4ddb0;
  --cream:#f7ead0;
  --muted:#b8a9a0;
  --line:rgba(217,181,109,.25);
  --glow:rgba(217,181,109,.25);
}

*{
  box-sizing:border-box;
  margin:0;
  padding:0;
}

html{
  scroll-behavior:smooth;
}

body{
  background:
    radial-gradient(circle at 50% 0%,#281019 0%,#0b0709 38%,#050405 100%);
  color:var(--cream);
  font-family:"DM Sans",sans-serif;
  overflow-x:hidden;
}

body.locked{
  overflow:hidden;
}

::selection{
  background:var(--gold);
  color:#140b08;
}

/* -------------------------------------------------
   GLOBAL
------------------------------------------------- */

.section{
  position:relative;
  min-height:100vh;
  padding:120px 7vw;
  display:flex;
  align-items:center;
  justify-content:center;
  overflow:hidden;
}

.inner{
  width:min(1100px,100%);
  position:relative;
  z-index:3;
}

.eyebrow{
  color:var(--gold);
  letter-spacing:.28em;
  text-transform:uppercase;
  font-size:11px;
  margin-bottom:18px;
}

.title{
  font-family:"Cormorant Garamond",serif;
  font-weight:400;
  font-size:clamp(48px,8vw,105px);
  line-height:.9;
  letter-spacing:-.03em;
}

.subtitle{
  max-width:600px;
  color:var(--muted);
  line-height:1.9;
  font-size:14px;
  margin-top:25px;
}

.gold{
  color:var(--gold);
}

.center{
  text-align:center;
}

.btn{
  border:1px solid var(--line);
  background:rgba(255,255,255,.025);
  color:var(--cream);
  padding:15px 25px;
  border-radius:2px;
  cursor:pointer;
  letter-spacing:.15em;
  text-transform:uppercase;
  font-size:10px;
  transition:.45s ease;
  backdrop-filter:blur(12px);
}

.btn:hover{
  background:rgba(217,181,109,.12);
  border-color:var(--gold);
  box-shadow:0 0 30px rgba(217,181,109,.12);
  transform:translateY(-2px);
}

.line{
  width:70px;
  height:1px;
  background:var(--gold);
  margin:25px auto;
  opacity:.6;
}

.bg-glow{
  position:absolute;
  width:600px;
  height:600px;
  border-radius:50%;
  background:radial-gradient(circle,rgba(111,30,53,.28),transparent 68%);
  pointer-events:none;
}

/* -------------------------------------------------
   FILM GRAIN
------------------------------------------------- */

.grain{
  position:fixed;
  inset:0;
  pointer-events:none;
  z-index:1000;
  opacity:.045;
  background-image:url("data:image/svg+xml,%3Csvg viewBox='0 0 180 180' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='.9' numOctaves='3' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='.7'/%3E%3C/svg%3E");
}

/* -------------------------------------------------
   LOADER
------------------------------------------------- */

#loader{
  position:fixed;
  inset:0;
  z-index:999;
  background:#050405;
  display:flex;
  align-items:center;
  justify-content:center;
  transition:opacity 1.4s ease,visibility 1.4s;
}

#loader.hide{
  opacity:0;
  visibility:hidden;
}

.loader-content{
  text-align:center;
}

.loader-ring{
  width:90px;
  height:90px;
  border:1px solid rgba(217,181,109,.2);
  border-top-color:var(--gold);
  border-radius:50%;
  animation:spin 1.5s linear infinite;
  margin:0 auto 30px;
}

.loader-text{
  font-family:"Cormorant Garamond",serif;
  font-size:28px;
  color:var(--gold2);
}

@keyframes spin{
  to{transform:rotate(360deg)}
}

/* -------------------------------------------------
   AMBIENT PARTICLES
------------------------------------------------- */

#particles{
  position:fixed;
  inset:0;
  pointer-events:none;
  z-index:1;
}

.particle{
  position:absolute;
  width:2px;
  height:2px;
  background:#f0dca8;
  border-radius:50%;
  opacity:.35;
  animation:floatParticle linear infinite;
}

@keyframes floatParticle{
  0%{
    transform:translate3d(0,30px,0);
    opacity:0;
  }
  15%{opacity:.5}
  85%{opacity:.4}
  100%{
    transform:translate3d(30px,-100vh,0);
    opacity:0;
  }
}

/* -------------------------------------------------
   MUSIC
------------------------------------------------- */

#music{
  min-height:100vh;
  padding-top:80px;
  background:
    radial-gradient(circle at 50% 45%,rgba(101,27,48,.3),transparent 50%);
}

.music-wrap{
  text-align:center;
}

.music-title{
  font-family:"Cormorant Garamond",serif;
  font-size:clamp(55px,10vw,120px);
  font-weight:300;
}

.music-title span{
  color:var(--gold);
  font-style:italic;
}

.player{
  width:min(680px,100%);
  margin:45px auto 0;
  padding:28px;
  border:1px solid var(--line);
  background:rgba(10,6,8,.7);
  backdrop-filter:blur(20px);
  box-shadow:0 30px 80px rgba(0,0,0,.4);
}

.player-top{
  display:flex;
  align-items:center;
  justify-content:space-between;
  gap:20px;
}

.song-name{
  text-align:left;
}

.song-name small{
  display:block;
  color:#887a73;
  font-size:9px;
  letter-spacing:.2em;
  text-transform:uppercase;
  margin-bottom:7px;
}

.song-name strong{
  font-family:"Cormorant Garamond",serif;
  font-size:25px;
  font-weight:400;
}

.play{
  width:54px;
  height:54px;
  border-radius:50%;
  border:1px solid var(--gold);
  background:transparent;
  color:var(--gold);
  cursor:pointer;
  position:relative;
}

.play:before{
  content:"";
  position:absolute;
  left:21px;
  top:17px;
  width:0;
  height:0;
  border-top:9px solid transparent;
  border-bottom:9px solid transparent;
  border-left:13px solid var(--gold);
}

.play.pause:before{
  width:4px;
  height:17px;
  border:0;
  border-left:4px solid var(--gold);
  border-right:4px solid var(--gold);
  left:18px;
  top:18px;
}

.visualizer{
  height:50px;
  display:flex;
  justify-content:center;
  align-items:center;
  gap:4px;
  margin:25px 0;
}

.bar{
  width:3px;
  height:8px;
  background:var(--gold);
  opacity:.6;
  transition:height .2s;
}

.visualizer.active .bar{
  animation:eq .7s ease-in-out infinite alternate;
}

.bar:nth-child(2){animation-delay:.1s}
.bar:nth-child(3){animation-delay:.2s}
.bar:nth-child(4){animation-delay:.3s}
.bar:nth-child(5){animation-delay:.4s}
.bar:nth-child(6){animation-delay:.2s}
.bar:nth-child(7){animation-delay:.1s}

@keyframes eq{
  from{height:5px}
  to{height:35px}
}

.progress{
  width:100%;
  height:2px;
  background:#2a2020;
  cursor:pointer;
}

.progress-fill{
  width:0%;
  height:100%;
  background:var(--gold);
}

/* -------------------------------------------------
   OPENING
------------------------------------------------- */

#opening{
  min-height:100vh;
  background:
    radial-gradient(circle at 50% 50%,rgba(95,24,43,.25),transparent 45%),
    #070506;
}

.opening-light{
  position:absolute;
  width:500px;
  height:500px;
  border-radius:50%;
  background:radial-gradient(circle,rgba(238,202,128,.12),transparent 68%);
  filter:blur(15px);
  animation:breath 6s ease-in-out infinite;
}

@keyframes breath{
  0%,100%{transform:scale(.9);opacity:.5}
  50%{transform:scale(1.08);opacity:1}
}

.opening-content{
  text-align:center;
  position:relative;
}

.opening-content h1{
  font-family:"Cormorant Garamond",serif;
  font-weight:300;
  font-size:clamp(65px,13vw,170px);
  line-height:.8;
  letter-spacing:-.05em;
}

.opening-content h1 span{
  display:block;
  color:var(--gold);
  font-style:italic;
}

.opening-content p{
  margin:35px auto;
  color:#9d8d85;
  letter-spacing:.1em;
  font-size:12px;
}

/* -------------------------------------------------
   CAKE
------------------------------------------------- */

#cake-section{
  background:
    radial-gradient(circle at 50% 65%,rgba(217,181,109,.08),transparent 35%);
}

.cake-stage{
  text-align:center;
}

.cake{
  width:250px;
  height:190px;
  margin:80px auto 40px;
  position:relative;
  opacity:0;
  transform:translateY(80px) scale(.9);
  transition:1.5s cubic-bezier(.2,.8,.2,1);
}

.cake.show{
  opacity:1;
  transform:translateY(0) scale(1);
}

.plate{
  position:absolute;
  bottom:0;
  left:-30px;
  width:310px;
  height:18px;
  border-radius:50%;
  background:linear-gradient(#d5bb8a,#7e5b35);
  box-shadow:0 10px 35px rgba(0,0,0,.5);
}

.cake-layer{
  position:absolute;
  left:10px;
  width:230px;
  border-radius:8px;
  box-shadow:inset 0 -10px 15px rgba(0,0,0,.2),0 8px 15px rgba(0,0,0,.2);
}

.layer1{
  bottom:18px;
  height:55px;
  background:linear-gradient(90deg,#55202a,#8e3c4c,#4d1825);
}

.layer2{
  bottom:70px;
  height:48px;
  left:25px;
  width:200px;
  background:linear-gradient(90deg,#4a1824,#7d3040,#451522);
}

.cream-line{
  position:absolute;
  height:8px;
  border-radius:50%;
  background:#e7d2a4;
  left:35px;
  width:180px;
  bottom:105px;
  box-shadow:0 3px 8px rgba(0,0,0,.3);
}

.cream-drip{
  position:absolute;
  width:13px;
  height:22px;
  background:#e7d2a4;
  border-radius:0 0 10px 10px;
  bottom:90px;
}

.drip1{left:60px}
.drip2{left:105px;height:28px}
.drip3{left:150px;height:18px}

.candle{
  position:absolute;
  bottom:112px;
  width:8px;
  height:43px;
  background:linear-gradient(90deg,#8b632e,#f2d28e,#8b632e);
  border-radius:2px;
}

.c1{left:72px}
.c2{left:121px}
.c3{left:170px}

.flame{
  position:absolute;
  width:13px;
  height:20px;
  left:-2.5px;
  top:-23px;
  border-radius:50% 50% 50% 50%;
  background:
    radial-gradient(circle at 50% 70%,#fff5b4 0 18%,#ffd15c 20% 45%,#ff7a1c 60%,transparent 72%);
  filter:blur(.2px);
  transform-origin:50% 90%;
  animation:flame .16s infinite alternate ease-in-out;
  box-shadow:0 0 18px #ffad45,0 0 35px rgba(255,155,65,.35);
}

@keyframes flame{
  0%{transform:rotate(-4deg) scaleY(.95)}
  100%{transform:rotate(5deg) scaleY(1.1)}
}

.cake.out .flame{
  animation:none;
  opacity:0;
  transform:scale(.2);
  transition:.3s;
}

.smoke{
  position:absolute;
  width:5px;
  height:35px;
  border-radius:50%;
  background:linear-gradient(transparent,rgba(190,190,190,.15),transparent);
  top:-30px;
  opacity:0;
}

.cake.out .smoke{
  opacity:1;
  animation:smoke 2s ease-out forwards;
}

@keyframes smoke{
  0%{transform:translate(0,0) scale(.7);opacity:.4}
  100%{transform:translate(15px,-55px) scale(2);opacity:0}
}

.blow-btn{
  margin-top:15px;
}

/* -------------------------------------------------
   LIGHT OUT
------------------------------------------------- */

#cinematic-dark{
  position:fixed;
  inset:0;
  background:#000;
  z-index:200;
  opacity:0;
  visibility:hidden;
  pointer-events:none;
  transition:opacity 1.5s;
}

#cinematic-dark.active{
  opacity:.94;
  visibility:visible;
}

/* -------------------------------------------------
   WISH
------------------------------------------------- */

.wish-orb{
  width:170px;
  height:170px;
  margin:45px auto;
  border-radius:50%;
  border:1px solid rgba(217,181,109,.4);
  position:relative;
  box-shadow:0 0 60px rgba(217,181,109,.08);
  cursor:pointer;
}

.wish-orb:before{
  content:"";
  position:absolute;
  inset:30px;
  border-radius:50%;
  background:radial-gradient(circle,#f8dfa3,rgba(217,181,109,.2),transparent 70%);
  filter:blur(4px);
  transition:1s;
}

.wish-orb.wished{
  box-shadow:0 0 100px rgba(217,181,109,.4);
}

.wish-orb.wished:before{
  transform:scale(1.7);
  opacity:.8;
}

/* -------------------------------------------------
   SECRET CLUES
------------------------------------------------- */

.clues{
  display:grid;
  grid-template-columns:repeat(3,1fr);
  gap:18px;
  margin-top:50px;
}

.clue{
  min-height:190px;
  border:1px solid rgba(217,181,109,.16);
  background:rgba(255,255,255,.018);
  display:flex;
  flex-direction:column;
  align-items:center;
  justify-content:center;
  padding:25px;
  text-align:center;
  cursor:pointer;
  transition:.6s ease;
}

.clue:hover{
  border-color:var(--gold);
  background:rgba(217,181,109,.04);
}

.clue-number{
  color:var(--gold);
  font-family:"Cormorant Garamond",serif;
  font-size:40px;
  margin-bottom:12px;
}

.clue p{
  color:#8f817c;
  font-size:12px;
  line-height:1.6;
}

.clue.revealed{
  background:rgba(217,181,109,.07);
  box-shadow:inset 0 0 50px rgba(217,181,109,.04);
}

.key{
  width:80px;
  height:80px;
  margin:45px auto 0;
  border:1px solid var(--gold);
  border-radius:50%;
  display:flex;
  align-items:center;
  justify-content:center;
  color:var(--gold);
  opacity:0;
  transform:scale(.6);
  transition:1s;
  cursor:pointer;
}

.key.show{
  opacity:1;
  transform:scale(1);
}

/* -------------------------------------------------
   DOOR
------------------------------------------------- */

#door-section{
  min-height:100vh;
}

.door-frame{
  width:min(420px,80vw);
  height:570px;
  margin:50px auto;
  position:relative;
  perspective:1200px;
}

.room-glow{
  position:absolute;
  inset:15px;
  background:
    radial-gradient(circle at 50% 45%,rgba(255,209,128,.8),rgba(133,59,27,.5) 35%,transparent 70%);
  filter:blur(15px);
  opacity:0;
  transition:1.4s;
}

.door{
  position:absolute;
  inset:0;
  background:
    linear-gradient(90deg,#160c0e,#3a171d,#160b0d);
  border:2px solid #6b492d;
  transform-origin:left center;
  transition:2s cubic-bezier(.2,.8,.15,1);
  z-index:3;
  box-shadow:inset 0 0 40px rgba(0,0,0,.6);
}

.door:before{
  content:"";
  position:absolute;
  inset:25px;
  border:1px solid rgba(217,181,109,.25);
}

.door-handle{
  position:absolute;
  right:45px;
  top:50%;
  width:13px;
  height:13px;
  border-radius:50%;
  background:var(--gold);
  box-shadow:0 0 15px rgba(217,181,109,.4);
}

.door-frame.open .door{
  transform:rotateY(-108deg);
}

.door-frame.open .room-glow{
  opacity:1;
}

.room-content{
  position:absolute;
  inset:30px;
  z-index:1;
  display:flex;
  align-items:center;
  justify-content:center;
  flex-direction:column;
  text-align:center;
}

/* -------------------------------------------------
   LETTER
------------------------------------------------- */

.letter-wrap{
  max-width:750px;
  margin:50px auto;
  perspective:1200px;
}

.envelope{
  width:100%;
  min-height:300px;
  background:
    linear-gradient(135deg,#c8a66c,#ead8aa,#b28b4f);
  position:relative;
  cursor:pointer;
  box-shadow:0 30px 80px rgba(0,0,0,.45);
  transition:1s;
}

.envelope:before{
  content:"";
  position:absolute;
  inset:12px;
  border:1px solid rgba(70,40,15,.3);
}

.seal{
  position:absolute;
  left:50%;
  top:50%;
  transform:translate(-50%,-50%);
  width:70px;
  height:70px;
  border-radius:50%;
  background:#641d2d;
  border:2px solid #c49b5c;
  display:flex;
  align-items:center;
  justify-content:center;
  color:#e5c985;
  font-family:"Cormorant Garamond",serif;
  font-size:26px;
  z-index:5;
}

.letter{
  position:absolute;
  left:7%;
  width:86%;
  min-height:280px;
  top:10px;
  padding:45px;
  background:#efe2c5;
  color:#3a2923;
  transform:translateY(0);
  opacity:0;
  transition:1.3s cubic-bezier(.2,.8,.2,1);
  z-index:2;
  box-shadow:0 20px 50px rgba(0,0,0,.4);
}

.envelope.open .letter{
  transform:translateY(-150px);
  opacity:1;
}

.letter h3{
  font-family:"Parisienne",cursive;
  font-size:38px;
  color:#622133;
  margin-bottom:20px;
}

.letter p{
  font-family:"Cormorant Garamond",serif;
  font-size:20px;
  line-height:1.6;
}

/* -------------------------------------------------
   CONSTELLATION
------------------------------------------------- */

.constellation{
  width:min(750px,100%);
  height:480px;
  margin:45px auto;
  position:relative;
  border:1px solid rgba(217,181,109,.1);
  background:radial-gradient(circle at center,rgba(40,20,28,.6),transparent);
  overflow:hidden;
}

.constellation svg{
  width:100%;
  height:100%;
}

.constellation-star{
  fill:#e8d29b;
  cursor:pointer;
  transition:.4s;
  filter:drop-shadow(0 0 5px #d9b56d);
}

.constellation-star:hover{
  r:7;
}

.constellation-line{
  stroke:#c9a764;
  stroke-width:1;
  opacity:0;
  transition:1s;
}

.constellation.complete .constellation-line{
  opacity:.55;
}

.constellation-message{
  opacity:0;
  transition:1s;
  position:absolute;
  inset:0;
  display:flex;
  align-items:center;
  justify-content:center;
  pointer-events:none;
}

.constellation.complete .constellation-message{
  opacity:1;
}

.constellation-message span{
  font-family:"Cormorant Garamond",serif;
  font-size:42px;
  color:var(--gold2);
  text-shadow:0 0 30px rgba(217,181,109,.5);
}

/* -------------------------------------------------
   PET
------------------------------------------------- */

.pet-stage{
  width:320px;
  height:260px;
  margin:50px auto;
  position:relative;
  border:1px solid rgba(217,181,109,.15);
  background:radial-gradient(circle at 50% 65%,rgba(217,181,109,.09),transparent 55%);
  cursor:pointer;
}

.pet{
  position:absolute;
  left:50%;
  top:50%;
  width:115px;
  height:105px;
  transform:translate(-50%,-45%);
  animation:petBreath 3s ease-in-out infinite;
}

@keyframes petBreath{
  0%,100%{transform:translate(-50%,-45%) scaleY(1)}
  50%{transform:translate(-50%,-45%) scaleY(.96)}
}

.pet-body{
  position:absolute;
  bottom:0;
  left:10px;
  width:95px;
  height:70px;
  background:linear-gradient(145deg,#5b3039,#32151d);
  border-radius:48% 48% 42% 42%;
  box-shadow:inset 8px 5px 15px rgba(255,255,255,.06),0 15px 30px rgba(0,0,0,.4);
}

.pet-head{
  position:absolute;
  top:5px;
  left:17px;
  width:82px;
  height:72px;
  background:linear-gradient(145deg,#6c3944,#351720);
  border-radius:48% 48% 45% 45%;
}

.ear{
  position:absolute;
  top:-17px;
  width:32px;
  height:36px;
  background:#4d2530;
  transform:rotate(25deg);
  border-radius:8px 25px 5px 25px;
}

.ear.left{left:4px}
.ear.right{right:4px;transform:rotate(65deg)}

.eye{
  position:absolute;
  top:31px;
  width:6px;
  height:8px;
  border-radius:50%;
  background:#f4d994;
  box-shadow:0 0 7px #f4d994;
}

.eye.left{left:25px}
.eye.right{right:25px}

.nose{
  position:absolute;
  width:6px;
  height:5px;
  background:#c88d8d;
  border-radius:50%;
  left:38px;
  top:45px;
}

.pet-msg{
  text-align:center;
  margin-top:20px;
  color:#8e817b;
  font-size:12px;
}

/* -------------------------------------------------
   FLOWER GARDEN
------------------------------------------------- */

.garden{
  height:420px;
  position:relative;
  overflow:hidden;
  margin-top:50px;
  border-bottom:1px solid rgba(217,181,109,.15);
  background:
    linear-gradient(to bottom,transparent 0%,rgba(49,18,27,.15) 75%,rgba(26,12,17,.7));
}

.ground{
  position:absolute;
  bottom:0;
  left:0;
  right:0;
  height:55px;
  background:linear-gradient(#17100f,#0d0909);
}

.flower{
  position:absolute;
  bottom:45px;
  width:4px;
  height:0;
  background:#48604a;
  transition:1.4s cubic-bezier(.2,.8,.2,1);
  transform-origin:bottom;
}

.flower.bloom{
  height:180px;
}

.stem1{left:18%}
.stem2{left:35%;height:0}
.stem3{left:51%}
.stem4{left:67%}
.stem5{left:82%}

.flower-head{
  position:absolute;
  top:-15px;
  left:-16px;
  width:36px;
  height:36px;
  transform:scale(0);
  transition:1s .8s;
}

.flower.bloom .flower-head{
  transform:scale(1);
}

.petal{
  position:absolute;
  width:18px;
  height:25px;
  background:linear-gradient(#b96a7c,#612331);
  border-radius:50% 50% 45% 45%;
}

.petal:nth-child(1){left:9px;top:0}
.petal:nth-child(2){left:18px;top:7px;transform:rotate(72deg)}
.petal:nth-child(3){left:14px;top:18px;transform:rotate(144deg)}
.petal:nth-child(4){left:1px;top:18px;transform:rotate(216deg)}
.petal:nth-child(5){left:0;top:7px;transform:rotate(288deg)}

.flower-center{
  position:absolute;
  left:13px;
  top:12px;
  width:10px;
  height:10px;
  border-radius:50%;
  background:var(--gold);
  z-index:2;
}

/* -------------------------------------------------
   REASONS
------------------------------------------------- */

.reason-box{
  width:min(700px,100%);
  min-height:270px;
  margin:50px auto;
  border:1px solid rgba(217,181,109,.18);
  display:flex;
  align-items:center;
  justify-content:center;
  flex-direction:column;
  background:rgba(255,255,255,.015);
  padding:40px;
}

.reason-number{
  font-family:"Cormorant Garamond",serif;
  font-size:100px;
  line-height:.8;
  color:var(--gold);
}

.reason-text{
  margin:30px 0;
  font-family:"Cormorant Garamond",serif;
  font-size:28px;
  text-align:center;
  max-width:500px;
}

/* -------------------------------------------------
   RAIN WINDOW
------------------------------------------------- */

.rain-window{
  width:min(800px,100%);
  height:470px;
  margin:50px auto;
  position:relative;
  overflow:hidden;
  border:8px solid #211618;
  background:
    linear-gradient(180deg,#10101a,#25243a 60%,#17131a);
  box-shadow:0 30px 80px rgba(0,0,0,.5);
}

.window-light{
  position:absolute;
  width:170px;
  height:170px;
  border-radius:50%;
  background:radial-gradient(circle,rgba(245,203,122,.7),transparent 68%);
  right:100px;
  bottom:90px;
  filter:blur(12px);
}

.building{
  position:absolute;
  bottom:0;
  width:90px;
  background:#08080c;
}

.b1{left:30px;height:170px}
.b2{left:140px;height:230px}
.b3{right:100px;height:140px}
.b4{right:20px;height:200px}

.window-dot{
  position:absolute;
  width:5px;
  height:5px;
  background:#d7b96f;
  box-shadow:0 0 8px #d7b96f;
}

.rain{
  position:absolute;
  top:-40px;
  width:1px;
  height:35px;
  background:linear-gradient(transparent,rgba(190,205,220,.5));
  transform:rotate(12deg);
  animation:rainFall linear infinite;
}

@keyframes rainFall{
  to{transform:translate(-60px,550px) rotate(12deg)}
}

.window-message{
  position:absolute;
  left:50%;
  top:50%;
  transform:translate(-50%,-50%);
  width:80%;
  text-align:center;
  font-family:"Cormorant Garamond",serif;
  font-size:38px;
  text-shadow:0 2px 15px #000;
}

/* -------------------------------------------------
   SECRET MESSAGE
------------------------------------------------- */

.secret-box{
  width:150px;
  height:150px;
  margin:60px auto;
  border:1px solid var(--gold);
  position:relative;
  cursor:pointer;
  display:flex;
  align-items:center;
  justify-content:center;
  transition:.8s;
}

.secret-box:before,
.secret-box:after{
  content:"";
  position:absolute;
  background:var(--gold);
}

.secret-box:before{
  width:1px;
  height:100%;
}

.secret-box:after{
  height:1px;
  width:100%;
}

.secret-box span{
  font-family:"Cormorant Garamond",serif;
  font-size:13px;
  letter-spacing:.2em;
}

.secret-content{
  max-width:650px;
  margin:0 auto;
  text-align:center;
  opacity:0;
  transform:translateY(20px);
  transition:1s;
  pointer-events:none;
}

.secret-content.show{
  opacity:1;
  transform:translateY(0);
}

.secret-content h3{
  font-family:"Cormorant Garamond",serif;
  font-size:55px;
  font-weight:400;
}

.secret-content p{
  color:var(--muted);
  line-height:1.9;
  margin-top:20px;
}

/* -------------------------------------------------
   MOON
------------------------------------------------- */

.moon{
  width:170px;
  height:170px;
  margin:50px auto;
  border-radius:50%;
  background:
    radial-gradient(circle at 35% 30%,#fff2c9,#d6bb78 60%,#816536);
  box-shadow:0 0 80px rgba(220,193,125,.25);
  position:relative;
}

.moon:after{
  content:"";
  position:absolute;
  width:170px;
  height:170px;
  border-radius:50%;
  background:#0b0709;
  left:55px;
  top:-20px;
  transition:1.5s;
}

.moon.full:after{
  opacity:0;
}

/* -------------------------------------------------
   FINAL SKY
------------------------------------------------- */

#final{
  min-height:100vh;
  background:
    radial-gradient(circle at 50% 50%,rgba(80,23,40,.25),transparent 45%),
    #040304;
}

.final-title{
  font-family:"Cormorant Garamond",serif;
  font-size:clamp(60px,11vw,150px);
  line-height:.85;
  font-weight:300;
}

.final-title span{
  color:var(--gold);
  font-style:italic;
}

.final-line{
  width:120px;
  height:1px;
  background:var(--gold);
  margin:35px auto;
  opacity:.5;
}

.final-text{
  color:#9d8e87;
  max-width:550px;
  margin:auto;
  line-height:2;
  font-size:13px;
}

.credits{
  margin-top:70px;
  color:#645953;
  font-size:10px;
  letter-spacing:.25em;
  text-transform:uppercase;
}

/* -------------------------------------------------
   FLOATING HEARTS / STARS
------------------------------------------------- */

.float-heart{
  position:fixed;
  width:10px;
  height:10px;
  pointer-events:none;
  z-index:2;
  transform:rotate(45deg);
  opacity:0;
}

.float-heart:before,
.float-heart:after{
  content:"";
  position:absolute;
  width:10px;
  height:10px;
  background:rgba(188,74,100,.45);
  border-radius:50%;
}

.float-heart:before{
  left:-5px;
}

.float-heart:after{
  top:-5px;
}

.float-heart{
  background:rgba(188,74,100,.45);
}

@keyframes heartFloat{
  0%{transform:translateY(20px) rotate(45deg) scale(.5);opacity:0}
  15%{opacity:.5}
  85%{opacity:.3}
  100%{transform:translateY(-100vh) rotate(45deg) scale(1);opacity:0}
}

/* -------------------------------------------------
   RESPONSIVE
------------------------------------------------- */

@media(max-width:700px){

  .section{
    padding:90px 22px;
  }

  .clues{
    grid-template-columns:1fr;
  }

  .clue{
    min-height:140px;
  }

  .player{
    padding:20px;
  }

  .cake{
    transform:translateY(80px) scale(.75);
  }

  .cake.show{
    transform:translateY(0) scale(.75);
  }

  .door-frame{
    height:480px;
  }

  .letter{
    padding:30px 22px;
  }

  .letter p{
    font-size:17px;
  }

  .envelope.open .letter{
    transform:translateY(-110px);
  }

  .constellation{
    height:360px;
  }

  .window-message{
    font-size:28px;
  }

  .reason-number{
    font-size:80px;
  }

  .reason-text{
    font-size:23px;
  }
}

@media(prefers-reduced-motion:reduce){
  *,*:before,*:after{
    animation-duration:.01ms!important;
    animation-iteration-count:1!important;
    scroll-behavior:auto!important;
    transition-duration:.01ms!important;
  }
}
</style>
</head>

<body class="locked">

<div id="loader">
  <div class="loader-content">
    <div class="loader-ring"></div>
    <div class="loader-text">A little world is waiting...</div>
  </div>
</div>

<div class="grain"></div>
<div id="particles"></div>
<div id="cinematic-dark"></div>

<!-- =================================================
     MUSIC — AT THE VERY TOP
================================================= -->

<section id="music" class="section">
  <div class="inner music-wrap">

    <div class="eyebrow">Press play</div>

    <h1 class="music-title">
      <span>Tera Naam Doon</span>
    </h1>

    <div class="line"></div>

    <p class="subtitle" style="margin-left:auto;margin-right:auto;text-align:center;">
      Before anything else begins, let the music stay with you.
    </p>

    <div class="player">

      <div class="player-top">

        <div class="song-name">
          <small>Now playing</small>
          <strong>tera naam doon.mp3</strong>
        </div>

        <button class="play" id="playBtn" aria-label="Play music"></button>

      </div>

      <div class="visualizer" id="visualizer">
        <div class="bar"></div>
        <div class="bar"></div>
        <div class="bar"></div>
        <div class="bar"></div>
        <div class="bar"></div>
        <div class="bar"></div>
        <div class="bar"></div>
      </div>

      <div class="progress" id="progress">
        <div class="progress-fill" id="progressFill"></div>
      </div>

    </div>

    <div style="margin-top:60px;">
      <button class="btn" onclick="goTo('opening')">Enter</button>
    </div>

  </div>
</section>

<audio id="song" preload="auto">
  <source src="tera naam doon.mp3" type="audio/mpeg">
</audio>

<!-- =================================================
     CINEMATIC OPENING
================================================= -->

<section id="opening" class="section">
  <div class="opening-light"></div>

  <div class="opening-content inner">

    <div class="eyebrow">A night made for one person</div>

    <h1>
      Tonight
      <span>is yours.</span>
    </h1>

    <p>
      Kyuutu, this little world was made<br>
      with nothing but you in mind.
    </p>

    <button class="btn" onclick="goTo('cake-section')">
      Begin
    </button>

  </div>
</section>

<!-- =================================================
     CAKE
================================================= -->

<section id="cake-section" class="section">

  <div class="inner cake-stage">

    <div class="eyebrow">The moment begins</div>

    <h2 class="title">Make a wish.</h2>

    <p class="subtitle" style="margin-left:auto;margin-right:auto;">
      Three little flames. One very special birthday.
    </p>

    <div class="cake" id="cake">

      <div class="plate"></div>

      <div class="cake-layer layer1"></div>
      <div class="cake-layer layer2"></div>

      <div class="cream-line"></div>
      <div class="cream-drip drip1"></div>
      <div class="cream-drip drip2"></div>
      <div class="cream-drip drip3"></div>

      <div class="candle c1">
        <div class="flame"></div>
        <div class="smoke"></div>
      </div>

      <div class="candle c2">
        <div class="flame"></div>
        <div class="smoke"></div>
      </div>

      <div class="candle c3">
        <div class="flame"></div>
        <div class="smoke"></div>
      </div>

    </div>

    <button class="btn blow-btn" id="blowBtn">
      Blow the candles
    </button>

    <p id="blowText"
       style="margin-top:25px;color:#8e8079;font-size:12px;opacity:0;transition:1s;">
      And just like that... your wish belongs to the stars.
    </p>

  </div>

</section>

<!-- =================================================
     WISH
================================================= -->

<section id="wish" class="section">

  <div class="inner center">

    <div class="eyebrow">Keep one wish for yourself</div>

    <h2 class="title">
      Close your eyes.
    </h2>

    <p class="subtitle" style="margin-left:auto;margin-right:auto;">
      Tap the light when you've made your wish.
    </p>

    <div class="wish-orb" id="wishOrb"></div>

    <p id="wishResult"
       style="color:var(--gold);opacity:0;transition:1s;">
       The stars heard you.
    </p>

  </div>

</section>

<!-- =================================================
     SECRET CLUES
================================================= -->

<section id="clues" class="section">

  <div class="inner">

    <div class="center">
      <div class="eyebrow">Something is hidden</div>

      <h2 class="title">Look closer.</h2>

      <p class="subtitle" style="margin-left:auto;margin-right:auto;text-align:center;">
        Three small secrets are scattered through this night.
        Find them all.
      </p>
    </div>

    <div class="clues">

      <div class="clue" data-clue="1">
        <div class="clue-number">I</div>
        <p>Some things are easier to find when you stop looking for them.</p>
      </div>

      <div class="clue" data-clue="2">
        <div class="clue-number">II</div>
        <p>A memory can hide inside a single little light.</p>
      </div>

      <div class="clue" data-clue="3">
        <div class="clue-number">III</div>
        <p>The last secret is waiting somewhere you already visited.</p>
      </div>

    </div>

    <div class="key" id="key">
      KEY
    </div>

    <p id="keyText"
       class="center"
       style="opacity:0;color:var(--gold);margin-top:20px;transition:1s;">
      You found it.
    </p>

  </div>

</section>

<!-- =================================================
     SECRET DOOR
================================================= -->

<section id="door-section" class="section">

  <div class="inner center">

    <div class="eyebrow">The hidden room</div>

    <h2 class="title">One last door.</h2>

    <p class="subtitle" style="margin-left:auto;margin-right:auto;">
      Some surprises aren't meant to be seen immediately.
    </p>

    <div class="door-frame" id="doorFrame">

      <div class="room-glow"></div>

      <div class="room-content">
        <div class="eyebrow">Welcome inside</div>
        <h3 style="font-family:'Cormorant Garamond';font-size:45px;font-weight:400;">
          For you.
        </h3>
      </div>

      <div class="door">
        <div class="door-handle"></div>
      </div>

    </div>

    <button class="btn" id="openDoor">
      Use the key
    </button>

  </div>

</section>

<!-- =================================================
     LETTER
================================================= -->

<section id="letter-section" class="section">

  <div class="inner">

    <div class="center">

      <div class="eyebrow">Something I wanted to say</div>

      <h2 class="title">A letter.</h2>

      <p class="subtitle" style="margin-left:auto;margin-right:auto;text-align:center;">
        Some feelings deserve more than a message on a screen.
      </p>

    </div>

    <div class="letter-wrap">

      <div class="envelope" id="envelope">

        <div class="letter">

          <h3>For Kyuutu,</h3>

          <p>
            I don't know if a website can ever explain what someone means
            to you, but I wanted to try anyway.
            <br><br>
            In a world full of ordinary days, somehow you became one of
            those little things that make everything feel a little more
            beautiful.
            <br><br>
            So today isn't just about wishing you a happy birthday.
            It's about celebrating the person you are, the smile you have,
            and every little moment that somehow becomes a memory.
            <br><br>
            I hope this year gives you reasons to smile that you never
            expected.
            <br><br>
            And whenever you look back at this little night,
            I hope you remember that someone made it just for you.
          </p>

          <p style="margin-top:30px;">
            — With love, Biraja
          </p>

        </div>

        <div class="seal">K</div>

      </div>

    </div>

    <div class="center">
      <button class="btn" id="openLetter">Open the letter</button>
    </div>

  </div>

</section>

<!-- =================================================
     CONSTELLATION
================================================= -->

<section id="constellation-section" class="section">

  <div class="inner">

    <div class="center">

      <div class="eyebrow">Our little sky</div>

      <h2 class="title">Connect the stars.</h2>

      <p class="subtitle" style="margin-left:auto;margin-right:auto;text-align:center;">
        Touch every glowing star.
      </p>

    </div>

    <div class="constellation" id="constellation">

      <svg viewBox="0 0 750 480">

        <line class="constellation-line" x1="120" y1="320" x2="220" y2="210"/>
        <line class="constellation-line" x1="220" y1="210" x2="315" y2="145"/>
        <line class="constellation-line" x1="315" y1="145" x2="375" y2="250"/>
        <line class="constellation-line" x1="375" y1="250" x2="435" y2="145"/>
        <line class="constellation-line" x1="435" y1="145" x2="530" y2="210"/>
        <line class="constellation-line" x1="530" y1="210" x2="630" y2="320"/>
        <line class="constellation-line" x1="630" y1="320" x2="375" y2="380"/>
        <line class="constellation-line" x1="375" y1="380" x2="120" y2="320"/>

        <circle class="constellation-star" cx="120" cy="320" r="4"/>
        <circle class="constellation-star" cx="220" cy="210" r="4"/>
        <circle class="constellation-star" cx="315" cy="145" r="4"/>
        <circle class="constellation-star" cx="375" cy="250" r="4"/>
        <circle class="constellation-star" cx="435" cy="145" r="4"/>
        <circle class="constellation-star" cx="530" cy="210" r="4"/>
        <circle class="constellation-star" cx="630" cy="320" r="4"/>
        <circle class="constellation-star" cx="375" cy="380" r="4"/>

      </svg>

      <div class="constellation-message">
        <span>Kyuutu</span>
      </div>

    </div>

  </div>

</section>

<!-- =================================================
     VIRTUAL PET
================================================= -->

<section id="pet-section" class="section">

  <div class="inner center">

    <div class="eyebrow">You found a little friend</div>

    <h2 class="title">Someone wanted to meet you.</h2>

    <p class="subtitle" style="margin-left:auto;margin-right:auto;">
      Tap the little companion.
    </p>

    <div class="pet-stage" id="petStage">

      <div class="pet">

        <div class="ear left"></div>
        <div class="ear right"></div>

        <div class="pet-head">
          <div class="eye left"></div>
          <div class="eye right"></div>
          <div class="nose"></div>
        </div>

        <div class="pet-body"></div>

      </div>

    </div>

    <p class="pet-msg" id="petMsg">
      It seems to like you already.
    </p>

  </div>

</section>

<!-- =================================================
     FLOWER GARDEN
================================================= -->

<section id="garden-section" class="section">

  <div class="inner">

    <div class="center">

      <div class="eyebrow">Let something beautiful grow</div>

      <h2 class="title">A garden for you.</h2>

      <p class="subtitle" style="margin-left:auto;margin-right:auto;text-align:center;">
        Every flower carries one little reason.
      </p>

    </div>

    <div class="garden" id="garden">

      <div class="ground"></div>

      <div class="flower stem1">
        <div class="flower-head">
          <i class="petal"></i><i class="petal"></i><i class="petal"></i>
          <i class="petal"></i><i class="petal"></i>
          <b class="flower-center"></b>
        </div>
      </div>

      <div class="flower stem2">
        <div class="flower-head">
          <i class="petal"></i><i class="petal"></i><i class="petal"></i>
          <i class="petal"></i><i class="petal"></i>
          <b class="flower-center"></b>
        </div>
      </div>

      <div class="flower stem3">
        <div class="flower-head">
          <i class="petal"></i><i class="petal"></i><i class="petal"></i>
          <i class="petal"></i><i class="petal"></i>
          <b class="flower-center"></b>
        </div>
      </div>

      <div class="flower stem4">
        <div class="flower-head">
          <i class="petal"></i><i class="petal"></i><i class="petal"></i>
          <i class="petal"></i><i class="petal"></i>
          <b class="flower-center"></b>
        </div>
      </div>

      <div class="flower stem5">
        <div class="flower-head">
          <i class="petal"></i><i class="petal"></i><i class="petal"></i>
          <i class="petal"></i><i class="petal"></i>
          <b class="flower-center"></b>
        </div>
      </div>

    </div>

    <div class="center" style="margin-top:35px;">
      <button class="btn" id="bloomBtn">
        Let it bloom
      </button>
    </div>

  </div>

</section>

<!-- =================================================
     REASONS COUNTER
================================================= -->

<section id="reasons" class="section">

  <div class="inner center">

    <div class="eyebrow">I could keep going</div>

    <h2 class="title">Reasons.</h2>

    <p class="subtitle" style="margin-left:auto;margin-right:auto;">
      There are probably more than I could ever count.
    </p>

    <div class="reason-box">

      <div class="reason-number" id="reasonNumber">0</div>

      <div class="reason-text" id="reasonText">
        Because you're you.
      </div>

      <button class="btn" id="reasonBtn">
        Give me another
      </button>

    </div>

  </div>

</section>

<!-- =================================================
     RAIN / NIGHT WINDOW
================================================= -->

<section id="rain-section" class="section">

  <div class="inner center">

    <div class="eyebrow">Imagine this</div>

    <h2 class="title">If you were here.</h2>

    <p class="subtitle" style="margin-left:auto;margin-right:auto;">
      A quiet night. Rain outside. Warm light inside.
    </p>

    <div class="rain-window">

      <div class="window-light"></div>

      <div class="building b1"></div>
      <div class="building b2"></div>
      <div class="building b3"></div>
      <div class="building b4"></div>

      <div class="window-message">
        Maybe I'd just sit beside you
        and let the whole world stay quiet.
      </div>

    </div>

  </div>

</section>

<!-- =================================================
     SECRET MESSAGE
================================================= -->

<section id="secret-section" class="section">

  <div class="inner center">

    <div class="eyebrow">Not everything should be obvious</div>

    <h2 class="title">One last secret.</h2>

    <div class="secret-box" id="secretBox">
      <span>OPEN</span>
    </div>

    <div class="secret-content" id="secretContent">

      <h3>
        You are someone's favorite thought.
      </h3>

      <p>
        On ordinary days. On difficult days.
        On the days when nothing special happens.
        Somehow, you still have a way of making a place
        in someone's thoughts.
      </p>

    </div>

  </div>

</section>

<!-- =================================================
     MOON
================================================= -->

<section id="moon-section" class="section">

  <div class="inner center">

    <div class="eyebrow">Before the night ends</div>

    <h2 class="title">Look at the moon.</h2>

    <div class="moon" id="moon"></div>

    <p id="moonText"
       class="subtitle"
       style="margin-left:auto;margin-right:auto;text-align:center;">
      Even the night feels a little softer tonight.
    </p>

    <button class="btn" id="moonBtn" style="margin-top:30px;">
      Make it full
    </button>

  </div>

</section>

<!-- =================================================
     FINAL
================================================= -->

<section id="final" class="section">

  <div class="inner center">

    <div class="eyebrow">And finally...</div>

    <h1 class="final-title">
      Happy
      <span>Birthday.</span>
    </h1>

    <div class="final-line"></div>

    <p class="final-text">
      I hope somewhere between the music, the stars,
      the little secrets and all these quiet moments,
      you felt how special you are.
      <br><br>
      This wasn't meant to be just a birthday website.
      It was meant to be a tiny world where,
      for a little while,
      everything was about you.
    </p>

    <div class="credits">
      Made with love — Biraja
    </div>

  </div>

</section>

<script>

/* =================================================
   BASIC NAVIGATION
================================================= */

function goTo(id){
  document.getElementById(id)?.scrollIntoView({
    behavior:"smooth"
  });
}

/* =================================================
   LOADER
================================================= */

window.addEventListener("load",()=>{

  setTimeout(()=>{
    document.getElementById("loader").classList.add("hide");
    document.body.classList.remove("locked");
  },1800);

});

/* =================================================
   PARTICLES
================================================= */

const particleContainer=document.getElementById("particles");

for(let i=0;i<45;i++){

  const p=document.createElement("div");

  p.className="particle";

  p.style.left=Math.random()*100+"%";
  p.style.top=(60+Math.random()*50)+"%";
  p.style.animationDuration=(7+Math.random()*12)+"s";
  p.style.animationDelay=(Math.random()*10)+"s";
  p.style.opacity=.15+Math.random()*.35;

  particleContainer.appendChild(p);
}

/* =================================================
   FLOATING HEARTS
================================================= */

function createHeart(){

  const h=document.createElement("div");

  h.className="float-heart";

  h.style.left=Math.random()*100+"vw";
  h.style.bottom="-20px";
  h.style.animation=`heartFloat ${8+Math.random()*8}s linear forwards`;

  document.body.appendChild(h);

  setTimeout(()=>h.remove(),17000);
}

setInterval(createHeart,2200);

/* =================================================
   MUSIC PLAYER
================================================= */

const song=document.getElementById("song");
const playBtn=document.getElementById("playBtn");
const visualizer=document.getElementById("visualizer");
const progress=document.getElementById("progress");
const progressFill=document.getElementById("progressFill");

playBtn.addEventListener("click",()=>{

  if(song.paused){

    song.play().catch(()=>{});

    playBtn.classList.add("pause");
    visualizer.classList.add("active");

  }else{

    song.pause();

    playBtn.classList.remove("pause");
    visualizer.classList.remove("active");

  }

});

song.addEventListener("timeupdate",()=>{

  if(song.duration){

    progressFill.style.width=
      (song.currentTime/song.duration*100)+"%";

  }

});

progress.addEventListener("click",(e)=>{

  if(!song.duration)return;

  const rect=progress.getBoundingClientRect();

  const percent=(e.clientX-rect.left)/rect.width;

  song.currentTime=percent*song.duration;

});

/* =================================================
   CAKE ENTRANCE
================================================= */

const cake=document.getElementById("cake");

const cakeObserver=new IntersectionObserver(entries=>{

  entries.forEach(entry=>{

    if(entry.isIntersecting){
      cake.classList.add("show");
    }

  });

},{threshold:.3});

cakeObserver.observe(cake);

/* =================================================
   BLOW CANDLES
================================================= */

const blowBtn=document.getElementById("blowBtn");
const blowText=document.getElementById("blowText");
const cinematicDark=document.getElementById("cinematic-dark");

let candlesBlown=false;

blowBtn.addEventListener("click",()=>{

  if(candlesBlown)return;

  candlesBlown=true;

  cake.classList.add("out");

  blowBtn.textContent="Wish made";

  blowText.style.opacity="1";

  setTimeout(()=>{

    cinematicDark.classList.add("active");

    setTimeout(()=>{

      cinematicDark.classList.remove("active");

    },1800);

  },350);

});

/* =================================================
   WISH ORB
================================================= */

const wishOrb=document.getElementById("wishOrb");
const wishResult=document.getElementById("wishResult");

wishOrb.addEventListener("click",()=>{

  wishOrb.classList.add("wished");

  wishResult.style.opacity="1";

});

/* =================================================
   SECRET CLUES
================================================= */

const clues=document.querySelectorAll(".clue");
const key=document.getElementById("key");
const keyText=document.getElementById("keyText");

let foundClues=new Set();

clues.forEach(clue=>{

  clue.addEventListener("click",()=>{

    const id=clue.dataset.clue;

    if(foundClues.has(id))return;

    foundClues.add(id);

    clue.classList.add("revealed");

    clue.querySelector("p").textContent=
      [
        "The first secret: you make ordinary moments feel different.",
        "The second secret: some memories don't need photographs.",
        "The third secret: there is always a little more to discover."
      ][Number(id)-1];

    if(foundClues.size===3){

      setTimeout(()=>{

        key.classList.add("show");

        keyText.style.opacity="1";

      },500);

    }

  });

});

/* =================================================
   SECRET KEY / DOOR
================================================= */

const openDoor=document.getElementById("openDoor");
const doorFrame=document.getElementById("doorFrame");

openDoor.addEventListener("click",()=>{

  if(foundClues.size<3){

    openDoor.textContent="Find the three clues first";

    setTimeout(()=>{
      openDoor.textContent="Use the key";
    },1800);

    return;
  }

  doorFrame.classList.add("open");

  openDoor.textContent="Welcome inside";

});

/* =================================================
   LETTER
================================================= */

const envelope=document.getElementById("envelope");
const openLetter=document.getElementById("openLetter");

openLetter.addEventListener("click",()=>{

  envelope.classList.toggle("open");

  openLetter.textContent=
    envelope.classList.contains("open")
    ?"Close the letter"
    :"Open the letter";

});

/* =================================================
   CONSTELLATION
================================================= */

const constellation=
document.getElementById("constellation");

const constellationStars=
document.querySelectorAll(".constellation-star");

let starsFound=0;

const starOrder=new Set();

const constellationMessages=[
  "A little light for every memory.",
  "Some moments stay.",
  "Some people stay longer.",
  "Somewhere in the middle of it all...",
  "you became special.",
  "And this little sky is yours.",
  "Almost there.",
  "Found you."
];

const starLabels=document.createElement("div");

starLabels.style.position="absolute";
starLabels.style.bottom="22px";
starLabels.style.left="0";
starLabels.style.right="0";
starLabels.style.textAlign="center";
starLabels.style.color="#9e8d84";
starLabels.style.fontSize="11px";
starLabels.style.pointerEvents="none";
starLabels.textContent="";

const constellationParent=constellation;
const msg=constellation.querySelector(".constellation-message");

constellationStars.forEach((star,i)=>{

  star.addEventListener("click",()=>{

    if(starOrder.has(i))return;

    starOrder.add(i);
    starsFound++;

    star.style.fill="#fff1bd";
    star.setAttribute("r","7");

    starLabels.textContent=
      constellationMessages[i] || "A little memory.";

    if(starsFound===constellationStars.length){

      constellation.classList.add("complete");

      setTimeout(()=>{
        starLabels.textContent="A sky made just for Kyuutu.";
      },1000);

    }

  });

});

constellation.appendChild(starLabels);

/* =================================================
   PET
================================================= */

const petStage=document.getElementById("petStage");
const petMsg=document.getElementById("petMsg");

let petClicks=0;

petStage.addEventListener("click",()=>{

  petClicks++;

  const messages=[
    "It blinked. I think it likes you.",
    "Okay... now it definitely likes you.",
    "It has officially chosen you.",
    "I think you have a new little friend.",
    "It says happy birthday."
  ];

  petMsg.textContent=
    messages[Math.min(petClicks-1,messages.length-1)];

});

/* =================================================
   FLOWER GARDEN
================================================= */

const bloomBtn=document.getElementById("bloomBtn");
const flowers=document.querySelectorAll(".flower");

bloomBtn.addEventListener("click",()=>{

  flowers.forEach((flower,i)=>{

    setTimeout(()=>{

      flower.classList.add("bloom");

    },i*260);

  });

  bloomBtn.textContent="The garden is yours";

});

/* =================================================
   REASONS COUNTER
================================================= */

const reasonNumber=document.getElementById("reasonNumber");
const reasonText=document.getElementById("reasonText");
const reasonBtn=document.getElementById("reasonBtn");

const reasons=[
  "Because your smile changes the mood.",
  "Because you make little moments memorable.",
  "Because you're wonderfully you.",
  "Because some conversations stay in my mind.",
  "Because your presence feels different.",
  "Because you have your own kind of magic.",
  "Because you make ordinary days less ordinary.",
  "Because there is always another reason.",
  "Because this list could honestly go on forever.",
  "Because you're Kyuutu."
];

let reasonIndex=0;
let displayedNumber=0;

reasonBtn.addEventListener("click",()=>{

  reasonIndex=(reasonIndex+1)%reasons.length;

  displayedNumber++;

  reasonNumber.textContent=displayedNumber;

  reasonText.style.opacity="0";
  reasonText.style.transform="translateY(10px)";

  setTimeout(()=>{

    reasonText.textContent=reasons[reasonIndex];

    reasonText.style.opacity="1";
    reasonText.style.transform="translateY(0)";

  },250);

});

/* =================================================
   RAIN
================================================= */

const rainWindow=document.querySelector(".rain-window");

for(let i=0;i<70;i++){

  const drop=document.createElement("div");

  drop.className="rain";

  drop.style.left=Math.random()*100+"%";
  drop.style.animationDuration=(.7+Math.random()*1.1)+"s";
  drop.style.animationDelay=(Math.random()*2)+"s";
  drop.style.opacity=.15+Math.random()*.35;

  rainWindow.appendChild(drop);
}

/* =================================================
   SECRET MESSAGE
================================================= */

const secretBox=document.getElementById("secretBox");
const secretContent=document.getElementById("secretContent");

secretBox.addEventListener("click",()=>{

  secretBox.style.transform="rotate(45deg) scale(.5)";
  secretBox.style.opacity="0";

  setTimeout(()=>{

    secretContent.classList.add("show");

  },700);

});

/* =================================================
   MOON
================================================= */

const moon=document.getElementById("moon");
const moonBtn=document.getElementById("moonBtn");

moonBtn.addEventListener("click",()=>{

  moon.classList.toggle("full");

  moonBtn.textContent=
    moon.classList.contains("full")
    ?"The moon is full"
    :"Make it full";

});

/* =================================================
   POINTER LIGHT
================================================= */

let pointerX=0;
let pointerY=0;

const pointerGlow=document.createElement("div");

pointerGlow.style.position="fixed";
pointerGlow.style.width="180px";
pointerGlow.style.height="180px";
pointerGlow.style.borderRadius="50%";
pointerGlow.style.pointerEvents="none";
pointerGlow.style.zIndex="0";
pointerGlow.style.background=
  "radial-gradient(circle,rgba(217,181,109,.055),transparent 70%)";
pointerGlow.style.transform="translate(-50%,-50%)";

document.body.appendChild(pointerGlow);

window.addEventListener("pointermove",(e)=>{

  pointerX=e.clientX;
  pointerY=e.clientY;

  pointerGlow.style.left=pointerX+"px";
  pointerGlow.style.top=pointerY+"px";

});

/* =================================================
   SMOOTH SECTION REVEALS
================================================= */

const sections=document.querySelectorAll(".section");

const revealObserver=new IntersectionObserver(entries=>{

  entries.forEach(entry=>{

    if(entry.isIntersecting){

      entry.target.style.opacity="1";
      entry.target.style.transform="translateY(0)";

    }

  });

},{
  threshold:.08
});

sections.forEach(section=>{

  if(
    section.id!=="music" &&
    section.id!=="opening"
  ){

    section.style.opacity=".35";
    section.style.transform="translateY(20px)";
    section.style.transition=
      "opacity 1.2s ease, transform 1.2s ease";

  }

  revealObserver.observe(section);

});

/* =================================================
   FINAL SKY STARS
================================================= */

const finalSection=document.getElementById("final");

for(let i=0;i<70;i++){

  const star=document.createElement("div");

  star.style.position="absolute";
  star.style.width=(Math.random()*2+1)+"px";
  star.style.height=star.style.width;
  star.style.borderRadius="50%";
  star.style.background="#e7d39b";
  star.style.opacity=.15+Math.random()*.65;
  star.style.left=Math.random()*100+"%";
  star.style.top=Math.random()*100+"%";
  star.style.boxShadow="0 0 7px rgba(217,181,109,.35)";
  star.style.animation=
    `twinkle ${2+Math.random()*4}s ease-in-out infinite alternate`;

  finalSection.appendChild(star);

}

const starStyle=document.createElement("style");

starStyle.textContent=`
@keyframes twinkle{
  from{opacity:.15;transform:scale(.7)}
  to{opacity:.85;transform:scale(1.4)}
}
`;

document.head.appendChild(starStyle);

</script>

</body>
</html>
