FROM rocker/drd

MAINTAINER Thibaut Jombart <thibautjombart@gmail.com>

RUN apt-get update && apt-get upgrade -y
RUN apt-get install --fix-missing -y
RUN apt-get install libssl-dev libxml2-dev pandoc pandoc-citeproc libblas-dev liblapack-dev git qpdf texlive aptitude -y
# RUN aptitude install libcairo2-dev -y

## add guest user

RUN adduser --disabled-password --gecos "" guest
RUN usermod -a -G users guest && usermod -a -G staff guest
RUN chmod a+rw /usr/local/lib/R/site-library -R



## install CRAN packages

RUN echo 'options(download.file.method = "libcurl", repos = c(CRAN = "https://cran.ma.imperial.ac.uk"))' > ~/.Rprofile

RUN r -e "install.packages('devtools')" \
 && r -e "install.packages('roxygen2')" \
 && r -e "install.packages('testthat')" \
 && r -e "install.packages('rmarkdown')" 
# && r -e "install.packages('vdiffr')"


## install devel packages (github)

RUN r -e "devtools::install_github('reconhub/outbreaks', dependencies = c('Depends', 'Imports', 'Suggests'))" \
 && r -e "devtools::install_github('reconhub/incidence', dependencies = c('Depends', 'Imports', 'Suggests'))" \
 && r -e "devtools::install_github('reconhub/epicontacts', dependencies = c('Depends', 'Imports', 'Suggests'))" \
 && r -e "devtools::install_github('reconhub/outbreaker2', dependencies = c('Depends', 'Imports', 'Suggests'))" \
 && r -e "devtools::install_github('reconhub/distcrete', dependencies = c('Depends', 'Imports', 'Suggests'))" \
 && r -e "devtools::install_github('reconhub/vimes', dependencies = c('Depends', 'Imports', 'Suggests'))" \
 && r -e "devtools::install_github('reconhub/shinyHelpers', dependencies = c('Depends', 'Imports', 'Suggests'))" \
 && r -e "devtools::install_github('reconhub/recon.ui', dependencies = c('Depends', 'Imports', 'Suggests'))" \
 && r -e "devtools::install_github('reconhub/incidence.ui', dependencies = c('Depends', 'Imports', 'Suggests'))" \
 && r -e "devtools::install_github('reconhub/epicontacts.ui', dependencies = c('Depends', 'Imports', 'Suggests'))"



## clone repos to get sources

RUN su guest
RUN mkdir ~/dev
WORKDIR /home/guest/dev

RUN git clone https://github.com/reconhub/outbreaks \
 && git clone https://github.com/reconhub/incidence \
 && git clone https://github.com/reconhub/epicontacts \
 && git clone https://github.com/reconhub/outbreaker2 \
 && git clone https://github.com/reconhub/distcrete \
 && git clone https://github.com/reconhub/vimes \
 && git clone https://github.com/reconhub/shinyHelpers \
 && git clone https://github.com/reconhub/recon.ui \
 && git clone https://github.com/reconhub/incidence.ui \
 && git clone https://github.com/reconhub/epicontacts.ui


WORKDIR /home/guest/
RUN ls='ls --color=auto'
