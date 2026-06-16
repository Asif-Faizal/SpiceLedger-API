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
| `proxyUrl` | `http://localhost:8080` |
| `baseUrl` | `http://localhost:8080/rest` |
| `graphqlUrl` | `http://localhost:8080/graphql` |

## Collection structure

| Folder | Endpoints |
|--------|-----------|
| **Health** | Proxy, REST, GraphQL health checks |
| **Auth** | Login (admin/merchant), refresh, logout |
| **Accounts** | Email check, CRUD, merchant info |
| **Products** | Create, list |
| **Grades** | Create, list by product |
| **Daily Prices** | Create, list, today by grade/product |
| **GraphQL Queries** | products, positions, transactions, admin dashboard (native GraphQL type) |
| **GraphQL Mutations** | create product/grade/price, buy, sell (native GraphQL type) |

## Seed credentials

- **Admin:** `admin@spice.com` / `secret123`
- **Merchant:** `merchant@spice.com` / `secret123`
- **Basic Auth (REST):** `admin` / `secret123`

## Notes

- List endpoints require trailing slashes: `/products/`, `/grades/`, `/daily-prices/`
- GraphQL requires Bearer JWT — run login requests first
- REST auto-injects Basic Auth when no Authorization header is sent
