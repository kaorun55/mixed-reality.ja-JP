---
title: Unity と Visual Studio を使用するためのベスト プラクティス
description: ヒントし、テクニックを Unity と Visual Studio での複合現実のアプリケーションの作成のワークフローを効率化します。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 展開、unity、visual studio、HoloLens、イマーシブ ヘッドセット
ms.openlocfilehash: 80a533851b3bee0d747a90dfececbaa558c4ec1f
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604106"
---
# <a name="best-practices-for-working-with-unity-and-visual-studio"></a>Unity と Visual Studio を使用するためのベスト プラクティス

Unity を使用した複合現実のアプリケーションを作成する開発者は、HoloLens や、イマーシブ ヘッドセットに展開されているアプリケーション パッケージを作成するには、Unity と Visual Studio の間で切り替える必要があります。 既定で Visual Studio の 2 つのインスタンスは必要な (Unity のスクリプトを変更するもの) とデバッグとデバイスに展開する 1 つを使用します。 次の手順により、1 つの Visual Studio インスタンスを使用して開発するには、Unity プロジェクトでは、エクスポートの頻度が削減され、デバッグ エクスペリエンスが向上します。

## <a name="improving-iteration-time"></a>イテレーションの時間を改善

Unity と Visual Studio を使用する場合は、一般的なワークフロー問題には、複数の windows の Visual Studio の開いていると継続的に反復処理するには、Visual Studio と Unity の間で切り替える必要が発生しました。
1. **Unity** - シーンを変更すると、Visual Studio ソリューションをエクスポートします。
2. **Visual Studio (1)** - スクリプトを変更します。
3. **Visual Studio (2)** - ビルドと展開、Unity は、デバイスに Visual Studio ソリューションをエクスポートするために

さいわい、Visual Studio の単一のインスタンスを効率化し、Unity から頻繁にエクスポートを削減する方法があります。

ときに[Unity からプロジェクトをエクスポートする](exporting-and-building-a-unity-visual-studio-solution.md)、確認、 **UnityC#プロジェクト**"ファイル > のビルド設定 メニューのチェック ボックスをオンします。 ここで、Unity からエクスポートしたプロジェクトを含むすべてのプロジェクトのC#スクリプトし、いくつかの利点があります。
* Visual Studio の同じインスタンスを使用して、スクリプトを記述すると、プロジェクトのビルド/展開
* シーンが Unity エディターで変更されたときにのみ、Unity からのエクスポートします。再度エクスポートすることがなく、Visual Studio でしてスクリプトの内容の変更を実行することができます。

**UnityC#プロジェクト**有効にすると、各プログラムの 1 つだけのインスタンスを開く必要があります。
1. **Unity** - シーンを変更すると、Visual Studio ソリューションをエクスポートします。
2. **Visual Studio** - ビルドと展開、Unity は、デバイスに Visual Studio ソリューションをエクスポートし、スクリプトを変更します。

## <a name="visual-studio-tools-for-unity"></a>Visual Studio Tools for Unity

ダウンロード[Visual Studio Tools for Unity](https://visualstudiogallery.msdn.microsoft.com/8d26236e-4a64-4d64-8486-7df95156aba9)

**Visual Studio Tools for Unity の利点があります。**
* Visual Studio から Unity エディターでの再生モードは、変数や複雑な式を評価するブレークポイントを配置することでデバッグします。
* Unity プロジェクト エクスプ ローラーを使用すると、Unity を表示する正確な同じ階層に、スクリプトを検索できます。
* Visual Studio 内から直接、Unity コンソールを取得します。
* ウィザードを使用して、迅速に作成またはスクリプトに移動します。

## <a name="expose-c-class-variables-for-easy-tuning"></a>公開C#容易なチューニング用の変数をクラス

クラスの変数を公開する 2 つの方法はあります。 推奨される方法では、プライベート変数を [SerializeField] 属性を追加します。 これにより、エディターからのアクセスがないプログラムで公開することができます。  その他のオプションはさせるC#クラス変数を public エディター UI で公開します。 

両方のアプローチを使用すれば、エディターでの再生中に変数を簡単に調整できます。 これは、チューニング操作メカニック プロパティに特に便利です。

## <a name="regenerate-uwp-visual-studio-solutions-after-windows-sdk-or-unity-upgrade"></a>Windows SDK または Unity のアップグレード後は、UWP の Visual Studio ソリューションを再生成します。

UWP の Visual Studio ソリューションをソース管理にチェックインは、新しい Windows SDK または Unity エンジンへのアップグレード後に古いで取得できます。 アップグレード後、Unity から新しい UWP ソリューションを構築し、チェックイン済みのソリューションに相違点をマージして、これを解決できます。

## <a name="use-text-format-assets-for-easy-comparison-of-content-changes"></a>変更内容を比較しやすいテキスト形式の資産を使用します。

テキスト形式でアセットを格納すると、Visual Studio での差分をコンテンツの変更を確認しやすきます。 有効にするこの「> プロジェクトの設定 > エディターの編集」に変更する**資産のシリアル化**モード**Force テキスト**します。 ただし、資産ファイルのテキストの変更をマージすることはエラーを起こしやすいし、ソース管理システムで排他的バイナリ チェック アウトを有効にするを検討、推奨されませんのでします。
