# docker-swarm

README IN CONSTRUCTION

What do you have :

- **dc stack** with Traefik & Portainer
- **blog stack** with WordPress (FPM, php handler and files only !), Nginx and MariaDB, Redis, nginx-exporter and sql-exporter to have some metrics parsed by/from Prometheus
- **stats stack** with Matomo (FPM, php handler and files only !), Nginx and MariaDB, nginx-exporter and sql-exporter to have some metrics parsed by/from Prometheus
- **monitoring stack** with Grafana, Prometheus, cAdvisor and Node-Exporter

Before starting these stacks :

```bash
# create networks overlay that will be attached by containers
docker network create --driver=overlay --attachable oueb
docker network create --driver=overlay --attachable backend
docker network create --driver=overlay --attachable monitoring
```

How to play with it :

```bash
git clone https://github.com/Mettmett/docker-swarm.git && cd docker-swarm
docker stack deploy --compose-file dc-stack.yml dc
docker stack deploy --compose-file monitoring-stack.yml monitoring
docker stack deploy --compose-file blog-stack.yml blog
docker stack deploy --compose-file stats-stack.yml stats
```

Enjoy it.. ;)
