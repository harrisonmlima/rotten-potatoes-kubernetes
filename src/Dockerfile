FROM python:3.8
WORKDIR /app
COPY requirements.txt requirements.txt

RUN python3 -m pip install --upgrade pip && pip install -r requirements.txt

COPY . .
EXPOSE 5000
CMD ["python3", "-m", "flask", "run", "--host=0.0.0.0"]