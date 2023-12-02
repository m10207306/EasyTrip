# EasyTrip

# Windows環境布置
1. pyenv
   1. 用途: 安裝與管理python版本
   2. 安裝方式: https://github.com/pyenv-win/pyenv-win/blob/master/docs/installation.md#powershell
   3. 安裝python指令: pyenv install 3.11.6
   4. python安裝路徑: C:\Users\User\.pyenv\pyenv-win\versions\3.11.6

2. virtualenv
   1. 用途: 安裝python虛擬環境
   2. 安裝方式: pip install virtualenv
   3. 建立虛擬環境:
      1. 建立資料夾放置虛擬環境們: mkdir VirtualEnvs
      2. 進入資料夾後創建虛擬環境: 
      cd VirtualEnvs
      virtualenv EasyTrip
   4. 啟動虛擬環境:
      1. VirtualEnvs路徑: C:\Users\User\VirtualEnvs
      2. 啟動許你環境: C:\Users\User\VirtualEnvs\EasyTrip\Scripts\activate

3. Git
   1. Git 安裝: https://gitforwindows.org/
   2. TortoiseGit 安裝: https://tortoisegit.org/download/
      1. 金鑰設定: https://blog.csdn.net/weixin_44299027/article/details/121178817


# MacOS 環境建置
1. brew update出錯: fatal: couldn't find remote ref refs/heads/master  
   ```
   brew tap --repair
   brew cleanup
   brew update-reset
   ```

2. 安裝 pyenv:
   ```
   brew install pyenv
   export PYENV_ROOT="$HOME/.pyenv"
   command -v pyenv >/dev/null || export PATH="$PYENV_ROOT/bin:$PATH"
   eval "$(pyenv init -)"
   ```

3. 安裝 python:  
   ```
   pyenv install 3.11.6
   ```

4. 安裝 pyenv-virtualenv:  
   ```
   git clone https://github.com/pyenv/pyenv-virtualenv.git $(pyenv root)/plugins/pyenv-virtualenv
   ```

# GCP 遠端連線設定
1. 於 GCP 建立 Compute Engine
2. 於主機安裝 gcloud CLI: https://cloud.google.com/sdk/docs/install?hl=zh-cn
   1. Windows安裝路徑: C:\Users\User\AppData\Local\Google\Cloud SDK
3. 於 Terminal 輸入:
   ```
   gcloud compute ssh --project=[PROJECT_ID] --zone=[ZONE_ID] [USER_NAME]@[VM_NAME]
   ```
   此時會於本機建立連線金鑰
      1. MacOS金鑰路徑: /home/.ssh/google_compute_engine  
      2. Windows金鑰路徑: C:\Users\User\.ssh\google_compute_engine
4. 於 VSCode 的 SSH config 設定以下:
   ```
   Host [自定義連線名稱]
    HostName [VM外部IP]
    IgnoreUnknown UseKeychain
    UseKeychain yes
    AddKeysToAgent yes
    IdentityFile [連線金鑰路徑]
    User [USER_NAME]
   ```
5. 以 VSCode SSH Extensions 連線

# GCP Ubuntu Python 環境設置
1. 安裝 Ubuntu 相依套件: 
   ```
   sudo apt-get update
   sudo apt-get install -y --no-install-recommends make build-essential libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev xz-utils tk-dev libxml2-dev libxmlsec1-dev libffi-dev liblzma-dev net-tools
   ```

2. pyenv & pyenv-virtualenv 自動安裝指令: 
   curl https://pyenv.run | bash

   參考: https://github.com/pyenv/pyenv#set-up-your-shell-environment-for-pyenv

3. pyenv 路徑設定:
   ```shell
   echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bashrc
   echo 'command -v pyenv >/dev/null || export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bashrc
   echo 'eval "$(pyenv init -)"' >> ~/.bashrc

   echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.profile
   echo 'command -v pyenv >/dev/null || export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.profile
   echo 'eval "$(pyenv init -)"' >> ~/.profile
   ```

4. pyenv 安裝 python:
   pyenv install 3.11.6
   pyenv global 3.11.6

5. pyenv-virtualenv 創建虛擬環境:
   pyenv virtualenv 3.11.6 EasyTrip
   pyenv activate EasyTrip
