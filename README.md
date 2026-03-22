# CSV生成フロー README（UiPath）

## 概要

PDFから取得したテキストを解析し、行・列に分解してDataTableに格納し、CSV形式で出力するUiPathフローです。

## 目的

PDFから取得したテキスト（pdfText）を加工し、CSV形式に変換して出力する。

## 全体フロー

pdfText → Lines → For Each → cols → dtRate → CSV出力

## 詳細

### 1. pdfText

PDF全文の文字列

### 2. Lines

改行で分割 例： A,B,C D,E,F

↓

\["A,B,C", "D,E,F"\]

### 3. For Each

1行ずつ処理

### 4. cols

カンマで列分割 cols = line.Split(","c)

### 5. Add Data Row

DataTableに1行追加

If(cols.Length \> 0, cols(0), "") で安全に取得

### 6. dtRate完成

ループ終了時に完成

### 7. Invoke Code（CSV変換）

DataTable → CSV文字列

-   ヘッダー作成
-   行データ処理
-   改行で結合
-   ファイル保存

## 出力

result.csv

## 重要ポイント

-   行 → 列 の順で分解
-   DataTableは中間データ
-   CSVはテキスト
-   安全に配列アクセスする

-   ## 使用技術

- UiPath
- VB.NET（Invoke Code）
- Git / GitHub
