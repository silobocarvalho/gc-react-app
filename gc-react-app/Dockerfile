# Etapa 1: Construir o app React com Vite
FROM node:18 AS build

WORKDIR /app

# Copiar os arquivos de configuração
COPY package.json package-lock.json ./

# Instalar dependências
RUN npm install

# Copiar o restante do projeto
COPY . .

# Executar o build com Vite
RUN npm run build

# Verificar a estrutura do diretório após o build (opcional)
RUN ls -l /app

# Etapa 2: Servir os arquivos estáticos com Nginx
FROM nginx:stable-alpine

# Copiar os arquivos de build para o diretório padrão do Nginx
COPY --from=build /app/dist /usr/share/nginx/html

# Expor a porta
EXPOSE 80

# Iniciar o Nginx
CMD ["nginx", "-g", "daemon off;"]