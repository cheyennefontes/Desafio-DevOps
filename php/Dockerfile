FROM php:8.0-fpm
# Utiliza a imagem oficial do PHP na versão 8.0-fpm como base para construir este contêiner.

RUN apt update \
    && apt install -y zlib1g-dev g++ git libicu-dev zip libzip-dev zip \
    # Executa o comando 'apt update' para atualizar o cache dos pacotes disponíveis e, em seguida, instala algumas dependências necessárias para as extensões do PHP que serão habilitadas a seguir.
    
    && docker-php-ext-install intl opcache pdo pdo_mysql \
    # Instala as extensões do PHP intl, opcache, pdo e pdo_mysql utilizando a ferramenta docker-php-ext-install.

    && pecl install apcu \
    && docker-php-ext-enable apcu \
    # Instala a extensão do PHP APCu e a habilita utilizando a ferramenta docker-php-ext-enable.

    && docker-php-ext-configure zip \
    && docker-php-ext-install zip
    # Configura e instala a extensão zip do PHP utilizando as ferramentas docker-php-ext-configure e docker-php-ext-install.

WORKDIR /var/www/symfony_docker
# Define o diretório de trabalho padrão do contêiner para /var/www/symfony_docker.

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
# Faz o download do instalador do Composer e o instala globalmente no contêiner.

RUN curl -sS https://get.symfony.com/cli/installer | bash
# Faz o download do instalador da CLI do Symfony e o executa utilizando o shell bash.

RUN mv /root/.symfony5/bin/symfony /usr/local/bin/symfony
# Move o executável da CLI do Symfony para o diretório /usr/local/bin para torná-lo acessível globalmente no contêiner

