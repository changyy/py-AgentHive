FROM python:3.12-slim

WORKDIR /app

# 安裝系統依賴
RUN apt-get update && apt-get install -y \
    build-essential \
    curl \
    && rm -rf /var/lib/apt/lists/* \
    && curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh -s -- -y \
    && echo 'source $HOME/.cargo/env' >> $HOME/.bashrc

COPY requirements/base_requirements.txt ./base_requirements.txt
COPY requirements/test_requirements.txt ./requirements.txt
RUN pip install --no-cache-dir -r requirements.txt

# 複製專案檔案
COPY . .

# 安裝專案
# RUN pip install -e .
CMD ["pytest", "-xvs", "tests/"]
