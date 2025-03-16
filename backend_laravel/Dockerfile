# Etapa 1: Configurar o ambiente PHP/Laravel
FROM php:8.2-fpm

# Instalando extensões necessárias
RUN apt-get update && apt-get install -y \
    zip \
    unzip \
    git \
    curl \
    libpng-dev \
    libfreetype-dev \ 
    libonig-dev \
    libxml2-dev \
    libjpeg62-turbo-dev \
    && docker-php-ext-install pdo_mysql mbstring exif pcntl bcmath gd

# Instalando Composer
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# Configurando diretório de trabalho
WORKDIR /var/www

# Copiando arquivos do Laravel para dentro do container
COPY . .

# Instalar dependências do Laravel
RUN composer install --no-dev --optimize-autoloader

# Permissões corretas para o Laravel
RUN chown -R www-data:www-data /var/www/storage /var/www/bootstrap/cache

#RUN useradd -m -G www-data -s /bin/bash laravel
#USER laravel

# Expondo a porta 9000
EXPOSE 9000

# Comando para iniciar o PHP-FPM
CMD ["php-fpm"]
