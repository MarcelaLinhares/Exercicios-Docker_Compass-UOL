FROM python:3.9.20-slim

RUN useradd -m marcela

WORKDIR /app

COPY requirements.txt .

RUN pip install --no-cache-dir -r requirements.txt

USER marcela

COPY . .

CMD ["python", "-m", "flask", "run", "--host=0.0.0.0"]