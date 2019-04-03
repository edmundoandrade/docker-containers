FROM nvcr.io/nvidia/cuda:10.1-cudnn7-devel-ubuntu18.04

ENV DEBIAN_FRONTEND noninteractive
RUN apt-get update && apt-get install apt-utils -yq
RUN apt-get install wget -yq

ENV CONDA_DIR=/opt/conda

RUN wget -q -O conda.sh https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
RUN chmod +x conda.sh
RUN ./conda.sh -b -p $CONDA_DIR
RUN rm conda.sh

ENV PATH=$CONDA_DIR/bin:$PATH

RUN conda update -y conda
RUN conda install -y python=3.7.3
RUN conda install -y jupyter
RUN conda install -y cuda100 -c pytorch
RUN conda install -y -c pytorch -c fastai fastai pytorch

WORKDIR /home/jovyan

EXPOSE 8888

ENTRYPOINT ["jupyter", "notebook", "--port=8888"]
CMD ["--ip=0.0.0.0", "--allow-root", "--no-browser", "/home/jovyan"]
