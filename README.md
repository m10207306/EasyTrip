# EasyTrip
1. Windows環境布置
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

