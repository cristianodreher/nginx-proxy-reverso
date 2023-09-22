# Use a imagem oficial do PHP com o servidor Apache embutido
FROM php:8.0-apache

# Copie o arquivo index.php para o diretório padrão do Apache
COPY index.php /var/www/html/

# Exponha a porta 80 para acessar o servidor web
EXPOSE 80
EXPOSE 443


# Crie um arquivo de configuração para redirecionamento HTTP para HTTPS
RUN echo "<VirtualHost *:80>\n\
    ServerName nextjeans.com.br\n\
    Redirect permanent / https://nextjeans.com.br/\n\
</VirtualHost>" > /etc/apache2/sites-available/redirect.conf

# Ative o arquivo de configuração de redirecionamento
RUN a2ensite redirect

# Configure o Apache para usar o certificado SSL
RUN a2enmod ssl

# Inicialize o Apache
CMD ["apache2-foreground"]