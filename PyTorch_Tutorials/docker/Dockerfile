FROM pytorch/pytorch:1.9.0-cuda11.1-cudnn8-devel
# Has Pytorch, Spacy, Transformers, Sentence-transformersFROM pytorch/pytorch:1.9.0-cuda11.1-cudnn8-devel

# proxy related env settings
ENV http_proxy ${HTTP_PROXY}
ENV https_proxy ${HTTP_PROXY}
ENV no_proxy ${NO_PROXY}
ENV DEBIAN_FRONTEND=noninteractive

# the following 2 environment variables are needed to download spacy models
ENV LC_ALL=C.UTF-8
ENV LANG=C.UTF-8

RUN apt-get update && apt-get install -y --allow-downgrades --allow-change-held-packages --no-install-recommends \
    build-essential \
    cmake \
    g++ \
    git \
    curl \
    vim \
    wget

# to enable scp inside and outside of docker container
RUN apt-get update && apt-get install -y openssh-server

RUN pip install -U pip setuptools wheel # this is a very important line

# install sentence transformers, huggingface and spacy with GPU
RUN pip install -U transformers tokenizers sentencepiece

RUN pip install -U spacy[cuda111]


RUN python -m spacy download en_core_web_sm
RUN python -m spacy download en_core_web_trf

# first spacy, then fastai
RUN pip install -U torchtext fastai

RUN pip install -U fasttext gensim python-Levenshtein

# python ecosystem for traditional machine learning/ data science
RUN pip install -U scikit-learn pandas numpy scipy matplotlib seaborn

# new-age viz libraries
RUN pip install -U altair vega-datasets plotly plotly-express

# additional tabular processing libraries
RUN pip install -U pandas-profiling pyarrow xlrd

RUN pip install jupyter
RUN jupyter nbextension enable --py widgetsnbextension && \
    rm -rf /var/lib/apt/lists/*

RUN pip install -U sentence-transformers
