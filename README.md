# Weather ETL Pipeline (Apache Airflow + Docker)

A simple ETL pipeline that fetches London's weather data (using latitude & longitude), processes it, and prints the results. Built with Apache Airflow and run using Docker, with scheduled execution.

## Location Used
- City: London
- Latitude: 51.5074
- Longitude: -0.1278

## Tech Stack
- Apache Airflow
- Docker & Docker Compose
- Python
- Open-Meteo Weather API

## How It Works
1. **Extract** – Fetch current weather data for London from the weather API.
2. **Transform** – Clean and format the data (temperature, windspeed, time).
3. **Load** – Print the final weather data (can be extended to save to a file/DB).

## Setup & Run

```bash
git clone https://github.com/<your-username>/weather-etl-airflow.git
cd weather-etl-airflow
docker compose up airflow-init
docker compose up -d
```

Open the Airflow UI at `http://localhost:8080` (login: `airflow` / `airflow`), then turn ON and trigger the `weather_etl_dag`.

## Scheduling

The DAG runs automatically on a schedule (default: hourly), set in `dags/weather_etl_dag.py`:

```python
schedule_interval='@hourly'
```

## Sample Output

```
London Weather Update -> {'temperature_C': 18.5, 'windspeed_kmh': 12.3, 'time': '2026-07-17T10:00'}
```

## License

MIT
