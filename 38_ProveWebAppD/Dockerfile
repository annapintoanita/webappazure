# Usa l'immagine ufficiale di Nginx / --> (registry)
FROM nginx:latest 


# Copia il file di configurazione personalizzato di nginx
# Copy ngix.conf /etc/ngnix.conf

# Copia i file HTML nella cartella di Nginx
COPY index.html /usr/share/nginx/html/index.html


#Esponi la porta 80 per il server web
EXPOSE 80 


# Avvia Nginx
# -g deamon off;" serve a far partire Ngnx in primo piano
CMD ["nginx", "-g" , "daemon off;"]  