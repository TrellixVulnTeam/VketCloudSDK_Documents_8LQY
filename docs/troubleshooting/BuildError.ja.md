
# ビルドエラー
![BuildError](img/BuildError.jpg)

Build And Runでブラウザが起動しますが、稀にエラーによってコンテンツが表示されない場合があります。

この原因には、いくつかのケースが考えられますが、よくある原因は以下の通りです。

|  原因 |  対策  |
| ----   | ---- |
| アバターリストが空になっている | 最低1体以上、アバターを登録してください |
| .heoファイルの出力に失敗している | Unityのコンソールにエラー（赤文字）が出ていないか確認してください |
| キャッシュによる不具合 | Preferencesからキャッシュをクリアしてください |
| 必要なファイルが見つからない(404) | 後述の方法するエラーログから、404なファイルを確認し、VketCloudがサポートしないファイルなら変更する |

## エラーログを確認する

ビルドエラーの原因を調べるには、お使いのブラウザのコンソールをチェックします。

ブラウザによって方法は異なりますが、Google Chromeの場合は、右上の三点リーダーから **その他のツール > デベロッパーツール** を開きます。

![DeveloperTool](img/DeveloperTool.jpg)

必ずしもコンソールに出ている内容が、VketCloudのビルドエラーに直結しているとは限りませんが、赤字でエラーが出ている場合はその内容がビルドエラーの原因になっている可能性があります。

![DeveloperToolConsole](img/DeveloperToolConsole.jpg)

## インポートしたライブラリを確認する
Package Managerなどからインポートしたライブラリまたはスクリプトによってエラーの原因になっている可能性があります。

このケースでは後から追加した対象のライブラリをインポートし直すことで解消される場合があります。