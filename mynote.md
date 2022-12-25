## 运行步骤

1. clone

2. 切换到目录下

3. （可选）  [dst_master exited with code 6 ](https://github.com/mathielo/dst-dedicated-server/issues/19#top)  #19

   ```
   docker-compose up -d && docker exec -u root -it dst_master bash -c "chown -Rv dst:dst /home/dst/.klei/DoNotStarveTogether"

4. `docker-compose up` 可选`-d`

## 关服步骤

### Saving and shutting down

To **save the game** right before shutdown, attach to the container and execute `c_shutdown()`:

```
docker attach dst_master --sig-proxy=false
c_shutdown()
```

The Master shard will manage to save the game and send a shutdown signal to the Caves shard as well.

### Alternative: shutdown without saving

If you simply want to shutdown the containers without saving the game:

```
docker-compose down
```

> 🛑 Caution! Stopping the containers **DOES NOT SAVE THE GAME**, it simply gracefully shutdown the server processes and kills the containers.