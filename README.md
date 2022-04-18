# データアナリティクスII-2022
本レポジトリは，2022年前期に静岡大学情報学部で開講される講義「データアナリティクスII」（山本担当パート）の資料置き場です．


## 開講情報
* 実施時期：静岡大学 情報学部 行動情報学科 3年次
* 日時：前期月曜4-5コマ（14:25-17:35）
* 場所：共31


## 【重要】ガイダンス動画
本授業科目のガイダンスは，4月11日（月）の初回授業前にオンデマンド動画を視聴する形式で行います．
本授業科目の履修を検討している学生は，初回授業が始まる前の**4月6日から4月10日の間**に必ず下記動画を視聴してください．

[ガイダンス動画へのリンク](https://www.youtube.com/watch?v=gKUFHUq8bvo)


## 成績評価（山本担当パート）
山本担当パートでは，本授業科目の約33％の成績を評価します（残り67％は金先生，大島先生パートで評価）．
評価は以下の2つの観点から行います．
* レポート課題(山本担当パート100％)
* 授業参加への積極性
	* 加点要素．山本担当パート最大20％分まで加点（レポート課題分の得点との合計が100%を超えた場合，山本担当パートの成績は100%となる）
	* 「毎回の授業で出題するノックの回答発表」 or 「授業内容への質問 in 授業中」


## 授業の予定とコンテンツ（山本担当パート）
| |  日時  | トピック | 講義資料 | 課題&ドリル（模範回答なし） | ドリル（模範解答あり） |
| ---- | ---- | ---- | ---- | ---- | ---- |
| 第1回 | 4月11日（月） | BadData, not BigData | [Speaker Deck](https://speakerdeck.com/trycycle/2022nian-du-tetaanariteikusuii-di-1hui-20220411) | [nbviewer](https://nbviewer.org/github/hontolab-courses/data-analytics-2022/blob/main/notebook/day-01.ipynb) |  今回はなし |
| 第2回 | 4月18日（月） | データ選択・集約のための基礎的なSQL操作 | [Speaker Deck](https://speakerdeck.com/trycycle/2022nian-du-tetaanariteikusuii-di-2hui-20220418) | [Google Colab](https://colab.research.google.com/github/hontolab-courses/data-analytics-2022/blob/main/notebook/day-02.ipynb) | [Google Colab](https://colab.research.google.com/github/hontolab-courses/data-analytics-2022/blob/main/notebook/answer/day-02.ipynb) |
| 第3回 | 4月25日（月） | データの結合やデータ変換のためのSQL操作 | [Speaker Deck](https://speakerdeck.com/trycycle/2022nian-du-detaanariteikusuii-di-3hui-20220425) | [Google Colab](https://colab.research.google.com/github/hontolab-courses/data-analytics-2022/blob/main/notebook/day-03.ipynb) |  |
| 第4回 | 5月02日（月） |  |  |  |  |
| 第5回 | 5月09日（月） |  |  |  |  |


## レポート課題
### 課題1（Day 1より）
杏森堂では，顧客台帳をExcelフォーマットを使って管理している．売上は順調であり，Excelのデータがかなりのボリュームになっているため，データ分析を行うことで色々な知見が期待できる．

杏森堂からデータ分析の依頼を受けたとしよう．[こちらのOneDrive（要Office365アカウント）](https://scii-my.sharepoint.com/:f:/g/personal/yusuke_yamamoto_cii_shizuoka_ac_jp/Egffkcr-VBRDrMpGG-4uc1UB2jv9B7Uh9omCkUmc-RUigA?e=2fgjQh)には，杏森堂の売上に関する以下の4つのファイルが格納されている：
* 購買記録に関するデータ（2019年1月〜2019年7月の売上履歴）
    * uriage_1.csv
    * uriage_2.csv
* 顧客台帳データ（手入力で店舗が管理している顧客台帳）
    * kokyaku_daicho_1.csv
    * kokyaku_daicho_2.csv

2つのファイルを用いて，以下に関する表を作成せよ：
1. 縦方向にある年のある月，横方向に商品を並べた，商品ごとの年月別売上情報
2. 縦方向にある年のある月，横方向に地域（市）を並べた，各市ごとの年月別売上情報
3. 集計期間中（2019年1月〜2019年7月）に杏森堂で購買行動をしていない顧客のリスト


### 課題2（Day 2より）
データベースを整備した杏森堂から，再度データ分析の依頼を受けたとする．
購買履歴が格納されたデータベースを用いて，これまでに何名の顧客が何回（何日）ショッピングを行ったのかを分析したい．

レシート明細テーブル（`receipt`）を用いて顧客の購買頻度を分析し，以下の項目について分析結果を表示するSQL文を書き，実行結果とともに示しなさい：
* 購買頻度（これまでに店舗を利用した日数）
* 購買頻度に対応する顧客の数
* 該当する購買頻度以下の顧客数の累積値

ただし，顧客ID（`customer_id`）が"Z"から始まるのものは非会員を表すため，除外して分析すること．


### 課題3（Day 3より）
課題3-1，課題3-2のいずれかを選択し，結果を得るためのSQL文を書き，実行結果とともに示しなさい．

#### 課題3-1: 月別売上の対昨年比

レシート明細テーブル（`receipt`）には2017年1月から2019年10月の間の購買情報が記録されている．2017年から2019年までの期間の売上を把握するために，1ヶ月ごとに以下の情報を集約表示せよ：
* 年月（`year_month`）
* 購買回数（`purchase_freq`）
* 購買1回あたりの平均購入額（`avg_amount_per_purchase`）
* 月間売上高（`total_amount`）
* 当該月の前年売上高（`total_amount_last_year`）
* 売上の対前年比（`ratio`）

#### 課題3-2: ABC分析

ABC分析は販売戦略を考えるために，売上によって商品をランク付けする手法である．
一般に，ABC分析では売上総額の
* 上位0〜70％の商品をAランク
* 上位70〜90％の商品をBランク
* 上位90〜100%の商品をCランク

とするランク付けを行う．

商品カテゴリ「菓子（`category_major_cd = 08`）」に属する商品について，小区分（`category_small_name`）ごとに売上を集計し，菓子カテゴリの売上総額に占める割合（構成比）を計算せよ．
また，売上がN位の小区分の行には売上額上位N位までの構成比累計，および構成比累計に基づくABC分析のランク付け結果も表示せよ．
