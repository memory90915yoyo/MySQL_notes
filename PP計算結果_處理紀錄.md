# 這是PP計算出所有property後 MySQL處理步驟的紀錄

## 存放資料
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

## 資料運算處理

先計算出IP Ea
```
CREATE TABLE result_db.ML_temp_7260case_v1
SELECT Original_Smiles AS Canonical_Smiles, 
Neutral_TotalDipole AS TotalDipole,
( (Cation_ZeroPointEnergy + Cation_ElectronicEnergy) - (Neutral_ZeroPointEnergy + Neutral_ElectronicEnergy) )  AS Ionization_energy, 
( (Neutral_ZeroPointEnergy + Neutral_ElectronicEnergy) - (Anion_ZeroPointEnergy + Anion_ElectronicEnergy) )  AS Electron_affinity
FROM result_db.result_7260_case_originaldata
```



再算出chemical Hardness 並且只抓需要的資料
```
CREATE TABLE result_db.ML_real_7260case_v1
SELECT Canonical_Smiles,
Electron_affinity,
(Ionization_energy - Electron_affinity) / 2 AS Chemical_hardness,
TotalDipole
FROM result_db.ML_temp_7260case_v1
```
最後export table
```
your table --> right click --> table data export wizard
```


# extra operation

重抓7260統計資料
```
CREATE TABLE result_db.ML_temp_7260case_v3
SELECT Original_Smiles AS Canonical_Smiles,
Neutral_HOMOEnergy AS HOMO,
Neutral_LUMOEnergy AS LUMO,
Neutral_TotalDipole AS TotalDipole,
( (Cation_ZeroPointEnergy + Cation_ElectronicEnergy) - (Neutral_ZeroPointEnergy + Neutral_ElectronicEnergy) )  AS Ionization_energy, 
( (Neutral_ZeroPointEnergy + Neutral_ElectronicEnergy) - (Anion_ZeroPointEnergy + Anion_ElectronicEnergy) )  AS Electron_affinity
FROM result_db.result_7260_case_originaldata
```

```
CREATE TABLE result_db.ML_real_7260case_v3
SELECT Canonical_Smiles,
HOMO,LUMO,
Electron_affinity AS EAv,
Ionization_energy AS IPv,
LUMO - HOMO AS Gap,
(Ionization_energy - Electron_affinity) / 2 AS Hardness,
TotalDipole
FROM result_db.ml_temp_7260case_v3
```







