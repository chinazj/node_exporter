## Method to build arm64 images

```shell
git clone https://github.com/kubesphere/node_exporter.git

cd node_exporter

git checkout -b ks-v0.18.1 origin/ks-v0.18.1

docker buildx build -f build/arm64/Dockerfile --output type=docker,dest=node_exporter:ks-v0.18.1-arm64.tar --platform linux/arm64 -t kubesphere/node_exporter:ks-v0.18.1-arm64 .
```

