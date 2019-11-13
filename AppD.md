1. AppDynamics 可監控系統類型 
	( 如App、後端Server等?)
2. 應用系統如何配合監測
	( 埋碼、plugin等?)
3. 可監測哪些方面效能 
4. AppDynamics 操作使用方式
	( 下載Local、遠端啟動?)

------------
0. Cisco APM License    
1. 每年一次免費APM健檢(數分資訊處)
2. QA就可以先監控, 早期發生早期解決(效能問題、瓶頸)
3. Java、.NET、PHP
------------
# 專有名詞
1. Node型態
	Backend node : 無法識別的它端系統
2. Health rules
	預設6個，可自訂
# Snapshot
## 為每次交易的快照
可查看： 
1. stackTrace
2. method、function時間
3. SQL指令&時間
	-- 資安issue (若用dynamic "?" 則不會show出來 )
4. backend時間(意指不受控之他端AP的回應時間)
5. http param、cookie、session資料
	-- 資安issue (若用???? 沒聽清楚, 但可防護)
6. 每個method input、output資料
	-- 資安issue (若用???? 沒聽清楚, 但可防護)
7. 交易錯誤訊息(撈Log超難! 透過監控系統撈...)

## 交易流程圖
實線 : 同步交易
虛線：非同步交易（丟了就走，不管。如：MQ）
Drill Down： 
	若有星號代表快照多次 
	點進去可以看到 
	1. 程式呼叫流程(stackTrace，包含行號)
	2. Exit Calls (如 JDBC)，可呈現SQL指令、資料庫、metadata
	3. Drill Down 可以再Drill Down

## 自動產生快照
1. 緩慢、錯誤、不正常 ( 預設6個Health rule )
2. 自定義Health rule violation
3. 手動側錄
4. monitor level=development 調整 ( 可以針對某幾個Transaction進行無漏式快照 )

# Controller & Agent
1. 防火牆的開法都是1-way，不會互連
2. App Ahent ( 核心 )
3. Machine Agent ( CPU、RAM、Disk...等等較不重要資訊 )
4. event service ( 資料分析用。一般都是用平均時間來計算效能，若需要逐筆資料分析，則需要安裝event service。該工具可以抓出某一筆用戶交易的詳細資料，粒度較細，但只有90天 )
5. 需要Flash外掛( 4.5.2 )

# Controller 安裝
1. RHEL6-7、CentOS6-7、Ubuntu14&16
	(RHEL目前不支援)
2. Windows Server 2008、2012、2016(建議)
3. 皆x64

## Controller profile
1. linux 需安裝 net-tools & lib-aio(for MySQL)
2. nofile -> 65535
3. Controller資料庫一定要安裝在Controller 的主機上

# Agent 類型
1. App agent
2. Machine agent
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEzNDQxNDIwODRdfQ==
-->