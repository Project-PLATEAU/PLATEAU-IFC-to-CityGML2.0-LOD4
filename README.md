# FMEを用いたIFCからCityGML2.0建築物モデル（LOD4）への変換テンプレート
![image](https://user-images.githubusercontent.com/79615787/227794867-e499045a-9f0d-48e0-aa19-6fdf55d75d49.png)

## 概要

* FMEを用いた「3D都市モデルとの連携のための情報伝達マニュアル（IDM）・モデルビュー定義（MVD）第2版」に準ずるIFCから、PLATEAU 標準のCityGML2.0 建築物モデル（LOD4）へのデータ変換テンプレートです

### 前提ソフトウェア

* 商用ソフトウェア：[FME Desktop](https://www.safe.com/fme/fme-desktop/)
* 動作確認済みのソフトウェアバージョン：ver.2022.1

## 利用方法

* 上記の前提ソフトウェアをインストール
* 本レポジトリの一式をダウンロードし、任意のディレクトリに置く
* FME Workbenchで本ファイルを開いて実行
* 変換元の建築物ファイル(IFC2x3 CV2.0)と各ファイルの読み込み
* ”Run” の実行と保存：詳細の実行手順は Project PLATEAU にて公開されている、[「3D都市モデル整備のためのBIM活用マニュアル（第3.0版）資料1 第5章 5.2」](https://www.mlit.go.jp/plateau/libraries/handbooks/)を参照

## 開発について

* 本変換テンプレートは、2022年度に国土交通省が策定した「3D都市モデル標準製品仕様書 第3.0版」に定義された建築物モデル（LOD4）及び「3D都市モデルとの連携のための情報伝達マニュアル（IDM）・モデルビュー定義（MVD） 第2.0版」に基づき、BIMモデル（IFC2x3 CV2.0)を3D都市モデル（CityGML2.0形式の建築物モデルLOD4）に変換するために開発されました。

## License

* ソースコードおよび関連ドキュメントの著作権は国土交通省に帰属します。
* 本ドキュメントはProject PLATEAUのサイトポリシー（CCBY4.0および政府標準利用規約2.0）に従い提供されています。

## 注意事項

* 本レポジトリは参考資料として提供しているものです。動作保証は行っておりません。
* 予告なく変更・削除する可能性があります。
* 本リポジトリの利用により生じた損失及び損害等について、国土交通省、デジタル庁および著作権者はいかなる責任も負わないものとします。

## 参考資料

* 3D都市モデル整備のためのBIM活用マニュアル（第3.0版）：https://www.mlit.go.jp/plateau/libraries/handbooks/

### IFCクラスと建築物モデル（LOD4）クラスの対応およびLOD4.0-4.2対応表
| データタイプ  | IFCクラス | CityGMLクラス | LOD4.0 | LOD4.1 | LOD4.2 |
| ------------- | ------------- | ------------- | ------------- | ------------- | ------------- |
| プロジェクト情報  | IfcProject  | CityModel | 〇 | 〇 | 〇 |
| 敷地・施設  | IfcSite  | LandUse | 〇 | 〇 | 〇 |
| 建物  | IfcBuilding  | Building | 〇 | 〇 | 〇 |
| 建物階  | IfcBuildingStorey  | CityObjectGroup | 〇 | 〇 | 〇 |
| 部屋・物理的な空間データ  | IfcSpace  | Room | 〇 | 〇 | 〇 |
| 壁（屋内）  | IfcSpace  | InteriorWallSurface | 〇 | 〇 | 〇 |
| 壁（屋外）  | IfcWall・IfcWallStandardCase  | WallSurface | 〇 | 〇 | 〇 |
| 窓  | IfcOpeningElement・IfcWindow  | Window | 〇 | 〇 | 〇 |
| ドア  | IfcOpeningElement・IfcDoor  | Door | 〇 | 〇 | 〇 |
| 床（屋内）  | IfcSpace  | FloorSurface | 〇 | 〇 | 〇 |
| 床（屋外・歩行部） | IfcSlab  | OuterFloorSurface | 〇 | 〇 | 〇 |
| 床（屋外・歩行部以外） | IfcSlab  | BuildingInstallation | 〇 | 〇 | 〇 |
| 屋根（上面） | IfcRoof  | RoofSurface | 〇 | 〇 | 〇 |
| 屋根（上面以外） | IfcRoof  | BuildingInstallation | 〇 | 〇 | 〇 |
| 柱（屋内） | IfcColumn | IntBuildingInstallation |   | 〇 | 〇 |
| 柱（屋外） | IfcColumn | BuildingInstallation | 〇 | 〇 | 〇 |
| カーテンウォール | IfcCurtainWall | WallSurface | 〇 | 〇 | 〇 |
| 天井 | IfcSpace | CeilingSurface | 〇 | 〇 | 〇 |
| パネル（屋内） | IfcPlate | IntBuildingInstallation |   |   | 〇 |
| パネル（屋外） | IfcPlate | BuildingInstallation |   |   | 〇 |
| 手すり（屋内） | IfcRailing | IntBuildingInstallation |   |   | 〇 |
| 手すり（屋外） | IfcRailing | BuildingInstallation |   |   | 〇 |
| スロープ（屋内） | IfcRamp, IfcRampFlight | IntBuildingInstallation |   | 〇 | 〇 |
| スロープ（屋外） | IfcRamp, IfcRampFlight | BuildingInstallation | 〇 | 〇 | 〇 |
| 階段（屋内） | IfcStair, IfcStairFlight | IntBuildingInstallation |   | 〇 | 〇 |
| 階段（屋外） | IfcStair, IfcStairFlight | BuildingInstallation | 〇 | 〇 | 〇 |
| 梁（屋内） | IfcBeam | IntBuildingInstallation |   |   | 〇 |
| 梁（屋外） | IfcBeam | BuildingInstallation |   |   | 〇 |
| その他の建築物要素（屋内） | IfcBuildingElementProxy | IntBuildingInstallation |   | 〇 | 〇 |
| その他の建築物要素（屋外） | IfcBuildingElementProxy | BuildingInstallation | 〇 | 〇 | 〇 |
| EV等輸送設備（屋内） | IfcTransportElement | IntBuildingInstallation	 |   | 〇 | 〇 |
| EV等輸送設備（屋外） | IfcTransportElement | BuildingInstallation | 〇 | 〇 | 〇 |
| 家具等設置物 | IfcFurnishingElement | BuildingFurniture	 |   |   | 〇 |
| 開口要素 | IfcOpeningElement | Window, Door | 〇 | 〇 | 〇 |
| 任意設定空間グループ | IfcZone | CityObjectGroup |   |   | 〇 |
