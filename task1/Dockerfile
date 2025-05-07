FROM ubuntu:latest

RUN apt-get update && apt-get upgrade -y && \
    apt-get install -y python3 python3-pip python3.12-venv
    
WORKDIR /app

COPY ./api.py /app/api.py
    
RUN python3 -m venv .venv
RUN . .venv/bin/activate && pip install flask

ENV VIRTUAL_ENV=/app/.venv
ENV PATH="$VIRTUAL_ENV/bin:$PATH"

EXPOSE 5252

CMD ["python3", "api.py"]
