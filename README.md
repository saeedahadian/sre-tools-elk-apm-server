# APM Server

APM is a service for monitoring some important metrics of a service e.g. error rate, successful transactions, etc. It uses an agent-server architecture. This is a simple APM server that is run using docker-compose. After deploying this service, you can connect your agents to it and send your service's metrics.


## Usage

Copy either of `.env.sample` or `.env.fish.sample` to `.env` and set your desired values.

```bash
cp .env.sample .env
```

If the elasticsearch server that APM attempts to connect to is using a secure connection (SSL), you need to also provide certificates in a separate volume that is named "certs." Note that this volume is external and you need to have it prior to starting the APM server. Besides SSL username and password, you need a `.pem` certificate to connect to elasticsearch over SSL.

The path to this certificate could be set in the `apm-server.docker.yml` file. 

```yaml
output.elasticsearch:
  hosts: ["es01"]
  enabled: true
  #compression_level: 0
  protocol: "https"
  #api_key: "id:api_key"
  username: "${SERVER_SSL_USERNAME}"
  password: "${SERVER_SSL_PASSWORD}"
  ssl.enabled: true
  ssl.certificate_authorities: "${CERTS_DIR}/kibana/elasticsearch-ca.pem"
```

The `ssl.certificate_authorities` field is the path where `.pem` file is placed. You can change the path here.

Finally, start the server using docker-compose.

```bash
docker-compose up -d
```
