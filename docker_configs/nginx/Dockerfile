# Configurar o ambiente Nginx para servir a aplicação Angular
# E a configuração do Nginx para servir a api laravel
FROM nginx:alpine

# Permissões geral
RUN chmod -R 777 /usr/share/nginx/html/
RUN chmod -R 777 /etc/nginx
RUN chmod -R 777 /etc/nginx

# Remove os arquivos padrão do Nginx
RUN rm -rf /usr/share/nginx/html/

# Copia o build da aplicação Angular para o diretório do Nginx
COPY --from=pergeco-frontend_angular /app/dist/frontend_angular usr/share/nginx/html

#COPY default.conf /etc/nginx/conf.d/default.conf

# Copia o arquivo de configuração do Nginx para o container
COPY nginx.conf /etc/nginx/nginx.conf

# Copia o arquivo de tipos de mídia para o container
COPY mime.types /etc/nginx/mime.types

# Expõe a porta 80 do container
EXPOSE 80  

# Inicia o servidor Nginx
CMD ["nginx", "-g", "daemon off;"]