# campus-chime
## 概要
キャンパスのチャイムをRaspberry Piで鳴らす

## 必要なもの
- Raspberry Pi 3 Model B
- Raspberry Pi用ACアダプター
- Raspberry Pi用ケース
- microSDカード（8GB以上）
- スピーカー

## 準備
1. [Raspberry Pi OS](https://www.raspberrypi.org/software/)をSDカードに入れてRaspberry Piに差し込む
1. /home/pi/chimeディレクトリを作成し、chime.mp3（チャイム音源）を格納する
1. mpg321コマンドを使えるようにする
```
sudo apt-get install mpg321
```
4. atコマンドを使えるようにする
```
sudo apt-get install at
```
5. 平日0時にシェルスクリプトを実行するためにcronを設定する
```
0 0 * * 1, 2, 3, 4, 5 /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/progedu/campus-chime/master/chime.sh)"
```
