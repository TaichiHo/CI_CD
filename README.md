# [Continuous Integration](https://www.thoughtworks.com/continuous-integration)


 ---------

## Concept

Continuous Integration (CI) is a development practice that requires developers to integrate code into a shared repository several times a day. Each check-in is then verified by an automated build, allowing teams to detect problems early.

CIとは一つの開発プロセスで、開発者が毎日何回もコミットして、レポジトリが自動的にビルドし、テストを行う。バグの早期発見につなぎます。

> Continuous Integration doesn't get rid of bugs, but it does make them dramatically easier to find and remove.
CIはバグをなくすことはできないが、バグを発見し、排除することを簡単化することはできる。
\- Martin Fowler
 


### Practice

- Maintain a single source repository　一つのレポジトリにする

-  Automate the build　自動化ビルド

- Make your build self-testing　ビルドとテストの連携

- Every commit should build on an integration machine　ビルドはプロダクション環境で行う

- Keep the build fast　もっと速いビルドを追求する

- Test in a clone of the production environment　テストもプロダクション環境で行う

- Make it easy for anyone to get the latest executable　最後に作成するデプロイファイルを誰もが手に入れやすくする

- Everyone can see what's happening　何があったのかを誰もが一目でわかるようにする

- Automate deployment　自動的にデプロイ



### How to do it?　手順

- Developers check out code into their private workspaces　自分のマシンにコードをチェックアウト

- When done, commit the changes to the repository　コードを書き終えたら、リポジトリにコミットする

- The CI server monitors the repository and checks out changes when they occur　CIサーバーががリポジトリをモニタリングし、変更を探知する

- The CI server builds the system and runs unit and integration tests　CIサーバーがシステムをビルドし、unit testとintegration testを行う

- The CI server releases deployable artifacts for testing　CIサーバーがデプロイ可能なファイルを作成する

- The CI server assigns a build label to the version of the code it just built　CIサーバーがビルドしたバージョンにラベルをつける

- The CI server informs the team of the successful build　CIサーバーがチームにビルドが成功したと報告する

- If the build or tests fail, the CI server alerts the team.　失敗したら、CIサーバーがチームに警告する

- The team fix the issue at the earliest opportunity　チームがバグを修正する

- Continue to continually integrate and test throughout the project　以上のプロセスを継続的に行う



### Team Responsibilities

- Check in Frequently　頻繁的にチェックインする

- Don't check in broken code　壊れたコードベースをチェックしない

- Don't check in untested code　テストしていないコードをチェックインしない

- Don't check in when the build is broken　ビルドが壊れた場合はチェックインしない

- Don't go home after checking in until the system builds　システムのビルドが成功するまで家に帰らない



# Continous Deployment && Continuous Delivery

-------------

## Concept

> Continuous deployment is the practice of releasing every good build to users - a more accurate name might have been "continuous release".
> Continuous Deploymentとは、ビルドが成功するたびに、ユーザーに届けること。Continuous Releaseといった方が正確です。

>\- Jez Humble, author of Continous Delivery



## Confusion 
Continuous delivery is sometimes confused with continuous deployment. Continuous deployment means that every change is automatically deployed to production. Continuous delivery means that the team ensures every change can be deployed to production but may choose not to do it, usually due to business reasons. In order to do continuous deployment one must be doing continuous delivery.
Continuous DeliveryはContinuous Deploymentと違って、直接にデプロイして、ユーザーに届くのではなく、いつでもデプロイできるような状態にすることです。いつデプロイするのかはビズネス関連の知見も絡んできます。



Continuous Delivery is the natural extension of Continuous Integration: an approach in which teams ensure that every change to the system is releasable, and that we can release any version at the push of a button.
Continuous DeliveryはContinuous Integrationの自然な流れで、システムに対しての変更がいつでもリリース可能な状態にすることです、リリースはボタン一つをクリックだけのことになってしまいます。



# DevOps
----
> Emphasize the colllaborations and communication of both software developers and other IT professionals while automating the process of software delivery and infrastructure changes.
開発者と他のIT業者の協力とコミュニケーションを強調し、ソフトウェアのデリバリーとインフラの変更を自動化する。

> -- wikipedia





![](https://upload.wikimedia.org/wikipedia/commons/b/b5/Devops.svg)




### Relationship with Continous Delivery

Continuous delivery and DevOps are similar.

DevOps has a borader scope, centers around the **cultural change**.

DevOpsはCDと似て、ですがもっとカルチャー的な話です。



# Docker
-------

CI and docker are **made for each other**. 
CIとDockerはお互いのために生まれようなものです。

### Concept
-----
>Docker containers wrap up a piece of software in a complete filesystem that contains everything it needs to run: code, runtime, system tools, system libraries – anything you can install on a server. This guarantees that it will always run the same, regardless of the environment it is running in.
>Docker Containerはいくつのソフトウェアをパッケージして、コードを運行するため全ての環境を用意する。コード、ツール、ライブラリー、サーバーでインストールできることは全部ここでもできます。それによって、どこで運行しても、同じ結果が見込まれる。

### Difference with Virtual machine
![](https://cloud.githubusercontent.com/assets/6963581/14523902/d41ae8e6-0270-11e6-90d0-f21fe57ad016.png)
### With Vagrant?
![](https://cloud.githubusercontent.com/assets/6963581/14523906/d42e971a-0270-11e6-9a9e-aef5bff882c0.png)
More detailed description and comparison can be found at [Ref](http://www.ociweb.com/resources/publications/sett/march-2015-docker-vs-vagrant/)
詳しくは[こちら](http://www.ociweb.com/resources/publications/sett/march-2015-docker-vs-vagrant/)!




# Practical Experiments 実験やってみよう
-----
## Docker
------
We will try out some simple docker command and get familiar with this fantastic tool in this section.

いくつかDockerのコマンドを試してみましょう。

### A simple Dockerfile　簡単なDocker fileの作成 [Ref](http://www.ociweb.com/resources/publications/sett/march-2015-docker-vs-vagrant/)
------
```
# A simple example of Dockerfile to run node.js. Key word are # # # capitalized
# base image (bare OS) ベースのイメージ
FROM ubuntu  
# 開発者署名
MAINTAINER Yong Fu　 
# install necessary packages　必要なパッケージをインストール
RUN apt-get update
RUN apt-get install -y python-software-properties python
RUN add-apt-repository ppa:chris-lea/node.js
RUN echo "deb http://us.archive.ubuntu.com/ubuntu/ precise universe" >> /etc/apt/sources.list
RUN apt-get install -y nodejs
RUN mkdir /var/www
# map a local directory into Docker　ファイルシステムのマッピング
ADD app.js /var/www/app.js
# default application when exec “docker run … “　デフォルト行うスクリプト
CMD ["/usr/bin/node", "/var/www/app.js"]
```
### [Installation on OSX](https://docs.docker.com/engine/installation/mac/)
After installation of the Docker Toolbox, run the  following:
Docker Toolboxをインストールした後、以下の通り：
```
docker-machine create --driver virtualbox default
```
This will create a lightweight Linux VM called default and all the docker will be hosted on it.
簡単なヴァーチャルマシンをセットアップ。Dockerはその上で運行する。
For example, list all the machines and check the environment parameters
docer-machineのコマンドを使って、今の状態がわかる。
```
docker-machine ls
docker-machine env default
```
Run the following to actually connect to the linux environment where we can run docker command.
以下のコマンドでdefaultというバーチャルマシンをactivateする。
```
eval $(docker-machine env default)
```
We can then run the docker commands on this bash shell. 
Run the following to check installation.
以下のコマンドでインストールをチェックしましょう。
```
docker run hello-world
```
It shows the process of basic docker:
こんな感じになるはずです。
```
To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.
```

A more sophisticated example is this:
もうちょっと複雑なものはこちら：
```
$ docker run -d -P --name web nginx
$ docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED              STATUS              PORTS                                           NAMES
fa5b7cdb4cc8        nginx               "nginx -g 'daemon off"   About a minute ago   Up About a minute   0.0.0.0:32769->80/tcp, 0.0.0.0:32768->443/tcp   web

$ docker port web
443/tcp -> 0.0.0.0:32768
80/tcp -> 0.0.0.0:32769
$ docker-machine ip default
192.168.99.100
```
Open http://192.168.99.100:32769/ and we will see the result
それぞれのポートが違うと思うので、各自ブラウザーで試してみましょう。
Finally we stop and remove the docker image.
最後はdocker imageを中止して、削除する。
```
$ docker stop web
$ docker rm web
```

Or we can also try to mount the volumn with the -v flag:
他にも幾つか役に立つコンマンドのオプションがあります。例えば、-vはファイルシステムのマッピングです。
```
$ docker run -d -P -v $HOME/site:/usr/share/nginx/html --name mysite nginx
```

# [Using Travis](https://travis-ci.org/)　Travisを使ってみましょう
----

Travis is mainly for CI. It can also deploy to heroku and S3 automatically. 
TravisはOpen source softwareには無料で使える。幾つかサーバーと連携があるので、簡単にherokuやaws s3にデプロイできる。設定もすごく簡単で、使えやすいです。是非プライベートなリポジトリで使ってみましょう。


![](https://cloud.githubusercontent.com/assets/6963581/14523907/d4420da4-0270-11e6-9d3c-5aa67928b2d9.png)

- Link to your own github account. Check the repositories that you want to have travis support. Go to [https://travis-ci.org/](https://travis-ci.org/) and link your account.
自分のgithubにリンクして、travisを使いたいと思うリポジトリをチェックして、リンクさせる。

![](https://cloud.githubusercontent.com/assets/6963581/14523883/d38c2e3a-0270-11e6-9614-a7058f8320d8.png)



- Create a file called .travis.yml in your repository
リポジトリの中で.travis.ymlというファイルを作る
```

language: node_js
node_js:
- '5'
- '4'
env:
- TEST_DIR=voting-client
- TEST_DIR=voting-server
script: cd $TEST_DIR && npm install && npm test
deploy:
  provider: heroku
  api_key:
    secure: iTKoIzjhPfw7B1aVSkfsN20tzKXQQ198oo9Sa+rIJO7Orqwo4Bz74AGmkQW/VvVwBwzHAxqe5PdrRr+bi8XF+ck/pXwYw/Unxu0B08Vf7TEgCb5jN8Hr1zrS4EjdDJwc6EyGNU0+DNaPxPOoAzCSVjsgA+bHOexRxLxQtJw9VGHqDs2SXOmSabsy9kkV46UEjeP6GMHbmNU8kGC0ktlMlRP6AXbgrZxqCYhIipv/NCGmqU5ey4M0tf/pWUkFVjHfX04V7xQjJ/F+4bb8vrlH/JCvjYGRYjBbYwHA4qHl1lNSZoSb3n8mgIyZXwd79eg9oZ1XLRxqSorEsj0iAXSrQrXKs/3V5qkj42BKdsSSJSCjMLlGclneShxDn6+efxEJfkLEOehvZoQm+KZuqmKy47IZ+lphP9l3y9TjGwBXAxwKv0vLReM2cBDadhLMZ12SY3+k3GyurPEUAh9uxixvrlNIAq3Qta54meiaEDWoaCuAKU+8nzhMMtK1cs3H95XADdOYU1ynGgBaI+s05//18BUCfmD7I8f86qA81pu5Ts89F2TR3Tdmeef0KfrZ2aTrJtbyOP9xESuQrDWk9SNIPq5smZd5ZP1j+ZJUHpHd95kmYvoM1zdLkB/BVPVJkobLrLvoPj/qv9DfWJt85TqKWSgyHxB2LfzRhlqvhcUyG+4=
  app: redux-vote
  on:
    repo: TaichiHo/redux-vote
```

- Push to your the repository to trigger travis
このファイルを追加して、リポジトリにプッシュする

```
git add .travis.yml

git commit -m "add travis support"

git push origin master
```

- Check the tests status in the travis account
ビルドとテストのステータスがtraivisのウェブサイトで確認できる

![](https://cloud.githubusercontent.com/assets/6963581/14523884/d38f2afe-0270-11e6-9974-bccd10150b18.png)



　　Will receive a email when you fail a commit.
　　失敗したら、自動的にメールが来る。

- Fix the bug and push again
バグを直して、もう一度。

![](https://cloud.githubusercontent.com/assets/6963581/14523885/d394e6f6-0270-11e6-8ef7-41dfe0ab872a.png)





- [Deploy](https://docs.travis-ci.com/user/deployment/). Can easily integrate with aws [codedeploy](http://docs.aws.amazon.com/codedeploy/latest/userguide/welcome.html). The guide can be found [here](https://docs.travis-ci.com/user/deployment/codedeploy/). Can easily deploy to the heroku environment as well as shown above.
デプロイ：いくつの大きいサーバー提供者と連携しているので、簡単な設定で自動でデプロイできる。詳しくは[こちら](https://docs.travis-ci.com/user/deployment/)



# TeamCity (By JetBrains)
------

## [Basic CI Workflow in TeamCity](https://confluence.jetbrains.com/display/TCD9/Continuous+Integration+with+TeamCity) 簡単なワークフロー

- The TeamCity server detects a change in your VCS Root and stores it in the database.
 VCSの変更が探知され、変更をデータベースに保存する

- The build trigger sees the change in the database and adds a build to the queue.
 ビルドトリガーが変更に気づき、タスクキューにビルドを追加する

- The server finds an idle compatible build agent and assigns the queued build to this agent.
 ビルドサーバーが暇なエージェントにビルド任務を配布する

- The agent executes the Build Steps. While the build steps are being executed, the build agent reports the build progress to the TeamCity server sending all the log messages, test reports, code coverage results, etc. to the server on the fly, so you can monitor the build process in real time.
 エージェントがビルドを行う。ビルド中のプログレスや、ログ、テストレポートをサーバーに報告する。サーバーのウェブインタフェースでリアルタイムで確認できるようになっている
- After finishing the build, the build agent sends Build Artifacts to the server. 
 ビルドが終わると、エイジェントがビルドの最後に作成したファイルをサーバーに送る



## Core Concept

**Distributed in nature**　分散化の設計

- Build Server　ビルドサーバー
- Build Agent　ビルドエイジェント

自分のマシンに配置できるので、企業向けです。



## Process　簡単な流れ
First install teamcity following the tutorial [here](https://confluence.jetbrains.com/display/TCD9/Installation+Quick+Start).
[ここ](https://confluence.jetbrains.com/display/TCD9/Installation+Quick+Start)で順を追って、ダウンロードして、インストールする
When finished installation, run the server and agent together.
終わったら、ビルドサーバーとエージェントを一緒に起動する。
```
cd TeamCity
./bin/runAll.sh start
```
In case you just want to run the server, type the following
単純にサーバーを起動する場合はこちら
```
./bin/teamcity-server.sh start
```
![](https://cloud.githubusercontent.com/assets/6963581/14523886/d3986ba0-0270-11e6-896b-dfab64524819.png)

Creating the build server. 
少し時間をおいて、諸々設定などを行う。

![](https://cloud.githubusercontent.com/assets/6963581/14523887/d39a55be-0270-11e6-8971-f6bc0abb4931.png)

For test purpose, build server and build agents are in the same machine. But in production, they should sit on different machines.
簡単な試しなので、サーバーとエージェントを一つのマシンで一緒に起動しました。プロダクションの時は、分けたほうがいいでしょう。


General settings. Set the artifact path and the names
Genearl settingsで名前の指定と最後に作成したファイルのパスを指定する

![](https://cloud.githubusercontent.com/assets/6963581/14523898/d3f08236-0270-11e6-9454-a8e00939f384.png)

Add build steps and set running parameters; If using maven, gradle, gulp, etc, it should detect the build steps automatically.
ビルドステップの追加が出来ます。選んだリポジトリによって、自動的にステップが検出される場合もあります。

![](https://cloud.githubusercontent.com/assets/6963581/14523888/d3b9df38-0270-11e6-8285-f4fc04f0c54e.png)

![](https://cloud.githubusercontent.com/assets/6963581/14523891/d3c2906a-0270-11e6-838b-066c96658440.png)



Add the VCS triggers so that the build will automatically get executed
リポジトリから変更が検出された場合、自動的にビルドすることをここで設定。

![](https://cloud.githubusercontent.com/assets/6963581/14523900/d4121c0c-0270-11e6-80ff-3f70d2a9aa39.png)



Dependency settings. Useful in managing multiple projects in the same teamcity server
依頼関係を設定する画面です。もし幾つかの大きいプロジェクトを管理する場合は役に立つでしょう。

![](https://cloud.githubusercontent.com/assets/6963581/14523899/d3fb07ce-0270-11e6-8022-1c51bee41839.png)

Parameter settings
環境変数の設定などここで行う

![](https://cloud.githubusercontent.com/assets/6963581/14523896/d3ebfe5a-0270-11e6-9e9a-bf857551f70a.png)


Check the failure build log 
ビルドが失敗した時のログをこちら

![](https://cloud.githubusercontent.com/assets/6963581/14523889/d3c08446-0270-11e6-9534-0c33cf411ecc.png)

![](https://cloud.githubusercontent.com/assets/6963581/14523895/d3e96870-0270-11e6-9e4d-c239c5d4b0de.png)


Every time a new commit comes in, it triggers a new build.
コミットが来るたびに、新しいビルドが発生する

![](https://cloud.githubusercontent.com/assets/6963581/14523894/d3e5a0c8-0270-11e6-904d-431544135368.png)

Successful build
ビルド成功

![](https://cloud.githubusercontent.com/assets/6963581/14523893/d3c91c8c-0270-11e6-945c-1502f678c04b.png)




# Problem (Try this out!) 課題（やってみよう）
Find a repository with test code. Create one if you want. And then try to create a teamcity server and build agent on different docker container. Try to run your Continuous integration on this setting. 
一つテストコードが付いているリポジトリを探しましよう。他の人のリポジトリも大丈夫です、自分が持っていれば一番、後でコミットとプッシュも試せます。Dockerを活用し、Teamcityのbuild serverとbuild clientを二つの違うDocker containerで起動しましょう。起動できたら、さっきのレポジトリのビルドに使ってみてください。
Feel free to use any prepared docker image you can find on the internet.
ネットで見つかるDocker imageを自由に使って構いません。

- Step 1: Install Docker toolbox
 Docker toolboxをインストールする
- Step 2: Find a docker image that contains the teamcity server or create your own image. Run it and make sure you can enter the web interface. Pay attention to the port settings.
 Teamcityサーバーを含めたDocker Imageを探し、または自分で作り、起動してみましょう。さっきのウェブインタフェースが見ることができるはずです。ポートの設定とかに気をつけてください
- Step 3:  Find a docker image that contains the teamcity agent or create your own image. Run it. Think about how you can point to the teamcity server.
 Teamcityエージェントを含めたDocker Imageを探し、または自分で作り、起動してみよう。どうすればサーバーに接続できるのか考えてみよう。
- Step 4:  You should be able to see the agent from the web interface of the teamcity server. Authorize the agent. 
 サーバーのウェブインタフェースでエージェントを見つかり、オーソライズして、接続完了。
- Step 5: Play with the settings, and do the build and test on your own.
 ビルド設定を諸々行って、実際にテストする。

## [Answer](http://ariya.ofilabs.com/2015/03/continuous-integration-for-node-js-projects-with-teamcity.html)
-----
### Using Docker together with teamcity　TeamcityとDockerの連携

I use teamcity to do the continuous integration with one of my own github [node project](https://github.com/TaichiHo/redux-vote).
今回は、teamcityとdockerを使って、ある自分のgithub[プロジェクト](https://github.com/TaichiHo/redux-vote)をCI化しました。

There are plenty of teamcity docker image out there on the internet. I chose this [one](https://hub.docker.com/r/ariya/centos7-teamcity-server/)
ネットではたくさんdocker imageが溢れています、今回は、teamcityとの連携ということで、[このdocker image](https://hub.docker.com/r/ariya/centos7-teamcity-server/)を使用しました。

If you haven't already, run the following command to activate the default vm where docker will be running on.
まだdocker-machineを起動していない場合は、まず起動してください。
```
$ docker-machine ls
$ docker-machine env default
$ eval $(docker-machine env default)
```
Run the teamcity server.
あとはteamcity serverを起動する。



```　
$ docker run -dt --name teamcity_server -p 8111:8111 ariya/centos7-teamcity-server
```
Open http://192.168.99.100:8111 to see the WEB UI of teamcity server
ブラウザーでサーバーの動作を確認する。私のip addressはhttp://192.168.99.100:8111ですが、各自のマシンでは違う可能性があるので、ご確認ください。

To connect server and agent, we need to know the network address of the server so that agent can reference it. By default, the containers in the same machine will be added to the bridge network by default. This is a subnet in the same machine. The containers can talk to each other by referencing the other's ip address. Check out the reference [here](https://docs.docker.com/engine/userguide/networking/dockernetworks/).
エージェントとサーバーを繋ぐには、サーバのIPアドレスを知ることが必要です。デフォルトでは、サーバーと同じマシンにいるので、Container同士でBridgeというサブネットワークを通じて通信ができる。詳しくは[こちら](https://docs.docker.com/engine/userguide/networking/dockernetworks/)。

We can check the network status easily running the following. The network address of all the containers will be shown here.
ネットワークのパラメータ諸々はこのコマンドを使えばわかる。
```
$ docker network inspect bridge
[
    {
        "Name": "bridge",
        "Id": "231027a95e3bb77de8ea6261448b6eeb07f6674cad24d3e492a7db50a8e1158e",
        "Scope": "local",
        "Driver": "bridge",
        "IPAM": {
            "Driver": "default",
            "Options": null,
            "Config": [
                {
                    "Subnet": "172.17.0.0/16"
                }
            ]
        },
        "Containers": {
            "a25b7ad667e25546e403f8bd0e8a2860dc5bab3553ccd0649fee8e181b7ffc02": {
                "Name": "teamcity_server",
                "EndpointID": "f1941856a14eb0561692f2ddc932b3cb6c7b6137ffce07724c9ad14c444fe6be",
                "MacAddress": "02:42:ac:11:00:02",
                "IPv4Address": "172.17.0.2/16",
                "IPv6Address": ""
            }
        },
        "Options": {
            "com.docker.network.bridge.default_bridge": "true",
            "com.docker.network.bridge.enable_icc": "true",
            "com.docker.network.bridge.enable_ip_masquerade": "true",
            "com.docker.network.bridge.host_binding_ipv4": "0.0.0.0",
            "com.docker.network.bridge.name": "docker0",
            "com.docker.network.driver.mtu": "1500"
        }
    }
]
```
The post above use another way to get the ip address of the teamcity server.
以上の記事では別のやり方でサーバーのipを知ることができる。
```
# because we are running both agent and server on the same machine, we export the TEAMCITY_HOST
# environment variable to be the docker ip address

$ export TEAMCITY_HOST=$(sudo docker inspect --format \
  '{{ .NetworkSettings.IPAddress }}' teamcity_server)
```
Run the teamcity agent at last.
最後はagentを起動するだけです。
```
$ docker run -e TEAMCITY_SERVER=http://$TEAMCITY_HOST:8111 -dt -p 9090:9090 \
  taichiho/centos7-teamcity-agent-nodejs4
```

Then go to the web ui to authorize the build agent.
ウェブインタフェースでエージェントをオーソライズする。

![](https://cloud.githubusercontent.com/assets/6963581/14523904/d41e58b4-0270-11e6-9a86-eb8f6cce7aea.png)

Start doing whatever you want with teamcity and docker!
いろいろやってみましょう！

![](https://cloud.githubusercontent.com/assets/6963581/14523903/d41c6f2c-0270-11e6-9b41-fe8e5a9f2692.png)

以上で、CI/CDについては少しわかるようになったかな？








