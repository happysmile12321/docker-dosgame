支持斐讯N1、我家云(arm64架构)

实例

```
docker run -d \
  --name dosgame \
  --restart=always \
  -p 6000:6000 \
  -v /docker/dosgame:/app/static/games/ \
  lstcml/n1_dosgame
```

注：打包的镜像中只有42种游戏（目前共1898种游戏，共31.9G，所以悠着点，需要更多游戏的时候记得创建容器的时候把/app/static/games/挂载到移动硬盘后再去下载，否则后果不堪设想）

下载更多游戏方法：

```
docker exec -it dosgame sh
进入容器后操作
mv /app/static/games/games.json /app/static/games/42games.json
mv /app/static/games/1898all_games.json /app/static/games/games.json
python /app/static/games/download_data.py
等待下载完后重启容器即可
docker restart dosgame
```
