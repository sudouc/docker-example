```
docker build -t sudoapp .

docker swarm init
docker stack deploy --compose-file=docker-compose.yml prod
```

### Deploy new stack

New JS Code:

```js
var http = require('http');
var os = require('os');
http.createServer(function (req, res) {
    res.writeHead(200, {'Content-Type': 'text/html'});
    res.end(`<h1>I'm ${os.hostname()}!!!</h1>`);
}).listen(8080);

```

Tag new image with the version – in this case `v2`

```
docker build -t sudoapp:v2 .
```

Deploy new docker images

```
docker service update --image sudoapp:v2 prod_sudoapp
```
