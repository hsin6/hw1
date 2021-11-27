# 計算機概論實習作業
## Git
1. 免費、開源專案管理工具
2. 紀錄版本更動情形
3. 分散式系統
4. 可離線工作
5. 多人合作專案時
***
## Linux
1. 作業系統之一
2. 提供所有最基本的功能，像是鍵盤輸入、螢幕輸出，記憶體管理
3. 相對比較不耗資源的系統，常用來處理巨量資料
4. 雲端部署時常使用
***
## Linux各個目錄存放的內容
- /:根目錄，所有檔案從此開始，只有root使用者具該目錄的許可權
- /root:該目錄為系統管理員，也稱作超級許可權者的使用者主目錄
- /bin: 存放著經常使用的命令
- /boot: 系統啟動時必須讀取的檔案，包括系統核心
- /home: 存放普通使用者的家目錄，每個使用者都有自己的家目錄
- /etc: 放置與系統設定、管理相關的檔案
- /usr: 很重要的目錄，使用者的應用程式和檔案都放在這個目錄下，類似windows下的program files目錄
- /media: 可用來作為光碟、軟碟片、隨身碟與其他分割區的自動掛載點
- /tmp: 供全部使用者暫時放置檔案的目錄
- /var: 系統執行時，內容經常變動的資料或暫存檔(log file)，都會放置在這個目錄裡
***
## Linux指令
### 絕對/相對路徑的移動
- 絕對路徑：路徑的寫法「一定由根目錄/寫起」
  例如：/usr/share/doc 這個目錄。
- 相對路徑：路徑的寫法「不是由/寫起」
  例如由/usr/shate/doc到/usr/share/man底下時，寫成「cd../man」，
  相對路徑意指「相對於目前工作木錄的路徑！」
- 比較特殊的目錄
  - · ：代表此層目錄
  - ··：代表上一層目錄
  - － ：代表前一個工作目錄
  - ～ ：代表「目前使用者身分」所在的家目錄
- 指令
  - cd: 變換目錄
  - pwd: 顯示目前的目錄的所在位置
  - ls: 顯示目錄下的所有檔案
  - touch: 建立檔案
  - cp: 複製
  - cat: 查看檔案內容
  - vi: 編輯檔案
  - mkdir: 建立一個新目錄
  - mkdir -p: 同時建立多個目錄
  - rmdir: 刪除一個裡面是空的空目錄
  - rm: 刪除檔案
  - rm -r: 強制刪除
  - mv: 移動、重新命名
### 查看檔案目錄資訊
- ls -l: 顯示目錄下的所有檔案詳細資訊
- ls -al: 顯示目錄下的所有檔案（包含隱藏檔）詳細資訊
### 更改檔案或目錄權限
- chown：可修改檔案或目錄的擁有者及群組
### 更改使用者權限
- chmod可控制檔案如何被他人調用
  &rarr; chmod[-cfvR][--help][--version]mode file...
- mode許可權設定字串
  &rarr; [ugoa...][[+-=][rwxX]...][,...]
- 檔案file1.txt 設為所有人皆可讀取
  - chmod ugo+r file1.txt
- 將檔案file1.txt與file2.txt設為該檔案擁有者可以執行：
  - chmod ug+w,o-w file1.txt file2.txt
- 將ex1.py設為只有該檔案擁有者可以執行：
  - chmod u+x ex1.py
- 將目前目錄下的所有檔案與子目錄皆設為任何人可讀取：
  - chmod -R a+r*
- chmod a=rwx file == chmod 777 file
- chmod ug=rwx,o=x file -- chmod 771 file
### 編輯文檔
-nano
  -Ctrl C:顯示游標所在
  -Ctrl W:查詢命令，按下後會跳轉到沒行的反白位置，輸入要查詢的內容再按enter即可
- vi/vim(vim相當於vi的升級版)
  - 一般模式：可使用上下左右進行游標宜動、刪除字元及複製貼上檔案資料。
  - 編輯模式：編輯文字
    - i鍵可進入編輯模式
    - Esc鍵退出編輯模式
  - 命令列模式（！為「強制」的意思）
    - :w &rarr; 將編輯的資料寫入硬碟檔案中
    - :w! &rarr; 若檔案屬性為「只讀」時，強制寫入該檔案
    - :q &rarr; 離開
    - :q! &rarr; 強製離開不儲存檔案
    - :wq &rarr; 儲存後離開
    - :wq! &rarr; 強制儲存後離開
    - :w[filename] &rarr; 將編輯的資料儲存成另一個檔案
    - :r[filename] &rarr; 在編輯的資料中，讀入另一個檔案的資料
    - :wq &rarr; 儲存後離開
    - :n1,n2 w[filename] &rarr; 將n1到n2的內容儲存成filename這個檔案
### 複製檔案或目錄
- cp: 複製檔案或目錄
- 指令：cp -參數 來源檔案 目錄檔案
- 參數：
  -a:- pdr
  -d: 若來源為連結黨的屬性，複製連結檔屬性而非檔案本身
  -i: 如要複製過去的位置已經有相同檔案，會在覆蓋前詢問是否持續進行
  -p: 將檔案本身屬性（權限、所有者、時間）同時複製過去（多用於備份）
  -r: 針對目錄下檔案做遞歸複製（整個目錄下每一個檔案複製到你想要的位置）
  -s: 複製成符號連結檔（symbolic link）（複製成捷徑檔）
###各壓縮的差別
- 需要在記憶體很小的機器（如小於 128MB）上解壓縮時，則選擇 gzip 格式。
- 需要在很簡單、沒有什麼工具可用的機器解壓縮時，則選擇 gzip 格式。
- 需要節省網路頻寬、縮短下載所需要的時間時，則選擇 xz 格式。
- 需要有最好的壓縮率時，則選擇 tar.xz  格式。
### 壓縮檔案
- gzip
  - 壓縮：gzip FileName
  - 解壓縮：
    -  gunzip FileName.gz
    -  gzip -d FileName.gz
- xz
  - 壓縮:xz -z FileName
  - 解壓縮:xz -d FileName
- tar.gz
  - 壓縮:tar -zcvf FileName.tar.gz DirName
  - 解壓縮:tar -zxvf FileName.tar.gz
### 檔案搜尋
- find [path][option][action] filename
  - option
    - -size EX: 找出大於500M的檔案 &rarr; -size +500M
    - -name EX: 找出為照片的檔案 &rarr; -name "*.jpg"
    - -type EX: -type f &rarr; 一般檔案; -type d &rarr 一般目錄
    - -user EX: 同時找兩個擁有者的檔案 &rarr; -user user1 -o -user user2
  - action -exec
    - ls
    - print
- which filename
  - -a:系統會顯示所有被找到的令執行檔之完整路徑
  - -n<文件名長度>指定文件名長度，指定的長度必須大於或等於所有文件中最長的文件名。
  - -p<文件名長度>與-n參數相同，但此處的<文件名長度>包括了文件的路徑。
  - -w: 指定輸出欄位的寬度。
  - -v: 顯示版本訊息。
### 檔案內容查閱
- cat 從第一行顯示檔案內容、形成新檔案
  - cat -n file1>file2 &rarr; 把file1的檔案內容加上行號後輸入file2檔案
    - -n &rarr; 由1開始對所有輸出的行數編號
    - &gt; &rarr; 將多個文件覆蓋到目標文件中
    - &gt;&gt; &rarr; 將多個文件追加到目標文件中，不覆蓋
- tac 從最後一行開始顯示
  - tac -r -s 'x\|[^x]'test.log &rarr; 一個接著一個字符的反轉一個文件
    - -r &rarr; 將分隔符號作為基礎正規表達是處理
    - -s &rarr; 使用String做為分隔代替默認的換行符號
- more 一頁一頁的顯示檔案內容
  - more +20 testfile &rarr; 從第20行開始顯示testfile的文檔內容
    - ENTER: 向下n行(default為1行)
    - Ctrl+F/SPACE: 向下滾動一屏
    - Ctrl+B: 返回上一屏
- less與more類似，顯示檔案是允許用戶既可以向前又可以向後翻頁閱讀檔案
  - pa -ef|less &rarr; ps查看進程信息並通過less分頁顯示
    - j &rarr; 下一行
    - k &rarr; 上一行
    - G &rarr; 移動到最後一行
    - g &rarr; 移動到第一行
- head 取出前面幾行（預設10行）
  - -n: 後面接數字，代表幾行
- tail
  - -n: 後面接數字，代表幾行
  - -n +20: 只想列出20行以後的資料
***
## Linux背景知識
### 使用者與群組
- 關於身份：
  - 身份分類：
    - user(owner)
    - group
    - others
  - 群組(group)的主要用意：
    - 將帳號歸類，有助於類似專案開發
    - 每個使用者均可加入多個群組
- 關於身份類別：
  - 系統管理員：root
  - 一般帳號：
    - 系統帳號（用於系統帳號的工作）
    - 一般使用者帳號（用於一般使用者登入用）
### 資料傳輸
| OSI模型階層 | OSI模型 | TCP/IP | 協定 |
| --- | --- | ------ | ----- |
| 第七層 | 應用層 | 應用層 | HTTP、FTP、DNS |
| 第六層 | 展現層 |       |               | 
| 第五層 | 會談層 | | |
| 第四層 | 傳輸層 | 傳輸層 | TCP、UDP |
| 第三層 | 網路層 | 網際網路層 | IP、ICMP、IPX |
| 第二層 | 資料連接層 | 網路存取層 | 乙太網、Wi-Fi、PPP |
| 第一層 | 實體層 | | |

### Port
通訊埠號是 TCP/UDP 與上層通訊的通道，當 TCP/UDP 要傳送訊息時，會指定要由哪一個通訊埠號來接收。一些常用的服務會使用特定的埠號來等待要求的訊息。埠號是由 16 個位元所組成的號碼，0 ~ 255 為保留號碼，256 ~ 65535 則可自行設定
*** 
### TCP/IP
點對點的連結機制，將資料應該如何封裝、定址、傳輸、路由以及在目的地如何接收，都加以標準化。它將軟體通信過程抽象化為四個抽象層，採取協議堆疊的方式，分別實作出不同通信協定。協定套組下的各種協議，依其功能不同，被分別歸屬到這四個階層之中，常被視為是簡化的七層OSI模型。
***
### 網路相關
- route
&rarr; Destination, Genmask：完整的網域
&rarr; Gateway：這個網域是從哪個Gateway連接出去的，0.0.0.0表示這個路由是從本機傳送，有IP的話，
                代表需要經過路由器才能傳出去
&rarr; Iface：網路卡介面
### 網路相關
- route
  - add : 新增一條路由規則
  - del : 刪除一條路由規則
  - -net : 目的地址是一個網路
  - -host : 目的地址是一個主機
  - target : 目的網路或主機
  - netmask : 目的地址的網路掩碼
  - gw : 路由資料包通過的閘道器
  - dev : 為路由指定的網路介面
- ping
  - 常用網路檢測工具，可藉由發送 ICMP ECHO_REQUEST 封包，檢查自己與特定設備之間的網路是否暢通，
    並同時測量網路連線的來回通訊延遲時間（round-trip delay time）。
    - -n：參數指定封包數→EX：ping -n 10 blog.gtwang.org
    - -t：持續監看網路是否正常→EX：ping -t blog.gtwang.org
    - -4/-6：IPv4/IPv6
    - -c：指定Ping次數→EX：ping -c 4 blog.gtwang.org
    - -s：指定發送的數據字結數→EX：ping -s 1024 facebook.com
    - -i：指定收發資訊間隔時間→EX：ping -i 0.4 facebook.com
- 影響網路速度的因素:
  - 延遲（Latency）：封包從來源端至目的端中間所花的時間
  - 頻寬（Bandwidth）：傳輸媒介的最大吞吐量
- 網路延遲（Latency）的組成元素:
  - propagation delay：封包在網路線上傳輸所花費的時間，與網路線上電子訊號跑的速度有關， <br> 這個時間就是距離除以訊號傳送速度所得到的數值。
  - transmission delay：網路卡將資料傳送到網路線上所花的時間，與網路設備的傳送速度有關。
  - nodal processing delay：路由器處理封包表頭、檢查位元資料錯誤與尋找配送路徑等所花費的時間。
  - queuing delay：路由器因為某些因素無法立刻將封包傳送到網路上，造成封包暫存在佇列中等待的時間。
- netstat
![image](https://user-images.githubusercontent.com/91867022/143666877-49b8296d-d320-4bcd-9214-8ab628bf7228.png)
![image](https://user-images.githubusercontent.com/91867022/143666895-9a927f14-f5d3-4676-a8e9-2beb309c1356.png)
  - 查看端口是否被占用：netstat -al grep 3306
  - 查看數據包統計信息：netstat -s
  - 查看路由信息：netstat -r
