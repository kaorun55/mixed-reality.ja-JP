## <a name="lesson-2"></a><span data-ttu-id="4287b-101">レッスン 2</span><span class="sxs-lookup"><span data-stu-id="4287b-101">Lesson 2</span></span>

<span data-ttu-id="4287b-102">レッスン 2 で Azure サービスに接続できませんおよびはときに、ローカルの音声からテキストへの変換を実行できるオフラインのモードは追加*シミュレート*切断状態。</span><span class="sxs-lookup"><span data-stu-id="4287b-102">In Lesson 2, we will add an Offline mode that will allow us to perform local speech-to-text translation when we are unable to connect to the Azure service and we will *simulate* a disconnected state.</span></span>

1. <span data-ttu-id="4287b-103">階層で"Lunarcom_Base"オブジェクトを選択し、inspector パネルで"コンポーネントの追加 をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4287b-103">Select the "Lunarcom_Base" object in the hierarchy and click “Add Component” in the inspector panel.</span></span> <span data-ttu-id="4287b-104">検索して選択「Lunarcom オフライン Recognition」。</span><span class="sxs-lookup"><span data-stu-id="4287b-104">Search for and select the "Lunarcom Offline Recognition."</span></span>

![Module4Chapter2step1im](images/module4chapter2step1im.PNG)



2. <span data-ttu-id="4287b-106">"LunarcomOfflineRecognizer"で、ドロップダウン リストをクリックし、「有効です。」を選択します。</span><span class="sxs-lookup"><span data-stu-id="4287b-106">Click the dropdown in the “LunarcomOfflineRecognizer” and select “Enabled.”</span></span> <span data-ttu-id="4287b-107">ユーザーが持っていない接続のように機能プロジェクトをこのプログラムはします。</span><span class="sxs-lookup"><span data-stu-id="4287b-107">This will program the project to act like the user doesn't have connection.</span></span> 

![Module4Chapter2step1im](images/module4chapter2step2im.PNG)

3. <span data-ttu-id="4287b-109">ここで、キーを押して、Unity エディターで再生して、テストします。</span><span class="sxs-lookup"><span data-stu-id="4287b-109">Now, press play on the Unity Editor and test it.</span></span> <span data-ttu-id="4287b-110">シーンの左下隅で、マイクを押し、読み上げを開始します。</span><span class="sxs-lookup"><span data-stu-id="4287b-110">Press the microphone in the bottom left hand corner in the scene and begin speaking.</span></span> 

> <span data-ttu-id="4287b-111">注: オフラインだから、Word のスリープ解除機能が無効です。</span><span class="sxs-lookup"><span data-stu-id="4287b-111">note: because we’re offline, the Wake Word functionality has been disabled.</span></span> <span data-ttu-id="4287b-112">音声認識される必要があるたびに、マイクを物理的にをクリックする必要がそのため、中にオフラインです。</span><span class="sxs-lookup"><span data-stu-id="4287b-112">So, you will have to physically click the microphone every time you wish to have your speech recognized while offline.</span></span> 

<span data-ttu-id="4287b-113">シーンでしたの外観の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="4287b-113">Below is an example of what your scene could look like:</span></span>

![Module4Chapter2exampleim](images/module4chapter2exampleim.PNG)

## <a name="congratulations"></a><span data-ttu-id="4287b-115">結論</span><span class="sxs-lookup"><span data-stu-id="4287b-115">Congratulations</span></span>

<span data-ttu-id="4287b-116">オフライン モードを有効になっています。</span><span class="sxs-lookup"><span data-stu-id="4287b-116">The offline mode has been enabled!</span></span> <span data-ttu-id="4287b-117">ここでのすべてのインターネットから離れている、ときにまだで作業できます Speech SDK を使用してプロジェクト!</span><span class="sxs-lookup"><span data-stu-id="4287b-117">Now when you're away from any form of internet, you can still work on your project with Speech-SDK!</span></span> 

[<span data-ttu-id="4287b-118">次のレッスン:SpeechSDK レッスン 3</span><span class="sxs-lookup"><span data-stu-id="4287b-118">Next Lesson: SpeechSDK Lesson 3</span></span>](link placeholder)

