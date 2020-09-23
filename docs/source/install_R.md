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
