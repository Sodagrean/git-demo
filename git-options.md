```
列出所有 Git 配置及其來源
git config --list --show-origin
```
- 系統層級(--system)
  - credential.helper=osxkeychain - 是 Git 的憑據助手（Credential Helper），用於存儲和管理 Git 訪問憑據（如用户名和密碼

- 使用者層級(--global)
  - core.excludesfile=/Users/sodgreen/.gitignore_global - 指定 全局 .gitignore 文件，用於忽略特定文件（如日誌、臨時文件等），適用於所有 Git 項目
  - difftool.sourcetree.cmd=opendiff "\$LOCAL" "\$REMOTE" - 使用 macOS 自帶的 opendiff（屬於 Xcode 的 FileMerge 工具）來對比本地 (\$LOCAL) 和遠程 (\$REMOTE) 代碼差異
  - difftool.sourcetree.path= - Git diff 工具 Sourcetree 的路徑配置，用於指定 Sourcetree 的可執行文件路徑
  - mergetool.sourcetree.cmd=/Applications/Sourcetree.app/Contents/Resources/opendiff-w.sh "\$LOCAL" "\$REMOTE" -ancestor "\$BASE" -merge "\$MERGED" - 指定 Sourcetree 內置的 opendiff-w.sh 作為 Git 合併工具，幫助解決代碼衝突。
  - mergetool.sourcetree.trustexitcode=true - 讓 Git 信任 Sourcetree 合併工具的退出代碼，避免每次合併後手動確認
  - user.name=Feixiao 
  - user.email=1596902093@qq.com - 設置 Git 提交（commit）的用户信息，所有 Git 提交都會使用這個名稱和郵箱
  - commit.template=/Users/sodgreen/.stCommitMsg - 指定 默認的提交信息模板
  - credential.helper=!aws codecommit credential-helper $@ - 讓 Git 使用 AWS CLI 的 codecommit credential-helper 進行身份驗證，而不是默認的 osxkeychain
  - credential.usehttppath=true - 允許 Git 使用完整的 HTTP 路徑進行認證（比如 https://git-codecommit.us-east-1.amazonaws.com/v1/repos/my-repo）

- 儲存區層級(--local) 
  - core.repositoryformatversion=0 - 代表 Git 倉庫格式的版本，0 表示標準 Git 倉庫格式
  - core.filemode=true - 讓 Git 識別文件的權限變化
  - core.bare=false - 説明這個是一個 工作區倉庫，而不是 裸倉庫（bare repository）
  - core.logallrefupdates=true - 讓 Git 記錄所有的引用（refs）更新，比如 HEAD 指向哪個分支
  - core.ignorecase=true - 讓 Git 忽略大小寫
  - core.precomposeunicode=true - 處理 macOS 文件名的 Unicode 規範化問題，防止文件名在不同 Git 版本或系統間顯示不一致
  - remote.git-demo.url=https://github.com/Sodagrean/git-demo.git - 配置名為 git-demo 的遠程倉庫
  - remote.git-demo.fetch=+refs/heads/*:refs/remotes/git-demo/* - 定義 Git 從遠程拉取（fetch）哪些分支，`+refs/heads/*:refs/remotes/git-demo/*` 表示將遠程 git-demo 的所有分支同步到本地 refs/remotes/git-demo/ 下
  - branch.main.remote=git-demo - 本地 main 分支 關聯到遠程 git-demo 倉庫的 main 分支
  - branch.main.merge=refs/heads/main - 當你運行 git pull，Git 會從 git-demo/main 獲取更新併合併到本地 main
  - branch.main.vscode-merge-base=git-demo/main - VS Code 相關的 Git 配置，用於記錄 git-demo/main 的合併基準（merge base），幫助 VS Code 進行 Git 操作



`git config --global core.autocrlf true`
當設置為 true 時，Git 會在 提交（commit）時將 Windows 風格的 CRLF（\r\n）轉換為 Unix 風格的 LF（\n），並且在 檢出（checkout）時，將 LF 轉換回 CRLF（\r\n）以適應 Windows 環境
