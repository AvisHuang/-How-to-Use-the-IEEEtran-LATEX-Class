# How-to-Use-the-IEEEtran-LATEX-Class
#用途：IEEEtran可幫助作者快速排版出符合 IEEE 格式的專業論文。

進階操作技巧可參閱：bare_adv.tex

# II.CLASSOPTION

## 文字大小
10pt:絕大多數 IEEE 論文採用

9pt:簡報/通訊/短文使用

11pt:一些會議的初稿投稿要求

*IEEE Computer Society 的出版品用的是bp，不是傳統的pt。有大小差異
10pt Computer Society 期刊，實際字體大小是 9.5 bp。

但IEEEtran 會自動調整字體大小，根據不同模式 (journal, conference, technote 等)，讓輸出符合 IEEE 標準。

## IEEEtran 的三個特殊模式：comsoc、compsoc、transmag
1.Comsoc Mode (IEEE 通訊學會格式)
影響；只修改數學字體，讓它更接近 Times Roman 正文字體。
<img width="824" height="417" alt="image" src="https://github.com/user-attachments/assets/397ebba3-05f6-4b28-b2d3-d616f4200eca" />
注意事項:不需要載入 amssymb.sty及不要載入 newtxtext.sty

2.Compsoc Mode (IEEE 計算機學會格式)
影響:正文字體從 Times Roman → 改為 Palatino/Palladio（只限非會議模式）

調整頁邊距、與一般會議模式差異不大，但保留了阿拉伯數字的章節編號。

3.Transmag Mode(適用於 IEEE Transactions on Magnetics 與 IEEE Magnetics Letters)
特點:\author 欄位要輸入完整形式（不像會議模式那樣簡寫）

啟用 \IEEEtitleabstractindextext 指令 → 摘要與索引詞為單欄排版

\IEEEauthorrefmark 會產生阿拉伯數字的作者單位符號。

## 紙張
通常要選letterpaper(8.5 × 11 英吋，美國標準，IEEE 預設)

注意：要確保 .tex 與後處理 (PS, PDF) 使用相同紙張設定，不然常會出現邊界錯誤。

## 附錄
romanappendices → 附錄預設是 A, B, C…；加這個選項可改成 I, II, III…。

## nofonttune
因為IEEEtran 會自動優化字間距，nofonttune可以關閉這個優化



# III.CLASSINPUT、CLASSOPTION 與 CLASSINFO 控制

## classinputs
可用的CLASSINPUTs函式有：

\CLASSINPUTbaselinestretch → 設定文件的行距

\CLASSINPUTinnersidemargin → 設定內側（裝訂邊）邊界

\CLASSINPUToutersidemargin → 設定外側邊界

\CLASSINPUTtoptextmargin → 設定上邊界

\CLASSINPUTbottomtextmargin → 設定下邊界

<img width="618" height="294" alt="image" src="https://github.com/user-attachments/assets/e37f910f-74d0-4f6d-8bbd-fd606379d126" />

CLASSINPUTs預設參數

\headheight = 12pt

\headsep = 0.25in

\footskip = 0.4in

<img width="473" height="164" alt="image" src="https://github.com/user-attachments/assets/f32db80c-200c-437a-8488-6b7dc309fb09" />

**CLASSINPUT 適合進階使用者客製邊界/行距，但要小心，因為這樣做可能不再符合 IEEE 投稿規範。

## classoptions

CLASSOPTIONs是一組由 IEEEtran 自動設定的\if 條件，依照使用者在\documentclass 中選的選項來決定，可以方便在文件中做條件式編譯。

<img width="562" height="291" alt="image" src="https://github.com/user-attachments/assets/de85d6e3-84e5-48a0-83dc-7f70ef020919" />

*限制：這些變數是唯讀的，不能手動改，因為IEEEtran本身用它們來控制格式。

## CLASSINFOs
提供文件環境資訊（是否 PDF、行距、紙張大小等），方便查詢。

字體行距資訊：

\CLASSINFOnormalsizebaselineskip → 正文字體的行距值。

\CLASSINFOnormalsizeunitybaselineskip → 在 \baselinestretch=1 時的行距值。

頁面尺寸：

\CLASSINFOpaperwidth

\CLASSINFOpaperheight
→ 會輸出完整尺寸（含單位），例如 8.5in, 297mm







