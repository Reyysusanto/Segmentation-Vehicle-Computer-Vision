# Kelompok 6 – UTS Computer Vision

Pengolahan citra mobil: input citra, *image enhancement* (Contrast Stretching, Histogram Equalization, CLAHE + Median Filtering, evaluasi MSE/PSNR/SSIM), dan segmentasi objek (Otsu dan Adaptive Local Mean Thresholding + operasi morfologi).

## Struktur Project

```
Kelompok 6_UTS/
├── data/                 # dataset (tidak di-commit, lihat bagian Dataset)
│   ├── img/              # citra mobil (.jpg)
│   ├── masks/            # mask ground truth (.png)
│   └── masks_info.csv    # warna label setiap elemen mobil pada mask
├── notebooks/
│   └── Kelompok_6_Computer_Vision_Ujian_Tengah_Semester.ipynb
├── pyproject.toml        # daftar dependency (uv)
├── uv.lock
├── requirements.txt      # dependency untuk pip (hasil uv export)
└── README.md
```

## Dataset

Dataset: [Car Masks – TrainingData.pro (Kaggle)](https://www.kaggle.com/datasets/trainingdatapro/car-masks).

Notebook menentukan sumber dataset secara otomatis:

- **Lokal**: jika folder `data/` (berisi `img/`) ada di root project, data dibaca dari situ. Folder ini dicari dari direktori kerja notebook ke atas, sehingga notebook bisa dijalankan dari root project maupun dari `notebooks/`.
- **Google Colab** (atau jika folder `data/` tidak ada): dataset diunduh otomatis dari Kaggle dengan `kagglehub` ke `~/.cache/kagglehub/`.

Folder `data/` masuk `.gitignore`. Jika ingin memakai data lokal, salin isi folder `cars/` dari dataset (`img/`, `masks/`, `masks_info.csv`) ke `data/` sesuai struktur di atas.

## Cara Menjalankan

### Google Colab

Upload notebook dari folder `notebooks/` ke Colab lalu jalankan semua cell. Dataset akan diunduh otomatis.

### Lokal

Dengan [uv](https://docs.astral.sh/uv/) (Python 3.13):

```bash
uv sync
uv run --with jupyter jupyter lab
```

Atau dengan pip:

```bash
python -m venv .venv
.venv\Scripts\activate
pip install -r requirements.txt
```

Di VS Code cukup buka notebook di `notebooks/` lalu pilih kernel `.venv`.
