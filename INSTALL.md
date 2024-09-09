
```ZSH

# Install CUDA 11.8
wget wget https://developer.download.nvidia.com/compute/cuda/11.8.0/local_installers/cuda_11.8.0_520.61.05_linux.run
sudo chmod +x cuda_11.8.0_520.61.05_linux.run
sudo ./cuda_11.8.0_520.61.05_linux.run --silent --toolkit --override


conda create -n d3fields python=3.10 -y

# Change the cache directory to a local directory
pip config --user set global.cache-dir /juno/u/ziangcao/cache_local
# Verify the cache directory
pip cache dir

# Install the dependencies
conda activate d3fields


pip install torch==2.1.0 torchvision==0.16.0 torchaudio==2.1.0 --index-url https://download.pytorch.org/whl/cu118

pip install matplotlib dgl open3d scipy PyYAML lxml PyMCubes trimesh scikit-image transforms3d git+https://github.com/facebookresearch/segment-anything.git git+https://github.com/IDEA-Research/GroundingDINO.git tqdm
pip install ipykernel

python scripts/install_pytorch3d.py

# https://www.dgl.ai/pages/start.html
pip install  dgl -f https://data.dgl.ai/wheels/torch-2.1/cu118/repo.html


# Export the environment
conda env export --name d3fields > d3fields.yaml
```