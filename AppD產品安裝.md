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
	- 記得解壓縮時先建立根目錄(原壓縮檔內無根目錄)
	- 設定conf/controller-info.xml

## Transaction analytics"啟用"

## 安裝問題排除
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTg5OTYyMTg1NSwxMDczMzA5OTA1LC04Mj
EzNjY4MzAsLTE5NTUxMDMxNDIsLTcxNjEzMzk3NywxNDc0MzQ5
Njg1XX0=
-->