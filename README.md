# ロボットシステム学　課題1
先生が講義用に作ってくださったデバイスドライバを少し改変したものです。
## 概要
交通信号機を再現しました。  
歩行者用信号が赤に変わった後、車両用信号も赤に変わります。
## 動作環境
- Ubuntu 20.04
- Raspberry Pi 4 Model B
## 使用したもの　
- LED(赤×２、青×２、黄×１)
- 抵抗(220Ω)　×５
- ブレッドボード
- ユニバーサル基板
- 接続用ケーブル

## 使用方法
### 接続
GPIO、抵抗、LED、GNDの順につなぎます。  
対応するGPIOとLEDの組み合わせは以下の通りです。  
＜歩行者用＞　　青　GPIO25  
　　　　　　　　赤　GPIO24  
＜車両用＞　　　青　GPIO23  
　　　　　　　　黄　GPIO22  
　　　　　　　　赤　GPIO21  
### 実行
```
git clone https://github.com/masakifukuchi/robosys_device_driver.git  
cd myled
make
sudo insmod myled.ko
sudo chmod 666 /dev/myled0
```
青点灯  
```
echo 1 > /dev/myled0
```
青点滅から赤へ  
```
echo 2 > /dev/myled0
```
全消灯  
```
echo 0 > /dev/myled0
```

## 動画
https://youtu.be/YxAS4ktgqR0
## ライセンス
[GNU General Public License v3.0](https://github.com/masakifukuchi/robosys_device_driver/blob/main/LICENSE)
