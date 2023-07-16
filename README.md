cd docker 
./build.sh
./run.sh

cd /home/upup/graspnet-baseline/pointnet2
sudo python3 setup.py install

cd /home/upup/graspnet-baseline/knn
sudo python3 setup.py install

cd /home/upup/graspnetAPI
sudo pip3 install .


sudo apt install software-properties-common
sudo add-apt-repository ppa:deadsnakes/ppa -y
sudo apt install -y python3.9

sudo update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.8 2
sudo update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.9 3





mv tolerance.tar /home/upup/graspnet-baseline/dataset
cd /home/upup/graspnet-baseline/dataset
sudo tar -xvf tolerance.tar

cd /home/upup/graspnet-baseline
sudo mkdir -p data/Benchmark/graspnet/grasp_label
cd /home/upup/graspnet-baseline/dataset
sudo vim command_generate_tolerance_label.sh 
python3 generate_tolerance_label.py --dataset_root /home/upup/graspnet-baseline/data/Benchmark/graspnet --num_workers 50
:wq!
sh command_generate_tolerance_label.sh

