# 総合実験1

## 環境構築

### 0. 事前準備（Windowsのみ）

#### 0.1. [Windows Subsystem for Linux（WSL）](https://learn.microsoft.com/ja-jp/windows/wsl/about)のインストール

ターミナルを管理者モードで起動（以後、管理者モードで起動したターミナルを「PowerShell」と呼ぶ）

![open-terminal](assets/open-terminal.png)

PowerShellでコマンド`wsl --install`を実行

![install-wsl](assets/install-wsl.png)

インストールが完了したら、マシンを再起動

#### 0.2. Ubuntuのインストール

PowerShellでコマンド`wsl --install ubuntu`を実行

![install-ubuntu](assets/install-ubuntu.png)

#### 0.3. [usbipd-win](https://learn.microsoft.com/ja-jp/windows/wsl/connect-usb)のインストール

[GitHubのリリースページ](https://github.com/dorssel/usbipd-win/releases)から.msiファイルをダウンロードして実行

![install-usbipd-win](assets/install-usbipd-win.png)

Ubuntuとusbipd-winのインストールが完了したら、もう一度マシンを再起動

#### 0.4. 倒立振子の接続

PowerShellとUbuntuを起動（Ubuntu初回起動時はユーザー名とパスワードの設定が必要）

![open-ubuntu](assets/open-ubuntu.png)

![setup-ubuntu](assets/setup-ubuntu.png)

倒立振子をUSBポートに接続し、PowerShellで以下のコマンドを実行（適宜`usbipd list`で接続状況を確認）

```powershell
usbipd bind --hardware-id 1962:2080
usbipd attach --hardware-id 1962:2080 --auto-attach --wsl
```

![bind-and-attach](assets/bind-and-attach.png)

これにより、倒立振子がUbuntuに接続される（`lsusb`で確認可能）

![check-connection](assets/check-connection.png)

次回以降、0.1-0.3の手順は省略可能（0.4の手順は毎回必要）

### 1. Dockerの準備

#### 1.1. Docker Desktopのインストール

[公式サイト](https://www.docker.com/products/docker-desktop)からインストーラーをダウンロードして実行

![install-docker-desktop](assets/install-docker-desktop.png)

インストールが完了したら、マシンを再起動

#### 1.2. Docker Desktopの起動

Docker Desktopを起動しておく

![open-docker-desktop](assets/open-docker-desktop.png)

### 2. Visual Studio Code（VSCode）の準備

#### 2.1. VSCodeのインストール

[公式サイト](https://code.visualstudio.com)からインストーラーをダウンロードして実行

![install-vscode](assets/install-vscode.png)

#### 2.2. VSCode拡張機能のインストール

VSCode拡張機能「Dev Containers」をインストール

![install-dev-containers](assets/install-dev-containers.png)

#### 2.3. Dev Containersの起動

VSCodeで実験のディレクトリを開く

左下の「><」アイコンをクリックして「Reopen in Container」を選択

![reopen-in-container](assets/reopen-in-container.png)
