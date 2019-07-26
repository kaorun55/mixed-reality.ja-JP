# <a name="2-getting-unity-ready-for-development"></a>2. Unity を開発用に準備する 


このチュートリアルでは、Mixed Reality Toolkit のインポート、ビルド設定の構成、シーンの準備など、アプリケーション開発のために Unity を準備して構成する方法について説明します。

事項

- アプリケーション開発のための Unity の構成

- Mixed Reality ツールキットをインポートする

- プロジェクトシーンを準備する

## <a name="instructions"></a>手順

1. ここをクリックして、Mixed Reality Toolkit unity パッケージをダウンロードして保存し[ます。](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2.1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.1.unitypackage)

2. Unity で、[アセット] メニューをクリックし、[パッケージのインポート] をクリックして、[カスタムパッケージ] をクリックします。

![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. 手順 1. で指定したリンクからダウンロードした Unity パッケージを選択します。 [インポート] ポップアップウィンドウが Unity に表示されたら、[インポート] ボタンをクリックしてインポートを開始します。 MRTK のインポートには数分かかる場合があります。

![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

> 注:ダウンロードしたパッケージは、ファイルを保存したローカルフォルダーにあります。 上の図では、パッケージを検索する場所はされるません。

4. 新しいシーンを作成します。 これを行うには、[ファイル] をクリックし、[新しいシーン] を選択します)。 シーンを HLSharedProjectMain として保存します。

> 注: 次の図のようなポップアップが表示される場合があります。 ここでは、[いいえ] をクリックします。
>
> ![Module3Chapter2note1im](images/module3chapter2note1im.PNG)

5. Mixed Reality Toolkit の [シーンに追加] をクリックし、[構成] をクリックします。

![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. この処理が完了すると、新しい構成ファイルが表示され、プロファイルをカスタマイズすることができます。 [コピーとカスタマイズ] をクリックします。

![Module3Chapter2step6ima](images/module3chapter2step6ima.PNG)

![Module3Chapter2step6imb](images/module3chapter2step6imb.PNG)

![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

7. [診断] ウィンドウを非表示にする場合は、下にスクロールし、[診断システムを有効にする] チェックボックスをオフにします。 アプリケーションの開発中に、パフォーマンスを監視し、運用またはアプリケーションのデモンストレーション中に無効にすることをお勧めします。 

![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

8. Ctrl + shift + B キーを押すか、[ファイル > ビルド設定] に移動して、ビルド設定を開きます。 プログラムは、現在 PC、Mac、および Linux スタンドアロンプラットフォームで設定されていることに注意してください。 HoloLens 2 開発の場合は、プラットフォームをユニバーサル Windows プラットフォームに設定します。 それを選択し、[プラットフォームの切り替え] をクリックします。

![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

9. 完了したら、[Open シーンの追加] というボックスをクリックします。 次に、[インスペクター] パネルにアクセスし、[サポートされている仮想現実 (下の図を参照)] の右側にあるチェックボックスがオンになっていることを確認します。 また、次の図に示すように、[シーン/HLSharedProjectMain] の横のチェックボックスもオンになっていることを確認します。

![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

10. [インスペクター] パネルの [発行の設定] セクションで、[機能] まで下にスクロールし、次のチェックボックスがオンになっていることを確認します。

![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

11. ここでダウンロードできる SharingAssetCollection というカスタムパッケージをインポートし[ます。](https://github.com/microsoft/MixedRealityLearning/releases/tag/development)

![Module3Chapter2step12im](images/module3chapter2step11im.PNG)

12. [プロジェクト] パネルで、Prefabs フォルダーにアクセスします。 次のいくつかの手順では、いくつかの prefabs をシーンに実装します。 Prefabs フォルダーで、[prefab]、[デバッグ] ウィンドウをクリックし、階層にドラッグします。 完了したら、[ファイル] をクリックし、[保存] をクリックしてプロジェクトを保存するか、ctrl + S キーを押します。

![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

   > 注:Prefab をクリックするとポップアップが表示され、TMP Essentials について質問されることがあります。 必要に応じて、[TMP Essentials のインポート] をクリックします。 このポップアップが表示された場合は、テキスト関連のエラーが発生しないように、階層から prefab を削除し、階層に再ドラッグする必要がある場合があります。
   >
>![Module3Chapter2note2im](images/module3chapter2note2im.PNG)


## <a name="congratulations"></a>結論

Unity プロジェクトは Photon の準備ができました。 今後のチュートリアルでは、このシーンと Unity プロジェクトを完全な共有エクスペリエンスに向けて構築します。

[次のチュートリアル:3.複数ユーザーの接続](mrlearning-sharing(photon)-ch3.md)

