# PPE Detection (K3 Industri) - YOLOv8n
## Ringkasan
Deteksi 7 kelas: person, hat, gloves, vest, no_hat, no_gloves, no_vest. Dataset `data_ppe` (200 foto), semuanya dianotasi (bounding box). Anotasi dibuat dengan bantuan AI (kotak person dari detektor, penilaian visual per orang, konversi ke format YOLO) dan belum diaudit orang kedua.
## Struktur
`dataset_yolo/{images,labels}/{train,val}`, `dataset_yolo/data.yaml`, `best.pt`, `PPE_Final_Workflow.ipynb`, `report_assets/`, `testing-file/` (lihat `testing-file/ATTRIBUTION.md`).
## Pengaturan
model yolov8n dari bobot yolov8n.pt; epoch maks 100 (dijalankan 78, terbaik 48); imgsz 640; batch 16; patience 30; seed 42; perangkat CPU (56.9 menit); split train 160 / val 40 (seed split dicari agar kelas langka ada di val).
## Keterbatasan
Data kecil, kelas no_hat/no_gloves/no_vest sedikit, metrik val kurang stabil; pelatihan di CPU. Detail di `Laporan_Take_Home_Assignment_Syauqi.pdf`.
