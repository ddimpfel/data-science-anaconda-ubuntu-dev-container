FROM ubuntu:24.04

# Install Anaconda
ENV DEBIAN_FRONTEND=noninteractive
ENV CONDA_DIR=/opt/conda
ENV PATH=${CONDA_DIR}/bin:$PATH

RUN apt-get update --fix-missing && \
    apt-get install -y wget bzip2 ca-certificates libglib2.0-0 libsm6 libxext6 libxrender1 && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

RUN wget https://repo.anaconda.com/archive/Anaconda3-2025.06-0-Linux-x86_64.sh -O anaconda.sh && \
    /bin/bash anaconda.sh -b -p ${CONDA_DIR} && \
    rm anaconda.sh && \
    ${CONDA_DIR}/bin/conda init bash

# Setup Conda environment
COPY ./environment.yml /tmp/environment.yml
ENV CONDA_PLUGINS_AUTO_ACCEPT_TOS=true
RUN /bin/bash -c "\
    source ${CONDA_DIR}/etc/profile.d/conda.sh && \
    conda init bash && \
    conda update -n base -c defaults conda -y && \
    conda config --set solver libmamba && \
    conda env create -f /tmp/environment.yml && \
    conda activate en685648 && \
    python -m ipykernel install --user --name en685648 --display-name 'Python (en685648)' \
    "

# Commands to run on container start for conda env activation
RUN echo "source ${CONDA_DIR}/etc/profile.d/conda.sh" >> ~/.bashrc && \
    echo "conda activate en685648" >> ~/.bashrc

# Conda environment variables to activate by default 
ENV CONDA_DEFAULT_ENV=en685648
ENV CONDA_PREFIX=${CONDA_DIR}/envs/${CONDA_DEFAULT_ENV}
ENV PATH=${CONDA_DIR}/envs/${CONDA_DEFAULT_ENV}/bin:${PATH}

# Keep the container running after startup
CMD ["sleep", "infinity"]