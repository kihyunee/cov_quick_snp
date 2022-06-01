
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


Also install R for visualization script to work.

```
sudo apt install r-base-core
```

Inside R, install the two necessary packages.

Go to R interface by
```
sudo R
```

and install them.

```
install.packages(c("RColorBrewer", "ggplot2"))
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
  echo "export COV_PKG_BASE=${COV_PKG_BASE}" >> ~/.bashrc
fi
if [ -f ~/.bash_profile ]; then
  echo "export PATH=\$PATH:${COV_PKG_BASE}/dependency/bin" >> ~/.bash_profile
  echo "export COV_PKG_BASE=${COV_PKG_BASE}" >> ~/.bash_profile
fi
```


If you get ^M related error when you execute `quick_corona_mutation` 
there is a solution like this:

```
cd scripts/

sed -i 's/\r$//' quick_corona_mutation

cp quick_corona_mutation ../dependency/bin/
```

