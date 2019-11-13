# AppD產品安裝

## Agent安裝 
- Java 1.6~11
- NgwinX 有支援
- 一般Linux的Machine Agent都含有JRE，若為AIX需自行安裝JRE1.8
- Docker Container環境不適用Machine Agent（其實Docker自行用OSS監控即可）
- 安裝Agent需要key，Key需要從管理網頁的Account取得
- 各單位的APM窗口有Account權限
- Agent為inprocess，ps -ef時可能只看得到一個java執行process
- 安裝
	- 設定環境變數！<Agent_Home>
	- 記得解壓縮時先建立根目錄(原壓縮檔內無根目錄)
	- 設定conf/controller-info.xml
	- 同一台主機只能共用一個controller-info.xml
	- node-name是唯一
	- 若同一台主機有多個tomcat，會吃到同一個controller-info.xml
	- 可在啟動agent.sh內overwrite參數即可
- Tomcat安裝
	- tomcat/bin新增 setenv.sh，內容為export javaagent
- Docker Container安裝
	- 不確定以下env是否是設定在JAVA_OPTS (此為JBoss範例)  
	
`JAVA_OPTS="${JAVA_OPTS} -Djboss.modules.system.pkgs=${JBOSS_MODULES_SYSTEM_PKGS}" `
`JAVA_OPTS="${JAVA_OPTS} -javaagent:/opt/AppServerAgent/javaagent.jar" `
`JAVA_OPTS="${JAVA_OPTS} -Dappdynamics.controller.hostName=${APPD_HOST}" `
`JAVA_OPTS="${JAVA_OPTS} -Dappdynamics.controller.port=${APPD_PORT}" `
`JAVA_OPTS="${JAVA_OPTS} -Dappdynamics.agent.accountName=${APPD_ACCOUNT_NAME}" `
`JAVA_OPTS="${JAVA_OPTS} -Dappdynamics.agent.accountAccessKey=${APPD_ACCESS_KEY}" `
`JAVA_OPTS="${JAVA_OPTS} -Dappdynamics.agent.applicationName=${APPD_APP_NAME}" `
`JAVA_OPTS="${JAVA_OPTS} -Dappdynamics.agent.tierName=${APPD_TIER_NAME}" `
`JAVA_OPTS="${JAVA_OPTS} -Dappdynamics.agent.reuse.nodeName=true"  `
`JAVA_OPTS="${JAVA_OPTS} -Dappdynamics.agent.reuse.nodeName.prefix=${APPD_NODE_PREFIX}" `
 
 
- 或者是使用(猜測應該是要以這為主，或者在ACM執行image的時候設定)： 
 	`–-Dappdynamics.controller.hostName=${APPD_HOST} `
 	`–-Dappdynamics.controller.port=${APPD_PORT} `
 	`–-Dappdynamics.agent.acountName=${APPD_ACCOUNT_NAME} `
 	`–-Dappdynamics.agent.accountAccessKey=${APPD_ACCESS_KEY}`
	`–-Dappdynamics.agent.applicationName=${APPD_APP_NAME}`
	`–-Dappdynamics.agent.tierName=${APPD_TIER_NAME}`
	`–-Dappdynamics.agent.reuse.nodeName=true`
	`–-Dappdynamics.agent.reuse.nodeName.prefix=${APPD_NODE_PREFIX} ` 

- 執行docker run
 payment
docker run --rm -it -p 8080:8080 \
-e APPD_HOST=192.168.200.57 \
-e APPD_PORT=8090 \
-e APPD_ACCOUNT_NAME=customer1 \
-e APPD_ACCESS_KEY=90253aee-ebf1-47ae-9abb-a14e25757360 \
-e APPD_APP_NAME=Payment \
-e APPD_TIER_NAME=AP \
-e APPD_NODE_PREFIX=AP \
payment

## Transaction analytics"啟用"

## 安裝問題排除

## 神
1. 聽說agent可以植入web、app裡面
2. Machine agent 的免費版只能檢測 CPU、RAM、InternetIO、DiskIO
3. VM有提供Controller License, License若過期, 改VM時間即可

## QA
1. OCSG C的應用
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTE2OTU3NDY3MywtNDI2Mjc3NTc4LDYyNj
MxNTA4MywtMTU1MTY5MDgwOSwxNDQxNDkwNjQ2LC0zNjc2NTE4
ODJdfQ==
-->