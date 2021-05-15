Minimal docker image based on `alpine` that bundles POSIX compliant fork of
[wait-for-it.sh](https://github.com/vishnubob/wait-for-it): https://github.com/raphaelahrens/wait-for-it

# Usage

```bash
docker run --rm -it lexuzieel/wait-for-it -h google.com -p 80
```

## In Kubernetes

I made this image to use it inside Kubernetes as an `initContainer`:

```yaml
initContainers:
  - name: wait-for-redis
    image: lexuzieel/wait-for-it
    args: [
      '-t', '0', # Wait indefinitely
      '-h', 'cache-redis',
      '-p', '6379'
    ]
```
