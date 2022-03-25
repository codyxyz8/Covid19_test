# 台灣Covid19境內外疫病統計
## 一、專案描述
本專案主要解決處理與分析大量Covid19資料的時間，透過Python、MSSQL與PowerBI的應用，我們可以很快知道台灣這兩年來Covid19的各項趨勢，以便我們可以花更多精力在資料分析上面。本專案之所以採用Covid19資料主要有三個理由。首先是Covid19作為近兩年全球流行的傳染病，台灣同樣深受影響，特別是去年五月興起了一波又一波的本土疫情，所以透過Covid19資料分析，可以更精準知道台灣境內外的感染趨勢與防疫成效，具有了解公共議題的價值。其次是Covid19原始API資料是由政府開放平台所提供，由於是開放資料在資料取得與應用上較無問題。最後是Covid19資料庫涵蓋著近兩年的Covid19確診資料，並有統計相關資料如年齡、居住地等等，筆者認為可以作為資料分析的作品範本，並從中應用Python、SQL與PowerBI等技術，以證明筆者在資料分析相關的程式設計能力。以下將逐一介紹筆者在此專案所應用的程式語言與軟體，如何應用在Covid19的資料分析上。

Python在此專案主要應用在爬蟲、資料庫連接以及定時排程等，可以在固定時間將API檔案下載下來，並儲存在MSSQL資料庫中，作為原始資料到後端資料庫的橋樑。Python目前可說是資料分析的熱門語言，不僅擁有許多資料分析相關的模組，同時也是資料分析師必備的職場技能，所以筆者透過本專案來展現Python的程式設計能力。首先在環境開發部分，筆者所使用的IDE為PyCharm Community Edition2021.2的版本，它目前是Python開發上主流選擇之一，十分切合本專案使用Python的開發需求。而在Python程式設計上，筆者總共設計了五個Python類別(Class)，分別來執行儲存JSON檔、連接MSSQL資料庫、紀錄檔、定時排程與主執行檔。在主要的程式執行流程中，首先是使用Request模組進行API資料下載與解析，並透過自製方法儲存成JSON檔以及取出最新的檔案路徑。接著，筆者在MSSQL建立名為「Covid19」的DataBase，並透過PYMSSQL模組連接到MSSQL的資料庫，再藉由SQL語法將Covid19的資料存入MSSQL當中。存入資料庫之後，筆者為了讓專案在執行上更加完善，透過Python語法進行定時排程與紀錄檔功能的撰寫，前者讓專案可以在每天下午三點(也就是衛福部兩點會議結束後一小時)進行資料下載，確保資料庫的Covid19是最新資料；後者則是讓專案在程式執行時能即時回報相關訊息，以便進行程式除錯與修改。最後藉由這些Python程式執行，讓Covid19的API資料順利存入MSSQL資料庫當中，為下一步資料分析做準備。

在存入資料的部分，筆者使用SQL語法讓API資料得以順利儲存在MSSQL當中，同時能在Pycharm介面中進行資料庫的查詢。在資料分析領域中，SQL語言也是十分重要的程式語言，比起Excel更具有處理大量資料的能力，同時也是許多企業會使用的資料庫語言，所以本專案採用MSSQL來展現筆者具有操作SQL語法的基礎能力。前面已經使用過Python將API資料下載並儲存成JSON檔，接著筆者使用PYMMSQL模組輸入SQL語法，建立屬於Covid19的資料表並設定其變數。在這邊需要注意的是筆者有使用到Drop語法，其原因是因為原本Covid19資料並沒有任何唯一的識別號碼，必須使用SQL語法中的Identity來建立，但如果遇到更新資料時可能會造成自創的識別碼對不上的問題。所以筆者會使用Drop語法先刪除先前建立的資料表再重新建立資料表，以確保Covid19資料是完整無誤的。當建立完資料表後，筆者再使用INSERT語法將Covid19原始資料輸入到MSSQL當中，如此一來完成了將資料儲存到資料庫的部分。最後筆者有設計方法可以在連接MSSQL的狀況下進行資料查詢，不需要到MSSQL的介面可以直接在Pycharm進行Select查詢，減少轉換IDE與維護程式碼的時間。

本專案的最後，筆者使用PowerBI視覺化軟體，將Covid19資料進行資料處理與圖表化，可以快速了解台灣近兩年來的Covid19的趨勢與防疫成效，呈現出筆者使用BI軟體的能力。PowerBI同樣廣泛地應用在各種資料分析領域，能夠將大量資料轉化成簡單易懂的互動式圖表，協助企業進行進一步的商業資料分析，所以本專案將透過PowerBI軟體的應用，進行台灣境內外Covid19的資料分析。在使用PowerBI技術層面上，是透過儲存在MSSQL的Covid19資料進行讀取，並且藉由PowerQuery進行資料清整(如切割時間、年齡層重新劃分等)。接著，則是透過PowerBI所提供的圖表與交叉分析篩選器進行圖表製作，最後再透過PowerBI帳號進行雲端上傳。而在Covid19資料分析與PowerBI網址則是放在後面的「PowerBI資料分析」第四章中，有興趣的讀者可以到此章節進一步閱讀。

總結來說，本專案作為資料分析的示範作品，目的是要呈現後端資料處理以及資料視覺化的能力。而本專案未來仍有許多需要加以改善的地方，像是Python其他資料分析模組的應用，如Pandas、NumPy模組，讓專案可以不需要依靠SQL或BI軟體就能夠進行完整的資料分析。或是在程式寫法可以更具有可維護性等，這些將會是筆者會持續精進的部分。十分感謝閱讀到這的讀者們，希望本專案能給予您一些啟發。

## 二、專案技術亮點
* **Python**
  * 資料爬蟲
  * 物件導向
  * 資料庫連接
  * 定時排程
  * 執行紀錄檔
* **MSSQL**
  * SQL語法應用
* **PowerBI**
  * 資料清整
  * 資料視覺化

## 三、本專案執行流程
本章將介紹本專案的執行流程，以及呈現專案執行成果。
1. 首先到covid19_main的檔案，會看到這段程式碼，接著在此頁面按下執行。
![Imgur](https://i.imgur.com/UU6c5PU.png)
2. 在console就會看到「排程成功」的訊息，以及預定執行時間與剩餘秒數。
![Imgur](https://i.imgur.com/9vQgloq.png)
3. 當執行時間一到，就會開始執行本專案所設計的程式碼，如有順利執行成功將會出現此畫面。這當中會有出現程式執行的紀錄訊息，方便程式碼的除錯與例外處理。
![Imgur](https://i.imgur.com/vPnTA49.png)
4. 如果是在今日三點以後執行covid19_main，同樣會出現「排程成功」的訊息，並顯示明日預定的執行時間。
![Imgur](https://i.imgur.com/0t1VnFx.png)
5. 本專案有設計查詢資料庫的功能，透過執行下列程式碼，先建立Covid19類別物件，接著與SQL資料庫進行連接，最後執行Select的查詢語法。
![Imgur](https://i.imgur.com/sO9lY8S.png)
6. 查詢結果如下，如查詢成功將會出現「查詢完畢」的訊息。
![Imgur](https://i.imgur.com/RYbATui.png)




## 四、PowerBI資料分析
[Covid19資料分析_PowerBI連結](https://app.powerbi.com/view?r=eyJrIjoiOTc1MjkxZDItNDNjZS00OWVlLWI3N2UtYjM4MDgyMWE5ZjFiIiwidCI6ImY3Njk4MThiLWI2MmYtNGY0ZS04OGJkLWI0MjJlOTA3YTkwMyJ9)

本章節主要呈現出Covid19資料在PowerBI的應用，透過清晰簡易的互動式圖表，很快知道不同時間下的感染趨勢與人口組成，達到數據分析很重要的目的-**「讓人容易理解數據」**。本專案的PowerBI圖表的資料來源來自於政府開放平台的「地區年齡性別統計表-嚴重特殊傳染性肺炎-依個案研判日統計」的API資料，在原始資料中有幾個重要的統計變項，如個案研判日、縣市、年齡層、是否為境外移入等等。本專案將分析主軸放在「時間」這個變項，在圖表中是由Covid19_確診個案時間軸來控制，這個時間軸除了年之外，還可以到不同季度、不同月份。透過這個時間軸的操控，可以讓我們看到其他視覺化圖表的趨勢變化。例如不同縣市感染人口的分布；境內外感染人數的比例；感染人口的年齡層分布；整體確診數的趨勢變化以及確診人數的地理分布等。以下將逐一介紹不同變項與時間的趨勢，並提供可能的分析解釋。

**1.境外移入為主的感染趨勢：2020-2021/04**

這時期境外移入雖然較多，然而在確診人數上並沒有大幅爆發的跡象，顯示台灣在邊境管制上成效不錯。在2020年Covid19剛爆發時，實際上境外移入比境內移入還多，甚至到2021年四月止，境外移入仍有九成比例。而在這些境外移入的人口組成，多半是以年輕族群為主，集中在20-29與30-39這區間，推測有多半是留學回來或是商務人士居多。然而有趣的是雖然這段時間境外移入較多，卻沒有境外移入確診數大爆發的問題。實際上在這時間區間境外移入確診人數總共約1000人左右而已，甚至確診人數最多的是在2020年3月有258人，而後都是十位數最多到100多人。另一方面，這時期的本土感染數不到百人，感染人口也多半集中在北部地區。這代表當時台灣政府邊境管制成效不錯，有效控制境內外的感染人數。

**2.境內感染為主的高峰期與控制期：2021/05-2021/12**

這時期因大量本土病例多點爆發，造成境內感染數大幅增加，然而在同年度九月境內感染再次比境外感染還少，顯示出台灣本土疫情雖然爆發猛烈，然而在後續的疫苗施打與防疫政策下，仍在四個月後重新控制疫情。這段期間遭逢萬華茶室與諾富特事件的影響，先是造成北部地區大量染疫人口增加，而後又因為苗栗電子廠、彰化葡萄農與獅子會等事件推波助瀾下，造成全台疫情遍地開花。從縣市數據來看，當時染疫最多前幾名為新北市、台北市、桃園市、苗栗縣與彰化縣，主要是因為都是重要染疫事件的核心地區或周邊地區。有趣的是這波染疫多半是中高齡族群為主，像新北市與台北市大多集中在40歲以上人口，唯獨苗栗縣因為是較為年輕的外籍移工染疫所以年齡層偏低。儘管說台灣這波疫情來得又猛又烈，造成了經濟與生活的衝擊，但是這波疫情並沒有蔓延太久。到了同年度九月境內感染重新回到百位數以下，並且與境外移入進行黃金交叉，直至去年12月都還是保持境外比境內多的趨勢。這也代表了疫情在後續的疫苗施打與防疫政策下，得到有效的控制。

**3.境外感染為主但境內感染微幅增加的趨勢；2022/01-2022/03**

到了今年，雖然有維持境外多於境內的趨勢，然而本土感染也重新回到百人以上的規模，甚至境外移入創下歷史新高，顯示出儘管疫情先前得到控制，但Covid19是傳染力極高的病毒，仍有可能一個不注意讓疫情再次死灰復燃。從去年十二月底爆發桃園歌友會群聚事件以來，台灣各地陸陸續續有群聚事件出現，像是高雄港區、物流公司等，讓整個本土病例從原先百人以下又回到400-300人規模。其中又以桃園市、高雄市與新北市為前三高的確診地區，與先前的大爆發不同的是，這次的本土感染都集中在青壯年人口居多。而比較特別的是今年境外感染人數(4196人)遠遠超過前兩年的規模(2020年743人；2021年1703人)，這可能跟國外疫情反覆爆發跟Covid19病毒不斷變種有關，造成回國人口染疫機率較高。所以從今年這兩個月下來，還是可以發現Covid19病毒傳染能力依舊非常強，不論是境外還是境內的感染人數都有明顯成長，政府與民眾仍需要做好各種防疫的準備，防範下一波可能的大感染出現。


## 五、參考資料
本章節提供製作專案過程所使用的參考資料，供讀者未來做類似專案的參考。

**1.專書**

林俊瑋、林修博，2018，《Python網路爬蟲與資料分析入門實戰》。新北市:博碩文化

**2.網路資料**

[Logging HOWTO](https://docs.python.org/3/howto/logging.html)

[Python logging 日誌用法與範例](https://shengyu7697.github.io/python-logging/)

[pymssql module](https://pymssql.readthedocs.io/en/stable/ref/pymssql.html)

[threading timer](https://docs.python.org/3/library/threading.html#timer-objects)

[如何定時執行程式，來將每日例行工作自動化。](https://ghl0506.medium.com/python-sikuli-%E5%A6%82%E4%BD%95%E5%AE%9A%E6%99%82%E5%9F%B7%E8%A1%8C%E7%A8%8B%E5%BC%8F-%E4%BE%86%E5%B0%87%E6%AF%8F%E6%97%A5%E4%BE%8B%E8%A1%8C%E5%B7%A5%E4%BD%9C%E8%87%AA%E5%8B%95%E5%8C%96-b2cceb68220d)

[sched Event scheduler](https://docs.python.org/3/library/sched.html)

[PowerBI教學影片](https://www.youtube.com/watch?v=9RcQUhlIb_Y)

## 六、版權聲明
版權所有 © 2022 codyxyz8

