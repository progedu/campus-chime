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
2. nstudentsにWiFi接続する
3. BluetoothのGUI設定ツールをインストールする（なくても良さそうだが、不具合起きた時に現場が対応しやすいように入れておく）
```
sudo apt-get install -y blueman
```
4. Bluetoothスピーカー（S1 Pro）を接続する
5. /home/pi/chimeディレクトリを作成し、chime.mp3（チャイム音源）を格納する
6. mpg321コマンドを使えるようにする
```
sudo apt-get install mpg321
```
7. atコマンドを使えるようにする
```
sudo apt-get install at
```
8. 平日0時にシェルスクリプトを実行するためにcronを設定する
```
XDG_RUNTIME_DIR=/run/user/1000
0 0 * * 1, 2, 3, 4, 5 /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/progedu/campus-chime/master/chime.sh)"
```
