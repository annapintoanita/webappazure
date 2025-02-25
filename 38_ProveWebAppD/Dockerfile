# Usa l'immagine ufficiale di Nginx
FROM nginx:latest

# Copia i file HTML nella cartella di Nginx
COPY index.html /usr/share/nginx/html/index.html


#Esponi la porta 80 per il server web
EXPOSE 80 


# Avvia Ngnx
# -g deamon off;" serve a far partire Ngnx in primo piano
CMD ["nginx", "-g" , "deamon off;"]  