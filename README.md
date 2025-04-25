
# 🎯 Mục Tiêu

Hướng dẫn cài đặt và sử dụng mô hình đã được huấn luyện sẵn trên COCO với NanoDet để dự đoán đối tượng trên **ảnh**, **video** hoặc **webcam**.

---

## 🧰 1. Cài đặt môi trường

### Bước 1: Tạo và kích hoạt môi trường ảo

```bash
conda create -n nanodet python=3.8 -y
conda activate nanodet
```

### Bước 2: Cài đặt PyTorch

```bash
conda install pytorch torchvision cudatoolkit=11.1 -c pytorch -c conda-forge
```

---

## 📦 2. Clone mã nguồn & cài đặt NanoDet

```bash
git clone https://github.com/RangiLyu/nanodet.git
cd nanodet
pip install -r requirements.txt
python setup.py develop
```

---

## 📥 3. Tải mô hình huấn luyện sẵn

- **Checkpoint:** [NanoDet-Plus-m-416 (COCO pretrained)](https://github.com/RangiLyu/nanodet/releases)
- **Config:** `config/nanodet-plus-m_416.yml` (đã có sẵn trong repo)

> ✅ Đảm bảo file `.pth` và file `.yml` cùng tương ứng phiên bản.

---

## 📸 4. Chạy thử với ảnh

### Cú pháp chung:

```bash
python demo/demo.py image --config CONFIG_PATH --model MODEL_PATH --path IMAGE_PATH
```

### Ví dụ:

```bash
python demo/demo.py image \
--config config/nanodet-plus-m_416.yml \
--model nanodet-plus-m-416_20220219.pth \
--path test.jpg
```

> 💡 Lưu ý: Ảnh `test.jpg` cần đặt đúng đường dẫn hoặc ở thư mục gốc.

---

## 🎥 5. Chạy với video hoặc webcam

### Với video:

```bash
python demo/demo.py video \
--config config/nanodet-plus-m_416.yml \
--model nanodet-plus-m-416_20220219.pth \
--path video.mp4
```

### Với webcam:

```bash
python demo/demo.py webcam \
--config config/nanodet-plus-m_416.yml \
--model nanodet-plus-m-416_20220219.pth \
--camid 0
```

> 🔧 `--camid 0` là ID webcam mặc định, có thể thay đổi nếu có nhiều thiết bị camera.

---



## Run libtorch C++
 '''bash
 export PYTHONPATH=$PYTHONPATH:/home/an/an_workplace/ICD/obdetect_icd
'''