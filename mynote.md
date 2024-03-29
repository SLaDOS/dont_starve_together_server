## [Console/Don't Starve Together Commands](https://dontstarve.fandom.com/wiki/Console/Don%27t_Starve_Together_Commands#Network/Server_Commands)

## [Creating_the_Map](https://dontstarve.fandom.com/wiki/Guides/Don%E2%80%99t_Starve_Together_Dedicated_Servers#Creating_the_Map)

## 运行步骤

-  clone or pull

-  切换到目录下

-  （可选）`sudo chmod -R 777 *`

-  （可选）`sudo service docker start`

-  （可选）获取sudo权限

   ```bash
   sudo groupadd docker
   sudo usermod -aG docker $USER
   newgrp docker
   docker run hello-world
   ```

-  （可选）  [dst_master exited with code 6 ](https://github.com/mathielo/dst-dedicated-server/issues/19#top)  #19

  ```
  docker-compose up [-d] && docker exec -u root -it dst_master bash -c "chown -Rv dst:dst /home/dst/.klei/DoNotStarveTogether && chown -Rv dst:dst /home/dst/server_dst/mods"
  ```

- `docker-compose up` 可选`docker-compose up -d`

   ☝️ You can follow logs when running in detached mode: docker-compose logs -f

## 关服步骤

### Saving and shutting down

To **save the game** right before shutdown, attach to the container and execute `c_shutdown()`:

```
docker attach dst_master
c_shutdown()
```

The Master shard will manage to save the game and send a shutdown signal to the Caves shard as well.

### Alternative: shutdown without saving

If you simply want to shutdown the containers without saving the game:

```
docker-compose down
```

> 🛑 Caution! Stopping the containers **DOES NOT SAVE THE GAME**, it simply gracefully shutdown the server processes and kills the containers.

## mod

每次pull完，要

sudo chmod -R 777 *

否则没权限读取mod列表

## 备忘录

sudo chmod -R 777 *

eval $(ssh-agent -s)

ssh-add ~/.ssh/id_ed25519
