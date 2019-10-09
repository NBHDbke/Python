# Python
Note

import os
import shutil

# os.getcwd()                    # 回傳str, 取得目前工作目錄之路徑
# os.chdir(str_path)             # 更改工作目錄至path
# os.mkdir(str_path)             # 根據path建立資料夾（無法用於建立檔案，另資料夾已存在會噴error）
# os.rmdir(str_path)             # 根據path刪除資料夾（無法用於刪除檔案）
# os.listdir(str_path)           # 回傳list, 顯示path包含的資料夾及檔案名稱（檔案會含副檔名）

# os.rename(str_src, str_dst)    # 更改資料夾或檔案之名稱（src → dst）
# os.remove(str_path)            # 刪除path之檔案（不適用資料夾）
# os.removedirs(str_path)        # 刪除path之資料夾（不適用"非空"的資料夾）

# os.path.exists(str_path)       # 判斷path之物件是否存在
# os.path.isfile(str_path)       # 判斷path之物件是否為檔案（txt,mp4,docx,xlsx...etc）
# os.path.isdir(str_path)        # 判斷path之物件是否為資料夾

# os.path.split(str_path)        # 回傳turple, 解析path之物件 →（物件位置, 物件名稱）     #1 物件之名稱會包含副檔名，資料夾之附檔名為空值""
# os.path.splitext(str_path)     # 回傳turple, 解析path之物件 →（物件位置, 物件之副檔名） #1 物件位置包含物件之名稱
# os.path.dirname(str_path)      # 回傳str, path的上一層位置（可視為：回傳該物件所在之位置）（可視為：解析path至倒數第二層）
# os.path.basename(str_path)     # 回傳str, path的物件名稱（含副檔名）（可視為：解析path之最後一層）
# os.path.getsize(str_path)      # 回傳int, path的物件之位元組大小

# shutil.copy(str_src, str_dst)  # 複製檔案（src → dst）（不適用於資料夾）
# shutil.move(str_src, str_dst)  # 移動檔案或資料夾（src → dst）
# shutil.rmtree(str_path)        # 刪除資料夾及其內部所有檔案（不適用於檔案）


#  open("file.path", "r", encoding = "UTF-8")
#                   　r for read； w for write（從開頭）； a for append（從結尾）

# soup.tag name              回傳該tag name的全部資訊（若該份XML中有多列具有相同tag name, 則回傳第一筆）
# soup.tag name.attrs        以dict回傳該tag name下的全部屬性（若該份XML中有多列具有相同tag name, 則回傳第一筆的屬性）
# soup.find_all()            以list回傳該soup下的全部tag name + attributes
# soup.find_all("tag name")  以list回傳該soup下所指定tag的全部資訊（含attributes）

from bs4 import BeautifulSoup
with open(r"D:\ana\123.xml", "r", encoding='UTF-8') as f:
    soup = BeautifulSoup(f, "xml")
    
#### xml.etree.ElementTree

try:
    import xml.etree.cElementTree as ET
except ImportError:
    import xml.etree.ElementTree as ET

# ET.parse(str_path)            # 回傳tree, 根據path直接讀取XML格式之檔案，並將其轉成tree型態
# tree.getroot()                # 回傳element, 該tree的root element

# element.tag                   # 回傳str,  該element的tag
# element.attrib                # 回傳dict, 該element的attributes及values
# element.keys()                # 回傳list, 該element的全部attributes名稱（官網說沒有順序，但感覺有照XML的排序回傳）
# element.items()               # 回傳list, list內的元素為turple, 該element的全部attributes名稱+值
# element.text                  # 回傳str, 該element的start tag與first child or end tag之間的文字
# element.tail                  # 回傳str, 該element的end tag與next tag之間的文字
# element.get(str_key)          # 回傳str, 該element之key attribute的值（若找不到該attribute，則回傳None） # element.get(str_key, default=None)
# element.set(str_key, value)   # 賦值, 將element的某屬性值設為value

# element.find(str_tag)         # 回傳element, 從element的child中，尋找該層符合規則的child（若有多筆，僅回傳第一筆）（若str_tag為孫子層會找不到 == None）
# element.findall(str_tag)      # 回傳list, element.find()的加強版，尋找符合規則的child（若有多筆，都會回傳）（若str_tag為孫子層會找不到 == None）
# element.iter(str_tag)         # 遞迴器, 從element開始，往下找至最後一層，回傳所有符合規則的element
# element.iterfind(str_tag)     # 遞迴器, 只適用child層

                                  # str_tag 可以是tag name或是XPath的path表示法
                                     # 選取當前的節點
                                        # root.findall(".")
                                     # 選取當前節點的全部child element
                                        # root.findall("*")
                                        # root.findall("**") → 找全部的孫子
                                        # root.findall("***") → 找全部的曾孫
                                     # 選取當前節點的全部subelements（包含孩子、孫子、曾孫...etc）
                                        # root.findall(".//")
                                        # root.findall(".//tag") → 只尋找名為tag的subelements
                                     # 選取名為tag & 屬性1=value1 & 屬性2=value2的elements
                                        # root.findall("tag[@attrib1='value1'][@attrib2='value2']")
                                     # 使用位置座標選取element
                                        # root[0]    → root的第一個孩子
                                        # root[0][0] → root的第一個孫子

# tree.write(str_path, encoding="UTF-8", xml_declaration=True)  # 輸出XML; xml_declaration=XML聲明






# None == None
# np.nan != np.nan               -> a scalar equality comparison versus a None/np.nan doesn’t provide useful information
# Pandas treats None like np.nan
  # a = pd.series([1,2,3]),   a[0] = None, a[0] will become NaN   -> print(a[0]) will return "nan"   -> call a[0] will return "nan"
  # a = pd.series([1,"2",3]), a[0] = None, a[0] will become None  -> print(a[0]) will return "None"  -> call a[0] will return nothing/empty
  # 第2種情境中，由於[1,"2",3]中包含型態不同元素，故這個series物件可視作一個容器，dtype = object
# type(np.nan) -> float
#

# establish a Series
s = pd.Series(data, index = list_index)

    # one-dimensional labeled array capable of holding any data type   i.e. 1 column with index name
    # data cane be: tuple, list, dict
    # if no index is passed, one will be created having values [0, ..., len(data) - 1]
    
    # 1個Series可視作一個僅有index name, 但沒有column name的直行, 呼叫會 return 2個直行, 第1行代表index names, 第2行代表values, 最後會附註dtype屬性
    # Series可視作只有一行的data-frame, 故 s.dtypes == s.dtype, 並回傳一個dtype屬性
    
    
# get index of a Series
s.index

    # s.index[idx]    can use idx to get the particular index, return in itself type: str/int...etc
    # s.index[slice]  can use slice to get a serices of index, return type can be: range/index...etc

