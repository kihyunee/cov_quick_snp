# This code
```
git clone <this repository .git>

```


# Minimap2

```
git clone https://github.com/lh3/minimap2

cd minimap2 && make

cd ..
```


# SAMtools & BCFtools
```
# unzip & unpack tar 

cd samtools-1.x    # and similarly for bcftools and htslib

./configure --prefix=/where/to/install

make

make install
```


# Mafft (optional for slow_snp workflow)

```
tar -xzf mafft-7.490-without-extensions-src.tgz

cd mafft-7.490-without-extensions-src/core/

make clean

make

cd ../..

```

