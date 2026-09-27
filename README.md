<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>千年科举路 · 古代人才选拔</title>
<style>
/* ============ 基础 ============ */
*{margin:0;padding:0;box-sizing:border-box}
:root{
  --ink:#2b2118; --gold:#c9a24a; --gold-l:#e8cd87; --paper:#f3e6ce;
  --gold-d:#8a6a20; --jade:#4a6b52; --vermilion:#8c2b21; --lacquer:#7a1f18;
}
html,body{height:100%;overflow:hidden}
body{
  font-family:"KaiTi","STKaiti","SimSun","Songti SC",serif;
  background:#080503; color:var(--paper);
  user-select:none; -webkit-user-select:none;
}
#app{position:fixed;inset:0;perspective:1800px}

/* ============ 内景：贡院明伦堂 ============ */
.hall{
  position:absolute;inset:0;overflow:hidden;
  background:
    radial-gradient(ellipse at 50% 30%, rgba(74,50,28,.55) 0%, rgba(40,24,12,0) 55%),
    linear-gradient(180deg,#2a180e 0%,#1a0e07 50%,#0c0603 100%);
  transform-origin:center center;
  will-change:transform,opacity,filter;
}
/* 屋顶梁架 */
.roof{position:absolute;left:0;right:0;top:0;height:16%;pointer-events:none;
  background:
    repeating-linear-gradient(90deg,transparent 0,transparent 9.6%,rgba(0,0,0,.55) 9.6%,rgba(0,0,0,.55) 10.4%),
    linear-gradient(180deg,#3a2414,#5a381e 60%,#3a2414);
  box-shadow:0 10px 30px rgba(0,0,0,.7);opacity:.95}
.roof::after{content:"";position:absolute;left:0;right:0;bottom:-6px;height:6px;
  background:repeating-linear-gradient(90deg,#7a2020 0,#7a2020 30%,#5a1515 30%,#5a1515 100%)}
/* 屋檐瓦当 */
.eaves{position:absolute;left:0;right:0;top:16%;height:2.4%;pointer-events:none;
  background:repeating-linear-gradient(90deg,#2a1a10 0,#2a1a10 4.4%,#4a2c18 4.4%,#4a2c18 5%);
  box-shadow:0 4px 14px rgba(0,0,0,.6)}
/* 远山 */
.mountains{position:absolute;left:0;right:0;top:22%;height:32%;opacity:.45}
.mountains svg{width:100%;height:100%;display:block}
/* 天光 */
.skylight{position:absolute;left:50%;top:6%;transform:translateX(-50%);
  width:66%;height:78%;
  background:radial-gradient(ellipse at center,rgba(255,238,196,.6) 0%,rgba(255,214,140,.22) 32%,rgba(255,214,140,0) 70%);
  filter:blur(4px);pointer-events:none}
/* 木柱 */
.pillars{position:absolute;inset:0;pointer-events:none}
.pillar{position:absolute;top:0;width:4.4%;height:100%;
  background:linear-gradient(90deg,#241408,#4e3320 40%,#382414 72%,#180d06);
  box-shadow:inset 0 0 22px rgba(0,0,0,.7),6px 0 22px rgba(0,0,0,.55);
  border-top:4px solid #6a3e20}
.pillar::after{content:"";position:absolute;left:0;right:0;bottom:0;height:7%;
  background:linear-gradient(180deg,#5a3a22,#241408)}
.pillar .brace{position:absolute;left:120%;top:34%;width:200%;height:14%;
  background:linear-gradient(180deg,transparent,#5a341c 40%,#3a2010 60%,transparent);
  clip-path:polygon(0 0,100% 100%,0 100%)}
/* 匾额 */
.plaque{position:absolute;left:50%;top:6.5%;transform:translateX(-50%);
  width:min(33vw,410px);padding:1vw 2vw 1.2vw;text-align:center;
  background:linear-gradient(180deg,#7a2020,#4a100c);border:3px solid var(--gold);
  border-radius:4px;box-shadow:0 10px 34px rgba(0,0,0,.75),inset 0 0 20px rgba(0,0,0,.55);
  z-index:5}
.plaque .cn{font-size:clamp(19px,2.8vw,36px);letter-spacing:.5em;text-indent:.5em;
  color:var(--gold-l);text-shadow:0 2px 8px #000}
.plaque .en{margin-top:.45em;font-size:clamp(9px,1vw,13px);letter-spacing:.28em;
  color:rgba(232,205,135,.7);font-family:"SimSun",serif}
.plaque::before{content:"";position:absolute;left:8px;right:8px;top:8px;bottom:8px;
  border:1px solid rgba(201,162,74,.4)}
/* 对联 */
.couplet{position:absolute;top:13%;width:min(5.4vw,56px);text-align:center;z-index:5}
.couplet.left{left:7.5%}.couplet.right{right:7.5%}
.couplet span{display:block;writing-mode:vertical-rl;margin:0 auto;
  font-size:clamp(14px,2vw,27px);line-height:1.5;letter-spacing:.16em;
  color:var(--gold-l);text-shadow:0 2px 10px #000}
.couplet .roll{position:absolute;left:50%;width:2px;height:120%;background:#3a2010;
  transform:translateX(-50%);z-index:-1;top:0}
/* 灯笼 */
.lantern{position:absolute;top:5%;width:min(7vw,84px);height:min(9.4vw,112px);z-index:6;
  border-radius:48% 48% 44% 44%/52% 52% 48% 48%;
  background:radial-gradient(circle at 48% 40%,#ffe2a0,#e8982e 52%,#8a3c10 100%);
  box-shadow:0 0 44px rgba(255,170,60,.65),0 0 110px rgba(255,140,40,.35),inset 0 0 18px rgba(120,40,10,.6);
  animation:flicker 3.6s ease-in-out infinite}
.lantern.l1{left:15.5%}.lantern.l2{right:15.5%}
.lantern::before{content:"";position:absolute;left:50%;top:-15%;transform:translateX(-50%);
  width:2px;height:16%;background:#2a1a10}
.lantern::after{content:"";position:absolute;left:50%;bottom:-24%;transform:translateX(-50%);
  width:62%;height:22%;background:linear-gradient(180deg,var(--gold-l),#7a5a20);
  clip-path:polygon(0 0,100% 0,88% 100%,12% 100%)}
@keyframes flicker{0%,100%{filter:brightness(1)}50%{filter:brightness(1.2)}}

/* 书案 */
.desk{position:absolute;left:50%;bottom:1.6%;transform:translateX(-50%);
  width:min(46vw,580px);height:min(15vw,145px);z-index:5;
  background:linear-gradient(180deg,#5e381e,#3a2010);border-radius:8px 8px 4px 4px;
  box-shadow:0 -7px 0 #6e4222,0 18px 44px rgba(0,0,0,.72)}
.desk::before{content:"論語 · 孟子 · 大學 · 中庸";position:absolute;left:0;right:0;top:-2.6em;
  text-align:center;font-size:clamp(11px,1.4vw,18px);color:rgba(232,205,135,.5);letter-spacing:.3em}
.desk::after{content:"";position:absolute;left:8%;right:8%;bottom:14%;height:2px;
  background:rgba(0,0,0,.4);box-shadow:0 1px 0 rgba(255,255,255,.06)}
.book{position:absolute;top:20%;left:12%;width:33%;height:20%;
  background:linear-gradient(90deg,#7a2020,#9a3030);box-shadow:0 4px 12px rgba(0,0,0,.55);
  border-radius:2px;transform:rotate(-3deg)}
.book::after{content:"";position:absolute;right:-32%;top:-10%;width:30%;height:122%;
  background:linear-gradient(90deg,#4a6b52,#35503c);border-radius:2px;transform:rotate(6deg);
  box-shadow:0 4px 12px rgba(0,0,0,.55)}
.scroll{position:absolute;top:26%;right:11%;width:5.5%;height:44%;
  background:linear-gradient(180deg,var(--paper),#dcc398);border-radius:3px;
  box-shadow:0 4px 12px rgba(0,0,0,.55)}
.scroll::before,.scroll::after{content:"";position:absolute;left:-16%;width:132%;height:8%;
  background:linear-gradient(90deg,var(--gold),#8a6a20);border-radius:4px}
.scroll::before{top:-4%}.scroll::after{bottom:-4%}
.brush{position:absolute;top:34%;right:3%;width:16%;height:6%;border-radius:50%;
  background:linear-gradient(90deg,#2a1a10,#4a2c18 40%,#1a0e08);transform:rotate(-14deg);
  box-shadow:0 3px 8px rgba(0,0,0,.5)}
.brush::after{content:"";position:absolute;right:-6%;top:30%;width:12%;height:40%;
  background:linear-gradient(90deg,#e8cd87,#a07a2a);border-radius:50%}

/* 孔子像 */
.sage{position:absolute;left:50%;bottom:min(15vw,145px);transform:translateX(-50%);
  width:min(16vw,160px);height:min(23vw,240px);opacity:.32;pointer-events:none;z-index:4}
.sage svg{width:100%;height:100%;display:block}

/* ============ 流动字幕墙 ============ */
.wall{position:absolute;inset:0;pointer-events:none;z-index:26;overflow:hidden;
  background:rgba(8,5,2,.28);
  -webkit-mask-image:linear-gradient(180deg,transparent,#000 9%,#000 91%,transparent);
          mask-image:linear-gradient(180deg,transparent,#000 9%,#000 91%,transparent)}
.wall .m{position:absolute;left:0;right:-200%;overflow:visible;will-change:transform}
.wall .track{display:flex;white-space:nowrap;will-change:transform;transform:translateZ(0)}
.wall .track>*{flex:none;padding:0 .75em}
/* 实色而非半透明：避免与 wall 的 opacity 再次叠乘导致发灰 */
.wall .track .w{font-size:clamp(18px,2.6vw,34px);letter-spacing:.24em;color:#f4dc9c;font-weight:600;text-shadow:0 0 18px rgba(244,220,156,.55),0 0 6px rgba(0,0,0,.85),0 2px 4px #000}
.wall .track .k{font-size:clamp(17px,2.4vw,31px);letter-spacing:.22em;color:#ead59a;font-weight:600;text-shadow:0 0 16px rgba(234,213,154,.5),0 0 6px rgba(0,0,0,.8),0 2px 4px #000}
.wall .track .g{font-size:clamp(16px,2.2vw,29px);letter-spacing:.2em;color:#d9483b;font-weight:600;text-shadow:0 0 14px rgba(217,72,59,.45),0 0 6px rgba(0,0,0,.9),0 1px 3px #000}
.wall .track .j{font-size:clamp(16px,2.2vw,29px);letter-spacing:.2em;color:#ffd864;font-weight:600;text-shadow:0 0 18px rgba(255,216,100,.6),0 0 6px rgba(0,0,0,.8),0 2px 4px #000}
.wall .track .h{font-size:clamp(15px,2vw,27px);letter-spacing:.2em;color:#7fb98a;font-weight:600;text-shadow:0 0 14px rgba(127,185,138,.4),0 0 6px rgba(0,0,0,.9),0 1px 3px #000}

/* ============ 大门（雕花朱漆宫门） ============ */
.gate-wrap{position:absolute;inset:0;display:flex;align-items:stretch;justify-content:center;
  z-index:30;transform-style:preserve-3d}
/* 门楼 */
.portico{position:absolute;left:50%;top:0;transform:translateX(-50%);z-index:29;
  width:min(80vw,880px);height:100%;pointer-events:none}
.portico .top{position:absolute;left:0;right:0;top:0;height:9%;
  background:linear-gradient(180deg,#2a1a10,#4a2c18 50%,#2a1a10);
  border-bottom:3px solid #6a3e20;box-shadow:0 12px 30px rgba(0,0,0,.7)}
.portico .top::after{content:"";position:absolute;left:0;right:0;bottom:-10px;height:10px;
  background:repeating-linear-gradient(90deg,#7a2020 0,#7a2020 24%,#5a1515 24%,#5a1515 100%)}
.portico .cap{position:absolute;left:0;right:0;top:9%;height:5.5%;
  background:linear-gradient(180deg,#7a2020,#5a1515 60%,#3a0c08)}
.portico .cap::before{content:"";position:absolute;left:6%;right:6%;top:0;bottom:0;
  background:repeating-linear-gradient(90deg,transparent 0,transparent 6.6%,rgba(0,0,0,.35) 6.6%,rgba(0,0,0,.35) 7.6%),
  linear-gradient(180deg,#7a2020,#5a1515)}
.portico .cap::after{content:"";position:absolute;left:10%;right:10%;bottom:-3px;height:3px;background:var(--gold)}
.portico .side{position:absolute;top:14.5%;bottom:0;width:3.6%;
  background:linear-gradient(90deg,#4a2c18,#6a3e20 45%,#3a2010);
  box-shadow:inset 0 0 16px rgba(0,0,0,.6)}
.portico .side.left{left:0}.portico .side.right{right:0}
.portico .side::after{content:"";position:absolute;inset:0;
  background:repeating-linear-gradient(0deg,transparent 0,transparent 12.4%,rgba(0,0,0,.4) 12.4%,rgba(0,0,0,.4) 13.6%)}
/* 门槛 */
.threshold{position:absolute;left:0;right:0;bottom:0;height:5.4%;z-index:31;
  background:linear-gradient(180deg,#5a341c,#3a2010);box-shadow:0 -6px 18px rgba(0,0,0,.65)}
.threshold::after{content:"";position:absolute;left:0;right:0;top:0;height:3px;background:var(--gold)}

.door{position:absolute;top:0;width:50%;height:100%;z-index:30;
  transform-style:preserve-3d;will-change:transform}
.door.left{left:0;transform-origin:0 50%}
.door.right{right:0;transform-origin:100% 50%}
/* 门扇：朱漆底 + 竖棱 */
.face{position:absolute;inset:0;backface-visibility:hidden;
  background:
    repeating-linear-gradient(90deg,rgba(0,0,0,0) 0,rgba(0,0,0,0) 9.2%,rgba(0,0,0,.32) 9.2%,rgba(0,0,0,.32) 9.9%),
    linear-gradient(180deg,#8a2418 0%,#6e1a12 52%,#4a100a 100%);
  border:5px solid #241008;border-radius:2px;
  box-shadow:inset 0 0 70px rgba(0,0,0,.65),inset 0 0 20px rgba(0,0,0,.4);
  overflow:hidden}
/* 门内侧面（厚度） */
.inner{position:absolute;inset:0;background:linear-gradient(90deg,#2a160c,#4a2414 50%,#2a160c);
  transform:rotateY(180deg);backface-visibility:hidden;
  box-shadow:inset 0 0 40px rgba(0,0,0,.8);
  display:flex;align-items:center;justify-content:center}
.inner::after{content:"勤 · 學";font-size:clamp(22px,4vw,46px);letter-spacing:.4em;text-indent:.4em;
  color:rgba(201,162,74,.4);writing-mode:vertical-rl;text-shadow:0 2px 10px #000}
/* 描金边框双层 */
.face::before{content:"";position:absolute;inset:4.5% 5%;border:2px solid rgba(201,162,74,.55)}
.face::after{content:"";position:absolute;inset:7% 7.6%;border:1px solid rgba(201,162,74,.32)}
/* 裙板雕花（回纹 + 团花） */
.apron{position:absolute;left:14%;right:14%;bottom:6%;height:26%;
  border:2px solid rgba(201,162,74,.5);border-radius:4px;overflow:hidden}
.apron::before{content:"";position:absolute;inset:5px;border:1px solid rgba(201,162,74,.3)}
.apron svg{width:100%;height:100%;display:block;opacity:.85}
/* 腰板 */
.waist{position:absolute;left:14%;right:14%;top:6%;height:11%;
  border:2px solid rgba(201,162,74,.45);border-radius:3px}
.waist::after{content:"";position:absolute;inset:4px;border:1px solid rgba(201,162,74,.25)}
/* 门钉：7列5行 浮雕刻花钉 */
.stud{position:absolute;width:7.2%;aspect-ratio:1/1;border-radius:50%;
  background:
    radial-gradient(circle at 34% 30%,#f6e0a0 0%,#d8b460 30%,#a07a2a 58%,#6a4e10 100%);
  box-shadow:0 3px 6px rgba(0,0,0,.65),inset 0 0 5px rgba(0,0,0,.5);
  display:flex;align-items:center;justify-content:center}
.stud::before{content:"";position:absolute;width:52%;height:52%;border-radius:50%;
  background:radial-gradient(circle at 50% 50%,transparent 30%,rgba(120,90,30,.75) 32%,rgba(120,90,30,.75) 46%,transparent 48%);
  mask:radial-gradient(circle,#000 1.6px,transparent 2px) 0 0/26% 26%;-webkit-mask:radial-gradient(circle,#000 1.6px,transparent 2px) 0 0/26% 26%}
/* 辅首（兽面衔环） */
.knocker{position:absolute;left:86%;top:44%;transform:translate(-50%,-50%);
  width:16%;height:26%;z-index:2}
.knocker .plate{position:absolute;inset:0;
  background:radial-gradient(ellipse at center,#c9a24a 0%,#a07a2a 45%,#6a4e10 100%);
  clip-path:polygon(50% 0,78% 14%,92% 40%,92% 60%,78% 86%,50% 100%,22% 86%,8% 60%,8% 40%,22% 14%);
  filter:drop-shadow(0 4px 6px rgba(0,0,0,.7))}
.knocker .plate::after{content:"";position:absolute;inset:18%;
  background:radial-gradient(ellipse at 50% 42%,#6a4e10 0%,#3a2a08 60%,#1a1204 100%);
  clip-path:polygon(50% 0,72% 22%,88% 46%,72% 78%,50% 100%,28% 78%,12% 46%,28% 22%);
  box-shadow:inset 0 2px 6px rgba(0,0,0,.8)}
.knocker .ring{position:absolute;left:50%;top:58%;transform:translate(-50%,-50%);
  width:80%;height:56%;border-radius:50%;border:5px solid #a07a2a;
  box-shadow:0 5px 12px rgba(0,0,0,.7),inset 0 2px 5px rgba(0,0,0,.5)}
.knocker .ring::before{content:"";position:absolute;left:50%;top:-22%;transform:translateX(-50%);
  width:26%;height:30%;border-radius:50%;background:#c9a24a;
  box-shadow:0 2px 5px rgba(0,0,0,.7)}
.door.right .knocker{left:14%}
/* 门缝微光 */
.glow{position:absolute;left:50%;top:2%;transform:translateX(-50%);width:4px;height:92%;
  z-index:32;pointer-events:none;opacity:0;
  background:linear-gradient(180deg,rgba(255,224,170,0),rgba(255,232,190,1) 20%,rgba(255,232,190,1) 80%,rgba(255,224,170,0));
  box-shadow:0 0 30px 10px rgba(255,214,140,.8),0 0 80px 30px rgba(255,190,110,.4);
  mix-blend-mode:screen}
/* 中央题额 */
.gate-title{position:absolute;left:50%;top:21%;transform:translate(-50%,-50%);z-index:33;
  text-align:center;pointer-events:none}
.gate-title .big{font-size:clamp(30px,6vw,68px);letter-spacing:.32em;text-indent:.32em;
  color:var(--gold-l);text-shadow:0 4px 22px #000,0 0 50px rgba(0,0,0,.85)}
.gate-title .sub{margin-top:.5em;font-size:clamp(12px,1.7vw,21px);letter-spacing:.55em;text-indent:.55em;
  color:rgba(232,205,135,.82);text-shadow:0 2px 10px #000}
.gate-title .seal-mark{display:inline-block;margin-top:1em;padding:.35em .9em;border:2px solid rgba(232,205,135,.7);
  border-radius:3px;font-size:clamp(10px,1.2vw,15px);letter-spacing:.2em;color:rgba(232,205,135,.7);
  transform:rotate(-4deg)}
.hint{position:absolute;left:50%;bottom:7.5%;transform:translateX(-50%);z-index:33;
  font-size:clamp(13px,1.7vw,20px);letter-spacing:.3em;color:rgba(232,205,135,.88);
  text-shadow:0 2px 12px #000;pointer-events:none;animation:hintPulse 2.2s ease-in-out infinite}
.hint .arrow{display:block;margin-top:.25em;font-size:1.4em;letter-spacing:0}
@keyframes hintPulse{0%,100%{opacity:.45}50%{opacity:1}}

/* ============ 门后金光 ============ */
.reveal{position:absolute;inset:0;z-index:25;display:flex;align-items:center;justify-content:center;
  background:radial-gradient(ellipse at center,rgba(255,228,176,.94) 0%,rgba(255,196,120,.8) 28%,rgba(180,120,50,.45) 58%,rgba(20,13,9,0) 76%);
  opacity:0;pointer-events:none;mix-blend-mode:screen}
/* 开门后的内景（替代黄片） */
.depth{position:absolute;inset:0;z-index:24;opacity:0;transform:scale(1.05);pointer-events:none;
  background:
    radial-gradient(ellipse at 50% 30%,rgba(255,236,196,.55) 0%,rgba(255,236,196,0) 48%),
    linear-gradient(180deg,#5a381e 0%,#3a2414 40%,#241408 100%);
  transition:opacity 1.4s,transform 1.6s}
.depth .dgate{position:absolute;left:50%;top:50%;transform:translate(-50%,-50%);
  width:min(42vw,500px);height:min(60vh,520px);opacity:.5}
.depth .dgate svg{width:100%;height:100%;display:block}
.depth .steps{position:absolute;left:0;right:0;bottom:0;height:14%;
  background:repeating-linear-gradient(0deg,#4a2c18 0,#4a2c18 30%,#3a2010 30%,#3a2010 100%)}
.depth .floor{position:absolute;left:50%;top:64%;transform:translateX(-50%);width:70%;height:14%;
  background:linear-gradient(90deg,transparent,rgba(255,214,140,.18),transparent)}
.depth .stamp{position:absolute;left:50%;top:20%;transform:translateX(-50%);
  font-size:clamp(30px,7vw,84px);letter-spacing:.5em;text-indent:.5em;
  color:rgba(255,236,190,.16);text-shadow:0 0 40px rgba(255,214,140,.2);writing-mode:vertical-rl}
.particles{position:absolute;inset:0;z-index:26;pointer-events:none}
.particle{position:absolute;bottom:-10px;width:6px;height:6px;border-radius:50%;
  background:radial-gradient(circle,rgba(255,244,200,.95),rgba(255,200,120,0) 70%);
  animation:rise linear infinite;opacity:0}
@keyframes rise{
  0%{transform:translateY(0) scale(.4);opacity:0}
  12%{opacity:1}
  100%{transform:translateY(-105vh) scale(1.3);opacity:0}
}

/* ============ 时间轴 ============ */
.timeline{position:absolute;left:0;right:0;bottom:0;z-index:40;
  padding:min(7vh,64px) 4vw min(4vh,38px);
  display:flex;align-items:flex-end;justify-content:center;gap:clamp(6px,1.1vw,14px);
  flex-wrap:wrap;opacity:0;transform:translateY(30px);pointer-events:none;
  transition:opacity 1s,transform 1s}
.timeline.show{opacity:1;transform:translateY(0);pointer-events:auto}
.era{flex:1 1 108px;max-width:165px;min-width:92px;cursor:pointer;
  background:linear-gradient(180deg,rgba(66,41,26,.94),rgba(30,18,10,.97));
  border:1px solid rgba(201,162,74,.5);border-radius:6px;padding:10px 7px 12px;text-align:center;
  position:relative;overflow:hidden;
  transition:transform .3s,border-color .3s,box-shadow .3s}
.era::before{content:"";position:absolute;left:0;right:0;top:0;height:3px;
  background:linear-gradient(90deg,transparent,var(--gold),transparent)}
.era::after{content:"";position:absolute;left:14%;right:14%;bottom:0;height:2px;
  background:linear-gradient(90deg,transparent,rgba(122,32,32,.8),transparent)}
.era:hover{transform:translateY(-9px);border-color:var(--gold-l);
  box-shadow:0 12px 30px rgba(0,0,0,.65),0 0 24px rgba(201,162,74,.28)}
.era .dyn{font-size:clamp(12px,1.5vw,18px);color:var(--gold-l);letter-spacing:.1em;margin-bottom:3px}
.era .name{font-size:clamp(15px,2vw,24px);color:var(--paper);letter-spacing:.05em;margin-bottom:6px}
.era .key{font-size:clamp(10px,1.05vw,12.5px);color:rgba(232,205,135,.6);line-height:1.5}

/* ============ 详情弹卡 ============ */
.curtain{position:absolute;inset:0;z-index:50;background:rgba(8,5,3,.74);
  display:none;align-items:center;justify-content:center;padding:4vw}
.curtain.show{display:flex;animation:fade .4s ease}
@keyframes fade{from{opacity:0}to{opacity:1}}
.card{width:min(640px,92vw);max-height:84vh;overflow:auto;position:relative;
  background:linear-gradient(180deg,#f7ead4,#ecd9b8);color:var(--ink);
  border-radius:8px;padding:34px 36px 30px;border:3px solid var(--gold);
  box-shadow:0 20px 70px rgba(0,0,0,.72);
  background-image:radial-gradient(circle at 12% 8%,rgba(201,162,74,.14),transparent 40%),
  radial-gradient(circle at 88% 92%,rgba(122,32,32,.1),transparent 42%),linear-gradient(180deg,#f7ead4,#ecd9b8)}
.card::before{content:"";position:absolute;inset:8px;border:1px solid rgba(122,32,32,.35);border-radius:5px;pointer-events:none}
.card .seal{position:absolute;right:26px;top:26px;width:58px;height:58px;border-radius:6px;
  border:2px solid rgba(122,32,32,.7);color:rgba(122,32,32,.75);
  display:flex;align-items:center;justify-content:center;font-size:20px;line-height:.95;
  transform:rotate(-6deg)}
.card .edyn{font-size:14px;letter-spacing:.4em;color:var(--vermilion);margin-bottom:6px}
.card h2{font-size:clamp(24px,3.6vw,36px);color:var(--ink);margin-bottom:4px;letter-spacing:.06em}
.card .epithet{font-size:clamp(13px,1.5vw,16px);color:rgba(43,33,24,.6);margin-bottom:18px;font-style:italic}
.card .divider{height:1px;background:linear-gradient(90deg,transparent,var(--vermilion),transparent);margin:0 0 20px;opacity:.5}
.card .block{margin-bottom:16px}
.card .block h4{font-size:16px;color:var(--vermilion);margin-bottom:6px;letter-spacing:.08em}
.card .block h4 i{font-style:normal;color:var(--gold);margin-right:8px}
.card p{font-size:clamp(14px,1.55vw,16.5px);line-height:1.95;color:#3a2c1c;text-indent:2em;margin-bottom:6px}
.card .quote{margin:18px 0;padding:14px 18px;background:rgba(122,32,32,.06);
  border-left:3px solid var(--vermilion);border-radius:0 4px 4px 0;
  font-size:clamp(14px,1.5vw,16px);line-height:1.9;color:#4a3520}
.card .quote em{font-style:normal;color:var(--vermilion)}
.card .close{margin-top:22px;display:block;width:100%;padding:12px;cursor:pointer;
  background:linear-gradient(180deg,var(--vermilion),#6a1c14);color:var(--paper);
  border:none;border-radius:4px;font-family:inherit;font-size:17px;letter-spacing:.3em;text-indent:.3em;
  box-shadow:0 4px 14px rgba(122,32,32,.4);transition:filter .2s}
.card .close:hover{filter:brightness(1.12)}
.scrollbar{position:absolute;right:6px;top:12px;bottom:12px;width:4px;background:rgba(0,0,0,.1);border-radius:2px}
.scrollbar i{position:absolute;left:0;right:0;background:var(--gold);border-radius:2px}

/* ============ 开场 ============ */
.veil{position:absolute;inset:0;z-index:60;display:flex;align-items:center;justify-content:center;
  background:radial-gradient(ellipse at center,rgba(20,13,9,.72),rgba(8,5,3,.96));
  transition:opacity 1.2s}
.veil.hide{opacity:0;pointer-events:none}
.veil .panel{text-align:center;padding:30px}
.veil h1{font-size:clamp(28px,5.5vw,60px);letter-spacing:.3em;text-indent:.3em;color:var(--gold-l);text-shadow:0 4px 24px #000}
.veil p{margin-top:1em;font-size:clamp(14px,1.8vw,20px);letter-spacing:.2em;color:rgba(232,205,135,.7)}
.veil button{margin-top:2.4em;padding:12px 42px;cursor:pointer;font-family:inherit;
  font-size:clamp(15px,2vw,22px);letter-spacing:.3em;text-indent:.3em;
  background:linear-gradient(180deg,var(--gold),#8a6a20);color:#2b2118;border:none;border-radius:4px;
  box-shadow:0 6px 24px rgba(201,162,74,.35);transition:transform .2s,filter .2s}
.veil button:hover{transform:scale(1.05);filter:brightness(1.1)}

.state-readout{position:absolute;left:50%;top:50%;transform:translate(-50%,-50%);z-index:45;
  font-size:clamp(40px,11vw,140px);letter-spacing:.2em;color:rgba(255,236,190,.92);
  text-shadow:0 0 44px rgba(255,210,140,.65);pointer-events:none;opacity:0}

@media (max-width:640px){
  .pillar{width:6%}
  .plaque{width:62%}
  .couplet{display:none}
  .apron{height:24%}
  .timeline{padding-bottom:2.5vh}
  .card{padding:26px 20px 22px}
}
</style>
</head>
<body>
<div id="app">

  <!-- ===== 内景 ===== -->
  <div class="hall" id="hall">
    <div class="roof"></div>
    <div class="eaves"></div>
    <div class="mountains">
      <svg viewBox="0 0 1200 200" preserveAspectRatio="none">
        <path d="M0,185 L0,130 L130,60 L250,140 L380,35 L520,150 L660,50 L800,160 L920,55 L1060,145 L1180,75 L1200,120 L1200,185 Z" fill="rgba(60,40,24,.5)"/>
        <path d="M0,185 L0,160 L160,115 L320,168 L480,108 L640,168 L820,112 L980,168 L1140,120 L1200,160 L1200,185 Z" fill="rgba(38,24,13,.6)"/>
      </svg>
    </div>
    <div class="skylight"></div>

    <div class="pillars">
      <div class="pillar" style="left:4%"><div class="brace"></div></div>
      <div class="pillar" style="left:13%"></div>
      <div class="pillar" style="right:13%"></div>
      <div class="pillar" right style="right:4%"><div class="brace"></div></div>
    </div>

    <div class="lantern l1"></div>
    <div class="lantern l2"></div>

    <div class="plaque">
      <div class="cn">明 倫 堂</div>
      <div class="en">講經明道之所 · 聚士育賢之地</div>
    </div>

    <div class="couplet left"><span>黑髮不知勤學早</span></div>
    <div class="couplet right"><span>白首方悔讀書遲</span></div>

    <div class="sage">
      <svg viewBox="0 0 100 160">
        <ellipse cx="50" cy="22" rx="18" ry="20" fill="#1a120a"/>
        <path d="M34,30 Q50,8 66,30 Q76,44 66,54 L34,54 Q24,44 34,30 Z" fill="#2a1c10"/>
        <path d="M30,54 Q50,46 70,54 L82,130 L60,140 L60,160 L40,160 L40,140 L18,130 Z" fill="#2a1c10"/>
        <path d="M50,60 L44,100 L56,100 Z" fill="#1a120a"/>
      </svg>
    </div>

    <div class="desk">
      <div class="book"></div>
      <div class="scroll"></div>
      <div class="brush"></div>
    </div>
  </div>

  <!-- ===== 流动字幕墙 ===== -->
  <div class="wall" id="wall"></div>

  <!-- ===== 门后景（替代黄片） ===== -->
  <div class="depth" id="depth">
    <div class="stamp">科 舉 千 秋</div>
    <div class="dgate">
      <svg viewBox="0 0 200 300">
        <rect x="10" y="10" width="180" height="280" fill="none" stroke="rgba(255,236,190,.5)" stroke-width="3"/>
        <rect x="20" y="20" width="80" height="280" fill="rgba(122,32,24,.5)"/>
        <rect x="100" y="20" width="80" height="280" fill="rgba(122,32,24,.5)"/>
        <circle cx="86" cy="130" r="6" fill="rgba(201,162,74,.75)"/>
        <circle cx="114" cy="130" r="6" fill="rgba(201,162,74,.75)"/>
      </svg>
    </div>
    <div class="floor"></div>
    <div class="steps"></div>
  </div>

  <div class="particles" id="particles"></div>
  <div class="reveal" id="reveal"></div>

  <!-- ===== 大门 ===== -->
  <div class="gate-wrap" id="gateWrap">
    <div class="portico">
      <div class="top"></div>
      <div class="cap"></div>
      <div class="side left"></div>
      <div class="side right"></div>
    </div>

    <div class="door left" id="doorL">
      <div class="face">
        <div class="waist"></div>
        <div class="apron">
          <svg viewBox="0 0 100 100" preserveAspectRatio="none">
            <g fill="none" stroke="rgba(201,162,74,.9)" stroke-width="1.6">
              <path d="M5,5 h90 v90 h-90 z M15,15 h70 v70 h-70 z"/>
              <path d="M5,5 l90,90 M95,5 l-90,90"/>
              <circle cx="50" cy="50" r="20"/><circle cx="50" cy="50" r="12"/>
              <path d="M50,28 v44 M28,50 h44 M33,33 l34,34 M67,33 l-34,34"/>
              <path d="M50,8 v14 M50,78 v14 M8,50 h14 M78,50 h14"/>
            </g>
          </svg>
        </div>
      </div>
      <div class="inner"></div>
    </div>

    <div class="door right" id="doorR">
      <div class="face">
        <div class="waist"></div>
        <div class="apron">
          <svg viewBox="0 0 100 100" preserveAspectRatio="none">
            <g fill="none" stroke="rgba(201,162,74,.9)" stroke-width="1.6">
              <rect x="5" y="5" width="90" height="90"/>
              <rect x="15" y="15" width="70" height="70"/>
              <path d="M5,5 l90,90 M95,5 l-90,90"/>
              <circle cx="50" cy="50" r="22"/><circle cx="50" cy="50" r="9"/>
              <path d="M50,26 v48 M26,50 h48"/>
              <path d="M36,36 q14,-12 28,0 q-14,12 -28,0z M36,64 q14,-12 28,0 q-14,12 -28,0z"/>
            </g>
          </svg>
        </div>
      </div>
      <div class="inner"></div>
    </div>

    <div class="threshold"></div>
    <div class="glow" id="glow"></div>

    <div class="gate-title" id="gateTitle">
      <div class="big">登 科 門</div>
      <div class="sub">古 代 人 才 選 拔</div>
      <div class="seal-mark">推 · 門 · 入 · 内</div>
    </div>
    <div class="hint" id="hint">点击或拖开双门<span class="arrow">↔</span></div>
  </div>

  <div class="state-readout" id="readout"></div>

  <!-- ===== 时间轴 ===== -->
  <div class="timeline" id="timeline"></div>

  <!-- ===== 详情弹卡 ===== -->
  <div class="curtain" id="curtain">
    <div class="card" id="card">
      <div class="seal" id="seal"></div>
      <div class="edyn" id="cDyn"></div>
      <h2 id="cName"></h2>
      <div class="epithet" id="cEpi"></div>
      <div class="divider"></div>
      <div id="cBody"></div>
      <button class="close" id="cClose">掩卷而归</button>
      <div class="scrollbar"><i id="cScroll"></i></div>
    </div>
  </div>

  <!-- ===== 开场 ===== -->
  <div class="veil" id="veil">
    <div class="panel">
      <h1>千年科舉路</h1>
      <p>自世卿世禄，至科舉取士 · 一扇門隔開兩重天</p>
      <button id="enterBtn">推門入内</button>
    </div>
  </div>
</div>

<script>
/* ================= 数据 ================= */
const ERAS = [
  {dyn:"夏 · 商 · 西周", abbr:"西周", key:"世卿世禄制",
   name:"世卿世禄制", epi:"大人世及以为礼 · 亲贵官三位一体",
   blocks:[
    {t:"制度要义", c:"以血缘宗法关系为核心，官职与爵位世代承袭。天子—诸侯—卿大夫—士的等级秩序与分封制互为表里，诸侯与卿大夫的子弟在贵族学校习礼，成年后依次继位为官。"},
    {t:"选才标准", c:"不看才学，只看出身。官职在家族内部父死子继，亲、贵、官三者合一，世卿世禄制下形成了中国最早的世官体系。"},
    {t:"制度评价", c:"在宗法社会早期有利于政权的稳定传承，却把天下贤能挡在门第之外。至春秋战国，随着世袭贵族衰败，这一制度逐渐被军功与荐举取代。"}
   ],
   quote:"<em>「大人世及以为礼。」</em>—— 官职在亲族内部承袭，乃西周选官之本。"},
  {dyn:"春秋 · 战国", abbr:"战国", key:"军功授爵 · 荐举养士",
   name:"军功爵制 · 养士荐举", epi:"有军功者，各以率受上爵",
   blocks:[
    {t:"军功爵制", c:"商鞅变法「宗室非有军功，不得为属籍」，以二十等爵授田宅、定服饰、分奴婢，斩一首者爵一级。魏国李悝倡「食有劳而禄有功」，韩国申不害立「循功劳，视次第」，齐国以乡举选才，军功成为布衣上升的正途。"},
    {t:"养士与荐举", c:"战国诸国以高门大馆招揽贤士：齐有稷下学宫，学者不治而议论；秦行相府宾客之制。举荐亦成定制——商鞅由景监荐入秦，范雎经王稽、郑安平引见，甚至可毛遂自荐。"},
    {t:"历史转折", c:"军功授官破除了贵族对官职的垄断，为平民越阶入仕打开通道。但它毕竟只适用于征战年代，天下安定之后，亟需一种更稳定的文官选拔方式。"}
   ],
   quote:"<em>「有军功者，各以率受上爵。」</em>—— 血缘不再等于官位，战功成为新的通行证。"},
  {dyn:"两汉", abbr:"汉", key:"察举 · 征辟",
   name:"察举制 · 征辟制", epi:"乡举里选 · 四科取士",
   blocks:[
    {t:"察举制的确立", c:"汉高祖刘邦下求贤诏开其先河，汉文帝始设贤良方正、直言极谏科目，至汉武帝「令二千石举孝廉」，察举成为定制。东汉以孝廉、茂才为主要科目，由州郡长官按科目向中央定期推荐士人。"},
    {t:"四科取士", c:"一曰德行高妙、志节清白；二曰学通行修、经中博士；三曰明达法令、足以决疑；四曰刚毅多略、才任三辅令。察举重在品行与经术，辅以「对策」「射策」加以考核。"},
    {t:"征辟与别途", c:"皇帝特征聘召名士称「征」，公卿州郡自聘幕僚称「辟」，合称征辟。此外还有博士弟子射策为官的「郎选」、二千石以上高官保举子弟为郎的「任子」，以及汉武帝因军费所开的「赀选」。"}
   ],
   quote:"<em>「举秀才，不知书；察孝廉，父别居。」</em>—— 东汉末乡闾舆论被门阀操纵，察举渐趋腐败。"},
  {dyn:"魏晋南北朝", abbr:"魏", key:"九品中正制",
   name:"九品中正制", epi:"上品无寒门，下品无士族",
   blocks:[
    {t:"九品官人法", c:"公元220年，曹丕采纳吏部尚书陈群之议，在州设大中正、郡设中正，按家世门第与德才将本地人物评为上上至下下九品，吏部据之品授官职，又称「九品官人法」。"},
    {t:"设计初衷", c:"它上承两汉察举、下启隋唐科举，把品评人物之权由地方收归中央，选才标准由乡闾舆论转为中正官评定，本是一次选官权的集中与制度化尝试。"},
    {t:"门阀化结局", c:"中正一职渐被著姓士族垄断，品评唯看出身，「计门第」取代「计德才」，终成「上品无寒门，下品无士族」。隋统一后，这一制度被正式废除。"}
   ],
   quote:"<em>「上品无寒门，下品无士族。」</em>—— 出身决定了一切，门阀政治至此登峰造极。"},
  {dyn:"隋 · 唐", abbr:"唐", key:"科举制 · 常举 制举 武举",
   name:"科举制创立与确立", epi:"分科取士 · 投牒自进",
   blocks:[
    {t:"科举创始于隋", c:"隋文帝开皇七年废九品中正制，设「志行修谨」「清平干济」二科取士；隋炀帝置进士科，以试策取士，科举制度由此正式形成。"},
    {t:"唐代科目", c:"唐承隋制并加完备，分常举与制举两类：常举每年举行，有进士、明经、秀才、俊士、明法、明字、明算、一史、三史、开元礼、道举、童子等五十余科，其中进士科最重；制举由皇帝临时下诏开科取非常之才。武则天长安二年（702年）又增设武举。"},
    {t:"考试程序", c:"士人先应州县「乡试」，合格者称「乡贡」，送至尚书省参加「省试」。进士、明经之外，明法、明字、明算考选法律、书法、数学之才，已初具专业分科取士之形。"}
   ],
   quote:"<em>「朝为田舍郎，暮登天子堂。」</em>—— 科举把读书、应考与做官连为一体。"},
  {dyn:"宋", abbr:"宋", key:"三级考试 · 殿试 糊名誊录",
   name:"科举完备于宋", epi:"糊名誊录 · 一切以程文为去留",
   blocks:[
    {t:"三级与殿试", c:"宋太祖开宝六年（973年）创立殿试，科举由解试、省试两级发展为解试、省试、殿试三级；英宗治平三年（1066年）定「三岁一开科场」，遂为后世定制。"},
    {t:"防弊之制", c:"太宗、真宗时创立封弥（糊名）、誊录，仁宗时废除「公荐」「公卷」，确立「一切以程文为去留」。取士规模空前，两宋共取士十二万余人，年均三百七十余人。"},
    {t:"王安石变法", c:"神宗时废明经诸科，专以进士一科取士；经术考试废帖经、墨义，改以经义、诗赋、论策试进士，奠定了后世科举以经义为主的格局。"}
   ],
   quote:"<em>「一切以程文为去留。」</em>—— 考卷上不著姓名，文章本身成了唯一的尺子。"},
  {dyn:"明", abbr:"明", key:"八股取士 · 科举必由学校",
   name:"科举鼎盛于明", epi:"八股文 · 童试 乡试 会试 殿试",
   blocks:[
    {t:"科举必由学校", c:"明代以前学校只是选才途径之一，至明「科举必由学校」，入国子监者通称监生，科举与官学教育结合达到顶峰。考试分童试、乡试、会试、殿试四级。"},
    {t:"八股取士", c:"以《四书》文句命题，文章定式为八股文，解释一律依朱熹《四书章句集注》，「代圣贤立言」，不得自由发挥。殿试一甲三名赐进士及第，即状元、榜眼、探花。"},
    {t:"科场防弊", c:"搜检、回避、复试、锁院、别试、按号就坐、禁怀挟传义代笔等制度空前严密，科场舞弊的惩处也最为严酷。"}
   ],
   quote:"<em>「科举必由学校。」</em>—— 天下读书人，尽入八股一格之中。"},
  {dyn:"清", abbr:"清", key:"八旗翻译科 · 博学鸿词 · 经济特科",
   name:"科举衰亡于清", epi:"光绪三十一年 · 废科举兴学堂",
   blocks:[
    {t:"沿明而更密", c:"清沿明制，以八股取士。雍正元年（1723年）殿试后增「朝考」，优者用庶吉士；清初分满、汉两榜，后定旗人与汉人一体考试。防弊之制益加周密，科场大案亦屡兴。"},
    {t:"特科之举", c:"康熙十七年开博学鸿词科，延揽遗逸；光绪二十九年（1903年）复开经济特科。科举至此已不再只是常科，而兼纳非常之才。"},
    {t:"千年之终结", c:"科举渊源于南北朝，创始于隋，确立于唐，完备于宋，兴盛于明清，历经约一千三百年。光绪三十一年（1905年），清廷行新学、废科举，这一延续千年的选才之制就此退出历史舞台。"}
   ],
   quote:"<em>「光绪三十一年，行新学，废科举。」</em>—— 一扇门缓缓合上，另一扇门同时打开。"}
];

/* ================= 流动字幕墙 ================= */
const LINES = [
  {c:"w", d:8,  spd:11, dir:1, t:["世卿世禄 · 父死子继 · 大人世及以为礼 · 分封宗法 · 亲贵官三位一体", "軍功授爵 · 二十等爵 · 食有劳而禄有功 · 循功劳视次第", "養士之風 · 稷下學宫 · 毛遂自荐 · 客卿入秦 · 門下三千"]},
  {c:"k", d:20, spd:10, dir:-1, t:["賢良方正 · 直言極諫 · 孝廉茂才 · 四科取士 · 對策射策", "察舉征辟 · 鄉舉里選 · 郎選任子 · 賢良文學 · 計偕赴京"]},
  {c:"g", d:34, spd:8, dir:1, t:["九品中正 · 九品官人法 · 計門第不計德才 · 中正定品 · 州郡著姓", "上品無寒門 · 下品無士族 · 門閥政治 · 譜牒之學"]},
  {c:"j", d:46, spd:7, dir:-1, t:["科舉取士 · 分科舉人 · 投牒自進 · 懷牒自列 · 自由報考", "常舉 · 制舉 · 武舉 · 童子科 · 明經科 · 秀才科 · 明法明字明算", "進士科 · 省試 · 鄉貢 · 行卷温卷 · 曲江宴 · 雁塔題名"]},
  {c:"h", d:58, spd:6, dir:1, t:["糊名謄錄 · 封彌卷首 · 別頭試 · 鎖院避嫌 · 一切以程文為去留", "八股取士 · 四書文 · 代聖賢立言 · 童試鄉試會試殿試 · 貢院棘圍"]},
  {c:"w", d:68, spd:4, dir:-1, t:["十年寒窗 · 頭懸梁錐刺股 · 囊螢映雪 · 三更燈火五更雞", "學而優則仕 · 萬般皆下品惟有讀書高 · 書中自有黃金屋"]},
  {c:"k", d:80, spd:3, dir:1, t:["春風得意馬蹄疾 · 一日看盡長安花 · 金榜題名 · 狀元及第", "連中三元 · 解元會元狀元 · 五子登科 · 衣錦還鄉"]},
  {c:"g", d:92, spd:2, dir:-1, t:["博學鴻詞科 · 經濟特科 · 八旗翻譯科 · 孝廉方正科", "光緒三十一年 · 廢科舉興學堂 · 一千三百年之終結"]}
];
(function(){
  const wall=document.getElementById('wall');
  const rows=[];
  LINES.forEach(row=>{
    const el=document.createElement('div');
    el.className='m';
    el.style.top=row.d+'%';
    el.style.lineHeight='2.0';
    const tr=document.createElement('div');
    tr.className='track';
    const txt=row.t.join(' 　　　◆　　　 ');
    const cls=row.c==='k'?'k':row.c==='g'?'g':row.c==='j'?'j':row.c==='h'?'h':'w';
    const seg=document.createElement('span');seg.className=cls;seg.textContent=txt;
    tr.appendChild(seg);tr.appendChild(seg.cloneNode(true));
    el.appendChild(tr);
    wall.appendChild(el);
    // 速度：spd 越大越慢，形成远近景深
    const speed=(row.dir<0?-1:1)*((14-row.spd)*7+16);
    rows.push({tr,seg,text:txt,speed,offset:0,rev:row.dir<0,cls});
  });

  // 宽度测量：用 Range 取文字几何宽度，元素即便在屏外也能拿到真实值
  function measure(){
    const tmp=document.createElement('div');
    tmp.style.cssText='position:absolute;visibility:hidden;white-space:nowrap;left:-9999px;top:0;font-size:16px';
    document.body.appendChild(tmp);
    const r=document.createElement('div');
    r.className='wall';
    r.style.position='static';
    tmp.appendChild(r);
    const dpr=Math.max(0.75,Math.min(2.5,window.devicePixelRatio||1));
    rows.forEach(row=>{
      const s=document.createElement('span');
      s.className=row.cls;
      s.style.cssText='white-space:nowrap;font-size:inherit';
      s.textContent=row.text;
      r.appendChild(s);
      let w=s.getBoundingClientRect().width;
      // 双段内容按单段宽度记（track 内已有两段）
      w=w/2;
      row.width=Math.max(400,w)*dpr;
      row.half=row.width;
      r.removeChild(s);
    });
    tmp.remove();
  }
  measure();
  window.addEventListener('resize',measure);

  let last=performance.now();
  (function step(now){
    let dt=(now-last)/1000; if(dt>0.05)dt=0.05; if(dt<=0)dt=0.016; last=now;
    rows.forEach(r=>{
      if(!r.width){requestAnimationFrame(step);return;}
      r.offset=(r.offset+r.speed*dt)%r.half;
      const x=r.rev?(r.half+r.offset):(-r.offset);
      r.tr.style.transform='translate3d('+x+'px,0,0)';
    });
    requestAnimationFrame(step);
  })(performance.now());
})();
function clamp(a,v,b){return Math.max(a,Math.min(b,v))}

/* ================= 门钉 + 辅首 ================= */
function buildDoor(door){
  const face=door.querySelector('.face');
  const cols=[16,33,50,67,84], rows=[26,44,62];
  cols.forEach(c=>rows.forEach(r=>{
    const s=document.createElement('div');
    s.className='stud';s.style.left=c+'%';s.style.top=r+'%';face.appendChild(s);
  }));
  const k=document.createElement('div');k.className='knocker';face.appendChild(k);
}
buildDoor(document.getElementById('doorL'));
buildDoor(document.getElementById('doorR'));

/* ================= 粒子 ================= */
(function(){
  const box=document.getElementById('particles');
  for(let i=0;i<42;i++){
    const p=document.createElement('div');
    p.className='particle';
    const s=Math.random()*.8+.45;
    p.style.left=Math.random()*100+'%';
    p.style.animationDuration=(5+Math.random()*9)+'s';
    p.style.animationDelay=(Math.random()*14)+'s';
    p.style.transform=`scale(${s})`;
    box.appendChild(p);
  }
})();

/* ================= 时间轴 ================= */
const tl=document.getElementById('timeline');
ERAS.forEach((e,i)=>{
  const d=document.createElement('div');
  d.className='era';
  d.innerHTML=`<div class="dyn">${e.dyn}</div><div class="name">${e.name}</div><div class="key">${e.key}</div>`;
  d.onclick=()=>openCard(i);
  tl.appendChild(d);
});

/* ================= 弹卡 ================= */
const curtain=document.getElementById('curtain');
function openCard(i){
  const e=ERAS[i];
  document.getElementById('seal').textContent=e.abbr;
  document.getElementById('cDyn').textContent=e.dyn;
  document.getElementById('cName').textContent=e.name;
  document.getElementById('cEpi').textContent=e.epi;
  document.getElementById('cBody').innerHTML=
    e.blocks.map(b=>`<div class="block"><h4><i>▍</i>${b.t}</h4><p>${b.c}</p></div>`).join('')
    +`<div class="quote">${e.quote}</div>`;
  curtain.classList.add('show');updateScroll();
}
document.getElementById('cClose').onclick=()=>curtain.classList.remove('show');
curtain.onclick=e=>{if(e.target===curtain)curtain.classList.remove('show')};
document.addEventListener('keydown',e=>{if(e.key==='Escape'){curtain.classList.remove('show');target=0}});
function updateScroll(){
  const c=document.getElementById('card'),bar=document.getElementById('cScroll');
  const sh=c.scrollHeight,ch=c.clientHeight;
  if(sh<=ch){bar.style.display='none';return}
  bar.style.display='block';
  bar.style.height=(ch/sh*100)+'%';
  bar.style.top=(c.scrollTop/sh*100)+'%';
}
document.getElementById('card').addEventListener('scroll',updateScroll);

/* ================= 开门 ================= */
const doorL=document.getElementById('doorL'),doorR=document.getElementById('doorR');
const hall=document.getElementById('hall'),glow=document.getElementById('glow');
const reveal=document.getElementById('reveal'),depth=document.getElementById('depth');
const hint=document.getElementById('hint'),gateTitle=document.getElementById('gateTitle');
const gateWrap=document.getElementById('gateWrap'),readout=document.getElementById('readout');

let openAmt=0,target=0,opened=false;
let dragging=false,dragStart=0,dragBase=0;

function tick(){
  openAmt+=(target-openAmt)*0.08;
  const ang=openAmt*118;
  doorL.style.transform=`rotateY(${-ang}deg)`;
  doorR.style.transform=`rotateY(${ang}deg)`;
  gateWrap.style.transform=`scale(${1+openAmt*0.05})`;

  // 内景淡入对焦
  hall.style.opacity=0.22+openAmt*0.78;
  hall.style.filter=`blur(${(1-openAmt)*9}px) brightness(${0.48+openAmt*0.85})`;
  hall.style.transform=`scale(${0.93+openAmt*0.13})`;

  // 字幕墙：常驻滚动、亮度固定，不再被逐帧压暗；开门后整体上浮到门后景之上
  const wall=document.getElementById('wall');
  wall.style.opacity=0.8+openAmt*0.2;
  wall.style.filter='none';
  wall.style.zIndex=openAmt>0.15?27:26;

  // 门后：先爆光，后浮现深景
  glow.style.opacity=Math.pow(openAmt,1.5);
  reveal.style.opacity=Math.pow(openAmt,2.4);
  depth.style.opacity=Math.pow(Math.max(0,openAmt-0.35),1.6)*1.05;
  depth.style.transform=`scale(${1.05-openAmt*0.06})`;

  gateTitle.style.opacity=1-openAmt*2.4;
  gateTitle.style.transform=`translate(-50%,${openAmt*-32}px)`;
  hint.style.opacity=(1-openAmt*3)*0.9;

  if(openAmt>0.55&&!opened){
    opened=true;readout.textContent="入 室";readout.style.opacity=1;
    setTimeout(()=>{readout.style.transition='opacity 1.2s';readout.style.opacity=0},700);
    setTimeout(()=>{document.getElementById('timeline').classList.add('show')},500);
  }
  if(openAmt<0.5&&opened){
    opened=false;document.getElementById('timeline').classList.remove('show');
  }
  requestAnimationFrame(tick);
}
requestAnimationFrame(tick);

function tog(e){
  if(target>0.4){target=0;hint.style.display='block'}
  else{target=1;hint.style.display='none'}
}
gateWrap.addEventListener('click',tog);
function ds(x){if(target>=1)return;dragging=true;dragStart=x;dragBase=target;gateWrap.style.cursor='grabbing'}
function dm(x){if(!dragging)return;const w=window.innerWidth;
  target=Math.min(1,Math.max(0,dragBase+(x-dragStart)/w*1.6));
  if(target>0.05)hint.style.display='none'}
function de(){dragging=false;gateWrap.style.cursor=''}
doorL.addEventListener('mousedown',e=>{e.stopPropagation();ds(e.clientX)});
doorR.addEventListener('mousedown',e=>{e.stopPropagation();ds(e.clientX)});
window.addEventListener('mousemove',e=>dm(e.clientX));
window.addEventListener('mouseup',de);
doorL.addEventListener('touchstart',e=>{e.stopPropagation();ds(e.touches[0].clientX)},{passive:true});
doorR.addEventListener('touchstart',e=>{e.stopPropagation();ds(e.touches[0].clientX)},{passive:true});
window.addEventListener('touchmove',e=>dm(e.touches[0].clientX),{passive:true});
window.addEventListener('touchend',de);
document.addEventListener('keydown',e=>{
  if(e.key==='ArrowLeft'||e.key==='ArrowRight'||e.key===' '){tog(e)}
});
let wl=false;
window.addEventListener('wheel',e=>{
  if(target<0.05&&e.deltaY>8&&!wl){wl=true;target=1;hint.style.display='none';setTimeout(()=>wl=false,900)}
},{passive:true});

/* ================= 开场 ================= */
document.getElementById('enterBtn').onclick=()=>{
  const v=document.getElementById('veil');
  v.classList.add('hide');setTimeout(()=>v.style.display='none',1300);
};
</script>
</body>
</html>
