FROM node:current-slim

# Cria usuário não-root
RUN useradd -m appuser

# Define diretório de trabalho
WORKDIR /app

# Copia o app.js
COPY app.js .

# Define o usuário não-root
USER appuser

# Expõe a porta usada pela aplicação
EXPOSE 3000

# Comando para iniciar o app
CMD ["node", "app.js"]
