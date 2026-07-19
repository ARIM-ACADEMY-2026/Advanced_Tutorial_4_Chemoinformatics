# ARIM情報活用講座：機械学習チュートリアル（SHAP／溶解度予測）

ARIMデータポータル会員向けセミナー・ワークショップで使用する、Jupyter Notebook形式の機械学習チュートリアル教材です。scikit-learn・XGBoost・SHAP・RDKit・Mordredなどを用いて、モデル解釈（XAI）と有機化合物の水溶解度予測を扱います。

## ノートブック一覧

| No. | ノートブック | 内容 | Google Colabで開く |
| --- | --- | --- | --- |
| 1 | [`1_SHAP.ipynb`](./1_SHAP.ipynb) | SHAP（SHapley Additive exPlanations）入門編。California HousingデータセットとXGBoost回帰モデルを題材に、bar plot・beeswarm plot・waterfall plot・force plot・scatter plotによるモデル解釈を体験します。 | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/ARIM-Training/Training_python_12/blob/main/1_SHAP.ipynb) |
| 2 | [`2_descriptor-paper2.ipynb`](./2_descriptor-paper2.ipynb) | 論文追試 Part-1（Mordred分子記述子編）。Mordredで生成した物理化学的記述子を用いて、線形重回帰（MLR）とランダムフォレスト回帰（RFR）で水溶解度を予測します。 | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/ARIM-Training/Training_python_12/blob/main/2_descriptor-paper2.ipynb) |
| 3 | [`3_morgan paper2.ipynb`](./3_morgan%20paper2.ipynb) | 論文追試 Part-2（Morganフィンガープリント編）。ECFP4相当のMorganフィンガープリントを用いて同じ溶解度予測タスクに取り組み、記述子モデルとの精度比較を行います。 | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/ARIM-Training/Training_python_12/blob/main/3_morgan%20paper2.ipynb) |

> Colabバッジは GitHub リポジトリ `ARIM-Training/Training_python_12`（`main`ブランチ）を参照します。バッジが正しく開かない場合（リポジトリ未反映・ブランチ名相違など）は、Colabの `ファイル > ノートブックをアップロード` から `.ipynb` を直接アップロードして開いてください。

ノートブック2・3は、以下の論文の追試・教材化を目的としています。

> Tayyebi, A., Alshami, A.S., Rabiei, Z. et al. Prediction of organic compound aqueous solubility using machine learning: a comparison study of descriptor-based and fingerprints-based models. *J Cheminform* 15, 99 (2023). https://doi.org/10.1186/s13321-023-00752-6

## フォルダ構成

```
├── 1_SHAP.ipynb
├── 2_descriptor-paper2.ipynb
├── 3_morgan paper2.ipynb
├── data/                       # 学習・検証用データ
│   ├── new222new.csv                        # 論文 Additional file 1（8,438化合物、SMILES＋実測水溶解度）
│   ├── testexperiment2upload2raw.csv        # 外部検証データ「Solubility Challenge」（32化合物、Llinàs et al. 2008由来）
│   └── testexperiment2upload3raw.csv        # 外部検証データ「Blind test」（32化合物、同上）
├── img/
│   └── shap_header.svg         # 1_SHAP.ipynb 内で使用する説明図
└── paper/                      # 原論文PDFと付録データ（ノートブック2・3の元論文）
    ├── s13321-023-00752-6.pdf
    ├── Additional file 1_13321_2023_752_MOESM1_ESM.csv   # data/new222new.csv と同一内容
    └── 13321_2023_752_MOESM2_ESM.docx                    # Additional file 2（記述子一覧・上位特徴量表など）
```

## 実行環境

いずれのノートブックもGoogle Colabでの実行を想定しています。各ノートブック冒頭の「Google Colabにおける環境設定」セルで、必要なライブラリ（xgboost・shap・rdkit・mordred等）のインストールとリポジトリの`git clone`を行います。

ローカル環境で実行する場合は、`git clone`セルを実行せず、あらかじめ以下をインストールしてください（このフォルダに`data/`・`img/`が既に含まれているため、`git clone`は不要です）。

```bash
pip install xgboost shap rdkit mordred scikit-learn pandas numpy matplotlib openpyxl
```

動作確認済みバージョン: rdkit 2026.03 系、mordred 1.2 系、scikit-learn 1.7 系、shap 0.49 系、xgboost 3.2 系。

## 対象読者

ARIMデータポータル会員の研究者・技術者を想定しています。Pythonの基礎文法は理解しているが、pandas・scikit-learn・RDKit・SHAPなどのライブラリには初めて触れる、統計学・機械学習の予備知識は前提としない、という読者を想定して構成しています。各ノートブック冒頭に「対象読者・前提知識・動作環境・版とライセンス」のブロックを設けています。

## ライセンス・出典

- 教材本体はARIMデータポータル情報活用講座向けのオリジナル教材です。
- `data/new222new.csv`・`data/testexperiment2upload2raw.csv`・`data/testexperiment2upload3raw.csv`および`paper/`内のファイルは、上記論文の公開データ（Additional files）に基づきます。データの利用条件は原論文の公開元（Springer / *Journal of Cheminformatics*, オープンアクセス）に従ってください。
- `1_SHAP.ipynb`で使用するCalifornia Housingデータセットは`shap.datasets.california()`（scikit-learn経由）で取得される公開データセットです。
