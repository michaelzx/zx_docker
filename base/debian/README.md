```
docker build --rm --no-cache  -t <imageName> .
docker run -ti -d --name host <imageName> /bin/bash
docker run --rm -ti <imageName> /bin/bash
```