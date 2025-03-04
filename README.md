# base16384
> **Note**: This project used the awesome cross-platform binary compiling tool [cosmopolitan](https://github.com/jart/cosmopolitan)

> Alternatives: [Go](https://github.com/fumiama/go-base16384), [Python](https://github.com/synodriver/pybase16384), [Android](https://github.com/fumiama/android-base16384), [TypeScript](https://github.com/shigma/base16384.js), [Lua(binding)](https://github.com/synodriver/lua-base16384), [Lua(pure)](https://github.com/Yiwen-Chan/base16384), [C#](https://github.com/lc6464/Base16384Coder-Console), [Rust](https://github.com/Wybxc/base16384-rs)

Encode binary file to printable utf16be, and vice versa.

## Description 说明
Use 16384 Chinene characters (from \u4E00 to \u8DFF) as the "alphabet", just like what base64 did.

使用16384个汉字(从`\u4E00`到`\u8DFF`)作为字符表，就像base64用64个字符作为字符表一样。

If length of the data has a remainder after moduled by 7, we will use \u3Dxx to log it with xx ranging from 01 to 06.

使用`\u3Dxx`附加在末尾以表示编码时数据不满7位的个数，其范围在01~06。

## Benefits 优点
Save more space and since the code 0x0000 is encoded to "一", finding zero space seems to be easier.

相较base64节省更多空间，更容易发现二进制文件的规律。

## Usage 使用说明

### Install from Debian Bookworm or higher 从 Debian Bookworm 或更高版本安装
```bash
sudo apt install base16384
```

### Install from Homebrew 从 Homebrew 安装
```bash
brew install base16384
```

### Install from my PPA in Ubuntu 乌班图下从我的 PPA 安装
```bash
sudo add-apt-repository ppa:fumiama/ppa
sudo apt-get update
sudo apt-get install base16384
```

### Build from source code 编译

Clone this repo first.

首先克隆该仓库。

```bash
git clone https://github.com/fumiama/base16384.git
cd base16384
```

Then use `cmake` to build.

然后使用`cmake`进行构建。

```bash
mkdir build
cd build
cmake -DCMAKE_BUILD_TYPE:STRING=Release -G Ninja ..
cmake --build . --config Release --target all --
cmake --install .
```

Now you can encode/decode a file by commands below.

现在可以使用命令对文件进行编码/解码。

```kotlin
Usage:
base16384 [-edt] [inputfile] [outputfile]
  -e		encode
  -d		decode
  -t		show spend time
  inputfile	pass - to read from stdin
  outputfile	pass - to write to stdout
```

## Examples 用例
1. Encode simple text 简单文本编码

```bash
echo -n "1234567" | base16384 -e - - | iconv -f utf-16be -t utf-8
婌焳廔萷
```

3. Decode simple text 简单文本解码

```bash
echo -n "婌焳廔萷" | iconv -f utf-8 -t utf-16be | base16384 -d - -
1234567
```

3. Encode file 编码文件

The text below is the encoding of the base16384 itself on MacOS 12.6 arm64. It is clear to see the strucutre of the binary file.

下面的文本是使用base16384程序在 MacOS Mojave 版本下编码自身的结果。可见文件结构十分清晰。

臾糟蘜一乀縀倀倀一仰一习佀丈戀渀一一乤一丒一丁浟成扴捩卒懀一一一一一一一一一一伀一一一一一一一一一一一一一一一一一一一丙一不渄一旗荄捡戀一一一一一一一丁一一亀一一一一一一一一丠一一一丅一一戀一佀一一一丗菷徕虴一一一一一丅譽扅搕一一一一一丂爋一丐一仈刀一一一眂縀丈一一一一一一一市一一一一一一一佽浳欝搧娀一一一一也旕剕潐一一一一一丛俀一伀一唠一一一丆繰一乀一一一一一一嘄丠一一丆一一一一旗蔷忕灟栙擇侕耀一叵譑単挀一一一一一冀樀一帀七尀一一一仠唀一嘀一一一一一一乀倀一一一一一一丅譽煳欜璖螜一一一丁浟挑掅帀一一一一一禇帀丄一丸帐一一一壡舀一一一一一一一丈一一一一一一一一也旝擧殥籤旚擦枼一丗菵引晔一一一一一三乼一乀一俀一一一丂帟一丠一一一一一一一一一一一一一一一侐一予乀丅譽剁挐帀一一一一一丠一丐一一刈一一一丈一一一一伀一一一丰一七一一帀一一一佽浮椗蔷玵灯椗蔇忈也旑刕弄一一一一一一倀一伀一亀一一一一亀一什一一一一一一吀一估一一一一一一旗葶诐一一一一一一叵謑佔幀一一一一一丠渀一帀一昀一一一丈嘀一娀一一一一一丁渀一戀一一一一一丅譽穡旜薖莉絬旜啇嘁浟弐捄刀一一一一一嘈一丄一並一一一一倂一七一一一一一一东一丅縀一一一一一也旘蓶莵絮一一一一丗菴弅扁一一一一一丌亀一乀一丰丠一一一一一乀一一一一一一乀一一一一一一一一侐一么一丅譽婉憒艔弥戀一一一丰嘀丐一一刀一一一丌一一一丼习一一一丐一丁一一一一一一予一渌一一丰一亀一丈娀七一一一一一一与儀一币一劃刀付一一嘀一吀一你耀三一丁丵一夀刀下一丅一一一一丄一一帀一嬀一仠一世一一一一一一一一一一一一一一一亘嬀丂瘀一一一一一一一一一一仠一丠一一縀一姝攷嚽穩暋葇玱爀一一一丛一丁渀一斪罒跻舷圪讫惙硗垚愠一丠一一刀一七溠一崊一帀一儀一一么倪一丁一一一一一一上一倀昀一峀稀一一一一一一一丰一与一一昀一丠一一一幐一伀姝攷嚽穩暋蓆玉慹櫝呖芹倮朞擆玈一一一亘一丄一一渲一侀一丩一丁一一尌渀亀一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一丁捈灹挴瀏稘怣揞烼吀一劈畻皮刀丄澤姨什丄烣椴箵蘭虭先诚纄瀧幈繺凴焇蠒怣幀圠俈怠詁潭毃捒嚞挅敁掐捅嬢凬删跰忔蝉災劈筸嚀峋敒茢域蠮伀丂埁滸淨巤偵媑嚧稅侀距啓怏蘂歟粇蘈一簿淿跿礊蠜渠丂蛿跿跴瀏刐擐揄卹佟数貅稈一簿緿跿秧滾丰谖夀一嘇稉舏潞縐丁嚍整姰昀一怢毮熰崀丒咐綠儀丒妍竒蓗溷澴嬣蕫倒暝朢埐怰沃謧俾劒帜朤俎裒劈荷庿侀一伢埞蠬仰丁嚸蓍奭氋氛廒嵶稡垉莒咐嶠儀丒嚝匣俩巒樟虉圁膒帜朦奄圂剈矠僫仑感朄嶾翠趆忐皃谙廸敘一丒暷纐幉烝偁漢嬕粄缀伢嬍盄縀冣码一岱茦奼圄劘篐爘怣彙穌帀怣廘幌一蠼繐丁侉翓晟柑晅潿蕕嬦奄圆周嫠筴怒囕蕂贆一丄瀧注亃縀伡眳蠀縀伢蛛嬭筸奸楃怽蒰漢埐怰沃謣俺劒东地矶怀此瀴謔刀七唃瘓净七唁厅跃虉添跿幣承谏蘆毑劈舷昀一劆娒佈乲巾伢嬽譃縀冣欎一妀刀一衚巯跿盐一下燯跿跺掟觿跨繀一僣諿跿貔移跿怣懘湀一蠪廠丁劉谺慯觿赈煏檐言仨獃渀僠倀一岒击跿怣懝娼一蠟绠丂蘃一与爫賿跒囓蕰崀为咐蘀亸伀一冧苽跿芈苷洏一岅娸一簁帀七矞赿跴瀴诧净与滴尀丮习一仩耿淿謢嬽覃縀冠甎一妀樀一衬緟跼崟丌淿跽蟿跿蛿跿趥跿跻緿跿艿跿趟跿跕抈疕嚍嵵绰七盺兀丄瀴謘刀与熸嬀丒囓苘帀为尠舀么煏慱一仨莃帀伢嬽射一冣堍一劈苵倐一岋蘴一怣懕繀一敺椐舀亐爤協瀧獁提捤单佔拒嘞肠一丒暜茦埖怢涶栌购怢敜濔捈灼犈獷幈烁橱一乌烈儜疬荈煭意跿赈灷貆訴一幯縐一亅縃虖済一怢苙伢叉凢厰嘀么灗欄拇版烕檆栌蠭歃劈稖吐一勈竣礘怢檴瀴菭净丄瀧旨蛃一伢埙恢橴萗贏漪帀丁嚅聃虊稀一怠涐刀帀凣柠一么灓樄瀭诐婽焜冣弌一噜举嘹乀丈甌翿愢葜伲埦粀帀丂蜂一丄吧久婲沉舰一怠趏訾刚乀丈獷幉曳劆畆愤恤犌喨湄乸皝唇真繾渠唪嬜荀一一矚幣捁懾出佃虰娄一怣廙訄一怘罉匠俊跸犘甚凋侺涰一乁緀渀七睩乀丄萗牵唒囓扤崀丒嚷蕃瘋儀丄琧剈潰仸悤一丯跠一乌灿粏測一緿縀丁媉趺岰稀亾乀一僫諿净勈痝媉虺寀稀么潰啂謲執灱狈疪蜸恄渎濤唀丒吿僨伀一勈疽媉豺妀稀么潰啛膧洀一劈笗噦滎僗帡媉跺嗠稀久婿芈笗幦滎僐谓倀一勈疟癥僀与瓔一丐槰戀一衪渀丁便侀一冦洀一创訌一为杀一义灱瘼娣礓恢橮稹垉羠誰憬呉灱瘼娪凃启跠一乌灿粂昬一緿縀丁媉趺侐稀乌災苈算乄灹狈疪埙蠯繠丁噣訮渐一乌灻苈痧盾傀丄瀗乴墓嚟欲埦蠾溠丁嚋彲周嫠筴倓嚟趢谊一嚷蕃皰傀丄拇跫侐槰帀一弢涄瀇动一丅笅橁敐揤卽毃枤启跿赪趿跶移跿捿跿譗跿跚緿跽捈灹戕欅摁挔芈旽艶恢浴瀗葴歒暜蜢埓恢淋跸一专嚟覡渊一姿言一愢淮潌堀丯渐一人贿绰伢域愢氞漐堀丒噜俐赈灷蚜朲埲籎劑嘃盡佀丄澏纺乀一伲執愢涞満堀丒噜俖誸伀一冬庸什一冬垸亀一冬倱縖舕缅汁旗樵挢埥幕舕朅捁挔茈旽虨幢浸旙虨恢櫤琧捁灿劈苗嘌一妠嘀一弢淾渜堀丮総証乄灹苈疻盟偀丄瀗乴嵓嚞谧呌灼禓漤怀蠓乐丁噣萑嚟謲埶怢殮焼圀丒冝濷冸伀一冬庸什一冬垸亀一冬倱縒嘼帡楁攐揔卹佟数荔瀧獁提捤单佔拒嘞肠一丒暜缢坕縒暟挢埻枠臲菔恈灗欄瀬厢儀丄耬縱蓺腴瀶茰跿跴瀧淨悂帀伆贁一丈攀嶅搀渀伢奍爒噜爾噋亀丄瀧噈灗欄拇葈灲葤名謀奓嚖蔡茌怢繕爰一愢膎穉嚍孰纰丁媉觺妐渀义灱苈箷乍潿绸慈一丒噝稾勔一丄瀇褁丄一谷唀一劈篷帱讌樎炨嘀両樀谣吁一刘甘翿怢毫瘄一丮帠一乁灰剓唧癹倀丄瀏蛿凡塰刀义灱嚝甇蜟繺忐啦埈繾丸嶇蘩繠訑勇乁渏偏蘾拀恣懄张俀灷炜朲埪蠁习丁噣訮渐一乌灻苈痧瘟倀丄瀗丏漆縐丁媉蟒嚝覠攈一劈笗噦滎僗帡媉跺宰樀乄災貌舜一彌淾狔伀丐槰嘀一衊渐丁宅讝忄瀴菅傀丄瀭诐蠭繰丁垉羒噜举刃乀丄耧藨畁縀价谀一啐眲執蠣湰七礊灱苈痛盖俀下蘄一丮渀乀乌灹苈症癿俀丄瀧内蓃蛨樀一愢浾潨唀丠趏译劃谏敓挲執蠒买丂叀欌芈略囁虈劋瘀一一帀丁嘁艒吽嬇各匏曕稉囁豈刘渐嫫傢橴耧蓨杁縀伲埧灷狈疪蜑七渎熤刀丒吿僨伀一勈疽媉豺乀樀么潰仸掇跿跐槰帀一裏芈笗噦滎僗帡媉跺娰昀久婿芈笗幦滎僗庁媉诺壠昀仫厐槰戀一裃爛記一为繤哼儀一剈痡嚁缪一丁楁攐揔卹佟数荔瀧獁提捤单佔拔劈旽舧恢浴瀗葴塒暜缦埖恢淞潸吀丏淠一乵喓嚞趡崆一岱裠儀一岛縀一簀渀七瞲一丈甝媉覺嘰昀亾乀一僨一刀勈疝媉衺僀昀么灰虝稾岆一丄耧編俁渀倏蛿欑嘿滵茵愢泾燔匀両樇廍嚉葒娞劁嚺一一丄一丒丝匡燓幱湁延孛互娟犁侈伃岰砧啌灻粁嘘一愢汸畹媉誮弐丸仨玀縀伡燰粀帀丁媉诓嚟疢缅一劈攀嶅晿跿賠刀一岰囇么滱亅笅橁敐揤卽毃捒嚞挅敁掐捔卑慈滻侄瀥揀灟欈旼嶈赀一倧膅讃蚏瘀一恢櫬昄人亀一倭诐怢櫮濨匀丒嚜哠唀一劈巤倏然縀丂坝脑愞茆举趐廹攕匁襒搽茦嬴單渀乀么塶皷蕃癀佀丄琧喅蓟纔搗贏熨帀丁匱蜑晟诹廆彵縋瘄一丢藝伢孵菺估戀亊彵臃菔抺乀一倭诐怣敝涣褄一嚤敝匁赡娇幍坣腐橠常譄煚帤吡刎乺繤哰伀一勈痝劉覒嚵蔁嚉蒮弐丸仨桀渀伱燸烟櫄瀧汌灾粌渐一形汔继蘏煓淿跾蘄一与穂蘃一与稦蘂一与稈翀怠詁潭作幗戕蜅浝绤圅挢埥幕舕朅打怘詤羧亓園朤甇瘠幀洄性仁蠇舜嗠偁买刨舓匀一丄劧乂煓乯谏蜅毈犈艷唁一劆娲奈乶淾吏嘆裃昼丣礈滲乎税净傐帟倏哹氞拆崹匱蜒榠一一一巳謦褀一丏諼一息渄蘁尀憀勤拇赊烇側渿奈灷犌喸偌噵犈略囁衁勂啥嘉詒嚝蜣修侠池七贿怂櫬喬嚁蛿臰丁嘉諓丟嬠巋悢忏眧跇恠詀欴蟌涬岰朔翿彌汄搗丏漄帐丁吏箃側耧坈繺帤琏漃恰氐蜤埉幠趀刾勒一丄瘾豌埀抈甹囁螁瘞昀贀专亜蜢凡仒娞剑垉聒废匆凸亃虊帀一悃觤纜偈灳犌喘媁螀一訁娉膒嘾刽囁虇劘甥圉詐昿渍艺悃觤纜先灳犌喘抁螀一丽娉膒嘾刽囁虈犘甥圉詐昿渑艐悃觤纜剈灳犈喛一一劌喘桌偳犈嶄赈繸悤琧坉偼战巠却坒滻蜰甅怢櫤瀇瓀一丄焇琢愂櫤瀏漿怰氓传埱恢檔烥尀憀勠伸乌乲抨爳衈曲婤師谽弢剀秽楁攐揤卽毃枤勏觿赂趿跴姻跿忿緿謟賿跔淯跽噣羑愜倁訇趏敓茐嶾弁跴吵仿滾乗檹嚍兲帐丁噣传技唣跠滱綮穦准谺罈崛詁簀帀七礉滱絤哠吀一協瀧獁提捤单佔拢洌嗠淁蠇帟倧俁豀蘾几矈庣拀処叉氞苆崥匱蜒榠儣資趱跬欦褀一一七諿息渀一仼跀丄瓼一縿绰一久婻抨穳絈凲芘苒案灼拂啥嚉諓借嬢嬌瑒嚟嬣俣伓借笠埋怰池标琀跏縄渧汈凳犨狐灉跱折崐啍屳嗫熬呅婻打喑刁縑晜举勠一丄砬諯煓褬喤岃虀蛘胧图跿舨渰灁滾丐谒谀一劈萾胿穿蚜複簆湹緀一争胰沱怏焃偼舨潰瀁幠趀嘾劓一丈画修儠汯一一繺忀病傈愈渤吏蘃欞劋糋趱跬淿跽嘁賢毬喸抁螼一丁嚉葒娞犊凡凂洔堡娢仐昿渑艉怢殔焇眚湸樀一么繺肨嶌贉胐皅纈剁滾乗庡嚹窿褟資趱跒东謢培怰沒堇激一丄焇細滹臰甽傈洈湕笅橁敐揤卽毃悿緿謃賿跐巯跽叾跿艟觿赕趿跿誖簃一已擀儀丿聛嘌一跉楀娀仿坭渰七败簀縀凼玺什丏誖訃一已擸儀丿聜丌一跉樠娀仿坱丰七败羀縀凼珈什丏誗堃一已攰儀丿聜蘌一跉欀娀仿坴渰一一愣忑爌一幔跲护儀两咀一一衹緿跽瘕一与畳跿跚倠一仩芿跿讠縀一岜燿跿栏帀七瞾跿跶漨一为楏跿赨揀一冦磿跿蒆帀一表巿跽癲一与瑛跿跚嗠一仩焿跿订娀一岘姿跿栦一七睸跿跶炘一为擯跿赨筀一冥狿跿蒌嘀一衖緿跽盏一与獃跿跚局一仩徿跿讣脀一岓臿跿栀渐七眲跿跷寁獮月商玵猺嘉擇掵脊丘琗宔缶嫎充讕聲旙著彽瑩椙揷宥补丘琗宔缶嫎充讕聲旙瓷侕籟槝敇俕艟枚擆戁灡櫙愓曌蘴旙攧坽瑯標擥讥籰歝叶枥穥丘琗宔缶嫎充讕聲旝蔦珑獟枚擆戁灡櫙愓曌蘴旙攧坽絰杛珶玹繵欗葦玱猀暘收拄萳對叶揉聟楘攅讥籰歝叶枥穥丘琗宔缶嫎充讕聲旜瑖厑浦桛呐侉潳杌慣嫠舀廛蔇珉睧栝倂澌眠媌儣嚁呵楚搖莄湍桛琖莽良如爦反猱完膃庀耮媋焢亡剥曈儓忑瘠媌儣嚤簠捜萖殔蠀暘收拄萳對倅窵獤欗怅箥籰歝呦玱獝嘖蓷揑繵欙璖羕欀嘈僖戤坥榘蓶徔丠嘋摀爥牥曛葆戀渠奝亐珍癯毈唷侕籤嘝咖莔丠嘚擧俕艦桛呐珁潳櫈僒俑素檙搖庁瑲槛怇寑物榀倂侽荴樝敆枥穥停吗富渭嘝哲保聩欙怇徼湳欙哷提乷暀唦嘃賿一丐一东一一嘀一圀一一一三一一倀一伐稐俑搁帚帬一崀一仰一丛忀一一一净一七一一縀嘀夀丠一一仒一一娃一璀娀佘侀丏樘丁瘃一儐尀乀一丄伀乀帀一一一一一一一一一一一一一一一一一仰唀一刀一貇一丄一丁俐一伀一仡舀丁一丁湴一乀一予欀一帀一稝一丐一丶啀一刀一帇帀丄一丒濐一伀一十舀丁一丅虴一乀一侠欀一帀丁耝一丐一乼啀一刀一澇帀丄一两俐一伀一垡舀丁一上年一乀一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一丁劈湠勀一久也旗蔷徑睮樀北嘢幀旗菷寑牯歝唀偁乤汛呅词艵暗萦玹牥檀圇嚀彀旘蓆讍祟柙敇徥筥两万嚠彀旘蓆词猀爀唣久也枘蓆词猀爀唣湅也枙著後亐东爁匁浦槜呖蘂帀檒伔佽瑰歝吰偀乲戄戅讙聥晙三丁聘剐叶柝聩欙帉丁聠剐叶莵潰两万垠彀旛敖螵潰两万埀彀旛蔆掸亐东疁匁浰杜甦诈亐东瘀剅也樜璖蟑琀爀唨渄彀旜啗忌亐东眀剅也檙搖市帀檦丑匁浳欘敂弥屏弑慣市帀檨丑匁浳欜瓆掸亐东碀剅也歛瑶揑焀爀唫丄彀旝蔦珑猀爀一卼丅丁珶莡浥氙搷揑獟栙搖徕耀慙著彽腴晜畅讵脀扛搖玸乖暘收拄萳對台佭牥曘畖昃圁杛琶埕琀膀帠一七丩佰丌们叀一垕籣槙呐侹牥曛葆戂搁一珶昁蔀緀帀宥穥両縗丂威最圐刌二喀丰凰焀什垲戀丂旙渊丄仄乀丶玱猀稀攀僔佤丮渐娂舦一縏檬七両烠丌仄娀丰冠舀什娄刀刀舰戀一一丩佴焐卜訁柰呤促佣縫蘊爄一一偐尀万一布爑一侀丐乐咀丁渀刀指一习丄丧帐一封一夀蘀丁一一嘀一净开一一一帀一搀一仰刀乨咀一刀一堀一丼伀丁潰一伀一凐一丏乀七幌一乀一佐一七縐七蔕一丐一乩一一訄一弆一丄一丞縀一崁一垱嘀丁一三一一净帀丰崀一帀丂甀一仰刀仼剀一刀一紀一丼圀丰倀一伀一婀一丏偀不亀帀乀一儰一七縐丂爋一丐一仚一一訄一褂縀丄一丸一一伀一帀一一一与瘀一乀一刀一一一七茀一丐一伀一一一一伀帀丄一乀一一一一亰刀丁一丐一一一一乌伀一帀丄一一一一业乀一刀丁一一一一丈帐一伀一帀一一一丂渄一乀一刀一一一一紁一丐一伀一一一一寀帀丄一乀一一一一凐刀丁一丐一一一一伔伀一帀丄一一一一之乀一刀丁一一一一且縐一伀一帀一一一丅稄一乀一刀一一一丁漁一丐一伀一一一一柀帀丄一乀一一一一啐刀丁一丐一一一一俴伀一帀丄一一一一亅乀一刀丁一一一一丣丐一伀一帀一一一丁一一剀一么一丄縀一戀一佐一世一丁樀一吀一乤一丆渀一椀一俀一丝一丁蘀一嗀一亀一丈帀一瀀一一丁与一一言一囀一乀一丄帀一怀一估一且一丁戀一厀一乜一丆一一最一侠一丛一丁縀一啀一乸一万縀一渀一倐一丢一丂丁浟楚叶握獣歝呕计獡朙攠佽灡櫙愓曌蘴旙呖宽牥丗萦反猱完膃彽牥曛葆捽瑤丗萦反猱完膃彽牥曛葆捽瑩椙帅讉潳杌慣嫠艟朙搶讑獟果丅讉潳杌慣嫠艟杛琶讑猀旘琗宔缶嫎充讕籣槙呕讙爀旘琗宔缶嫎充讕籣槙呕讙睬杀叶垅腥婍焳滑浥榘蓶徕浦樀叶徕煢歙清讕籣暝摠佽略欗蔷待聴旛攰佽筡桛清譽浳欙咖蟀也旗蔷徑絵欜丅讍穯曚菶殕艴桛摐佽煬槜葐佽瑣椛蔶戁浦柙敆威浦槜呖蘁浦樝敆威浦檙搖币浦毜璗徔也楛搗丁浭歛瓖叀也槜呖蘁浰杜甦诈也樜璖蟑琀旜啗忌也檙搖币浳欘敂弥屏弑慣币浳欜瓆掸也歛瑶揑焀旝蔦珑猀朞擆彽腴歘珶垥籤杜清证聩榝号揍潧杀一一一一㴁
