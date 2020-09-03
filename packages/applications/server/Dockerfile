ARG VERSION=1.0.0
FROM python:3.7-alpine
EXPOSE 8000

RUN mkdir -p app/

RUN apk add --update --no-cache --virtual .build-deps \
        g++ \
        python-dev \
        libxml2 \
        libxml2-dev && \
    apk add libxslt-dev
RUN pip install --no-cache-dir -r req.txt
RUN apk del .build-deps

WORKDIR /app
COPY . .

CMD ["gunicorn", "-c", "gunicorn_config.py", "src.app:application"]
ARG $VERSION
