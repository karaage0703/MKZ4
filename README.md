MKZ4
====

ワイルドミニ四駆改造キット「MKZ4」用のマニュアル、サンプルプログラム、回路図などをまとめたレポジトリです。

## Attention
これは「MKZ4」のリポジトリをベースにkaraage0703が独自にサーボモータのキャリブレーション機能を追加したものになります

## Folder structure
**Calibration_Tool**  ：キャリブレーションツール。  
**Cerevo_MKZ4** ：サンプルプログラム。  
**custom** ：改造用のプログラムや、オリジナルボディのSTLデータ。  
**manual** ：キット付属のマニュアル。  
**schematic**:回路図。  

## Requirement
サンプルプログラムの使用にはVer1.6.8の[Arduino IDE](https://www.arduino.cc/en/Main/OldSoftwareReleases#previous)と[ESP8266 core for Arduino](https://github.com/esp8266/Arduino)のインストールが必要です。  
インストールの説明はそれぞれのURLを参照してください。

## Demo
/Cerevo_MKZ4/Cerevo_MKZ4.inoがサンプルプログラムになります。  
ESP8266を追加したArduino IDEでビルドしてください。  
※ボードマネージャーのesp8266のVerは2.2.0で動作確認をしています。  

## Calibration
Calibration_Tool/Calibration_Tool.inoがキャリブレーションツールのプログラムになります。プログラミングを書き込み、MKZ4で電池で動作させた状態で、PCとMKZ4をシリアルケーブルで接続します（シリアルの方は、電源ピンは接続しないでください）。
Arduino IDEのシリアルモニタ機能でサーボモータモータの角度を指定できます。サーボモータのニュートラル角度、右のステアリング角度、左のステアリング角度を数字を少しずつ変えながら確認してください。最初は90から始めるのがよいと思います。

キャリブレーションツールで確認した値を、/Cerevo_MKZ4/Cerevo_MKZ4.ino に書き込むとサーボモータの位置を調整できます。52行目が左のステアリング角度、53行目が右のステアリング角度、54行目がサーボモータのニュートラル角度です。例えば、それぞれ`90` `130` `110` だった場合は以下のように書き換えることになります。

```
#define servo_left    90
#define servo_right   130
#define servo_center   110
```
後は、Cerevo_MKZ4.inoをMKZ4に書き込むとキャリブレーション完了です。

## Licence

[BSD 3-Clause License](https://opensource.org/licenses/BSD-3-Clause)

