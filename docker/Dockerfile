FROM mattocci/myenv:4.0.3

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
