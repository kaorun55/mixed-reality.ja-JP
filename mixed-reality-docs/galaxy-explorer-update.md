# <a name="the-making-of-galaxy-explorer-for-hololens-2"></a>HoloLens 2 用 Galaxy エクスプローラーの作成

HoloLens 2 の Galaxy エクスプローラーの更新方法について説明します。 [Galaxy エクスプローラー](https://docs.microsoft.com/windows/mixed-reality/galaxy-explorer "Galaxy エクスプローラー")は、当初、アイデアプログラムを共有することによって HoloLens 用のオープンソースアプリケーションとして開発されており、多くの人が経験した最初の mixed reality の1つです。 ここでは、 [HoloLens 2 の新機能と魅力的な機能](https://www.microsoft.com/hololens/hardware)を更新します。

Microsoft Mixed Reality スタジオ (1) の1つとして、通常、商用レベルのソリューションを開発し、クリエイティブおよび開発プロセスを通じて対象プラットフォームで & テストを開発しています。 私たちは、まだ HoloLens 2 デバイスにアクセスできないが、Galaxy エクスプローラーの更新プログラムを開始したいという、固有の状況になっています。 私たちは、フレームワークとツール ( [Mrtk v2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)など) を使用してこのプロジェクトを着手しています。これは、microsoft とコミュニティで利用できるようになったためです。

元の Galaxy エクスプローラーと同じように、コミュニティにフルアクセスがあることを確認するために、 [GitHub でプロジェクトのソーシングを開始](https://github.com/Microsoft/GalaxyExplorer)します。 ここでは、MRTK v1 から MRTK v2 への行い移植方法、HoloLens 2 で利用可能な新機能に基づいてエクスペリエンスがどのように強化されたか、および Galaxy エクスプローラーが次のようになっていることを確認する方法について、完全な透明性についても説明します。マルチプラットフォームエクスペリエンス。 これにより、HoloLens (第1世代)、HoloLens 2、Windows Mixed Reality ヘッドセット、または Windows 10 デスクトップ上で Galaxy エクスプローラーを表示している場合でも、イマーシブエクスペリエンスを使用していることを確認し、その過程を十分に体験したいと考えています。

このページは、プロジェクトの進行に合わせて拡張され、さらに詳細な記事、コード、デザイン artefacts、追加の MRTK v2 ドキュメントなどにリンクします。これにより、insider がプロジェクトを確認できるようになります。



(1) 米国、ヨーロッパ、およびアジア太平洋に配置されている Microsoft Mixed Reality Studio チームは、ユーザーエクスペリエンス設計、holographic computing、AR/VR テクノロジ、3D 開発の専門家です。3D アセットの作成、DirectX、Unity、Unreal など。 お客様が組織全体に大きな影響を与えることを可能にすると同時に、必要なフューチャの計画、設計、構築、および提供を支援します。 スタジオは、エンタープライズアプリケーションの統合、導入、運用、およびサポートのために、22000を超える Microsoft サービスプロフェッショナルと密接に連携しています。
