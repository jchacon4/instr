# instr

RASPBIAN JESSIE　2016-05-27版を使用

最初にraspberry piを更新しておく

sudo rpi-update
sudo apt-get update
sudo apt-get upgrade

OpenCVのbuildに必要なファイルのインストール
sudo apt-get install -y cmake libgtk2.0-dev
sudo apt-get install -y libavcodec-dev libavformat-dev libswscale-dev libjpeg-dev libpng-dev libtiff-dev libjasper-dev libgstreamer0.10-dev v4l-utils libv4l-dev libgstreamer-plugins-base0.10-dev
sudo apt-get install -y python-dev python-numpy libeigen3-dev

ソースの準備
ホストPCでダウンロードした、OpenCV2.4.13.1のソースを展開して、外付けUSB HDDにコピー
USB　HDDをRaspberry Pi 3に接続する（USB HDDへの電源供給が不足しているとマウントされない）

2.4.13.1のフォルダーにbuildpi3を作成し、cd buildpi3

CMAKEの実行
cmake -DCMAKE_BUILD_TYPE=RELEASE -DENABLE_VFPV3=ON -DENABLE_NEON=ON -DBUILD_DOCS=OFF -DBUILD_TESTS=off -DBUILD_PERF_TESTS=OFF -DBUILD_TBB=ON -DBUILD_opencv_apps=OFF -DBUILD_opencv_gpu=OFF -DWITH_OPENCL=off -DWITH_1394=off -DWITH_CUDA=OFF -DWITH_CUFFT=OFF -DWITH_GIGEAPI=OFF -DWITH_OPENCLAMDBLAS=off -DWITH_OPENCLAMDFFT=off -DWITH_TBB=ON ..

ビルド
time make -j4でビルドを行う

ビルド時間
real    41m55.667s
user    147m11.760s
sys    4m29.960s

インストール
sudo make install
sudo ldconfig

以上
