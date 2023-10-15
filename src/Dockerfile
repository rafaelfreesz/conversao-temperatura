# Foi consultado no dockerhub qual nome da imagem.
# A ideia desse dockerfile é instalar as dependencias do
# É uma boa pratica colocar a versão a ser utiliziada para não haver problemas de compatibilidade 
FROM node:16.13.2
# Diretorio de trabalho. Criando um diretorio onde vai ser construida a solução
WORKDIR /app
#Copiando todos os packages*.json para o workdir. package*.json importa tanto o package quanto o package-lock.json
COPY package*.json ./
#Instalando as dependencias
RUN npm install
# Copiando todo o resto dos arquivos para o WORKDIR. O arquivo .dockerignore funciona como o .gitignore. Ele impede que alguns elementos nao sejam copiados. O node_modules no caso não é necessario.
COPY . . 
CMD ["node","server.js"]

# Por que copior primeiro os package.json e depois o resto?
# R: Por que se houver apenas uma mudança no código e não nas dependencias, o build da imagem não vai reinstalar todas as dependencias do projeto. Elas ainda estarão utilizando a cache. 