# Estágio de build
FROM golang:1.19 AS build-stage
WORKDIR /app

# Copia os arquivos do projeto
COPY . .

# Compila o binário
RUN CGO_ENABLED=0 GOOS=linux go build -o /docker-gs-ping

# Estágio final com imagem enxuta
FROM gcr.io/distroless/base-debian11 AS final-stage
WORKDIR /

# Copia apenas o binário gerado anteriormente
COPY --from=build-stage /docker-gs-ping /docker-gs-ping

EXPOSE 8080
ENTRYPOINT ["/docker-gs-ping"]
