# 5374について
##「いつ、どのゴミが収集されているのか？」

ゴミの問題はどの地域でも深刻になりつつあります。
 [Code for Kanazawa](http://codeforkanazawa.org/)
では、先ずは正しいゴミの捨て方に注目しました。例えばお引っ越しをされた場合や、新しく船橋市に住むことになった時、このアプリを使えばすぐに分かるように、目的と使い方をとてもシンプルにデザインしました。

《使い方》

■色でゴミのジャンルを表示
一番近いゴミの日とジャンルを上から順に表示しています。

■捨てる事が可能なゴミ
ゴミのジャンルをタップすると、捨てることが可能なゴミの一覧を見ることができます。

■設定
お住まいの地域を選択することで、ゴミ収集日が自動的に更新されます。
今後スマートフォンのGPSから位置情報を取得する機能を追加する予定です。

[5374 for kanazawa](http://kanazawa.5374.jp/ )を使う。


##提供されるゴミ情報について
船橋市が公開しているホームページデータをもとにしています。

##開発チームとライセンスについて
- 小野 祐貴(Yuki ONO)　Developer
- 五十川 員申(Kazunobu IKAGAWA)　Developer
- 高木 志宗(Yukimune TAKAGI)　Developer
- 宮田 人司(Hotoshi MIYATA)　Designer

本アプリ及びソースコードの著作権はCode for Kanazawaに帰属します。
但し、このソースコードは[MPL](http://www.mozilla.org/MPL/2.0/)のもと配布されています。MPLに従えば、どなたでも利用、改変、及び再配布が可能です。

## 5374をあなたの地域に導入したい場合について

あなたの地域で5374を立ち上げたい場合、以下のドキュメントがきっと役立ちます。ご参考ください。
- [5374(ゴミナシ).jpサービスの立ち上げに必要なデータの準備](http://qiita.com/tosato3/items/e7a231e8190508e278fa)
- [地元の 5374 を、自前サーバを用意せずに github pages で公開する手順](http://qiita.com/kuboon/items/1b4f64a42ce5365fb1c7)

## 5374のカスタマイズについて

基本的にはdataフォルダの中を変更していただければ、データが変更できます。

Code for Kanazawaでは美しいデザインで問題解決を出来ればと考えています。
ゴミの項目数など金沢市と違う所もあると思いますが、使う色に関してのデザインガイドラインを作成しました。同梱の5374colormanual.pdfを参考に色を指定して頂けると幸いです。

generateフォルダは
特に金沢のゴミの解析用のプログラムなので、他の地域では使用しないと思いますが、参考までに同梱します。

unusedは将来的には使用するかもしれないプログラムなどが入っております。
具体的には、位置情報をもとに自分のエリアを自動的に設定するプログラムを作っておりましたが、諸事情により、現時点では使用されておりません。

## data/remarks.csvの仕様
ゴミ収集日に注意事項を追加したい場合に記述します。特別な条件がなければ使いません。
ID,注意事項
の形で記述してください。
例えば以下のようになります。
1,一部地域（渋谷1・2・3丁目）で収集曜日が異なります。

## data/area_days.csvの仕様

各エリアのゴミを出す曜日を記述します。
特に金沢の場合、１月にセンターが休止期間があり、
その期間１週間ずらすという仕様のため、センターの名称を記述します。

### 地名

ゴミの地名を記述します。

###センター

上記の理由で、ゴミ処理センターを記述します。
data/center.csvと対応した、名称を記述します。
特にそのような仕様がない場合は、センターの列は、空文字でも大丈夫です。

### 燃やすごみ,燃やさないごみ,資源,びん

ゴミのカテゴリについて、ゴミの捨てる曜日を記述します。
曜日は「日」・「月」・「火」・「水」・「木」・「金」・「土」
という各曜日の一文字を記述します。

毎週の場合は、一文字だけ記述する。第1週などの限定がある場合、月1と記述する。
また、複数ある場合は、半角スペースで区切り記述する。

つまり、毎週月曜・木曜の場合は 「月 木」と記述する。
毎月第1週月曜の場合は、「月1」と記述する。

（茨城町版仕様より追加） 毎月収集が無いゴミは対象月をコロン(:)の後に指定できます。 例えば、４、６、８、１０、１２、２月の偶数月の第２火曜、第４金曜の場合には、 火2 金4:4 6 8 10 12 2 のように記述します。
＊この機能を利用する場合は、下記にあるsetting.jsのWeekShift = trueをfalseに変更して下さい。

（渋谷区版仕様より追加）収集日について、特別な条件がある場合、例えば「一部地域（渋谷1・2・3丁目）で収集曜日が異なります。」などという条件がある場合、data/remarks.csv を用意し注意事項を追加した後、* につづいてremarks.csv のID番号を記述してください。つまり、remarks.csv のID１番を表示したい場合は、火 木 *1 のように記述します。


## data/center.csvの仕様

上記の理由で、センターの休止期間を記述します。
そういった仕様がない場合は、空のファイルにしてもらっても大丈夫です。


## data/description.csvの仕様

各ゴミの分別を記述します。

### label

ゴミの分別名を記述します。

### sublabel

現在、使用されておりません。

### description

現在、使用されておりません。

### styles

カテゴリの表示となる。イメージ画像を指定します。（デフォルトはsvgとなっております。）

### bgcolor
背景で使う色を指定して下さい。

## data/target.csvの仕様

あるゴミが、どのゴミの日に捨てられるかのリストを表す。
画面表示上では、各ゴミをタップした時のアコーディオンをタップした時の
表示されるものである。


### type

typeの値としてはそれぞれ
description.csvで記述したものでこれをもとに、紐付けを行う。
（例：「燃えるゴミ」、「燃えないゴミ」、「びんゴミ」、「資源ゴミ」など）

### name

ゴミの名前です。

### notice

このゴミを捨てるときの注意事項を記述します。
*ただし、本アプリケーションでは現在使用されておりません*

### furigana

リストで表示する際のラベルとしてのふりがなを指定します。
このふりがなによってグルーピングされます。

## その他のカスタマイズについて

メインのスクリプトファイルは　js/script.jsをカスタマイズしてください。

cssはcustom.cssとなっております。

このアプリケーションは

[Twitter bootstrap](http://getbootstrap.com/javascript/)のライブラリ

[mobile-bookmark-bubble](https://code.google.com/p/mobile-bookmark-bubble/)のライブラリを使用しており、
それらのファイルも含まれております。
##定数（茨城町版仕様より追加）

js/setting.jpに定数を追加しています。

###SVGLabel

SVGイメージを使用するときは、true ※金沢市版はSVGも用意している為、trueを指定します。
用意できない場合は、falseを指定して下さい。
###MaxDescription

ごみの最大の種類数を指定します。最大値９を超えない場合は設定の必要は特にありません。

###MaxMonth

何ヶ月先まで計算するかを指定します。

###WeekShift

金沢仕様の休止期間なら週をずらす処理を有効にするときは、trueを指定します。 茨城町版の記述方法で指定した場合はfalseを指定します。

#生駒市の方からプルリクエストで

回収日が不定期な場合にも簡単に対応する事ができるようになりました。

##不定期な場合のデータ

・area_days.csv 　area_days.csvにて、不定期な日付を半角スペース区切りで、以下のように指定します。
　20140301 20140325・・・ 　形式はYYYYMMDDとなります。
