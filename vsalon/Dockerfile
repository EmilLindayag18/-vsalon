FROM python:3.12-alpine

# Install MySQL development headers and build tools required to compile mysqlclient
RUN apk add --no-cache \
    mysql-dev \
    gcc \
    python3-dev \
    musl-dev \
    pkgconfig

WORKDIR /app

COPY . .

# Create a virtual environment and install Python dependencies
RUN python -m venv /app/venv && \
    /app/venv/bin/pip install --upgrade pip && \
    /app/venv/bin/pip install -r requirements.txt

ENV PATH="/app/venv/bin:$PATH"

EXPOSE 8000

CMD ["gunicorn", "app:app"]
