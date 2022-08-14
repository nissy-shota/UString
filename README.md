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
```

## CUDA and cuDNN version
```bash
cat /usr/local/cuda/version.txt
dpkg -l | grep "cudnn"
```

## reference

[UString](https://github.com/Cogito2012/UString)