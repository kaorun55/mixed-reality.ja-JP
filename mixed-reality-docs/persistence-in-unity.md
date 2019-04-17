---
title: Unity で永続化
description: 永続化には、ユーザー、および後で使用、アプリの多くで期待される場所を探してな場所は、個々 のホログラムまたはワークスペースをピン留めことができます。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens、Unity の永続化
ms.openlocfilehash: b6a67e52b3a5ce724a90eb1a479c5eda74b0c4cb
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605078"
---
# <a name="persistence-in-unity"></a>Unity で永続化

**名前空間:***UnityEngine.XR.WSA.Persistence*<br>
**クラス:***WorldAnchorStore*

WorldAnchorStore は、アプリケーションのインスタンス間で特定の実際の位置にホログラムまま、holographic エクスペリエンスを作成するキーです。 これにより、ユーザーは個々 のホログラムまたはワークスペースを固定後は、し、検索後で、アプリのさまざまな用途で期待される場所。

## <a name="how-to-persist-holograms-across-sessions"></a>ホログラムをセッション間で永続化する方法

WorldAnchorStore はセッション間での WorldAnchor の場所を保持できます。 セッション間で保持ホログラムが実際には個別に追跡する特定の世界のアンカーを使用する、Gameobject 必要があります。 多くの場合、理にかなって world アンカーを持つ GameObject ルートを作成し、子を持つローカルの位置のオフセットによってホログラムが固定されています。

前のセッションからホログラムを読み込めません。
1. WorldAnchorStore を取得します。
2. 世界のアンカーの id を提供する世界アンカーに関連するアプリ データの読み込み
3. その id から世界アンカーを読み込む

今後のセッション ホログラムを保存します。
1. WorldAnchorStore を取得します。
2. Id を指定する世界アンカーを保存します。
3. Id と共に世界アンカーに関連するアプリのデータを保存します。

### <a name="getting-the-worldanchorstore"></a>WorldAnchorStore を取得します。

操作を実行すると移動する準備ができましたがわかるように、周り WorldAnchorStore への参照を保持します。 呼び出すしたいので、これは、非同期呼び出し、可能性のある開始とすぐ、

```
WorldAnchorStore.GetAsync(StoreLoaded);
```

StoreLoaded は、ここで、WorldAnchorStore の読み込みが完了すると、ハンドラーを示します。

```
private void StoreLoaded(WorldAnchorStore store)
{
       this.store = store;
}
```

保存および特定の世界のアンカーの読み込みに使用する WorldAnchorStore への参照があるようになりました。

### <a name="saving-a-worldanchor"></a>WorldAnchor を保存しています

を保存するには、だけに保存していること確認し、保存する場合、選択する前に先ほど WorldAnchor で渡しますの名前を付ける必要があります。 注: (ストアが失敗は、同じ文字列に 2 つのアンカーを保存しようとしています。保存は false を返します)。 新しいものを保存する前に、前の保存を削除する必要があります。

```
private void SaveGame()
{
       // Save data about holograms positioned by this world anchor
       if (!this.savedRoot) // Only Save the root once
       {
              this.savedRoot = this.store.Save("rootGameObject", anchor);
              Assert(this.savedRoot);
       }
}
```

### <a name="loading-a-worldanchor"></a>WorldAnchor の読み込み

読み込めません。

```
private void LoadGame()
{
       // Save data about holograms positioned by this world anchor
       this.savedRoot = this.store.Load("rootGameObject", rootGameObject);
       if (!this.savedRoot)
       {
              // We didn't actually have the game root saved! We have to re-place our objects or start over
       }
}
```

さらにストアを使用できます。以前保存したアンカーを削除する Delete() とストア。Clear() 以前に保存したすべてのデータを削除します。

### <a name="enumerating-existing-anchors"></a>既存のアンカーを列挙します。

以前に保存されたアンカーを検出するには、GetAllIds を呼び出します。

```
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
        Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a>複数のデバイスの永続化するホログラム

使用することができます<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間アンカー</a>をローカル WorldAnchor、それらのデバイスが同じ一緒に存在しない場合でも、アプリが複数の HoloLens、iOS、Android デバイス間で検索しできますから永続的なクラウド アンカーを作成するには時間です。  クラウド アンカーが永続的なので、時間の経過と共に複数のデバイスできます各を参照してください同じ物理的な場所でそのアンカーに対して相対的にレンダリングされたコンテンツ。

5 分間試して、Unity での共有エクスペリエンスの構築を開始、<a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">空間アンカー Unity の Azure クイック スタート</a>します。

空間のアンカーを Azure で稼働しているを開発したとして、<a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">を作成し、Unity 内でアンカーを検索</a>します。

## <a name="see-also"></a>関連項目
* [空間アンカーの永続化](coordinate-systems.md#spatial-anchor-persistence)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure の空間アンカー</a>
* <a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure 空間アンカー Unity 用の SDK</a>
