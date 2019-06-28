**Unity の開発の準備** 

このレッスンでは、Mixed Reality ツールキットをインポート、ビルドの設定を構成して、シーンの準備を含む、アプリ開発用の Unity の構成を準備の方法について説明します。

目標:

- アプリ開発用の Unity を構成します。

- Mixed Reality ツールキットをインポートする

- プロジェクト シーンを準備します。

### <a name="instructions"></a>手順

1. ダウンロードし、クリックして、Mixed Reality Toolkit unity パッケージを保存[ここです。](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2.1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.1.unitypackage)
2. Unity では、[資産] メニューをクリックし、パッケージのインポート"、"を選択し、「カスタム パッケージです」をクリックしてください

![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. 手順 1. で指定されたリンクからダウンロードした Unity パッケージを選択します。 Unity にインポートのポップアップ ウィンドウが表示されると、インポートを開始する [インポート] ボタンをクリックします。 MRTK をインポートするには数分かかる場合があります。

![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

> 注:ダウンロードしたパッケージは、ファイルを保存したローカル フォルダーになります。 上の図は、パッケージをどこを提示していません。

4. (これを行う"file"をクリックし、「新しいシーン」を選択)、新しいシーンを作成します。 シーンを付けて保存"HLSharedProjectMain"

> 注: 次の図のようなポップアップが表示される可能性があります。 ここでは、クリックするだけ「いいえ」
>
> ![Module3Chapter2note1im](images/module3chapter2note1im.PNG)

5. "Mixed Reality Toolkit"クリック「シーンに追加して構成します」

![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. 完了すると、新しい構成ファイルが表示され選択してプロファイルをカスタマイズすること。 「コピーし、カスタマイズ」をクリックします。

   ![Module3Chapter2step6ima](images/module3chapter2step6ima.PNG)

   ![Module3Chapter2step6imb](images/module3chapter2step6imb.PNG)

   ![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

7. 下へスクロールし、「有効化」診断システムに診断ウィンドウを非表示にする場合をオフにします。 パフォーマンスを監視するアプリの開発時に有効になっており、運用環境やアプリケーションのデモンストレーションの中に無効にすると、診断ウィンドウを維持することをお勧めします。 

   ![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

8. ビルドの設定コントロール + shift + B を押すか、ファイルを開く > ビルドの設定。 プログラムが「PC、Mac、Linux のスタンドアロン」プラットフォームで現在設定されていることを確認します。 「ユニバーサル Windows プラットフォーム」を使用するプラットフォームを設定すると、HoloLens 2 開発用 選択して、「プラットフォームの切り替え」をクリックします。![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

9. 完了すると、「開いているシーンを追加します。」と書かれたボックスをクリックします。 Inspector パネルに移動し、(下図参照) として「サポートされている仮想現実」の右側にあるチェック ボックスを確認するようになりましたがチェックされます。 また、"シーン/HLSharedProjectMain"の横にあるチェック ボックスがオンも次の図に示すように。![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

10. "発行の設定 の下で「機能」までインスペクター パネル スクロール セクションし、次のチェック ボックスがマークされていることを確認します。![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

11. ダウンロードできる"SharingAssetCollection"と呼ばれるカスタム パッケージをインポート[ここ](https://github.com/microsoft/MixedRealityLearning/releases/download/Sharing_2/SharingAssetCollection.unitypackage)。![Module3Chapter2step12im](images/module3chapter2step11im.PNG)

12. ここで、プロジェクト パネルで、フォルダーに移動「プレハブ」、いくつかのプレハブをシーンに次の手順で実装されるためです。 「プレハブ」フォルダーにをクリックし、"DebugWindow"階層に、プレハブをドラッグします。 完了すると、プロジェクトを保存 (ファイル、 をクリックし、保存、またはコントロール + S キーを押します)

    ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

   > 注:TMP Essentials について質問する、プレハブをクリックすると表示されるポップアップ ウィンドウがあります。 これらが必要になります"インポート TMP Essentials をクリックします。 このポップアップが表示されている場合は、階層からプレハブを削除し再潜在的なテキストに関連するエラーを回避するために、階層にドラッグする必要があります。
   >
   > ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)


## <a name="congratulations"></a>結論

Unity プロジェクトは Photon 準備ができました! 今後のレッスンでは、このシーンと共有のエクスペリエンスを完全に Unity プロジェクトをビルドします。

[次のレッスン:Sharing(Photon) レッスン 3](mrlearning-sharing(photon)-ch3.md)

