# strongswan-SM
## 1.编译安装gmssl
GmSSL 3 采用了cmake构建系统。下载源代码后将其解压缩，进入源码目录，执行：  

mkdir build
cd build
cmake ..
make
make test
sudo make install
在make install完成后，GmSSL会在默认安装目录中安装gmssl命令行工具，在头文件目录中创建gmssl目录，并且在库目录中安装libgmssl.a、libgmssl.so等库文件。  

## 2.编译安装openssl兼容层
本项目依赖GmSSL主项目，需要首先安装GmSSL。  

OpenSSL-Compatible-Layer需要预先安装CMake和GCC编译工具链。下载 OpenSSL-Compatible-Layer 源代码并解压，进入源代码目录，执行  

mkdir build
cd build
cmake ..
make
sudo make install
在安装完成后，会在/usr/local/include目录下创建openssl目录并安装OpenSSL同名的头文件，并且在/usr/local/lib目录下安装libcrypto和libssl两个和OpenSSL同名的库文件。  

## 3.编译安装strongswan
参考https://docs.strongswan.org/docs/latest/install/install.html  

需要禁用自带openssl以调用本地的openssl兼容层

编译配置命令：  
./configure --prefix=/usr --sysconfdir=/etc --enable-systemd --disable-openssl --enable-kernel-libipsec --enable-kernel-netlink