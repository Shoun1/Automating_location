Ambulance Dispatch & GPS Tracking System
An automated dispatch and GPS tracking system built using PostgreSQL as the backend database and Apache Airflow for task orchestration. The system is designed to ensure real-time ambulance status tracking and updates, but this functionality becomes fully operational only when live data is integrated. With seamless data visualization using Folium and periodic task automation via DAGs, the project serves as a robust prototype that can scale into a production-ready solution.


Key Features
Database-Driven Workflow

PostgreSQL stores ambulance status and location data.

psycopg2 enables reliable interaction between Python scripts and the database.

Apache Airflow Integration

DAG scheduled every 30 seconds to simulate real-time dispatch operations.

Modular Python operators to fetch, update, and log ambulance data.

Dynamic Status Management

On assignment, ambulance status is updated from Idle to On Duty.

CRUD operations support data lifecycle management.

Live GPS Mapping with Folium

Coordinates fetched from the database are visualized on an interactive map.

Maps are saved as HTML (ambulance_map.html) for rapid response view.

System Architecture
Layer	Technology
Automation	Apache Airflow
Backend	PostgreSQL
DB Connector	psycopg2
Mapping	Folium
Scheduler	Airflow DAG (30s)
Visual Output	HTML Map View

Database Operations
Connection: Connects to local PostgreSQL database using hostname, port, user, and password.

Cursoring: Cursor used to execute SELECT and UPDATE queries.

Table Operations:

ambulance_status: stores ID, status, latitude, longitude.

Example Query:

UPDATE ambulance_status SET status = 'On Duty' WHERE id = 1;
Airflow DAG Flow

start → connect_to_db → fetch_ambulance_data → update_status → plot_on_map → end
Custom Python operators manage each task.

DAG reruns every 30 seconds (configurable).

Setup Instructions
Clone Repository

git clone https://github.com/your-username/ambulance-tracker.git
cd ambulance-tracker
Set Up Virtual Environment

python -m venv env
source env/bin/activate  # Windows: env\Scripts\activate
pip install -r requirements.txt
Start PostgreSQL Database
Ensure your PostgreSQL server is running and accessible with correct host, port, and credentials.

Run Airflow Scheduler


airflow db init
airflow webserver --port 8080
airflow scheduler
Sample Output
The map output is saved as:

ambulance_map.html
It shows live ambulance positions and updates their movement across coordinates.

Tech Stack Summary
Apache Airflow: Task scheduling and orchestration

PostgreSQL: Backend data storage

psycopg2: Python to PostgreSQL connectivity

Folium: Real-time geographic visualization

Python: Backend and automation logic

