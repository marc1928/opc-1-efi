#  The Notion Killer Docker Compose Setup - DocMost 

Welcome to the **DocMost Docker Compose** setup! This repository provides a seamless way to deploy and run **DocMost**, a powerful document management system, along with its required dependencies (PostgreSQL and Redis) using Docker Compose. Whether you're a developer, tester, or just exploring DocMost, this setup ensures a smooth experience.

---

## 🌟 Features of This Setup

- **Fully Containerized**: All services (DocMost, PostgreSQL, Redis) are containerized for consistency across environments.
- **Easy Configuration**: Pre-configured environment variables and volumes for quick deployment.
- **Persistent Storage**: Data persistence is ensured for both PostgreSQL and Redis.
- **Scalable**: Easily extendable for production use cases.
- **Developer-Friendly**: Includes clear instructions and best practices for local development.

---

## 📦 What's Included?

This Docker Compose file sets up the following services:

1. **DocMost**:
   - Image: `docmost/docmost:latest`
   - Port: Exposed on `3000` (accessible via `http://localhost:3000`)
   - Environment Variables:
     - `APP_URL`: The base URL of your DocMost instance.
     - `APP_SECRET`: A secret key for secure operations.
     - `DATABASE_URL`: Connection string for PostgreSQL.
     - `REDIS_URL`: Connection string for Redis.
   - Volumes: Persistent storage for uploaded files.

2. **PostgreSQL**:
   - Image: `postgres:16-alpine`
   - Database Name: `docmost`
   - User: `docmost`
   - Password: `xZh2xV4gOL0SMK`
   - Persistent Volume: Ensures data retention even after container restarts.

3. **Redis**:
   - Image: `redis:7.2-alpine`
   - Persistent Volume: Stores Redis data for caching and session management.

---

## 🚀 Getting Started

### Prerequisites

Before you begin, ensure you have the following installed on your machine:

- [Docker](https://www.docker.com/get-started)
- [Docker Compose](https://docs.docker.com/compose/install/)

### Step 1: Clone the Repository

```bash
git clone https://github.dev/docker/awesome-compose.git
cd docmost
docker compose up -d
```

### Step 2: Start the Services

Run the following command to start all services:

```bash
docker compose up -d
```

This will:
- Pull the required Docker images.
- Start the `docmost`, `db`, and `redis` containers in detached mode.
- Set up persistent volumes for data storage.

### Step 3: Access DocMost

Once the containers are up and running, you can access DocMost at:

```
http://localhost:3000
```

---

## 🛠️ Configuration

### Environment Variables

You can customize the behavior of the services by modifying the environment variables in the `docker-compose.yml` file:

- **DocMost**:
  - `APP_URL`: Update this if you're hosting DocMost on a different domain or port.
  - `APP_SECRET`: Replace with a unique secret key for enhanced security.
  - `DATABASE_URL` and `REDIS_URL`: Ensure these match your database and Redis configurations.

- **PostgreSQL**:
  - `POSTGRES_DB`, `POSTGRES_USER`, and `POSTGRES_PASSWORD`: Modify these if you want to use custom credentials.

### Persistent Volumes

The following volumes are created to ensure data persistence:

- `docmost`: Stores uploaded files and other application data.
- `db_data`: Stores PostgreSQL data.
- `redis_data`: Stores Redis data.

To clean up all data and start fresh, you can remove the volumes:

```bash
docker compose down -v
```

---

## 🧰 Maintenance

### View Logs

To view logs for a specific service:

```bash
docker compose logs <service_name>
```

For example, to view logs for DocMost:

```bash
docker compose logs docmost
```

### Restart Services

If you make changes to the configuration, restart the services:

```bash
docker compose restart
```

### Stop Services

To stop all services:

```bash
docker compose down
```

---

## 📝 Notes

1. **Security**: For production use, replace the default `APP_SECRET`, `POSTGRES_PASSWORD`, and other sensitive values with strong, unique ones.
2. **Backup**: Regularly back up your PostgreSQL and Redis data to prevent data loss.
3. **Scaling**: This setup is designed for local development. For production, consider scaling services and optimizing resource allocation.

---

## 🤝 Contributing

We welcome contributions! If you find any issues or have suggestions for improvement, feel free to open an issue or submit a pull request.

---

## 📄 License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgments

- **DocMost Team**: For creating an amazing document management system.
- **Docker Community**: For providing tools that make containerization easy and accessible.

---

Happy coding! 🚀