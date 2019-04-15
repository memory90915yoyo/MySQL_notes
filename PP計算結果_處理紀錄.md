# 這是PP計算出所有property後 MySQL處理步驟的紀錄

先創新資料庫存放結果
```
CREATE DATABASE result_db
```

用workbrnch內建的 table data import wizard 以預設值把全部四個csv檔案都給匯入

```
schemas -> your db -> Tables -> right click -> table data import wizard
```

canoncial SMILE 設為primary key 檢查是否重複
```
ALTER TABLE result_db.result_7260_case_originaldata
MODIFY Original_Smiles VARCHAR(120)
```

```
ALTER TABLE result_db.result_7260_case_originaldata
ADD PRIMARY KEY (Original_Smiles)
```


