# LGB_KINOME_Internal

[Installation & Getting Started](#installation) <br>
  Create KinomePred conda environment
  ```
  conda env create -f environment.yml
  ```
  Go to root folder and un-pack the data zip file
  ```
  cd ./data/ && unzip init_kinomepred_data.zip && rm init_kinomepred_data.zip && cd ..
  ```

[Kinome Prediction Pipeline](#run_pipeline) <br>
Activate KinomePred env
```
conda activate KinomePred
```
Run the bash script kinomepred_parallel.sh to run the full Kinome prediction pipeline
```
nohup bash kinomepred_parallel.sh & 
```
[Prediction using combined multi-output model](#run_pipeline) <br>
Run the bash script kinome_prediction_multioutput.sh to run prediction using the multi-output model, compiled from the individual kinase activity prediction models.
```
bash kinome_prediction_multioutput.sh 
```
Or you may run the multi-output prediction on a different set of prospective data <prospective_data_path> and respective fingerprints data <prospective_data_feature_path>
```
params=("AAK1" "ABL1(E255K)-phosphorylated" "ABL1(F317I)-nonphosphorylated" "ABL1(F317I)-phosphorylated" "ABL1(F317L)-nonphosphorylated" "ABL1(F317L)-phosphorylated" "ABL1(H396P)-nonphosphorylated" "ABL1(H396P)-phosphorylated" "ABL1(M351T)-phosphorylated" "ABL1(Q252H)-nonphosphorylated" "ABL1(Q252H)-phosphorylated" "ABL1(T315I)-nonphosphorylated" "ABL1(T315I)-phosphorylated" "ABL1(Y253F)-phosphorylated" "ABL1-nonphosphorylated" "ABL1-phosphorylated" "ABL2" "ACVR1" "ACVR1B" "ACVR2A" "ACVR2B" "ACVRL1" "ADCK3" "ADCK4" "AKT1" "AKT2" "AKT3" "ALK" "ALK(C1156Y)" "ALK(L1196M)" "AMPK-alpha1" "AMPK-alpha2" "ANKK1" "ARK5" "ASK1" "ASK2" "AURKA" "AURKB" "AURKC" "AXL" "BIKE" "BLK" "BMPR1A" "BMPR1B" "BMPR2" "BMX" "BRAF" "BRAF(V600E)" "BRK" "BRSK1" "BRSK2" "BTK" "BUB1" "CAMK1" "CAMK1B" "CAMK1D" "CAMK1G" "CAMK2A" "CAMK2B" "CAMK2D" "CAMK2G" "CAMK4" "CAMKK1" "CAMKK2" "CASK" "CDC2L1" "CDC2L2" "CDC2L5" "CDK11" "CDK2" "CDK3" "CDK4" "CDK4-cyclinD1" "CDK4-cyclinD3" "CDK5" "CDK7" "CDK8" "CDK9" "CDKL1" "CDKL2" "CDKL3" "CDKL5" "CHEK1" "CHEK2" "CIT" "CLK1" "CLK2" "CLK3" "CLK4" "CSF1R" "CSF1R-autoinhibited" "CSK" "CSNK1A1" "CSNK1A1L" "CSNK1D" "CSNK1E" "CSNK1G1" "CSNK1G2" "CSNK1G3" "CSNK2A1" "CSNK2A2" "CTK" "DAPK1" "DAPK2" "DAPK3" "DCAMKL1" "DCAMKL2" "DCAMKL3" "DDR1" "DDR2" "DLK" "DMPK" "DMPK2" "DRAK1" "DRAK2" "DYRK1A" "DYRK1B" "DYRK2" "EGFR" "EGFR(E746-A750del)" "EGFR(G719C)" "EGFR(G719S)" "EGFR(L747-E749del, A750P)" "EGFR(L747-S752del, P753S)" "EGFR(L747-T751del,Sins)" "EGFR(L858R)" "EGFR(L858R,T790M)" "EGFR(L861Q)" "EGFR(S752-I759del)" "EGFR(T790M)" "EIF2AK1" "EPHA1" "EPHA2" "EPHA3" "EPHA4" "EPHA5" "EPHA6" "EPHA7" "EPHA8" "EPHB1" "EPHB2" "EPHB3" "EPHB4" "EPHB6" "ERBB2" "ERBB3" "ERBB4" "ERK1" "ERK2" "ERK3" "ERK4" "ERK5" "ERK8" "ERN1" "FAK" "FER" "FES" "FGFR1" "FGFR2" "FGFR3" "FGFR3(G697C)" "FGFR4" "FGR" "FLT1" "FLT3" "FLT3(D835H)" "FLT3(D835V)" "FLT3(D835Y)" "FLT3(ITD)" "FLT3(ITD,D835V)" "FLT3(ITD,F691l)" "FLT3(K663Q)" "FLT3(N841I)" "FLT3(R834Q)" "FLT3-autoinhibited" "FLT4" "FRK" "FYN" "GAK" "GCN2(Kin.Dom.2,S808G)" "GRK1" "GRK2" "GRK3" "GRK4" "GRK7" "GSK3A" "GSK3B" "HASPIN" "HCK" "HIPK1" "HIPK2" "HIPK3" "HIPK4" "HPK1" "HUNK" "ICK" "IGF1R" "IKK-alpha" "IKK-beta" "IKK-epsilon" "INSR" "INSRR" "IRAK1" "IRAK3" "IRAK4" "ITK" "JAK1(JH1domain-catalytic)" "JAK1(JH2domain-pseudokinase)" "JAK2(JH1domain-catalytic)" "JAK3(JH1domain-catalytic)" "JNK1" "JNK2" "JNK3" "KIT" "KIT(A829P)" "KIT(D816H)" "KIT(D816V)" "KIT(L576P)" "KIT(V559D)" "KIT(V559D,T670I)" "KIT(V559D,V654A)" "KIT-autoinhibited" "LATS1" "LATS2" "LCK" "LIMK1" "LIMK2" "LKB1" "LOK" "LRRK2" "LRRK2(G2019S)" "LTK" "LYN" "LZK" "MAK" "MAP3K1" "MAP3K15" "MAP3K2" "MAP3K3" "MAP3K4" "MAP4K2" "MAP4K3" "MAP4K4" "MAP4K5" "MAPKAPK2" "MAPKAPK5" "MARK1" "MARK2" "MARK3" "MARK4" "MAST1" "MEK1" "MEK2" "MEK3" "MEK4" "MEK5" "MEK6" "MELK" "MERTK" "MET" "MET(M1250T)" "MET(Y1235D)" "MINK" "MKK7" "MKNK1" "MKNK2" "MLCK" "MLK1" "MLK2" "MLK3" "MRCKA" "MRCKB" "MST1" "MST1R" "MST2" "MST3" "MST4" "MTOR" "MUSK" "MYLK" "MYLK2" "MYLK4" "MYO3A" "MYO3B" "NDR1" "NDR2" "NEK1" "NEK10" "NEK11" "NEK2" "NEK3" "NEK4" "NEK5" "NEK6" "NEK7" "NEK9" "NIK" "NIM1" "NLK" "OSR1" "p38-alpha" "p38-beta" "p38-delta" "p38-gamma" "PAK1" "PAK2" "PAK3" "PAK4" "PAK6" "PAK7" "PCTK1" "PCTK2" "PCTK3" "PDGFRA" "PDGFRB" "PDPK1" "PFCDPK1(P.falciparum)" "PFPK5(P.falciparum)" "PFTAIRE2" "PFTK1" "PHKG1" "PHKG2" "PIK3C2B" "PIK3C2G" "PIK3CA" "PIK3CA(C420R)" "PIK3CA(E542K)" "PIK3CA(E545A)" "PIK3CA(E545K)" "PIK3CA(H1047L)" "PIK3CA(H1047Y)" "PIK3CA(I800L)" "PIK3CA(M1043I)" "PIK3CA(Q546K)" "PIK3CB" "PIK3CD" "PIK3CG" "PIK4CB" "PIKFYVE" "PIM1" "PIM2" "PIM3" "PIP5K1A" "PIP5K1C" "PIP5K2B" "PIP5K2C" "PKAC-alpha" "PKAC-beta" "PKMYT1" "PKN1" "PKN2" "PKNB(M.tuberculosis)" "PLK1" "PLK2" "PLK3" "PLK4" "PRKCD" "PRKCE" "PRKCH" "PRKCI" "PRKCQ" "PRKD1" "PRKD2" "PRKD3" "PRKG1" "PRKG2" "PRKR" "PRKX" "PRP4" "PYK2" "QSK" "RAF1" "RET" "RET(M918T)" "RET(V804L)" "RET(V804M)" "RIOK1" "RIOK2" "RIOK3" "RIPK1" "RIPK2" "RIPK4" "RIPK5" "ROCK1" "ROCK2" "ROS1" "RPS6KA4(Kin.Dom.1-N-terminal)" "RPS6KA4(Kin.Dom.2-C-terminal)" "RPS6KA5(Kin.Dom.1-N-terminal)" "RPS6KA5(Kin.Dom.2-C-terminal)" "RSK1(Kin.Dom.1-N-terminal)" "RSK1(Kin.Dom.2-C-terminal)" "RSK2(Kin.Dom.1-N-terminal)" "RSK2(Kin.Dom.2-C-terminal)" "RSK3(Kin.Dom.1-N-terminal)" "RSK3(Kin.Dom.2-C-terminal)" "RSK4(Kin.Dom.1-N-terminal)" "RSK4(Kin.Dom.2-C-terminal)" "S6K1" "SBK1" "SGK" "SgK110" "SGK2" "SGK3" "SIK" "SIK2" "SLK" "SNARK" "SNRK" "SRC" "SRMS" "SRPK1" "SRPK2" "SRPK3" "STK16" "STK33" "STK35" "STK36" "STK39" "SYK" "TAK1" "TAOK1" "TAOK2" "TAOK3" "TBK1" "TEC" "TESK1" "TGFBR1" "TGFBR2" "TIE1" "TIE2" "TLK1" "TLK2" "TNIK" "TNK1" "TNK2" "TNNI3K" "TRKA" "TRKB" "TRKC" "TRPM6" "TSSK1B" "TSSK3" "TTK" "TXK" "TYK2(JH1domain-catalytic)" "TYK2(JH2domain-pseudokinase)" "TYRO3" "ULK1" "ULK2" "ULK3" "VEGFR2" "VPS34" "VRK2" "WEE1" "WEE2" "WNK1" "WNK2" "WNK3" "WNK4" "YANK1" "YANK2" "YANK3" "YES" "YSK1" "YSK4" "ZAK" "ZAP70")

source activate KinomePred
python ./code/ML_pred_V2.py <prospective_data_path> --structure_col 'Structure' --workflow 'predict' --activity "${params[@]}" --feature_path <prospective_data_feature_path> --task_type 'multiclass' --model './results/LGB/model_combined.rds' --results_path './results/LGB/'
```
