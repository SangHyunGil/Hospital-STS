conda create -n open-mmlab_cu10.0 python=3.7 -y
conda activate open-mmlab_cu10.0

conda install pytorch==1.2.0 torchvision==0.4.0 cudatoolkit=10.0 -c pytorch
conda install -c anaconda cython
conda install -c conda-forge lazy_import
pip install mmcv

cd mmskeleton
python setup.py develop

cd mmskeleton/ops/nms/
python setup_linux.py 

mmskl configs/recognition/st_gcn_aaai18/$DATASET/test.yaml
mmskl configs/recognition/st_gcn_aaai18/$DATASET/train.yaml
where the $DATASET must be ntu-rgbd-xsub, ntu-rgbd-xview or kinetics-skeleton 