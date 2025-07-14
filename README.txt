# 構成ファイル一覧

# README.md
このプロジェクトの概要を記載

# main.py
食品名の類似検索（Top3マッチング）を実行するスクリプト。
【処理概要】
1. 対象施設A（query）と比較施設B（base）の食品データをCSVから読み込む
2. 食品名を正規化（表記ゆれの除去など）
3. TF-IDFによる文字ベースベクトル化（文字n-gram: 1〜3）
4. 正規化された食品名ベクトルをもとに、queryごとにbaseから類似食品をTop3検索
5. 結果をCSV形式で出力

# preprocess.py
食品名の表記ゆれを正規化。

# matcher.py
正規化済みの食品名ベクトル（TF-IDFベース）を用いて、各query食品に対して比較対象（base）から類似食品Top3をコサイン類似度で検索。

# vectorizer.py
食品名（文字列）を対象に、文字n-gram（1～3文字）に基づくTF-IDFベクトルを作成し、query用とbase用のベクトルに分離して返す関数。
TF-IDFにはsklearnのTfidfVectorizerを使用。

# output_writer.py
結果をCSVで出力させる。
