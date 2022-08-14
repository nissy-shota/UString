# UString

[original repository](https://github.com/Cogito2012/UString)

## environment
```bash
docker compose build
docker compose up -d
docker compose exec core bash
poetry install
poetry shell
pip install torch-scatter torch-sparse torch-cluster torch-spline-conv torch-geometric -f https://data.pyg.org/whl/torch-1.12.0+cu102.html
pip3 install -U openmim
mim install mmcv-full
```
[mmcv for torch 1.12.1](https://github.com/open-mmlab/mmcv/releases/tag/v1.6.1)

## CUDA and cuDNN version
```bash
cat /usr/local/cuda/version.txt
dpkg -l | grep "cudnn"
```

## Demo
```bash
python demo.py --task extract_feature --video_file demo/000821_vis.gif
```

## reference

[UString](https://github.com/Cogito2012/UString)

pip install mmcv-full=={1.1.6} -f https://download.openmmlab.com/mmcv/dist/cu102/torch1.12.1/index.html
