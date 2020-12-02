---
title: 在 Power BI Desktop (預覽) 中使用圖形地圖
description: 在 Power BI Desktop 中使用圖形地圖建立區域的相對比較
author: mihart
ms.author: mihart
ms.reviewer: sujata
ms.service: powerbi
ms.subservice: pbi-visuals
ms.topic: how-to
ms.date: 03/18/2020
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 9e77e539a098633badef6e4a88b99d07f2781974
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96397632"
---
# <a name="create-shape-map-visualizations-in-power-bi-desktop-preview"></a>在 Power BI Desktop (預覽) 中建立圖形對應視覺效果

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

建立 **圖形地圖** 視覺效果，使用色彩比較地圖上的區域。 不同於 **地圖** 視覺效果，**圖形地圖** 無法在地圖上顯示資料點的確切地理位置。 相反地，其主要目的是要藉由不同的著色，在地圖上顯示區域的相對比較。

**圖形地圖** 視覺效果以 TopoJSON 地圖為基礎，其具有使用您可建立自訂地圖的強大能力。 自訂地圖的範例包括：地理位置、座位安排、樓面規劃等等。 此預覽版的 **圖形地圖** 無法使用自訂地圖。

> [!NOTE]
> 若要與 Power BI 同事共用報表，必須兩人都擁有個人的 Power BI Pro 授權，或將報表儲存在 Premium 容量中。

## <a name="creating-shape-maps"></a>建立圖形地圖
您可以用此 Preview 版本隨附的地圖測試 [圖形地圖]  控制項，如果您自己的自訂地圖符合下一節 **使用自訂地圖** 中所述需求，也可加以使用。

**圖形地圖** 視覺效果僅供預覽，且必須在 Power BI Desktop 中加以啟用。 若要啟用 **圖形地圖**，請選取 [檔案] > [選項及設定] > [選項] > [預覽功能]  ，然後選取 [圖形對應視覺效果]  核取方塊。 您完成選取後必須重新啟動 Power BI Desktop。

![啟用圖形對應預覽功能](media/desktop-shape-map/power-bi-preview-features.png)

啟用 [圖形對應]  後，選取 [視覺效果]  窗格中的 **圖形對應** 圖示。

![選取圖形對應的範本](media/desktop-shape-map/power-bi-shape-map-template2.png)

Power BI Desktop 會建立空的 **圖形地圖** 視覺效果設計畫布。

![您的畫布上會出現空白圖形對應](media/desktop-shape-map/shape-map-3.png)

執行下列步驟來建立 **圖形地圖**：

1. 在 [欄位]  窗格中，將具有區域名稱 (或縮寫) 的資料欄位拖曳到 **位置** 貯體，並將資料量值欄位拖曳到 **色彩飽和度** 貯體 (您還不會看到地圖)。

   > [!NOTE]
   > 如需快速取得地圖資料以測試 **圖形地圖** 的資訊，請參閱以下主題為 **取得地圖資料** 的一節。
   > 
   > 

   ![建置您的圖形對應](media/desktop-shape-map/shape-map-3a.png)
2. 在 [格式]  設定窗格中，展開 [圖形]  ，然後從 [標準地圖]  下拉式清單中選取，以顯示您的資料。 此時會出現轉譯，如下圖所示。

   ![開啟 [格式化] 窗格，然後選取 [圖形]](media/desktop-shape-map/shape-map-3b-new.png)

   > [!NOTE]
   > 本文章最後的 **區域索引鍵** 一節中為具有地圖區域索引鍵的資料表集合，您可以用來測試 **圖形地圖** 視覺效果。
   > 
   > 
3. 然後，您就可以使用格式化選項 (例如 [預設色彩]  、[縮放]  等) 修改地圖。 而且，您也可以將類別資料行新增至 **圖例** 貯體中，並以類別為基礎來分類地圖區域。

## <a name="use-custom-maps"></a>使用自訂地圖
只要自訂地圖為 **TopoJSON** 格式，就可在 **圖形地圖** 加以使用。 如果您的地圖為其他格式，可以使用 [**Map Shaper**](https://mapshaper.org/) 等線上工具將 *shapefiles* 或您的 *GeoJSON* 地圖轉換成 **TopoJSON** 格式。

若要使用您的 **TopoJSON** 地圖檔，請將 ShapeMap 視覺效果加入報表中，然後將一些資料加入「位置」  與「色彩飽和度」  貯體中。 然後，在已選取 [格式]  區段 (在下圖顯示為 (1)) 的 [視覺效果]  窗格中，展開 [圖形]  區段，然後選取 [+ 新增地圖]  。

![開啟 [格式化] 窗格，然後選取 [新增地圖]](media/desktop-shape-map/shape-map-6-new.png)

## <a name="sample-custom-map"></a>自訂地圖範例
「美國律師事務所」  發行有關其訴訟和個案數的年度會計報表。  您可以在下列連結中找到其所有報表：

https://www.justice.gov/usao/resources/annual-statistical-reports

由於州會劃分為多個區域，因此我們必須使用自訂圖形地圖。  藉由將美國司法管轄區的 **TopoJSON** 地圖匯入 **Power BI Desktop**，我們可以接著將年度會計區域律師資料視覺化。  下圖顯示此地圖的範例。

![自訂圖形對應](media/desktop-shape-map/shape-map-7a.png)

您也可以使用個別州地圖來執行有趣的作業，並根據其所包含的區域顯示更多詳細資料。 

![德克薩斯州圖形對應](media/desktop-shape-map/shape-map-7b.png)

如果您想要測試此資料集和視覺效果，則可使用下列連結來下載原先用於產生此報表的原始 PBIX 檔案。

* [自訂圖形地圖示範 .PBIX 檔案](https://download.microsoft.com/download/1/2/8/128943FB-9231-42BD-8A5D-5E2362C9D589/DistrictAttorneyFiscalReport.pbix)

## <a name="getting-map-data"></a>取得地圖資料
若您需要快速將資料輸入模型，以測試 **圖形地圖**，您可以複製本文章最後的其中一個資料表，然後從 [主資料夾]  功能區選取 [輸入資料]  。

![在 Desktop 中，選取 [輸入資料]](media/desktop-shape-map/shape-map-4-new.png)

如果您的資料有多個資料行，您必須使用類似 Excel 的編輯器貼上資料，然後分別複製每個資料行。 然後您就可以將資料貼到 Power BI Desktop 中。 頂端列會自動識別為標頭。

![建立資料表窗格](media/desktop-shape-map/shape-map-5.png)

您只需要輸入新的資料行名稱 (在空白資料行右邊)，就可以新增資料行，然後在每個資料格中加入值，就像您在 Excel 中的做法一樣。 完成後，選取 [載入]  ，該資料表就會加入 Power BI Desktop 的資料模型中。

> [!NOTE]
> 使用國家或地區時，請使用三個字母的縮寫，以確保地理編碼在地圖視覺效果中運作正常。 請「不要」  使用兩個字母的縮寫，因為可能無法正確辨識某些國家或地區。
> 
> 如果您只有兩個字母的縮寫，請參閱[此外部部落格文章](https://blog.ailon.org/how-to-display-2-letter-country-data-on-a-power-bi-map-85fc738497d6#.yudauacxp)，以了解如何將兩個字母的國家/地區縮寫與三個字母的國家/地區縮寫產生關聯的步驟。
> 
> 

## <a name="preview-behavior-and-requirements"></a>預覽行為及需求
本 **圖形地圖** 的預覽版本有幾個考量和需求：

* **圖形地圖** 視覺效果僅供預覽，且必須在 Power BI Desktop 中加以啟用。 若要啟用 **圖形地圖**，請選取 [檔案] > [選項及設定] > [選項] > [預覽功能]  ，然後選取 [圖形對應視覺效果]  核取方塊。
* 目前，您也必須設定 **色彩飽和度** 貯體，如此一來，**圖例** 分類才能正常運作。
* **圖形地圖** 的最終發行版本將提供使用者介面來顯示目前選取之地圖的地圖索引鍵 (並未針對最後發行版本設定任何日期，而 **圖形地圖** 仍處於預覽狀態)。 在此預覽版本中，您可以參考可在本文後續 **區域索引鍵** 一節中找到之表格中的地圖區域索引鍵。
* [圖形地圖]  視覺效果最多可繪製 1,500 個資料點。

## <a name="region-keys"></a>區域索引鍵

使用此預覽版本的下列 **區域索引鍵** 來測試 **圖形地圖**。

### <a name="australia-states"></a>澳洲：州

| 識別碼 | abbr | iso | name | 郵遞區號 |
| --- | --- | --- | --- | --- |
| au-wa |WA |AU-WA |西澳洲 |WA |
| au-vic |Vic |AU-VIC |維多利亞 |VIC |
| au-tas |Tas |AU-TAS |塔斯馬尼亞 |TAS |
| au-sa |SA |AU-SA |澳洲南部 |SA |
| au-qld |Qld |AU-QLD |昆士蘭 |QLD |
| au-nt |NT |AU-NT |北領地 |NT |
| au-nsw |NSW |AU-NSW |新南威爾斯 |NSW |
| au-act |ACT |AU-ACT |澳洲首都特區 |ACT |

### <a name="austria-states"></a>奧地利：州

| 識別碼 | iso | name | 名稱 - 繁體中文 | 郵遞區號 |
| --- | --- | --- | --- | --- |
| at-wi |AT-9 |Wien |維也納 |WI |
| at-vo |AT-8 |Vorarlberg |福拉爾貝格 |VO |
| at-tr |AT-7 |Tirol |提洛 |TR |
| at-st |AT-6 |Steiermark |史泰爾馬克 |ST |
| at-sz |AT-5 |Salzburg |薩爾斯堡 |SZ |
| at-oo |AT-4 |Oberösterreich |上奧地利 |OO |
| at-no |AT-3 |Niederösterreich |下奧地利 |NO |
| at-ka |AT-2 |Kärnten |克恩頓 |KA |
| at-bu |AT-1 |Burgenland |布根蘭 |BU |

### <a name="brazil-states"></a>巴西：州

| 識別碼 |
| --- |
| 托坎廷斯 |
| 伯南布科 |
| 戈亞斯 |
| 塞爾希培 |
| 聖保羅 |
| 聖卡塔琳娜 |
| 羅賴馬 |
| 朗多尼亞 |
| 南里奧格蘭德 |
| 北里奧格蘭德 |
| 里約熱內盧 |
| 皮奧伊 |
| 巴拉那 |
| 帕拉伊巴 |
| 帕拉 |
| 米納斯吉拉斯 |
| 馬托格羅索 |
| 馬拉尼昂 |
| 南馬托格羅索 |
| 聯邦區 |
| 塞阿臘 |
| 聖埃斯皮里圖 |
| 巴伊亞 |
| 亞馬遜 |
| 阿馬帕 |
| 阿拉戈斯 |
| 阿克雷 |
| 訴訟區域 1 |
| 訴訟區域 2 |
| 訴訟區域 3 |
| 訴訟區域 4 |

### <a name="canada-provinces"></a>加拿大：省

| 識別碼 | iso | name | 郵遞區號 |
| --- | --- | --- | --- |
| ca-nu |CA-NU |努納福特 |NU |
| ca-nt |CA-NT |西北領地 |NT |
| ca-yt |CA-YT |育空 |YT |
| ca-sk |CA-SK |薩克其萬 |SK |
| ca-qc |CA-QC |魁北克 |QC |
| ca-pe |CA-PE |愛德華王子島 |PE |
| ca-on |CA-ON |安大略 |ON |
| ca-ns |CA-NS |新斯科細亞 |NS |
| ca-nl |CA-NL |紐芬蘭及拉布拉多 |NL |
| ca-nb |CA-NB |新布藍茲維 |NB |
| ca-mb |CA-MB |曼尼托巴 |MB |
| ca-bc |CA-BC |不列顛哥倫比亞 |BC |
| ca-ab |CA-AB |亞伯達 |AB |

### <a name="france-regions"></a>法國：區

| 識別碼 | name | 名稱 - 繁體中文 |
| --- | --- | --- |
| Auvergne-Rhone-Alpes |  |  |
| Bourgogne-Franche-Comte |  |  |
| Bretagne |Bretagne |布列塔尼 |
| 中央-羅亞爾河谷 |Centre-Val de Loire |中央-羅亞爾河谷 |
| Corse |Corse |科西嘉島 |
| Grand Est |  |  |
| 哥德洛普 | |   |
| Hauts-de-France |  |  |
| 法蘭西島 |Île-de-France |法蘭西島 |
| La Reunion |  |  |
| 馬約特島  |  |  |
| Normandie |Normandie |  |
| Nouvelle-Aquitaine |  |  |
| Occitanie  |  |  |
| Pays de la Loire |Pays de la Loire |Pays de la Loire |
| Provence-Alpes-Cote d'Azur |Provence-Alpes-Côte d'Azur |Provence-Alpes-Cote d'Azur |
|  |  |  |

### <a name="germany-states"></a>德國：州

| 識別碼 | iso | name | 名稱 - 繁體中文 | 郵遞區號 |
| --- | --- | --- | --- | --- |
| de-be |DE-BE |Berlin |柏林 |BE |
| de-th |DE-TH |Thüringen |圖林根 |TH |
| de-st |DE-ST |Sachsen Anhalt |薩克森─安哈特 |ST |
| de-sn |DE-SN |Sachsen |薩克森 |SN |
| de-mv |DE-MV |Mecklenburg Vorpommern |梅克倫堡─前波莫瑞 |MV |
| de-bb |DE-BB |Brandenburg |布蘭登堡 |BB |
| de-sh |DE-SH |Schleswig Holstein |什列斯威─好斯敦 |SH |
| de-sl |DE-SL |Saarland |薩爾蘭 |SL |
| de-rp |DE-RP |Rheinland Pfalz |萊茵蘭─普法茲 |RP |
| de-nw |DE-NW |Nordrhein Westfalen |北萊茵─西發利亞 |NW |
| de-ni |DE-NI |Niedersachsen |下薩克森 |NI |
| de-he |DE-HE |Hessen |黑森 |HE |
| de-hh |DE-HH |Hamburg |漢堡 |HH |
| de-hb |DE-HB |Bremen |不萊梅 |HB |
| de-by |DE-BY |Bayern |巴伐利亞 |BY |
| de-bw |DE-BW |Baden-Württemberg |巴登─符登堡 |BW |

### <a name="ireland-counties"></a>愛爾蘭：郡

| 識別碼 |
| --- |
| 威克洛 |
| 韋克斯福德 |
| 韋斯特米斯 |
| 瓦特福 |
| 斯萊戈 |
| 蒂珀雷里 |
| 羅斯康芒 |
| 奧法利 |
| 莫納亨 |
| 米斯 |
| 梅奧 |
| 勞斯 |
| 朗福德 |
| 利默里克 |
| 利特里姆 |
| 萊伊什 |
| 基爾肯尼 |
| 基爾代爾 |
| 凱里 |
| 戈爾韋 |
| 都柏林 |
| 多尼戈爾 |
| 科克 |
| 克萊爾 |
| 卡文 |
| 卡洛 |

### <a name="italy-regions"></a>義大利：區

| 識別碼 | iso | name | 名稱 - 繁體中文 | 郵遞區號 |
| --- | --- | --- | --- | --- |
| it-vn |IT-34 |Veneto |威尼托 |VN |
| it-vd |IT-23 |Valle d'Aosta |瓦萊達奧斯塔 |VD |
| it-um |IT-55 |Umbria |溫布利亞 |UM |
| it-tt |IT-32 |Trentino Alto Adige |特倫提諾─上阿迪傑 |TT |
| it-tc |IT-52 |Toscana |托斯卡尼 |TC |
| it-sc |IT-82 |Sicilia |西西里 |SC |
| it-sd |IT-88 |Sardegna |薩丁尼亞 |SD |
| it-pm |IT-21 |Piemonte |皮埃蒙特 |PM |
| it-ml |IT-67 |Molise |莫利塞 |ML |
| it-mh |IT-57 |Marche |馬爾凱 |MH |
| it-lm |IT-25 |Lombardia |倫巴底 |LM |
| it-lg |IT-42 |Liguria |利古里亞 |LG |
| it-lz |IT-62 |Lazio |拉吉歐 |LZ |
| it-fv |IT-36 |Friuli-Venezia Giulia |佛里烏利─威尼斯朱利亞 |FV |
| it-er |IT-45 |Emilia-Romagna |艾米利亞─羅馬涅 |ER |
| it-cm |IT-72 |Campania |坎帕尼亞 |CM |
| it-lb |IT-78 |Calabria |卡拉布里亞 |LB |
| it-bc |IT-77 |Basilicata |巴西利卡塔 |BC |
| it-pu |IT-75 |Apulia |普利亞 |PU |
| it-ab |IT-65 |Abruzzo |阿布魯佐 |AB |

### <a name="mexico-states"></a>墨西哥：州

| 識別碼 | abreviatura | iso | name | 名稱 - 繁體中文 | 郵遞區號 |
| --- | --- | --- | --- | --- | --- |
| mx-zac |Zac. |MX-ZAC |Zacatecas |薩卡特卡斯 |ZA |
| mx-yuc |Yuc. |MX-YUC |Yucatán |猶加敦 |YU |
| mx-ver |Ver. |MX-VER |Veracruz |維拉克魯斯 |VE |
| mx-tla |Tlax. |MX-TLA |Tlaxcala |特拉斯卡拉 |TL |
| mx-tam |Tamps. |MX-TAM |Tamaulipas |塔毛利帕斯 |TM |
| mx-tab |Tab. |MX-TAB |Tabasco |塔巴斯科 |TB |
| mx-son |Son. |MX-SON |Sonora |索諾拉 |SO |
| mx-sin |Sin. |MX-SIN |Sinaloa |錫那羅亞 |SI |
| mx-slp |S.L.P. |MX-SLP |San Luis Potosí |聖路易斯波托西 |SL |
| mx-roo |Q.R. |MX-ROO |Quintana Roo |金塔納羅奧 |QR |
| mx-que |Qro. |MX-QUE |Querétaro |克雷塔羅 |QE |
| mx-pue |Pue. |MX-PUE |Puebla |普埃布拉 |PU |
| mx-oax |Oax. |MX-OAX |Oaxaca |瓦哈卡 |OA |
| mx-nle |N.L. |MX-NLE |Nuevo León |新萊昂 |NL |
| mx-nay |Nay. |MX-NAY |Nayarit |納亞里特 |NA |
| mx-mor |Mor. |MX-MOR |Morelos |莫雷洛斯 |MR |
| mx-mic |Mich. |MX-MIC |Michoacán |米卻肯 |MC |
| mx-mex |Méx. |MX-MEX |Estado de México |墨西哥州 |MX |
| mx-jal |Jal. |MX-JAL |Jalisco |哈利斯科 |JA |
| mx-hid |Hgo. |MX-HID |Hidalgo |伊達爾戈 |HI |
| mx-gro |Gro. |MX-GRO |Guerrero |格雷羅 |GR |
| mx-gua |Gto. |MX-GUA |Guanajuato |瓜納華托 |GT |
| mx-dur |Dgo. |MX-DUR |Durango |杜蘭戈 |DU |
| mx-dif |CDMX. |MX-DIF |Ciudad de México |墨西哥城 |DF |
| mx-col |Col. |MX-COL |Colima |科利馬 |CL |
| mx-coa |Coah. |MX-COA |Coahuila |科阿韋拉 |加利福尼亞 |
| mx-chh |Chih. |MX-CHH |Chihuahua |契瓦瓦 |CH |
| mx-chp |Chis. |MX-CHP |Chiapas |恰帕斯 |CP |
| mx-cam |Camp. |MX-CAM |Campeche |坎佩切 |CM |
| mx-bcs |B.C.S. |MX-BCS |Baja California Sur |南下加利福尼亞 |BS |
| mx-bcn |B.C. |MX-BCN |Baja California |下加利福尼亞 |BN |
| mx-agu |Ags. |MX-AGU |Aguascalientes |阿瓜斯卡連特斯 |AG |

### <a name="netherlands-provinces"></a>荷蘭：省

| 識別碼 | iso | name | 名稱 - 繁體中文 |
| --- | --- | --- | --- |
| nl-zh |NL-ZH |Zuid-Holland |南荷蘭 |
| nl-ze |NL-ZE |Zeeland |澤蘭 |
| nl-ut |NL-UT |Utrecht |烏特勒支 |
| nl-ov |NL-OV |Overijssel |上愛塞 |
| nl-nh |NL-NH |Noord-Holland |北荷蘭 |
| nl-nb |NL-NB |Noord-Brabant |北布拉邦 |
| nl-li |NL-LI |Limburg |林堡 |
| nl-gr |NL-GR |Groningen |格羅寧根 |
| nl-ge |NL-GE |Gelderland |吉德蘭 |
| nl-fr |NL-FR |Fryslân |菲士蘭 |
| nl-fl |NL-FL |Flevoland |夫利佛蘭 |
| nl-dr |NL-DR |Drenthe |德倫特 |

### <a name="uk-countries"></a>英國：國家/地區

| 識別碼 | iso | name |
| --- | --- | --- |
| gb-wls |GB-WLS |威爾斯 |
| gb-sct |GB-SCT |蘇格蘭 |
| gb-nir |GB-NIR |北愛爾蘭 |
| gb-eng |GB-ENG |英格蘭 |

### <a name="usa-states"></a>美國：州

| 識別碼 | name | 郵遞區號 |
| --- | --- | --- |
| us-mi |密西根 |MI |
| us-ak |阿拉斯加 |AK |
| us-hi |夏威夷 |HI |
| us-fl |佛羅里達 |FL |
| us-la |路易斯安那 |LA |
| us-ar |阿肯色 |AR |
| us-sc |南卡羅來納 |SC |
| us-ga |喬治亞 |GA |
| us-ms |密西西比 |MS |
| us-al |阿拉巴馬 |AL |
| us-nm |新墨西哥 |NM |
| us-tx |德克薩斯 |TX |
| us-tn |田納西 |TN |
| us-nc |北卡羅來那州 |NC |
| us-ok |奧克拉荷馬 |OK |
| us-az |亞歷桑那 |亞利桑那 |
| us-mo |密蘇里 |MO |
| us-va |維吉尼亞 |維吉尼亞 |
| us-ks |堪薩斯 |堪薩斯 |
| us-ky |肯塔基 |KY |
| us-co |科羅拉多 |CO |
| us-md |馬里蘭 |MD |
| us-wv |西維吉尼亞 |WV |
| us-de |德拉瓦 |DE |
| us-dc |哥倫比亞特區 |DC |
| us-il |伊利諾 |IL |
| us-oh |俄亥俄 |OH |
| us-ca |加利福尼亞 |加利福尼亞 |
| us-ut |猶他 |UT |
| us-nv |內華達 |NV |
| us-in |印第安納 |IN |
| us-nj |紐澤西 |NJ |
| us-ri |羅德島 |RI |
| us-ct |康乃狄克 |CT |
| us-pa |賓夕法尼亞 |PA |
| us-ny |紐約 |NY |
| us-ne |內布拉斯加 |NE |
| us-ma |麻薩諸塞 |MA |
| us-ia |愛荷華 |愛荷華 |
| us-nh |新罕布夏 |NH |
| us-or |奧勒崗 |OR |
| us-mn |明尼蘇達 |明尼蘇達 |
| us-vt |佛蒙特 |佛蒙特 |
| us-id |愛達荷 |ID |
| us-wi |威斯康辛 |WI |
| us-wy |懷俄明 |WY |
| us-sd |南達科他 |SD |
| us-nd |北達科他 |ND |
| us-me |緬因 |ME |
| us-mt |蒙大拿 |蒙大拿 |
| us-wa |華盛頓 |WA |

## <a name="next-steps"></a>後續步驟

* [Power BI 中的矩陣視覺效果](desktop-matrix-visual.md)

* [Power BI 中的視覺效果類型](power-bi-visualization-types-for-reports-and-q-and-a.md)
