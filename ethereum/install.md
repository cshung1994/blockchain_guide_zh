## 安裝客戶端

本節將介紹如何安裝 Geth，即 Go 語言實現的以太坊客戶端。這裡以 Ubuntu 16.04 操作系統為例，介紹從 PPA 倉庫和從源碼編譯這兩種方式來進行安裝。

### 從 PPA 直接安裝

首先安裝必要的工具包。

```sh
$ apt-get install software-properties-common
```

之後用以下命令添加以太坊的源。

```sh
$ add-apt-repository -y ppa:ethereum/ethereum
$ apt-get update
```

最後安裝 go-ethereum。

```sh
$ apt-get install ethereum
```

安裝成功後，則可以開始使用命令行客戶端 Geth。可用 `geth --help` 查看各命令和選項，例如，用以下命令可查看 Geth 版本為 1.6.1-stable。

```sh
$ geth version

Geth
Version: 1.6.1-stable
Git Commit: 021c3c281629baf2eae967dc2f0a7532ddfdc1fb
Architecture: amd64
Protocol Versions: [63 62]
Network Id: 1
Go Version: go1.8.1
Operating System: linux
GOPATH=
GOROOT=/usr/lib/go-1.8
```

### 從源碼編譯

也可以選擇從源碼進行編譯安裝。

#### 安裝 Go 語言環境

Go 語言環境可以自行訪問 [golang.org](https://golang.org) 網站下載二進制壓縮包安裝。注意不推薦通過包管理器安裝版本，往往比較舊。

如下載 Go 1.8 版本，可以採用如下命令。

```bash
$ curl -O https://storage.googleapis.com/golang/go1.8.linux-amd64.tar.gz
```

下載完成後，解壓目錄，並移動到合適的位置（推薦為 /usr/local 下）。

```bash
$ tar -xvf go1.8.linux-amd64.tar.gz
$ sudo mv go /usr/local
```

安裝完成後記得配置 GOPATH 環境變量。

```bash
$ export GOPATH=YOUR_LOCAL_GO_PATH/Go
$ export PATH=$PATH:/usr/local/go/bin:$GOPATH/bin
```

此時，可以通過 `go version` 命令驗證安裝 是否成功。

```bash
$ go version

go version go1.8 linux/amd64
```

#### 下載和編譯 Geth

用以下命令安裝 C 的編譯器。

```sh
$ apt-get install -y build-essential
```

下載選定的 go-ethereum 源碼版本，如最新的社區版本：

```bash
$ git clone https://github.com/ethereum/go-ethereum
```

編譯安裝 Geth。

```bash
$ cd go-ethereum
$ make geth
```

安裝成功後，可用 `build/bin/geth --help` 查看各命令和選項。例如，用以下命令可查看 Geth 版本為 1.6.3-unstable。

```bash
$ build/bin/geth version
Geth
Version: 1.6.3-unstable
Git Commit: 067dc2cbf5121541aea8c6089ac42ce07582ead1
Architecture: amd64
Protocol Versions: [63 62]
Network Id: 1
Go Version: go1.8
Operating System: linux
GOPATH=/usr/local/gopath/
GOROOT=/usr/local/go
```

