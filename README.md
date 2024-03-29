# Historical OHLC Price Data

We have just purchased a large amount of historical OHLC price data that were shared to us in CSV files format. We need to start centralising and digitalising those data. These files can be ranging from a few GBs to a couple of TBs.
 

## Quickstart

### Deploy using Docker

1. Make sure you have Docker installed.
2. Clone this repo to your local machine

```bash
git clone https://github.com/vandanapareek/ohlc-price-data.git
```

3. Change to the directory for the project.
```bash
cd ohlc-price-data
```

4. Build or rebuild the services

```bash
docker compose build
```

5. Start a container that serves the development version of the app

```bash
# Open your browser at http://localhost:8080 to access the app
docker compose up
```

## REST API example

### 1. Upload CSV API

```http
POST /read-csv
```

| Parameter | Type | Description |
| :--- | :--- | :--- |
| `file` | `file` | **Required**. |


### Response

```javascript
{
    "msg": "CSV successfully uploaded. Total processed rows:5"
}
```


### 2. Search and Pagination API

```http
GET /search?page=1&count=100&symbol=BTCUSDT&open_price=gt:4212&close_price=lteq:42124
```

### Response

```javascript
[
    {
        "unix": 1644719640000,
        "symbol": "BTCUSDT",
        "open": 42113.08000000,
        "high": 42126.32000000,
        "low": 42113.07000000,
        "close": 42123.07000000
    },
    {
        "unix": 1644719640000,
        "symbol": "BTCUSDT",
        "open": 42113.47000000,
        "high": 42126.22000000,
        "low": 42113.06000000,
        "close": 42123.47000000
    }
]
```