# ecs-local-test

参考：https://dev.classmethod.jp/cloud/aws/ecs-local/

## インストール

```
$ sudo curl -o /usr/local/bin/ecs-cli https://amazon-ecs-cli.s3.amazonaws.com/ecs-cli-darwin-amd64-latest
```

```
$ sudo chmod +x /usr/local/bin/ecs-cli
```

```
$ ecs-cli --version
```

## タスク定義JSONから、Docker Composeファイルの生成

```
$ ecs-cli local create --task-def-file ecs-local-wordpress.json --output docker-compose.wp-mysql.yml
```

そうするとdocker-composeファイルが生成される。  
以下で起動。

```
$ ecs-cli local up --task-def-compose docker-compose.wp-mysql.yml
```

http://localhost:8080

```
$ ecs-cli local ps -f ecs-local-wordpress.json 
```

```
$ docker ps
```

```
$ ecs-cli local down --all
```