# X-Ray Multi-Class Classification (ResNet50 Transfer Learning)

README siap-paste untuk `README.md`. Menggunakan bahasa Indonesia dan sudah ditambahkan emoji agar lebih hidup ✨.

---

## 📌 Deskripsi singkat

Proyek ini memakai **transfer learning** dengan backbone **ResNet50** (pretrained on ImageNet) untuk mengklasifikasikan gambar X-ray menjadi 4 kelas: `Covid-19`, `Normal`, `Viral Pneumonia`, dan `Bacterial Pneumonia`. Pipeline mencakup preprocessing, augmentasi sederhana, fine-tuning, serta evaluasi pada test set. 🖼️➡️🤖

---

## 🏗️ Arsitektur model (singkat)

* **Backbone**: ResNet50 (`weights='imagenet'`, `include_top=False`, input `(256,256,3)`).
* **Head**:

  * `AveragePooling2D(pool_size=(4,4))`
  * `Flatten`
  * `Dense(512, relu)` + `Dropout(0.4)`
  * `Dense(256, relu)` + `Dropout(0.3)`
  * `Dense(4, softmax)`
* **Loss / Optimizer / Metrics**: `categorical_crossentropy`, `RMSprop(lr=1e-4)` (atau coba `AdamW`), metric `accuracy`. ⚙️

---


## 📊 Hasil singkat

Contoh hasil yang pernah didapatkan pada eksperimen:

* Best `val_loss` ≈ `0.5289`
* `val_accuracy` sempat mencapai \~`0.8269`
* Evaluasi test set (contoh 40 gambar): test accuracy ≈ `0.675` (≈ 67.5%)
* Contoh `classification_report` (precision/recall/f1 per kelas) tersedia di notebook. 📈
