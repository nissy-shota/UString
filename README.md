# UString

[original repository](https://github.com/Cogito2012/UString)

## environment

## CUDA and cuDNN version
```bash
cat /usr/local/cuda/version.txt
dpkg -l | grep "cudnn"
```

# feature extraction environment

```bash
docker compose build
docker compose up -d
docker compose exec core bash
python3 -m pip install torch==1.4.0+cu100 torchvision==0.5.0+cu100 -f https://download.pytorch.org/whl/torch_stable.html
python3 -m pip install mmcv==0.4.2

mkdir lib
cd lib
git clone https://github.com/open-mmlab/mmdetection.git
cd mmdetection
git checkout v1.1.0  # important!
# Move the downloads from https://drive.google.com/drive/folders/1fbjKrzgXv_FobuIAS37k9beCkxYzVavi into mmdetection
cp -r Cascade\ R-CNN/* ./
# compile & install
python3 -m pip install -v -e .
cd ..
python3 -m pip install mmdetection/
python3 -m pip install Cython==0.29.13
python3 -m pip install pycocotools==2.0.0
```

# inference environment
```bash
docker compose build
docker compose up -d
docker compose exec inference bash

python3 -m pip install torch==1.2.0
python3 -m pip install torchvision==0.4.0
python3 -m pip install Cython==0.29.13
python3 -m pip install pycocotools==2.0.0
python3 -m pip install -r requirements.txt
```

## Demo
feature extraction
```bash
python3 demo.py --task extract_feature --video_file demo/000821_vis.gif
```

inference
```bash
python3 demo.py --task inference --feature_file demo/000821_vis_feature.npz
```

visualization
```bash
python3 demo.py --task visualize  --video_file demo/000821_vis.gif --result_file demo/000821_result.npz
```
> **Note**
> visualization and inference container are same. 

## reference

[UString](https://github.com/Cogito2012/UString)

