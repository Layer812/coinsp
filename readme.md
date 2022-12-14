# coinsp (Coin Insert Sound Player)
人気ガチャ[コイン投入口](https://tama-kyu.com/lineup/cointounyuguchi/)にコイン投入音(通称:バキューン)を再生させる魔改造です。<br>
[こんな感じの物](https://twitter.com/layer812/status/1565692875064885248)が出来上がります。<br>
![IMG_3628](https://user-images.githubusercontent.com/111331376/190154078-3bc946c0-95fe-468a-ac1c-b80aed325abc.jpg)

## 作り方
### 使うもの
 - [コイン投入口](https://tama-kyu.com/lineup/cointounyuguchi/)
 - [Pimoroni Tiny2040](https://www.switch-science.com/catalog/7615/) 1個
 - [マイクロスピーカー8Ω](https://akizukidenshi.com/catalog/g/gP-12494/) 1個
 - [ディテクタスイッチ](https://akizukidenshi.com/catalog/g/gP-05031/) 1個
 - [2Wアンプモジュール](https://akizukidenshi.com/catalog/g/gK-08217/) 1個
 - ドリル
 - ジャンパ線適宜
 - 鳴らしたいvgmファイル(YM2149かAY-3-8910向け)
 - 100円

![使うもの](https://user-images.githubusercontent.com/111331376/190069098-7a068b2d-af8c-4e2d-89e0-dc66c8c74091.jpg)

### 結線図
以下の結線図の様に各部品を接続します。<br>
電池と上部のスイッチから出ている線はLED基盤に接続している既存の線です。<br>
 ![結線図](https://user-images.githubusercontent.com/111331376/190074215-4a93f07b-73cc-4cb4-85f6-fa01eee383dd.png)

### 改造手順
1.5本のネジを外し裏蓋を開けます。<br>
2.LED基盤を取り付けているホットボンドをある程度取ります。<br>
　![LED基盤](https://user-images.githubusercontent.com/111331376/190109123-f75c9168-653e-4abd-863b-73fe9be7536d.jpg)<br>
3.LED基盤に繋がっている２本の線(白と黒)をLED基盤ギリギリで切断します。<br>
4.切断した２本の線を結線図にあるようにTiny2040に接続します。<br>
5.Tiny2040を両面テープなどでLED基盤のあった場所に固定します。<br>
　コイン投入の邪魔にならないように少し左にオフセットして固定します。<br>
  ![IMG_3622](https://user-images.githubusercontent.com/111331376/190109795-620534e2-a48e-4b2b-9829-e7cd04a98db7.jpg)<br>
6.結線図に従ってデテクタスイッチ、アンプ、スピーカーと結線します。<br>
　基盤上の表記A0にディテクタスイッチ、A1にアンプの(+)入力を結線します。<br>
　![IMG_3624](https://user-images.githubusercontent.com/111331376/190153688-288163e2-1fc0-4d44-a961-430d5d3d11b7.jpg)<br>
7.スピーカーを上蓋の正面から見て左側の壁に設置します。<br>
　ネジ固定の柱を避けるためニッパー等で切断します。<br>
　接着前に壁に穴を開けておくと、音が大きくなって良いです。<br>
8.コイン投入口の下の方にディテクタスイッチを固定します。<br>
　穴が100円より大きいので大胆にスイッチが押し込める位の位置で大丈夫です。<br>
9.電池を抜いてTiny2040にUSB接続を行い、次項のソフトウェア設定を行い、vgmファイルを書き込みます。<br>
　ディテクタスイッチを押しこみ、コイン投入音が鳴ることを確認してください。<br>
　![IMG_3625](https://user-images.githubusercontent.com/111331376/190153878-a7d630c2-76dd-4cab-997b-037cf14b8a6a.jpg)<br>
10.気合で上蓋を閉めてネジを締めこみます。<br>
　断線しないように＋コイン投入口を線でふさがないように注意しましょう。<br>
11.電池を入れれば完成です。<br>
　![IMG_3628](https://user-images.githubusercontent.com/111331376/190154078-3bc946c0-95fe-468a-ac1c-b80aed325abc.jpg)<br>

### ソフトウェア設定
1.VGMファイル準備<br>
　VGMファイルがvgz形式の場合、7zipやgzipなどで展開しvgm形式にします。<br>
2.ファームウェア書き込み<br>
　tiny2040をUSB接続モードで起動し、firmware.uf2を書き込みます。<br>
3.ファイル書き込み<br>
　Thonnyなどを使い、main.pyと上記vgmファイルを同じディレクトリに転送します。<br>

## 補足
 - 電池を入れたままUSBを繋がないでください。
 - 複数のvgmファイルを入れるとランダムに１曲演奏します。
 - オリジナルと見分けがつかないように赤く光らせていますが、七色に光らせても恰好良いかもです。
 - ドリルで穴を開ける時、手をケガしないようにしてください。
 - firmware.uf2に含むPwmPSGの実装は[とよしまさん](https://twitter.com/toyoshim)及び[boochowpさん](https://twitter.com/boochowp)のコードをパ..参考にしています。

## 制限
 - VGMコマンド全てには対応していません。
 - 読み込めるVGMファイルサイズは160Kbyte位までです。
 - 本記事内容及びプログラムを使用したことにより発生する、いかなる損害も補償しません。

## Thanks to
 - [SoundCortexLPC](https://github.com/toyoshim/SoundCortexLPC) 音楽も懐かしハードもソフトもスパコンも...凄い
 - [楽しくやろう。](https://blog.boochow.com/) 天才

## ライセンス
 [Apache License v2.0](http://www.apache.org/licenses/LICENSE-2.0)に基づいてご利用ください。ご連絡は[layer8](https://twitter.com/layer812)までお願いします。
