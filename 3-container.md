# Contenedores

### Crear un contenedor
Para crear un nuevo contenedor Docker a partir de una imagen específica, pero sin iniciarlo automáticamente. 

```
docker create --name <nombre contenedor> <nombre imagen>:<tag>
```
Crear el contenedor  **srv-web** usando la imagen nginx version alpine

# COMPLETAR
```
PS C:\Users\PC> docker create --name srv-web nginx:alpine
67b43487cf358315ca2d0f1c14f12bb412df2cf47f33008b6392812e6f109470
```
Si creas un contenedor en Docker sin asignarle un nombre específico utilizando la opción --name, Docker asignará automáticamente un nombre aleatorio al contenedor. Este nombre suele consistir en una combinación de palabras y números.  

Crear el contenedor usando la imagen hello-world
# COMPLETAR

```
PS C:\Users\PC> docker create hello-world
ee509bb4c58666a7af7a52a2caa3bcf6c9d0be60c2321916e2094ad68f66aac3
```

### Listar los contenedores ejecutándose o no

```
docker ps -a
```

### Para iniciar un contenedor

```
docker start <nombre contenedor o identificador>
```
Iniciar el contenedor srv-web 
# COMPLETAR

```
PS C:\Users\PC> docker start srv-web
srv-web
```
### Listar los contenedores ejecutándose
```
docker ps 
docker ps | grep <nombre contenedor>
```

### Para detener un contenedor

```
docker stop <nombre contenedor>
```

### Para crear un contenedor y ejecutarlo inmediatamente

```
docker run --name <nombre contenedor> <nombre imagen>:<tag>
```
![Ecosistema de Docker](img/dockerRun.PNG)

Crear y ejecutar inmediatamente el contenedor **srv-web2** usando la imagen nginx:alpine
# COMPLETAR
```
docker run --name srv-web2 nginx:alpine
/docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
/docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
/docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh   
10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
10-listen-on-ipv6-by-default.sh: info: Enabled listen on IPv6 in /etc/nginx/conf.d/default.conf
/docker-entrypoint.sh: Sourcing /docker-entrypoint.d/15-local-resolvers.envsh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh       
/docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh       
/docker-entrypoint.sh: Configuration complete; ready for start up
2024/10/09 23:53:23 [notice] 1#1: using the "epoll" event method
2024/10/09 23:53:23 [notice] 1#1: nginx/1.27.2
2024/10/09 23:53:23 [notice] 1#1: built by gcc 13.2.1 20240309 (Alpine 13.2.1_git20240309)
2024/10/09 23:53:23 [notice] 1#1: OS: Linux 5.15.153.1-microsoft-standard-WSL2
2024/10/09 23:53:23 [notice] 1#1: getrlimit(RLIMIT_NOFILE): 1048576:1048576
2024/10/09 23:53:23 [notice] 1#1: start worker processes
2024/10/09 23:53:23 [notice] 1#1: start worker process 30
2024/10/09 23:53:23 [notice] 1#1: start worker process 31
2024/10/09 23:53:23 [notice] 1#1: start worker process 32
2024/10/09 23:53:23 [notice] 1#1: start worker process 33
2024/10/09 23:53:23 [notice] 1#1: start worker process 34
2024/10/09 23:53:23 [notice] 1#1: start worker process 35
2024/10/09 23:53:23 [notice] 1#1: start worker process 36
2024/10/09 23:53:23 [notice] 1#1: start worker process 37
2024/10/09 23:53:23 [notice] 1#1: start worker process 38
2024/10/09 23:53:23 [notice] 1#1: start worker process 39
2024/10/09 23:53:23 [notice] 1#1: start worker process 40
2024/10/09 23:53:23 [notice] 1#1: start worker process 41
2024/10/09 23:53:23 [notice] 1#1: start worker process 42
2024/10/09 23:53:23 [notice] 1#1: start worker process 43
2024/10/09 23:53:23 [notice] 1#1: start worker process 44
2024/10/09 23:53:23 [notice] 1#1: start worker process 45
```
**¿Qué sucede luego de la ejecución del comando?**
```
Empieza a ejecutarse y salir lineas de comando que dicen start work process y no se permite ingresar mas comandos dentro de la terminal
```
# COMPLETAR  

Cuando ejecutas un contenedor en primer plano sin la opción -d (modo detach), el contenedor captura la entrada estándar (stdin) del terminal, lo que significa que el terminal queda "atrapado" y no puedes introducir más comandos hasta que detengas el contenedor.

### Para crear un contenedor y ejecutarlo inmediatamente sin estar vinculados al mismo
-d: Es la opción que indica a Docker que ejecute el contenedor en segundo plano (en modo "detach").
Cuando un contenedor se ejecuta en segundo plano, Docker devuelve el control al terminal inmediatamente después de iniciar el contenedor, lo que permite al usuario seguir ejecutando otros comandos en el mismo terminal sin que el contenedor detenga la interacción.

```
docker run -d --name <nombre contenedor> <nombre imagen>:tag
```
Crear y ejecutar inmediatamente el contenedor **srv-web3** en modo detach usando la imagen nginx:alpine
# COMPLETAR
```
docker run -d --name srv-web3 nginx:alpine
c23162adcfd0cca09636cf49c0028ba4b1b13a645af3d5e6c682ac33a15ab1d7
```

### Para eliminar un contenedor

```
docker rm <nombre contenedor>
```
Eliminar el contenedor que se creó a partir de la imagen hello-world 
# COMPLETAR
```
Primero verificamos el id del docker que tiene hello-world
docker ps -a
CONTAINER ID   IMAGE          COMMAND                  CREATED          STATUS                      PORTS     NAMES   
c23162adcfd0   nginx:alpine   "/docker-entrypoint.…"   6 minutes ago    Up 6 minutes                80/tcp    srv-web3
471968b9c638   nginx:alpine   "/docker-entrypoint.…"   15 minutes ago   Exited (0) 13 minutes ago             srv-web2
67b43487cf35   nginx:alpine   "/docker-entrypoint.…"   2 hours ago      Exited (0) 2 minutes ago              srv-web 
5d35cc156753   hello-world    "/hello"                 17 hours ago     Exited (0) 17 hours ago               focused_elgamal

en este caso tiene el codigo 5d35cc156753
eliminamos dicho contenedor
docker rm -f 5d35cc156753
5d35cc156753
```
Verificar que el contenedor que se eliminó
# COMPLETAR
```
PS C:\Users\PC> docker ps -a
CONTAINER ID   IMAGE          COMMAND                  CREATED          STATUS                      PORTS     NAMES   
c23162adcfd0   nginx:alpine   "/docker-entrypoint.…"   10 minutes ago   Up 10 minutes               80/tcp    srv-web3
471968b9c638   nginx:alpine   "/docker-entrypoint.…"   20 minutes ago   Exited (0) 17 minutes ago             srv-web2
67b43487cf35   nginx:alpine   "/docker-entrypoint.…"   2 hours ago      Exited (0) 6 minutes ago              srv-web 
//ya no existe el contenedor con hello-world
```

### Para eliminar un contenedor que esté ejecutándose

```
docker rm -f <nombre contenedor>
```
Eliminar el contenedor **srv-web3** 
# COMPLETAR
```
PS C:\Users\PC> docker rm -f srv-web3
srv-web3
```
Verificar que el contenedor que se eliminó
# COMPLETAR
```
PS C:\Users\PC> docker ps -a
CONTAINER ID   IMAGE          COMMAND                  CREATED          STATUS                      PORTS     NAMES   
471968b9c638   nginx:alpine   "/docker-entrypoint.…"   22 minutes ago   Exited (0) 20 minutes ago             srv-web2
67b43487cf35   nginx:alpine   "/docker-entrypoint.…"   2 hours ago      Exited (0) 9 minutes ago              srv-web 
PS C:\Users\PC>

#ya no existe el contenedor srv-web3
```

### Para inspecionar un contenedor 

Inspeccionar el contenedor **srv-web** 
# COMPLETAR
```
PS C:\Users\PC> docker inspect srv-web
>>
[
    {
        "Id": "67b43487cf358315ca2d0f1c14f12bb412df2cf47f33008b6392812e6f109470",
        "Created": "2024-10-09T22:34:34.533029003Z",       
        "Path": "/docker-entrypoint.sh",
        "Args": [
            "nginx",
            "-g",
            "daemon off;"
        ],
        "State": {
            "Status": "exited",
            "Running": false,
            "Paused": false,
            "Restarting": false,
            "OOMKilled": false,
            "Dead": false,
            "Pid": 0,
            "ExitCode": 0,
            "Error": "",
            "StartedAt": "2024-10-09T22:56:41.400572272Z", 
            "FinishedAt": "2024-10-10T00:06:38.121497048Z" 
        },
        "Image": "sha256:2140dad235c130ac861018a4e13a6bc8aea3a35f3a40e20c1b060d51a7efd250",
        "ResolvConfPath": "/var/lib/docker/containers/67b43487cf358315ca2d0f1c14f12bb412df2cf47f33008b6392812e6f109470/resolv.conf",
        "HostnamePath": "/var/lib/docker/containers/67b43487cf358315ca2d0f1c14f12bb412df2cf47f33008b6392812e6f109470/hostname",
        "HostsPath": "/var/lib/docker/containers/67b43487cf358315ca2d0f1c14f12bb412df2cf47f33008b6392812e6f109470/hosts",
        "LogPath": "/var/lib/docker/containers/67b43487cf358315ca2d0f1c14f12bb412df2cf47f33008b6392812e6f109470/67b43487cf358315ca2d0f1c14f12bb412df2cf47f33008b6392812e6f109470-json.log",
        "Name": "/srv-web",
        "RestartCount": 0,
        "Driver": "overlayfs",
        "Platform": "linux",
        "MountLabel": "",
        "ProcessLabel": "",
        "AppArmorProfile": "",
        "ExecIDs": null,
        "HostConfig": {
            "Binds": null,
            "ContainerIDFile": "",
            "LogConfig": {
                "Type": "json-file",
                "Config": {}
            },
            "NetworkMode": "bridge",
            "PortBindings": {},
            "RestartPolicy": {
                "Name": "no",
                "MaximumRetryCount": 0
            },
            "AutoRemove": false,
            "VolumeDriver": "",
            "VolumesFrom": null,
            "ConsoleSize": [
                30,
                120
            ],
            "CapAdd": null,
            "CapDrop": null,
            "CgroupnsMode": "host",
            "Dns": [],
            "DnsOptions": [],
            "DnsSearch": [],
            "ExtraHosts": null,
            "GroupAdd": null,
            "IpcMode": "private",
            "Cgroup": "",
            "Links": null,
            "OomScoreAdj": 0,
            "PidMode": "",
            "Privileged": false,
            "PublishAllPorts": false,
            "ReadonlyRootfs": false,
            "SecurityOpt": null,
            "UTSMode": "",
            "UsernsMode": "",
            "ShmSize": 67108864,
            "Runtime": "runc",
            "Isolation": "",
            "CpuShares": 0,
            "Memory": 0,
            "NanoCpus": 0,
            "CgroupParent": "",
            "BlkioWeight": 0,
            "BlkioWeightDevice": [],
            "BlkioDeviceReadBps": [],
            "BlkioDeviceWriteBps": [],
            "BlkioDeviceReadIOps": [],
            "BlkioDeviceWriteIOps": [],
            "CpuPeriod": 0,
            "CpuQuota": 0,
            "CpuRealtimePeriod": 0,
            "CpuRealtimeRuntime": 0,
            "CpusetCpus": "",
            "CpusetMems": "",
            "Devices": [],
            "DeviceCgroupRules": null,
            "DeviceRequests": null,
            "MemoryReservation": 0,
            "MemorySwap": 0,
            "MemorySwappiness": null,
            "OomKillDisable": false,
            "PidsLimit": null,
            "Ulimits": [],
            "CpuCount": 0,
            "CpuPercent": 0,
            "IOMaximumIOps": 0,
            "IOMaximumBandwidth": 0,
            "MaskedPaths": [
                "/proc/asound",
                "/proc/acpi",
                "/proc/kcore",
                "/proc/keys",
                "/proc/latency_stats",
                "/proc/timer_list",
                "/proc/timer_stats",
                "/proc/sched_debug",
                "/proc/scsi",
                "/sys/firmware",
                "/sys/devices/virtual/powercap"
            ],
            "ReadonlyPaths": [
                "/proc/bus",
                "/proc/fs",
                "/proc/irq",
                "/proc/sys",
                "/proc/sysrq-trigger"
            ]
        },
        "GraphDriver": {
            "Data": null,
            "Name": "overlayfs"
        },
        "Mounts": [],
        "Config": {
            "Hostname": "67b43487cf35",
            "Domainname": "",
            "User": "",
            "AttachStdin": false,
            "AttachStdout": true,
            "AttachStderr": true,
            "ExposedPorts": {
                "80/tcp": {}
            },
            "Tty": false,
            "OpenStdin": false,
            "StdinOnce": false,
            "Env": [
                "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin",
                "NGINX_VERSION=1.27.2",
                "PKG_RELEASE=1",
                "DYNPKG_RELEASE=1",
                "NJS_VERSION=0.8.6",
                "NJS_RELEASE=1"
            ],
            "Cmd": [
                "nginx",
                "-g",
                "daemon off;"
            ],
            "Image": "nginx:alpine",
            "Volumes": null,
            "WorkingDir": "",
            "Entrypoint": [
                "/docker-entrypoint.sh"
            ],
            "OnBuild": null,
            "Labels": {
                "maintainer": "NGINX Docker Maintainers \u003cdocker-maint@nginx.com\u003e"
            },
            "StopSignal": "SIGQUIT"
        },
        "NetworkSettings": {
            "Bridge": "",
            "SandboxID": "",
            "SandboxKey": "",
            "Ports": {},
            "HairpinMode": false,
            "LinkLocalIPv6Address": "",
            "LinkLocalIPv6PrefixLen": 0,
            "SecondaryIPAddresses": null,
            "SecondaryIPv6Addresses": null,
            "EndpointID": "",
            "Gateway": "",
            "GlobalIPv6Address": "",
            "GlobalIPv6PrefixLen": 0,
            "IPAddress": "",
            "IPPrefixLen": 0,
            "IPv6Gateway": "",
            "MacAddress": "",
            "Networks": {
                "bridge": {
                    "IPAMConfig": null,
                    "Links": null,
                    "Aliases": null,
                    "MacAddress": "",
                    "DriverOpts": null,
                    "NetworkID": "c34b157f95d5c823b51ecd34d8e6bc42cac793605a21ad49d1c2a63b441ded4a",
                    "EndpointID": "",
                    "Gateway": "",
                    "IPAddress": "",
                    "IPPrefixLen": 0,
                    "IPv6Gateway": "",
                    "GlobalIPv6Address": "",
                    "GlobalIPv6PrefixLen": 0,
                    "DNSNames": null
                }
            }
        }
    }
]

```
