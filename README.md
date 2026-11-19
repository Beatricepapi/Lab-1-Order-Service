# Lab 7 - Docker and Data Persistence

I containerised the Order Service using a Dockerfile based on Eclipse Temurin Java 21. The Docker image was built as `cicd1-order-service:lab7`.

I created a `compose.yaml` file to run the Order Service on port 8082. I configured the production profile, the Catalog Service URL, and a Docker named volume, `order_data`, to store the H2 database files.

## Testing

1. **Docker image:** Successfully built `cicd1-order-service:lab7`.
2. **Docker Compose:** Successfully started the Order Service on port 8082.
3. **Catalog integration:** `GET /orders/test-catalog/1` returned HTTP 200 OK with product ID 1, name Laptop, and price 750.
4. **POST /orders:** Created an order with product ID 1 and quantity 2. Received HTTP 200 OK.
5. **GET /orders:** Returned HTTP 200 OK and displayed the saved order with ID 1.
6. **Persistence test:** Restarted the Order Service container using `docker compose restart`. After restarting, `GET /orders` returned HTTP 200 OK and the original order was still present.

## Result

The Order Service runs successfully in Docker, communicates with the Catalog Service, and retains order data across container restarts using the Docker named volume `order_data`.