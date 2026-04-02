# エラー内容
- Githubの.gitファイルが壊れてコミット、プッシュできなくなった。以下表示文　error: object file .git/objects/... is empty
fatal: bad object HEAD
fatal: HEAD をパースできませんでした 
## 状態
- Gitの内部データ（.git/objects）が破損
- オブジェクトファイルが「空」→　HEADが参照できない→ Gitの履歴構造が崩壊している状態
## 原因
### コミット中に書き込みが中断された可能性
- VirtualBoxの不安定なディスク書き込み←　今回はこれ
- 強制終了・スリープ
- Git操作中の中断
## 対応策
- 新リポジトリを作成→　rsyncで.git除外コピー→　push
- 今回打った文章　rsync -av --exclude='.git' ../linux.study.log/ .
## 予防策
- 特に仮想環境でGitは書き込み途中に弱いのでこまめなPushが必要

