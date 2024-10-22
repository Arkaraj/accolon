# Accolon

## Overview
A **Real-time User Activity Analytics Platform** which is a backend service designed to track user activities (like clicks, views, and purchases) in real-time, process them asynchronously, and provide low-latency querying for analytics and reporting purposes. This service ensures high throughput and low latency by leveraging Apache Kafka for event streaming, Redis for real-time caching, and PostgreSQL for persistent data storage.

## Features
1. **Event Ingestion**:
    - RESTful APIs to capture user activities such as clicks, views, and searches.
    - Activities are streamed to **Kafka** for asynchronous processing.

2. **Real-time Processing**:
    - Kafka consumers in **Spring Boot** process activity streams in real time.
    - Redis is used to store real-time analytics data such as active users or recent clicks.
    - PostgreSQL stores historical data for long-term querying and analytics.

3. **Data Storage**:
    - **Redis**: Stores aggregated real-time data (e.g., online users, active sessions) for fast access.
    - **PostgreSQL**: Long-term storage of detailed user activity logs and historical data.

4. **Querying and Reporting**:
    - Real-time data queries are served from **Redis** for low-latency responses.
    - Historical data queries are handled by **PostgreSQL** for in-depth reporting.

5. **Alerting & Notifications**:
    - Kafka streaming analytics allows real-time monitoring of thresholds (e.g., sudden activity spikes).
    - Alerts are triggered and published to Kafka topics when certain conditions are met.

6. **Scalability**:
    - The system leverages Kafka's ability to scale horizontally to handle large volumes of incoming events.
    - Redis provides quick access to the latest, frequently used data, ensuring high performance.

## Tech Stack
- **Java Spring Boot**: For developing RESTful APIs, Kafka consumers, and services.
- **Apache Kafka**: For event streaming and asynchronous processing.
- **Redis**: For caching real-time data, ensuring low-latency queries.
- **PostgreSQL**: For long-term storage of user activity logs and complex queries.
- **Spring Data Redis**: For easy integration of Redis into Spring Boot services.
- **Spring Kafka**: For integrating Kafka with Spring Boot for event-driven architecture.

## Project Structure
```

```

## Key Challenges

### 1. **Real-time Data Flow Optimization**:
- Managing high throughput of user activity events in real time using **Kafka**.
- Balancing between real-time event processing and the need for fast response times.

### 2. **Efficient Use of Redis**:
- Designing Redis key structures that provide low-latency access to aggregated data (e.g., online users or recent activity).
- Ensuring that Redis can handle both high write loads and frequent read requests without becoming a bottleneck.

### 3. **Data Consistency Between Redis and PostgreSQL**:
- Ensuring consistency between real-time data stored in **Redis** and the persistent historical data stored in **PostgreSQL**.
- Handling potential race conditions or discrepancies when aggregating and querying across both data stores.

### 4. **Scalability**:
- Ensuring the system can handle a large number of user events concurrently without degradation in performance.
- Scaling **Kafka** and **Redis** to manage spikes in activity while maintaining low-latency processing.

### 5. **Alerting on Activity Spikes**:
- Developing real-time monitoring mechanisms using Kafka to detect and alert on sudden spikes in user activity or unusual behaviors.

## Getting Started

### Prerequisites
- **Java 17+**
- **Apache Kafka**: Installed and running.
- **Redis**: Installed and running.
- **PostgreSQL**: Installed and running.

### Installation
1. Clone this repository:
   ```bash
   git clone https://github.com/Arkaraj/accolon.git
   cd accolon
   ```

2. Update `application.properties` with your PostgreSQL, Kafka, and Redis configurations:
   ```properties
   # PostgreSQL
   spring.datasource.url=jdbc:postgresql://localhost:5432/activity_db
   spring.datasource.username=your_username
   spring.datasource.password=your_password

   # Kafka
   kafka.bootstrap-servers=localhost:9092
   kafka.topic=activity-tracking

   # Redis
   spring.redis.host=localhost
   spring.redis.port=6379
   ```

3. Build and run the application:
   ```bash
   mvn clean install
   mvn spring-boot:run
   ```

### API Endpoints

- **POST /api/activity**:
    - Endpoint to ingest user activity data.
    - Body:
      ```json
      ```

- **GET /api/activity/summary**:
    - Get real-time summary of user activities (e.g., active users, most clicked items).

## License


---
