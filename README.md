# docker-opentsdb

opentsdb docker image

## Run server

```
# load default env
eval $(docker-machine env default)

# network 
docker network create vnet

# make docker-compose.yml 
./make_docker_compose_yml.sh hdfs hbase tsdb > docker-compose.yml

# hadoop+hbase+tsdb startup (zookeeper, journalnode, namenode, datanode, hmaster, regionserver, tsdb)
docker-compose up -d

# tail logs for a while
docker-compose logs -f

# check ps
docker-compose ps

# check stats
docker ps --format {{.Names}} | xargs docker stats

# check web ui
open http://$(docker-machine ip default):4242
```