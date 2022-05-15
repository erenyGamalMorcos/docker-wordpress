FROM nginx:latest


COPY vhost.conf /etc/nginx/conf.d/default.conf


RUN apt-get update \
    && apt-get install -y openssl \
    && apt-get install -y bash \
    && apt-get install -y curl \
    && apt-get install -y cron


# Rocket-Nginx configuration
COPY gzip.conf /etc/nginx/conf.d/gzip.conf

# Add crontab file in the cron directory
COPY crontab /etc/cron.d/wordpress-cron
# Give execution rights on the cron job && link created cron file
RUN chmod 0644 /etc/cron.d/wordpress-cron && crontab /etc/cron.d/wordpress-cron	  
