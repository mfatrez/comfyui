FROM nvidia/cuda:12.4.0-runtime-ubuntu20.04
ENV TZ=Europe/Paris
ENV DEBIAN_FRONTEND=noninteractive

WORKDIR /home/workspace

RUN apt-get update && apt-get install -y \
    git \
    python3.10 \
    python3-pip

RUN pip install torch torchvision torchaudio --extra-index-url https://download.pytorch.org/whl/cu124

RUN git clone https://github.com/comfyanonymous/ComfyUI.git \
    && cd ComfyUI \
    && git checkout v0.2.4 \
    && find . -name ".git*" | xargs rm -rf

RUN pip install -r ComfyUI/requirements.txt
RUN pip install urllib3==1.26.20 numpy==2.1.2 PyYAML==6.0.2 toml==0.10.2

EXPOSE 8848

# RUN
CMD ["python3", "-u", "/home/workspace/ComfyUI/main.py", "--listen", "0.0.0.0", "--port", "8848"]
