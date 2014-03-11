#Visual Studio 2012対応  

注)このページはVisual Studio 2012に対応させる際の作業ログである．  
最終的には整理されてソースツリー内にドキュメントを配置する．  


ダウンロード・インストールするもの  

* [Microsoft Visual Studio Express 2012 for Windows Desktop](http://www.google.com/url?q=http%3A%2F%2Fwww.microsoft.com%2Fvisualstudio%2Fjpn%2Fproducts%2Fvisual-studio-express-for-windows-desktop&sa=D&sntz=1&usg=AFrqEzfSRWncB4YlV7k4Qlff-6e-yrsOSw)  
    * for Windows 8は使えない  
* [ZeroC Ice3.5](http://www.google.com/url?q=http%3A%2F%2Fwww.zeroc.com%2Fdownload.html&sa=D&sntz=1&usg=AFrqEzf-QFGZTZoYjhriFdwV_ebLgVU8Hw)  
    * インストール直後の状態はVS2010用のファイルがlibとdllに入っているため，ファイルを移動するかPathやライブラリパスを適宜変更する  
    
ダウンロード・ビルドするもの  
* [Boost 1.54 ソース](http://www.google.com/url?q=http%3A%2F%2Fwww.boost.org%2Fusers%2Fhistory%2Fversion_1_54_0.html&sa=D&sntz=1&usg=AFrqEze20vEm8PhvTx9FYBGf5Vx1bb5eEA)  
* [Qt 4.8.5 ソース](http://www.google.com/url?q=http%3A%2F%2Fdownload.qt-project.org%2Fofficial_releases%2Fqt%2F4.8%2F4.8.5%2Fqt-everywhere-opensource-src-4.8.5.zip&sa=D&sntz=1&usg=AFrqEzezi3yQbHW97EXO0i9d1RZtZnzCJQ)  
* OpenCV 2.4.6.1　ソース  

Boostビルド手順  

* 「VS2012 x86 Native Tools コマンド　プロンプト」を開く  
* Boostを展開してそのディレクトリに移動(cd)  

    > bootstrap.bat  
    > b2 --prefix=c:\boost install  

* prefixはインストール先．適宜変更すること  
* 環境変数Boost_ROOTをC:\boost等インストール先に合わせて設定すること  
* インストール先 C:\devel\boost\libに libboost\*\*\*\*\*vc110\*\*\*.libという名前のファイルがたくさんできていることを確認する  
* 終わったら展開したソースは削除して良い  

Qtビルド手順(完全版)  

* コントロールパネルでロケールを「英語(米国)」に変更する．Windowsを再起動  
* Qtを展開してC:\Qt4.8.5に移動，名前を変える  
* <http://stackoverflow.com/questions/12113400/compiling-qt-4-8-x-for-visual-studio-2012/14928303#14928303>からHashSet.hをダウンロード．  
* ディレクトリのsrc\3rdparty\webkit\Source\JavaScriptCore\wtfにあるHashSet.hと置き換える  
* 「VS2012 x86 Native Tools コマンド プロンプト」を開く  


    > cd C:\Qt4.8.5  
    > set QT_HOME=C:\Qt4.8.5  
    > set PATH=%QT_HOME%\bin;%PATH%  
    > configure -mp -opensource -nomake demos -nomake examples -platform win32-msvc2012  
    > (ライセンスを確認する)  
    > nmake(数時間かかる)  
    
* 終わったら nmake cleanして，srcディレクトリを削除するとディスク使用量を減らすことができる  
Qtビルド手順(簡易版)  

* おそらく使わない機能を省いた簡易版．HashSet.hの修正が不要  
* コントロールパネルでロケールを「英語(米国)」に変更する．Windowsを再起動  
* Qtを展開してC:\Qt4.8.5に移動，名前を変える  
* 「VS2012 x86 Native Tools コマンド プロンプト」を開く  
* configureのコマンドを下記のようにする．それ以外は上記と同じ手順でビルド．  


    > configure -mp -opensource -nomake demos -nomake examples -no-script -no-scripttools -no-webkit -no-qt3support -platform win32-msvc2012  
    
OpenCVビルド注意  
* CMakeでWITH_CUDAをオフにする  
プリコンパイル済みヘッダの問題  
* src/cmake_modules/PrecompiledHeader.cmake中のコンパイルオプションに/Zm200を追加  

zipファイルの載せ方が分かり次第更新
