FROM python:3.9

WORKDIR /app

COPY requirements.txt .

RUN apt update && \
    apt upgrade -y && \
    apt -y install gcc && \
    python3 -m pip install --upgrade pip && \
    pip3 install -r requirements.txt --no-cache-dir

# (для Linux) Если ошибка: OSError: no library called "cairo-2" was found
# RUN apt-get update -y
# RUN apt-get install python3-cffi python3-brotli libpango-1.0-0 libharfbuzz0b libpangoft2-1.0-0 libgtk-3-dev gcc -y

COPY . ./

CMD ["gunicorn", "foodgram.wsgi:application", "--bind", "0:8000"]