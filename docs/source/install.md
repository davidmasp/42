# Software installations

Note: This instructions will modify configuration files in your machine,
if note under a dotfile repo I strongly suggest to back them up. The
instructions are given AS IS and can contain errors. They are normally partially tested.

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

## R (base) - ubuntu

R is a [statistical software](https://www.r-project.org/)

### From repositories (old versions)

The version freely available from the normal repos which normally is far away
from the current update.

```bash
sudo apt-get update
sudo apt-get install r-base r-base-dev
```

### From repositories (newest versions)

In order to add the newest R version but still install the software
through a package manager you need to use the R repository.

**First step** is to
add the cran repo of your choice.

```bash
sudo echo "deb https://cloud.r-project.org/bin/linux/ubuntu xenial-cran40/" | sudo tee -a /etc/apt/sources.list
```

The **second step** is to add the R key to Ubuntu Keyring. Note that is important to
fill in all the gpg code as apparently
there was a second one in the servers
which wasn't correct. See
[this](https://rubuntu.netlify.app/post/changes-to-cran-ubuntu-webpage-regarding-apt-secure-key/).
Apparently there wasn't any malicious intend but it was technically possible.

```bash
gpg --keyserver keyserver.ubuntu.com --recv-key E298A3A825C0D65DFD57CBB651716619E084DAB9
gpg -a --export E298A3A825C0D65DFD57CBB651716619E084DAB9 | sudo apt-key add -
```

Finally, we can now install R-base.

```bash
sudo apt-get update
sudo apt-get install r-base r-base-dev
```

At date of writing this installs the v `3.4.1`

## R (packages) - ubuntu

### tidyverse

In order to install tidyverse packages in ubuntu a set of system dependencies
are needed, to continue, install the required packages.

```bash
sudo apt-get install libxml2-dev
sudo apt-get install libcurl4-openssl-dev
sudo apt-get install libssl-dev
```

Open R and install tidyverse:

```R
install.packages("tidyverse")
```

## Installing VEP

VEP is an annotation program from ENSEMBL which a lot of people use.
Because it is written in perl it is awful to install if you don't normally
use it. I had a troublesome expirience trying to install the software but
I think I managed.

### Installing VEP dependencies

(I guess you should first have Perl if not available)

First we need to install the perl dependencies. Some are listed as VEP

```bash
curl -L https://cpanmin.us | perl - App::cpanminus
~/perl5/bin/cpanm --local-lib=~/perl5 local::lib && eval $(perl -I ~/perl5/lib/perl5/ -Mlocal::lib)

~/perl5/bin/cpanm Archive::Zip
~/perl5/bin/cpanm DBD::mysql
~/perl5/bin/cpanm DBI
~/perl5/bin/cpanm Module::Build
~/perl5/bin/cpanm autodie
```

### Installing VEP tool

First we are gonna simply clone the github directory. Note that I use the
`src` folder strucuture as here [].

Then we are setting the PERL libraries that we just installed available
to the VEP installer

Finally we run the installer. Hopefully, things will work out.

```bash
cd ~/src
git clone https://github.com/Ensembl/ensembl-vep.git
cd ensembl-vep
# this makes the libraries that we installed before available
export PERL5LIB=$(realpath /home/dmas/perl5/lib/perl5/):$(realpath ~/src/ensembl-vep/)

perl INSTALL.pl

```

It will ask you to download a cache in `~/.vep`. I did as I hope it will make
things go faster when annotating.

### Setting up paths

For later use, you should put the programs in the current paths.

```bash
echo "export PERL5LIB=$(realpath /home/dmas/perl5/lib/perl5/):$(realpath ~/src/ensembl-vep/)" >>  ~/.bashrc_fsupekserver
ln -s $(realpath /home/dmas/src/ensembl-vep/vep) ~/bin
```
