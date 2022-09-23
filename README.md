# Dockerized react app with runtime environment variables
To start run
```
nx docker react-app
docker run --rm -p 8080:80 -e NX_ENV_VARIABLE=foo react-app
```