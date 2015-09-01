
![Quake 2](https://raw.githubusercontent.com/InAnimaTe/docker-quake2/master/Quake2_logo.png)

### Quake 2 Dedicated Server Image

A fancy containerized [quake2](https://en.wikipedia.org/wiki/Quake_II) dedicated server container. Get playing in no time!

Ideally, you would setup the config how you want, build, launch, and play. I originally sourced from *[drags](https://github.com/drags/docker-quake2)* release That image now doesn't build and so I've tagged and moved on creating my own debian based [yquake](https://github.com/yquake2/yquake2) engine image.

I want to thank the Debian Games Team for [this](https://packages.debian.org/stable/games/quake2-server) excellent package :)

#### Launching

##### The `server.cfg` way

There is an included `docker-compose.yml.example` that shows the best way to launch this container and how to take care of the core dependencies: the retail `pak0.pak`, the port forward for `27910/udp`, and optionally, your own `server.cfg`.

> Note that the server.cfg must exist in the `/usr/share/games/quake2/baseq2` directory!

If you decide to build and incorporate your own `server.cfg`, as is recommended, make sure you modify the `image` source or just use `build: .` in your `docker-compose.yml` :)

You could also just `-v ./server.cfg:/use/share/games/quake2/baseq2/server.cfg` on the command line.

##### The command way

You can also pass in configuration options via passing them as docker commands either on the command line or in your `docker-compose.yml`. 

```
docker run -d -v ./pak0.pak:/usr/share/games/quake2/baseq2/pak0.pak inanimate/quake2 +fraglimit 150
```

#### Maps

I've set a default launch map of q2dm1, which is *The Edge*, one of the more popular deathmatch maps. **This means you can just run the container straight off with no options and be playing instantly.**

A great map breakdown can be seen [here](http://quake.wikia.com/wiki/Quake_II#Multiplayer_Maps).

#### Troubleshooting

```
docker logs quake2
```

Yep, the server logs to stdout/stderr!

