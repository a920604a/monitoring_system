
1. cAdvisor：收集 Container 資料
2. Node Exporter：收集運行的機器（Node）的資料
3. Prometheus：採集 cAdvisor、Node Exporter 與 Grafana 的 Metrics
4. Tempo：收集 Grafana 送出的 Trace 資訊
5. Nginx：單純作為被監測的 Container/ Grafana 服務的入口，擔任 Load Balancer 將 Request 分散到 Grafana Instance 上
6. Grafana：視覺化與告警的核心組件
Grafana Renderer：搭配 Alerting 截取 Panel 圖片。

7. Postgres：Grafana Instance 共用的資料庫
8. Redis：Grafana Instance 用來同步告警狀態的資料庫



refer to 
1. https://github.com/blueswen/grafana-zero-to-hero
2. https://github.com/blueswen/observability-ironman30-lab


DB Plugins
https://github.com/blueswen/grafana-zero-to-hero/tree/main/04-datasource/03-db
trigger event 
https://github.com/blueswen/grafana-zero-to-hero/blob/main/06-alerting/02-trigger-event/readme.md


![](https://github.com/blueswen/grafana-zero-to-hero/raw/main/02-best-practice/lab-arch.png)




### 使用者角色
- **Admin (管理者)**: 負責設定和管理數據源，擁有所有權限。
- **Editor (編輯者)**: 可以創建和編輯 Dashboards、設置告警等，並使用 Explore 功能進行查詢。
- **Viewer (瀏覽者)**: 只能查看其他人創建的 Dashboards，無法進行修改。

### 團隊與組織
- **Team**: 每個 User 也可以同時屬於多個 Team。設定 Team 可以操作哪些內容，然後再把 Team 標記在不同 User 身上。
- **Organization (多租戶)**:Multi Tenant 是平台型服務中特別強調的一個功能，目的是希望不同組別的使用者在同一平台上時不會看到彼此的資料，



### 安裝與配置
1. **導入 Dashboards**
   - 在 **Grafana** 中點擊左側側邊欄的 `+` > `Import`。
   - 在 **Import via Grafana.com** 欄位中輸入以下 Dashboard ID，並點擊 Load：
     - Node Exporter for Prometheus Dashboard based on 11074: 15172
     - Node Exporter Full: 1860
     - cAdvisor Exporter: 14282
     - Prometheus Blackbox Exporter: 7587

2. **配置數據源**
   - 在 **Dashboard** 加載頁面中，選擇已經添加的 **Prometheus** 數據源，並點擊 **Import**。

3. **建立資料夾結構**
   ```bash
   mkdir storage/
   mkdir storage/grafana-data
   mkdir storage/prometheus_data
   ```


- alert manger
- nginx
- blackbox to monitor http, tcp, icmp
    https://ithelp.ithome.com.tw/articles/10223175
- grafana
- data flow
- add app scrape
- docker config