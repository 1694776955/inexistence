# inexistence

This branch is used for file storage for inexistence, including prebuilt debian packages, image host, softwares for scripts to wget and so on.

---

### libtorrent-rasterbar
```
apt-get install -y git build-essential python python-dev pkg-config autoconf automake libtool libssl-dev geoip-database libgeoip-dev libgl1-mesa-dev zlib1g-dev checkinstall
apt-get install -y libboost-dev libboost-system-dev libboost-chrono-dev libboost-random-dev libboost-python-dev

repo="https://github.com/airium/libtorrent"
branch=1.1
version=1.1.13.1
cpp_flag="CXXFLAGS=-std=c++11"
# boost_flag=--with-boost-libdir=/usr/lib

git clone --depth=1 -b $branch $repo libtorrent
cd libtorrent

./autotool.sh
./configure --enable-python-binding --with-libiconv --disable-debug --enable-encryption --with-libgeoip=system $cpp_flag $boost_flag
make -j$(nproc)
make install

mkdir -p doc-pak
echo "an efficient feature complete C++ bittorrent implementation, installed by inexistence script" 
checkinstall -y --pkgname=libtorrent-rasterbar --pkggroup libtorrent --pkgversion $version
```


### qt
```
apt-get install -y build-essential pkg-config automake libtool git screen libgeoip-dev python python-dev python3 python3-dev libgl1-mesa-dev libicu-dev libbz2-dev libssl-dev zlib1g-dev checkinstall screen
wget https://download.qt.io/archive/qt/5.9/5.9.8/single/qt-everywhere-opensource-src-5.9.8.tar.xz
tar xf qt-everywhere-opensource-src-5.9.8.tar.xz
cd qt-everywhere-opensource-src-5.9.8

./configure -release -opensource -confirm-license -strip -shared -ltcg -make libs -make tools -dbus -nomake examples -no-compile-examples -no-qml-debug -no-icu -no-gtk -no-opengles3 -no-angle -no-sql-sqlite -no-sql-odbc -no-sqlite -skip qt3d -skip qtactiveqt -skip qtandroidextras -skip qtcanvas3d -skip qtcharts -skip qtconnectivity -skip qtdatavis3d -skip qtdoc -skip qtgamepad -skip qtgraphicaleffects -skip qtimageformats -skip qtlocation -skip qtmacextras -skip qtmultimedia -skip qtnetworkauth -skip qtpurchasing -skip qtquickcontrols -skip qtquickcontrols2 -skip qtremoteobjects -skip qtscript -skip qtscxml -skip qtsensors -skip qtserialbus -skip qtserialport -skip qtspeech -skip qtvirtualkeyboard -skip qtwayland -skip qtwebchannel -skip qtwebengine -skip qtwebsockets -skip qtwebview -skip qtx11extras -skip qtxmlpatterns
make -j$(nproc)
make install

mkdir -p doc-pak
echo "Qt 5, installed by inexistence script" > description-pak
checkinstall -y --pkgname=qt --pkgversion=5.9.8 --pkggroup qt
```


### gcc
```
wget https://ftp.gnu.org/gnu/gcc/gcc-7.3.0/gcc-7.3.0.tar.xz
tar xf gcc-7.3.0.tar.xz
cd gcc-7.3.0

./contrib/download_prerequisites
mkdir objdir
cd objdir
../configure --enable-checking=release --enable-languages=c,c++ --disable-multilib
make -j$(nproc)
make install

mkdir -p doc-pak
echo "GNU C compiler, installed by inexistence script" > description-pak
checkinstall -y --pkgname=gcc-7.3.0 --pkggroup gcc --pkgversion 7.3.0
```
```
cp /usr/local/lib64/libstdc++.so.6.0.24 /usr/lib/x86_64-linux-gnu/
rm /usr/lib/x86_64-linux-gnu/libstdc++.so.6
ln -s /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.24 /usr/lib/x86_64-linux-gnu/libstdc++.so.6
```

---



### ffmpeg
```
https://johnvansickle.com/ffmpeg/
https://johnvansickle.com/ffmpeg/releases/ffmpeg-release-amd64-static.tar.xz
```


### rar
```
https://www.rarlab.com/download.htm
https://www.rarlab.com/rar/rarlinux-x64-5.7.1.tar.gz
```


### Linux Kernel
```
https://www.kernel.org/
https://kernel.ubuntu.com/~kernel-ppa/mainline/
http://xanmod.org/
https://sourceforge.net/projects/xanmod/files/releases/
```


### TCP Congestion Control
```
https://github.com/KozakaiAya/TCP_BBR
```



---



#### Miscellaneous 
```
dd if=/dev/zero of=/root/.swapfile bs=1M count=3072
mkswap /root/.swapfile
swapon /root/.swapfile
swapon -s

wget https://dl.bintray.com/boostorg/release/1.65.1/source/boost_1_65_1.tar.bz2
tar xf boost_1_65_1.tar.bz2
cd boost_1_65_1
./bootstrap.sh --with-libraries=all --prefix=/usr/local
./b2 -j$(nproc) toolset=gcc
./b2 install
ldconfig
cd ..
```








