# Part of the implementation of this container is based on the Amazon SageMaker Apache MXNet container.
# https://github.com/aws/sagemaker-mxnet-container

FROM debian

LABEL maintainer="Ashley Miller"

WORKDIR /

# Installing numpy, pandas, scikit-learn, scipy
RUN apt-get update
RUN apt-get install python3 -y
RUN apt-get install pip -y
RUN pip3 install --no-cache scikit-learn 
RUN pip3 install --no-cache pandas 

# Setting some environment variables.
# ENV PYTHONDONTWRITEBYTECODE=1 \
#     PYTHONUNBUFFERED=1 \
#     LD_LIBRARY_PATH="${LD_LIBRARY_PATH}:/usr/local/lib" \
#     PYTHONIOENCODING=UTF-8 \
#     LANG=C.UTF-8 \
#     LC_ALL=C.UTF-8

RUN pip3 install --no-cache --upgrade sagemaker-training

# Copies code under /opt/ml/code where sagemaker-containers expects to find the script to run
COPY code/* /opt/ml/code/

# Defines train.py as script entry point
ENV SAGEMAKER_PROGRAM train.py