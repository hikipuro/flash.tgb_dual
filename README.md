# TGB Dual を Flash に移植してみた

TGB Dual Ver. Vol.8''' を Flash に移植してみました。  
http://gigo.retrogames.com/

動作確認用
http://hkpr.info/flash/tgb_dual/


概要
-----

* Flash Player 11 以降でないと動かないと思います。
* Flash Player が動作する環境であれば、 Windows 以外でも動くと思います。
* FlasCC 1.0.1 を使って、配布元のコードの Windows 依存部分以外を、ほぼそのままビルドしています。
* GB, GB Color のソフトが動作します。
* サウンドも再生されます。 Flash の再生環境によってはノイズが乗る可能性もありますので、ヘッドフォン等で再生される場合は気を付けてください。
* Core i5 4 Core の環境で、 CPU 使用率 10 % から 15 % で動作します。


今のところ対応していない機能
-----------------------------

* セーブできません。後々修正したいと思います。
* リアルタイムクロック、加速度センサー等を使用するソフトは動きません。
* 通信機能がありません。
* 各種設定画面がありません。
* 2 画面同時に動かす機能がありません。


FlasCC + FlashDevelop 環境でのビルド方法
-----------------------------------------

* FlasCC_1.0.1/run.bat から cygwin を起動する
* export LANG=C  
を入力する
* ソースコードの入っているディレクトリ (tgb_dual_8_3_src) に cd で移動
* make FLASCC="/path/to/FlasCC_1.0.1/sdk" FLEX="/path/to/flex_sdk_4.6/"  
で make が通ると思います
* make 後、 build ディレクトリに SWC ファイルが作成されます
* FlashDevelop で flash ディレクトリを開き、出力された SWC ファイルへのパスを通してビルドしてください。


動作確認環境
-------------

* FlashDevelop 4.3.0
* Flex SDK 4.6
* Flash Player 11
* FlasCC 1.0.1


ライセンス
-----------

本家 TGB Dual のライセンスが GPL ですので、おそらく GPL になります。


