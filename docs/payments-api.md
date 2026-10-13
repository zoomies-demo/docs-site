# Payments API

## Create a charge

`POST /v1/charges`

| Field | Type | Notes |
| --- | --- | --- |
| `amount` | integer | The currency's smallest unit: `1250` is 12.50. Positive, at most `10000000`. |
| `currency` | string | `GBP`, `EUR` or `USD`, in any case. |
| `reference` | string | Your own identifier for the order. Required. |

Send an `Idempotency-Key` header to make a retry safe. A second request with the
same key returns the first charge, with status `200` and an
`Idempotent-Replay: true` header. Reusing a key for a different charge is
refused with `409`.

| Status | Meaning |
| --- | --- |
| `201` | The charge was created. |
| `200` | A retry: this is the charge made the first time. |
| `400` | The body is not a charge, or has a field the API does not know. |
| `409` | The idempotency key was used for a different charge. |
| `422` | The charge is not valid. The message says what to change. |

## Read a charge

`GET /v1/charges/{id}` returns the charge, or `404`.

## Health

`GET /healthz` answers `{"ok": true}`.
