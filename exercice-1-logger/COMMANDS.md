## docker volume create logs_volume
## docker pull alpine
## docker run --name logger1 -v logs_volume:/var/logs alpine sh -c "echo 'Log depuis logger1' >> /var/logs/app.log"
## docker run --name logger2 -v logs_volume:/var/logs alpine sh -c "echo 'Log depuis logger2' >> /var/logs/app.log"
## docker run --rm -v logs_volume:/var/logs alpine cat /var/logs/app.log
## docker rm -f logger1 logger2
## docker run --rm -v logs_volume:/var/logs alpine cat /var/logs/app.log
## docker volume rm logs_volume









console complète : 












PS C:\Users\Hicha\Desktop\dev\cours-docker\docker-tp-volumes\exercice-1-logger> docker volume logs_volume
docker: unknown command: docker volume logs_volume

Usage:  docker volume COMMAND

Run 'docker volume --help' for more information
PS C:\Users\Hicha\Desktop\dev\cours-docker\docker-tp-volumes\exercice-1-logger> docker volume create logs_volume
logs_volume
PS C:\Users\Hicha\Desktop\dev\cours-docker\docker-tp-volumes\exercice-1-logger> docker pull alpine
Using default tag: latest
latest: Pulling from library/alpine
Digest: sha256:25109184c71bdad752c8312a8623239686a9a2071e8825f20acb8f2198c3f659
Status: Downloaded newer image for alpine:latest
docker.io/library/alpine:latest
PS C:\Users\Hicha\Desktop\dev\cours-docker\docker-tp-volumes\exercice-1-logger> docker run --name logger1 alpine
PS C:\Users\Hicha\Desktop\dev\cours-docker\docker-tp-volumes\exercice-1-logger> docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
PS C:\Users\Hicha\Desktop\dev\cours-docker\docker-tp-volumes\exercice-1-logger> docker images
REPOSITORY                                TAG       IMAGE ID       CREATED          SIZE
chami59212/stats-api                      2.0.0     20fb24e612ba   6 minutes ago    186MB
chami59212/stats-api                      latest    20fb24e612ba   6 minutes ago    186MB
<none>                                    <none>    00d7d3f56eca   16 minutes ago   186MB
<none>                                    <none>    81614ead6ceb   55 minutes ago   186MB
chami59212/stats-api                      2.0.3     2599ecaf2a1a   55 minutes ago   186MB
chami59212/stats-api                      1.0.0     314a0ee84b70   2 hours ago      202MB
chami59212/weather-api                    1.0.0     41d62b29316b   2 hours ago      196MB
chami59212/weather-api                    latest    41d62b29316b   2 hours ago      196MB
chami59212/stats-api                      2.0.2     26a25f304048   3 hours ago      197MB
<none>                                    <none>    bd5d7aee36c4   3 hours ago      197MB
mon_app_python                            latest    86f2a8bc2296   3 hours ago      197MB
hello-flask                               1.0.0     e31129edc842   3 hours ago      197MB
hello-flask                               latest    e31129edc842   3 hours ago      197MB
chami59212/stats-api                      2.0.1     61d97e7f8d2a   3 hours ago      197MB
alpine                                    latest    25109184c71b   5 weeks ago      13MB
kalilinux/kali-rolling                    latest    8913de4b58ee   4 months ago     192MB
anssi/fcsc2024-pwn-blind-attack           latest    f367da0196ef   22 months ago    14.8MB
anssi/fcsc2024-pwn-blind-attack-shovel    latest    69ba9950856b   22 months ago    212MB
anssi/fcsc2021-web-push-it-to-the-limit   latest    3377a2e2dc8e   2 years ago      647MB
tleemcjr/metasploitable2                  latest    e559450b37dc   8 years ago      2.3GB
PS C:\Users\Hicha\Desktop\dev\cours-docker\docker-tp-volumes\exercice-1-logger> docker -h
Flag shorthand -h has been deprecated, use --help
Usage:  docker [OPTIONS] COMMAND

A self-sufficient runtime for containers

Common Commands:
  run         Create and run a new container from an image
  exec        Execute a command in a running container
  ps          List containers
  build       Build an image from a Dockerfile
  bake        Build from a file
  pull        Download an image from a registry
  push        Upload an image to a registry
  images      List images
  login       Authenticate to a registry
  logout      Log out from a registry
  search      Search Docker Hub for images
  version     Show the Docker version information
  info        Display system-wide information

Management Commands:
  ai*         Docker AI Agent - Ask Gordon
  builder     Manage builds
  buildx*     Docker Buildx
  cloud*      Docker Cloud
  compose*    Docker Compose
  container   Manage containers
  context     Manage contexts
  debug*      Get a shell into any image or container
  desktop*    Docker Desktop commands
  extension*  Manages Docker extensions
  image       Manage images
  init*       Creates Docker-related starter files for your project
  manifest    Manage Docker image manifests and manifest lists
  mcp*        Docker MCP Plugin
  model*      Docker Model Runner
  network     Manage networks
  plugin      Manage plugins
  sbom*       View the packaged-based Software Bill Of Materials (SBOM) for an image
  scout*      Docker Scout
  system      Manage Docker
  trust       Manage trust on Docker images
  volume      Manage volumes

Swarm Commands:
  swarm       Manage Swarm

Commands:
  attach      Attach local standard input, output, and error streams to a running container
  commit      Create a new image from a container's changes
  cp          Copy files/folders between a container and the local filesystem
  create      Create a new container
  diff        Inspect changes to files or directories on a container's filesystem
  events      Get real time events from the server
  export      Export a container's filesystem as a tar archive
  history     Show the history of an image
  import      Import the contents from a tarball to create a filesystem image
  inspect     Return low-level information on Docker objects
  kill        Kill one or more running containers
  load        Load an image from a tar archive or STDIN
  logs        Fetch the logs of a container
  pause       Pause all processes within one or more containers
  port        List port mappings or a specific mapping for the container
  rename      Rename a container
  restart     Restart one or more containers
  rm          Remove one or more containers
  rmi         Remove one or more images
  save        Save one or more images to a tar archive (streamed to STDOUT by default)
  start       Start one or more stopped containers
  stats       Display a live stream of container(s) resource usage statistics
  stop        Stop one or more running containers
  tag         Create a tag TARGET_IMAGE that refers to SOURCE_IMAGE
  top         Display the running processes of a container
  unpause     Unpause all processes within one or more containers
  update      Update configuration of one or more containers
  wait        Block until one or more containers stop, then print their exit codes

Global Options:
      --config string      Location of client config files (default
                           "C:\\Users\\Hicha\\.docker")
  -c, --context string     Name of the context to use to connect to the
                           daemon (overrides DOCKER_HOST env var and
                           default context set with "docker context use")
  -D, --debug              Enable debug mode
  -H, --host string        Daemon socket to connect to
  -l, --log-level string   Set the logging level ("debug", "info",
                           "warn", "error", "fatal") (default "info")
      --tls                Use TLS; implied by --tlsverify
      --tlscacert string   Trust certs signed only by this CA (default
                           "C:\\Users\\Hicha\\.docker\\ca.pem")
      --tlscert string     Path to TLS certificate file (default
                           "C:\\Users\\Hicha\\.docker\\cert.pem")
      --tlskey string      Path to TLS key file (default
                           "C:\\Users\\Hicha\\.docker\\key.pem")
      --tlsverify          Use TLS and verify the remote
  -v, --version            Print version information and quit

Run 'docker COMMAND --help' for more information on a command.

For more help on how to use Docker, head to https://docs.docker.com/go/guides/
PS C:\Users\Hicha\Desktop\dev\cours-docker\docker-tp-volumes\exercice-1-logger> docker run --name logger1 alpine
docker: Error response from daemon: Conflict. The container name "/logger1" is already in use by container "64c5cee8add07da38c37b64e7c39ae79ea43ea72a0dd4704de2c69ad430a171a". You have to remove (or rename) that container to be able to reuse that name.

Run 'docker run --help' for more information
PS C:\Users\Hicha\Desktop\dev\cours-docker\docker-tp-volumes\exercice-1-logger> docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
PS C:\Users\Hicha\Desktop\dev\cours-docker\docker-tp-volumes\exercice-1-logger> docker stop 64c5cee8add07da38c37b64e7c39ae79ea43ea72a0dd4704de2c69ad430a171a
64c5cee8add07da38c37b64e7c39ae79ea43ea72a0dd4704de2c69ad430a171a
PS C:\Users\Hicha\Desktop\dev\cours-docker\docker-tp-volumes\exercice-1-logger> docker run logger1
Unable to find image 'logger1:latest' locally
docker: Error response from daemon: pull access denied for logger1, repository does not exist or may require 'docker login'

Run 'docker run --help' for more information
PS C:\Users\Hicha\Desktop\dev\cours-docker\docker-tp-volumes\exercice-1-logger> docker start logger1                                                         
logger1
PS C:\Users\Hicha\Desktop\dev\cours-docker\docker-tp-volumes\exercice-1-logger> docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
PS C:\Users\Hicha\Desktop\dev\cours-docker\docker-tp-volumes\exercice-1-logger> docker rm -f logger1
logger1
PS C:\Users\Hicha\Desktop\dev\cours-docker\docker-tp-volumes\exercice-1-logger> docker run --name logger1 -v \ logs_volume:/var/logs \ alpine sh -C "echo 'Log depuis logger1' >> /var/logs/app.log"
docker: invalid reference format

Run 'docker run --help' for more information
PS C:\Users\Hicha\Desktop\dev\cours-docker\docker-tp-volumes\exercice-1-logger> docker run --name logger1 -v logs_volume:/var/logs \
>>   alpine sh -c "echo 'Log depuis logger1' >> /var/logs/app.log"
docker: invalid reference format

Run 'docker run --help' for more information
alpine : Le terme «alpine» n'est pas reconnu comme nom d'applet de commande, fonction, fichier de script ou programme exécutable. Vérifiez l'orthographe du nom, ou si un chemin 
d'accès existe, vérifiez que le chemin d'accès est correct et réessayez.
Au caractère Ligne:2 : 3
+   alpine sh -c "echo 'Log depuis logger1' >> /var/logs/app.log"
+   ~~~~~~
    + CategoryInfo          : ObjectNotFound: (alpine:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException

PS C:\Users\Hicha\Desktop\dev\cours-docker\docker-tp-volumes\exercice-1-logger> docker run --name logger1 -v logs_volume:/var/logs  
>>   alpine sh -c "echo 'Log depuis logger1' >> /var/logs/app.log"
docker: 'docker run' requires at least 1 argument

Usage:  docker run [OPTIONS] IMAGE [COMMAND] [ARG...]

See 'docker run --help' for more information
alpine : Le terme «alpine» n'est pas reconnu comme nom d'applet de commande, fonction, fichier de script ou programme exécutable. Vérifiez l'orthographe du nom, ou si un chemin 
d'accès existe, vérifiez que le chemin d'accès est correct et réessayez.
Au caractère Ligne:2 : 3
+   alpine sh -c "echo 'Log depuis logger1' >> /var/logs/app.log"
+   ~~~~~~
    + CategoryInfo          : ObjectNotFound: (alpine:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException

PS C:\Users\Hicha\Desktop\dev\cours-docker\docker-tp-volumes\exercice-1-logger> docker run --name logger1 -v logs_volume:/var/logs  
>>   alpine sh -c "echo 'Log depuis logger1' >> /var/logs/app.log"
docker: 'docker run' requires at least 1 argument

Usage:  docker run [OPTIONS] IMAGE [COMMAND] [ARG...]

See 'docker run --help' for more information
alpine : Le terme «alpine» n'est pas reconnu comme nom d'applet de commande, fonction, fichier de script ou programme exécutable. Vérifiez l'orthographe du nom, ou si un chemin 
d'accès existe, vérifiez que le chemin d'accès est correct et réessayez.
Au caractère Ligne:2 : 3
+   alpine sh -c "echo 'Log depuis logger1' >> /var/logs/app.log"
+   ~~~~~~
    + CategoryInfo          : ObjectNotFound: (alpine:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException

PS C:\Users\Hicha\Desktop\dev\cours-docker\docker-tp-volumes\exercice-1-logger> docker run --name logger1 -v logs_volume:/var/logs alpine sh -c "echo 'Log depuis logger1' >> /var/logs/app.log"
PS C:\Users\Hicha\Desktop\dev\cours-docker\docker-tp-volumes\exercice-1-logger> docker run --name logger2 -v logs_volume:/var/logs alpine sh -c "echo 'Log depuis logger2' >> /var/logs/app.log"
PS C:\Users\Hicha\Desktop\dev\cours-docker\docker-tp-volumes\exercice-1-logger> docker run --rm -v logs_volume:/var/logs alpine cat /var/logs/app.log
>>
Log depuis logger1
Log depuis logger2
PS C:\Users\Hicha\Desktop\dev\cours-docker\docker-tp-volumes\exercice-1-logger> docker rm -f logger1 logger2
logger1
logger2
PS C:\Users\Hicha\Desktop\dev\cours-docker\docker-tp-volumes\exercice-1-logger> docker run --rm -v logs_volume:/var/logs alpine cat /var/logs/app.log
>>
Log depuis logger1
Log depuis logger2
PS C:\Users\Hicha\Desktop\dev\cours-docker\docker-tp-volumes\exercice-1-logger> docker volume rm logs_volume
>>
logs_volume
PS C:\Users\Hicha\Desktop\dev\cours-docker\docker-tp-volumes\exercice-1-logger> 