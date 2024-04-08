1. Install docker desktop
2. ```
   ❯ docker buildx create --name mybuilder
   mybuilder
   ❯ docker buildx use mybuilder
   ❯ docker buildx inspect --bootstrap
   ```
3. docker buildx build --platform linux/amd64,linux/arm64 -t <repo_url>/<path>:<tag> --push .
