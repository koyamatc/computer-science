---
layout: post
postTitle:  Ancient Cryptography
date:   2014-11-30 23:00:00
categories: crypto 
---

## What is cryptography?

<div class="row">
	<div class="col-sm-5">
		<div id="svg01"></div>
	</div>
	<div class="col-sm-7">
		アリスは遠方のボブに大切な情報を送ろうとしています。<br>
		イブは途中でそれを盗み見ようとします。<br><br>
		そこでアリスは、大切な情報を秘密のコードで書き、箱に入れ、
		その箱にダイアル錠をかけロックします。(encryption:暗号化)<br><br>
		ダイアル錠の番号と秘密のコードの解き方はアリスとボブだけが知っています。<br>
		アリスはボブにその箱を送ります。<br><br>
		途中でイブがその箱を盗んだとしても、鍵が開けられません、
		もし開けたとしても秘密のコードで書かれているので読むことができません。<br><br>
		ボブは受け取った箱のロックを外し、秘密のコードを元の文章に戻します。（decryption:解読）<br><br>
		ボブは大切な情報を読むことができました。
	</div>
</div>

--------

## The Caesar cipher

__置換暗号(substitution cipher)__

紀元前５８年ごろ、ジュリアス・シーザーが軍事命令文書の中で使いました

今ではシーザー暗号と言われています。

文書の各文字を決められた文字数分移動した文字に置き換えて文書を作成します。

たとえば、送り手と受けての間で、３つ移動すると決めたとすると

元の文章のＡはＤに、ＢはＥにＤはＧに置換されます（encryption）

$$LOVE \quad LETTERS \to orzh \quad OHXXHUV$$ 

すると、意味のない文書ができあがります

敵が読んでもまったく内容はわかりません

受けては決まりに従って、暗号化された文書を元に戻します(decryption)

シーザー暗号は、８００年後アラブの数学者アル・キンドによって解読方法が公開されました

その方法は、言語の重要な要素で、各文字が出現する頻度を調べそれを手掛かりに解いたのです

英語では、Eが最も多く使われます、暗号化した文書でHが最も多く使われていれば、
３つシフトしていることがわかります。

これで元の文書がわかります

この方法を frequency analysis(頻度分析)といいます

-------

## Polyalphabetic cipher

解読の手掛かりとなるもの（文字の出現頻度）を平坦にして分かり辛くする方法として、

１５世紀中ごろまでに開発された暗号化方法が、polyalphabetic cipherです

Alberti cipherとよばれます

文字を変換するのに複数の文字を使用します、たとえば単語など

アリスとボブの間で　SNAKE　という単語を使うことを決めたとします

SNAKE を数字に変換します 19 14 1 11 5

元のメッセージの文字を、この数字の順番にシフトしていきます

$$LOVE \quad LETTERS \to ECWP \quad QXUEPWL$$

文字数が多いほど、暗号は難解になります

しかし、メッセージの暗号化に同じ単語を繰り返し使っていると

平坦化した頻度にも差が表れてきます

そこから使われている単語の文字数が見破られると

シーザー暗号と同様に解読されてしまいます

---------

## One-time pad

400年間、問題は解決されず、指紋を隠し、情報の漏えいを止める暗号の開発はどうなったでしょう

その答えは”ランダム性”です

単語をシフトコードとするのではなく、
たとえばアリスが２６面のさいころを振って出た目のランダムな長いリストを変換コードとしてボブと共有します

この変換コードのリストがメッセージと同じくらい長ければ、繰り返しによる解読を防げることが重要です。

イブがこの暗号文を読もうとしても、２つの強力な属性がそれを妨げます

1.  この変換パターンは繰り返しにならない

2. 文字の出現頻度は平坦になります

したがって、暗号を破るための情報漏えいが発生しません

これが暗号化の最も強力なメソッドであり、１９世紀の終わりには出現しました

今では __one-time pad__ として知られています

one-time padの強力さを認識するには、組合せ数の激増が起こることを理解する必要ががあります

シーザー暗号の場合、"ALICE"を変換するのに1から26のうちの１つを変換コードとして各文字を変換します

その暗号の組み合わせ数は26です

組合せ数が少ないと、力ずく探査ですべての組合せを見つけられてしまいます

これに比べ、one-time padでは、各文字ごとに1-26の異なる変換が行われます

つまり"ALICE"であれば 26x26x26x26x26 約１,200万通りになります

1,200万通りの５文字の連なりの中から、ランダムに選ばれた変換コードで暗号化されたメッセージは
パーフェクトです。

------------

## Frequency stability property

２つの部屋があり、それぞれの部屋に男性一人、女性一人がいます

男性はコイン投げて、表が出たら部屋の電灯を点け、浦が出たら電灯を消します

点灯した時を1、消灯した時を0とします

女性は、任意に電灯を点けたり消したりします

二人は同時にスイッチを操作し、この動作を繰り返します。

二人の操作は1と0の並びとして表せます

２つの数字の並びを見て、どちらがコインを使っているかわかるでしょうか

わかるのです

３回連続した数の並び110,010,001などの出現頻度を調べます

コインを使ている場合、この頻度は一様になりますが、
人が任意で操作した場合には頻度は凸凹になります

このように頻度が一様になることを __Frequency Stability__ といいます















<script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_SVG"></script>
<script src="http://d3js.org/d3.v3.min.js" charset="utf-8"></script>
<script src="{{site.url}}/js/d3draws.js" charset="utf-8"></script>

<script>

  var height = 400;
  var width = 400;
  

/**  */
  var svg01 = d3.select("#svg01")
                .append("svg")
                .attr("height",height)
                .attr("width",width)
                .style("background","#000");


  // line
  var rectData01 = [
    {"x":170,"y":75,"width":60,"height":50,"stroke":"#f0f" },
    {"x":40,"y":275,"width":60,"height":50,"stroke":"lime" },
    {"x":300,"y":275,"width":60,"height":50,"stroke":"lime" }
  ];
  drawRect(svg01,rectData01);

  // vector
  var vecData01 = [
    {
      "x1":100,
      "y1":300,
      "x2":300,
      "y2":300,
      "stroke":"#ff0",
      "strokeWidth":4
    },
    {
      "x1":200,
      "y1":300,
      "x2":200,
      "y2":125,
      "stroke":"#f0f",
      "strokeWidth":3
    }
  ];
  drawVectorB(svg01,vecData01);

  // TEXT
  var textData01 = [
    {"x":200,"y":110,
    	"text":"イブ",
    	"stroke":"#fff",
    	"fontSize":"20px",
    	"anchor":"middle"},
    {"x":70,"y":310,
    	"text":"アリス",
    	"stroke":"#fff",
    	"fontSize":"20px",
    	"anchor":"middle"},
    {"x":330,"y":310,
    	"text":"ボブ",
    	"stroke":"#fff",
    	"fontSize":"20px",
    	"anchor":"middle"},
  ];
  drawText(svg01,textData01);

</script>
