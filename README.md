# SpiceLedger API (Bruno)

Bruno collection documenting every working REST and GraphQL endpoint in [SpiceLedger-Backend](../SpiceLedger-Backend).

## Setup

1. Open this folder in [Bruno](https://www.usebruno.com/)
2. Select the **local** environment (top-right)
3. Start the backend: `make up-full` in `SpiceLedger-Backend`
4. **Close and reopen** the collection if REST folders look empty (Bruno caches the file tree)
5. Run **Auth → Login Admin** and **Auth → Login Merchant** to populate tokens

## Troubleshooting empty REST folders

If only GraphQL requests appear, close the collection completely and reopen it from **Open Collection → SpiceLedger-API**. All REST `.yml` files match the same format as the working Health requests (`type: http`, quoted URLs, `auth: inherit` or explicit auth).

## Base URLs (local environment)

| Variable | Default |
|----------|---------|
| `gatewayUrl` | `http://localhost:8080` |
| `baseUrl` | `http://localhost:8080/rest` |
| `graphqlUrl` | `http://localhost:8080/graphql` |

## Collection structure

| Folder | Endpoints |
|--------|-----------|
| **Health** | Gateway liveness/ready, REST health, GraphQL health (`__typename`) |
| **Auth** | Login (admin/merchant), refresh, logout |
| **Accounts** | Email check, CRUD, merchant info |
| **Products** | Create, list |
| **Grades** | Create, list by product |
| **Daily Prices** | Create, list, today by grade/product |
| **Merchant** | Merchant dashboard (portfolio, charts, insights) |
| **GraphQL Queries** | By use case: Admin, Catalog, Merchant |
| **GraphQL Mutations** | By use case: Admin (catalog mgmt), Merchant (buy/sell) |

## Seed credentials

- **Admin:** `admin@spice.com` / `secret123`
- **Merchant:** `merchant@spice.com` / `secret123`
- **Basic Auth (REST):** `admin` / `secret123`

## Notes

- List endpoints require trailing slashes: `/products/`, `/grades/`, `/daily-prices/`
- GraphQL requires Bearer JWT — run login requests first
- REST auto-injects Basic Auth when no Authorization header is sent

## GraphQL folder layout

```
GraphQL-Queries/
  Admin/          admin-dashboard
  Catalog/        products
  Merchant/       get-positions, get-grade-position, list-transactions, list-grade-transactions

GraphQL-Mutations/
  Admin/          create-product, create-grade, create-daily-price
  Merchant/       buy, sell

Merchant/         merchant-dashboard (full portfolio dashboard query)
```

Run **Auth → Login Merchant** before Merchant folder or GraphQL Merchant requests.
Run **Auth → Login Admin** before Admin GraphQL requests.
