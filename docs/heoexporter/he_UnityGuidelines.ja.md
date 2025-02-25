## まえおき
VketCloudで使用するワールドモデル等はUnityでセットアップをおこない、専用エクスポータ（HEOExporter）で出力をおこないます。ただし、Unityの機能がすべて使用できるわけではないため、後述する仕様に合わせて調整をおこなう必要があります

## ポリゴン
ワールドモデルは８０万トライアングル以下

## テクスチャ
* 大きさが2048x2048以下のPNG
* ２の累乗サイズの正方形（2048x2048,1024x1024,512x512等）または2の累乗サイズの長方形
* ビット深度は24bitまたは32bit
* png換算で80MB以下
* 拡張子は小文字(.png)にする。”.PNG”になっているとサーバーアップでエラーが出ます

## テクスチャ圧縮
VketCloudでは軽量化の方法の一つとしてテクスチャを圧縮するようにしています。詳しくは [こちら](he_TextureCompression.md)をご覧ください。

## リフレクションプローブ
VketCloudではUnityのリフレクションプローブを使用することができます。詳しくは[こちら](he_ReflectionProbe.md)をご覧ください。

## ライトマップ
* Android(dLDRフォーマット) または PC(RGBMフォーマット)  プラットフォームに切り替える
* Other SettingsのLightMap EncodingがAndroidプラットフォームの場合『Low Quality』、PCプラットフォームの場合『Normal Quality』になっているか確認する
    * LightMap  Encodingが間違っている場合、ライトマップが白飛びすることがあるので注意してください
    * リアルタイムのグローバルイルミネーションはサポートしていないので、ライトマップで表現してください(UnityとVketCloudで見た目が違う場合、ほとんどはGI周りが原因だと思います)
* Other Settings の Color Spaceが『Linear』になっているか確認する
<img src="he_image/スクリーンショット 2022-05-27 193242.png">
* Max Lightmap Sizeは2048以下にする
* ライトマップの圧縮は無効にする
* Format: RGB24またはRGBA32、Compressed: Noneになっているか確認する
<img src="he_image/スクリーンショット 2021-06-16 105720.png">

## シェーダー
* Standard 
* Autodesk Interactive　
    * Autodesk Interactiveのメタリックテクスチャはテクスチャスロット数の都合上、書き出していないので、メタリックテクスチャとラフネステクスチャを組み合わせて使用する場合は、Standard Shaderを使用してください。
* Unlit
* UnlitWF（両面表示等のみ対応）

## コライダー
* 衝突判定用はBoxColliderとMeshColliderのみ対応。MeshColliderは処理に非常に負荷がかかるため使用は必要最低限にしてください。BoxColliderはTPSモード時にプレイヤーアバターとカメラの間に位置するオブジェクトによって遮断されるのを防ぐためにも利用しているため、天井など移動出来ない場所でも設定して下さい。MeshColliderの書き出し方法については[こちら](he_MeshCollider.md)をご覧ください。
* SphereColliderはクリック（タップ）判定用にのみ使用しています。（ポスターなど）
* ヒエラルキーのネストが深いとコライダーが出力されない場合があります。
* 膝下ぐらいのコライダーは登れてしまいます。かといって大きすぎるコライダーはカメラの妨げになるので、気を付けてください。
* 必ずMeshRendererを非表示にしてください。Materialsのsizeを０にして非表示にすると、出力エラーとなります。

## スカイボックス
* スカイボックスは非対応です。使わないもしくは天球などでごまかす必要があります。

## スケール
* マイナススケールは無視されます。裏返しにする場合は、180度回転させてください。

## オブジェクト
HEOExportを行う時に１つのオブジェクトを選択してExportを行う為、全てのオブジェクトがまとまった親オブジェクトを必ず作るようにしてください。

<div> 
    <div>
        <img src="he_image/image-20211220-133702.png">
        <p>上記のように一つにまとまっていればOK</p>
    </div>
    <div>
        <img src="he_image/image-20211220-133737.png">
        <p>親オブジェクトが２つ以上ある場合は、まとめる必要がある。</p>
    </div>
</div>