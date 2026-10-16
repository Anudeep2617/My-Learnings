# Stripe Payment Method Configurations API Reference

## 1. Overview

### Purpose

The Payment Method Configurations API allows a Stripe account to create, retrieve, update, and list configurations that control payment-method availability and display preferences in supported payment flows.

A configuration does not process a payment. It controls settings used by a supported checkout or payment integration.

**Official documentation:** https://docs.stripe.com/api/payment_method_configurations

### Intended audience

- Backend developers
- API integrators
- Technical support engineers
- Developers implementing Stripe Connect

## 2. Base URL

All requests use the following base URL:

`https://api.stripe.com`

All requests must use HTTPS.

## 3. Authentication and security

Stripe authenticates API requests using API keys.

### Supported key types

| Key type | Purpose |
|---|---|
| Publishable key (`pk_test_...` or `pk_live_...`) | Used in client-side integrations where supported. |
| Secret key (`sk_test_...` or `sk_live_...`) | Used for authenticated server-side API requests. |
| Restricted key (`rk_...`) | Provides limited server-side permissions based on its configuration. |

A secret key is required for the server-side requests in this reference.

### Obtain an API key

1. Sign in to the Stripe Dashboard.
2. Open the API keys section: https://dashboard.stripe.com/apikeys
3. Select the appropriate test or live environment.
4. Use a test secret key for development.

### Configure the key

Store the secret key in an environment variable or an approved secrets manager.

```bash
export STRIPE_SECRET_KEY="sk_test_REPLACE_WITH_YOUR_TEST_KEY"
```

The value above is a placeholder, not a valid key.

### Authorization header

Stripe uses HTTP Basic authentication. With `curl`, supply the secret key as the username and an empty password:

```bash
curl https://api.stripe.com/v1/payment_method_configurations \
  -u "$STRIPE_SECRET_KEY:"
```

**Security requirements**

- Never expose secret keys in frontend code, public repositories, screenshots, or logs.
- Do not commit credentials to Git.
- Use test keys during development.
- Restrict access to keys and rotate exposed credentials.
- Make all API requests over HTTPS.

## 4. Endpoint summary

| Operation | HTTP method | Endpoint |
|---|---|---|
| Create a configuration | POST | `/v1/payment_method_configurations` |
| Update a configuration | POST | `/v1/payment_method_configurations/{configuration_id}` |
| Retrieve a configuration | GET | `/v1/payment_method_configurations/{configuration_id}` |
| List configurations | GET | `/v1/payment_method_configurations` |

Stripe uses `POST` for updates to this resource. Follow the documented method rather than substituting `PATCH`.

## 5. Create a payment method configuration

### Purpose

Creates a Payment Method Configuration object.

**Endpoint:** `POST /v1/payment_method_configurations`

### Request parameters

| Parameter | Type | Required | Description |
|---|---|---|---|
| `name` | string | Required unless `parent` is provided | Name of the configuration. |
| `parent` | string | Required unless `name` is provided | Parent configuration ID used to create a child configuration. |
| Payment-method settings | object | Optional | Settings for supported payment methods, such as `card` or `affirm`. |

Payment-method-specific objects and their supported fields vary. Refer to the official endpoint schema before using additional parameters.

### Request example

```bash
curl https://api.stripe.com/v1/payment_method_configurations \
  -u "$STRIPE_SECRET_KEY:" \
  -d "name=Website checkout configuration"
```

This example creates a configuration by name. It does not configure every payment method or guarantee that a particular method is available.

### Successful response

The API returns a Payment Method Configuration object. The following is a shortened illustrative example:

```json
{
  "id": "pmc_example123",
  "object": "payment_method_configuration",
  "active": true,
  "name": "Website checkout configuration"
}
```

The ID and values above are illustrative. The actual response can contain additional fields.

### Response parameters

| Field | Type | Description |
|---|---|---|
| `id` | string | Unique identifier of the configuration. |
| `object` | string | Object type: `payment_method_configuration`. |
| `active` | boolean | Indicates whether the configuration can be used for new payments. |
| `name` | string or null | Configuration name, where applicable. |
| `parent` | string or null | Parent configuration ID, where applicable. |
| Payment-method fields | object | Settings and effective availability for individual payment methods. |

### Success status

Stripe's API normally returns `200 OK` for a successful create request. Verify the response body to confirm that the configuration was created.

## 6. Update a payment method configuration

### Purpose

Updates an existing configuration.

**Endpoint:** `POST /v1/payment_method_configurations/{configuration_id}`

### Path parameters

| Parameter | Type | Required | Description |
|---|---|---|---|
| `configuration_id` | string | Yes | ID of the configuration to update. |

### Request parameters

| Parameter | Type | Required | Description |
|---|---|---|---|
| `active` | boolean | No | Whether the configuration can be used for new payments. |
| `name` | string | No | Updated configuration name. |
| Payment-method settings | object | No | Updates supported settings for a payment method. |

### Request example

```bash
curl https://api.stripe.com/v1/payment_method_configurations/pmc_example123 \
  -u "$STRIPE_SECRET_KEY:" \
  -d "active=true"
```

Replace `pmc_example123` with an actual configuration ID.

### Successful response

Stripe returns the updated configuration object. Inspect the response to verify the updated fields.

### Success status

`200 OK`

## 7. Retrieve a payment method configuration

### Purpose

Retrieves a configuration by its ID.

**Endpoint:** `GET /v1/payment_method_configurations/{configuration_id}`

### Path parameters

| Parameter | Type | Required | Description |
|---|---|---|---|
| `configuration_id` | string | Yes | ID of the configuration to retrieve. |

### Request example

```bash
curl https://api.stripe.com/v1/payment_method_configurations/pmc_example123 \
  -u "$STRIPE_SECRET_KEY:"
```

### Successful response

The response contains the requested configuration object, including its ID, active state, and applicable payment-method settings.

Use the response to verify that the expected configuration exists and that its settings are correct.

### Success status

`200 OK`

## 8. List payment method configurations

### Purpose

Returns a list of configurations accessible to the account.

**Endpoint:** `GET /v1/payment_method_configurations`

### Query parameters

| Parameter | Type | Required | Description |
|---|---|---|---|
| `application` | string | No | Filters configurations by associated Connect application, where applicable. |
| `ending_before` | string | No | Returns results before the specified object ID. |
| `limit` | integer | No | Limits the number of objects returned. |
| `starting_after` | string | No | Returns results after the specified object ID. |

### Request example

```bash
curl -G https://api.stripe.com/v1/payment_method_configurations \
  -u "$STRIPE_SECRET_KEY:" \
  -d "limit=10"
```

### Successful response

A list request returns a list object. The following example is illustrative:

```json
{
  "object": "list",
  "has_more": false,
  "data": [
    {
      "id": "pmc_example123",
      "object": "payment_method_configuration",
      "active": true,
      "name": "Website checkout configuration"
    }
  ]
}
```

### Response parameters

| Field | Type | Description |
|---|---|---|
| `object` | string | Identifies the response as a list. |
| `data` | array | Configuration objects returned by the request. |
| `has_more` | boolean | Indicates whether more results are available. |

### Pagination

If `has_more` is `true`, retrieve the next page using `starting_after` with the last object ID from the current page. Use `ending_before` to navigate in the opposite direction.

### Success status

`200 OK`

## 9. Error handling

Stripe returns an HTTP status code and an error response when a request fails.

| HTTP status | General meaning | Recommended action |
|---|---|---|
| `400 Bad Request` | Invalid request or parameter. | Verify parameter names, types, and supported values. |
| `401 Unauthorized` | Authentication failed. | Verify the API key and authentication syntax. |
| `403 Forbidden` | The request is not permitted. | Check account access and permissions. |
| `404 Not Found` | The resource cannot be found or accessed. | Verify the configuration ID and account context. |
| `429 Too Many Requests` | The request was rate-limited. | Reduce request frequency and follow retry guidance. |
| `5xx` | Server-side error. | Retry cautiously when appropriate and investigate persistent failures. |

The exact status and error details depend on the request. Use Stripe's current error reference for authoritative behavior.

### Example error response

```json
{
  "error": {
    "type": "invalid_request_error",
    "message": "Invalid request parameters."
  }
}
```

This is an illustrative response. Actual error objects can include additional fields, such as an error code or request identifier.

### Error-handling recommendations

- Inspect the HTTP status code and error type.
- Use stable error codes when available instead of parsing message text.
- Record the Stripe request ID when investigating failures.
- Never log secret keys or sensitive payment details.
- Avoid blindly retrying requests that might create duplicate resources.

## 10. Troubleshooting

| Problem | Possible cause | Resolution |
|---|---|---|
| Authentication fails | Invalid key or incorrect environment. | Verify the key and confirm test/live mode. |
| Configuration cannot be retrieved | Incorrect ID or account context. | Verify the ID and account associated with the request. |
| Request is rejected | Unsupported parameter or invalid value. | Compare the request with the current API schema. |
| Payment method is not displayed | Ineligible account, payment flow, or configuration settings. | Check payment-method availability and effective display preferences. |
| Results are incomplete | More list pages are available. | Check `has_more` and paginate. |
| Rate limit is exceeded | Too many requests. | Reduce request frequency and apply appropriate retry handling. |

## 11. Related resources

- Payment Method Configurations API: https://docs.stripe.com/api/payment_method_configurations
- Stripe API authentication: https://docs.stripe.com/api/authentication
- Stripe API errors: https://docs.stripe.com/api/errors
- Stripe API keys: https://docs.stripe.com/keys
- Payment Methods API: https://docs.stripe.com/api/payment_methods

## 12. Documentation note

This independently authored reference is intended for a technical-writing portfolio. The request examples use placeholder IDs and environment variables. Verify all parameter details, response fields, and error behavior against the current Stripe API documentation before using these examples in a live integration.
