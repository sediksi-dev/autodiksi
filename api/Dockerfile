FROM python:3.11-slim

WORKDIR /api

RUN apt-get update && apt-get install -y \
    build-essential \
    curl \
    software-properties-common \
    git \
    && rm -rf /var/lib/apt/lists/*

RUN git clone https://github.com/sediksi-dev/auto-diksi.git .

RUN pip install --no-cache-dir -r requirements.txt
RUN pip install --upgrade pip

COPY . .

ENTRYPOINT ["sh", "-c", "uvicorn app.main:app --proxy-headers --host 0.0.0.0 --port $PORT"]
