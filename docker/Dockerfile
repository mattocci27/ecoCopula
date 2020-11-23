FROM mattocci/myenv:4.0.3

ARG USER_NAME

RUN useradd --user-group --create-home --shell /bin/false ${USER_NAME} &&\
  echo "${USER_NAME} ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers.d/${USER_NAME}

ENV HOME=/home/${USER_NAME}

RUN Rscript -e "BiocManager::install('graph')"

RUN Rscript -e "BiocManager::install('BiocGenerics')"

Run install2.r --error -s \
      --deps TRUE \
      dbplyr \
      mvabund \
      glasso \
      plyr \
      sna \
      MASS \
      tweedie \
      igraph \
      betareg \
      doParallel \
      mgcv \
      glm2 \
      ordinal \
      foreach

Run install2.r --error -s \
      --deps TRUE \
    knitr \
    rmarkdown \ 
    testthat \
    tidyr \ 
    ggplot2 \ 
    RColorBrewer \ 
    ggraph \ 
    labdsv \ 
    tidygraph

RUN chown -R ${USER_NAME}:staff /opt/texlive \
  && chown -R ${USER_NAME}:staff /usr/local/texlive \
  && chmod -R 777 /opt/texlive \
  && chmod -R 777 /usr/local/texlive

#USER ${USER_NAME}

RUN mkdir -p ${HOME} \
  &&  chown -R ${USER_NAME}:${USER_NAME} ${HOME}

RUN mkdir -p ${HOME}/.R \
  && echo 'CXXFLAGS=-O3 -mtune=native -fPIC' >> ${HOME}/.R/Makevars
