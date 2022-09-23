FROM nginx:alpine

WORKDIR /usr/share/nginx/html

COPY ./dist/apps/react-app .

RUN printf "server {\n\
        listen       80;\n\
        location / {\n\
                root   /usr/share/nginx/html;\n\
                try_files \$uri \$uri/ /index.html;\n\
                add_header Cache-Control \"no-store, no-cache, must-revalidate\";\n\
        }\n\
}\n" > /etc/nginx/conf.d/default.conf

EXPOSE 80

CMD sed  -i '/\/\*ENV_BEGIN\*\/`/r '<(env | grep --color=never "^NX_") index.html; nginx '-g daemon off;'
