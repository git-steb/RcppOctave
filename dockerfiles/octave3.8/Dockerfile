## Emacs, make this -*- mode: sh; -*-
 
FROM docsteb/trusty-r-texlive

RUN export OVERSION="3.8.1 (trusty)" \
		&& apt-get install -y liboctave-dev

ADD . /root/repo

RUN cd /root/repo; Rscript -e 'deps <- devtools::dev_package_deps(dependencies = NA);devtools::install_deps(dependencies = TRUE);if (!all(deps$package %in% installed.packages())) { message("missing: ", paste(setdiff(deps$package, installed.packages()), collapse=", ")); q(status = 1, save = "no")}'

EXPOSE 4567
