# Getting started

You need Node 22 or later for the storefront and Go 1.22 or later for the
payments service. Neither project has any dependencies to install.

## Run the storefront's tests

```sh
git clone https://github.com/zoomies-demo/storefront
cd storefront
npm test
```

## Run the payments service

```sh
git clone https://github.com/zoomies-demo/payments-api
cd payments-api
go test ./...
ADDR=127.0.0.1:8080 go run .
```

Then, from another terminal:

```sh
curl -s -X POST http://127.0.0.1:8080/v1/charges \
  -H 'Content-Type: application/json' \
  -H 'Idempotency-Key: demo-1' \
  -d '{"amount": 1250, "currency": "GBP", "reference": "order-7"}'
```

Send it twice. The second answer is the same charge, with an
`Idempotent-Replay: true` header.
