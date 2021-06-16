FROM nginx:stable
WORKDIR /root/docker-compose/nginx/
COPY nginx.conf /etc/nginx/nginx.conf
COPY joomla.albanv.fr.conf /etc/nginx/conf.d/joomla.albanv.fr.conf
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
