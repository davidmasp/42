## htslib

Htslib is a set of tools developed by
[Heng Li (lh3)](https://en.wikipedia.org/wiki/Heng_Li)
which are widely used in bioinformatics
for dealing with large files and data. He is also the developer of another
wide used tool like [bwa](https://github.com/lh3/bwa).

The instructions can be also found [here](http://www.htslib.org/download/).

Note: at the time of writing the latest version is 1.11.

Note2: These commands are following the
[software installation convention]().

```bash
mkdir -p tmp_dir
wget https://github.com/samtools/htslib/releases/download/1.11/htslib-1.11.tar.bz2
cd tmp_dir

tar xvf htslib-1.11.tar.bz2
cd htslib-1.11
./configure --prefix=$(realpath $HOME/src/htslib)
make
make install

cd ..
# rm -r tmp_dir
```

Finally we will need to add the bin folder generated in the install directory
in our path. Go to the machine specific server profile
(for example `.bashrc_hostname`) or to
your `.bashrc` file and add:

```bash
echo "export PATH=\"\$PATH:$(realpath $HOME)/src/htslib/bin\"" >> ~/.bashrc
```

This will install in your path 3
