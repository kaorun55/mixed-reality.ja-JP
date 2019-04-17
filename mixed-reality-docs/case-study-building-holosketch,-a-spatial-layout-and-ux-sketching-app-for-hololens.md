---
title: -ビルド HoloSketch、レイアウト空間および HoloLens 用アプリのスケッチ UX のケース スタディ
description: HoloSketch はデバイス上の空間レイアウトおよび holographic エクスペリエンスの構築に役立つ HoloLens 用ツールのスケッチ UX です。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: アプリのスケッチ HoloSketch、HoloLens、Windows Mixed Reality
ms.openlocfilehash: d7f94a09bf4a8a16000c2345adf1a046dab4bd15
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59600134"
---
# <a name="case-study---building-holosketch-a-spatial-layout-and-ux-sketching-app-for-hololens"></a>-ビルド HoloSketch、レイアウト空間および HoloLens 用アプリのスケッチ UX のケース スタディ

HoloSketch はデバイス上の空間レイアウトおよび holographic エクスペリエンスの構築に役立つ HoloLens 用ツールのスケッチ UX です。 HoloSketch はペアになっている Bluetooth キーボードとマウスだけでなくジェスチャと音声コマンドでは動作します。 HoloSketch では、クイック ビジュアル化およびイテレーションの単純な UX レイアウト ツールを提供します。

![HoloSketch:空間のレイアウトと UX HoloLens 用アプリのスケッチをします。](images/holosketch-image-01-640px.png)<br>
*HoloSketch: 空間的なレイアウトと UX HoloLens 用アプリのスケッチ*

![簡単な視覚エフェクトとイテレーションの単純な UX レイアウト ツールです。](images/holosketch-image-02.png)<br>
*簡単な視覚エフェクトとイテレーションの単純な UX レイアウト ツール*

## <a name="features"></a>機能

### <a name="primitives-for-quick-studies-and-scale-prototyping"></a>クイック スタディとスケール プロトタイプ作成用のプリミティブ

![プリミティブ図形を使用します。](images/holosketch-primitives-giphy.gif)

クイック massing スタディとスケール-プロトタイプの作成には、プリミティブ図形を使用します。

### <a name="import-objects-through-onedrive"></a>OneDrive からオブジェクトのインポート

![オブジェクトのインポート](images/holosketch-importobjects-giphy.gif)

PNG または JPG 画像や FBX の 3D オブジェクトのインポート (Unity でパッケージ化が必要) が OneDrive から複合現実領域。

### <a name="manipulate-objects"></a>オブジェクトを操作します。

![オブジェクトの操作](images/manipulate-objects-640px.jpg)

3D オブジェクトを使い慣れたインターフェイスを持つオブジェクト (移動/回転/スケール) を操作します。

### <a name="bluetooth-mousekeyboard-gestures-and-voice-commands"></a>Bluetooth、マウス/キーボード、ジェスチャと音声コマンド

![Bluetooth をサポートしています](images/supports-bluetooth-640px.jpg)

HoloSketch は、Bluetooth マウス/キーボード、ジェスチャ、音声コマンドをサポートしています。

## <a name="background"></a>背景

### <a name="importance-of-experiencing-your-design-in-the-device"></a>デバイスで、設計が発生していることの重要性

HoloLens のものを設計するときは、デバイスで、設計が発生する必要があります。 複合現実アプリの設計では、最大の課題の 1 つは、従来の 2D スケッチを特にスケール、位置、および、深さの把握が困難であります。

### <a name="cost-of-2d-based-communication"></a>2D のコスト ベースの通信

UX のフローおよび他のユーザー シナリオを効果的に通信するには、デザイナーは、多くの Illustrator、Photoshop、および PowerPoint などの従来の 2D ツールを使用して資産を作成する時間を費やすことになる可能性があります。 これらの 2D デザインは多くの場合に変換する追加の作業を必要と 3D にします。 いくつかのアイデアは、3d 2D から変換時に失われます。

### <a name="complex-deployment-process"></a>複雑な展開プロセス

複合現実は、私たちにとって新しいキャンバスであるために、その性質上のデザインの繰り返しおよび試行錯誤の多くが含まれます。 Unity と Visual Studio などのツールに慣れていないデザイナーの HoloLens のものをまとめる簡単ではありません。 通常は、デバイスでの 2d/3d アートワークを表示するために以下のプロセスを通過する必要があります。 これは、アイデアやシナリオをすばやく反復処理するデザイナーにとって大きな防策です。

![複雑な展開プロセス](images/holosketch-image-03-1000px.png)<br>
*展開プロセス*

### <a name="simplified-process-with-holosketch"></a>HoloSketch を簡略化されたプロセス

HoloSketch での開発ツールとデバイスのポータルのペアを使用することがなく、このプロセスを簡略化する考えました。 OneDrive を使用して、ユーザーに簡単に配置できます 2d/3d 資産 HoloLens にします。

![HoloSketch を簡略化されたプロセス](images/holosketch-image-04-1000px.png)<br>
*HoloSketch を簡略化されたプロセス*

### <a name="encouraging-three-dimensional-design-thinking-and-solutions"></a>3 次元のデザインの考え方とソリューションを促進

このツールでも、デザイナーを本当に 3 次元空間でソリューションを確認して、2 D になっていないことできるようになりますと考えました。 バック グラウンドは Hololens の場合は、現実の世界であるため、UI の 3D のバック グラウンドの作成について考慮する必要はありません。 HoloSketch は、Hololens で 3D のデザインを簡単に探索するデザイナーが開きます。

## <a name="get-started"></a>はじめに

### <a name="how-to-import-2d-images-jpgpng-into-holosketch"></a>HoloSketch に 2 D 画像 (JPG または PNG) をインポートする方法

* OneDrive フォルダー 'ドキュメント/HoloSketch' を JPG または PNG イメージをアップロードします。
* HoloSketch で、[OneDrive] メニューから選択し、環境にイメージを配置することができます。

![2D イメージをインポートします。](images/import-2d-images-1000px.jpg)<br>
*イメージと OneDrive を 3D オブジェクトをインポートします。*

### <a name="how-to-import-3d-objects-into-holosketch"></a>HoloSketch に 3D オブジェクトをインポートする方法

OneDrive フォルダーにアップロードする前に、Unity asset のバンドルにパッケージ化、3 D オブジェクトには、次の手順に従ってください。 このプロセスを使用すると、Maya、シネマ 4 D Microsoft ペイントの 3 D などの 3D のソフトウェアから FBX/OBJ ファイルをインポートできます。

>[!IMPORTANT]
>現時点では、Unity バージョン 5.4.5f1 資産バンドルの作成がサポートされます。

1. ダウンロードして、Unity プロジェクトを開く['AssetBunlder_Unity'](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity)します。 この Unity プロジェクトには、バンドルの資産の生成のためのスクリプトが含まれています。
2. 新しい GameObject を作成します。
3. 内容に基づく GameObject の名前を付けます。
4. Inspector パネルで、コンポーネントの追加 をクリックし、' 足場に Box Collider' を追加します。 

   ![Inspector パネルで、コンポーネントの追加 をクリックし、' 足場に Box Collider' を追加](images/holosketch-10a-assetbundles-1000px.png)
   
   ![Inspector パネルで、コンポーネントの追加 をクリックし、' Box Collider'2 を追加](images/holosketch-10b-assetbundles-1000px.png)

5. [プロジェクト] パネルにドラッグして 3D FBX ファイルをインポートします。
6. 階層のパネルに、オブジェクトをドラッグ**下に新しい GameObject**します。

   ![オブジェクトを階層のパネルに新しい GameObject の下にドラッグします。](images/holosketch-12-assetbundles-1000px.png)

7. オブジェクトが一致しない場合は、collider ディメンションを調整します。 直面するオブジェクトを回転させる**z 軸**します。

   ![オブジェクトが一致しない場合は、コライダーのディメンションを調整します。](images/holosketch-13-assetbundles-1000px.png)

8. プロジェクト パネル、[階層] パネルからオブジェクトをドラッグ**prefab ように**します。
9. Inspector パネルの下部にある、ドロップダウンをクリックします。 作成して新しい一意の名前を割り当てます。 次の例の追加や AssetBundle 名 'brownchair' の割り当てを示しています。 

   ![Inspector パネルの下部にある、ドロップダウン リストをクリックし、新しい一意の名前を割り当てます。](images/holosketch-14-assetbundles-1000px.png)

10. モデル オブジェクトのサムネイル イメージを準備します。 
   ![[プロジェクト] パネルにイメージをドラッグし、オブジェクトに使用される名前を割り当てます。](images/holosketch-15-assetbundles-1000px.png)

11. Unity プロジェクトの '資産' フォルダーの下には、'Assetbundles' という名前のフォルダーを作成します。

12. 資産 メニューからファイルを生成する ' AssetBundles のビルド を選択します。 
   ![[資産] メニューからファイルを生成する ' AssetBundles のビルド] を選択します。](images/holosketch-15a-assetbundles.png)


13. **OneDrive 上の/Files/Documents/HoloSketch フォルダーに生成されたファイルをアップロードします。** Asset_unique_name ファイルのみアップロードします。 マニフェスト ファイルまたは AssetBundles ファイルをアップロードする必要はありません。 <br>
![ファイル/ドキュメント/HoloSketch にファイルを追加/フォルダー](images/holosketch-onedriveupload-1000px.png)
![HoloSketch の OneDrive のメニューに追加された 3D オブジェクトが表示されます](images/holosketch-14-onedriveexample-1000px.jpg)

## <a name="how-to-manipulate-the-objects"></a>オブジェクトを操作する方法

HoloSketch は、3 D のソフトウェアで広く使用されている従来のインターフェイスをサポートします。 Move を使用して、回転、ジェスチャと、マウスを使ってオブジェクトを拡張できます。 音声、キーボードでの異なるモードをすばやく切り替えることができます。

### <a name="object-manipulation-modes"></a>オブジェクトの操作モード

![オブジェクトを操作する方法](images/holosketch-image-06-1000px.png)<br>
*オブジェクトを操作する方法*

### <a name="contextual-and-tool-belt-menus"></a>コンテキストとツール ベルト メニュー

**コンテキスト メニューを使用してください。**

コンテキスト メニューを開き二重のエア タップします。 

メニュー項目。
* **画面のレイアウト:** これは 3D のグリッド システム レイアウトを複数のオブジェクトとそれらのグループとして管理します。 オブジェクトを追加するのにレイアウト画面で二重のエア タップします。
* **プリミティブ。** スタディ massing のキューブ、球体、円柱、および円錐を使用します。
* **OneDrive:** オブジェクトをインポートする [OneDrive] メニューを開きます。
* **ヘルプ：** ヘルプ画面を表示します。

![コンテキスト メニュー](images/holosketch-image-07.png)<br>
*コンテキスト メニュー*

**ツール ベルトのメニューを使用してください。**

移動、回転、スケール、保存、および負荷のシーンはツール ベルトのメニューから利用できます。 

## <a name="using-keyboard-gestures-and-voice-commands"></a>キーボード、ジェスチャ、音声コマンドを使用します。

![キーボード、ジェスチャ、音声コマンド](images/holosketch-image-08-1000px.png)<br>
*キーボード、ジェスチャ、音声コマンド*

## <a name="download-the-app"></a>アプリをダウンロードします。

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="HoloSketch app icon" width="60" height="60" src="images/holosketch-app-icon.png">
</td>
<td style="border-style: none"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">ダウンロードして Microsoft Store から無料 HoloSketch アプリをインストール</a>
</td>
</tr>
</table>

## <a name="known-issues"></a>既知の問題
* 資産のバンドルの作成がサポートされている現在**Unity バージョン 5.4.5f1 します。**
* OneDrive の内容を読み込み中に停止した場合と、OneDrive 内のデータの量、によって、アプリが表示可能性があります。
* 現時点では、保存し、読み込み機能は、プリミティブ オブジェクトのみがサポートされます。
* コンテキスト メニューのテキスト、サウンド、ビデオ、および写真のメニューが無効になっています
* [ツール] メニューの [再生] ボタンは、操作ギズモをクリアします。

## <a name="sharing-your-sketches"></a>スケッチの共有

HoloLens のビデオ記録の機能を使用することを示す ' Hey Cortana、開始/停止の記録 '。 ボリューム上/下、スケッチの画像を撮影してキーを押します。

## <a name="about-the-authors"></a>著者について

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>ドン Yoon Park</b><br>UX デザイナー @Microsoft</td>
</tr>
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Patrick Sebring" width="60" height="60" src="images/paseb-60px.jpg"></td>
<td style="border-style: none"><b>Patrick Sebring</b><br>開発者向け @Microsoft</td>
</tr>
</table> 
