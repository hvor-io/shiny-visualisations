# shiny-visualisations
My own setup of Shiny server for R

# Documentation
https://docs.posit.co/shiny-server/#stopping-and-starting
https://cloud.r-project.org/
https://www.digitalocean.com/community/tutorials/how-to-set-up-shiny-server-on-ubuntu-20-04

# How

VERY IMPORTANT. LTS versions please

Installing R:
```
## update indices
sudo apt update -qq
## install two helper packages we need
sudo apt install --no-install-recommends software-properties-common dirmngr
## add the signing key (by Michael Rutter) for these repos
## To verify key, run gpg --show-keys /etc/apt/trusted.gpg.d/cran_ubuntu_key.asc 
## Fingerprint: E298A3A825C0D65DFD57CBB651716619E084DAB9
wget -qO- https://cloud.r-project.org/bin/linux/ubuntu/marutter_pubkey.asc | sudo tee -a /etc/apt/trusted.gpg.d/cran_ubuntu_key.asc
## add the R 4.0 repo from CRAN -- adjust 'focal' to 'groovy' or 'bionic' as needed
sudo add-apt-repository "deb https://cloud.r-project.org/bin/linux/ubuntu $(lsb_release -cs)-cran40/"

sudo apt install --no-install-recommends r-base
```

Install R-tools for `make`
```
sudo apt-get install r-base-dev
```

Install shiny server 
```
sudo apt-get install gdebi-core
wget https://download3.rstudio.org/ubuntu-18.04/x86_64/shiny-server-1.5.20.1002-amd64.deb
sudo gdebi shiny-server-1.5.20.1002-amd64.deb
```

Go into R and install rmarkdown and jsonlite:
```
> R
> install.packages("rmarkdown")
> install.packages("jsonlite")
```

and then 

```
sudo systemctl restart shiny-server
```

Is it running?
```
sudo ss -plut | grep -i shiny
```
