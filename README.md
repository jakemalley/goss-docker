# Goss Docker Container

Docker image based on the official [Docker in Docker](https://hub.docker.com/_/docker) image , with `goss` and `dgoss` installed for testing Docker images in CI environments.

See the Goss project here: https://goss.rocks

## Example

E.g. testing the `nginx:latest` image using the file `test/nginx-example/goss.yaml`
```
docker run \
    --rm \
    --name=goss-docker \
    --volume /var/run/docker.sock:/var/run/docker.sock \
    --volume $(pwd)/test:/test \
    --volume /tmp:/tmp \
    --env GOSS_FILES_PATH=/test/nginx-example \
    jakemalley/goss-docker:latest \
    dgoss run nginx:latest
```