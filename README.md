# PPE Detection (K3 Industri) - YOLOv8n
## Ringkasan
Deteksi 7 kelas: person, hat, gloves, vest, no_hat, no_gloves, no_vest. Dataset `data_ppe` (200 foto); 130 foto dianotasi (bounding box), 70 belum dan tidak dipakai. Anotasi dibuat dengan bantuan AI (penilaian visual per orang, konversi ke format YOLO) dan belum diaudit orang kedua.
## Struktur
`dataset_yolo/{images,labels}/{train,val}`, `dataset_yolo/data.yaml`, `best.pt`, `PPE_Final_Workflow.ipynb`, `report_assets/`, `test_media/` (lihat `test_media/ATTRIBUTION.md`).
## Pengaturan
model yolov8n dari bobot yolov8n.pt; epoch maks 100 (dijalankan 89, terbaik 59); imgsz 640; batch 16; patience 30; seed 42; perangkat cpu; split train 104 / val 26 (seed split dicari agar kelas langka ada di val).
## Hasil (val, 26 gambar)
| Metrik | Nilai |
|---|---|
| mAP50 | 0.790 |
| mAP50-95 | 0.481 |
| Precision | 0.779 |
| Recall | 0.796 |

| Kelas | P | R | AP50 | AP50-95 | n val |
|---|---|---|---|---|---|
| person | 0.984 | 1.000 | 0.995 | 0.907 | 50 |
| vest | 0.974 | 1.000 | 0.995 | 0.770 | 37 |
| no_vest | 0.796 | 1.000 | 0.982 | 0.370 | 13 |
| hat | 0.827 | 0.946 | 0.952 | 0.648 | 37 |
| no_hat | 0.853 | 0.846 | 0.889 | 0.357 | 13 |
| gloves | 0.549 | 0.622 | 0.604 | 0.284 | 37 |
| no_gloves | 0.471 | 0.158 | 0.114 | 0.029 | 19 |

AC-5 (mAP50 > 0,85 dan mAP50-95 > 0,75): tidak terpenuhi.
## Keterbatasan
Data kecil, kelas no_hat/no_gloves/no_vest sedikit, metrik val tidak stabil; pelatihan di CPU. Detail di `Laporan_Take_Home_Assignment_Syauqi.pdf`.
