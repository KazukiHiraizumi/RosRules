# ROS設計ガイドライン
## パラメータ  
1. ケーススタディ  
標準的なパラメータ空間は、以下のようなyamlファイルを展開したものとする
~~~
config:
  dashboard:
    launch_ycam:
      file: ycam3sxga_m.launch
    launch_rsock:
      file: ur.launch
      args:
        mc: ur5
        address: "172.16.58.20"
  searcher:
    solver: km1_solver
    scenes: ["surface"]

cropper:
  cropR: 0.2
  cropZ: 0.59
  mesh: 0.001
searcher:
  distance_threshold: 1.5
  icp_threshold: 5.0
  maxnn_feature: 100
  maxnn_normal: 30
~~~
2. 構成パラメータ  
config:以下のパラメータ空間には、機能単位(ノードまたはパッケージ。上例ではdashboardとsearcherが該当)の内部構造および外部インタフェースの構造を決める、固定的なパラメータを与える。これらのパラメータはノードの初期化時に一度だけ読み込む。
3. 調整パラメータ  
ルート以下空間のconfig以外(上例ではcropperとsearcherが該当)には、機能単位の調整パラメータを与える。

## トピック
## トピックハンドシェーク
