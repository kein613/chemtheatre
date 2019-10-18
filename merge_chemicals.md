

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
    6     CH0000007      CG0003                   OctaCDD   
    7     CH0000008      CG0004              2,3,7,8-TCDF   
    8     CH0000009      CG0004        1,2,3,7,8-PentaCDF   
    9     CH0000010      CG0004        2,3,4,7,8-PentaCDF   
    10    CH0000011      CG0004         1,2,3,4,7,8-HxCDF   
    11    CH0000012      CG0004         1,2,3,6,7,8-HxCDF   
    12    CH0000013      CG0004         1,2,3,7,8,9-HxCDF   
    13    CH0000014      CG0004         2,3,4,6,7,8-HxCDF   
    14    CH0000015      CG0004       1,2,3,4,6,7,8-HpCDF   
    15    CH0000016      CG0004       1,2,3,4,7,8,9-HpCDF   
    16    CH0000017      CG0004                   OctaCDF   
    17    CH0000018      CG0003               Total PCDDs   
    18    CH0000019      CG0004               Total PCDFs   
    19    CH0000020      CG0002             Total PCDD/Fs   
    20    CH0000021      CG0003                PCDDs-TEQs   
    21    CH0000022      CG0004                PCDFs-TEQs   
    22    CH0000023      CG0002              PCDD/Fs-TEQs   
    23    CH0000024      CG0002                Total TEQs   
    24    CH0000025      CG0014                  o,p'-DDE   
    25    CH0000026      CG0014                  o,p'-DDD   
    26    CH0000027      CG0014                  o,p'-DDT   
    27    CH0000028      CG0014                Σo,p'-DDTs   
    28    CH0000029      CG0014                  p,p'-DDE   
    29    CH0000030      CG0014                  p,p'-DDD   
    ...         ...         ...                       ...   
    1026  CH0001028      CG0049                Nitenpyram   
    1027  CH0001029      CG0049               Thiacloprid   
    1028  CH0001030      CG0049              Thiamethoxam   
    1029  CH0001031      CG0049                       CPF   
    1030  CH0001032      CG0049     Desnitro-imidacloprid   
    1031  CH0001033      CG0049                    IM-2-1   
    1032  CH0001034      CG0049         Thiacloprid-amide   
    1033  CH0001035      CG0060                  Fipronil   
    1034  CH0001036      CG0120               Bromobutide   
    1035  CH0001037      CG0120              Quinoclamine   
    1036  CH0001038      CG0120              Pretilachlor   
    1037  CH0001039      CG0120               Thenylchlor   
    1038  CH0001040      CG0120                 Mefenacet   
    1039  CH0001041      CG0060                Buprofezin   
    1040  CH0001042      CG0048                Fenobucarb   
    1041  CH0001043      CG0047               Silafluofen   
    1042  CH0001044      CG0116      2,3-Epoxy-1-propanol   
    1043  CH0001045      CG0116            Glutaraldehyde   
    1044  CH0001046      CG0116    2-Methoxyethyl acetate   
    1045  CH0001047      CG0115  2,4-Dichloronitrobenzene   
    1046  CH0001048      CG0116         Dicyclohexylamine   
    1047  CH0001049      CG0115        2,4-Dinitroaniline   
    1048  CH0001050      CG0116        Dimethyl disulfide   
    1049  CH0001051      CG0116                1-Naphthol   
    1050  CH0001052      CG0115            2-Naphthalenol   
    1051  CH0001053      CG0116           2-Vinylpyridine   
    1052  CH0001054      CG0116     4-Vinyl-1-cyclohexene   
    1053  CH0001055      CG0116                  Pyridine   
    1054  CH0001056      CG0115          3-Methylpyridine   
    1055  CH0001057      CG0116  Dibutyl phenyl phosphate   
    
                                                      IUPAC  \
    0                   2,3,7,8-tetrachlorodibenzo-p-dioxin   
    1                 1,2,3,7,8-pentachlorodibenzo-p-dioxin   
    2                1,2,3,4,7,8-hexachlorodibenzo-p-dioxin   
    3                1,2,3,6,7,8-hexachlorodibenzo-p-dioxin   
    4                1,2,3,7,8,9-hexachlorodibenzo-p-dioxin   
    5             1,2,3,4,6,7,8-heptachlorodibenzo-p-dioxin   
    6            1,2,3,4,6,7,8,9-octachlorodibenzo-p-dioxin   
    7                       2,3,7,8-tetrachlorodibenzofuran   
    8                     1,2,3,7,8-pentachlorodibenzofuran   
    9                     2,3,4,7,8-pentachlorodibenzofuran   
    10                   1,2,3,4,7,8-hexachlorodibenzofuran   
    11                   1,2,3,6,7,8-hexachlorodibenzofuran   
    12                   1,2,3,7,8,9-hexachlorodibenzofuran   
    13                   2,3,4,6,7,8-hexachlorodibenzofuran   
    14                1,2,3,4,6,7,8-heptachlorodibenzofuran   
    15                1,2,3,4,7,8,9-heptachlorodibenzofuran   
    16               1,2,3,4,6,7,8,9-octachlorodibenzofuran   
    17                                                  NaN   
    18                                                  NaN   
    19                                                  NaN   
    20                                                  NaN   
    21                                                  NaN   
    22                                                  NaN   
    23                                                  NaN   
    24    1-chloro-2-[2,2-dichloro-1-(4-chlorophenyl)eth...   
    25    1-chloro-2-[2,2-dichloro-1-(4-chlorophenyl)eth...   
    26    1-chloro-2-[2,2,2-trichloro-1-(4-chlorophenyl)...   
    27                                                  NaN   
    28    1-chloro-4-[2,2-dichloro-1-(4-chlorophenyl)eth...   
    29    1-chloro-4-[2,2-dichloro-1-(4-chlorophenyl)eth...   
    ...                                                 ...   
    1026  (E)-1-N'-[(6-chloropyridin-3-yl)methyl]-1-N'-e...   
    1027  [3-[(6-chloropyridin-3-yl)methyl]-1,3-thiazoli...   
    1028  (NE)-N-[3-[(2-chloro-1,3-thiazol-5-yl)methyl]-...   
    1029  N-[(6-chloropyridin-3-yl)methyl]-N-ethylformamide   
    1030  1-[(6-chloropyridin-3-yl)methyl]-4,5-dihydroim...   
    1031  N'-[(6-chloropyridin-3-yl)methyl]-N-cyanoethan...   
    1032  (Z)-[3-[(6-chloropyridin-3-yl)methyl]-1,3-thia...   
    1033  5-amino-1-[2,6-dichloro-4-(trifluoromethyl)phe...   
    1034  2-bromo-3,3-dimethyl-N-(2-phenylpropan-2-yl)bu...   
    1035              2-amino-3-chloronaphthalene-1,4-dione   
    1036  2-chloro-N-(2,6-diethylphenyl)-N-(2-propoxyeth...   
    1037  2-chloro-N-(2,6-dimethylphenyl)-N-[(3-methoxyt...   
    1038  2-(1,3-benzothiazol-2-yloxy)-N-methyl-N-phenyl...   
    1039  2-tert-butylimino-5-phenyl-3-propan-2-yl-1,3,5...   
    1040             (2-butan-2-ylphenyl) N-methylcarbamate   
    1041  (4-ethoxyphenyl)-[3-(4-fluoro-3-phenoxyphenyl)...   
    1042                                oxiran-2-ylmethanol   
    1043                                        pentanedial   
    1044                             2-methoxyethyl acetate   
    1045                        2,4-dichloro-1-nitrobenzene   
    1046                        N-cyclohexylcyclohexanamine   
    1047                                 2,4-dinitroaniline   
    1048                          (methyldisulfanyl)methane   
    1049                                    naphthalen-1-ol   
    1050                                    naphthalen-2-ol   
    1051                                  2-ethenylpyridine   
    1052                               4-ethenylcyclohexene   
    1053                                           pyridine   
    1054                                   3-methylpyridine   
    1055                           dibutyl phenyl phosphate   
    
                                                   Synonyms    PubChem  \
    0     2,3,7,8-Tetrachlorodibenzo-p-dioxin, TCDD, Dioxin      15625   
    1          1,2,3,7,8-pentachlorodibenzo-p-dioxin, PeCDD      38439   
    2                1,2,3,4,7,8-hexachlorodibenzo-p-dioxin      38251   
    3                1,2,3,6,7,8-hexachlorodibenzo-p-dioxin      42540   
    4                   1,2,3,7,8,9-Hexachlorodibenzodioxin      29575   
    5             1,2,3,4,6,7,8-heptachlorodibenzo-p-dioxin      37270   
    6                      octachlorodibenzo-4-dioxin; OCDD      18636   
    7                       2,3,7,8-TetraCDF; 2,3,7,8-TeCDF      39929   
    8                                       1,2,3,7,8-PCDBF      42138   
    9                     2,3,4,7,8-pentachlorodibenzofuran      42128   
    10                1,2,3,4,7,8-HexaCDF; 1,2,3,4,7,8-HCDB      51130   
    11    1,2,3,6,7,8-HexaCDF; 1,2,3,6,7,8-HEXACHLORODIB...      42140   
    12    1,2,3,7,8,9-HexaCDF; 1,2,3,7,8,9-HEXACHLORODIB...      51720   
    13    2,3,4,6,7,8-HexaCDF; 2,3,4,6,7,8-HEXACHLORODIB...      43495   
    14    1,2,3,4,6,7,8-HeptaCDF; 1,2,3,4,6,7,8-heptachl...      38199   
    15    1,2,3,4,7,8,9-HeptaCDF; 1,2,3,4,7,8,9-HEPTACHL...      41510   
    16                         octachlorodibenzofuran; OCDF      38200   
    17                                                  NaN        NaN   
    18                                                  NaN        NaN   
    19                                                  NaN        NaN   
    20                                                  NaN        NaN   
    21                                                  NaN        NaN   
    22                                                  NaN        NaN   
    23                                                  NaN        NaN   
    24    2,2-(2-chlorophenyl-4'-chlorophenyl)-1,1-dichl...     246598   
    25                                             Mitotane       4211   
    26    1,1,1-trichloro-2-(2-chlorophenyl)-2-(4-chloro...      13089   
    27                                                  NaN        NaN   
    28         1,1-dichloro-2,2-bis(p-chlorophenyl)ethylene       3035   
    29                       Dichlorodiphenyldichloroethane       6294   
    ...                                                 ...        ...   
    1026  Niterndipoine; Bestguard; (E)-Nitenpyram; (1E)...    3034287   
    1027  Calypso; (3-((6-Chloro-3-pyridinyl)methyl)-2-t...     115224   
    1028  3-(2-Chloro-thiazol-5-ylmethyl)-5-methyl-(1,3,...    5821911   
    1029  N-(6-Chloro-3-pyridylmethyl)-N-ethylformamide;...  101942083   
    1030  desnitroimidacloprid; 1-(6-chloro-pyridin-3-yl...   10130527   
    1031  N-demethyl acetamiprid; N-Desmethylacetamiprid...   11344811   
    1032  thiacloprid amide; Urea, N-[3-[(6-chloro-3-pyr...   16212161   
    1033         fipronil; Termidor; Fluocyanobenpyrazole;        3352   
    1034  bromobutide; (RS)-2-bromo-N-(alpha,alpha-dimet...      53079   
    1035  2-Amino-3-chloro-1,4-naphthoquinone; Quinoclam...      17748   
    1036  Solnet; pretilachlor; Acetamide, 2-chloro-N-(2...      91644   
    1037  Alherb; Acetamide, 2-chloro-N-(2,6-dimethylphe...     443036   
    1038  2-(2-benzothiazolyl-oxy)-N-methyl-N-phenylacet...      91716   
    1039  Applaud; buprofezin; 2-tert-butylimino-3-isopr...      50367   
    1040  BPMC; 2-(1-methylpropyl)phenyl methylcarbamate...      19588   
    1041  silafluofen; Benzene, 4-[3-[(4-ethoxyphenyl)di...      92430   
    1042  2-Oxiranemethanol; Glycidol; oxiran-2-ylmethan...      11164   
    1043  Pentanedial; glutaraldehyde; Glutaral; Glutari...       3485   
    1044  ethylene glycol monomethyl ether acetate; 2-me...       8054   
    1045  2,4-dichloro-1-nitro-benzen; 2,4-DICHLORONITRO...      11899   
    1046  N,N-Dicyclohexylamine; DCHA; Cyclohexanamine, ...       7582   
    1047  2,4-DINITROANILINE; Benzenamine, 2,4-dinitro-;...       7321   
    1048  Dimethyl disulfide; METHYL DISULFIDE; Dimethyl...      12232   
    1049  1-NAPHTHOL; naphthalen-1-ol; alpha-naphthol; α...       7005   
    1050  2-hydroxynaphthalene; 2-naphthol; beta-naphtho...       8663   
    1051  2-Ethenylpyridine; Pyridine, 2-ethenyl-; 2-Pyr...       7521   
    1052  4-Vinylcyclohexene; Cyclohexene, 4-ethenyl-; 4...       7499   
    1053  PYRIDINE; Azabenzene; Azine; Pyridin; monopyri...       1049   
    1054  3-METHYLPYRIDINE; 3-Picoline; beta-Picoline; P...       7970   
    1055  dibutylphenylphosphate; Phosphoric acid, dibut...      17312   
    
                   CAS  NIST Remarks RegisterDate  UpdateDate  
    0        1746-01-6   NaN     NaN    2016/8/18   2016/8/26  
    1       40321-76-4   NaN     NaN    2016/8/18   2016/8/26  
    2       39227-28-6   NaN     NaN    2016/8/18   2016/8/26  
    3       57653-85-7   NaN     NaN    2016/8/18   2016/8/26  
    4       19408-74-3   NaN     NaN    2016/8/18   2016/8/26  
    5       35822-46-9   NaN     NaN    2016/8/18   2016/8/26  
    6        3268-87-9   NaN     NaN   2016/08/18  2016/08/26  
    7       51207-31-9   NaN     NaN   2016/08/18  2016/08/26  
    8       57117-41-6   NaN     NaN    2016/8/18   2016/8/26  
    9       57117-31-4   NaN     NaN    2016/8/18   2016/8/26  
    10      70648-26-9   NaN     NaN   2016/08/18  2016/08/26  
    11      57117-44-9   NaN     NaN   2016/08/18  2016/08/26  
    12      72918-21-9   NaN     NaN   2016/08/18  2016/08/26  
    13      60851-34-5   NaN     NaN   2016/08/18  2016/08/26  
    14      67562-39-4   NaN     NaN   2016/08/18  2016/08/26  
    15      55673-89-7   NaN     NaN   2016/08/18  2016/08/26  
    16      39001-02-0   NaN     NaN   2016/08/18  2016/08/26  
    17             NaN   NaN     NaN    2016/8/18   2016/8/26  
    18             NaN   NaN     NaN    2016/8/18   2016/8/26  
    19             NaN   NaN     NaN    2016/8/18   2016/8/26  
    20             NaN   NaN     NaN    2016/8/18   2016/8/26  
    21             NaN   NaN     NaN    2016/8/18   2016/8/26  
    22             NaN   NaN     NaN    2016/8/18   2016/8/26  
    23             NaN   NaN     NaN    2016/8/18   2016/8/26  
    24       3424-82-6   NaN     NaN     2016/7/5    2016/7/5  
    25         53-19-0   NaN     NaN     2016/7/5    2016/7/5  
    26        789-02-6   NaN     NaN     2016/7/5    2016/7/5  
    27             NaN   NaN     NaN     2016/7/5    2016/7/5  
    28         72-55-9   NaN     NaN     2016/7/5    2016/7/5  
    29         72-54-8   NaN     NaN     2016/7/5    2016/7/5  
    ...            ...   ...     ...          ...         ...  
    1026   150824-47-8   NaN     NaN    2019/6/24   2019/6/24  
    1027   111988-49-9   NaN     NaN    2019/6/24   2019/6/24  
    1028   153719-23-4   NaN     NaN    2019/6/24   2019/6/24  
    1029           NaN   NaN     NaN    2019/6/24   2019/6/24  
    1030   115970-17-7   NaN     NaN    2019/6/24   2019/6/24  
    1031   190604-92-3   NaN     NaN    2019/6/24   2019/6/24  
    1032   676228-91-4   NaN     NaN    2019/6/24   2019/6/24  
    1033   120068-37-3   NaN     NaN    2019/6/24   2019/6/24  
    1034    74712-19-9   NaN     NaN    2019/6/26   2019/6/26  
    1035     2797-51-5   NaN     NaN    2019/6/26   2019/6/26  
    1036    51218-49-6   NaN     NaN    2019/6/26   2019/6/26  
    1037    96491-05-3   NaN     NaN    2019/6/26   2019/6/26  
    1038    73250-68-7   NaN     NaN   2019/06/26  2019/06/26  
    1039    69327-76-0   NaN     NaN   2019/07/09  2019/07/09  
    1040     3766-81-2   NaN     NaN     2019/9/2    2019/9/2  
    1041   105024-66-6   NaN     NaN     2019/9/2    2019/9/2  
    1042      556-52-5   NaN     NaN    2019/9/13   2019/9/13  
    1043      111-30-8   NaN     NaN    2019/9/13   2019/9/13  
    1044      110-49-6   NaN     NaN    2019/9/13   2019/9/13  
    1045      611-06-3   NaN     NaN    2019/9/13   2019/9/13  
    1046      101-83-7   NaN     NaN    2019/9/13   2019/9/13  
    1047       97-02-9   NaN     NaN   2019/09/13  2019/09/13  
    1048      624-92-0   NaN     NaN    2019/9/13   2019/9/13  
    1049       90-15-3   NaN     NaN    2019/9/13   2019/9/13  
    1050      135-19-3   NaN     NaN    2019/9/13   2019/9/13  
    1051      100-69-6   NaN     NaN    2019/9/13   2019/9/13  
    1052      100-40-3   NaN     NaN    2019/9/13   2019/9/13  
    1053      110-86-1   NaN     NaN    2019/9/13   2019/9/13  
    1054      108-99-6   NaN     NaN    2019/9/13   2019/9/13  
    1055     2528-36-1   NaN     NaN    2019/9/13   2019/9/13  
    
    [1056 rows x 11 columns]

CAS RNで揃えて（on='CAS'），ChemTHEATREのテーブルをベースに（how='left'）2つのテーブルをマージする。

```python
pd.merge(chemtheatre, webkis, on='CAS', how='left')
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
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
    <tr>
      <th>6</th>
      <td>CH0000007</td>
      <td>CG0003</td>
      <td>OctaCDD</td>
      <td>1,2,3,4,6,7,8,9-octachlorodibenzo-p-dioxin</td>
      <td>octachlorodibenzo-4-dioxin; OCDD</td>
      <td>18636</td>
      <td>3268-87-9</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2016/08/18</td>
      <td>2016/08/26</td>
      <td>KUR01004</td>
      <td>オクタクロロジベンゾ−パラ−ジオキシン</td>
      <td>NaN</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/KUR01004</td>
    </tr>
    <tr>
      <th>7</th>
      <td>CH0000008</td>
      <td>CG0004</td>
      <td>2,3,7,8-TCDF</td>
      <td>2,3,7,8-tetrachlorodibenzofuran</td>
      <td>2,3,7,8-TetraCDF; 2,3,7,8-TeCDF</td>
      <td>39929</td>
      <td>51207-31-9</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2016/08/18</td>
      <td>2016/08/26</td>
      <td>KUR01021</td>
      <td>２，３，７，８−テトラクロロジベンゾフラン</td>
      <td>2,3,7,8-Tetrachlorodibenzofuran</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/KUR01021</td>
    </tr>
    <tr>
      <th>8</th>
      <td>CH0000009</td>
      <td>CG0004</td>
      <td>1,2,3,7,8-PentaCDF</td>
      <td>1,2,3,7,8-pentachlorodibenzofuran</td>
      <td>1,2,3,7,8-PCDBF</td>
      <td>42138</td>
      <td>57117-41-6</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2016/8/18</td>
      <td>2016/8/26</td>
      <td>KUR01029</td>
      <td>１，２，３，７，８−ペンタクロロジベンゾフラン</td>
      <td>NaN</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/KUR01029</td>
    </tr>
    <tr>
      <th>9</th>
      <td>CH0000010</td>
      <td>CG0004</td>
      <td>2,3,4,7,8-PentaCDF</td>
      <td>2,3,4,7,8-pentachlorodibenzofuran</td>
      <td>2,3,4,7,8-pentachlorodibenzofuran</td>
      <td>42128</td>
      <td>57117-31-4</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2016/8/18</td>
      <td>2016/8/26</td>
      <td>KUR01028</td>
      <td>２，３，４，７，８−ペンタクロロジベンゾフラン</td>
      <td>NaN</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/KUR01028</td>
    </tr>
    <tr>
      <th>10</th>
      <td>CH0000011</td>
      <td>CG0004</td>
      <td>1,2,3,4,7,8-HxCDF</td>
      <td>1,2,3,4,7,8-hexachlorodibenzofuran</td>
      <td>1,2,3,4,7,8-HexaCDF; 1,2,3,4,7,8-HCDB</td>
      <td>51130</td>
      <td>70648-26-9</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2016/08/18</td>
      <td>2016/08/26</td>
      <td>KUR01053</td>
      <td>１，２，３，４，７，８−ヘキサクロロジベンゾフラン</td>
      <td>NaN</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/KUR01053</td>
    </tr>
    <tr>
      <th>11</th>
      <td>CH0000012</td>
      <td>CG0004</td>
      <td>1,2,3,6,7,8-HxCDF</td>
      <td>1,2,3,6,7,8-hexachlorodibenzofuran</td>
      <td>1,2,3,6,7,8-HexaCDF; 1,2,3,6,7,8-HEXACHLORODIB...</td>
      <td>42140</td>
      <td>57117-44-9</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2016/08/18</td>
      <td>2016/08/26</td>
      <td>KUR01030</td>
      <td>１，２，３，６，７，８−ヘキサクロロジベンゾフラン</td>
      <td>NaN</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/KUR01030</td>
    </tr>
    <tr>
      <th>12</th>
      <td>CH0000013</td>
      <td>CG0004</td>
      <td>1,2,3,7,8,9-HxCDF</td>
      <td>1,2,3,7,8,9-hexachlorodibenzofuran</td>
      <td>1,2,3,7,8,9-HexaCDF; 1,2,3,7,8,9-HEXACHLORODIB...</td>
      <td>51720</td>
      <td>72918-21-9</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2016/08/18</td>
      <td>2016/08/26</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>13</th>
      <td>CH0000014</td>
      <td>CG0004</td>
      <td>2,3,4,6,7,8-HxCDF</td>
      <td>2,3,4,6,7,8-hexachlorodibenzofuran</td>
      <td>2,3,4,6,7,8-HexaCDF; 2,3,4,6,7,8-HEXACHLORODIB...</td>
      <td>43495</td>
      <td>60851-34-5</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2016/08/18</td>
      <td>2016/08/26</td>
      <td>KUR01038</td>
      <td>２，３，４，６，７，８−ヘキサクロロジベンゾフラン</td>
      <td>NaN</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/KUR01038</td>
    </tr>
    <tr>
      <th>14</th>
      <td>CH0000015</td>
      <td>CG0004</td>
      <td>1,2,3,4,6,7,8-HpCDF</td>
      <td>1,2,3,4,6,7,8-heptachlorodibenzofuran</td>
      <td>1,2,3,4,6,7,8-HeptaCDF; 1,2,3,4,6,7,8-heptachl...</td>
      <td>38199</td>
      <td>67562-39-4</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2016/08/18</td>
      <td>2016/08/26</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>15</th>
      <td>CH0000016</td>
      <td>CG0004</td>
      <td>1,2,3,4,7,8,9-HpCDF</td>
      <td>1,2,3,4,7,8,9-heptachlorodibenzofuran</td>
      <td>1,2,3,4,7,8,9-HeptaCDF; 1,2,3,4,7,8,9-HEPTACHL...</td>
      <td>41510</td>
      <td>55673-89-7</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2016/08/18</td>
      <td>2016/08/26</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>16</th>
      <td>CH0000017</td>
      <td>CG0004</td>
      <td>OctaCDF</td>
      <td>1,2,3,4,6,7,8,9-octachlorodibenzofuran</td>
      <td>octachlorodibenzofuran; OCDF</td>
      <td>38200</td>
      <td>39001-02-0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2016/08/18</td>
      <td>2016/08/26</td>
      <td>BNS00357</td>
      <td>１，２，３，４，６，７，８，９−オクタクロロジベンゾフラン</td>
      <td>１，２，３，４，６，７，８，９−Ｏｃｔａｃｈｌｏｒｏｄｉｂｅｎｚｏｆｕｒａｎ；　１，２，３，...</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/BNS00357</td>
    </tr>
    <tr>
      <th>17</th>
      <td>CH0000018</td>
      <td>CG0003</td>
      <td>Total PCDDs</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
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
      <th>18</th>
      <td>CH0000019</td>
      <td>CG0004</td>
      <td>Total PCDFs</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
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
      <th>19</th>
      <td>CH0000020</td>
      <td>CG0002</td>
      <td>Total PCDD/Fs</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
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
      <th>20</th>
      <td>CH0000021</td>
      <td>CG0003</td>
      <td>PCDDs-TEQs</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
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
      <th>21</th>
      <td>CH0000022</td>
      <td>CG0004</td>
      <td>PCDFs-TEQs</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
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
      <th>22</th>
      <td>CH0000023</td>
      <td>CG0002</td>
      <td>PCDD/Fs-TEQs</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
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
      <th>23</th>
      <td>CH0000024</td>
      <td>CG0002</td>
      <td>Total TEQs</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
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
      <th>24</th>
      <td>CH0000025</td>
      <td>CG0014</td>
      <td>o,p'-DDE</td>
      <td>1-chloro-2-[2,2-dichloro-1-(4-chlorophenyl)eth...</td>
      <td>2,2-(2-chlorophenyl-4'-chlorophenyl)-1,1-dichl...</td>
      <td>246598</td>
      <td>3424-82-6</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2016/7/5</td>
      <td>2016/7/5</td>
      <td>KUR01007</td>
      <td>ｏ，ｐ’−ＤＤＥ</td>
      <td>o,p'-DDE</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/KUR01007</td>
    </tr>
    <tr>
      <th>25</th>
      <td>CH0000026</td>
      <td>CG0014</td>
      <td>o,p'-DDD</td>
      <td>1-chloro-2-[2,2-dichloro-1-(4-chlorophenyl)eth...</td>
      <td>Mitotane</td>
      <td>4211</td>
      <td>53-19-0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2016/7/5</td>
      <td>2016/7/5</td>
      <td>KUR01024</td>
      <td>NaN</td>
      <td>2,4'-DDD</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/KUR01024</td>
    </tr>
    <tr>
      <th>26</th>
      <td>CH0000027</td>
      <td>CG0014</td>
      <td>o,p'-DDT</td>
      <td>1-chloro-2-[2,2,2-trichloro-1-(4-chlorophenyl)...</td>
      <td>1,1,1-trichloro-2-(2-chlorophenyl)-2-(4-chloro...</td>
      <td>13089</td>
      <td>789-02-6</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2016/7/5</td>
      <td>2016/7/5</td>
      <td>KUR00684</td>
      <td>ｏ，ｐ’−ＤＤＴ</td>
      <td>O,P'-DDT</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/KUR00684</td>
    </tr>
    <tr>
      <th>27</th>
      <td>CH0000028</td>
      <td>CG0014</td>
      <td>Σo,p'-DDTs</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2016/7/5</td>
      <td>2016/7/5</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>28</th>
      <td>CH0000029</td>
      <td>CG0014</td>
      <td>p,p'-DDE</td>
      <td>1-chloro-4-[2,2-dichloro-1-(4-chlorophenyl)eth...</td>
      <td>1,1-dichloro-2,2-bis(p-chlorophenyl)ethylene</td>
      <td>3035</td>
      <td>72-55-9</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2016/7/5</td>
      <td>2016/7/5</td>
      <td>KUR00617</td>
      <td>ｐ，ｐ’−ジクロロジフェニルエチレン</td>
      <td>P,P'-DICHLORODIPHENYLDICHLOROETHYLENE</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/KUR00617</td>
    </tr>
    <tr>
      <th>29</th>
      <td>CH0000030</td>
      <td>CG0014</td>
      <td>p,p'-DDD</td>
      <td>1-chloro-4-[2,2-dichloro-1-(4-chlorophenyl)eth...</td>
      <td>Dichlorodiphenyldichloroethane</td>
      <td>6294</td>
      <td>72-54-8</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2016/7/5</td>
      <td>2016/7/5</td>
      <td>KUR00616</td>
      <td>ｐ，ｐ’−ジクロロジフェニルジクロロエタン</td>
      <td>P,P'-DICHLORODIPHENYLDICHLOROETHANE</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/KUR00616</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>1027</th>
      <td>CH0001028</td>
      <td>CG0049</td>
      <td>Nitenpyram</td>
      <td>(E)-1-N'-[(6-chloropyridin-3-yl)methyl]-1-N'-e...</td>
      <td>Niterndipoine; Bestguard; (E)-Nitenpyram; (1E)...</td>
      <td>3034287</td>
      <td>150824-47-8</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2019/6/24</td>
      <td>2019/6/24</td>
      <td>NT200055</td>
      <td>（Ｅ）−Ｎ−（６−クロロ−３−ピリジルメチル）−Ｎ−エチル−Ｎ’−メチル−２−ニトロビニリデ...</td>
      <td>NaN</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/NT200055</td>
    </tr>
    <tr>
      <th>1028</th>
      <td>CH0001029</td>
      <td>CG0049</td>
      <td>Thiacloprid</td>
      <td>[3-[(6-chloropyridin-3-yl)methyl]-1,3-thiazoli...</td>
      <td>Calypso; (3-((6-Chloro-3-pyridinyl)methyl)-2-t...</td>
      <td>115224</td>
      <td>111988-49-9</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2019/6/24</td>
      <td>2019/6/24</td>
      <td>DOK01982</td>
      <td>３−（６−クロロピリジン−３−イルメチル）−１・３−チアゾリジン−２−イリデンシアナミド</td>
      <td>THIACLOPRID</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/DOK01982</td>
    </tr>
    <tr>
      <th>1029</th>
      <td>CH0001030</td>
      <td>CG0049</td>
      <td>Thiamethoxam</td>
      <td>(NE)-N-[3-[(2-chloro-1,3-thiazol-5-yl)methyl]-...</td>
      <td>3-(2-Chloro-thiazol-5-ylmethyl)-5-methyl-(1,3,...</td>
      <td>5821911</td>
      <td>153719-23-4</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2019/6/24</td>
      <td>2019/6/24</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1030</th>
      <td>CH0001031</td>
      <td>CG0049</td>
      <td>CPF</td>
      <td>N-[(6-chloropyridin-3-yl)methyl]-N-ethylformamide</td>
      <td>N-(6-Chloro-3-pyridylmethyl)-N-ethylformamide;...</td>
      <td>101942083</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2019/6/24</td>
      <td>2019/6/24</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1031</th>
      <td>CH0001032</td>
      <td>CG0049</td>
      <td>Desnitro-imidacloprid</td>
      <td>1-[(6-chloropyridin-3-yl)methyl]-4,5-dihydroim...</td>
      <td>desnitroimidacloprid; 1-(6-chloro-pyridin-3-yl...</td>
      <td>10130527</td>
      <td>115970-17-7</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2019/6/24</td>
      <td>2019/6/24</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1032</th>
      <td>CH0001033</td>
      <td>CG0049</td>
      <td>IM-2-1</td>
      <td>N'-[(6-chloropyridin-3-yl)methyl]-N-cyanoethan...</td>
      <td>N-demethyl acetamiprid; N-Desmethylacetamiprid...</td>
      <td>11344811</td>
      <td>190604-92-3</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2019/6/24</td>
      <td>2019/6/24</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1033</th>
      <td>CH0001034</td>
      <td>CG0049</td>
      <td>Thiacloprid-amide</td>
      <td>(Z)-[3-[(6-chloropyridin-3-yl)methyl]-1,3-thia...</td>
      <td>thiacloprid amide; Urea, N-[3-[(6-chloro-3-pyr...</td>
      <td>16212161</td>
      <td>676228-91-4</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2019/6/24</td>
      <td>2019/6/24</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1034</th>
      <td>CH0001035</td>
      <td>CG0060</td>
      <td>Fipronil</td>
      <td>5-amino-1-[2,6-dichloro-4-(trifluoromethyl)phe...</td>
      <td>fipronil; Termidor; Fluocyanobenpyrazole;</td>
      <td>3352</td>
      <td>120068-37-3</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2019/6/24</td>
      <td>2019/6/24</td>
      <td>NT300103</td>
      <td>５−アミノ−１−（２，６−ジクロロ−４−トリフルオロメチルフェニル）−４−トリフルオロメチル...</td>
      <td>5-Amino-1-[2,6-dichloro-4-(trifluoromethyl)phe...</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/NT300103</td>
    </tr>
    <tr>
      <th>1035</th>
      <td>CH0001036</td>
      <td>CG0120</td>
      <td>Bromobutide</td>
      <td>2-bromo-3,3-dimethyl-N-(2-phenylpropan-2-yl)bu...</td>
      <td>bromobutide; (RS)-2-bromo-N-(alpha,alpha-dimet...</td>
      <td>53079</td>
      <td>74712-19-9</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2019/6/26</td>
      <td>2019/6/26</td>
      <td>NT300007</td>
      <td>（ＲＳ）−２−ブロモ−Ｎ−（α，α−ジメチルベンジル）−３，３−ジメチルブチルアミド</td>
      <td>(RS)-2-BROMO-N-(ALPHA,ALPHA-DIMETHYLBENZYL)-3,...</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/NT300007</td>
    </tr>
    <tr>
      <th>1036</th>
      <td>CH0001037</td>
      <td>CG0120</td>
      <td>Quinoclamine</td>
      <td>2-amino-3-chloronaphthalene-1,4-dione</td>
      <td>2-Amino-3-chloro-1,4-naphthoquinone; Quinoclam...</td>
      <td>17748</td>
      <td>2797-51-5</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2019/6/26</td>
      <td>2019/6/26</td>
      <td>NT300001</td>
      <td>２−アミノ−３−クロロ−１，４−ナフトキノン</td>
      <td>2-AMINO-3-CHLORO-1,4-NAPHTHOQUINONE</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/NT300001</td>
    </tr>
    <tr>
      <th>1037</th>
      <td>CH0001038</td>
      <td>CG0120</td>
      <td>Pretilachlor</td>
      <td>2-chloro-N-(2,6-diethylphenyl)-N-(2-propoxyeth...</td>
      <td>Solnet; pretilachlor; Acetamide, 2-chloro-N-(2...</td>
      <td>91644</td>
      <td>51218-49-6</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2019/6/26</td>
      <td>2019/6/26</td>
      <td>YOT00396</td>
      <td>２−クロロ−２’，６’−ジエチル−Ｎ−（２−プロポキシエチル）アセトアニリド</td>
      <td>2-CHLORO-2',6'-DIETHYL-N-(2-PROPOXYETHYL)ACETA...</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/YOT00396</td>
    </tr>
    <tr>
      <th>1038</th>
      <td>CH0001039</td>
      <td>CG0120</td>
      <td>Thenylchlor</td>
      <td>2-chloro-N-(2,6-dimethylphenyl)-N-[(3-methoxyt...</td>
      <td>Alherb; Acetamide, 2-chloro-N-(2,6-dimethylphe...</td>
      <td>443036</td>
      <td>96491-05-3</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2019/6/26</td>
      <td>2019/6/26</td>
      <td>NT300131</td>
      <td>２−クロロ−Ｎ−（３−メトキシ−２−チエニル）−２’，６’−ジメチルアセトアニリド</td>
      <td>NaN</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/NT300131</td>
    </tr>
    <tr>
      <th>1039</th>
      <td>CH0001040</td>
      <td>CG0120</td>
      <td>Mefenacet</td>
      <td>2-(1,3-benzothiazol-2-yloxy)-N-methyl-N-phenyl...</td>
      <td>2-(2-benzothiazolyl-oxy)-N-methyl-N-phenylacet...</td>
      <td>91716</td>
      <td>73250-68-7</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2019/06/26</td>
      <td>2019/06/26</td>
      <td>NT300009</td>
      <td>２−（２−ベンゾチアゾリルオキシ）−Ｎ−メチルアセトアニリド</td>
      <td>2-(2-BENZOTHIAZOLYLOXY)-N-METHYLACETANILIDE</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/NT300009</td>
    </tr>
    <tr>
      <th>1040</th>
      <td>CH0001041</td>
      <td>CG0060</td>
      <td>Buprofezin</td>
      <td>2-tert-butylimino-5-phenyl-3-propan-2-yl-1,3,5...</td>
      <td>Applaud; buprofezin; 2-tert-butylimino-3-isopr...</td>
      <td>50367</td>
      <td>69327-76-0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2019/07/09</td>
      <td>2019/07/09</td>
      <td>NT300185</td>
      <td>２−ｔ−ブチルイミノ−３−イソプロピル−５−フェニルペルヒドロ１，３，５−チアジアジン−４−オン</td>
      <td>2-T-BUTYLIMINO-3-ISOPROPYL-5-PHENYLPERHYDRO-1,...</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/NT300185</td>
    </tr>
    <tr>
      <th>1041</th>
      <td>CH0001042</td>
      <td>CG0048</td>
      <td>Fenobucarb</td>
      <td>(2-butan-2-ylphenyl) N-methylcarbamate</td>
      <td>BPMC; 2-(1-methylpropyl)phenyl methylcarbamate...</td>
      <td>19588</td>
      <td>3766-81-2</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2019/9/2</td>
      <td>2019/9/2</td>
      <td>YOK00014</td>
      <td>メチルカルバミン酸−２−ｓ−ブチルフェニル</td>
      <td>BASSA</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/YOK00014</td>
    </tr>
    <tr>
      <th>1042</th>
      <td>CH0001043</td>
      <td>CG0047</td>
      <td>Silafluofen</td>
      <td>(4-ethoxyphenyl)-[3-(4-fluoro-3-phenoxyphenyl)...</td>
      <td>silafluofen; Benzene, 4-[3-[(4-ethoxyphenyl)di...</td>
      <td>92430</td>
      <td>105024-66-6</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2019/9/2</td>
      <td>2019/9/2</td>
      <td>NT300108</td>
      <td>（４−エトキシフェニル）｛３−［（４−フルオロ−３−フェノキシ）フェニル］プロピル｝（ジメチ...</td>
      <td>Dimethyl(4-ethoxyphenyl)[3(4-fluoro-3-phenoxyp...</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/NT300108</td>
    </tr>
    <tr>
      <th>1043</th>
      <td>CH0001044</td>
      <td>CG0116</td>
      <td>2,3-Epoxy-1-propanol</td>
      <td>oxiran-2-ylmethanol</td>
      <td>2-Oxiranemethanol; Glycidol; oxiran-2-ylmethan...</td>
      <td>11164</td>
      <td>556-52-5</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2019/9/13</td>
      <td>2019/9/13</td>
      <td>TKY00032</td>
      <td>２，３−エポキシ−１−プロパノール</td>
      <td>2,3-EPOXY-1-PROPANOL</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/TKY00032</td>
    </tr>
    <tr>
      <th>1044</th>
      <td>CH0001045</td>
      <td>CG0116</td>
      <td>Glutaraldehyde</td>
      <td>pentanedial</td>
      <td>Pentanedial; glutaraldehyde; Glutaral; Glutari...</td>
      <td>3485</td>
      <td>111-30-8</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2019/9/13</td>
      <td>2019/9/13</td>
      <td>YOT00097</td>
      <td>グルタルアルデヒド</td>
      <td>GLUTARALDEHYDE</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/YOT00097</td>
    </tr>
    <tr>
      <th>1045</th>
      <td>CH0001046</td>
      <td>CG0116</td>
      <td>2-Methoxyethyl acetate</td>
      <td>2-methoxyethyl acetate</td>
      <td>ethylene glycol monomethyl ether acetate; 2-me...</td>
      <td>8054</td>
      <td>110-49-6</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2019/9/13</td>
      <td>2019/9/13</td>
      <td>TKV00088</td>
      <td>エチレングリコールモノメチルエーテル酢酸エステル</td>
      <td>ETHYLENEGLYCOLMONOMETHYLETHERACETATE</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/TKV00088</td>
    </tr>
    <tr>
      <th>1046</th>
      <td>CH0001047</td>
      <td>CG0115</td>
      <td>2,4-Dichloronitrobenzene</td>
      <td>2,4-dichloro-1-nitrobenzene</td>
      <td>2,4-dichloro-1-nitro-benzen; 2,4-DICHLORONITRO...</td>
      <td>11899</td>
      <td>611-06-3</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2019/9/13</td>
      <td>2019/9/13</td>
      <td>KN200921</td>
      <td>２，４−ジクロロニトロベンゼン</td>
      <td>2,4-DICHLORONITROBENZENE</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/KN200921</td>
    </tr>
    <tr>
      <th>1047</th>
      <td>CH0001048</td>
      <td>CG0116</td>
      <td>Dicyclohexylamine</td>
      <td>N-cyclohexylcyclohexanamine</td>
      <td>N,N-Dicyclohexylamine; DCHA; Cyclohexanamine, ...</td>
      <td>7582</td>
      <td>101-83-7</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2019/9/13</td>
      <td>2019/9/13</td>
      <td>YOT00162</td>
      <td>ジシクロヘキシルアミン</td>
      <td>DICYCLOHEXYLAMINE</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/YOT00162</td>
    </tr>
    <tr>
      <th>1048</th>
      <td>CH0001049</td>
      <td>CG0115</td>
      <td>2,4-Dinitroaniline</td>
      <td>2,4-dinitroaniline</td>
      <td>2,4-DINITROANILINE; Benzenamine, 2,4-dinitro-;...</td>
      <td>7321</td>
      <td>97-02-9</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2019/09/13</td>
      <td>2019/09/13</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1049</th>
      <td>CH0001050</td>
      <td>CG0116</td>
      <td>Dimethyl disulfide</td>
      <td>(methyldisulfanyl)methane</td>
      <td>Dimethyl disulfide; METHYL DISULFIDE; Dimethyl...</td>
      <td>12232</td>
      <td>624-92-0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2019/9/13</td>
      <td>2019/9/13</td>
      <td>TKY00101</td>
      <td>二硫化メチル</td>
      <td>DIMETHYLDISULFIDE</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/TKY00101</td>
    </tr>
    <tr>
      <th>1050</th>
      <td>CH0001051</td>
      <td>CG0116</td>
      <td>1-Naphthol</td>
      <td>naphthalen-1-ol</td>
      <td>1-NAPHTHOL; naphthalen-1-ol; alpha-naphthol; α...</td>
      <td>7005</td>
      <td>90-15-3</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2019/9/13</td>
      <td>2019/9/13</td>
      <td>BNT00166</td>
      <td>α−ナフトール</td>
      <td>ALPHA-NAPHTOL</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/BNT00166</td>
    </tr>
    <tr>
      <th>1051</th>
      <td>CH0001052</td>
      <td>CG0115</td>
      <td>2-Naphthalenol</td>
      <td>naphthalen-2-ol</td>
      <td>2-hydroxynaphthalene; 2-naphthol; beta-naphtho...</td>
      <td>8663</td>
      <td>135-19-3</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2019/9/13</td>
      <td>2019/9/13</td>
      <td>SEJ00337</td>
      <td>β−ナフトール</td>
      <td>BETA-NAPHTHOL</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/SEJ00337</td>
    </tr>
    <tr>
      <th>1052</th>
      <td>CH0001053</td>
      <td>CG0116</td>
      <td>2-Vinylpyridine</td>
      <td>2-ethenylpyridine</td>
      <td>2-Ethenylpyridine; Pyridine, 2-ethenyl-; 2-Pyr...</td>
      <td>7521</td>
      <td>100-69-6</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2019/9/13</td>
      <td>2019/9/13</td>
      <td>TKY00174</td>
      <td>２−ビニルピリジン</td>
      <td>2-VINYLPYRIDINE</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/TKY00174</td>
    </tr>
    <tr>
      <th>1053</th>
      <td>CH0001054</td>
      <td>CG0116</td>
      <td>4-Vinyl-1-cyclohexene</td>
      <td>4-ethenylcyclohexene</td>
      <td>4-Vinylcyclohexene; Cyclohexene, 4-ethenyl-; 4...</td>
      <td>7499</td>
      <td>100-40-3</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2019/9/13</td>
      <td>2019/9/13</td>
      <td>TKY00173</td>
      <td>４−ビニルシクロヘキセン</td>
      <td>4-VINYLCYCLOHEXENE</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/TKY00173</td>
    </tr>
    <tr>
      <th>1054</th>
      <td>CH0001055</td>
      <td>CG0116</td>
      <td>Pyridine</td>
      <td>pyridine</td>
      <td>PYRIDINE; Azabenzene; Azine; Pyridin; monopyri...</td>
      <td>1049</td>
      <td>110-86-1</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2019/9/13</td>
      <td>2019/9/13</td>
      <td>YOT00360</td>
      <td>ピリジン</td>
      <td>PYRIDINE</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/YOT00360</td>
    </tr>
    <tr>
      <th>1055</th>
      <td>CH0001056</td>
      <td>CG0115</td>
      <td>3-Methylpyridine</td>
      <td>3-methylpyridine</td>
      <td>3-METHYLPYRIDINE; 3-Picoline; beta-Picoline; P...</td>
      <td>7970</td>
      <td>108-99-6</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2019/9/13</td>
      <td>2019/9/13</td>
      <td>YOT00457</td>
      <td>３−メチルピリジン</td>
      <td>3-METHYLPYRIDINE</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/YOT00457</td>
    </tr>
    <tr>
      <th>1056</th>
      <td>CH0001057</td>
      <td>CG0116</td>
      <td>Dibutyl phenyl phosphate</td>
      <td>dibutyl phenyl phosphate</td>
      <td>dibutylphenylphosphate; Phosphoric acid, dibut...</td>
      <td>17312</td>
      <td>2528-36-1</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2019/9/13</td>
      <td>2019/9/13</td>
      <td>PRK00569</td>
      <td>ジブチルフェニルホスフェート</td>
      <td>DIBUTYLPHENYLPHOSPHATE</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/PRK00569</td>
    </tr>
  </tbody>
</table>
<p>1057 rows × 15 columns</p>
</div>




```python
chemicals_merged = pd.merge(chemtheatre, webkis, on='CAS', how='left')
```


```python
chemicals_merged.to_csv('chemtheatre_webkis_merged.tsv', sep='\t')
```


```python
link = '<a href ="'+chemicals_merged['URL']+'">Link to Webkis-plus</a>;'
```


```python
chemicals_merged['Remarks'] = link
```


```python
chemicals_merged
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
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
      <td>&lt;a href ="https://www.nies.go.jp/kisplus/dtl/c...</td>
      <td>2016/8/18</td>
      <td>2016/8/26</td>
      <td>KUR01014</td>
      <td>１，２，３，４，６，７，８−ヘプタクロロジベンゾ−パラ−ジオキシン</td>
      <td>NaN</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/KUR01014</td>
    </tr>
    <tr>
      <th>6</th>
      <td>CH0000007</td>
      <td>CG0003</td>
      <td>OctaCDD</td>
      <td>1,2,3,4,6,7,8,9-octachlorodibenzo-p-dioxin</td>
      <td>octachlorodibenzo-4-dioxin; OCDD</td>
      <td>18636</td>
      <td>3268-87-9</td>
      <td>NaN</td>
      <td>&lt;a href ="https://www.nies.go.jp/kisplus/dtl/c...</td>
      <td>2016/08/18</td>
      <td>2016/08/26</td>
      <td>KUR01004</td>
      <td>オクタクロロジベンゾ−パラ−ジオキシン</td>
      <td>NaN</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/KUR01004</td>
    </tr>
    <tr>
      <th>7</th>
      <td>CH0000008</td>
      <td>CG0004</td>
      <td>2,3,7,8-TCDF</td>
      <td>2,3,7,8-tetrachlorodibenzofuran</td>
      <td>2,3,7,8-TetraCDF; 2,3,7,8-TeCDF</td>
      <td>39929</td>
      <td>51207-31-9</td>
      <td>NaN</td>
      <td>&lt;a href ="https://www.nies.go.jp/kisplus/dtl/c...</td>
      <td>2016/08/18</td>
      <td>2016/08/26</td>
      <td>KUR01021</td>
      <td>２，３，７，８−テトラクロロジベンゾフラン</td>
      <td>2,3,7,8-Tetrachlorodibenzofuran</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/KUR01021</td>
    </tr>
    <tr>
      <th>8</th>
      <td>CH0000009</td>
      <td>CG0004</td>
      <td>1,2,3,7,8-PentaCDF</td>
      <td>1,2,3,7,8-pentachlorodibenzofuran</td>
      <td>1,2,3,7,8-PCDBF</td>
      <td>42138</td>
      <td>57117-41-6</td>
      <td>NaN</td>
      <td>&lt;a href ="https://www.nies.go.jp/kisplus/dtl/c...</td>
      <td>2016/8/18</td>
      <td>2016/8/26</td>
      <td>KUR01029</td>
      <td>１，２，３，７，８−ペンタクロロジベンゾフラン</td>
      <td>NaN</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/KUR01029</td>
    </tr>
    <tr>
      <th>9</th>
      <td>CH0000010</td>
      <td>CG0004</td>
      <td>2,3,4,7,8-PentaCDF</td>
      <td>2,3,4,7,8-pentachlorodibenzofuran</td>
      <td>2,3,4,7,8-pentachlorodibenzofuran</td>
      <td>42128</td>
      <td>57117-31-4</td>
      <td>NaN</td>
      <td>&lt;a href ="https://www.nies.go.jp/kisplus/dtl/c...</td>
      <td>2016/8/18</td>
      <td>2016/8/26</td>
      <td>KUR01028</td>
      <td>２，３，４，７，８−ペンタクロロジベンゾフラン</td>
      <td>NaN</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/KUR01028</td>
    </tr>
    <tr>
      <th>10</th>
      <td>CH0000011</td>
      <td>CG0004</td>
      <td>1,2,3,4,7,8-HxCDF</td>
      <td>1,2,3,4,7,8-hexachlorodibenzofuran</td>
      <td>1,2,3,4,7,8-HexaCDF; 1,2,3,4,7,8-HCDB</td>
      <td>51130</td>
      <td>70648-26-9</td>
      <td>NaN</td>
      <td>&lt;a href ="https://www.nies.go.jp/kisplus/dtl/c...</td>
      <td>2016/08/18</td>
      <td>2016/08/26</td>
      <td>KUR01053</td>
      <td>１，２，３，４，７，８−ヘキサクロロジベンゾフラン</td>
      <td>NaN</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/KUR01053</td>
    </tr>
    <tr>
      <th>11</th>
      <td>CH0000012</td>
      <td>CG0004</td>
      <td>1,2,3,6,7,8-HxCDF</td>
      <td>1,2,3,6,7,8-hexachlorodibenzofuran</td>
      <td>1,2,3,6,7,8-HexaCDF; 1,2,3,6,7,8-HEXACHLORODIB...</td>
      <td>42140</td>
      <td>57117-44-9</td>
      <td>NaN</td>
      <td>&lt;a href ="https://www.nies.go.jp/kisplus/dtl/c...</td>
      <td>2016/08/18</td>
      <td>2016/08/26</td>
      <td>KUR01030</td>
      <td>１，２，３，６，７，８−ヘキサクロロジベンゾフラン</td>
      <td>NaN</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/KUR01030</td>
    </tr>
    <tr>
      <th>12</th>
      <td>CH0000013</td>
      <td>CG0004</td>
      <td>1,2,3,7,8,9-HxCDF</td>
      <td>1,2,3,7,8,9-hexachlorodibenzofuran</td>
      <td>1,2,3,7,8,9-HexaCDF; 1,2,3,7,8,9-HEXACHLORODIB...</td>
      <td>51720</td>
      <td>72918-21-9</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2016/08/18</td>
      <td>2016/08/26</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>13</th>
      <td>CH0000014</td>
      <td>CG0004</td>
      <td>2,3,4,6,7,8-HxCDF</td>
      <td>2,3,4,6,7,8-hexachlorodibenzofuran</td>
      <td>2,3,4,6,7,8-HexaCDF; 2,3,4,6,7,8-HEXACHLORODIB...</td>
      <td>43495</td>
      <td>60851-34-5</td>
      <td>NaN</td>
      <td>&lt;a href ="https://www.nies.go.jp/kisplus/dtl/c...</td>
      <td>2016/08/18</td>
      <td>2016/08/26</td>
      <td>KUR01038</td>
      <td>２，３，４，６，７，８−ヘキサクロロジベンゾフラン</td>
      <td>NaN</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/KUR01038</td>
    </tr>
    <tr>
      <th>14</th>
      <td>CH0000015</td>
      <td>CG0004</td>
      <td>1,2,3,4,6,7,8-HpCDF</td>
      <td>1,2,3,4,6,7,8-heptachlorodibenzofuran</td>
      <td>1,2,3,4,6,7,8-HeptaCDF; 1,2,3,4,6,7,8-heptachl...</td>
      <td>38199</td>
      <td>67562-39-4</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2016/08/18</td>
      <td>2016/08/26</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>15</th>
      <td>CH0000016</td>
      <td>CG0004</td>
      <td>1,2,3,4,7,8,9-HpCDF</td>
      <td>1,2,3,4,7,8,9-heptachlorodibenzofuran</td>
      <td>1,2,3,4,7,8,9-HeptaCDF; 1,2,3,4,7,8,9-HEPTACHL...</td>
      <td>41510</td>
      <td>55673-89-7</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2016/08/18</td>
      <td>2016/08/26</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>16</th>
      <td>CH0000017</td>
      <td>CG0004</td>
      <td>OctaCDF</td>
      <td>1,2,3,4,6,7,8,9-octachlorodibenzofuran</td>
      <td>octachlorodibenzofuran; OCDF</td>
      <td>38200</td>
      <td>39001-02-0</td>
      <td>NaN</td>
      <td>&lt;a href ="https://www.nies.go.jp/kisplus/dtl/c...</td>
      <td>2016/08/18</td>
      <td>2016/08/26</td>
      <td>BNS00357</td>
      <td>１，２，３，４，６，７，８，９−オクタクロロジベンゾフラン</td>
      <td>１，２，３，４，６，７，８，９−Ｏｃｔａｃｈｌｏｒｏｄｉｂｅｎｚｏｆｕｒａｎ；　１，２，３，...</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/BNS00357</td>
    </tr>
    <tr>
      <th>17</th>
      <td>CH0000018</td>
      <td>CG0003</td>
      <td>Total PCDDs</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
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
      <th>18</th>
      <td>CH0000019</td>
      <td>CG0004</td>
      <td>Total PCDFs</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
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
      <th>19</th>
      <td>CH0000020</td>
      <td>CG0002</td>
      <td>Total PCDD/Fs</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
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
      <th>20</th>
      <td>CH0000021</td>
      <td>CG0003</td>
      <td>PCDDs-TEQs</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
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
      <th>21</th>
      <td>CH0000022</td>
      <td>CG0004</td>
      <td>PCDFs-TEQs</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
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
      <th>22</th>
      <td>CH0000023</td>
      <td>CG0002</td>
      <td>PCDD/Fs-TEQs</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
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
      <th>23</th>
      <td>CH0000024</td>
      <td>CG0002</td>
      <td>Total TEQs</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
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
      <th>24</th>
      <td>CH0000025</td>
      <td>CG0014</td>
      <td>o,p'-DDE</td>
      <td>1-chloro-2-[2,2-dichloro-1-(4-chlorophenyl)eth...</td>
      <td>2,2-(2-chlorophenyl-4'-chlorophenyl)-1,1-dichl...</td>
      <td>246598</td>
      <td>3424-82-6</td>
      <td>NaN</td>
      <td>&lt;a href ="https://www.nies.go.jp/kisplus/dtl/c...</td>
      <td>2016/7/5</td>
      <td>2016/7/5</td>
      <td>KUR01007</td>
      <td>ｏ，ｐ’−ＤＤＥ</td>
      <td>o,p'-DDE</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/KUR01007</td>
    </tr>
    <tr>
      <th>25</th>
      <td>CH0000026</td>
      <td>CG0014</td>
      <td>o,p'-DDD</td>
      <td>1-chloro-2-[2,2-dichloro-1-(4-chlorophenyl)eth...</td>
      <td>Mitotane</td>
      <td>4211</td>
      <td>53-19-0</td>
      <td>NaN</td>
      <td>&lt;a href ="https://www.nies.go.jp/kisplus/dtl/c...</td>
      <td>2016/7/5</td>
      <td>2016/7/5</td>
      <td>KUR01024</td>
      <td>NaN</td>
      <td>2,4'-DDD</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/KUR01024</td>
    </tr>
    <tr>
      <th>26</th>
      <td>CH0000027</td>
      <td>CG0014</td>
      <td>o,p'-DDT</td>
      <td>1-chloro-2-[2,2,2-trichloro-1-(4-chlorophenyl)...</td>
      <td>1,1,1-trichloro-2-(2-chlorophenyl)-2-(4-chloro...</td>
      <td>13089</td>
      <td>789-02-6</td>
      <td>NaN</td>
      <td>&lt;a href ="https://www.nies.go.jp/kisplus/dtl/c...</td>
      <td>2016/7/5</td>
      <td>2016/7/5</td>
      <td>KUR00684</td>
      <td>ｏ，ｐ’−ＤＤＴ</td>
      <td>O,P'-DDT</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/KUR00684</td>
    </tr>
    <tr>
      <th>27</th>
      <td>CH0000028</td>
      <td>CG0014</td>
      <td>Σo,p'-DDTs</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2016/7/5</td>
      <td>2016/7/5</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>28</th>
      <td>CH0000029</td>
      <td>CG0014</td>
      <td>p,p'-DDE</td>
      <td>1-chloro-4-[2,2-dichloro-1-(4-chlorophenyl)eth...</td>
      <td>1,1-dichloro-2,2-bis(p-chlorophenyl)ethylene</td>
      <td>3035</td>
      <td>72-55-9</td>
      <td>NaN</td>
      <td>&lt;a href ="https://www.nies.go.jp/kisplus/dtl/c...</td>
      <td>2016/7/5</td>
      <td>2016/7/5</td>
      <td>KUR00617</td>
      <td>ｐ，ｐ’−ジクロロジフェニルエチレン</td>
      <td>P,P'-DICHLORODIPHENYLDICHLOROETHYLENE</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/KUR00617</td>
    </tr>
    <tr>
      <th>29</th>
      <td>CH0000030</td>
      <td>CG0014</td>
      <td>p,p'-DDD</td>
      <td>1-chloro-4-[2,2-dichloro-1-(4-chlorophenyl)eth...</td>
      <td>Dichlorodiphenyldichloroethane</td>
      <td>6294</td>
      <td>72-54-8</td>
      <td>NaN</td>
      <td>&lt;a href ="https://www.nies.go.jp/kisplus/dtl/c...</td>
      <td>2016/7/5</td>
      <td>2016/7/5</td>
      <td>KUR00616</td>
      <td>ｐ，ｐ’−ジクロロジフェニルジクロロエタン</td>
      <td>P,P'-DICHLORODIPHENYLDICHLOROETHANE</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/KUR00616</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>1027</th>
      <td>CH0001028</td>
      <td>CG0049</td>
      <td>Nitenpyram</td>
      <td>(E)-1-N'-[(6-chloropyridin-3-yl)methyl]-1-N'-e...</td>
      <td>Niterndipoine; Bestguard; (E)-Nitenpyram; (1E)...</td>
      <td>3034287</td>
      <td>150824-47-8</td>
      <td>NaN</td>
      <td>&lt;a href ="https://www.nies.go.jp/kisplus/dtl/c...</td>
      <td>2019/6/24</td>
      <td>2019/6/24</td>
      <td>NT200055</td>
      <td>（Ｅ）−Ｎ−（６−クロロ−３−ピリジルメチル）−Ｎ−エチル−Ｎ’−メチル−２−ニトロビニリデ...</td>
      <td>NaN</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/NT200055</td>
    </tr>
    <tr>
      <th>1028</th>
      <td>CH0001029</td>
      <td>CG0049</td>
      <td>Thiacloprid</td>
      <td>[3-[(6-chloropyridin-3-yl)methyl]-1,3-thiazoli...</td>
      <td>Calypso; (3-((6-Chloro-3-pyridinyl)methyl)-2-t...</td>
      <td>115224</td>
      <td>111988-49-9</td>
      <td>NaN</td>
      <td>&lt;a href ="https://www.nies.go.jp/kisplus/dtl/c...</td>
      <td>2019/6/24</td>
      <td>2019/6/24</td>
      <td>DOK01982</td>
      <td>３−（６−クロロピリジン−３−イルメチル）−１・３−チアゾリジン−２−イリデンシアナミド</td>
      <td>THIACLOPRID</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/DOK01982</td>
    </tr>
    <tr>
      <th>1029</th>
      <td>CH0001030</td>
      <td>CG0049</td>
      <td>Thiamethoxam</td>
      <td>(NE)-N-[3-[(2-chloro-1,3-thiazol-5-yl)methyl]-...</td>
      <td>3-(2-Chloro-thiazol-5-ylmethyl)-5-methyl-(1,3,...</td>
      <td>5821911</td>
      <td>153719-23-4</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2019/6/24</td>
      <td>2019/6/24</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1030</th>
      <td>CH0001031</td>
      <td>CG0049</td>
      <td>CPF</td>
      <td>N-[(6-chloropyridin-3-yl)methyl]-N-ethylformamide</td>
      <td>N-(6-Chloro-3-pyridylmethyl)-N-ethylformamide;...</td>
      <td>101942083</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2019/6/24</td>
      <td>2019/6/24</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1031</th>
      <td>CH0001032</td>
      <td>CG0049</td>
      <td>Desnitro-imidacloprid</td>
      <td>1-[(6-chloropyridin-3-yl)methyl]-4,5-dihydroim...</td>
      <td>desnitroimidacloprid; 1-(6-chloro-pyridin-3-yl...</td>
      <td>10130527</td>
      <td>115970-17-7</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2019/6/24</td>
      <td>2019/6/24</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1032</th>
      <td>CH0001033</td>
      <td>CG0049</td>
      <td>IM-2-1</td>
      <td>N'-[(6-chloropyridin-3-yl)methyl]-N-cyanoethan...</td>
      <td>N-demethyl acetamiprid; N-Desmethylacetamiprid...</td>
      <td>11344811</td>
      <td>190604-92-3</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2019/6/24</td>
      <td>2019/6/24</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1033</th>
      <td>CH0001034</td>
      <td>CG0049</td>
      <td>Thiacloprid-amide</td>
      <td>(Z)-[3-[(6-chloropyridin-3-yl)methyl]-1,3-thia...</td>
      <td>thiacloprid amide; Urea, N-[3-[(6-chloro-3-pyr...</td>
      <td>16212161</td>
      <td>676228-91-4</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2019/6/24</td>
      <td>2019/6/24</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1034</th>
      <td>CH0001035</td>
      <td>CG0060</td>
      <td>Fipronil</td>
      <td>5-amino-1-[2,6-dichloro-4-(trifluoromethyl)phe...</td>
      <td>fipronil; Termidor; Fluocyanobenpyrazole;</td>
      <td>3352</td>
      <td>120068-37-3</td>
      <td>NaN</td>
      <td>&lt;a href ="https://www.nies.go.jp/kisplus/dtl/c...</td>
      <td>2019/6/24</td>
      <td>2019/6/24</td>
      <td>NT300103</td>
      <td>５−アミノ−１−（２，６−ジクロロ−４−トリフルオロメチルフェニル）−４−トリフルオロメチル...</td>
      <td>5-Amino-1-[2,6-dichloro-4-(trifluoromethyl)phe...</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/NT300103</td>
    </tr>
    <tr>
      <th>1035</th>
      <td>CH0001036</td>
      <td>CG0120</td>
      <td>Bromobutide</td>
      <td>2-bromo-3,3-dimethyl-N-(2-phenylpropan-2-yl)bu...</td>
      <td>bromobutide; (RS)-2-bromo-N-(alpha,alpha-dimet...</td>
      <td>53079</td>
      <td>74712-19-9</td>
      <td>NaN</td>
      <td>&lt;a href ="https://www.nies.go.jp/kisplus/dtl/c...</td>
      <td>2019/6/26</td>
      <td>2019/6/26</td>
      <td>NT300007</td>
      <td>（ＲＳ）−２−ブロモ−Ｎ−（α，α−ジメチルベンジル）−３，３−ジメチルブチルアミド</td>
      <td>(RS)-2-BROMO-N-(ALPHA,ALPHA-DIMETHYLBENZYL)-3,...</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/NT300007</td>
    </tr>
    <tr>
      <th>1036</th>
      <td>CH0001037</td>
      <td>CG0120</td>
      <td>Quinoclamine</td>
      <td>2-amino-3-chloronaphthalene-1,4-dione</td>
      <td>2-Amino-3-chloro-1,4-naphthoquinone; Quinoclam...</td>
      <td>17748</td>
      <td>2797-51-5</td>
      <td>NaN</td>
      <td>&lt;a href ="https://www.nies.go.jp/kisplus/dtl/c...</td>
      <td>2019/6/26</td>
      <td>2019/6/26</td>
      <td>NT300001</td>
      <td>２−アミノ−３−クロロ−１，４−ナフトキノン</td>
      <td>2-AMINO-3-CHLORO-1,4-NAPHTHOQUINONE</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/NT300001</td>
    </tr>
    <tr>
      <th>1037</th>
      <td>CH0001038</td>
      <td>CG0120</td>
      <td>Pretilachlor</td>
      <td>2-chloro-N-(2,6-diethylphenyl)-N-(2-propoxyeth...</td>
      <td>Solnet; pretilachlor; Acetamide, 2-chloro-N-(2...</td>
      <td>91644</td>
      <td>51218-49-6</td>
      <td>NaN</td>
      <td>&lt;a href ="https://www.nies.go.jp/kisplus/dtl/c...</td>
      <td>2019/6/26</td>
      <td>2019/6/26</td>
      <td>YOT00396</td>
      <td>２−クロロ−２’，６’−ジエチル−Ｎ−（２−プロポキシエチル）アセトアニリド</td>
      <td>2-CHLORO-2',6'-DIETHYL-N-(2-PROPOXYETHYL)ACETA...</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/YOT00396</td>
    </tr>
    <tr>
      <th>1038</th>
      <td>CH0001039</td>
      <td>CG0120</td>
      <td>Thenylchlor</td>
      <td>2-chloro-N-(2,6-dimethylphenyl)-N-[(3-methoxyt...</td>
      <td>Alherb; Acetamide, 2-chloro-N-(2,6-dimethylphe...</td>
      <td>443036</td>
      <td>96491-05-3</td>
      <td>NaN</td>
      <td>&lt;a href ="https://www.nies.go.jp/kisplus/dtl/c...</td>
      <td>2019/6/26</td>
      <td>2019/6/26</td>
      <td>NT300131</td>
      <td>２−クロロ−Ｎ−（３−メトキシ−２−チエニル）−２’，６’−ジメチルアセトアニリド</td>
      <td>NaN</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/NT300131</td>
    </tr>
    <tr>
      <th>1039</th>
      <td>CH0001040</td>
      <td>CG0120</td>
      <td>Mefenacet</td>
      <td>2-(1,3-benzothiazol-2-yloxy)-N-methyl-N-phenyl...</td>
      <td>2-(2-benzothiazolyl-oxy)-N-methyl-N-phenylacet...</td>
      <td>91716</td>
      <td>73250-68-7</td>
      <td>NaN</td>
      <td>&lt;a href ="https://www.nies.go.jp/kisplus/dtl/c...</td>
      <td>2019/06/26</td>
      <td>2019/06/26</td>
      <td>NT300009</td>
      <td>２−（２−ベンゾチアゾリルオキシ）−Ｎ−メチルアセトアニリド</td>
      <td>2-(2-BENZOTHIAZOLYLOXY)-N-METHYLACETANILIDE</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/NT300009</td>
    </tr>
    <tr>
      <th>1040</th>
      <td>CH0001041</td>
      <td>CG0060</td>
      <td>Buprofezin</td>
      <td>2-tert-butylimino-5-phenyl-3-propan-2-yl-1,3,5...</td>
      <td>Applaud; buprofezin; 2-tert-butylimino-3-isopr...</td>
      <td>50367</td>
      <td>69327-76-0</td>
      <td>NaN</td>
      <td>&lt;a href ="https://www.nies.go.jp/kisplus/dtl/c...</td>
      <td>2019/07/09</td>
      <td>2019/07/09</td>
      <td>NT300185</td>
      <td>２−ｔ−ブチルイミノ−３−イソプロピル−５−フェニルペルヒドロ１，３，５−チアジアジン−４−オン</td>
      <td>2-T-BUTYLIMINO-3-ISOPROPYL-5-PHENYLPERHYDRO-1,...</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/NT300185</td>
    </tr>
    <tr>
      <th>1041</th>
      <td>CH0001042</td>
      <td>CG0048</td>
      <td>Fenobucarb</td>
      <td>(2-butan-2-ylphenyl) N-methylcarbamate</td>
      <td>BPMC; 2-(1-methylpropyl)phenyl methylcarbamate...</td>
      <td>19588</td>
      <td>3766-81-2</td>
      <td>NaN</td>
      <td>&lt;a href ="https://www.nies.go.jp/kisplus/dtl/c...</td>
      <td>2019/9/2</td>
      <td>2019/9/2</td>
      <td>YOK00014</td>
      <td>メチルカルバミン酸−２−ｓ−ブチルフェニル</td>
      <td>BASSA</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/YOK00014</td>
    </tr>
    <tr>
      <th>1042</th>
      <td>CH0001043</td>
      <td>CG0047</td>
      <td>Silafluofen</td>
      <td>(4-ethoxyphenyl)-[3-(4-fluoro-3-phenoxyphenyl)...</td>
      <td>silafluofen; Benzene, 4-[3-[(4-ethoxyphenyl)di...</td>
      <td>92430</td>
      <td>105024-66-6</td>
      <td>NaN</td>
      <td>&lt;a href ="https://www.nies.go.jp/kisplus/dtl/c...</td>
      <td>2019/9/2</td>
      <td>2019/9/2</td>
      <td>NT300108</td>
      <td>（４−エトキシフェニル）｛３−［（４−フルオロ−３−フェノキシ）フェニル］プロピル｝（ジメチ...</td>
      <td>Dimethyl(4-ethoxyphenyl)[3(4-fluoro-3-phenoxyp...</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/NT300108</td>
    </tr>
    <tr>
      <th>1043</th>
      <td>CH0001044</td>
      <td>CG0116</td>
      <td>2,3-Epoxy-1-propanol</td>
      <td>oxiran-2-ylmethanol</td>
      <td>2-Oxiranemethanol; Glycidol; oxiran-2-ylmethan...</td>
      <td>11164</td>
      <td>556-52-5</td>
      <td>NaN</td>
      <td>&lt;a href ="https://www.nies.go.jp/kisplus/dtl/c...</td>
      <td>2019/9/13</td>
      <td>2019/9/13</td>
      <td>TKY00032</td>
      <td>２，３−エポキシ−１−プロパノール</td>
      <td>2,3-EPOXY-1-PROPANOL</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/TKY00032</td>
    </tr>
    <tr>
      <th>1044</th>
      <td>CH0001045</td>
      <td>CG0116</td>
      <td>Glutaraldehyde</td>
      <td>pentanedial</td>
      <td>Pentanedial; glutaraldehyde; Glutaral; Glutari...</td>
      <td>3485</td>
      <td>111-30-8</td>
      <td>NaN</td>
      <td>&lt;a href ="https://www.nies.go.jp/kisplus/dtl/c...</td>
      <td>2019/9/13</td>
      <td>2019/9/13</td>
      <td>YOT00097</td>
      <td>グルタルアルデヒド</td>
      <td>GLUTARALDEHYDE</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/YOT00097</td>
    </tr>
    <tr>
      <th>1045</th>
      <td>CH0001046</td>
      <td>CG0116</td>
      <td>2-Methoxyethyl acetate</td>
      <td>2-methoxyethyl acetate</td>
      <td>ethylene glycol monomethyl ether acetate; 2-me...</td>
      <td>8054</td>
      <td>110-49-6</td>
      <td>NaN</td>
      <td>&lt;a href ="https://www.nies.go.jp/kisplus/dtl/c...</td>
      <td>2019/9/13</td>
      <td>2019/9/13</td>
      <td>TKV00088</td>
      <td>エチレングリコールモノメチルエーテル酢酸エステル</td>
      <td>ETHYLENEGLYCOLMONOMETHYLETHERACETATE</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/TKV00088</td>
    </tr>
    <tr>
      <th>1046</th>
      <td>CH0001047</td>
      <td>CG0115</td>
      <td>2,4-Dichloronitrobenzene</td>
      <td>2,4-dichloro-1-nitrobenzene</td>
      <td>2,4-dichloro-1-nitro-benzen; 2,4-DICHLORONITRO...</td>
      <td>11899</td>
      <td>611-06-3</td>
      <td>NaN</td>
      <td>&lt;a href ="https://www.nies.go.jp/kisplus/dtl/c...</td>
      <td>2019/9/13</td>
      <td>2019/9/13</td>
      <td>KN200921</td>
      <td>２，４−ジクロロニトロベンゼン</td>
      <td>2,4-DICHLORONITROBENZENE</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/KN200921</td>
    </tr>
    <tr>
      <th>1047</th>
      <td>CH0001048</td>
      <td>CG0116</td>
      <td>Dicyclohexylamine</td>
      <td>N-cyclohexylcyclohexanamine</td>
      <td>N,N-Dicyclohexylamine; DCHA; Cyclohexanamine, ...</td>
      <td>7582</td>
      <td>101-83-7</td>
      <td>NaN</td>
      <td>&lt;a href ="https://www.nies.go.jp/kisplus/dtl/c...</td>
      <td>2019/9/13</td>
      <td>2019/9/13</td>
      <td>YOT00162</td>
      <td>ジシクロヘキシルアミン</td>
      <td>DICYCLOHEXYLAMINE</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/YOT00162</td>
    </tr>
    <tr>
      <th>1048</th>
      <td>CH0001049</td>
      <td>CG0115</td>
      <td>2,4-Dinitroaniline</td>
      <td>2,4-dinitroaniline</td>
      <td>2,4-DINITROANILINE; Benzenamine, 2,4-dinitro-;...</td>
      <td>7321</td>
      <td>97-02-9</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2019/09/13</td>
      <td>2019/09/13</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1049</th>
      <td>CH0001050</td>
      <td>CG0116</td>
      <td>Dimethyl disulfide</td>
      <td>(methyldisulfanyl)methane</td>
      <td>Dimethyl disulfide; METHYL DISULFIDE; Dimethyl...</td>
      <td>12232</td>
      <td>624-92-0</td>
      <td>NaN</td>
      <td>&lt;a href ="https://www.nies.go.jp/kisplus/dtl/c...</td>
      <td>2019/9/13</td>
      <td>2019/9/13</td>
      <td>TKY00101</td>
      <td>二硫化メチル</td>
      <td>DIMETHYLDISULFIDE</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/TKY00101</td>
    </tr>
    <tr>
      <th>1050</th>
      <td>CH0001051</td>
      <td>CG0116</td>
      <td>1-Naphthol</td>
      <td>naphthalen-1-ol</td>
      <td>1-NAPHTHOL; naphthalen-1-ol; alpha-naphthol; α...</td>
      <td>7005</td>
      <td>90-15-3</td>
      <td>NaN</td>
      <td>&lt;a href ="https://www.nies.go.jp/kisplus/dtl/c...</td>
      <td>2019/9/13</td>
      <td>2019/9/13</td>
      <td>BNT00166</td>
      <td>α−ナフトール</td>
      <td>ALPHA-NAPHTOL</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/BNT00166</td>
    </tr>
    <tr>
      <th>1051</th>
      <td>CH0001052</td>
      <td>CG0115</td>
      <td>2-Naphthalenol</td>
      <td>naphthalen-2-ol</td>
      <td>2-hydroxynaphthalene; 2-naphthol; beta-naphtho...</td>
      <td>8663</td>
      <td>135-19-3</td>
      <td>NaN</td>
      <td>&lt;a href ="https://www.nies.go.jp/kisplus/dtl/c...</td>
      <td>2019/9/13</td>
      <td>2019/9/13</td>
      <td>SEJ00337</td>
      <td>β−ナフトール</td>
      <td>BETA-NAPHTHOL</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/SEJ00337</td>
    </tr>
    <tr>
      <th>1052</th>
      <td>CH0001053</td>
      <td>CG0116</td>
      <td>2-Vinylpyridine</td>
      <td>2-ethenylpyridine</td>
      <td>2-Ethenylpyridine; Pyridine, 2-ethenyl-; 2-Pyr...</td>
      <td>7521</td>
      <td>100-69-6</td>
      <td>NaN</td>
      <td>&lt;a href ="https://www.nies.go.jp/kisplus/dtl/c...</td>
      <td>2019/9/13</td>
      <td>2019/9/13</td>
      <td>TKY00174</td>
      <td>２−ビニルピリジン</td>
      <td>2-VINYLPYRIDINE</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/TKY00174</td>
    </tr>
    <tr>
      <th>1053</th>
      <td>CH0001054</td>
      <td>CG0116</td>
      <td>4-Vinyl-1-cyclohexene</td>
      <td>4-ethenylcyclohexene</td>
      <td>4-Vinylcyclohexene; Cyclohexene, 4-ethenyl-; 4...</td>
      <td>7499</td>
      <td>100-40-3</td>
      <td>NaN</td>
      <td>&lt;a href ="https://www.nies.go.jp/kisplus/dtl/c...</td>
      <td>2019/9/13</td>
      <td>2019/9/13</td>
      <td>TKY00173</td>
      <td>４−ビニルシクロヘキセン</td>
      <td>4-VINYLCYCLOHEXENE</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/TKY00173</td>
    </tr>
    <tr>
      <th>1054</th>
      <td>CH0001055</td>
      <td>CG0116</td>
      <td>Pyridine</td>
      <td>pyridine</td>
      <td>PYRIDINE; Azabenzene; Azine; Pyridin; monopyri...</td>
      <td>1049</td>
      <td>110-86-1</td>
      <td>NaN</td>
      <td>&lt;a href ="https://www.nies.go.jp/kisplus/dtl/c...</td>
      <td>2019/9/13</td>
      <td>2019/9/13</td>
      <td>YOT00360</td>
      <td>ピリジン</td>
      <td>PYRIDINE</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/YOT00360</td>
    </tr>
    <tr>
      <th>1055</th>
      <td>CH0001056</td>
      <td>CG0115</td>
      <td>3-Methylpyridine</td>
      <td>3-methylpyridine</td>
      <td>3-METHYLPYRIDINE; 3-Picoline; beta-Picoline; P...</td>
      <td>7970</td>
      <td>108-99-6</td>
      <td>NaN</td>
      <td>&lt;a href ="https://www.nies.go.jp/kisplus/dtl/c...</td>
      <td>2019/9/13</td>
      <td>2019/9/13</td>
      <td>YOT00457</td>
      <td>３−メチルピリジン</td>
      <td>3-METHYLPYRIDINE</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/YOT00457</td>
    </tr>
    <tr>
      <th>1056</th>
      <td>CH0001057</td>
      <td>CG0116</td>
      <td>Dibutyl phenyl phosphate</td>
      <td>dibutyl phenyl phosphate</td>
      <td>dibutylphenylphosphate; Phosphoric acid, dibut...</td>
      <td>17312</td>
      <td>2528-36-1</td>
      <td>NaN</td>
      <td>&lt;a href ="https://www.nies.go.jp/kisplus/dtl/c...</td>
      <td>2019/9/13</td>
      <td>2019/9/13</td>
      <td>PRK00569</td>
      <td>ジブチルフェニルホスフェート</td>
      <td>DIBUTYLPHENYLPHOSPHATE</td>
      <td>https://www.nies.go.jp/kisplus/dtl/chem/PRK00569</td>
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
