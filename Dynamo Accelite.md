#Dynamo Accelite  

ソフトウェアの現状  

システム構成図  
![システム構造図](https://06a1993a-a-62cb3a1a-s-sites.googlegroups.com/site/citbrainsi/sekkeisiryou/dynamo-accelite/accelite_system.png?attachauth=ANoY7crtsnk6VeHLTraT8Eqkqdq6LCqFDofmB1rQEvj6BtOxNad3BZwkuaZFmQX5nHn41nsM5aAzAcz_ihocqPMh_6Md1u8l_zlSfmk9ZlztOcjhVo34yvLjNegM8ZmRJk-wgEfrBrJ8jGEEvHU2_Sib1BA2tIQKJJ3ZLBE7TCVC0hqa_L3ZDqzJEe2jwJ5TualEtFBkCcsD_t1u1T3o0pa62UJX_zuKtjcEC9FsQorwER4kOZ7-A1fWL6tEuimJ2ztIsY37Vh92&attredirects=0)  

###主なプログラム  

  *歩行制御:hr42_win  
  *認識ライブラリ:HPL(ファイルは_env.pydというダイナミックリンクライブラリ)  
  *ステータス表示・色調整:HPLStatusUI
  *歩行などのコマンド送信ツール:QHuSendCom  
  *初期姿勢調整ツール:PoseInitializer  
  
###使い方(実機)  

  *ホームディレクトリのfor2012/src以下にプログラムがある  
  *hr42_winを起動する(電源オンで自動起動するように設定されている機体もある)  
    *例) >hr42_win  
  *pythonで戦略プログラムを起動する  
    *例) >python fw3.py  
  *色調整する  
    *例) >python cgi.py(何もしないプログラムを起動しておいてから)  
    *  ) >./HPLStatusUI  
    
###使い方(シミュレータ)  
  *Subversionで下記のURLをチェックアウトする  
    *http://www.hayashibara-lab.it-chiba.ac.jp/robocup-svn/branches/for2012  
  *for2012のdocに設定ドキュメントがある  
    *DevEnvSetup.txtを呼んで開発環境をインストールする  
      *先にVisual Studio 2008とSP1をインストールしておくこと  
    *CソースからV-REP上のDynamoを動かす方法.txtを呼んでシミュレータ環境をインストールして使ってください  
  *とりあえずシミュレータが使えればいい人は，上記開発環境の設定をしなくても，WebDAVからhttp://www.hayashibara-lab.it-chiba.ac.jp/robocup-dav/software/V-REP/simulator_binary.zip  
  
