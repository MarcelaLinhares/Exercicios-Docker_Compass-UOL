# Exercício 13

## 🎯 Objetivo

Crie um Dockerfile que use a imagem python:3.11-slim, copie um script Python local (app.py) e o execute com CMD. O script pode imprimir a data e hora atual. 

a. Crie uma conta no Docker Hub. 

b. Faça login pelo terminal com docker login. 

c. Rebuild sua imagem meu-echo e a renomeie no formato seu usuario/meu-echo:v1. 

d. Faça o push da imagem para o Docker Hub. 

## ⚙️ Execução do Exercício

### 1. Crie script Python

```python
from datetime import datetime
import pytz

fuso_horario = pytz.timezone('America/Sao_Paulo')
data_e_horario_atuais = datetime.now(fuso_horario)

print("\nData e Horário atual:")
print(data_e_horario_atuais.strftime("%d/%m/%Y %H:%M:%S"))
```

Com esse script em Python, primeiro é importado da biblioteca datetime o objeto datetime e também a pytz (para fuso horário), após é definida a varíavel do horário e data e é feito um print dessa varíavel formatada.

### 2. Crie o Dockerfile

```Dockerfile
FROM python:3.11-slim

RUN useradd -m marcela

WORKDIR /app

COPY requirements.txt .

RUN pip install --no-cache-dir -r requirements.txt

USER marcelalinhares

COPY . .

CMD ["python", "app.py"]
```

Nesse _Dockerfile_, é definida a imagem solicitada, é criado um usuário, diretório de trabalho definido, loga no usuário criado, copia os arquivos para o container, instala o requirement (biblioteca para fuso horário) e roda o app.py .

### 3. Buildar imagem usando o Dockerfile

Em um terminal, na pasta do desafio, execute:

```Docker
docker build -t meu-echo .
```

### 4. Logar no Dockerhub via terminal

Com a conta Dockerhub já cadastrada, para fazer o login via terminal basta digitar:

```
docker login
```

Após, Digite seu usuário e depois sua senha.

### 5. Push da imagem para o Dockerhub

Primeiro vamos rebuildar a imagem agora com a tag :v1

```Docker
docker build -t marcelalinhares/meu-echo:v1 .
```

E agora, o _push_

```Docker
docker push marcelalinhares/meu-echo:v1
```

![Print do dockerhub](img/01-dockerhub.png)