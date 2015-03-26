#docker-gitbucket_container
Gitbucketパッケージとデータディレクトリを保持するコンテナ

##概要
主にTomcatで使用するためにGitbucketパッケージを配置します。
また、特定のGitbucketのデータディレクトリを設定しています。

##Gitbucket
- [Gitbucket](https://github.com/takezoe/gitbucket)

##Gitbucket Version
3.0

##Maintainer
minanon

##ソースリンク
- [Dockerfile](https://github.com/minanon/docker-gitbucket_container)
- [Docker registry](https://registry.hub.docker.com/u/minanon/gitbucket_container/)

##外部からアクセスするための情報

|パッケージディレクトリ             |データディレクトリ|
|---                                |---               |
|/usr/local/tomcat/webapps/gitbucket|/opt/gitbucket    |

##ビルド

    docker build -t minanon/gitbucket_container .

##起動方法
データは、ホストに保存することを推奨します。
パッケージやデータを保持することのみを目的としているため、プロセスがなく、すぐに終了状態になります。

    docker run -d --name gitbucket_container -v /opt/docker/data/gitbucket:/opt/gitbucket minanon/gitbucket_container

##使用方法
Tomcatコンテナと連携することを前提とした構造になっています。
gitbucket_containerをTomcatコンテナのボリュームとして連携すると自動的にGitbucketも立ち上がります。

    docker run -p 8080:8080 -td --volumes-from gitbucket_container tomcat

Tomcat起動後は、下記のURLからGitbucketにアクセス可能になります。
http://localhost:8080/gitbucket
