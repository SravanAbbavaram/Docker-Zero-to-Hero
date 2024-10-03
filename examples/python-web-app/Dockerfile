# FROM ubuntu

# WORKDIR /app

# COPY requirements.txt /app
# COPY devops /app

# RUN apt-get update && \
#     apt-get install -y python3 python3-pip && \
#     pip install -r requirements.txt && \
#     cd devops

# ENTRYPOINT ["python3"]
# CMD ["manage.py", "runserver", "0.0.0.0:8000"]

FROM ubuntu

WORKDIR /app

# Install apt-utils to prevent the debconf warning
RUN apt-get update && \
    apt-get install -y apt-utils

COPY requirements.txt /app
COPY devops /app/devops

# Install python3, pip3, and python3-venv
RUN apt-get update && \
    apt-get install -y python3 python3-pip python3-venv && \
    python3 -m venv /app/venv && \
    /app/venv/bin/pip install -r requirements.txt

WORKDIR /app/devops

CMD ["/app/venv/bin/python", "manage.py", "runserver", "0.0.0.0:8000"]







