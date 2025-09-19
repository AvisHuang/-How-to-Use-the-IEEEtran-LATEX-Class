# How-to-Use-the-IEEEtran-LATEX-Class
##用途：IEEEtran 幫助作者快速排版出符合 IEEE 格式的專業論文。

## 進階操作技巧可參閱：bare_adv.tex
# 介紹

##文字大小
10pt:絕大多數 IEEE 論文採用

9pt:簡報/通訊/短文使用

11pt:一些會議的初稿投稿要求

#IEEE Computer Society 的出版品用的是bp，不是傳統的pt。有大小差異
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
特點:\author 欄位要輸入完整形式（不像會議模式那樣簡寫）、啟用 \IEEEtitleabstractindextext 指令 → 摘要與索引詞為單欄排版、\IEEEauthorrefmark 會產生阿拉伯數字的作者單位符號。

## 紙張
通常要選letterpaper(8.5 × 11 英吋，美國標準，IEEE 預設)
注意：要確保 .tex 與後處理 (PS, PDF) 使用相同紙張設定，不然常會出現邊界錯誤。

## 附錄
romanappendices → 附錄預設是 A, B, C…；加這個選項可改成 I, II, III…。

# 
