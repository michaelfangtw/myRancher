# myRancher

This project provides a simple way to deploy and manage a Rancher instance using Docker Compose.

## Prerequisites

Before you begin, ensure you have the following installed on your system:

*   [Docker](https://docs.docker.com/get-docker/)
*   [Docker Compose](https://docs.docker.com/compose/install/)

## Project Structure

*   `docker-compose.yaml`: The Docker Compose file that defines the Rancher service.
*   `compose.sh`: A helper script to easily start and stop the Rancher container.
*   `rancher-data/`: A directory used to store persistent data for the Rancher instance.
*   `.gitignore`: Specifies files that should be ignored by Git.

## Getting Started

1.  **Clone the repository:**

    ```bash
    git clone <repository-url>
    cd myRancher
    ```

2.  **Start the Rancher instance:**

    Use the provided `compose.sh` script to start the Rancher container in detached mode.

    ```bash
    ./compose.sh
    ```

    This script is a simple wrapper around the following Docker Compose commands:

    ```bash
    docker compose down
    docker compose up -d
    ```

## Accessing Rancher

Once the container is running, you can access the Rancher UI by navigating to the following URL in your web browser:

```
https://<your-server-ip>
```

If you are running this on your local machine, you can use `https://localhost`.

## Managing the Rancher Instance

### Stopping the instance

To stop the Rancher container, you can run:

```bash
docker compose down
```

### Viewing logs

To view the logs from the Rancher container, you can use the following command:

```bash
docker compose logs -f
```

## Configuration

The `docker-compose.yaml` file contains the configuration for the Rancher service.

*   **Image:** `rancher/rancher:v2.8.5` - Specifies the version of the Rancher image to use.
*   **Ports:** `80:80` and `443:443` - Maps the standard HTTP and HTTPS ports from the host to the container.
*   **Volumes:** `./rancher-data:/var/lib/rancher` - Mounts the `rancher-data` directory on the host to the container to persist Rancher's data.
*   **Restart Policy:** `always` - Ensures that the Rancher container will always restart if it stops.
*   **Privileged:** `true` - Gives the container extended privileges, which may be required for certain Rancher operations.

## Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

## License

[MIT](https.choosealicense.com/licenses/mit/)
