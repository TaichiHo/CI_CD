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
![](https://lh3.googleusercontent.com/PfXfVQfVZ9J0fVpiRo6Wipw7DhvSBhLetpLNsL6wuO0IsendZ3te3xqb9h-uBIGTfqDrchSmxnW448POXGT_cwdZoIeScxpf3xidPDAIYw35PWHwThxRSMHH2hHZk8avG8FT7zlRDJ-NZFLLwRtjuyEC8qvETIjYG8nZUtK7qZrKm7z1tYjFg7XJ4urP0SsRJOUvCKQZdNu4_YIW58E4LF9vlwi8KX1VIJrMnYPGF2Vo-plIZezwI2KPH6o0LRJsaoEVn7UuE3lZq4MDNlttjdcXLfTizLw_xnrbWuBnMDeCOJtT21qedElZ33JtT9sbsWTN-0kSgV3PzbTSdEVQtmi5OVYL8K1M2_Oz4IElY92DtHizy8Qa8sMT1cIJZC3yKQZVKyTJcCCQze3lUfJqKByJDTEGfyhm3zODN1O9U4t-c130DyFHQHu-QN50z8NgcyXEF6zMu9vrJmVygMywzCyJTHh2NBI5NFXBWF9HejOoXh4rzgkGNYJQ2-yxI_gO4Fkte6JFfSdmGiG5ZDJGnXXoLjCP3RaPXX0WTkfnSK7mu2OqVa7BTYjAsvh6ODtI70w1=w1278-h808-no)
### With Vagrant?
![](https://lh3.googleusercontent.com/uH6b8h73n80YBRVvT8kLe8UrjNmavoJcFmm2lrAxxD_upob-iPYNtVO3ffJEhdLw04A9QEsM0vMt5cC9AEGdL36p4wQjhm9wUEOWHGzu_J-hxut5unG46lhGyuwTNtzZuByUUGYQEWO5gLqfF_n8EToZo8hOIkal1sFi9x7AZ5GRFBiCBA4kC3aZkK8tQUY-Jm7noMVQNZXXJObrBD-lk8HGpSbyMhtxzOJW5qtAmqw20b7HxRuzR6Wu6qGPIPqEmSIMwRM3tVRa19m0hPajVM0VqUWbWD4ZDVW2ygke72BkMj9__zWbYM9PMz55b5nOCqkIwJC5LHZJtzHIIrrR7XJtm4o-_6MSGuaeKvW6HVsG3vM32EdQaPTYbEjgRB36UdXbdpMI2kSTDTtoRqN0ECp-H_FlUebXaqwx-HMh2D1mPl537FfsEddMXEtypil6wJMU_h0yW5noet-U6Y5mGYOwWGm2NJGnp3gMhGMMsQc5dRspPsPRUvHk295YLPrTRaM7Bf4-Dhy6gEtPrGVZKWxWPhaT7ptUJOCH1-X-CZsQioyV-t0VLk6WqRIXNkBk0cVJ=w994-h647-no)
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


![](https://lh3.googleusercontent.com/7b_fctEblgX155Ttrb6YNUaBhKz0YPQHcxtkBCtPMmfVFqcsX-7QfzQ3-rFaOzBYQRfBhRrXufmhYXUJ7QWxn6Mx6Rho7k3hmYbuDl0dRBthWZCHp7lbDv2-DIzqXBiN9Rc5sMhFlcbsdZXS6udJ3YGlY-UyBQrKUpUjkDEuruHsh8aOwsmOiKy-XzQl4wui68ip0TNeRz1tUt1Tf81lrqwsGGdbzGPM_9TihSULCWhKcdUBpbK99ObAfyvoKWJJPaoqC_vFiUsxbBvuA2Rg0HhkM3-U2gfa4oDyJWM0R1fFiTOdPP2u0Q7sYcoU5dpkv4GhfYF3VwgBghMHpbaRScGP2DxPGbiP3UdpAfE5MBhNruPGLSVyuAgxFtCILyc2Kg1VdsmyiT3hAZsrKDw9oOdDpibp16S33MJ6fIVH6oSLbQTkN2iRLmJwwqTC_d6A8CWlKNhKBEF32y1WPgyduDtR5QhjDkgTISJdsQPqgkyiVIzv1jaSQPkzC0jFemijLEgtLknEvteWTNI-UnWMmI_T12kgSQPXgj6Re3VfRkWP4Z2vX4K67cJLtLv9Gybs-M5A=w929-h636-no)

- Link to your own github account. Check the repositories that you want to have travis support. Go to [https://travis-ci.org/](https://travis-ci.org/) and link your account.
自分のgithubにリンクして、travisを使いたいと思うリポジトリをチェックして、リンクさせる。

![](https://lh3.googleusercontent.com/NG9cM5jbcpPsM5fSSO8YrYKOxI2t2_gsEH-VnU4qkhCxXupxjnBdYTF1zV562XtC88Vk-mWvzspdDzMCwrC0NvBhEPQ5-XRfmfXYlvq1aHEUFjkj2g_wg3hhpe3b71KlerfE9iqrDGEk0K227zMWrejOfL4gW4_rGwn06dQ2kyHfuwSVJJD0QFGc0My3m69tK-v4MhglnBuHPNU0vWO636PEDFn960BMdAtCyS2mrTm9lOG4O2jKiraGnxp2E9uaoRmmPmtHVGGG_z9ndHyeYLd6Ts_FYPEPgV-rrvL-9KeGNm-sT4IuBxQ0g1kZDErvculb3gUH3NUMZrrC4CxYFTsfnzsbY9eBnjX2jKwAro8bI_hWrLMQl5tIJsrpnxOL9M71tc1dhES_GNMcKYy7v746AXkBwc8DrW7yxgQgt18sODabKvtwZ3gXYFYDCAFlRo1PlZW0w8DyQE4CI2dEuAp3FAwZ7HtaeEYKPJb9QfgqJ5kvonEKMQdh4_9i7maMC0W0G314-bmgI6us_5mcuZBqgMopKPluqIrhVgleAVN3Z0og3fHo0-zycwMSZwEq0L3g=w1073-h829-no)



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

![](https://lh3.googleusercontent.com/B-KEbv-Cpsco0OcAZbhfOPQSFIQNMI4UAtk_Pf8Fy4Q4d_dmol9KsuNDgGOiREh_8FIjWRdOnIbB7XjCMy0FyxrF17uVHIRBoc6JChVbxtoMl3e7cXGD7-pboD8tZpUrMgDZRHe2pcmM5S593cmtwJVBOT5TZDHtvZxipkgRrjzM2pOJ5JTGCpQPcCbDwUGmEpra38HGCQvmjtrXznU-CFmKTYVI3YTliGFpttkcV09ImNGms70O38TXhtPnnywu5KwXm2t-NT3kGJJrjffBbeO72yjb3O6aVEPz6Nll36v696P_mbYjVsARko6d3N_9jG6VOMvtawNqd2EnZZbq2JUzrX9f3aC6lNsoBD2rRnQw8B17jOYlc0MXp08bZbK8fl60cXA-wX9rjaRj8eItoMMtm4ZKVSOCyoRlxhyaGKqPSwPuvG8TTHXeSRiKaB0FStT4GkZodPLw9I2gj8jFbzJd-QfRztpsmd8-xdMs7QZBB5XFtLm-JXv-dDoPxcRtifiFoQqKYLp-4u0uWlhGodUFODtuzsZgsmi4XUmV-7IwojC_LwF-2J8eJpb6ytzCbe4D=w1901-h570-no)



　　Will receive a email when you fail a commit.
　　失敗したら、自動的にメールが来る。

- Fix the bug and push again
バグを直して、もう一度。

![](https://lh3.googleusercontent.com/gGlWT499NOXxmrgm0ZKWfBCc9NY9YcJrqlWNLZa7GaNGwdvz9VPXCSZWiwirz2a64Idp4E_NcICue125bqhDeszTkAissb25Ciz91NcOUjb74tvatnVeYolHlK79xbCD1V_LWGaPnN_gzViMNrodduTDX39v_sFCcUurKp8s9HAHziAgpQ7AW1X7A2Eh_MYE12aLiReRBc9l03LN0ApoFMtbMS0M5EPIBal3mnUVhHWLFWZL5bk7cqyjAbWrbklWkhWXpJqeIkCRTNbomJToufcI1yDpkjwMEmOMyDhrHZisH26SGt96VUs2xVLExf5-kWoHi7UpGATiN5ecmCfaekMYJnVrFknt2nNfY96h1mfy3aA2xeU0skaJNOH5t0hWyWyMTEuQmYWsdUBRQynV0HRIXmfOVcp84RdkrfybqXHL1ueC2n40sQwa6cU6uQdcw_sj4g19FFVcTz2BEcQV1YQXMLdJ_P-OP3SJT0scmOfvKwW9w747eyBWvHaZqTIRjcH16p6FWgRPIOhng18TAMXN_PhZtjILOoOGnv0_NctTc_LG6XdV8pH-Ty5W25IBHk5T=w1908-h574-no)





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
![](https://lh3.googleusercontent.com/Au9Z3ehXS-N-YmhY7c4tcX8mHrlzXaFSKDHM-OIGy-nIeTOri0Z2L9hLtjJybXBNwNDZJkEMStZTYj2Vey7xG5WS5xTSPk1K5i3qndpacNTSxrcpFv-J0uCcXlYEKR65LuPBjosN36G_iJNTH59C5TmSVAk_yOdIEegoPBCM7z1CD7gWvvggM06ZLc9ec7cCOy8EEGktzmSxfIYgFX4VlgIOjDDchJpKQZ2rHEUgO-CwxH7H5SBFcFAADZwp43uMre4S7LZlT3yqIzXQRrI9HMWzyLnQ5Eq998UyZzjW4_rZEs7W--ickTHfYO1JDgKOc0Ax1tpQUZI2RWEpctnicFApn8y-m97poUeyVS6DM7cQzbbMN1Cv_3tvYWQ7edav_n619z9INU7RMoMNvgqVFdNAlMeWKs5O-4pFTKwH5wKvAy9XPTiWjPSYdCmUB8nX_TTlXTqTAd0OR1u_BIC9usQ4LzhEXMT40gkgzQi-miBw6U7dFGaytxjVHoCv_GlrqHRfMByZJ61u_6fQ_GF8HBxuVLEZoo0-tu0XY7QsSkG3UtdZqFGR99eUZfVrU_8AKx3N=w2444-h834-no)

Creating the build server. 
少し時間をおいて、諸々設定などを行う。

![](https://lh3.googleusercontent.com/Eu3OYVhH1-V7ipGLkhTQEjcEWIq5C4Ytuk9E59LHsVPAso4OD8-jaJn7JpDeG7mYyrhr0ePGC00B7ph9VAhnKNjljMYjf1AQT2wyA_RmfJFw_K94zRmihe9mhmtLCHF0cwqgMAX1kRPCgJG2lgP65cgu2Od911t9yNURzbf-0ULD7ddsY1thVKKSSGlvlVqCI6rlDM69Drsqwm2Xbr6taFo6cFrvguvOgb23mjC2gcHYutfluXmbxYpIDABMMrN1TPI3FXAiMe8GKuZJBCKrCZVchZzbnPHfxr_rPWR1MSQCCll24u5JSxwHygyu1CNT-CXS1dpBMC9ulaVnOM-GdzXlcGw9bZBQln_oUCJhFukAg40-NGxCfFPJRupW0WdwENV4Tk3d-e4VS6Ys3hSDK1cNnAXLr6L39IEyP9RL-G9hB7YNuzw65w7sD5mCsd16kdMNXoOTaojs513q8_zz87ztb5-Mew81RDURExKWOhGPl3AAVsWezZEQ4brIufRy1GRvst_s5Ln7ZMcmqaYiswDT-3cVJwajZX1qRM8gS7IuprDuwRYo8DX8gXzttP7oVwXI=w2416-h448-no)

For test purpose, build server and build agents are in the same machine. But in production, they should sit on different machines.
簡単な試しなので、サーバーとエージェントを一つのマシンで一緒に起動しました。プロダクションの時は、分けたほうがいいでしょう。


General settings. Set the artifact path and the names
Genearl settingsで名前の指定と最後に作成したファイルのパスを指定する

![](https://lh3.googleusercontent.com/PsOlt_Rau-c1rlg3oBU3B01eGlXiKvY4B84OoE25uHDl3HO7MBjZiezXsi-yq8oFbUdiACPQduOZZL-detbaeUJ0VB-CUVAd4iiZ0oXKsfIKjb2rFSxu-MFXxJJ2SbgXxqaOj9yeuPtuo5H3bSkX8pFmVB_Cz7Q4iJHQzYb_RQQ_7-jHU8vMzS-A3Rue_jVI6ibtaaL36eLdrbJvO2yPy-yh0pwOGIk2u_UQhQ0gqxDTAI6KmlH_pbI1iO-tYx6ILzVoSFECuYtHG6ZRVhpQHxI4JVPET7SwcsQwKAZV88tn1cNJDB9UCTJ2fC2bUeTvSA50NMjceTWqKPDANRO8-NNM3u7qop4z_jFKjAFGz2q6-yWIAPOtal_BzK-Xa31gn6YeFtWQO26_FjHNhBL2o1Jnak4ikPfc9o4KTi2KEPniKtS0SNShPnENouwxenl4cIGsuLt2Iw3lk476nAFDv5xcLf5ygFrv55tuxc-Y4-ZnZiu6dMz2UTKAiR8xhnOvf7L7CIQpbWZZAaEX92tuhl5xYDm8EQ7achqOisFcMOpkdgvCMNRUbuLgHNrunFlpcD89=w2516-h794-no)

Add build steps and set running parameters; If using maven, gradle, gulp, etc, it should detect the build steps automatically.
ビルドステップの追加が出来ます。選んだリポジトリによって、自動的にステップが検出される場合もあります。

![](https://lh3.googleusercontent.com/4SEO1JhqqpM4LCV0B7B_nDhl0PsVRY0aTakbxJRRzwjeGPB4uoHKP8YT6Del0QYFuZTsR1-xXkpRGuEi5IofdQ-a3xh2g_8PIyIaKSOhZH1DfcK922LDBD5jBE03k_DdLvfKKcKjjSJm_f6oS3ISsAOSTP5CY_Zzd6eiyOsAGxc592q8Po_hebA9i7mw2Ppy5Sj4-v6_Q_mNsurnNpyg9Qv2qFEb7owUUSpFsbkZJftmERv2WA_4hcwN5BLu6ha9K6lddgi1xrYIq7PswKdWpacUNhjdUd6hqBrmwsqgzBlhvvEnkI4z9NXj4xs79Llz8Lo6iqmE-rq0jRFKel625p-ZQ-gJXJ1jy6ZPfJQGwtlbdoCQ0lR7sb1JcvmAXdEPqsnT2fI2jIWHC1YImeWFFjns__w5F1Fxx9PkPOoh5f7RtHNDGw6Q0C0mDbWg3dk59SrjWmxQWRS2DQBAFd7z9ewUo_EnURu8V52SEr1BO3gtfkgKfkueCv71AfE8a5DFKq82T-l_PEAABXI861c5ToD8MoqLsgQzbiZAKfoZuFccgE9i6EyueWWmP2S8HTcvD6JM=w2518-h1022-no)

![](https://lh3.googleusercontent.com/UMljVipxEyg1s8IBX8UmRy7ZYw5LZSbN8izjOriyai6Ygzzz6OV_ALeAm6esVcc3jND1Mh46n2pE7pgxdq-3MKyQfZJhGxJLBp-yq0nTkt0b3P1GYEhlci5S9mJw3L-hdQ7FZoXk48doQJJmdo4iuwdHX8nu_djvWjoRQC2xiR6qyIVhvU7Sxg-kxvcc1E_-govGDvCmPGTnTKbVQtqZCvgUnjHOtTBlZvlp5gvXMZAjmsd_dUIRbTkyXkTi_hPxVvl6HH41R5ujUrFlqhIVD4NxjPdo3S_aMnOYOQVk_XPCWT-JXkO8jcD6ufhdL2JzDrehm_XU1Omxr655Z61ynzDItymoV18KB3WV6SKSSlmH-xCkZNzcztor3MZYZhEbzPXeKvBh0f7vTrQpUBFnAAxAmukuWN16YYoTlzkq6lsCi6wztlY4rCUdi5rGtTT813fdX8j-kIN1_BhGQxYWR_xxXNv9Xd_LrvkUDZoVAVNBXB8ldtsAcrgS22IZJL95SYk8TNxftb7wg2O5aOmnd3ItHTEAiLKQC51AI_eo8irvzrlf3K1B1N8dnRpO1cEwB94a=w2514-h652-no)



Add the VCS triggers so that the build will automatically get executed
リポジトリから変更が検出された場合、自動的にビルドすることをここで設定。

![](https://lh3.googleusercontent.com/c35RUFXLeHwKYjFC-cofvslVq8CBoMWJIQSkVUpVn7pZEaltDhV57x8ZIpU93CvjkcHnUNaaKv0AGFtfsWf7qBgMz557NZZizKxpvzaoEwA0zcjXiI5oJdMQNDpXfUJu95ams-qmqDNSkV7CYM0dz82fg1V1ytXkvJJd_1b64D9gLC8YPDzubGW0wFvcoQSxcmBefIvwNKw5nVavb98ZX-fVfva1oyeWDa6i0HDj74A2BWs17T1o8BAMIcqfe3OonSrjiZxiH-jKZ9djun0WPSKOi-0K83ORB42CzJYpNqt9XwNTpxbmxqZmRKO98dROB8iK5ZYIlo-ehTW40mDLdKKWrNKdQ83PemiOyELqS4iW49LSBk6Jae1P7NUhjybPR6kCPczUjnK9oBd1MgO-O9ZNW5PuFhl2XFlDQKcfEJg4uyjAGA8WYzaxeHiMseIhLbQ3AoXuFAJm8TziCfGjx4LILHNz1xjXfHc-NHMq_2u6O2GzeIE_SeWNiLfiNedTACFInq4xWkeWzEQyInSWtJPluqY-sGPYmXEyA6lzJgM1ApKIhj749oEKYSm7y_q2HW88=w2526-h734-no)



Dependency settings. Useful in managing multiple projects in the same teamcity server
依頼関係を設定する画面です。もし幾つかの大きいプロジェクトを管理する場合は役に立つでしょう。

![](https://lh3.googleusercontent.com/Hedgss3c17JT53n42GoyPSmSnOa7LJlfnyGWjCO_V-30NL6ZKUNm9rWfo2pnnbpmVg2il-S18Gkpfe_LusqWJRN9OFUhLFHHysCM7oJGAvs7DQH-RyHXpk8rvnFG5PeFakCYDplLfL3NdWcf9ABjsNpKPs94yKt49J938CRytEtsGbsTKrO6nGAXZiWpDMQR4xioTsqyP3ozt54kOrqtfZWGhSP2_JPfKOgNo_fxKkOyVfWcN6Iqs8MHy2bgUSduDzTjRe2l1JgeIyo-94IGFVag-U8QmPZizucrATU9ZtwP1G0eN6VORcSeaBQYqLFLqvojiRyd513gVJWGCnogAdQRcZljo_x78YJjqn31wWB4mtTnqaf_sRGcyRMwAik2bc1Vlu3QO7uHwfjeoEFr4_OdIfRWr2v_gURB8f7S9Zf9zfUe93jeZVar9xjJ_k94CURylYKSeVORBs4XVPvPmTKUqEuedNDDGXHbdZI8aRzg75UFXQbf-0tZfk3DbX5YL1R6YxF7AINvBQkQvNakW9rNTeo2lWGASzuotzsy-Er_FzJO8VCUnSkMbL6v3qVdAozM=w2526-h906-no)

Parameter settings
環境変数の設定などここで行う

![](https://lh3.googleusercontent.com/GPTXtZ3cPtM6E-uv_8Oj92qO49fvSQdXIXQ7gy-bmwdIgARU0CMb9GySiF4QqFLmo0Ck63f-284L9wCpsT68ZhwFX5xOked-kU35-2QoE_rpKQhTtLirfAeePG-MgN6xoSgDenXNDuN6Hr7b4KX--5ySqv9VgZLcCx-1jZfnisMcz_fBRLuckzzSjNXnrXyT0WgWpLJ4P1KZSMgUHc6SqKAHJ-b-R8LepfT4GBZx2bhc7lGavx2NYpuhWQ1rp9-H9v6dxPeZ6ZGkxkmKY7L_4P77EL0MXkvILvUmDCpBpUx57JphPhevylxZPlHrBh8eWu7J6y2GzBolrToro0gED16BwwisiFIXJFT323pDyChHKia7r8qMLf5Od-jX_rmonF0MjEjTGemjYAbHn0mo0sZUwoyLGOcPYEYB_IQQYxwi8Pp8fdZGm5DMn7DXjRpxeDENINy3v6sl_1sSuZ31Xb37reLuad3XTXaKToie3xfBV3bY1jjkTZzfQyrSt_MsYPhaCbUZOtWXXObJDTrvumnmTdfOfIZ7qvVpYcWAZuF-r7ME1tJwd9qSbXBMoXYMFArl=w2540-h906-no)


Check the failure build log 
ビルドが失敗した時のログをこちら

![](https://lh3.googleusercontent.com/7rlzDkq0g35gKiPE6aYDv1uxYboR_OK2QaFUKlKMeewo5f6IXqB5pwuzzKFI2n9rsKo518CscjIjW9lYpftIpNr1_QnENTaJ9keihA107fFzXWqGUU2mnr2snymDXa5jlC5rui9fhu8GdvPzLLCwuqgpgHdDuCKz7BBa41nzkjLw-apKZCY_uT-ksp3XBuh4eRORnG5CysmAJLxw5VyHRXkP4DyL-zicAIeV6XH87qUt_YrK8XYcxsrb40FfonOiY2lpaigs5IM2T60FY7mMdBu_KW3C15Nnuj32oEc8L-4di7GenmzjYyI4Gj_Jn7RlqFaPtWGC-mSMOCB5fCYMlmYB6V8_ighizwAwXUKyXYfJDRIKpYz4Ky23-WBEDsZEUazB98CGlqsWwlIofDvWHfhVhmvyU-AxW1nARlEsWq6oUV1rrtoiUrsWiDn3J2KCZZOq9UZhgfmtUDfEgkYYyDZZk0BWXZtQKQQEuTuRaHRSMg8fqsuj83PBcyCqvWdXtX4n3j6buaFFHLUUt9_MxLew-iTqp8_24jv8UAwYw56GCKYN6a8hFJm1Vs2rWQg-PanO=w2522-h740-no)

![](https://lh3.googleusercontent.com/_bTefREhv8OoWR4cTt9-fSbB8RzKEwFr3FKD_YT8KnpC78ac3rCzSpb9cxTMvaF6qTAmhhhqDA17akdRM_K6Rj595fgtJcsuGwi3BmPKyG0LKkChDyZvR-lu7GRpuwMKMRgi668vlF3GSJF98hHr62MKWhLpslzZqYibwGk6j_m_twH-21pyuAId7eZMOKoUDV9DbZns_T5yK0Qyd70fmXqtvCFeF9qDe1o-hBE77UmLv5L9QziyK65g3MukDF-QaIHhpe1KeGBeWsXyx8AFC43XFmdyj3-F79DRkAW1H81UvMVHwz3aw0wD8w1sbrQV3DbVEASbJsXi83A-rBhAMVeYg98usGET7mpgIX-sSXZgPMKAbvrHU8hs38SW1BA9HWgV3ot8LQAMxHYFSC9xL_SHK-XZC718NNb77PozzzNZIdcBTzij09D2diNoRjYIxUvLfArB2bfnknjDtb0xiO96hvN9tW2oYB9hqad4XDXrBCLLSh27UVfz5ORFLL4p2e6kskGPnEUvKSoxGMIvocglpmo_MVcB2gYXYlgZJfT7mtX58SHhtW0wQTUyHIyO2CEZ=w2522-h962-no)


Every time a new commit comes in, it triggers a new build.
コミットが来るたびに、新しいビルドが発生する

![](https://lh3.googleusercontent.com/72KfQZ1ZvzIcBrptGsdDaPOyiVEdPntrdT2AaOJ-XrT-ciIVkxJXyTYcULnKqEcgYzgElQ_-RaT4jP9Xi94Gtl96-IwOm2btGhEOVZDs7bTHtkwTXWLazN-owxevXC4WyJOCv6rK0ovnIsCldJqcxPVJdK4ykBxwJEwYk7KQOH081GeRwozSXk6aFPRoTgzfCyyBZ7qNISZI2pftC37xfGAzhnEYHX-4GT-Kt37FwU5rcQVgg4aLN_WtJEMzxnfNwpeMmSEdv1lEdhLvGbiC3Lk39nHcVYG7l_VVpOE47cMIEJdBSdOJyLe2Hcnp-lnxT5_AnWh8CPWwhphbIIJVTHPMZ0s1SIFJJhLW9U69QGX5IMA5YUEf0fJySJCZenSvi1DhWV_qe-h6e6jOfjqJHfViExgbjr-HcJpAMylBhs3oYO3Crz9Be1tY2qT4reqrfG0BwVe8NXT91As79QWyid43-Pt9VSX5OL-v1Tlfg85Ytl9cz0vH0dJ32Ed0bRlfQmfdR99CTixNN3KnOvhJydkLG2F6TvTSFv2oNRg9821SRyAKbdngoeq7v_e1v8UyHJzU=w2522-h504-no)

Successful build
ビルド成功

![](https://lh3.googleusercontent.com/TQHkvtIIhWG4uxNdMzccINmKKpRRWbaZ9tX-b2AX-V_2Ht_j8n-Ys6FtAM3piCcLlXpybDtpoJUeMLv2QHx9Dka16B_RmW9Ai4d18P4WU1oqjBeeFotQvk7sJazUbbe79iKgRNdrtXu9TrmmdnZJ9RIt6blP4hIPmIp0NfMYA2h8DlPWPYVsQlPt8XMwBj_kbBFmUPR9IRgSthinu-_O2UOtYwCCj-ukXnfZzrGc2lP9QcOWHkx8RTPNsYpHs3pdPKhfkI6oOdrPezXXEZv9Pt8SSVREf_BQLF8JQ_D1aDAo9G35gPku25pFy44T4zH03aIIIKI8V-UKQ9NCQMRWEkyiHnfMAr8RFU6qR6RRIgRmIL5r6D-I8shvFsShisw0tpoW1KwgR5e0AbTlrR4VYA1mk2sgTujGV3acdZToqBTDZzH4bJp1OxTnBhfWdICZ7Vz6S2KKJl2smjJWXUyMaeE3vNF3ItlsxmuHeAM0X4RiQpsqYW9s8cOiMYOqIsJXwhML0A8ZkGjU8eLZfSfCHDnbwfmhWcKcHtBGubZFBaobxvZY8PY5JxcdiBiqyQll14kB=w2528-h472-no)




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

![](https://lh3.googleusercontent.com/haPBcnY0si5wjfb6BA5XTAZ-DQkzAEUJS-8i4Zv4iLsEfEbMHDr2JgUOuUwW5FYtsKBdtm6zeDRCfydM1vCPKZN6N5-aQ3n_5f3j_x09kH_shCakNa66J0TtlusR5u0A3ql12cK9WK9kaY8P2cakq0seMX2PNBLRDIyxN0I6ILP8q2XiUdk0aUmMfyQKNXMHzBv5WpMrZt1p8kExVy7MPVue3R7rt4W-zIoqzLbuUXAjslMdaDzP_2CkmpQKIfJU08Tq_HBWO2AxljTtHfbA4zmIphZVJDGp5G8PWMlsO-XA1eXE4FB87rT9yPEa54SRYG1Q-TmuPOSdjOxNIcDbQ2LH9v8poDCGYlTAEf8SC-qlY962CfGcTewQDJIGxDpDAUKwjYjwI5QKb_l3J-NBnmPS5T9pbnRDAMZHeZZg-TUMrmNall3VpE4ErajhgnXgRNjXUDPF3yz2O50vqyOZOFDxVt6hXRJTys8rkfQif_FXvOLxkknjrdLTNu7okKnHkB1FbGEsz9wojTJ4Xp6I7m83LuHy5sU-AvgVI8GqSywN6bWx1PAdiTgF6sWxqjSNoV4M=w1672-h234-no)

Start doing whatever you want with teamcity and docker!
いろいろやってみましょう！

![](https://lh3.googleusercontent.com/zw0vxWknH9xftrdJUOFnvYjx_H3eEStPoTYXgfE6IxOl48ha9AhzLFSK5RYdSxwPyComGlHYW3mOGAASE9zB2Qh9XCeLFygzqzyE16HMrxayNmnUUlulJ352iWeei6RZiLNuEPowXv3GCUq0UKKL0RnX1oGJjq63W1qHZFTwXygUEE287mvTS7XoY4Zqpr7tODOHWKlMNfwwRxuOqO3Xj-3sy2PwvgBz7dGKvHVTIizD6iOHxuA8tCR1VVm694cs-oDmjDhKMN3db4KOIbFBfy3fZ2WOmpJwhFnilNPJL5xHWlHDplvwZrlAOPelrcNCg-mLvJigX-zq8zltngCo_h_ngzgI2-VEtgJPbDpBM87vIHXEMKGJBM_4uiT3QqXdWILL2mwGraZYcR8Pxs8DdIu1CYnpfYqUonb8qRJFTP0aAsZbfyoK2z1qkn4jW9BKUepsYxRcFkFgI4dpWY8T0z7EcBNgQZLYCYzqDn_KrWtMl_pkQBLAk54yGJCWZJE6UGuVQ_PxO-WUXFNJXlRBzPEm_hEwI1YV5BiwB3yZG8Ps0CHYRceCA1h2uLr-BbJZNfQk=w1703-h540-no)

以上で、CI/CDについては少しわかるようになったかな？








