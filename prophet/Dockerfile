FROM ubuntu

LABEL version="0.1"
LABEL description="This image provides an environment to run prophet on pystan"

ENV PATH="/root/miniconda3/bin:${PATH}"
ARG PATH="/root/miniconda3/bin:${PATH}"
EXPOSE 9999

ENTRYPOINT []

RUN apt-get update && apt-get install -y

RUN apt-get install -y gcc && \
	apt-get install -y --reinstall build-essential

RUN apt-get install -y wget && rm -rf /var/lib/apt/lists/*

RUN wget \
    https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh \
    && mkdir /root/.conda \
    && bash Miniconda3-latest-Linux-x86_64.sh -b \
    && rm -f Miniconda3-latest-Linux-x86_64.sh 


RUN conda install -c conda-forge jupyterlab && \
    pip install pandas numpy convertdate Cython lunarcalendar ujson pillow korean-lunar-calendar kiwisolver hijri-converter cycler setuptools-git matplotlib holidays cmdstanpy && \
    pip install pystan==2.19.1.1 && \
    pip install prophet && \
    pip install plotly

WORKDIR /src/notebooks
CMD jupyter lab --ip 0.0.0.0 --port 9999 --allow-root --no-browser --NotebookApp.token='' --NotebookApp.password=''
