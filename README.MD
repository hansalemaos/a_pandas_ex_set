# Finds intersections / differences between pandas DataFrames

```python
$pip install a-pandas-ex-set
import numpy as np
import pandas as pd
from a_pandas_ex_set import Setdf
df = pd.read_csv("https://raw.githubusercontent.com/pandas-dev/pandas/main/doc/data/titanic.csv")

df2=pd.concat([df,df],ignore_index=True)
df2=df2.sample(len(df2))
df3,df4,df5=np.split(df2, 3)

setd=Setdf(df3,df4,df5)
columns=['Cabin', 'Embarked','Sex','Survived']
didis2=setd.get_difference_of_all(columns=columns)
didis3=setd.get_intersection_of_all(columns=columns)
didis4=setd.get_symmetric_difference_and(columns=columns)
print(didis2)
print(didis3)
print(didis4)

{0:       PassengerId  Survived  Pclass  ...      Fare    Cabin  Embarked
1631          741         1       1  ...   30.0000      D45         S
1411          521         1       1  ...   93.5000      B73         S
1164          274         0       1  ...   29.7000     C118         C
487           488         0       1  ...   29.7000      B37         C
248           249         1       1  ...   52.5542      D35         S
1615          725         1       1  ...   53.1000       E8         S
318           319         1       1  ...  164.8667       C7         S
337           338         1       1  ...  134.5000      E40         C
1753          863         1       1  ...   25.9292      D17         S
1642          752         1       3  ...   12.4750     E121         S
1536          646         1       1  ...   76.7292      D33         C
449           450         1       1  ...   30.5000     C104         S
1740          850         1       1  ...   89.1042      C92         C
1670          780         1       1  ...  211.3375       B3         S
571           572         1       1  ...   51.4792     C101         S
1680          790         0       1  ...   79.2000  B82 B84         C
1462          572         1       1  ...   51.4792     C101         S
31             32         1       1  ...  146.5208      B78         C
1100          210         1       1  ...   31.0000      A31         C
1340          450         1       1  ...   30.5000     C104         S
209           210         1       1  ...   31.0000      A31         C
943            53         1       1  ...   76.7292      D33         C
751           752         1       3  ...   12.4750     E121         S
558           559         1       1  ...   79.6500      E67         S
671           672         0       1  ...   52.0000      B71         S
724           725         1       1  ...   53.1000       E8         S
520           521         1       1  ...   93.5000      B73         S
849           850         1       1  ...   89.1042      C92         C
867           868         0       1  ...   50.4958      A24         S
1562          672         0       1  ...   52.0000      B71         S
779           780         1       1  ...  211.3375       B3         S
1228          338         1       1  ...  134.5000      E40         C
645           646         1       1  ...   76.7292      D33         C
1687          797         1       1  ...   25.9292      D17         S
862           863         1       1  ...   25.9292      D17         S
922            32         1       1  ...  146.5208      B78         C
1209          319         1       1  ...  164.8667       C7         S
1196          306         1       1  ...  151.5500  C22 C26         S
1758          868         0       1  ...   50.4958      A24         S
273           274         0       1  ...   29.7000     C118         C
1139          249         1       1  ...   52.5542      D35         S
796           797         1       1  ...   25.9292      D17         S
740           741         1       1  ...   30.0000      D45         S
789           790         0       1  ...   79.2000  B82 B84         C
52             53         1       1  ...   76.7292      D33         C
1378          488         0       1  ...   29.7000      B37         C
772           773         0       2  ...   10.5000      E77         S
305           306         1       1  ...  151.5500  C22 C26         S
1449          559         1       1  ...   79.6500      E67         S
1663          773         0       2  ...   10.5000      E77         S
[50 rows x 12 columns], 1:       PassengerId  Survived  Pclass  ...      Fare        Cabin  Embarked
21             22         1       2  ...   13.0000          D56         S
583           584         0       1  ...   40.1250          A10         C
445           446         1       1  ...   81.8583          A34         S
245           246         0       1  ...   90.0000          C78         Q
1476          586         1       1  ...   79.6500          E68         S
540           541         1       1  ...   71.0000          B22         S
366           367         1       1  ...   75.2500          D37         C
1136          246         0       1  ...   90.0000          C78         Q
879           880         1       1  ...   83.1583          C50         C
462           463         0       1  ...   38.5000          E63         S
1431          541         1       1  ...   71.0000          B22         S
275           276         1       1  ...   77.9583           D7         S
871           872         1       1  ...   52.5542          D35         S
1770          880         1       1  ...   83.1583          C50         C
1570          680         1       1  ...  512.3292  B51 B53 B55         C
1189          299         1       1  ...   30.5000         C106         S
912            22         1       2  ...   13.0000          D56         S
1762          872         1       1  ...   52.5542          D35         S
1590          700         0       3  ...    7.6500        F G63         S
1366          476         0       1  ...   52.0000          A14         S
1257          367         1       1  ...   75.2500          D37         C
1268          378         0       1  ...  211.5000          C82         C
700           701         1       1  ...  227.5250      C62 C64         C
1474          584         0       1  ...   40.1250          A10         C
585           586         1       1  ...   79.6500          E68         S
1166          276         1       1  ...   77.9583           D7         S
699           700         0       3  ...    7.6500        F G63         S
679           680         1       1  ...  512.3292  B51 B53 B55         C
630           631         1       1  ...   30.0000          A23         S
1353          463         0       1  ...   38.5000          E63         S
457           458         1       1  ...   51.8625          D21         S
1521          631         1       1  ...   30.0000          A23         S
475           476         0       1  ...   52.0000          A14         S
1336          446         1       1  ...   81.8583          A34         S
298           299         1       1  ...   30.5000         C106         S
1348          458         1       1  ...   51.8625          D21         S
377           378         0       1  ...  211.5000          C82         C
544           545         0       1  ...  106.4250          C86         C
284           285         0       1  ...   26.0000          A19         S
1435          545         0       1  ...  106.4250          C86         C
1591          701         1       1  ...  227.5250      C62 C64         C
1175          285         0       1  ...   26.0000          A19         S
[42 rows x 12 columns], 2:       PassengerId  Survived  Pclass  ...      Fare        Cabin  Embarked
872           873         0       1  ...    5.0000  B51 B53 B55         S
712           713         1       1  ...   52.0000         C126         S
618           619         1       2  ...   39.0000           F4         S
1061          171         0       1  ...   33.5000          B19         S
527           528         0       1  ...  221.7792          C95         S
1639          749         0       1  ...   53.1000          D30         S
1509          619         1       2  ...   39.0000           F4         S
1418          528         0       1  ...  221.7792          C95         S
339           340         0       1  ...   35.5000            T         S
647           648         1       1  ...   35.5000          A26         C
1538          648         1       1  ...   35.5000          A26         C
1763          873         0       1  ...    5.0000  B51 B53 B55         S
1115          225         1       1  ...   90.0000          C93         S
1603          713         1       1  ...   52.0000         C126         S
54             55         0       1  ...   61.9792          B30         C
1230          340         0       1  ...   35.5000            T         S
748           749         0       1  ...   53.1000          D30         S
170           171         0       1  ...   33.5000          B19         S
224           225         1       1  ...   90.0000          C93         S
118           119         0       1  ...  247.5208      B58 B60         C
3               4         1       1  ...   53.1000         C123         S
945            55         0       1  ...   61.9792          B30         C
894             4         1       1  ...   53.1000         C123         S
1009          119         0       1  ...  247.5208      B58 B60         C
[24 rows x 12 columns]}
{0:       PassengerId  Survived  Pclass  ...     Fare Cabin  Embarked
1546          656         0       2  ...  73.5000   NaN         S
1217          327         0       3  ...   6.2375   NaN         S
664           665         1       3  ...   7.9250   NaN         S
754           755         1       2  ...  65.0000   NaN         S
727           728         1       3  ...   7.7375   NaN         Q
           ...       ...     ...  ...      ...   ...       ...
1527          637         0       3  ...   7.9250   NaN         S
814           815         0       3  ...   8.0500   NaN         S
693           694         0       3  ...   7.2250   NaN         C
26             27         0       3  ...   7.2250   NaN         C
494           495         0       3  ...   8.0500   NaN         S
[459 rows x 12 columns], 1:       PassengerId  Survived  Pclass  ...     Fare Cabin  Embarked
1482          592         1       1  ...  78.2667   D20         C
552           553         0       3  ...   7.8292   NaN         Q
968            78         0       3  ...   8.0500   NaN         S
1205          315         0       2  ...  26.2500   NaN         S
1734          844         0       3  ...   6.4375   NaN         C
           ...       ...     ...  ...      ...   ...       ...
568           569         0       3  ...   7.2292   NaN         C
503           504         0       3  ...   9.5875   NaN         S
1544          654         1       3  ...   7.8292   NaN         Q
589           590         0       3  ...   8.0500   NaN         S
1191          301         1       3  ...   7.7500   NaN         Q
[471 rows x 12 columns], 2:       PassengerId  Survived  Pclass  ...     Fare Cabin  Embarked
1596          706         0       2  ...  26.0000   NaN         S
792           793         0       3  ...  69.5500   NaN         S
481           482         0       2  ...   0.0000   NaN         S
508           509         0       3  ...  22.5250   NaN         S
149           150         0       2  ...  13.0000   NaN         S
           ...       ...     ...  ...      ...   ...       ...
777           778         1       3  ...  12.4750   NaN         S
115           116         0       3  ...   7.9250   NaN         S
169           170         0       3  ...  56.4958   NaN         S
1162          272         1       3  ...   0.0000   NaN         S
963            73         0       2  ...  73.5000   NaN         S
[490 rows x 12 columns]}
{0:       PassengerId  Survived  Pclass  ...     Fare Cabin  Embarked
1546          656         0       2  ...  73.5000   NaN         S
1217          327         0       3  ...   6.2375   NaN         S
664           665         1       3  ...   7.9250   NaN         S
754           755         1       2  ...  65.0000   NaN         S
727           728         1       3  ...   7.7375   NaN         Q
           ...       ...     ...  ...      ...   ...       ...
814           815         0       3  ...   8.0500   NaN         S
1663          773         0       2  ...  10.5000   E77         S
693           694         0       3  ...   7.2250   NaN         C
26             27         0       3  ...   7.2250   NaN         C
494           495         0       3  ...   8.0500   NaN         S
[509 rows x 12 columns], 1:       PassengerId  Survived  Pclass  ...     Fare Cabin  Embarked
1482          592         1       1  ...  78.2667   D20         C
552           553         0       3  ...   7.8292   NaN         Q
968            78         0       3  ...   8.0500   NaN         S
1205          315         0       2  ...  26.2500   NaN         S
1734          844         0       3  ...   6.4375   NaN         C
           ...       ...     ...  ...      ...   ...       ...
568           569         0       3  ...   7.2292   NaN         C
503           504         0       3  ...   9.5875   NaN         S
1544          654         1       3  ...   7.8292   NaN         Q
589           590         0       3  ...   8.0500   NaN         S
1191          301         1       3  ...   7.7500   NaN         Q
[513 rows x 12 columns], 2:       PassengerId  Survived  Pclass  ...      Fare        Cabin  Embarked
872           873         0       1  ...    5.0000  B51 B53 B55         S
712           713         1       1  ...   52.0000         C126         S
1596          706         0       2  ...   26.0000          NaN         S
792           793         0       3  ...   69.5500          NaN         S
481           482         0       2  ...    0.0000          NaN         S
           ...       ...     ...  ...       ...          ...       ...
115           116         0       3  ...    7.9250          NaN         S
1009          119         0       1  ...  247.5208      B58 B60         C
169           170         0       3  ...   56.4958          NaN         S
1162          272         1       3  ...    0.0000          NaN         S
963            73         0       2  ...   73.5000          NaN         S
[514 rows x 12 columns]}


```