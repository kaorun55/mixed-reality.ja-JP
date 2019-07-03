# <a name="getting-unity-ready-for-development"></a>Unity の開発の準備 

このチュートリアルでは、準備し、Mixed Reality ツールキットをインポート、ビルドの設定を構成して、シーンの準備など、アプリケーション開発の Unity を構成する方法について説明します。

目標:

- アプリケーション開発のための Unity を構成します。

- Mixed Reality ツールキットをインポートする

- プロジェクト シーンを準備します。

### <a name="instructions"></a>手順

1. ダウンロードし、クリックして、Mixed Reality Toolkit unity パッケージを保存[ここです。](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2.1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.1.unitypackage)
2. Unity では、[アセット] メニューをクリックし、パッケージのインポートしてカスタム パッケージをクリックします。

![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. 手順 1. で指定されたリンクからダウンロードした Unity パッケージを選択します。 Unity にインポートのポップアップ ウィンドウが表示されると、インポートを開始する [インポート] ボタンをクリックします。 MRTK をインポートするには数分かかる場合があります。

![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

> 注:ダウンロードしたパッケージは、ファイルを保存したローカル フォルダーには。 上の図は、パッケージをどこを提示していません。

4. 新しいシーンを作成します。 %T この行うファイルをクリックすると、新しいシーンを選択して")。 HLSharedProjectMain としてシーンを保存します。

> 注: 次の図のようなポップアップが表示される可能性があります。 ここでは、次のようにクリックします。 いいえ。
>
> ![Module3Chapter2note1im](images/module3chapter2note1im.PNG)

5. 混合の現実 Toolkit では、シーンおよび構成する追加をクリックします。

![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. 完了すると、新しい構成ファイルが表示され、プロファイルをカスタマイズするかを選択します。 [コピー] をクリックし、カスタマイズします。

   ![Module3Chapter2step6ima](images/module3chapter2step6ima.PNG)

   ![Module3Chapter2step6imb](images/module3chapter2step6imb.PNG)

   ![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

7. 下へスクロールし、[診断] ウィンドウを非表示にする場合は、Siagnostics を有効にするシステムをオフにします。 パフォーマンスを監視するアプリケーション開発時に有効になっており、運用環境やアプリケーションのデモンストレーションの中に無効にすると、診断ウィンドウを維持することをお勧めします。 

   ![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

8. -> Build Settings をコントロール + shift + B を押すか、ファイルをビルド設定の開いています。 プログラムが、PC、Mac、Linux のスタンドアロン プラットフォームで現在設定されていることを確認します。 HoloLens 2 の開発用ユニバーサル Windows プラットフォームにするプラットフォームを設定します。 選択し、[Switch Platform] をクリックします。![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

9. 完了すると、開いているシーンを追加することを示すボックスをクリックします。 今すぐ、[Inspector] パネルに移動し、仮想現実ようサポートされてください (下図) の右側にチェック ボックスがオンになっていることを確認します。 また、シーン/HLSharedProjectMain 横のチェック ボックスは、次の図に示すようにチェックも確認します。![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

10. Inspector パネルの 発行の設定 セクションでは、機能、までスクロールし、次のチェック ボックスがマークされていることを確認します。![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

11. ダウンロードできる SharingAssetCollection と呼ばれるカスタム パッケージをインポート[ここ](https://github.com/microsoft/MixedRealityLearning/releases/download/Sharing_2/SharingAssetCollection.unitypackage)。![Module3Chapter2step12im](images/module3chapter2step11im.PNG)

12. プロジェクト パネル Prefabs フォルダーに移動します。 次の手順では、シーンにいくつかのプレハブを実装します。 Prefabs フォルダー をクリックし、プレハブは、階層にデバッグ ウィンドウをドラッグします。 完了すると、clckin ファイルで、プロジェクトを保存し、保存またはコントロール + S キーを押します。

    ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

   > 注:TMP Essentials について質問する、プレハブをクリックすると表示されるポップアップ ウィンドウがあります。 必要に応じて、インポート TMP Essentials をクリックします。 このポップアップが表示されている場合は、階層からプレハブを削除し再潜在的なテキストに関連するエラーを回避するために、階層にドラッグする必要があります。
   >
   > ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)


## <a name="congratulations"></a>結論

Unity プロジェクトは、Photon の準備ができました。 今後のチュートリアルでは、このシーンと共有のエクスペリエンスを完全に Unity プロジェクトをビルドします。

[次のチュートリアル:複数のユーザーを接続します。](mrlearning-sharing(photon)-ch3.md)

