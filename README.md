# docker-python

## テストコード
```python test.py```</br>

## よく使うコマンド</br>
```container_id = 0374971c278f```</br>
```docker ps```</br>
```docker stop <container_id>```</br>
```docker start <container_id>```</br>
```docker restart <container_id>```</br>


## コンテナ作成方法</br>
```git clone https://github.com/kino-code/docker-python.git (ディレクトリ名を記述)```</br>
```cd (ディレクトリ名を記述)```</br>
```docker-compose up --build -d```</br></br>

## Dockerの全削除の方法</br>
Dockerのイメージやコンテナを削除します。下記を上から下まで実行した上で、それを3回繰り返してください。</br>
他のイメージやコンテナも削除されるのでそれをしっかり理解した上で使いましょう。</br>
```docker image prune -af```</br>
```docker volume prune -f```</br>
```docker container prune -f```</br>
```docker system prune -f```</br>

## Dockerfileの内容
Ubuntu 22.04をベースとして、さまざまなソフトウェアとパッケージをインストールし、PythonとJupyterLabの環境を構築するための手順を示しています。以下に、各命令の内容を説明します。

1. FROM ubuntu:22.04: Ubuntu 22.04をベースとしてイメージを作成します。
2. RUN apt-get update && apt-get install -y sudo wget vim curl gawk make gcc: Ubuntuパッケージマネージャ（apt）を使用して、sudo、wget、vim、curl、gawk、make、gccなどのツールやパッケージをインストールします。
3. RUN sudo apt-get install bzip2: bzip2パッケージをインストールします。
4. RUN wget ...: Anaconda3をダウンロードし、インストールします。また、Node.jsをダウンロードし、インストールするためのスクリプトを実行します。
5. ENV PATH $PATH:/root/anaconda3/bin: 環境変数PATHにAnaconda3の実行ファイルへのパスを追加します。
6. RUN pip install ...: pipコマンドを使用してPythonパッケージをインストールします。pandas_datareader、mplfinance、japanize-matplotlib、TA-Libなどがインストールされます。
7. RUN wget ...: TA-Libというテクニカル分析のライブラリをダウンロードし、ビルドしてインストールします。
8. RUN mkdir /workspace: /workspaceというディレクトリを作成します。
9. CMD [...]: コンテナが起動した際に実行されるデフォルトのコマンドを指定します。ここでは、JupyterLabを起動するコマンドが指定されており、特定の設定でJupyterLabが実行されます。
10. このDockerfileを使用することで、PythonおよびJupyterLabがインストールされた環境を含むDockerイメージが作成されます。このイメージを使用してコンテナを起動すると、JupyterLabが起動し、指定したポートでアクセスできるようになります。
