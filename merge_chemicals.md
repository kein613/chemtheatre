

```python
import numpy as np
import pandas as pd
from pandas import DataFrame
```

Webkis-plusの化学物質テーブルを読み込む。
```python
webkis = pd.read_table('webkis_chemicals.txt')
```


```python
print(webkis)
```

          chem_id          CAS                                             j_name  \
    0    ACG00096    7440-36-0                                                NaN   
    1    BNS00319      57-91-0                                       １７α−エストラジオール   
    2    BNS00357   39001-02-0                      １，２，３，４，６，７，８，９−オクタクロロジベンゾフラン   
    3    BNS01011   28804-88-8                                          ジメチルナフタレン   
    4    BNS01066   22967-92-6                                                NaN   
    5    BNS01472    7439-89-6                                                  鉄   
      
                                                    e_name  \
    0                                 Antimony - Elemental   
    1                                    １７ａｌｐｈａ−ｅｓｔｒａｄｉｏｌ   
    2    １，２，３，４，６，７，８，９−Ｏｃｔａｃｈｌｏｒｏｄｉｂｅｎｚｏｆｕｒａｎ；　１，２，３，...   
    3                                  ｄｉｍｅｔｈｙｌｎａｐｈｔｈａｌｅｎｅ   
    4                                        Methylmercury   
    5                                            Ｉｒｏｎ　（Ｆｅ）   
    
                                                      URL  
    0    https://www.nies.go.jp/kisplus/dtl/chem/ACG00096  
    1    https://www.nies.go.jp/kisplus/dtl/chem/BNS00319  
    2    https://www.nies.go.jp/kisplus/dtl/chem/BNS00357  
    3    https://www.nies.go.jp/kisplus/dtl/chem/BNS01011  
    4    https://www.nies.go.jp/kisplus/dtl/chem/BNS01066  
    5    https://www.nies.go.jp/kisplus/dtl/chem/BNS01472  
   
ChemTHEATREのchemicalsテーブルを読み込む。
この時，PubChemのカラムだけ，データ型を文字型にしておく。PubChemIDは整数だが，PubChemIDが付かないレコードがあり，欠損値NaNとして表示される。NaNは浮動小数点型（float）として認識されるので，データ型を整数型には出来ない。

```python
chemtheatre = pd.read_table('chemtheatre_chemicals.tsv', dtype = {'PubChem':str})
```


```python
print(chemtheatre)
```

         ChemicalID ChemGroupID              ChemicalName  \
    0     CH0000001      CG0003              2,3,7,8-TCDD   
    1     CH0000002      CG0003        1,2,3,7,8-PentaCDD   
    2     CH0000003      CG0003       1,2,3,4,7,8-HexaCDD   
    3     CH0000004      CG0003       1,2,3,6,7,8-HexaCDD   
    4     CH0000005      CG0003       1,2,3,7,8,9-HexaCDD   
    5     CH0000006      CG0003    1,2,3,4,6,7,8-HeptaCDD   
   
                                                      IUPAC  \
    0                   2,3,7,8-tetrachlorodibenzo-p-dioxin   
    1                 1,2,3,7,8-pentachlorodibenzo-p-dioxin   
    2                1,2,3,4,7,8-hexachlorodibenzo-p-dioxin   
    3                1,2,3,6,7,8-hexachlorodibenzo-p-dioxin   
    4                1,2,3,7,8,9-hexachlorodibenzo-p-dioxin   
    5             1,2,3,4,6,7,8-heptachlorodibenzo-p-dioxin   
   
                                                   Synonyms    PubChem  \
    0     2,3,7,8-Tetrachlorodibenzo-p-dioxin, TCDD, Dioxin      15625   
    1          1,2,3,7,8-pentachlorodibenzo-p-dioxin, PeCDD      38439   
    2                1,2,3,4,7,8-hexachlorodibenzo-p-dioxin      38251   
    3                1,2,3,6,7,8-hexachlorodibenzo-p-dioxin      42540   
    4                   1,2,3,7,8,9-Hexachlorodibenzodioxin      29575   
    5             1,2,3,4,6,7,8-heptachlorodibenzo-p-dioxin      37270   
    
                   CAS  NIST Remarks RegisterDate  UpdateDate  
    0        1746-01-6   NaN     NaN    2016/8/18   2016/8/26  
    1       40321-76-4   NaN     NaN    2016/8/18   2016/8/26  
    2       39227-28-6   NaN     NaN    2016/8/18   2016/8/26  
    3       57653-85-7   NaN     NaN    2016/8/18   2016/8/26  
    4       19408-74-3   NaN     NaN    2016/8/18   2016/8/26  
    5       35822-46-9   NaN     NaN    2016/8/18   2016/8/26  

CAS RNで揃えて（on='CAS'），ChemTHEATREのテーブルをベースに（how='left'）2つのテーブルをマージする。

```python
pd.merge(chemtheatre, webkis, on='CAS', how='left')
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
    <tr>
      <th>5</th>
      <td>CH0000006</td>
      <td>CG0003</td>
      <td>1,2,3,4,6,7,8-HeptaCDD</td>
      <td>1,2,3,4,6,7,8-heptachlorodibenzo-p-dioxin</td>
      <td>1,2,3,4,6,7,8-heptachlorodibenzo-p-dioxin</td>
      <td>37270</td>
      <td>35822-46-9</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2016/8/18</td>
      <td>2016/8/26</td>
      <td>KUR01014</td>
      <td>１，２，３，４，６，７，８−ヘプタクロロジベンゾ−パラ−ジオキシン</td>
      <td>NaN</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/KUR01014</td>
    </tr>
  </tbody>
</table>
<p>1057 rows × 15 columns</p>
</div>


ChemTHEATREにアップロードできるよう，必要なカラムだけを抽出する。

```python
chemicals_upload = chemicals_merged.iloc[:, 0:11]
```

ChemTHEATREにアップロードするタブ区切り（sep='\t'）ファイルを出力する。この時，行番号は要らないので表示させない（index=False）。

```python
chemicals_upload.to_csv('chemicals_link_upload.tsv', sep='\t', index=False)
```
