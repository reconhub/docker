FROM rocker/verse

# RUN apt-get update

RUN adduser --disabled-password --gecos "" guest

RUN echo 'options(repos = c(CRAN = "http://cran.ma.imperial.ac.uk"))' > ~/.Rprofile

RUN r -e "install.packages('outbreaks', dependencies = c('Depends', 'Imports', 'Suggests'))"

RUN r -e "install.packages('incidence', dependencies = c('Depends', 'Imports', 'Suggests'))"

RUN r -e "devtools::install_github('reconhub/epicontacts', dependencies = c('Depends', 'Imports', 'Suggests'))"

RUN r -e "devtools::install_github('reconhub/outbreaker2', dependencies = c('Depends', 'Imports', 'Suggests'))"

RUN r -e "devtools::install_github('reconhub/shinyHelpers', dependencies = c('Depends', 'Imports', 'Suggests'))"

RUN r -e "devtools::install_github('reconhub/recon.ui', dependencies = c('Depends', 'Imports', 'Suggests'))"

RUN r -e "devtools::install_github('reconhub/incidence.ui', dependencies = c('Depends', 'Imports', 'Suggests'))"

RUN r -e "devtools::install_github('reconhub/epicontacts.ui', dependencies = c('Depends', 'Imports', 'Suggests'))"





