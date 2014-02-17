#環境設定  

###開発環境のインストールについて
2011年度追加  

###インストールするもの  
* **Visual Stadio 2008**  
* **Python 2.5**  
* **Python Scripter**  
* **Iron Python**  
* **OpenCV 1.0**  
* **GLUT**  
* **GLFW**  

以上のものについては"インストールソフト"というフォルダにそれぞれのインストーラパッケージ等を用意してある．なお，Visual Stadioについてだけはディスクを使ってインストールを行う．  

***
####追加情報  
2011/1/10  
DirectXのインストールが必要(未確認)  
> 現在DirectXがインストールされていない環境での動作が確認されていない  

2011/1/7  
OpenCV 1.0ではインストーラからPathの設定を行わないので各自  
C:\Program Files\OpenCV\bin  
を設定してください．  
> OpenCV 1.0のデフォルトのインストール先はC:\Program Files\です．  
    
***  

###インストール方法  
* **Python 2.5, Python Scripter, Iron Python**  
インストーラパッケージを使って行う．  
Iron Pythonについてはインストール後，環境変数からPathを通す．  
(例 C:\Program Files\IronPython 2.6 を環境変数Pathに追加する)  

* **OpenCV**  
インストーラパッケージを使って行う．  
実際にOpenCVでプログラムするには以下の設定が必要．  

Visual Studioの設定  

「ツール(T)」→「オプション(O)」→「プロジェクト」→「VC++ディレクトリ」を選択します．「ディレクトリを表示するプロジェクト(S)」で「インクルードファイル」を選択し，以下を追加．  

    C:\Program Files\OpenCV\cv\include  
    C:\Program Files\OpenCV\cvaux\include  
    C:\Program Files\OpenCV\cxcore\include  
    C:\Program Files\OpenCV\otherlibs\highgui  
    
「ディレクトリを表示するプロジェクト(S)」で「ライブラリファイル」を選択し，以下を追加．  

    C:\Program Files\OpenCV\lib  
プロジェクトの設定  

プロジェクトを作成する度に設定する．  

「プロジェクト(P)」→「\*\*\*のプロパティ(P)」→「構成プロパティ」→「リンカ」→「入力」を選択．「追加の依存ファイル」に以下を追加．  

    cv.lib cxcore.lib cvaux.lib highgui.lib  

インストール時の注意点  

v1.0のヘッダファイルcvaux.hには間違いがあるらしく，そのままだとコンパイルできない．  

そのため，C:\Program Files\OpenCV\cvaux\include\cvaux.hの1137行目の  

    CvMemStorage*   storage;      /*storage for foreground_regions・/                \  

を  

    CvMemStorage*   storage;      /*storage for foreground_regions*/                \  

と訂正することでコンパイルできるようになる．  

* **GLUT**  
インストールソフトにあるglut.h, glut32.lib, glut32.dllを，下記のディレクトリにコピーする．  

|glut.h|glut32.lib|glut32.dll|  
|---|---|---|  
| C:\Program Files\Microsoft SDKs\Windows\v6.0A\Include\gl | C:\Prigram Files\Microsoft SDKs\Windows\v6.0A\Lib | C:\WINDOWS\system32 |  

* **GLFW**  
インストールソフトにあるglfw.h, glfw.lib, glfwdll.lib, glfwdll.dllを，下記のディレクトリにコピーする．  

|glfw.h|glfw.lib  glfwdll.lib|glfwdll.dll|  
|---|---|---|  
| C:\Program Files\Microsoft SDKs\Windows\v6.0A\Include\gl | C:\Program Files\Microsoft SDKs\Windows\v6.0A\Lib | C:\WINDOWS\system32 |  

###\* **注意事項**
qedit.hの498行目でdxtrans.hがインクルードできないビルドエラーについて  
上記のものを全てインストールしても最新SDKではDirectShowの仕様変更対応の為，qedit.hに以下の編集を行わなければビルドできない．  

498行目はライン全体のコメントアウト，その他はIDXEffect基底クラスからの派生を定義しない為のライン途中からのコメントアウト  

    // qedit.h  498: //#include "dxtrans.h"  
    // qedit.h  837: IDxtCompositor //: public IDXEffect  
    // qedit.h 1151: IDxtAlphaSetter //: public IDXEffect  
    // qedit.h 1345: IDxtJpeg //: public IDXEffect  
    // qedit.h 1735: IDxtKey //: public IDXEffect  

### **参考**  
わからない場合は以下のサイト等を参考にするとよい．  
<http://chihara.naist.jp/opencv/>  
<http://www.arakin.dyndns.org/gl_glutenv.php>  
<http://neigerhidebu.blog.shinobi.jp/Entry/450/>  
<http://sourceforge.jp/forum/message.php?msg_id=42631>  

