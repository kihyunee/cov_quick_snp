
Before installing things, you need gcc and zlib.

Use the following commands one by one, assuming that you're using Ubuntu system.

```
sudo apt-get update

sudo apt install build-essential

sudo apt install zlib1g-dev

sudo apt-get install libbz2-dev

sudo apt install liblzma-dev

sudo apt-get install -y libncurses5-dev

```


If you have not extracted the `package_v1.tar.gz` yet, do this.

```
tar -xzf package_v1.tar.gz

cd package_v1/
```

Otherwise, go to `package_v1` directory and run the installation script `INITIAL_INSTALL_once.sh`

```
chmod 755 INITIAL_INSTALL_once.sh

./INITIAL_INSTALL_once.sh

source ~/.bashrc
```


The contents of `INITIAL_INSTALL_once.sh` is like this:

```
COV_PKG_BASE=$(pwd)

mkdir dependency/bin

cd dependency/bcftools-1.15.1

./configure --prefix=${COV_PKG_BASE}/dependency/

make

make install

cd ../minimap2/

make

cp minimap2 ${COV_PKG_BASE}/dependency/bin/

cd ../samtools-1.15.1/

./configure --prefix=${COV_PKG_BASE}/dependency/
make
make install

cd ../../

export PATH=\$PATH:${COV_PKG_BASE}/dependency/bin

if [ -f ~/.bashrc ]; then
  echo "export PATH=\$PATH:${COV_PKG_BASE}/dependency/bin" >> ~/.bashrc
fi
if [ -f ~/.bash_profile ]; then
  echo "export PATH=\$PATH:${COV_PKG_BASE}/dependency/bin" >> ~/.bash_profile
fi
```

