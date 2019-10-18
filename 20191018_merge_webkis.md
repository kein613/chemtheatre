

```python
import numpy as np
import pandas as pd
from pandas import DataFrame
```

Webkis-plusのChemicalsテーブルを読み込む。

```python
webkis = pd.read_table('webkis_chemicals.txt')
```


```python
webkis[0:5]
```

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>chem_id</th>
      <th>CAS</th>
      <th>j_name</th>
      <th>e_name</th>
      <th>URL</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>ACG00096</td>
      <td>7440-36-0</td>
      <td>NaN</td>
      <td>Antimony - Elemental</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/ACG00096</td>
    </tr>
    <tr>
      <th>1</th>
      <td>BNS00319</td>
      <td>57-91-0</td>
      <td>１７α−エストラジオール</td>
      <td>１７ａｌｐｈａ−ｅｓｔｒａｄｉｏｌ</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/BNS00319</td>
    </tr>
    <tr>
      <th>2</th>
      <td>BNS00357</td>
      <td>39001-02-0</td>
      <td>１，２，３，４，６，７，８，９−オクタクロロジベンゾフラン</td>
      <td>１，２，３，４，６，７，８，９−Ｏｃｔａｃｈｌｏｒｏｄｉｂｅｎｚｏｆｕｒａｎ；　１，２，３，...</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/BNS00357</td>
    </tr>
    <tr>
      <th>3</th>
      <td>BNS01011</td>
      <td>28804-88-8</td>
      <td>ジメチルナフタレン</td>
      <td>ｄｉｍｅｔｈｙｌｎａｐｈｔｈａｌｅｎｅ</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/BNS01011</td>
    </tr>
    <tr>
      <th>4</th>
      <td>BNS01066</td>
      <td>22967-92-6</td>
      <td>NaN</td>
      <td>Methylmercury</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/BNS01066</td>
    </tr>
  </tbody>
</table>
</div>


ChemTHEATREのChemicalsテーブルを読み込む。この時，PubChemのカラムはデータ型を文字型にしておく。PubChemIDは整数だが，IDが付かないレコードがあり，それらは欠損値NaNとして扱われる。NaNは浮動小数点型（float）として認識されるので，整数型には変換できず，PubChemIDにも小数点が付いてしまう。

```python
chemtheatre = pd.read_table('chemtheatre_chemicals.tsv', dtype = {'PubChem':str})
```

```python
chemtheatre[0:5]
```

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ChemicalID</th>
      <th>ChemGroupID</th>
      <th>ChemicalName</th>
      <th>IUPAC</th>
      <th>Synonyms</th>
      <th>PubChem</th>
      <th>CAS</th>
      <th>NIST</th>
      <th>Remarks</th>
      <th>RegisterDate</th>
      <th>UpdateDate</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>CH0000001</td>
      <td>CG0003</td>
      <td>2,3,7,8-TCDD</td>
      <td>2,3,7,8-tetrachlorodibenzo-p-dioxin</td>
      <td>2,3,7,8-Tetrachlorodibenzo-p-dioxin, TCDD, Dioxin</td>
      <td>15625</td>
      <td>1746-01-6</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2016/8/18</td>
      <td>2016/8/26</td>
    </tr>
    <tr>
      <th>1</th>
      <td>CH0000002</td>
      <td>CG0003</td>
      <td>1,2,3,7,8-PentaCDD</td>
      <td>1,2,3,7,8-pentachlorodibenzo-p-dioxin</td>
      <td>1,2,3,7,8-pentachlorodibenzo-p-dioxin, PeCDD</td>
      <td>38439</td>
      <td>40321-76-4</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2016/8/18</td>
      <td>2016/8/26</td>
    </tr>
    <tr>
      <th>2</th>
      <td>CH0000003</td>
      <td>CG0003</td>
      <td>1,2,3,4,7,8-HexaCDD</td>
      <td>1,2,3,4,7,8-hexachlorodibenzo-p-dioxin</td>
      <td>1,2,3,4,7,8-hexachlorodibenzo-p-dioxin</td>
      <td>38251</td>
      <td>39227-28-6</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2016/8/18</td>
      <td>2016/8/26</td>
    </tr>
    <tr>
      <th>3</th>
      <td>CH0000004</td>
      <td>CG0003</td>
      <td>1,2,3,6,7,8-HexaCDD</td>
      <td>1,2,3,6,7,8-hexachlorodibenzo-p-dioxin</td>
      <td>1,2,3,6,7,8-hexachlorodibenzo-p-dioxin</td>
      <td>42540</td>
      <td>57653-85-7</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2016/8/18</td>
      <td>2016/8/26</td>
    </tr>
    <tr>
      <th>4</th>
      <td>CH0000005</td>
      <td>CG0003</td>
      <td>1,2,3,7,8,9-HexaCDD</td>
      <td>1,2,3,7,8,9-hexachlorodibenzo-p-dioxin</td>
      <td>1,2,3,7,8,9-Hexachlorodibenzodioxin</td>
      <td>29575</td>
      <td>19408-74-3</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2016/8/18</td>
      <td>2016/8/26</td>
    </tr>
  </tbody>
</table>
</div>

CASを参照して（on='CAS'），ChemTHEATREのテーブルに合わせるように（how='left'），2つのテーブルをマージする。

```python
chemicals_merged = pd.merge(chemtheatre, webkis, on='CAS', how='left')
chemicals_merged[0:5]
```

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ChemicalID</th>
      <th>ChemGroupID</th>
      <th>ChemicalName</th>
      <th>IUPAC</th>
      <th>Synonyms</th>
      <th>PubChem</th>
      <th>CAS</th>
      <th>NIST</th>
      <th>Remarks</th>
      <th>RegisterDate</th>
      <th>UpdateDate</th>
      <th>chem_id</th>
      <th>j_name</th>
      <th>e_name</th>
      <th>URL</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>CH0000001</td>
      <td>CG0003</td>
      <td>2,3,7,8-TCDD</td>
      <td>2,3,7,8-tetrachlorodibenzo-p-dioxin</td>
      <td>2,3,7,8-Tetrachlorodibenzo-p-dioxin, TCDD, Dioxin</td>
      <td>15625</td>
      <td>1746-01-6</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2016/8/18</td>
      <td>2016/8/26</td>
      <td>KUR00979</td>
      <td>２，３，７，８−テトラクロロジベンゾ−ｐ−ジオキシン</td>
      <td>2,3,7,8-TETRACHLORODIBENZO-P-DIOXIN</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/KUR00979</td>
    </tr>
    <tr>
      <th>1</th>
      <td>CH0000002</td>
      <td>CG0003</td>
      <td>1,2,3,7,8-PentaCDD</td>
      <td>1,2,3,7,8-pentachlorodibenzo-p-dioxin</td>
      <td>1,2,3,7,8-pentachlorodibenzo-p-dioxin, PeCDD</td>
      <td>38439</td>
      <td>40321-76-4</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2016/8/18</td>
      <td>2016/8/26</td>
      <td>KUR01017</td>
      <td>１，２，３，７，８−ペンタクロロジベンゾ−パラ−ジオキシン</td>
      <td>NaN</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/KUR01017</td>
    </tr>
    <tr>
      <th>2</th>
      <td>CH0000003</td>
      <td>CG0003</td>
      <td>1,2,3,4,7,8-HexaCDD</td>
      <td>1,2,3,4,7,8-hexachlorodibenzo-p-dioxin</td>
      <td>1,2,3,4,7,8-hexachlorodibenzo-p-dioxin</td>
      <td>38251</td>
      <td>39227-28-6</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2016/8/18</td>
      <td>2016/8/26</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>CH0000004</td>
      <td>CG0003</td>
      <td>1,2,3,6,7,8-HexaCDD</td>
      <td>1,2,3,6,7,8-hexachlorodibenzo-p-dioxin</td>
      <td>1,2,3,6,7,8-hexachlorodibenzo-p-dioxin</td>
      <td>42540</td>
      <td>57653-85-7</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2016/8/18</td>
      <td>2016/8/26</td>
      <td>KUR01034</td>
      <td>1,2,3,6,7,8-ヘキサクロロジベンゾ-パラ-ジオキシン</td>
      <td>1,2,3,6,7,8-Hexachlorodibenzo-p-dioxin; 1,2,3,...</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/KUR01034</td>
    </tr>
    <tr>
      <th>4</th>
      <td>CH0000005</td>
      <td>CG0003</td>
      <td>1,2,3,7,8,9-HexaCDD</td>
      <td>1,2,3,7,8,9-hexachlorodibenzo-p-dioxin</td>
      <td>1,2,3,7,8,9-Hexachlorodibenzodioxin</td>
      <td>29575</td>
      <td>19408-74-3</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2016/8/18</td>
      <td>2016/8/26</td>
      <td>KUR00981</td>
      <td>NaN</td>
      <td>Hexachlorodibenzo-p-dioxin, mixture (HxCDD)</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/KUR00981</td>
    </tr>
  </tbody>
</table>
</div>

Webkis-plusのリンク先URLをHTMLタグに書き換える。

```python
link = '<a href ="'+chemicals_merged['URL']+'">Link to Webkis-plus</a>;'
chemicals_merged['Remarks'] = link
chemicals_merged[0:5]
```

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ChemicalID</th>
      <th>ChemGroupID</th>
      <th>ChemicalName</th>
      <th>IUPAC</th>
      <th>Synonyms</th>
      <th>PubChem</th>
      <th>CAS</th>
      <th>NIST</th>
      <th>Remarks</th>
      <th>RegisterDate</th>
      <th>UpdateDate</th>
      <th>chem_id</th>
      <th>j_name</th>
      <th>e_name</th>
      <th>URL</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>CH0000001</td>
      <td>CG0003</td>
      <td>2,3,7,8-TCDD</td>
      <td>2,3,7,8-tetrachlorodibenzo-p-dioxin</td>
      <td>2,3,7,8-Tetrachlorodibenzo-p-dioxin, TCDD, Dioxin</td>
      <td>15625</td>
      <td>1746-01-6</td>
      <td>NaN</td>
      <td>&lt;a href ="https://www.nies.go.jp/kisplus/dtl/c...</td>
      <td>2016/8/18</td>
      <td>2016/8/26</td>
      <td>KUR00979</td>
      <td>２，３，７，８−テトラクロロジベンゾ−ｐ−ジオキシン</td>
      <td>2,3,7,8-TETRACHLORODIBENZO-P-DIOXIN</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/KUR00979</td>
    </tr>
    <tr>
      <th>1</th>
      <td>CH0000002</td>
      <td>CG0003</td>
      <td>1,2,3,7,8-PentaCDD</td>
      <td>1,2,3,7,8-pentachlorodibenzo-p-dioxin</td>
      <td>1,2,3,7,8-pentachlorodibenzo-p-dioxin, PeCDD</td>
      <td>38439</td>
      <td>40321-76-4</td>
      <td>NaN</td>
      <td>&lt;a href ="https://www.nies.go.jp/kisplus/dtl/c...</td>
      <td>2016/8/18</td>
      <td>2016/8/26</td>
      <td>KUR01017</td>
      <td>１，２，３，７，８−ペンタクロロジベンゾ−パラ−ジオキシン</td>
      <td>NaN</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/KUR01017</td>
    </tr>
    <tr>
      <th>2</th>
      <td>CH0000003</td>
      <td>CG0003</td>
      <td>1,2,3,4,7,8-HexaCDD</td>
      <td>1,2,3,4,7,8-hexachlorodibenzo-p-dioxin</td>
      <td>1,2,3,4,7,8-hexachlorodibenzo-p-dioxin</td>
      <td>38251</td>
      <td>39227-28-6</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2016/8/18</td>
      <td>2016/8/26</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>CH0000004</td>
      <td>CG0003</td>
      <td>1,2,3,6,7,8-HexaCDD</td>
      <td>1,2,3,6,7,8-hexachlorodibenzo-p-dioxin</td>
      <td>1,2,3,6,7,8-hexachlorodibenzo-p-dioxin</td>
      <td>42540</td>
      <td>57653-85-7</td>
      <td>NaN</td>
      <td>&lt;a href ="https://www.nies.go.jp/kisplus/dtl/c...</td>
      <td>2016/8/18</td>
      <td>2016/8/26</td>
      <td>KUR01034</td>
      <td>1,2,3,6,7,8-ヘキサクロロジベンゾ-パラ-ジオキシン</td>
      <td>1,2,3,6,7,8-Hexachlorodibenzo-p-dioxin; 1,2,3,...</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/KUR01034</td>
    </tr>
    <tr>
      <th>4</th>
      <td>CH0000005</td>
      <td>CG0003</td>
      <td>1,2,3,7,8,9-HexaCDD</td>
      <td>1,2,3,7,8,9-hexachlorodibenzo-p-dioxin</td>
      <td>1,2,3,7,8,9-Hexachlorodibenzodioxin</td>
      <td>29575</td>
      <td>19408-74-3</td>
      <td>NaN</td>
      <td>&lt;a href ="https://www.nies.go.jp/kisplus/dtl/c...</td>
      <td>2016/8/18</td>
      <td>2016/8/26</td>
      <td>KUR00981</td>
      <td>NaN</td>
      <td>Hexachlorodibenzo-p-dioxin, mixture (HxCDD)</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/KUR00981</td>
    </tr>
  </tbody>
</table>
</div>

ChemTHEATREのchemicalsテーブルに必要な列だけを抽出して，
タブ区切りファイル（sep='\t'）として書き出す。この時，行番号は不要なので表示させない（index=False）。

```python
chemicals_upload = chemicals_merged.iloc[:, 0:11]
chemicals_upload.to_csv('chemicals_link_upload.tsv', sep='\t', index=False)
```
