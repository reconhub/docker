FROM rocker/verse

RUN apt-get update






## add guest user

RUN adduser --disabled-password --gecos "" guest
RUN usermod -a -G users guest
RUN usermod -a -G staff guest
RUN chmod a+rw /usr/local/lib/R/site-library -R






## install CRAN packages

RUN echo 'options(download.file.method = "libcurl", repos = c(CRAN = "https://cran.ma.imperial.ac.uk"))' > ~/.Rprofile

RUN r -e "install.packages('outbreaks', dependencies = c('Depends', 'Imports', 'Suggests'))"

RUN r -e "install.packages('incidence', dependencies = c('Depends', 'Imports', 'Suggests'))"






## install devel packages (github)

RUN r -e "devtools::install_github('reconhub/epicontacts', dependencies = c('Depends', 'Imports', 'Suggests'))"

RUN r -e "devtools::install_github('reconhub/outbreaker2', dependencies = c('Depends', 'Imports', 'Suggests'))"

RUN r -e "devtools::install_github('reconhub/distcrete', dependencies = c('Depends', 'Imports', 'Suggests'))"

RUN r -e "devtools::install_github('reconhub/vimes', dependencies = c('Depends', 'Imports', 'Suggests'))"


RUN r -e "devtools::install_github('reconhub/shinyHelpers', dependencies = c('Depends', 'Imports', 'Suggests'))"

RUN r -e "devtools::install_github('reconhub/recon.ui', dependencies = c('Depends', 'Imports', 'Suggests'))"

RUN r -e "devtools::install_github('reconhub/incidence.ui', dependencies = c('Depends', 'Imports', 'Suggests'))"

RUN r -e "devtools::install_github('reconhub/epicontacts.ui', dependencies = c('Depends', 'Imports', 'Suggests'))"






## clone repos to get sources

RUN su guest
RUN mkdir ~/dev
WORKDIR /home/guest/dev

RUN git clone https://github.com/reconhub/outbreaks
RUN git clone https://github.com/reconhub/incidence
RUN git clone https://github.com/reconhub/epicontacts
RUN git clone https://github.com/reconhub/outbreaker2
RUN git clone https://github.com/reconhub/distcrete
RUN git clone https://github.com/reconhub/vimes

RUN git clone https://github.com/reconhub/shinyHelpers
RUN git clone https://github.com/reconhub/recon.ui
RUN git clone https://github.com/reconhub/incidence.ui
RUN git clone https://github.com/reconhub/epicontacts.ui


WORKDIR /home/guest/



