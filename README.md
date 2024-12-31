
1. cAdvisor：收集 Container 資料
2. Node Exporter：收集運行的機器（Node）的資料
3. Prometheus：採集 cAdvisor、Node Exporter 與 Grafana 的 Metrics
4. Tempo：收集 Grafana 送出的 Trace 資訊
5. Nginx：單純作為被監測的 Container/ Grafana 服務的入口，擔任 Load Balancer 將 Request 分散到 Grafana Instance 上
6. Grafana：視覺化與告警的核心組件
Grafana Renderer：搭配 Alerting 截取 Panel 圖片

7. Postgres：Grafana Instance 共用的資料庫
8. Redis：Grafana Instance 用來同步告警狀態的資料庫


外部其他資料庫的service 
外部其他service Exporter

refer to 
1. https://github.com/blueswen/grafana-zero-to-hero
2. https://github.com/blueswen/observability-ironman30-lab


DB Plugins
https://github.com/blueswen/grafana-zero-to-hero/tree/main/04-datasource/03-db
trigger event 
https://github.com/blueswen/grafana-zero-to-hero/blob/main/06-alerting/02-trigger-event/readme.md


![](https://github.com/blueswen/grafana-zero-to-hero/raw/main/02-best-practice/lab-arch.png)



Admin：管理者，可以設定 Data Source
Editor：編輯者，可以建立 Dashboard、Alerting 等，並使用 Explore 功能
Viewer：瀏覽者，只能瀏覽別人建立的 Dashboard

Team : 每個 User 也可以同時屬於多個 Team。設定 Team 可以操作哪些內容，然後再把 Team 標記在不同 User 身上。
Organization : Multi Tenant 是平台型服務中特別強調的一個功能，目的是希望不同組別的使用者在同一平台上時不會看到彼此的資料，




安裝適合 Node Exporter 和 cAdvisor 的 Dashboards
導入 Grafana Dashboard

點擊左側側邊欄的 + > Import。
在 Import via Grafana.com 欄位中輸入以下 Dashboard ID，並點擊 Load：


Node Exporter for Prometheus Dashboard based on 11074 : 15172
Node Exporter Full: 1860
cAdvisor expoeter: 14282
Prometheus Blackbox Exporter : 7587

配置數據源

在 Dashboard 加載頁面中，選擇之前添加的 Prometheus 數據源。
點擊 Import。

mkdir storage/ storage/grafana-data storage/prometheus_data

## TODO
- alert manger
- nginx
- blackbox to monitor http, tcp, icmp
    https://ithelp.ithome.com.tw/articles/10223175
- grafana
- data flow
- add app scrape
- docker config