# UString

[original repository](https://github.com/Cogito2012/UString)

## environment
```bash
docker compose build
docker compose up -d
docker compose exec core bash
python3 -m pip install torch==1.2.0
python3 -m pip install torchvision==0.4.0
python3 -m pip install Cython==0.29.13
python3 -m pip install pycocotools==2.0.0
python3 -m pip install -r requirements.txt

mkdir lib
cd lib
git clone https://github.com/open-mmlab/mmdetection.git
cd mmdetection
git checkout v1.1.0  # important!
cp -r Cascade\ R-CNN/* ./
# compile & install
pip install -v -e .
cd ..
python3 -m pip install mmdetection/
```
[mmcv for torch 1.12.1](https://github.com/open-mmlab/mmcv/releases/tag/v1.6.1)

## CUDA and cuDNN version
```bash
cat /usr/local/cuda/version.txt
dpkg -l | grep "cudnn"
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

## reference

[UString](https://github.com/Cogito2012/UString)


python demo.py --task inference --feature_file $FEAT_FILE --ckpt_file demo/final_model_ccd.pth 
