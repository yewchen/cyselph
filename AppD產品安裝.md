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
`
`

## Transaction analytics"啟用"

## 安裝問題排除
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE4NDcwMTY4NjYsMjU5Njc1MjI3LDg4OT
M5NjYxMiwxMDczMzA5OTA1LC04MjEzNjY4MzAsLTE5NTUxMDMx
NDIsLTcxNjEzMzk3NywxNDc0MzQ5Njg1XX0=
-->