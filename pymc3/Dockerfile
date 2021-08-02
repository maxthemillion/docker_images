FROM ubuntu

LABEL version="0.1"
LABEL description="This image provides an environment to run pymc3"

ENV PATH="/root/miniconda3/bin:${PATH}"
ARG PATH="/root/miniconda3/bin:${PATH}"
EXPOSE 9999

ENTRYPOINT []

RUN apt-get update && apt-get install -y

RUN apt-get install -y wget && rm -rf /var/lib/apt/lists/*

RUN wget \
    https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh \
    && mkdir /root/.conda \
    && bash Miniconda3-latest-Linux-x86_64.sh -b \
    && rm -f Miniconda3-latest-Linux-x86_64.sh 


RUN conda install -c conda-forge pymc3 jupyterlab

WORKDIR /src/notebooks
CMD jupyter lab --ip 0.0.0.0 --port 9999 --allow-root --no-browser --NotebookApp.token='' --NotebookApp.password=''
