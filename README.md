# APM Server

APM is a service for monitoring some important metrics of a service e.g. error rate, successful transactions, etc. It uses an agent-server architecture. This is a simple APM server that is run using docker-compose. After deploying this service, you can connect your agents to it and send your service's metrics.


## Usage

Copy either of `.env.sample` or `.env.fish.sample` to `.env` and set your desired values.

```bash
cp .env.sample .env
```

Then, use docker-compose to start the server.

```bash
docker-compose up -d
```
