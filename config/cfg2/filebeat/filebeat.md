# Filebeat 7.4
1. 拉取镜像：
```shell
docker pull docker.elastic.co/beats/filebeat:7.4.1
```
2. 文件夹说明：
* home   ： /usr/share/filebeat
* bin    ： /usr/share/filebeat
* config ： /usr/share/filebeat
* data   ： /usr/share/filebeat/data
* logs   ： /usr/share/filebeat/logs
3. 运行容器示例
```shell script
docker run -d \
  --name=filebeat \
  --user=root \
  --volume="$(pwd)/filebeat.docker.yml:/usr/share/filebeat/filebeat.yml:ro" \
  --volume="/var/lib/docker/containers:/var/lib/docker/containers:ro" \
  --volume="/var/run/docker.sock:/var/run/docker.sock:ro" \
  docker.elastic.co/beats/filebeat:7.4.1 filebeat -e -strict.perms=false \
  -E output.elasticsearch.hosts=["elasticsearch:9200"]
```