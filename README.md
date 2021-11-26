# 計算機概論實習作業
## Linux各個目錄存放的內容
- /:根目錄，所有檔案從此開始，只有root使用者具該目錄的許可權
- /root:該目錄為系統管理員，也稱作超級許可權者的使用者主目錄
- /bin:
- /boot:
- /home:
- /etc:
- /usr:
- /media:
- /tmp:
- /var:
## Linux指令-壓縮檔案
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
## Linux指令-檔案搜尋
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
## Linux指令-檔案內容查閱
