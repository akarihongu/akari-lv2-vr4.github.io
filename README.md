# akari-lv2-vr4.github.io

「ヘッダー
320pxでNAVIとRECRUITの間隔が空けてくれていますが、今後はRECRUITが端にぴったりとくっついてしまいました。
カンプは375pxですので、320px〜374pxでNAVIやRECRUITのサイズを少し小さくすると、バランス良く整えられます」

→いろいろと試行錯誤した結果、「RECRUIT」の黄色ボタンをこのような形で修正しカンプに近づけました。

（参考）
https://kamuiblog.com/css-button-responsive/

.header-btn {

        display: inline-block;
        max-width:81px;
        width:  30%;
        max-height: 48px;
               
	/* box-sizing: border-box; */
        /* width: 30%; */
        /* padding:   */
	  /* margin-right: 15px; */
        text-align: center;
        /* box-sizing: border-box;
        max-width: 151px;
        padding-top: 15px;
        padding-bottom: 15px;
        width: 90%; */
    }


「769〜inner幅(1080px)でも不自然にならないようにする
画像を縮小すると良いとこちらからお伝えしておいて申し訳ないのですが、やはりまだアンバランス感が拭えません

カンプが無い範囲なので、これが正解！という決まったものがあるわけではないのですが、一例としてムービーを添付しますね。
元の比率をある程度保ったまま小さくなっていくイメージです。

この範囲は特にフォントサイズ等に指定はないので、ヘッダーと同じく要素自体を小さくして調節するとうまくいく場合も多いです」


該当の画像とテキストのwidthを調整して、不自然さを解消しました。

.headmain-copy {
    width: 43%;
    min-width: 505px;
}

.heading-img {
    max-width: 560px;
    width: 50%; 
    height: auto;
}


しっくりこず、さらにサイトで「コンテンツのレスポンシブ対応、比率」など検索し、フォントサイズのレスポンシブ対応を発見
（参考）
https://www.ivy-web.com/blog/css-font-size/

「日本の会社を、みちびく会社」タイトル：

.headmain-ttl {
    color: #333333;
    /* width: 505px; */
    font-size: 3.3vw;
    font-weight: bold;
    line-height: 1.7;
}

その下のテキスト：

.headmain-copy p {
    /* width: 43%; */
    /* max-width: 505px; */
    /* min-width: 505px; */
    color: #333333;
    font-size: 1.4vw;
    line-height: 1.7;
    margin-top: 34px;
    margin-bottom: 40px;
    /* box-sizing: border-box;
    padding-right: 15px;
    padding-left: 15px; */
}

上記二点の修正ですが、ギリギリ違和感ないかな・・？という感触です💦
こちらに関して、自力では10時間以上調べて万策尽きている状態です。
もし更なる修正が必要でしたら、本当に申し訳ないですが、少しヒントをいただけるとありがたいです🙇‍♀️💦


「文字改行について
“カンプと全く同じにする“という意識を持って取り組んでいらっしゃるのは
Goodですね◎

ただ今回の場合、 width:450px;を消して<br>とletter-spacingで調整する必要はありません

というのも、テキストを内包している要素(.about-p)の長さを適切に指定すれば、
自然とカンプ通りに改行されるからです。

width:450px;を復活させて、<br>とletter-spacingを消してみてください。
カンプと同じ改行になるはずです。

また、letter-spacingで文字詰めしたことによって、スマホサイズでの文章が詰まりすぎてしまっていますね。

実はXDカンプの「AV」という項目がletter-spacingを表しています(添付スクリーンショット)
ここが0pxになっていたら、letter-spacingはかかっていないということになりますね」


→アドバイスいただいた通りに指定し直し、さらに横並びしている画像と伸縮の比率をwidthで整えました。

.about-p {
    color: #333333;
    line-height: 1.7;
    max-width: 450px;
    margin-top: 30px;
    margin-bottom: 30px;
    /* letter-spacing: -0.1em; */
}

.img-about {
    max-width: 450px;
    width: 85%;
    height: auto;
    box-shadow: 0 11px 20px #00000029;
    /* margin: 40px; */
}


→「見本をいかに再現するか」ということに腐心し、大前提である「見やすいサイト」として作成する意識が抜けていました。
ご指摘ありがとうございます！🙇‍♀️


「SERVICE
フォントの大きさ、太さをご確認ください。また、320px幅で見出しが両端にくっついているので、ヘッダーと同じく左右に余白をつけましょう！」

→それぞれのサイズでのフォントサイズを整え、緑の横棒両端にmarginで余白を入れました。


「ABOUT
・2つのarticleの両端がそろっていない
何度も指摘しまってすみません…！

やはりこちらが揃っていない状態ですね。(添付スクリーンショット)

ここでは「inner」の考え方がヒントになります。
このページの要素全体は1080pxにおさまっていますが、このABOUTのテキストと画像は何pxにおさまっているでしょうか。
テキストと画像は450px、間隔が40pxなので940pxですね。

「ABOUTの中でひとまわり小さなinnerを作る」ようなイメージで
修正してみてください」


→「ABOUT」の要素ごとにそれぞれにちまちまつけていたpadding、marginを一掃し、要素のinnerである「.a-box」という枠で1080pxの幅の中に70pxの余白を作りました。

.a-box {
    max-width: 1080px;
    padding: 0 70px;
    /* max-width: 90%; */
    margin-right: auto;
    margin-left: auto;
    display: flex;
    align-items: center;
    justify-content: center;
    margin-bottom: 100px;
    /* padding: 0 70px; */
}


「フッター
まだ一番下にわずかに空白がありますね

デベロッパーツールで再検証してみてください。footerのいずれかのクラスにかかっているcssが悪さをしているようです。
また、フッターのみ1080pxにおさまらずに広がってしまっています。左右のpadding、margin含め、カンプ通りの配置になっているか改めてご確認ください」

まず、.footer-innerに指定していた
・左右padding: 10%;　→削除

また、max-heightと間違えて
「 max-block-size: 135px;」　？？？
と記入していた（自動入力で間違いを見落としていた？）ものを削除。

footer下が浮く原因だった.f-copyのmargin-bottom:20px;を削除し、代わりに.f-copyの親要素であるfooterのmargin-bottomでレイアウトを整える。

 .f-copy {
            margin-top: 40px;
            /* margin-bottom: 20px; */
            /* margin: 40px auto 20px; */
        }

footer {
        width: 100%;
        height: 289px;
        box-sizing: border-box;
        padding-bottom:20px;
        }



特に苦戦した「ABOUT」を改めて修正してみて、いかに自分がちぐはぐで遠回りなレイアウトをしていたかよくわかりました。
「innerが大事！」という意味がだいぶ理解できたと思います。

頭では「大枠で捉え、シンプルに」とわかっていても、いざコーディングしていくとカンプの数字にとらわれてそのまま数値を指定してしまっていました。修正にもどこがどこだか把握するのにも多大な時間を費やしました。

要素が増えて構造が複雑になっても、要素ごとにごちゃごちゃ余白をつけて幅を調節するのではなく、いろいろ要素を入れた上で箱そのものの幅・高さを調節をするイメージで考えるよう気をつけます💡

以上、よろしくお願いいたします。
