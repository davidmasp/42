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
