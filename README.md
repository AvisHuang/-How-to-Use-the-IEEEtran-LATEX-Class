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


# IV. THE TITLE PAGE

標題頁區塊由 LaTeX 的 \maketitle 指令生成。

## A.Paper Title

用 \title{...} 定義

e.g.\title{A Heuristic Coconut-based Algorithm}
規範：

1.標題大部分單字首字母需大寫。

2.可以用 \\ 斷行來讓標題行長度更均衡。

***禁止：不要在標題中使用數學公式或特殊符號。

## B.Author Names

用 \author{...} 定義。

e.g.

\author{
  Michael~Shell,~\IEEEmembership{Member,~IEEE,}
  
  John~Doe,~\IEEEmembership{Fellow,~OSA,}
  
  and~Jane~Doe,~\IEEEmembership{Life~Fellow,~IEEE}%
  
  \thanks{Manuscript received January 20, 2002; revised August 26, 2015. 
  
  This work was supported by the IEEE.}%
  
  \thanks{M. Shell was with the Georgia Institute of Technology.}%
  
}

重點說明：

1.\IEEEmembership{...} → 用來表示作者的 IEEE 或其他學會會員等級。

2.\thanks{...} → 用來加附註（如稿件日期、資助單位、作者單位）。

如果只是單行換行，可以在 \thanks 內用 \\

限制：\thanks 不能直接容納多段落。
→ 如果要分多段，必須多寫幾個 \thanks{...}。

3.~（non-breaking space） → 保持作者名字和稱謂間不換行。

  e.g.例：John~Doe,~\IEEEmembership{Member,~IEEE}

4.% → 避免 LaTeX 自動加空格。


## C.頁首標題

頁首標題是透過 \markboth{}{} 指令來設定的：

第一個參數：放置期刊名稱資訊。

第二個參數：放置作者名稱與論文標題。

e.g.\markboth{Journal of Quantum Telecommunications, Vol. 1, No. 1, January 2025}{Shell \MakeLowercase{\textit{et al.}}: A Novel Tin Can Link}

***

由於頁首標題文字會自動轉為大寫，若需要小寫文字，必須使用 \MakeLowercase{}。

Technote 論文不使用第二個參數。

## D.出版物識別標記

1.出版物識別標記放在標題頁，可用 \IEEEpubid{} 指令：

e.g.\IEEEpubid{0000--0000/00\$00.00 \copyright 2015 IEEE}

2.若使用，需在標題頁第二欄加 \IEEEpubidadjcol，防止文字與 ID 標記重疊。

3.草稿模式下，標記不會列印，但保留空間。

4.提交論文時可能尚無出版物 ID，但可用來預覽標題頁版面。

## E. 特別論文標示

1.特別論文標示（如邀請論文）可以透過以下指令設定：

\IEEEspecialpapernotice{(Invited Paper)}

2.有時還需要使用跨欄的空間（例如致敬語或 dedication [15]）。

IEEEtran 提供指令：
\IEEEaftertitletext{\vspace{-1\baselineskip}}

可用於插入文字或調整標題區與正文之間的間距。

#  V.摘要與關鍵詞

## 栽要

1.通常出現在 \maketitle 後的第一部分

2.使用環境

\begin{abstract}

摘要內容

\end{abstract}

3.摘要內容限制

一般不使用數學公式、特殊符號或引用

若需要粗體數學，可在摘要開頭加 \boldmath

## 關鍵詞

1.用於期刊與技術短文

2.使用環境

\begin{IEEEkeywords}

關鍵詞列表

\end{IEEEkeywords}

3.限制

不使用數學或特殊符號

# VI.章節

## 1.章節宣告方式

使用 LATEX 標準指令：

\section

\subsection

\subsubsection

\paragraph

## 2.章節編號規則

非 Compsoc(IEEE Computer Society) 模式：

  &nbsp;&nbsp;&nbsp;&nbsp;\section → 大寫羅馬數字（I, II, …）

  &nbsp;&nbsp;&nbsp;&nbsp;\subsection → 大寫英文字母（A, B, …）

  &nbsp;&nbsp;&nbsp;&nbsp;\subsubsection → 阿拉伯數字（1, 2, …）

  &nbsp;&nbsp;&nbsp;&nbsp;\paragraph → 小寫英文字母（a, b, …）

Compsoc 模式：

  &nbsp;&nbsp;&nbsp;&nbsp;只使用阿拉伯數字（1, 1.1, 1.1.1, …）

## 首字放大

1.期刊論文的第一個字母通常是大寫、放大並下降一行（drop cap）

2.第一個字的其他字母則一般為大寫

3.指令使用

\IEEEPARstart{W}{ith}

第一個參數：第一個字母（大寫、放大）

第二個參數：第一個字剩餘的字母

# VII.引用（Citations）

1.使用 thebibliography 環境或 BibTeX 建立文獻清單

2.文獻條目依引用順序編號，而不是依字母順序

3.論文標題僅首字母大寫（專有名詞除外）

4.未出版文章標註 “unpublished”，已接受但未刊出標註 “in press”

5.翻譯期刊：先給英文引文，再附原文引文

# IX. 圖表

1.圖（Figures）

&nbsp;&nbsp;&nbsp;&nbsp;使用 figure 環境

&nbsp;&nbsp;&nbsp;&nbsp;圖說（caption）放在圖的下方

&nbsp;&nbsp;&nbsp;&nbsp;避免使用彩色，除非必要

2.表（Tables）

&nbsp;&nbsp;&nbsp;&nbsp;使用 table 環境

&nbsp;&nbsp;&nbsp;&nbsp;表題放在表的上方

&nbsp;&nbsp;&nbsp;&nbsp;使用 \begin{tabular} 排版內容

3.注意事項

&nbsp;&nbsp;&nbsp;&nbsp;圖表需在文中首次被提及之後才出現

&nbsp;&nbsp;&nbsp;&nbsp;使用 \label 與 \ref 做交叉引用

&nbsp;&nbsp;&nbsp;&nbsp;避免太大或太小的圖表，保持可讀性

# X. 結論

1.簡短總結全文貢獻與發現

2.不應包含新的內容或未提及的數據

3.常以簡潔的段落形式呈現

