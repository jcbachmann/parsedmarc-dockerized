FROM python:3.11-bookworm

ENV DEBIAN_FRONTEND=noninteractive

# Added gir1.2-secret-1 and libsecret-1-dev
RUN apt-get update && apt-get install -y --no-install-recommends \
    libcairo2-dev \
    libgirepository1.0-dev \
    pkg-config \
    python3-dev \
    gir1.2-glib-2.0 \
    gir1.2-secret-1 \
    libsecret-1-dev \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Install dependencies
RUN pip install --no-cache-dir PyGObject==3.44.1
RUN pip install --no-cache-dir parsedmarc==9.0.9

COPY ./entrypoint.py /entrypoint.py
RUN chmod +x /entrypoint.py

ENTRYPOINT ["python", "/entrypoint.py"]
