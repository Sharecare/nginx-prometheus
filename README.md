## Documentation 

Docker image which provides an Nginx server based on OpenResty (alpine) with vts, sts, sts-stream and Prometheus lua metrics included.

- https://nginx.org
- https://openresty.org
- https://github.com/knyar/nginx-lua-prometheus
- https://github.com/vozlt/nginx-module-stream-sts
- https://github.com/vozlt/nginx-module-sts
- https://github.com/vozlt/nginx-module-vts

Adds a server instance listening on port 9527 with the following endpoints.

- http://localhost:9527/metrics
- http://localhost:9527/status/format/json
- http://localhost:9527/status/format/html
- http://localhost:9527/status/format/jsonp

The /metrics can be scraped directly with Prometheus. The /status requires an extra feature provided by https://github.com/hnlq715/nginx-vts-exporter.

## Sharecare Updates

To build the base image we need, execute the following command:
```shell
docker build -t nexus.admin.sharecare.com/nginx-prometheus -f Dockerfile .
```

Once the image is built, you'll need to login to Nexus and manually upload the image there:
```shell
docker login nexus.admin.sharecare.com
docker images (then look for the "IMAGE ID" of the one you want to tag)
docker tag <IMAGE ID> nexus.admin.sharecare.com/nginx-prometheus:<VERSION>
docker push nexus.admin.sharecare.com/nginx-prometheus:<VERSION>
docker tag <IMAGE ID> nexus.admin.sharecare.com/nginx-prometheus:latest
docker push nexus.admin.sharecare.com/nginx-prometheus:latest
```
