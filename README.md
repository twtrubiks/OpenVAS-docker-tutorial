# OpenVAS

OpenVAS 是一個用於漏洞掃描的開源框架,

(這邊先簡單紀錄一下, 有空再來更新)

官方文件可參考

[Greenbone Community Containers 22.4](https://greenbone.github.io/docs/latest/22.4/container/index.html)

這邊我們使用 docker,

先把官方的 docker-compose 抓下來,

```cmd
curl -f -L https://greenbone.github.io/docs/latest/_static/docker-compose-22.4.yml -o docker-compose.yml
```

pull

```cmd
docker-compose -p greenbone-community-edition pull
```

這邊說一下 `-p` , 其實只是代表 project name, 如果你不指定,

預設都是用資料夾命名.

執行

```cmd
docker-compose -p greenbone-community-edition up -d
```

瀏覽 [http://localhost:9392/login](http://localhost:9392/login)

就可以看到以下畫面

預設的帳號密碼是 admin / admin

![alt tag](https://i.imgur.com/yMn8WOM.png)

之後建議先確認 Feed Status

![alt tag](https://i.imgur.com/6GFW5JX.png)

![alt tag](https://i.imgur.com/iE6YlD8.png)

如果這邊有像這樣 Update in progress...

就是代表在更新中, 他更新真的蠻久的😪

建議可以直接查看 log 看更新狀態😁

這邊我是查看 greenbone/gvmd:stable 這個容器,

可以發現他在更新

![alt tag](https://i.imgur.com/Uvt24kr.png)

如果全部更新完了, 會全都顯示 Current

![alt tag](https://i.imgur.com/61jJeXk.png)

原因是如果沒有全部顯示 Current, 你會發現你無法建立 Tasks.

(當初我在這邊卡了超級久😭)

## 教學

建立 Target

![alt tag](https://i.imgur.com/hb5KLUD.png)

host 這邊可以填 ip 也可以填你的 domain

![alt tag](https://i.imgur.com/9tLgu8n.png)

接著建立你的 Tasks

![alt tag](https://i.imgur.com/GfpsiYL.png)

這邊選擇剛剛建立的 Target

![alt tag](https://i.imgur.com/PbOupYw.png)

點選這邊就會開始執行, 執行時間也是一個漫長的等待😪

![alt tag](https://i.imgur.com/WnWvfe3.png)

這邊可以看結果, 可以匯出 PDF 😀

會和你說你的 server 哪裡有什麼安全性問題😐

![alt tag](https://i.imgur.com/kTzc40w.png)

如果你想要更新, 像是 Feed Synchronization,

可參考 [https://greenbone.github.io/docs/latest/22.4/container/workflows.html](https://greenbone.github.io/docs/latest/22.4/container/workflows.html)

