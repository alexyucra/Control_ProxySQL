FROM python:3.9

# set environment variables
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1
ENV FLASK_APP main.py
ENV DEBUG True

RUN apt-get update -y 
#     && apt-get install -y default-mysql-client default-libmysqlclient-dev libmariadbclient-dev

# ARG PROXY_USER=proxyctl
# ARG PROXY_GROUP=proxyctl
# ARG PROXY_UID=1000
# ARG PROXY_GID=1000

# RUN groupadd -g ${PROXY_GID} ${PROXY_GROUP} && \
#     useradd -u ${PROXY_UID} ${PROXY_USER} -g ${PROXY_GROUP} && \
#     mkdir -p /home/${PROXY_USER}/app && \
#     chown -R ${PROXY_USER}:${PROXY_GROUP} /home/${PROXY_USER}

# USER ${PROXY_USER}

# WORKDIR /home/${PROXY_USER}/app

WORKDIR /app

COPY . /app

RUN python -m venv /venv

RUN python -m pip install -r requirements.txt

RUN cp config.yaml.default config.yaml

# EXPOSE 7080

# CMD [ "python", "main.py" ]

# gunicorn
CMD ["gunicorn", "--config", "gunicorn-cfg.py", "main:app"]