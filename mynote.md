## [Console/Don't Starve Together Commands](https://dontstarve.fandom.com/wiki/Console/Don%27t_Starve_Together_Commands#Network/Server_Commands)

## 运行步骤

1. clone or pull

2. 切换到目录下

3. （可选）`sudo service docker start`

4. （可选）获取sudo权限

   ```bash
   sudo groupadd docker
   sudo usermod -aG docker $USER
   newgrp docker
   docker run hello-world
   ```

5. （可选）  [dst_master exited with code 6 ](https://github.com/mathielo/dst-dedicated-server/issues/19#top)  #19

  ```
  docker-compose up -d && docker exec -u root -it dst_master bash -c "chown -Rv dst:dst /home/dst/.klei/DoNotStarveTogether"
  ```

6. `docker-compose up` 可选`docker-compose up -d`

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
