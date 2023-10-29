# しぇあまど

[![IMAGE ALT TEXT HERE](https://jphacks.com/wp-content/uploads/2023/07/JPHACKS2023_ogp.png)](https://www.youtube.com/watch?v=yYRQEdfGjEg)

## 製品概要
これは退屈な移動時間と日常に新しい視点を提供し、新しい発見をしたり、知らなかった素敵な景色を見逃さないためのアプリです。<br>
季節と時間帯に合わせた車窓スポットの投稿と共有、車窓スポット接近通知、すれちがい通信、乗り過ごし防止通知<br>
などの機能を提供します。乗り過ごしを防ぎながら、お気に入りの景色の共有と新たな発見を楽しめます。<br>
すれ違い通信ではすれ違ったユーザーと互いにお気に入りの車窓を交換し、ユーザー同士がつながります。

### 背景(製品開発のきっかけ、課題等）
毎日の通勤通学でスマホをいじったり、ぼーっとしたりしている人が多く、そんな人たちの変わり映えのない日常生活をより豊かにしたいと感じました。
特に社会人になると、毎日同じ時間に同じ電車に乗ることが多くなり、学生時代のように自由に日常生活に楽しいことを見つけるのが難しくなると思いました。<br>
そこで、私たちはそんな変わり映えしない日常を変化のある楽しめる物にしたいと考えました。


### 製品説明（具体的な製品の説明）
発表資料
https://1drv.ms/p/s!AskvRHPgeAdvjh6nozA5qsTQH7f4
### 特長
#### 1. 特長1
近くの車窓の写真が見れる！<br>
他の人が撮影した写真が表示されます。<br>
電車の窓から外を見てください、その写真と同じ景色が現れるかもしれません！<br>
また、違う季節の写真と見比べて、変化を楽しむこともできます。<br>
#### 2. 特長2
自分の好きな景色を共有できる！<br>
ふと電車から外を眺めると、「いい景色だな」と思うことはありませんか？<br>
ぜひ、写真に残して、他の人に共有しましょう！<br>

### 解決出来ること
*マンネリ化した日常生活に変化を与えることができる。
*変わり映えしない日常を変化のある楽しめる物にすることができる。
*日常生活において新たな発見をすることができる。
*他の人が自分と同じ路線での生活で知った発見を共有してもらうことができる。
*自分の好きな車窓を共有することができる。

### 今後の展望
*　すれ違い通信のような機能を導入し、すれ違った人のお気に入りの車窓を共有できるようにする
*　降りる駅でのリマインド機能を搭載する
* 広告を導入し、その路線の地域活性に活かす

### 注力したこと（こだわり等）
* ユーザーが親しみがあり、見やすいデザインにするため、交通系アプリで浸透している緑色を中心とした配色に統一
* ユーザーが触りたくなるようにボタン配置
* バックグラウンドでも位置情報を取得できる

## 開発技術
### 活用した技術
#### API・データ
* Google Maps API
* 国土数値情報 鉄道データ

#### フレームワーク・ライブラリ・モジュール
##### フロントエンド
* Flutter
* Dart
* Maps SDK for iOS
* (Maps SDK for Android)

##### バックエンド
* Firebase(Cloud Functions/Cloud Firestore/Cloud Storage)
* TypeScript

#### デバイス
* iOS
* (Android)

### 独自技術
#### ハッカソンで開発した独自機能・技術
* 1万行を超えるJSONの鉄道データから、欲しい形式のデータ(オブジェクト)に変換し、Firestoreに投入する仕組み<br>
[CreateStationsBatch.ts](server/functions/src/batch/CreateStationsBatch.ts)
* スポット取得アルゴリズムは、件数増加の際のスケーラビリティを考慮し、現在地→近くの駅→周辺のスポットという順で取るように<br>
FirestoreはKeyValueのデータベースだが、外部キー的に各spotDocumentがstationDocumentIdを持ち、駅と紐づいている<br>
現在地→近くの駅、スポット→近くの駅は、それぞれユークリッド距離を算出して近いものを選ぶ
[GetSpotsByLocationController.ts](server/functions/src/controller/spot/GetSpotsByLocationController.ts)
