
RECON docker images
===================


Starting a RECON docker image
-----------------------------

First of all, you need docker installed on your computer. Follow [this
link](https://www.docker.com/community-edition#/download) for guidelines to
install Docker Community Edition.


For a list of available images, go to:
https://hub.docker.com/u/reconhub/dashboard/


To start the docker image, type:
```
docker run --rm -it --user guest [image] /bin/bash
```

where `[image]` is the docker image you want to use. See next section for
available images.



Available docker images
-----------------------

### `reconhub/recon`

#### Start the image

These commands should be started from a terminal.

To start a `bash` session as 'guest', type:
```
docker run --rm -it --user guest reconhub/recon /bin/bash
```

To start a Rstudio server running in the background, accessible from a web-browser, type:
```
docker run -d -p 8787:8787 reconhub/recon
```

And then open a web browser and go to the URL `127.0.0.1:8787` (or `localhost:8787`).



#### Description

This image contains all functional RECON packages. CRAN versions are installed
when available, otherwise github versions are used. It also contains package
sources for testing.



#### Summary

- based on [rocker/verse](https://hub.docker.com/r/rocker/tidyverse/)

- CRAN packages: *outbreaks*, *incidence*

- github packages: *epicontacts*, *distcrete*, *outbreaker2*, *shinyHelpers*,
*recon.ui*, *incidence.ui*, *epicontacts.ui*

- user: 'guest'

- shell: `bash`, starting in `/home/guest`

- package sources: git-clone in `/home/guest/dev/`





Contributions
-------------

Contributors (by alphabetic order):
- [Thibaut Jombart](https://github.com/thibautjombart)

See details of contributions on:
<br>
https://github.com/reconhub/docker/graphs/contributors


Contributions are welcome via **pull requests**.

Please note that this project is released with a [Contributor Code of
Conduct](CONDUCT.md). By participating in this project you agree to abide by its
terms.

**Maintainer:** Thibaut Jombart (thibautjombart@gmail.com)
