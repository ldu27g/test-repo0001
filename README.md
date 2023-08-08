

■NTTD様うインフラ資料の確認
全資料拝見しました。※こちらの資料はまだ全量では無いように見受けられました。
拝見した範囲で気になった点を以下にご報告いたします。（※吹き出しにする程の内容ではないためこちらに記載させていただきます、）

・「08_サーバ設計.pptx」- 「xx.コンテナインスタンスタイプ 」(2ページ目)
「prometheusで監視するためprocess-exporterをインストールする」とありますが、exporterはPODではなくdaemonとして稼働させるのでしょうか？
また、node-exporterによるリソース監視はprometheusでは行わないのでしょうか？

・「14_可用性設計.pptx」
ストレージとコンテナの可用性に関する記載がございますが、ノード障害に関する記載がございません。
Multi-AZ構成に関する記載は別の章に記載されるのでしょうか？


■構成図差分の確認
Management/Data subnetを廃止してPrivate subnetに統一し、各コンポーネントの配置を変えたものと認識しました。
以下、１点気になった点がございますので確認させてください。
・各環境（本番含む）のEKSからNat Gateway経由でインターネットに抜ける経路が追加されていますが、この経路の用途は何でしょうか？
　また、本番リリース後も存在する経路でしょうか？



```

VM Name,Host,IP Addresses,Cores,Memory Capacity,Storage,CPU Usage,Memory Usage,Controller Read IOPS,Controller Write IOPS,Controller IO Bandwidth,Controller Avg IO Latency,Backup and Recovery Capable,Flash Mode
"rizad-proxy","rizadntx03/AHV","10.205.147.212",2,"2 GiB","8.5 GiB / 124.27 GiB","0.17%","18.84%","0","0","0 KBps","5.08 ms","Yes","No"
"syslog","rizadntx03/AHV","10.205.147.208",2,"5 GiB","164.71 GiB / 700 GiB","4.15%","97.49%","0","7","46 KBps","1.44 ms","Yes","No"
"windows test server dev 01","rizadntx03/AHV","10.205.147.205 | 10.205.146.205",2,"4 GiB","22.19 GiB / 40 GiB","24.12%","70%","24","8","1.93 MBps","3.3 ms","Yes","No"
"rizadrls01","rizadntx01/AHV","10.205.146.225",2,"4 GiB","21.39 GiB / 24.27 GiB","0.35%","93.94%","0","0","0 KBps","3.47 ms","Yes","No"
"rizadjdv01","rizadntx03/AHV","10.205.146.224",2,"4 GiB","65.05 GiB / 84.27 GiB","0.33%","53.15%","0","0","0 KBps","1.05 ms","Yes","No"
"rizaddxc01","rizadntx01/AHV","10.205.146.223",2,"4 GiB","8.2 GiB / 24.27 GiB","0.05%","96.7%","0","0","0 KBps","0 ms","Yes","No"
"rizadapl01","rizadntx02/AHV","10.205.146.222",2,"4 GiB","23.2 GiB / 24.27 GiB","0.79%","97.18%","0","0","0 KBps","3.82 ms","Yes","No"
"rizadhub02","rizadntx01/AHV","10.205.146.217 | 10.205.147.217",2,"4 GiB","6.77 GiB / 8 GiB","0.18%","47.95%","0","0","0 KBps","3.4 ms","Yes","No"
"rizadhub01","rizadntx01/AHV","10.205.146.216 | 10.205.147.216",2,"4 GiB","6.73 GiB / 8 GiB","0.22%","68.55%","0","0","0 KBps","2.82 ms","Yes","No"
"rizadweb02","rizadntx03/AHV","10.205.146.215 | 10.205.147.215",1,"4 GiB","20.77 GiB / 84.27 GiB","0.3%","93.17%","0","0","0 KBps","5 ms","Yes","No"
"rizadweb01","rizadntx03/AHV","10.205.146.214 | 10.205.147.214",1,"4 GiB","40.13 GiB / 84.27 GiB","0.37%","90.12%","0","0","0 KBps","1.02 ms","Yes","No"
"rizadbot01","rizadntx01/AHV","10.205.146.213 | 10.205.147.213",2,"4 GiB","169.07 GiB / 220 GiB","2.55%","95.88%","0","0","21 KBps","6.2 ms","Yes","No"
"rizaddoc01","rizadntx02/AHV","10.205.146.211 | 10.205.147.211",4,"12 GiB","130.4 GiB / 220 GiB","3.93%","96.96%","4","3","260 KBps","18.28 ms","Yes","No"
"rizadhul02","rizadntx02/AHV","10.205.146.210 | 10.205.147.210",2,"2 GiB","3.38 GiB / 140 GiB","2.99%","44.35%","0","0","3 KBps","1.4 ms","Yes","No"
"rizadhul01","rizadntx02/AHV","10.205.146.208 | 10.205.147.209",2,"2 GiB","3.42 GiB / 140 GiB","26.23%","49.48%","0","0","2 KBps","0.96 ms","Yes","No"
"rizadads02","rizadntx03/AHV","10.205.146.207 | 10.205.147.207",2,"4 GiB","32.18 GiB / 40 GiB","3.11%","32.25%","0","1","7 KBps","1.94 ms","Yes","No"
"rizadads01","rizadntx01/AHV","10.205.146.206 | 10.205.147.206",2,"4 GiB","18.05 GiB / 40 GiB","2.98%","31.87%","0","2","18 KBps","0.78 ms","Yes","No"
"rizadhul00","rizadntx01/AHV","10.205.146.204",2,"2 GiB","2.67 GiB / 140 GiB","0.05%","32.41%","-","-","-","-","Yes","No"
"rizadocw04","rizadntx02/AHV","10.205.146.203 | 10.205.147.203",4,"6 GiB","55.21 GiB / 150 GiB","17.52%","86.12%","0","5","30 KBps","2.83 ms","Yes","No"
"rizadocw03","rizadntx01/AHV","10.205.146.202 | 10.205.147.202",4,"8 GiB","86.35 GiB / 270 GiB","39.23%","97.32%","0","3","36 KBps","1.14 ms","Yes","No"
"rizadocw02","rizadntx03/AHV","10.205.146.201 | 10.205.147.201",4,"8 GiB","62.98 GiB / 270 GiB","37.73%","97.48%","0","13","95 KBps","1.41 ms","Yes","No"
"rizadocw01","rizadntx01/AHV","10.205.146.200 | 10.205.147.200",4,"8 GiB","56.06 GiB / 270 GiB","35.5%","97.56%","9","5","358 KBps","0.79 ms","Yes","No"
"rizadoci03","rizadntx01/AHV","10.205.146.197 | 10.205.147.197",4,"14 GiB","283.04 GiB / 300 GiB","63.12%","87.34%","0","67","1.65 MBps","3.8 ms","Yes","No"
"rizadoci02","rizadntx03/AHV","10.205.146.196 | 10.205.147.196",4,"14 GiB","283.67 GiB / 300 GiB","49.88%","96.09%","0","5","329 KBps","8.96 ms","Yes","No"
"rizadoci01","rizadntx02/AHV","10.205.146.195 | 10.205.147.195",4,"14 GiB","282.4 GiB / 300 GiB","58.17%","99.15%","0","71","4.61 MBps","17.12 ms","Yes","No"
"rizadocm03","rizadntx02/AHV","10.205.146.194 | 10.205.147.194",4,"8 GiB","46.11 GiB / 100 GiB","37.56%","93.93%","0","41","419 KBps","1.42 ms","Yes","No"
"rizadocm02","rizadntx03/AHV","10.205.146.193 | 10.205.147.193",4,"8 GiB","78.27 GiB / 100 GiB","31.53%","96.82%","0","31","365 KBps","2.74 ms","Yes","No"
"rizadocm01","rizadntx02/AHV","10.205.146.192 | 10.205.147.192",4,"8 GiB","55.27 GiB / 100 GiB","32.41%","96.09%","0","36","414 KBps","1.39 ms","Yes","No"
"cebtos7_base","","",2,"4 GiB","1.24 GiB / 20 GiB","-","0%","-","-","-","-","Yes","No"
"ocp_base_w_test","","",2,"2 GiB","1.31 GiB / 20 GiB","-","0%","-","-","-","-","Yes","No"
"rizadads01_base","","",2,"4 GiB","10.08 GiB / 40 GiB","-","0%","-","-","-","-","Yes","No"
"rizadocw05","","",4,"6 GiB","49.55 GiB / 150 GiB","-","0%","-","-","-","-","Yes","No"
"ocp_rhel7_base","","",2,"2 GiB","2 GiB / 20 GiB","0%","0%","-","-","-","-","Yes","No"
"test-win2016","","",2,"4 GiB","16.73 GiB / 26.98 GiB","-","0%","-","-","-","-","Yes","No"
"windows test server verify 01","","",2,"4 GiB","10.59 GiB / 40 GiB","0%","0%","-","-","-","-","Yes","No"
"windows test server dev 02","","",2,"4 GiB","18.24 GiB / 40 GiB","-","0%","-","-","-","-","Yes","No"
"rizadsat01","","",4,"20 GiB","10.96 GiB / 622.91 GiB","0%","0%","-","-","-","-","Yes","No"
"rhel7 test server","","",2,"2 GiB","2.62 GiB / 20 GiB","-","0%","-","-","-","-","Yes","No"
"rizadcob01","","",2,"2 GiB","8.43 GiB / 44.3 GiB","0%","0%","-","-","-","-","Yes","No"

```
