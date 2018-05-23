# workspace

## Gitコマンドまとめ																									
																									
◎すぐわかった。任せとけ。																									
〇だいわかった。大体な。																									
△わからん、調べてやるわ。																									
×マジギブアップ。無理無理。																									
																									
### 準備																									
作業始める前に、作業用のディレクトリを作ろう。																									
- 新しい作業用ディレクトリを作成する　ディレクトリ名は workspace																									
mkdir workspace																									
- workspaceにカレントディレクトリを移動する																									
cd workspace																									
- カレントディレクトの絶対パス（フルパス）を表示する																									
pwd																									
																									
### Git基本																									
カレントディレクトリでのファイル変更、追加、削除をGit管理するための基本を確認しよう。																									
- Git初期化（.gitディレクトリがカレントディレクトリ下に作られたらOK）																									
git init																									
- Githubでリポジトリを作成																									
																									
- Git remoteにGithubリポジトリを設定																									
																									
- なんかてけとーにファイル作る																									
touch file.txt																									
- ステージファイルに上げる（addのこと）																									
git add -A																									
- コミットする																									
git commit -m "aaa"																									
- プッシュする																									
git push																									
																									
### Git実践1（自分の変更をリモートにPushする）																									
実際の開発では、メインブランチ（master）から、作業用ブランチ（master#xxxxxなど）を作成し、PR（プルリクエスト）をGithubに上げることで、レビュー（確認作業）を行う。なぜブランチを分けるかというと、直接masterにコミットやpushをすると、そのまま本番環境に反映されて危険だから。一連の流れを確認しよう。																									
- masterから新規でブランチを切る（ブランチ名　master#jissen）																									
- master#jissenに作業ブランチを切り替える																									
git checkout -b master#jissen																									
- なんかてけとーにファイル作る																									
touch one.txt																									
- ステージファイルに上げる（addのこと）																									
git add -A																									
- コミットする																									
git commit -m "bbb"																									
- master#jissenにPushする																									
git push -u origin master#jissen																									
- Githubで確認																									
- 作業ブランチをmasterに切り替えておく																									
git checkout master																									
																									
### Git実践2（他人の変更をローカルに引っ張ってくる）																									
チーム開発では、他人のPRなどがマージされることで常にmasterブランチが進行していき、ローカルと差が生じて来る。																									
自分のローカルのファイルをリモートの状態に追従するように、その差をなくしていく必要がある。																									
- Github上でREADME.mdを編集→コミットする																									
- 上記の変更をローカルに取り込む（pull）																									
git pull origin master																									
- ローカルのREADME.mdファイルがリモートと一緒になることを確認																									
- ローカルでさらに変更を加える																									
- ステージファイルに上げる（addのこと）																									
git add -A																									
- コミット																									
git commit -m "ccc"																									
- プッシュ																									
git push																									
																									
### Git実践3（変更をmasterに合流させる）																									
Git実践1では、master#jissenというブランチでファイルの変更を行った。																									
この変更をmasterブランチに合体させると、テスト環境や、本番環境へ反映されることになる。																									
- masterブランチに切り替える（現在masterならそのまま）																									
git checkout master																									
- masterブランチを最新にする（リモートから取りなおす）																									
git pull origin master																									
- masterブランチにmaster#jissenブランチをマージする。																									
git merge master#jissen																									
- masterブランチをプッシュする																									
git push																									
- github上のmaster#jissenの変更内容が適用されていることを確認																									