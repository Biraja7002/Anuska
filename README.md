# Anuska
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>For Kyuutu — A Birthday Story</title>

<style>
@import url('https://fonts.googleapis.com/css2?family=Cormorant+Garamond:wght@300;400;500;600&family=Inter:wght@300;400;500&display=swap');

:root{
    --bg:#050507;
    --burgundy:#32151e;
    --rose:#d99aa9;
    --gold:#d8b27c;
    --cream:#f4e9dc;
    --muted:#a8a1a4;
}

*{
    margin:0;
    padding:0;
    box-sizing:border-box;
}

html{
    scroll-behavior:smooth;
}

body{
    background:var(--bg);
    color:white;
    font-family:Inter,sans-serif;
    overflow-x:hidden;
}

body::selection{
    background:#b86c7c;
    color:white;
}

/* =====================================================
   GLOBAL CINEMATIC BACKGROUND
===================================================== */

#background{
    position:fixed;
    inset:0;
    z-index:-20;
    overflow:hidden;
    background:
        radial-gradient(
            ellipse at 50% 20%,
            rgba(92,38,51,.28),
            transparent 45%
        ),
        #050507;
}

.ambient{
    position:absolute;
    width:60vw;
    height:60vw;
    border-radius:50%;
    filter:blur(100px);
    opacity:.12;
    animation:ambientMove 18s ease-in-out infinite alternate;
}

.ambient.one{
    background:#8f3048;
    top:-25%;
    left:-20%;
}

.ambient.two{
    background:#b8834d;
    right:-30%;
    bottom:-25%;
    animation-delay:-7s;
}

@keyframes ambientMove{
    from{
        transform:translate3d(-5%,0,0) scale(1);
    }
    to{
        transform:translate3d(8%,7%,0) scale(1.2);
    }
}

/* =====================================================
   PREMIUM PARTICLES
===================================================== */

#particleLayer{
    position:fixed;
    inset:0;
    pointer-events:none;
    z-index:50;
    overflow:hidden;
}

.particle{
    position:absolute;
    bottom:-30px;
    opacity:0;
    will-change:transform,opacity;
    animation:rise linear forwards;
}

.starParticle{
    width:2px;
    height:2px;
    border-radius:50%;
    background:#fff;
    box-shadow:
        0 0 4px #fff,
        0 0 10px rgba(255,255,255,.75);
}

.starParticle.large{
    width:3px;
    height:3px;
}

.heartParticle{
    width:9px;
    height:9px;
    transform:rotate(45deg);
    background:rgba(224,142,160,.8);
    box-shadow:0 0 10px rgba(224,142,160,.45);
}

.heartParticle::before,
.heartParticle::after{
    content:"";
    position:absolute;
    width:9px;
    height:9px;
    border-radius:50%;
    background:inherit;
}

.heartParticle::before{
    top:-4.5px;
    left:0;
}

.heartParticle::after{
    left:-4.5px;
    top:0;
}

@keyframes rise{
    0%{
        opacity:0;
        transform:translate3d(0,40px,0) rotate(45deg) scale(.4);
    }

    10%{
        opacity:.7;
    }

    50%{
        opacity:.55;
    }

    100%{
        opacity:0;
        transform:
            translate3d(
                calc(var(--drift) * 1px),
                -115vh,
                0
            )
            rotate(405deg)
            scale(1);
    }
}

/* =====================================================
   NAVIGATION
===================================================== */

.topBar{
    position:fixed;
    top:0;
    left:0;
    right:0;
    height:70px;
    z-index:100;
    display:flex;
    justify-content:space-between;
    align-items:center;
    padding:0 5%;
    background:linear-gradient(
        to bottom,
        rgba(0,0,0,.65),
        transparent
    );
    pointer-events:none;
}

.logo{
    font-family:"Cormorant Garamond",serif;
    font-size:22px;
    letter-spacing:3px;
    color:#eee;
}

.musicMini{
    pointer-events:auto;
    width:42px;
    height:42px;
    border:1px solid rgba(255,255,255,.18);
    border-radius:50%;
    background:rgba(255,255,255,.04);
    backdrop-filter:blur(12px);
    color:white;
    cursor:pointer;
}

/* =====================================================
   GENERAL
===================================================== */

section{
    min-height:100vh;
    position:relative;
    display:flex;
    justify-content:center;
    align-items:center;
    padding:100px 20px;
}

.container{
    width:min(1100px,92%);
    margin:auto;
    text-align:center;
}

.eyebrow{
    color:var(--gold);
    text-transform:uppercase;
    letter-spacing:6px;
    font-size:10px;
    margin-bottom:24px;
}

h1,h2,h3{
    font-family:"Cormorant Garamond",serif;
    font-weight:400;
}

h1{
    font-size:clamp(55px,10vw,120px);
    line-height:.9;
    letter-spacing:-2px;
}

h2{
    font-size:clamp(42px,6vw,75px);
    line-height:1;
}

p{
    color:#bbb4b7;
    font-size:16px;
    line-height:1.9;
    font-weight:300;
}

.gold{
    color:var(--gold);
}

.luxuryButton{
    margin-top:35px;
    padding:15px 30px;
    border:1px solid rgba(216,178,124,.4);
    border-radius:100px;
    color:#eee;
    background:rgba(255,255,255,.035);
    backdrop-filter:blur(12px);
    cursor:pointer;
    font-family:Inter,sans-serif;
    font-size:13px;
    letter-spacing:1px;
    transition:
        background .4s ease,
        border-color .4s ease,
        transform .4s ease,
        box-shadow .4s ease;
}

.luxuryButton:hover{
    background:rgba(216,178,124,.1);
    border-color:rgba(216,178,124,.75);
    transform:translateY(-3px);
    box-shadow:0 15px 40px rgba(0,0,0,.3);
}

/* =====================================================
   HERO
===================================================== */

#hero{
    background:
        radial-gradient(
            ellipse at center,
            rgba(67,27,38,.45),
            transparent 55%
        );
}

.heroContent{
    animation:heroReveal 2.2s cubic-bezier(.16,1,.3,1) both;
}

@keyframes heroReveal{
    from{
        opacity:0;
        transform:translateY(50px);
        filter:blur(15px);
    }
    to{
        opacity:1;
        transform:none;
        filter:blur(0);
    }
}

.heroLine{
    width:1px;
    height:110px;
    background:linear-gradient(
        transparent,
        var(--gold),
        transparent
    );
    margin:0 auto 35px;
}

.heroSub{
    margin-top:30px;
    font-family:"Cormorant Garamond",serif;
    font-size:22px;
    color:#d5c8ca;
}

/* =====================================================
   MUSIC
===================================================== */

#music{
    min-height:70vh;
}

.musicCard{
    position:relative;
    max-width:720px;
    margin:auto;
    padding:65px 40px;
    border:1px solid rgba(255,255,255,.09);
    background:
        linear-gradient(
            135deg,
            rgba(255,255,255,.055),
            rgba(255,255,255,.015)
        );
    backdrop-filter:blur(25px);
    border-radius:4px;
    overflow:hidden;
}

.musicCard::before{
    content:"";
    position:absolute;
    width:350px;
    height:350px;
    border-radius:50%;
    background:rgba(178,73,97,.14);
    filter:blur(80px);
    top:-180px;
    left:-100px;
}

.musicDisc{
    width:160px;
    height:160px;
    border-radius:50%;
    margin:0 auto 35px;
    background:
        radial-gradient(circle at center,
            #151217 0 9%,
            #9a6874 10% 11%,
            #151217 12% 26%,
            #4c2832 27% 29%,
            #111015 30% 45%,
            #3b2029 46% 48%,
            #0d0c10 49%);
    box-shadow:
        0 30px 70px rgba(0,0,0,.6),
        inset 0 0 20px rgba(255,255,255,.04);
}

.musicDisc.playing{
    animation:discSpin 5s linear infinite;
}

@keyframes discSpin{
    to{
        transform:rotate(360deg);
    }
}

.songName{
    font-family:"Cormorant Garamond",serif;
    font-size:32px;
}

.songHint{
    font-size:13px;
    color:#858084;
    margin-top:8px;
}

/* =====================================================
   CAKE
===================================================== */

#cakeScene{
    background:
        radial-gradient(
            circle at 50% 70%,
            rgba(100,39,51,.28),
            transparent 42%
        );
}

.cakeStage{
    margin:70px auto 40px;
    width:360px;
    height:320px;
    position:relative;
}

.cakeShadow{
    position:absolute;
    width:330px;
    height:35px;
    bottom:15px;
    left:15px;
    background:rgba(0,0,0,.7);
    filter:blur(18px);
    border-radius:50%;
}

.cakeBase{
    position:absolute;
    bottom:45px;
    left:30px;
    width:300px;
    height:120px;
    border-radius:0 0 25px 25px;
    background:
        linear-gradient(
            90deg,
            #52202d,
            #9e475e 48%,
            #5b2331
        );
    box-shadow:
        inset 0 -12px 20px rgba(0,0,0,.3),
        0 20px 50px rgba(0,0,0,.45);
}

.cakeTop{
    position:absolute;
    top:110px;
    left:30px;
    width:300px;
    height:75px;
    border-radius:50%;
    background:
        radial-gradient(
            ellipse at 50% 40%,
            #f4d3d8,
            #bd7587 75%
        );
    box-shadow:
        inset 0 -8px 15px rgba(100,30,50,.25);
}

.creamDrop{
    position:absolute;
    width:24px;
    height:35px;
    background:#edc8ce;
    border-radius:0 0 15px 15px;
    top:155px;
}

.creamDrop:nth-child(1){left:65px}
.creamDrop:nth-child(2){left:125px}
.creamDrop:nth-child(3){left:190px}
.creamDrop:nth-child(4){left:250px}

.candle{
    position:absolute;
    bottom:195px;
    width:13px;
    height:70px;
    background:
        repeating-linear-gradient(
            135deg,
            #f7e8df 0 5px,
            #d9aeb7 5px 10px
        );
    border-radius:4px;
    z-index:4;
}

.candle:nth-of-type(1){left:82px}
.candle:nth-of-type(2){left:145px}
.candle:nth-of-type(3){left:208px}

.flame{
    position:absolute;
    width:19px;
    height:29px;
    left:-3px;
    top:-31px;
    border-radius:
        50% 50% 48% 48% /
        65% 65% 35% 35%;
    background:
        radial-gradient(
            ellipse at 50% 70%,
            #fff7b0 0 18%,
            #ffc04b 35%,
            #ff7b22 63%,
            #c82b1b 100%
        );
    filter:blur(.2px);
    box-shadow:
        0 0 8px #ffca64,
        0 0 22px rgba(255,150,50,.9),
        0 0 45px rgba(255,90,30,.35);
    transform-origin:50% 90%;
    animation:
        flameMove .13s infinite alternate,
        flameGlow 1.4s infinite ease-in-out;
}

.flame::after{
    content:"";
    position:absolute;
    width:7px;
    height:14px;
    background:#fff8c7;
    border-radius:50%;
    left:6px;
    top:9px;
    filter:blur(1px);
}

@keyframes flameMove{
    from{
        transform:rotate(-5deg) scale(.94,.98);
    }
    to{
        transform:rotate(5deg) scale(1.04,1.08);
    }
}

@keyframes flameGlow{
    0%,100%{
        box-shadow:
            0 0 8px #ffca64,
            0 0 20px rgba(255,150,50,.75),
            0 0 38px rgba(255,90,30,.25);
    }
    50%{
        box-shadow:
            0 0 12px #fff0a0,
            0 0 28px rgba(255,180,60,.9),
            0 0 55px rgba(255,90,30,.4);
    }
}

.candle.off .flame{
    opacity:0;
    transform:scale(.2);
    transition:.25s;
}

.smoke{
    position:absolute;
    width:9px;
    height:30px;
    left:2px;
    top:-34px;
    opacity:0;
    filter:blur(4px);
    background:linear-gradient(
        transparent,
        rgba(220,220,220,.25),
        transparent
    );
}

.candle.off .smoke{
    opacity:1;
    animation:smoke 2.7s ease-out forwards;
}

@keyframes smoke{
    0%{
        transform:translateY(0) scale(.6);
        opacity:.2;
    }
    50%{
        transform:translate(-8px,-30px) scale(1.5);
        opacity:.16;
    }
    100%{
        transform:translate(12px,-75px) scale(2.3);
        opacity:0;
    }
}

.cakeAppear{
    opacity:0;
    transform:translateY(80px) scale(.85);
}

.cakeAppear.visible{
    animation:cakeEntrance 1.8s cubic-bezier(.16,1,.3,1) forwards;
}

@keyframes cakeEntrance{
    to{
        opacity:1;
        transform:none;
    }
}

/* =====================================================
   CINEMATIC FLASH
===================================================== */

#lightBurst{
    position:fixed;
    inset:0;
    pointer-events:none;
    z-index:200;
    opacity:0;
    background:
        radial-gradient(
            circle at center,
            rgba(255,210,145,.75),
            rgba(255,140,100,.18) 22%,
            transparent 65%
        );
}

#lightBurst.active{
    animation:cinematicBurst 4.5s ease-out forwards;
}

@keyframes cinematicBurst{
    0%{
        opacity:0;
    }
    12%{
        opacity:.9;
    }
    35%{
        opacity:.55;
    }
    100%{
        opacity:0;
    }
}

/* =====================================================
   SECRET ROOM
===================================================== */

#secretRoom{
    overflow:hidden;
}

.roomWrapper{
    position:relative;
    width:min(1000px,95vw);
    height:620px;
    perspective:1800px;
}

.hiddenRoom{
    position:absolute;
    inset:0;
    background:
        radial-gradient(
            ellipse at center,
            #4b222d,
            #12090d 55%,
            #030304
        );
    display:flex;
    justify-content:center;
    align-items:center;
    flex-direction:column;
    overflow:hidden;
}

.roomLight{
    position:absolute;
    width:600px;
    height:600px;
    border-radius:50%;
    background:radial-gradient(
        circle,
        rgba(239,180,112,.35),
        transparent 65%
    );
    filter:blur(20px);
}

.roomDoor{
    position:absolute;
    inset:0;
    z-index:5;
    transform-origin:left center;
    background:
        linear-gradient(
            90deg,
            #171015,
            #36242a 48%,
            #140e12
        );
    border:1px solid rgba(216,178,124,.18);
    box-shadow:
        20px 0 80px rgba(0,0,0,.6),
        inset 0 0 80px rgba(0,0,0,.5);
    transition:
        transform 2.2s cubic-bezier(.16,1,.3,1);
}

.roomDoor.open{
    transform:
        perspective(1800px)
        rotateY(-78deg);
}

.doorHandle{
    position:absolute;
    right:12%;
    top:50%;
    width:15px;
    height:15px;
    border-radius:50%;
    background:var(--gold);
    box-shadow:
        0 0 8px var(--gold),
        0 0 30px rgba(216,178,124,.4);
}

.doorTitle{
    position:absolute;
    top:45%;
    left:0;
    right:0;
    text-align:center;
    color:#ddd;
    font-family:"Cormorant Garamond",serif;
    font-size:38px;
}

/* =====================================================
   GIFTS
===================================================== */

#gifts{
    background:
        radial-gradient(
            circle at center,
            rgba(67,26,37,.2),
            transparent 60%
        );
}

.giftGrid{
    margin-top:55px;
    display:grid;
    grid-template-columns:repeat(4,1fr);
    gap:18px;
}

.giftCard{
    position:relative;
    height:210px;
    border:1px solid rgba(255,255,255,.09);
    background:
        linear-gradient(
            145deg,
            rgba(255,255,255,.05),
            rgba(255,255,255,.015)
        );
    overflow:hidden;
    cursor:pointer;
    transition:
        transform .6s cubic-bezier(.16,1,.3,1),
        border-color .5s;
}

.giftCard:hover{
    transform:translateY(-7px);
    border-color:rgba(216,178,124,.35);
}

.giftFront{
    position:absolute;
    inset:0;
    display:flex;
    align-items:center;
    justify-content:center;
    flex-direction:column;
    transition:1s cubic-bezier(.16,1,.3,1);
}

.giftNumber{
    font-family:"Cormorant Garamond",serif;
    font-size:55px;
    color:#d6b4a7;
}

.giftLabel{
    margin-top:8px;
    font-size:10px;
    letter-spacing:3px;
    color:#777;
    text-transform:uppercase;
}

.giftReveal{
    position:absolute;
    inset:0;
    padding:30px;
    display:flex;
    align-items:center;
    justify-content:center;
    background:
        radial-gradient(
            circle,
            rgba(113,45,61,.6),
            rgba(16,8,11,.95)
        );
    opacity:0;
    transform:scale(1.12);
    transition:
        opacity .7s,
        transform .9s;
}

.giftCard.open .giftFront{
    opacity:0;
    transform:scale(.85);
}

.giftCard.open .giftReveal{
    opacity:1;
    transform:none;
}

.giftReveal p{
    color:#e5dadd;
    font-family:"Cormorant Garamond",serif;
    font-size:22px;
    line-height:1.4;
}

/* =====================================================
   LETTER
===================================================== */

#letter{
    background:#070607;
}

.letterPaper{
    position:relative;
    max-width:780px;
    margin:50px auto 0;
    padding:65px 70px;
    text-align:left;
    color:#382b29;
    background:
        linear-gradient(
            110deg,
            #e9dcc5,
            #f6ecd9,
            #dfcfb5
        );
    box-shadow:
        0 35px 100px rgba(0,0,0,.65);
    transform:rotate(-.5deg);
}

.letterPaper::before{
    content:"";
    position:absolute;
    inset:15px;
    border:1px solid rgba(80,50,35,.18);
    pointer-events:none;
}

.letterPaper p{
    color:#463734;
    font-family:"Cormorant Garamond",serif;
    font-size:21px;
    line-height:1.65;
}

.letterSign{
    margin-top:30px;
    font-family:"Cormorant Garamond",serif;
    font-size:25px;
    color:#6c3d45;
}

/* =====================================================
   WISH
===================================================== */

#wish{
    overflow:hidden;
    background:
        radial-gradient(
            circle at center,
            rgba(84,36,47,.35),
            transparent 55%
        );
}

.wishCandle{
    position:relative;
    width:30px;
    height:140px;
    margin:60px auto 50px;
    border-radius:5px;
    background:
        linear-gradient(
            90deg,
            #c6a8a5,
            #f1e2d8,
            #b99695
        );
}

.wishCandle .flame{
    width:24px;
    height:37px;
    left:3px;
    top:-40px;
}

.wishCandle.extinguished .flame{
    opacity:0;
    transition:.3s;
}

.wishGlow{
    position:absolute;
    width:700px;
    height:700px;
    border-radius:50%;
    background:
        radial-gradient(
            circle,
            rgba(255,185,110,.22),
            transparent 65%
        );
    filter:blur(25px);
    opacity:0;
    transition:3s;
    pointer-events:none;
}

#wish.wished .wishGlow{
    opacity:1;
}

.wishMessage{
    opacity:0;
    transform:translateY(20px);
    transition:2s;
    margin-top:25px;
}

#wish.wished .wishMessage{
    opacity:1;
    transform:none;
}

/* =====================================================
   FLOWER GARDEN
===================================================== */

#garden{
    overflow:hidden;
}

.garden{
    height:430px;
    max-width:900px;
    margin:60px auto 0;
    position:relative;
    border-bottom:2px solid #253125;
}

.stem{
    position:absolute;
    bottom:0;
    width:4px;
    background:
        linear-gradient(
            to top,
            #263e2c,
            #4c704d
        );
    transform-origin:bottom;
    animation:stemSway 5s ease-in-out infinite;
}

@keyframes stemSway{
    0%,100%{
        transform:rotate(-2deg);
    }
    50%{
        transform:rotate(3deg);
    }
}

.flowerHead{
    position:absolute;
    top:-22px;
    left:50%;
    width:55px;
    height:55px;
    transform:translateX(-50%);
}

.petal{
    position:absolute;
    width:27px;
    height:37px;
    border-radius:70% 70% 45% 45%;
    background:
        radial-gradient(
            ellipse at 50% 70%,
            #f0b4c0,
            #8c4255
        );
    transform-origin:bottom center;
    box-shadow:0 0 15px rgba(219,132,152,.2);
}

.petal:nth-child(1){left:14px;top:0;transform:rotate(0deg)}
.petal:nth-child(2){left:27px;top:11px;transform:rotate(72deg)}
.petal:nth-child(3){left:20px;top:25px;transform:rotate(144deg)}
.petal:nth-child(4){left:2px;top:25px;transform:rotate(216deg)}
.petal:nth-child(5){left:-5px;top:11px;transform:rotate(288deg)}

.flowerCenter{
    position:absolute;
    width:15px;
    height:15px;
    border-radius:50%;
    background:#d9ad62;
    left:20px;
    top:20px;
    box-shadow:0 0 12px rgba(216,178,124,.5);
}

/* =====================================================
   REASONS
===================================================== */

#reasons{
    min-height:90vh;
}

.counter{
    font-family:"Cormorant Garamond",serif;
    font-size:150px;
    line-height:1;
    color:#dfbd98;
    margin:40px 0 10px;
    text-shadow:0 0 40px rgba(216,178,124,.12);
}

.reasonList{
    max-width:700px;
    margin:40px auto 0;
}

.reason{
    padding:20px;
    border-bottom:1px solid rgba(255,255,255,.07);
    color:#bdb6b8;
    font-family:"Cormorant Garamond",serif;
    font-size:21px;
    opacity:0;
    transform:translateY(15px);
    animation:reasonIn .8s forwards;
}

@keyframes reasonIn{
    to{
        opacity:1;
        transform:none;
    }
}

/* =====================================================
   FINAL
===================================================== */

#final{
    min-height:100vh;
    background:
        radial-gradient(
            ellipse at center,
            rgba(91,36,51,.4),
            transparent 60%
        );
}

.finalHeart{
    position:relative;
    width:90px;
    height:90px;
    margin:50px auto;
}

.finalHeart::before{
    content:"";
    position:absolute;
    inset:0;
    border-radius:50%;
    border:1px solid rgba(216,178,124,.35);
    animation:heartPulse 2.5s ease-in-out infinite;
}

@keyframes heartPulse{
    0%,100%{
        transform:scale(.9);
        opacity:.35;
    }
    50%{
        transform:scale(1.2);
        opacity:.8;
    }
}

.finalText{
    max-width:760px;
    margin:30px auto;
}

.signature{
    margin-top:45px;
    font-family:"Cormorant Garamond",serif;
    font-size:27px;
    color:#d9a0ad;
}

/* =====================================================
   SCROLL REVEALS
===================================================== */

.reveal{
    opacity:0;
    transform:translateY(45px);
    filter:blur(8px);
    transition:
        opacity 1.2s ease,
        transform 1.2s cubic-bezier(.16,1,.3,1),
        filter 1.2s ease;
}

.reveal.visible{
    opacity:1;
    transform:none;
    filter:blur(0);
}

/* =====================================================
   RESPONSIVE
===================================================== */

@media(max-width:800px){

    .giftGrid{
        grid-template-columns:repeat(2,1fr);
    }

    .roomWrapper{
        height:500px;
    }

    .cakeStage{
        transform:scale(.82);
        margin-left:auto;
        margin-right:auto;
    }

    .letterPaper{
        padding:45px 30px;
    }
}

@media(max-width:520px){

    section{
        padding:80px 15px;
    }

    h1{
        font-size:60px;
    }

    .giftGrid{
        grid-template-columns:1fr;
    }

    .musicCard{
        padding:45px 25px;
    }

    .letterPaper p{
        font-size:18px;
    }

    .counter{
        font-size:100px;
    }

    .cakeStage{
        transform:scale(.72);
        transform-origin:center;
        width:360px;
    }
}
</style>
</head>

<body>

<!-- =====================================================
     BACKGROUND
===================================================== -->

<div id="background">
    <div class="ambient one"></div>
    <div class="ambient two"></div>
</div>

<div id="particleLayer"></div>
<div id="lightBurst"></div>

<!-- =====================================================
     TOP BAR
===================================================== -->

<header class="topBar">
    <div class="logo">K.</div>

    <button class="musicMini" id="miniMusic">
        ♪
    </button>
</header>


<!-- =====================================================
     HERO
===================================================== -->

<section id="hero">

<div class="container heroContent">

    <div class="heroLine"></div>

    <div class="eyebrow">
        A little world made for you
    </div>

    <h1>
        Happy Birthday
        <br>
        <span class="gold">Kyuutu</span>
    </h1>

    <p class="heroSub">
        Tonight, everything is about you.
    </p>

</div>

</section>


<!-- =====================================================
     MUSIC
===================================================== -->

<section id="music">

<div class="container reveal">

    <div class="eyebrow">
        Press play
    </div>

    <h2>
        A song for you
    </h2>

    <p>
        Let this song play while the story unfolds.
    </p>

    <div class="musicCard">

        <div class="musicDisc" id="musicDisc"></div>

        <div class="songName">
            Your Birthday Song
        </div>

        <div class="songHint">
            Replace the audio file with your special song
        </div>

        <audio id="song" loop>
            <source src="birthday-song.mp3" type="audio/mpeg">
        </audio>

        <button class="luxuryButton" id="playButton">
            PLAY SONG
        </button>

    </div>

</div>

</section>


<!-- =====================================================
     INTRO
===================================================== -->

<section>

<div class="container reveal">

    <div class="eyebrow">
        September of memories
    </div>

    <h2>
        Some birthdays are
        <br>
        meant to be remembered.
    </h2>

    <p style="max-width:650px;margin:35px auto 0;">
        So instead of sending you an ordinary birthday message,
        I wanted to create something you could actually experience.
    </p>

</div>

</section>


<!-- =====================================================
     CAKE
===================================================== -->

<section id="cakeScene">

<div class="container">

    <div class="reveal">

        <div class="eyebrow">
            Make a wish
        </div>

        <h2>
            Your cake is waiting.
        </h2>

        <p>
            Three candles. One wish.
        </p>

    </div>


    <div class="cakeAppear" id="cakeAnimation">

        <div class="cakeStage">

            <div class="cakeShadow"></div>

            <div class="cakeBase"></div>

            <div class="cakeTop"></div>

            <div class="creamDrop" style="left:65px"></div>
            <div class="creamDrop" style="left:125px"></div>
            <div class="creamDrop" style="left:190px"></div>
            <div class="creamDrop" style="left:250px"></div>

            <div class="candle" data-candle="0">
                <div class="flame"></div>
                <div class="smoke"></div>
            </div>

            <div class="candle" data-candle="1">
                <div class="flame"></div>
                <div class="smoke"></div>
            </div>

            <div class="candle" data-candle="2">
                <div class="flame"></div>
                <div class="smoke"></div>
            </div>

        </div>

        <button class="luxuryButton" id="blowButton">
            BLOW OUT THE CANDLES
        </button>

    </div>

</div>

</section>


<!-- =====================================================
     SECRET ROOM
===================================================== -->

<section id="secretRoom">

<div class="container reveal">

    <div class="eyebrow">
        Something hidden
    </div>

    <h2>
        There's another room.
    </h2>

    <p>
        But you have to open the door yourself.
    </p>

    <div class="roomWrapper">

        <div class="hiddenRoom">

            <div class="roomLight"></div>

            <div class="eyebrow">
                You found it
            </div>

            <h2>
                Welcome, Kyuutu.
            </h2>

            <p>
                Seven surprises are waiting for you.
            </p>

        </div>

        <div class="roomDoor" id="roomDoor">

            <div class="doorTitle">
                OPEN
            </div>

            <div class="doorHandle"></div>

        </div>

    </div>

</div>

</section>


<!-- =====================================================
     SEVEN GIFTS
===================================================== -->

<section id="gifts">

<div class="container reveal">

    <div class="eyebrow">
        Seven little things
    </div>

    <h2>
        Open them slowly.
    </h2>

    <p>
        Each one contains something personal.
    </p>

    <div class="giftGrid">

        <div class="giftCard">
            <div class="giftFront">
                <div class="giftNumber">I</div>
                <div class="giftLabel">Open</div>
            </div>
            <div class="giftReveal">
                <p>
                    A memory I never want to forget.
                </p>
            </div>
        </div>

        <div class="giftCard">
            <div class="giftFront">
                <div class="giftNumber">II</div>
                <div class="giftLabel">Open</div>
            </div>
            <div class="giftReveal">
                <p>
                    One of the reasons your smile means so much.
                </p>
            </div>
        </div>

        <div class="giftCard">
            <div class="giftFront">
                <div class="giftNumber">III</div>
                <div class="giftLabel">Open</div>
            </div>
            <div class="giftReveal">
                <p>
                    A promise to keep cheering for you.
                </p>
            </div>
        </div>

        <div class="giftCard">
            <div class="giftFront">
                <div class="giftNumber">IV</div>
                <div class="giftLabel">Open</div>
            </div>
            <div class="giftReveal">
                <p>
                    A moment that deserves to stay forever.
                </p>
            </div>
        </div>

        <div class="giftCard">
            <div class="giftFront">
                <div class="giftNumber">V</div>
                <div class="giftLabel">Open</div>
            </div>
            <div class="giftReveal">
                <p>
                    A reminder that you are deeply appreciated.
                </p>
            </div>
        </div>

        <div class="giftCard">
            <div class="giftFront">
                <div class="giftNumber">VI</div>
                <div class="giftLabel">Open</div>
            </div>
            <div class="giftReveal">
                <p>
                    Something small, but filled with meaning.
                </p>
            </div>
        </div>

        <div class="giftCard">
            <div class="giftFront">
                <div class="giftNumber">VII</div>
                <div class="giftLabel">Open</div>
            </div>
            <div class="giftReveal">
                <p>
                    The biggest gift is simply getting to know you.
                </p>
            </div>
        </div>

    </div>

</div>

</section>


<!-- =====================================================
     LETTER
===================================================== -->

<section id="letter">

<div class="container reveal">

    <div class="eyebrow">
        From me to you
    </div>

    <h2>
        A letter.
    </h2>

    <div class="letterPaper">

        <p>
            Dear Kyuutu,
        </p>

        <br>

        <p>
            Today is your day, and I wanted to give you something
            more meaningful than a simple “Happy Birthday.”
        </p>

        <br>

        <p>
            I hope this new year of your life brings you the kind
            of happiness that stays. I hope you get closer to your
            dreams, meet beautiful moments, and have countless
            reasons to smile.
        </p>

        <br>

        <p>
            There will always be difficult days, but I hope you
            never forget how special you are to the people who
            genuinely care about you.
        </p>

        <br>

        <p>
            And today, more than anything, I hope you feel loved,
            appreciated and remembered.
        </p>

        <div class="letterSign">
            Happy Birthday, Kyuutu.
        </div>

    </div>

</div>

</section>


<!-- =====================================================
     WISH
===================================================== -->

<section id="wish">

<div class="wishGlow"></div>

<div class="container reveal">

    <div class="eyebrow">
        One last thing
    </div>

    <h2>
        Make your wish.
    </h2>

    <p>
        Don't tell anyone what it is.
    </p>

    <div class="wishCandle" id="wishCandle">

        <div class="flame"></div>

    </div>

    <button class="luxuryButton" id="wishButton">
        MAKE MY WISH
    </button>

    <div class="wishMessage">
        May the wish you keep quietly in your heart
        find its way to you.
    </div>

</div>

</section>


<!-- =====================================================
     FLOWER GARDEN
===================================================== -->

<section id="gardenSection">

<div class="container reveal">

    <div class="eyebrow">
        For you
    </div>

    <h2>
        A garden that never fades.
    </h2>

    <p>
        Because some people deserve flowers that last forever.
    </p>

    <div class="garden">

        <div class="stem" style="left:10%;height:190px;animation-delay:-1s">
            <div class="flowerHead">
                <span class="petal"></span>
                <span class="petal"></span>
                <span class="petal"></span>
                <span class="petal"></span>
                <span class="petal"></span>
                <span class="flowerCenter"></span>
            </div>
        </div>

        <div class="stem" style="left:25%;height:260px;animation-delay:-3s">
            <div class="flowerHead">
                <span class="petal"></span>
                <span class="petal"></span>
                <span class="petal"></span>
                <span class="petal"></span>
                <span class="petal"></span>
                <span class="flowerCenter"></span>
            </div>
        </div>

        <div class="stem" style="left:40%;height:210px;animation-delay:-2s">
            <div class="flowerHead">
                <span class="petal"></span>
                <span class="petal"></span>
                <span class="petal"></span>
                <span class="petal"></span>
                <span class="petal"></span>
                <span class="flowerCenter"></span>
            </div>
        </div>

        <div class="stem" style="left:56%;height:280px;animation-delay:-4s">
            <div class="flowerHead">
                <span class="petal"></span>
                <span class="petal"></span>
                <span class="petal"></span>
                <span class="petal"></span>
                <span class="petal"></span>
                <span class="flowerCenter"></span>
            </div>
        </div>

        <div class="stem" style="left:72%;height:225px;animation-delay:-1.5s">
            <div class="flowerHead">
                <span class="petal"></span>
                <span class="petal"></span>
                <span class="petal"></span>
                <span class="petal"></span>
                <span class="petal"></span>
                <span class="flowerCenter"></span>
            </div>
        </div>

        <div class="stem" style="left:88%;height:250px;animation-delay:-3.5s">
            <div class="flowerHead">
                <span class="petal"></span>
                <span class="petal"></span>
                <span class="petal"></span>
                <span class="petal"></span>
                <span class="petal"></span>
                <span class="flowerCenter"></span>
            </div>
        </div>

    </div>

</div>

</section>


<!-- =====================================================
     REASONS
===================================================== -->

<section id="reasons">

<div class="container reveal">

    <div class="eyebrow">
        I could keep going
    </div>

    <h2>
        Reasons to smile.
    </h2>

    <p>
        Let's count a few.
    </p>

    <div class="counter" id="counter">
        0
    </div>

    <button class="luxuryButton" id="countButton">
        START COUNTING
    </button>

    <div class="reasonList" id="reasonList"></div>

</div>

</section>


<!-- =====================================================
     FINAL
===================================================== -->

<section id="final">

<div class="container reveal">

    <div class="eyebrow">
        The end of the story
    </div>

    <h1>
        Happy Birthday,
        <br>
        <span class="gold">Kyuutu.</span>
    </h1>

    <div class="finalHeart"></div>

    <div class="finalText">

        <p>
            I hope this little world made you smile.
        </p>

        <p style="margin-top:22px;">
            And whenever you come back here,
            I hope it reminds you of one simple thing:
            you are worth celebrating.
        </p>

    </div>

    <div class="signature">
        With love,<br>
        Biraja
    </div>

</div>

</section>


<script>

/* =====================================================
   MUSIC
===================================================== */

const song = document.getElementById("song");
const playButton = document.getElementById("playButton");
const miniMusic = document.getElementById("miniMusic");
const disc = document.getElementById("musicDisc");

function toggleMusic(){

    if(song.paused){

        song.play();

        playButton.textContent="PAUSE SONG";
        miniMusic.textContent="Ⅱ";
        disc.classList.add("playing");

    }else{

        song.pause();

        playButton.textContent="PLAY SONG";
        miniMusic.textContent="♪";
        disc.classList.remove("playing");

    }

}

playButton.addEventListener("click",toggleMusic);
miniMusic.addEventListener("click",toggleMusic);


/* =====================================================
   SCROLL REVEALS
===================================================== */

const reveals=document.querySelectorAll(".reveal");

const revealObserver=new IntersectionObserver(

(entries)=>{

    entries.forEach(entry=>{

        if(entry.isIntersecting){

            entry.target.classList.add("visible");

        }

    });

},

{
    threshold:.14
}

);

reveals.forEach(el=>revealObserver.observe(el));


/* =====================================================
   CAKE ENTRANCE
===================================================== */

const cakeAnimation=document.getElementById("cakeAnimation");

const cakeObserver=new IntersectionObserver(

(entries)=>{

    entries.forEach(entry=>{

        if(entry.isIntersecting){

            cakeAnimation.classList.add("visible");

        }

    });

},

{
    threshold:.2
}

);

cakeObserver.observe(cakeAnimation);


/* =====================================================
   CAKE CANDLES
===================================================== */

const candles=document.querySelectorAll(".cakeStage .candle");
const blowButton=document.getElementById("blowButton");
const lightBurst=document.getElementById("lightBurst");

let blown=0;

function blowCandles(){

    candles.forEach((candle,index)=>{

        setTimeout(()=>{

            if(!candle.classList.contains("off")){

                candle.classList.add("off");
                blown++;

            }

        },index*220);

    });

    setTimeout(()=>{

        lightBurst.classList.remove("active");

        void lightBurst.offsetWidth;

        lightBurst.classList.add("active");

        createBurstParticles();

    },900);

}

blowButton.addEventListener("click",blowCandles);


/* =====================================================
   LIGHT BURST PARTICLES
===================================================== */

function createBurstParticles(){

    for(let i=0;i<45;i++){

        const p=document.createElement("div");

        p.style.position="fixed";
        p.style.left="50%";
        p.style.top="48%";
        p.style.width="2px";
        p.style.height="2px";
        p.style.borderRadius="50%";
        p.style.background="#f6d59c";
        p.style.boxShadow="0 0 8px #f6d59c";
        p.style.pointerEvents="none";
        p.style.zIndex="210";

        const angle=Math.random()*Math.PI*2;
        const distance=120+Math.random()*500;

        p.animate(

            [
                {
                    transform:"translate(-50%,-50%) scale(1)",
                    opacity:1
                },
                {
                    transform:
                        `translate(
                            calc(-50% + ${Math.cos(angle)*distance}px),
                            calc(-50% + ${Math.sin(angle)*distance}px)
                        ) scale(0)`,
                    opacity:0
                }
            ],

            {
                duration:1200+Math.random()*1200,
                easing:"cubic-bezier(.16,1,.3,1)"
            }

        );

        document.body.appendChild(p);

        setTimeout(()=>p.remove(),2600);

    }

}


/* =====================================================
   SECRET DOOR
===================================================== */

const door=document.getElementById("roomDoor");

door.addEventListener("click",()=>{

    door.classList.toggle("open");

});


/* =====================================================
   GIFTS
===================================================== */

document.querySelectorAll(".giftCard").forEach(card=>{

    card.addEventListener("click",()=>{

        card.classList.toggle("open");

    });

});


/* =====================================================
   WISH
===================================================== */

const wish=document.getElementById("wish");
const wishCandle=document.getElementById("wishCandle");
const wishButton=document.getElementById("wishButton");

wishButton.addEventListener("click",()=>{

    wishCandle.classList.add("extinguished");

    wish.classList.add("wished");

    lightBurst.classList.remove("active");

    void lightBurst.offsetWidth;

    lightBurst.classList.add("active");

    createBurstParticles();

    wishButton.textContent="WISH MADE";

    wishButton.disabled=true;

});


/* =====================================================
   REASON COUNTER
===================================================== */

const counter=document.getElementById("counter");
const countButton=document.getElementById("countButton");
const reasonList=document.getElementById("reasonList");

let counting=false;

const reasons=[

    "Because your smile can change an ordinary day.",

    "Because you make memories feel more meaningful.",

    "Because you deserve beautiful things.",

    "Because there is nobody quite like you.",

    "Because your happiness genuinely matters.",

    "Because you make people around you smile.",

    "Because being yourself is already enough."

];

countButton.addEventListener("click",()=>{

    if(counting)return;

    counting=true;

    let number=0;

    const interval=setInterval(()=>{

        number++;

        counter.textContent=number;

        if(number>=100){

            clearInterval(interval);

            countButton.textContent="100+ REASONS";

            showReasons();

        }

    },28);

});


function showReasons(){

    reasons.forEach((reason,index)=>{

        setTimeout(()=>{

            const div=document.createElement("div");

            div.className="reason";

            div.textContent=reason;

            reasonList.appendChild(div);

        },index*450);

    });

}


/* =====================================================
   PREMIUM FLOATING PARTICLES
===================================================== */

const particleLayer=document.getElementById("particleLayer");

function createParticle(){

    const particle=document.createElement("div");

    const heart=Math.random()<.20;

    particle.className=
        "particle "+
        (heart?"heartParticle":"starParticle");

    if(!heart && Math.random()<.25){

        particle.classList.add("large");

    }

    particle.style.left=
        Math.random()*100+"vw";

    particle.style.setProperty(
        "--drift",
        (-100+Math.random()*200).toFixed(0)
    );

    const duration=
        9+Math.random()*14;

    particle.style.animationDuration=
        duration+"s";

    particleLayer.appendChild(particle);

    setTimeout(()=>{

        particle.remove();

    },(duration+2)*1000);

}


/* Start atmosphere */

for(let i=0;i<45;i++){

    setTimeout(
        createParticle,
        i*120
    );

}

setInterval(
    createParticle,
    420
);


/* =====================================================
   SUBTLE PARALLAX
===================================================== */

let ticking=false;

window.addEventListener("scroll",()=>{

    if(!ticking){

        window.requestAnimationFrame(()=>{

            const scrollY=window.scrollY;

            document.querySelectorAll(".ambient").forEach(
                (el,index)=>{

                    const speed=
                        index===0?.035:.02;

                    el.style.transform=
                        `translate3d(0,${scrollY*speed}px,0)`;

                }
            );

            ticking=false;

        });

        ticking=true;

    }

});


/* =====================================================
   PREVENT AUDIO AUTOPLAY ISSUES
===================================================== */

document.addEventListener(
    "visibilitychange",
    ()=>{

        if(document.hidden && !song.paused){

            song.pause();

            playButton.textContent="PLAY SONG";
            miniMusic.textContent="♪";
            disc.classList.remove("playing");

        }

    }
);

</script>

</body>
</html>
