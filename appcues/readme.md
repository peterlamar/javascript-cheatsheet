# App-cues demo

This demonstrates the static example for app cues. The example must be triggered
by a webserver. Opening this locally with your web browser using the file:// 
protocol will not work. 

## Demo

Add your project number and unique id to the index.html

### Locally

To run, pass the local html file to nginx 
in a docker container with the following run command.

```
docker run -v <this absolute path>:/usr/share/nginx/html -p 8080:80 nginx
```

## Reference

[docker hub nginx](https://hub.docker.com/_/nginx)