# Data Streaming Project: Optimize Chicago Public Transportation
 
## A streaming event pipeline around Apache Kafka and its ecosystem. 
Using public data from the Chicago Transit Authority, an event pipeline around Kafka was created that allows to simulate and display the status of train lines in real time.

## After running
A website is showing trains move from station to station. A sample:
![Sample image of website](/images/website.png)

## Running on Your Computer
NOTE: You must allocate at least 4gb RAM to your Docker-Compose environment to run locally.

To run the simulation, you must first start up the Kafka ecosystem on your machine utilizing Docker-Compose.

`docker-compose up`

Docker-Compose can take some minutes to start. Once Docker-Compose is ready, the following services will be available on your local machine:

| Service        | URL           | Username | Password |
| ------------- |:-------------| --- | --- |
| Public Transit Status     | http://localhost:8888 | | |
|  Kafka      | PLAINTEXT://localhost:9092,PLAINTEXT://localhost:9093,PLAINTEXT://localhost:9094 | | |
| REST Proxy | http://localhost:8082 | | |
| Schema Registry |http://localhost:8881 | | |
| Kafka Connect | http://localhost:8083 | | |
| KSQL | http://KSQL:8088 | | |
| PostgreSQL | jdbc:postgresql://localhost:5432/cta | cta_admin | chicago |


### To run the producer:

1. `cd producers`
2. `virtualenv venv`
3. `. venv/bin/activate`
4. `pip install -r requirements.txt`
5. `python simulation.py`
6. `Once the simulation is running, you may hit Ctrl+C at any time to exit.`

### To run the Faust Stream Processing Application:

If using Project Workspace:

1. `cd consumers`
2. `virtualenv venv`
3. `. venv/bin/activate`
4. `pip install -r requirements.txt`
5. `faust -A faust_stream worker -l info`

### To run the KSQL Creation Script:

1. `cd consumers`
2. `virtualenv venv`
3. `. venv/bin/activate`
4. `pip install -r requirements.txt`
5. `python ksql.py`

### To run the consumer:

1. `cd consumers`
2. `virtualenv venv`
3. `. venv/bin/activate`
4. `pip install -r requirements.txt`
5. `python server.py`
