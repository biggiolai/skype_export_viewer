# skype_export_viewer

這個 HTML 檔案是一個用於解析和瀏覽從 Skype 導出的聊天記錄的網頁應用程式。它允許使用者選擇一個 messages.json 檔案（Skype 導出檔案的一部分），然後將其內容解析並以更易讀的格式顯示在網頁上。

以下是這個檔案的主要功能和運作方式的詳細說明：

主要功能:

檔案上傳 (File Upload):

網頁提供了一個檔案上傳表單 (<form id="jsonFile">)，讓使用者可以選擇 messages.json 檔案。
只接受 .json 檔案 (<input type="file" accept=".json" id="fileinput">)。
檔案讀取和解析 (File Reading and Parsing):

當使用者選擇檔案並點擊 "Load" 按鈕 (<input type="button" id="btnLoad">) 時，會觸發 JavaScript 程式碼。
程式碼使用 FileReader API 讀取 JSON 檔案的內容。
讀取完成後，使用 JSON.parse() 將 JSON 字串解析為 JavaScript 物件。
資料處理 (Data Processing):

程式碼檢查解析後的 JSON 資料是否包含必要的資訊，例如 userId、conversations 和 exportDate。
它過濾掉不必要的對話，例如 ID 為 "ALL" 或以 /@cast.skype$ 結尾的 ID。
將解析出的資料儲存在 window.Skype 物件中，方便後續使用。
將對話清單、匯出日期等資訊呈現在網頁上。
對話清單顯示 (Conversation List Display):

程式碼會建立一個對話清單 (<ul class="conversations">)，每個對話都是一個清單項目 (<li>)。
每個對話項目顯示對話的參與者姓名 (c(e[n]))、訊息數量和最後一次訊息的時間。
每個對話項目都是一個超連結，可以點擊查看該對話的詳細內容。
對話內容顯示 (Conversation Content Display):

當使用者點擊一個對話項目時，會觸發 m 函數。
m 函數會根據所選的對話索引，從 window.Skype.conversations 中獲取該對話的訊息列表。
它會清空訊息顯示區域 (<ul class="messages">)，然後將該對話的每則訊息建立成一個清單項目 (<li>)。
每則訊息包含發送者、時間戳和訊息內容。
對話內容的顯示包含header,與訊息列表.
樣式和介面 (Styling and Interface):

使用 CSS (<style>) 定義網頁的樣式，包括背景顏色、字體、排版等。
介面分為兩個主要部分：
左側 (<div class="left">): 顯示對話清單。
右側 (<div class="right">): 顯示選定對話的內容。
最初顯示一個step-1的form,當成功讀取檔案後會顯示step-2的對話清單與選定的對話內容.
安全性 (Security):

使用 Content-Security-Policy 標頭限制資源載入，以提高安全性。
base-uri 'none';frame-ancestors: 'none';block-all-mixed-content 等設定可以增強安全。
依賴:

此html不依賴任何外部資源，所有程式碼都在這個html檔案內.
總結：

這個 HTML 檔案是一個獨立的網頁應用程式，不需要伺服器，可以直接在瀏覽器中執行。它通過解析 Skype 導出的 messages.json 檔案，讓使用者可以更方便地瀏覽和查看他們的 Skype 聊天記錄。它巧妙的利用前端技術完成了對一個json檔案的資料處理和呈現.
