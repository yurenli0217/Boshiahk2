# Boshiahk2 - 嘸蝦殼2
免安裝的嘸蝦米輸入工具，以 AutoHotkey V2 開發。  
本程式會攔截鍵盤事件，所以會被某些掃毒軟體誤判，在下載頁面中有提供線上掃毒結果供參考。

# 緣起
嘸蝦米輸入法是一個很好用的輸入法，但並不是每台電腦都有嘸蝦米輸入法。  
使用嘸蝦米輸入法的人都會遇到一個問題，換了一台電腦就不一定有嘸蝦米輸入法可用，大大影響工作效率。  
偽蝦米輸入法雖然好用，但已經沒有在維護，在新的程式上開始有不相容的情況發生…  
為了方便在任何電腦上都能使用，我興起了一個念頭，使用 AHK 來開發一個免安裝的嘸蝦米輸入工具，讓我能夠在任何電腦上使用嘸蝦米輸入法打中文，並且也讓嘸蝦米的使用者在遇到輸入法的問題時，能夠有另一個選擇。  
只要 AHK 還能用，這個工具就會一直存在，持續維護。

### 更新 2025-04-05
- 跟隨游標功能修正：當坐標超出螢幕時會調整回來焦點視窗所在的螢幕內，但調整回來螢幕內的位置無法固定，目前的做法是「能看到」輸入介面做為解決方案。
- 程式內部運作調整。

### 更新 2025-03-31
- 新增跟隨輸入提示游標(Caret)的功能，`main.ini` 中新增設定值 `Floating`，設定介面中亦可設定。
- 跟隨游標的範例如下圖，目前測試 Word、Excel、Line、Chrome、一般文字編輯器 能正常運作。  
![image](Images/Floating.gif)

### 更新 2025-03-30
- 修正內部錯誤
- 加入自簽憑證，目前線上掃毒軟體沒有誤判病毒，這樣誤判機率應該就會變小了
  
### 更新 2025-03-22
- 修改注音模式的輸入方式 [說明](#注音模式)
- 調整送英文的熱鍵 [說明](#在中文輸入模式下可配合以下熱鍵直接送出英文)

### 更新 2025-03-09
- 嘗試修改剪貼簿模式下的文字預覽框，可以在雙螢幕下顯示在焦點視窗所在的螢幕中
  
### 更新 2025-03-02
- `Style.ini` 中新增剪貼簿模式文字編輯框的字體相關設定

# 下載與使用
- 直接到 [Release](https://github.com/yurenli0217/Boshiahk2/releases) 頁面下載 `Boshiahk2.zip` 即可。
- 建立一個資料夾，例如 `Boshiahk2`。將 `Boshiahk2.zip` 在此資料夾內解壓縮，執行 `Boshiahk2.exe` 即可開始使用。
- 資料夾與檔案結構如下圖：  
![image](Images/FileList.png)
- `Table`資料夾內放的是表格檔，`Config`資料夾放的是設定檔。
- 程式執行時，會載入 `Config\LastPosition.ini` 儲存的座標位置，輸入介面有變更位置時會更新此檔案。刪除此檔案，執行時輸入介面會以預設值顯示在螢幕左下角。
- 若是有多個螢幕時，輸入介面會自動移到焦點視窗所在的螢幕，介面會顯示在一樣的相對位置。

# 介面範例
![image](Images/Demo.gif)  
![image](Images/Floating.gif)  
![image](Images/Settings.png)  
### 推薦使用字體：[霞鶩文楷](https://github.com/lxgw/LxgwWenKai)、[全字庫楷體](https://data.gov.tw/dataset/5961)

## 系統輸入法和語系設定
嘸蝦殼輸入介面的運作屬外掛方式輸入中文，若要正常運作，系統內建的輸入法要先進行設定。  
系統的語言設定和輸入法設定可以參照以下兩種方式:  
1. 鍵盤配置設定成英文  
![image](Images/Lang1.png)  
此模式下使用外掛式中文輸入最穩定，但若是遇到某些應用程式需要系統輸入法在中文語系下才能輸入中文時，就必須要使用第二種方法。

2. 輸入法設定成倉頡英數模式(非必要時不建議)  
![image](Images/Lang2.png)  
設定成倉頡輸入法，可以配合「修正模式」的設定，程式會自動監控將系統輸入法狀態維持在英數模式。  
例如 Excel 中的 VBA 程式編輯，就會需要用到這種方式來輸入中文。
```diff
- 第二種方法在 Line 輸入完標點符號時，後面送出的字會變成重複送一次一樣的標點符號，之後才能正常輸入中文。
- 若要在 Line 中輸入標點符號，記得改回第一種方式。
```

## 熱鍵功能
#### 除了輸入法的開啟/關閉，其它的熱鍵皆在輸入法啟用時才會作用。
- `Shift-Space`: 半形/全形 輸入。
- `Shift+,.` 或 `Pgup/Pgdn`: 在多頁選字時，切換上下頁。
- `Shift+vrsf`: 有候選字時，可利用此熱鍵選字，對應編號 1~4 的候選字

- `Ctrl-Alt-B`: 開啟自訂字詞檔。
- `Ctrl-Alt-C`: 查看上一次送字之拆碼。
- `Ctrl-Alt-G`: 重複上一次送出的字。
- `Ctrl-Alt-K`: 複製一個文字後，按下此熱鍵可以顯示該字的所有拆碼。
- `Ctrl-Alt-L`: 切換送字後顯示3碼以內的拆碼
- `Ctrl-Alt-O`: 輸入介面位置重設。
- `Ctrl-Alt-P`: 切換/離開 注音模式。
- `Ctrl-Alt-R`: 重新載入程式。
- `Ctrl-Alt-X`: 結束程式。
- `Ctrl-Alt-Shift-C`: 查詢焦點視窗的 Class Name。
- `Ctrl-Alt-Shift-T`: 查詢焦點視窗的視窗標題。

#### 在中文輸入模式下，可配合以下熱鍵直接送出英文：
 - `Enter`: 送出全小寫的英文
 - `Shift-Enter`: 送出全大寫的英文
 - `Ctrl -Enter`: 送出首字大寫的英文

## 注音模式
- 利用熱鍵 Ctrl-Alt-P 可以切換注音模式與正常模式。
- 在注音模式下，可連續以注音輸入中文。
- 注音模式下的選字方式改成`Alt-0`~`Alt-9`

## 查詢功能
- 萬用碼查碼: 先輸入前導碼`[`，再輸入字根，不確定字根用`.`來代表。如`[A..P`，會顯示字碼首碼為`A`、尾碼為`P`、以及字根數為「四碼」的選字。
- 查詢注音與同音字: 先輸入字根碼，出現選字後，用「Ctrl + 選字編號」選擇要查的注音，會出現該字的所有注音，此時可再進一步選擇注音再查同音字。

## 修改 INI 設定檔
- `Main.ini`已可以透過設定介面修改設定，也可手動修改設定檔
- 設定檔中已有針對各項設定值簡述用法。
- 使用程式前可先詳細參閱 INI 檔內說明。

```diff
- 若 INI 檔文字編碼格式不是 UTF-16LE，程式將無法正常讀取設定，用記事本開啟另存成 UTF16-LE 即可。這是 Windows 本身的限制。
```

## FontName 與 FontNameExt 使用範例
- 使用的方式用全字庫來說明，全字庫正楷體中有兩個檔案名稱:  
`TW-Kai-98_1.ttf`  
`TW-Kai-Ext-B-98_1.ttf`  
其中`TW-Kai-Ext-B-98_1.ttf`儲存的文字是在Unicode `0x20000` 開始的文字，首先將字型安裝到系統，然後再使用以下設定值  
`FontName = 全字庫正楷體`  
`FontNameExt =全字庫正楷體 Ext-B`  
這樣在 Unicodde 0x20000 以後的文字就使用擴展字集區的字型了。

## 熱鍵功能
- 在`Hotkey.ini`中可自訂熱鍵，方便送出一連串的鍵盤動作。  
- 熱鍵的對應可參考 AHK 官網的鍵盤對應表。舉例如下:  
`^c||||^v `  
代表先送出Ctrl-c，然後暫停200ms，再送出Ctrl-v，其中`|`符號代表間隔50ms，上面有4個，所以就變成了200ms。

## 加字加詞額外功能
- 加字加詞檔中，可以用來呼叫外部程式。  
- 例: `,calc# calc`  
輸入「,calc」按下空白鍵後，即執行 Windows 內建小算盤。  
- 例: `,drv# c:\`  
輸入「,drv」按下空白鍵後，會用檔案總管開啟路徑C:\。  

## 自動判定剪貼簿送字
- 設定檔在 `Config\ClipAuto.txt`
- 檔案內容為視窗的 Class Name 清單，或是視窗標題，程式執行時會讀取該檔。
- 若焦點視窗有符合 Class Name 或視窗標題，就會自動以剪貼簿送字。
- 可以用上述的熱鍵功能取得焦點視窗的 Class Name 或視窗標題。
- 若想要符合的是 Class Name，每一行用*開頭，後面接 Class Name，如`*Notepad`，只要 Class Name 為 Notepad 的都會自動用剪貼簿貼上。  
- 若想要符合的是視窗標題，每一行直接輸入視窗標題包含的字串，如`批踢踢實業坊`，視窗標題只要包含此字串，就會自動以剪貼簿送字。  
- 視窗標題也可以支援正規表示法比對字串，這是比較進階的用法，有興趣的可以試試。視窗標題比對時的英文文字不分大小寫。
- 使用模式4跟模式5時，在輸入文字過程會自動顯示一條文字框，輸入完按下 Enter 鍵將會以剪貼簿模式貼上輸入的文字內容，請參閱下圖。此兩種模式在特定的商業遠端遙控軟體會使用到。
![image](Images/ClipMode45.jpg)

## 造訪數
(自2025/03/29重置)  
![Hits](https://visit-counter.vercel.app/counter.png?page=boshiahk2)
# 歷史更新
[連結](https://github.com/yurenli0217/Boshiahk2/blob/main/History.md)
