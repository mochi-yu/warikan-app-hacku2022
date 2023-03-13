# orc取扱説明書

カメラからのレスポンスのサンプルは下にあります


## itemクラス
## フィールド
- name: String
- price: int
- `toString`は`override`してあるのでprintで表示できます。

# receiptクラス
## コンストラクタ
- カメラのレスポンスを引数にインスタンスを生成します。
インスタンス生成時に自動で商品と値段を抽出し、フィールドに保存します。
    ```dart
    Receipt data = Receipt(cameraRspons);
    ```
## getInfo
- getInfoメソッド
`List<item>`型の商品画像の一覧が得られます。
    ```
    print(data.getInfo());
    // [{name:  ポン・デ・リング, price: 302}, {name:  ゴールデンチョコレート, price: 162}, {name:  桜もちっとドーナツ つぼみ, price: 151}]
    ```



# サンプル
```
Future<void> ocrSample() async {
  const platform = MethodChannel('warikan.flutter.dev/main');

  try {
    final String platformRes = await platform.invokeMethod('OCR');
    if(platformRes == 'cancel'){
      // 撮影がキャンセルされた時の処理
      
    }else{
      // 撮影が完了した時の処理

      print(platformRes);

      // インスタンス化
      Receipt data = Receipt(platformRes);
      print(data.getInfo());
     
    }
  } on PlatformException catch (e) {
    // swift/java から例外がスローされた場合
    print("${e.message}");
  }
  
}
```

`onPressed`属性に指定したりしてお使いください
```
onPressed: ocrSample
```


## カメラのレスポンスのサンプル
```
[{"minX":0.4079422407119204,"maxX":0.7725631763570083,"minY":0.08278795811518325,"maxY":0.11337208373384322,"text":"Wister"},{"minX":0.41122464481316484,"maxX":0.769280772255764,"minY":0.114160587650319,"maxY":0.14456032957706155,"text":"Dorut"},{"minX":0.2924187750303784,"maxX":0.6678700276228815,"minY":0.16424416746768655,"maxY":0.18895347954715114,"text":"No. 1238"},{"minX":0.151274044272954,"maxX":0.8378956449924929,"minY":0.1809116782942367,"maxY":0.23333248917344973,"text":"茅野ショップ"},{"minX":0.2815884518701013,"maxX":0.7220216682757151,"minY":0.2339659685863874,"maxY":0.2588350785340314,"text":"電話0266-82-2346"},{"minX":0.06739722633983103,"maxX":0.9182490246303695,"minY":0.2740183925129356,"maxY":0.3101037709500778,"text":"いつもご利用ありがとうございます"},{"minX":0.06432424539075224,"maxX":0.567530473591062,"minY":0.32808918977907187,"maxY":0.3578115533159665,"text":"2023年02月24日（金）"},{"minX":0.6710176871731538,"maxX":0.9210400907535118,"minY":0.3247539260624591,"maxY":0.3496646681381146,"text":"16時43分"},{"minX":0.07464877945592427,"maxX":0.7664480799572475,"minY":0.34896403207828863,"maxY":0.381289217484559,"text":"ポン・デ・リング 2点※"},{"minX":0.7617328656224552,"maxX":0.9169674851607034,"minY":0.35174418743992353,"maxY":0.3691860418669216,"text":"¥302"},{"minX":0.07839702394963864,"maxX":0.6617706621896948,"minY":0.37437346093941737,"maxY":0.4031153174595059,"text":"ゴールデンチョコレート"},{"minX":0.5703971129675253,"maxX":0.7220216682757151,"minY":0.39823298429319376,"maxY":0.42015706806282727,"text":"1点※"},{"minX":0.7942238226775626,"maxX":0.9205776053065198,"minY":0.39823298429319376,"maxY":0.41569767697319304,"text":"¥162"},{"minX":0.07383623651262215,"maxX":0.7674646532885027,"minY":0.416425709949114,"maxY":0.45541628992370287,"text":"桜もちっとドーナツ つぼみ"},{"minX":0.566787005247433,"maxX":0.7364620991560846,"minY":0.44469895287958117,"maxY":0.4666230366492147,"text":"1点※"},{"minX":0.7833935119430094,"maxX":0.913357389866335,"minY":0.44622093220655823,"maxY":0.4623691099476439,"text":"¥151"},{"minX":0.07581227454766389,"maxX":0.32851985223130215,"minY":0.4751308900523561,"maxY":0.5,"text":"[TO小計］ー"},{"minX":0.5740072206876177,"maxX":0.6931407940892521,"minY":0.4927325579508437,"maxY":0.5130890052356021,"text":"4点"},{"minX":0.7942238226775626,"maxX":0.9241877254523361,"minY":0.4911649214659686,"maxY":0.5088350785340314,"text":"¥615"},{"minX":0.07942239469348025,"maxX":0.29963899047056314,"minY":0.543520942408377,"maxY":0.5713350785340314,"text":"合計"},{"minX":0.0865730757822043,"maxX":0.3285894114342109,"minY":0.5914524038424667,"maxY":0.6149429301316826,"text":"(10%対象"},{"minX":0.086642610133665,"maxX":0.33212995995139455,"minY":0.6161649214659686,"maxY":0.6380890052356021,"text":"(8%対象"},{"minX":0.07581227454766389,"maxX":0.20577617732243736,"minY":0.6409883748798471,"maxY":0.6656976769731932,"text":"現金"},{"minX":0.07581227454766389,"maxX":0.20938627261680576,"minY":0.6583769633507853,"maxY":0.6861910994764397,"text":"釣残"},{"minX":0.7003610095294368,"maxX":0.9169674851607034,"minY":0.537630890052356,"maxY":0.5582460732984293,"text":"¥615"},{"minX":0.45478669206948547,"maxX":0.7184985033463965,"minY":0.5856051919347953,"maxY":0.6106157352787038,"text":"¥消費税"},{"minX":0.40782191621364133,"maxX":0.7221419989868562,"minY":0.6102298916322398,"maxY":0.636863149273458,"text":"¥570 消費税"},{"minX":0.8231046844383016,"maxX":0.9241877254523361,"minY":0.5857329842931938,"maxY":0.6047120418848168,"text":"¥0)"},{"minX":0.8014440381177473,"maxX":0.9241877254523361,"minY":0.6089659685863874,"maxY":0.6293604685998088,"text":"¥45)"},{"minX":0.7509025300364541,"maxX":0.9277978455981525,"minY":0.633720927213499,"maxY":0.6570680628272252,"text":"¥1,015"},{"minX":0.7942238226775626,"maxX":0.9277978455981525,"minY":0.6569767397735755,"maxY":0.6773560209424084,"text":"¥400"},{"minX":0.07942239469348025,"maxX":0.4945848306537839,"minY":0.7077879581151832,"maxY":0.7326570680628273,"text":"獲得予定ポイント"},{"minX":0.07454321050488599,"maxX":0.49959159819621607,"minY":0.7287189423725867,"maxY":0.7568851890364242,"text":"利用可能ポイント"},{"minX":0.855595666344857,"maxX":0.9241877254523361,"minY":0.7048429319371727,"maxY":0.7209302293068451,"text":"6P"},{"minX":0.7436823145962693,"maxX":0.9241877254523361,"minY":0.7280759162303665,"maxY":0.7514534795471511,"text":"5, 000P"},{"minX":0.07581227454766389,"maxX":0.5342960264473086,"minY":0.7718023330129254,"maxY":0.8023560209424084,"text":"楽天ポイントカード番号"},{"minX":0.49097472914655355,"maxX":0.9241877254523361,"minY":0.7994109947643979,"maxY":0.8197674376802294,"text":"ぁ*オネ****ネネ**6442"},{"minX":0.07220215440184752,"maxX":0.3537906186976728,"minY":0.8268979057591623,"maxY":0.8488372083733843,"text":"取引コード"},{"minX":0.30243833212588433,"maxX":0.9251655305247354,"minY":0.8461767466280473,"maxY":0.872813599271924,"text":"12380001020230224164347"},{"minX":0.19855596188225264,"maxX":0.7797833917971931,"minY":0.9083769633507853,"maxY":0.9404450261780105,"text":"並ばず受け取れる！"},{"minX":0.15884476453551252,"maxX":0.8050541582635637,"minY":0.9476439790575916,"maxY":0.9840116251201529,"text":"ミスドネットオーダー"}]
flutter: [{name:  ゴールデンチョコレート, price: 162}, {name:  桜もちっとドーナツ つぼみ 1点※, price: 151}, {name:  釣残, price: 400}]
flutter: [{"minX":0.4104547934829686,"maxX":0.7641229742091985,"minY":0.08217631131812242,"maxY":0.11356047350120035,"text":"mister"},{"minX":0.3963636362934595,"maxX":0.756363635521514,"minY":0.1132075471698113,"maxY":0.14389535744556525,"text":"iDont"},{"minX":0.28000001440964906,"maxX":0.6654545492908805,"minY":0.16408355795148244,"maxY":0.18901617250673852,"text":"No. 1238"},{"minX":0.1485309568665683,"maxX":0.8223781231885012,"minY":0.18189192203819915,"maxY":0.23380579781339494,"text":"茅野ショップ"},{"minX":0.2799999886781329,"maxX":0.7090909034767601,"minY":0.2324797843665768,"maxY":0.2558139482277102,"text":"電話0266-82-2346"},{"minX":0.06181821774873524,"maxX":0.9054545359104922,"minY":0.2789757412398921,"maxY":0.305256064690027,"text":"いつもご利用ありがとうございます"},{"minX":0.06545454414457737,"maxX":0.5563636316617866,"minY":0.32985175202156336,"maxY":0.3531976787227826,"text":"2023年02月24日（金）"},{"minX":0.6800000092633458,"maxX":0.9127272658967248,"minY":0.32703488085147825,"maxY":0.3531976787227826,"text":"16時43分"},{"minX":0.06909092200345172,"maxX":0.7418181755490488,"minY":0.3517441865247537,"maxY":0.37803234501347704,"text":"ポン・デ・リング2点※"},{"minX":0.7523720083510091,"maxX":0.9058098109536388,"minY":0.35268717763237556,"maxY":0.37115003477852304,"text":"¥302"},{"minX":0.06909092200345172,"maxX":0.6545454543115317,"minY":0.3763477088948788,"maxY":0.40128032345013476,"text":"ゴールデンチョコレート"},{"minX":0.5672727330740145,"maxX":0.7163636334629927,"minY":0.3982479784366577,"maxY":0.42014824797843664,"text":"1点※"},{"minX":0.7925059429509643,"maxX":0.9093122562710793,"minY":0.3980360108244452,"maxY":0.4173709581483085,"text":"¥162"},{"minX":0.06782462263187711,"maxX":0.7575413155515518,"minY":0.41818637282379234,"maxY":0.451270548159864,"text":"桜もちっとドーナツ つぼみ"},{"minX":0.5672727330740145,"maxX":0.7200000113218671,"minY":0.4433139533688115,"maxY":0.46511627978713044,"text":"158%"},{"minX":0.7890909075938027,"maxX":0.9090909137693666,"minY":0.444743935309973,"maxY":0.46366279015965217,"text":"¥151"},{"minX":0.0690908962719356,"maxX":0.3236363557297705,"minY":0.47371967654986524,"maxY":0.4970930229942754,"text":"「TO小計]-"},{"minX":0.5709090916342519,"maxX":0.6654545492908805,"minY":0.4925876010781671,"maxY":0.5131401617250674,"text":"4点"},{"minX":0.7890909075938027,"maxX":0.9163636437555992,"minY":0.49123989218328834,"maxY":0.5087601078167115,"text":"¥615"},{"minX":0.08000000411704258,"maxX":0.29818181364371443,"minY":0.5406976735816812,"maxY":0.5683962264150944,"text":"合計"},{"minX":0.6981818213631693,"maxX":0.9090909137693666,"minY":0.5377358490566038,"maxY":0.558288409703504,"text":"¥615"},{"minX":0.08363635624440083,"maxX":0.3236363685955286,"minY":0.5899595687331537,"maxY":0.6133720932623768,"text":"(10%対象"},{"minX":0.08312182884795268,"maxX":0.32426545270176804,"minY":0.6142545221950808,"maxY":0.6369819538291253,"text":"(8%対象"},{"minX":0.06909092200345172,"maxX":0.2036363624199647,"minY":0.639487870619946,"maxY":0.6627906943267247,"text":"現金"},{"minX":0.07272727413080997,"maxX":0.2036363624199647,"minY":0.6613372124108985,"maxY":0.683288409703504,"text":"釣銭"},{"minX":0.4581818218777996,"maxX":0.7127272684698764,"minY":0.5857558134752464,"maxY":0.6091644204851752,"text":"消費税"},{"minX":0.4072727248399294,"maxX":0.7163636334629927,"minY":0.6090116269504927,"maxY":0.6337601078167115,"text":"¥570 消費税"},{"minX":0.8145454496798588,"maxX":0.9163636437555992,"minY":0.5857558134752464,"maxY":0.6047843665768194,"text":"¥0)"},{"minX":0.7963636375800353,"maxX":0.9199999958829574,"minY":0.6090116269504927,"maxY":0.628032345013477,"text":"¥45)"},{"minX":0.7416786592686156,"maxX":0.9237758385592327,"minY":0.6335455799359838,"maxY":0.6571520885045959,"text":"¥1,015"},{"minX":0.7854545554664445,"maxX":0.9272727258691901,"minY":0.6555232539009855,"maxY":0.680256064690027,"text":"¥400"},{"minX":0.07908414226358294,"maxX":0.4955362027250293,"minY":0.703600963170959,"maxY":0.7292834999105037,"text":"獲得予定ポイント"},{"minX":0.07636362625816821,"maxX":0.49818181207570017,"minY":0.7280997304582211,"maxY":0.753032345013477,"text":"利用可能ポイント"},{"minX":0.8509090996110218,"maxX":0.9199999958829574,"minY":0.7034883730495073,"maxY":0.7210242587601078,"text":"SP"},{"minX":0.7418181755490488,"maxX":0.9199999958829574,"minY":0.7252906943267247,"maxY":0.75,"text":"5, 000P"},{"minX":0.06909092200345172,"maxX":0.5381818195619631,"minY":0.7702156334231806,"maxY":0.8008760107816711,"text":"楽天ポイントカード番号"},{"minX":0.4763636355858428,"maxX":0.9199999958829574,"minY":0.7978436657681941,"maxY":0.8168604560296812,"text":"※ネ**********6442"},{"minX":0.07160656367747417,"maxX":0.35423029212887336,"minY":0.823418362764014,"maxY":0.8480878968765794,"text":"取引コード"},{"minX":0.3047839031251647,"maxX":0.9207971582525295,"minY":0.8450596647442512,"maxY":0.8696777261492377,"text":"12380001020230224164347"},{"minX":0.20000001029260644,"maxX":0.7781817997486957,"minY":0.9055232539009855,"maxY":0.9375,"text":"並ばず受け取れる！"},{"minX":0.16000000823408517,"maxX":0.807272719693626,"minY":0.9433139687921159,"maxY":0.9811320754716981,"text":"ミスドネットオーダー"}]
flutter: [{name:  ポン・デ・リング2点※, price: 302}, {name:  ゴールデンチョコレート, price: 162}]
flutter: [{"minX":0.41605839584812976,"maxX":0.7737226322862628,"minY":0.08573675930781333,"maxY":0.11773255962817908,"text":"mister"},{"minX":0.4081734718855505,"maxX":0.763359381433218,"minY":0.11661776386134959,"maxY":0.1493705985554864,"text":"Dorur"},{"minX":0.28455168833374506,"maxX":0.6680030671975358,"minY":0.16687018119920027,"maxY":0.19359493805715777,"text":"No. 1238"},{"minX":0.15266971311707428,"maxX":0.8438064916960022,"minY":0.18813781258193496,"maxY":0.23710929178478957,"text":"茅野ショップ"},{"minX":0.2773722571974844,"maxX":0.7189780977874877,"minY":0.2369186009295523,"maxY":0.2616675406397483,"text":"電話0266-82-2346"},{"minX":0.0693430944550807,"maxX":0.916058405900033,"minY":0.2818563188253802,"maxY":0.3096486628211851,"text":"いつもご利用ありがとうございます"},{"minX":0.07299269926249588,"maxX":0.5620437943731215,"minY":0.3342947037231253,"maxY":0.3590116215802389,"text":"2023年02月24日（金）"},{"minX":0.6824817481562397,"maxX":0.9233576557224761,"minY":0.329837441006817,"maxY":0.35474567383324596,"text":"16時43分"},{"minX":0.07193439468564723,"maxX":0.5703854165058362,"minY":0.35519276355409346,"maxY":0.38297188913378344,"text":"ポン・デ・リング"},{"minX":0.5583941644359484,"maxX":0.7299270127287653,"minY":0.3560566334556896,"maxY":0.3779069793493134,"text":"2点※"},{"minX":0.7627737173449852,"maxX":0.916058405900033,"minY":0.35755813990704477,"maxY":0.3736234923964341,"text":"¥302"},{"minX":0.07539401852252141,"maxX":0.6618062397551002,"minY":0.37873391449982796,"maxY":0.4086989676320997,"text":"ゴールデンチョコレート"},{"minX":0.5656934293362463,"maxX":0.7189780977874877,"minY":0.40261627981408954,"maxY":0.42587209060420905,"text":"1点※"},{"minX":0.7992700669762332,"maxX":0.9233576557224761,"minY":0.40261627981408954,"maxY":0.421604614577871,"text":"¥162"},{"minX":0.07140071904078145,"maxX":0.7644493495051569,"minY":0.4230243700864619,"maxY":0.4572692975112763,"text":"桜もちっとドーナツ つぼみ"},{"minX":0.5693430693253226,"maxX":0.7262773677137372,"minY":0.44912790539505976,"maxY":0.47093023251161936,"text":"1点※"},{"minX":0.07255037531394104,"maxX":0.35445691537165985,"minY":0.4787727399965076,"maxY":0.5037853994104459,"text":"「TO小計]ーー"},{"minX":0.5693430693253226,"maxX":0.6751824782299901,"minY":0.4984268484530676,"maxY":0.5188953477672463,"text":"4点"},{"minX":0.7919707970499835,"maxX":0.9197080107074481,"minY":0.44912790539505976,"maxY":0.46802325516267174,"text":"¥151"},{"minX":0.7919707970499835,"maxX":0.8978102210325057,"minY":0.47819767488380593,"maxY":0.4869186039301008,"text":"ーーーー"},{"minX":0.7919707970499835,"maxX":0.9270073007375041,"minY":0.4955427372836916,"maxY":0.5145348837441903,"text":"¥615"},{"minX":0.08029198929255188,"maxX":0.3029197119912611,"minY":0.5464079706345044,"maxY":0.5742003146303094,"text":"合計"},{"minX":0.6970802880087389,"maxX":0.9197080107074481,"minY":0.5421511645584627,"maxY":0.5639748295752491,"text":"¥615"},{"minX":0.08394159409996706,"maxX":0.32846714668123145,"minY":0.5959302305112538,"maxY":0.6177325596281791,"text":"（10%対象"},{"minX":0.08394159409996706,"maxX":0.33211679169625946,"minY":0.6177241740954379,"maxY":0.6410592553749345,"text":"(8%対象"},{"minX":0.07299269926249588,"maxX":0.20802920295001648,"minY":0.6438953417661494,"maxY":0.6657052962768747,"text":"現金"},{"minX":0.08029198929255188,"maxX":0.20802920295001648,"minY":0.6656976788845372,"maxY":0.6875,"text":"釣銭"},{"minX":0.463238177092179,"maxX":0.7192435685510848,"minY":0.5910658853867945,"maxY":0.6138759667046981,"text":"¥0消寶税"},{"minX":0.4047941627552701,"maxX":0.7192934259909729,"minY":0.6141746212939786,"maxY":0.6401858317270664,"text":"¥570 消費税"},{"minX":0.8211678767549819,"maxX":0.9233576557224761,"minY":0.5930232591634029,"maxY":0.6104651192563582,"text":"¥0)"},{"minX":0.8029197119912611,"maxX":0.9270073007375041,"minY":0.6148255802788657,"maxY":0.6337209300464777,"text":"¥45)"},{"minX":0.7514420661373414,"maxX":0.9346893270339263,"minY":0.6390500401225337,"maxY":0.663275556159257,"text":"¥1,015"},{"minX":0.7991260030995244,"maxX":0.9271513646142128,"minY":0.6626221407253704,"maxY":0.6804011344409576,"text":"¥400"},{"minX":0.07664234427752388,"maxX":0.49999999294403885,"minY":0.710755818791582,"maxY":0.7341373885684321,"text":"獲得予定ポイント"},{"minX":0.07934598457828969,"maxX":0.49747833150177606,"minY":0.7316951021575527,"maxY":0.758267207113185,"text":"利用可能ポイント"},{"minX":0.8540146014750082,"maxX":0.9270073007375041,"minY":0.7078488394422686,"maxY":0.7252906995352238,"text":"SP"},{"minX":0.7445255525812644,"maxX":0.9270073007375041,"minY":0.7309910854745674,"maxY":0.7543604610225075,"text":"5, 000P"},{"minX":0.07664234427752388,"maxX":0.5291970797049984,"minY":0.7776162798140895,"maxY":0.8038804404824331,"text":"楽天ポイントカード番号"},{"minX":0.4927007407538976,"maxX":0.9233576557224761,"minY":0.8037790779549849,"maxY":0.8212209220450151,"text":"＊ネウネ*★★ネ****6442"},{"minX":0.07653008462255023,"maxX":0.3541268611299819,"minY":0.8268063589735186,"maxY":0.849065755635078,"text":"取引コード"},{"minX":0.3065693369024827,"maxX":0.919708010707448,"minY":0.8502884111169376,"maxY":0.8707393812270582,"text":"12380001020230224164347"},{"minX":0.21167884796504446,"maxX":0.7846715271237339,"minY":0.9084302385127163,"maxY":0.9404824331410593,"text":"並ばず受け取れる！"},{"minX":0.16058393837749094,"maxX":0.8065693369024827,"minY":0.9475616151022549,"maxY":0.9825581239041197,"text":"ミスドネットオーダー"}]
flutter: [{name:  ポン・デ・リング, price: 302}, {name:  ゴールデンチョコレート, price: 162}, {name:  桜もちっとドーナツ つぼみ 1点※, price: 151}]
```