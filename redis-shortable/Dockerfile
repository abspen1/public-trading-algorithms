FROM continuumio/miniconda3

RUN apt-get update -y
RUN apt-get install build-essential -y

RUN conda create -n py36 python=3.6
RUN conda run -n py36 pip install schedule alpaca_trade_api redis

# This will make the time in our container US/Central time
ENV TZ=US/Central 
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

COPY main.py /tmp/main.py

CMD ["/bin/bash", "-c", "source activate py36 && python -u /tmp/main.py" ]