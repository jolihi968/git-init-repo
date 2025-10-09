2025-10-07 17:35 #git #Spec-kit #github #SDD

https://github.com/github/spec-kit
教學影片[GitHub Spec Kit 操作指南](https://www.bilibili.com/video/BV1iSp4zVEPk/?vd_source=e6769a1180de1bec5841740d4dbfbbcf)

安裝 
1.   依賴 [UV](https://docs.astral.sh/uv/getting-started/installation/)  Python 套件和專案管理器    
``` powershell
	powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```
    
2. [Install Specify](https://github.com/github/spec-kit)
```
	uv tool install specify-cli --from git+https://github.com/github/spec-kit.git
```
3. init repo ( Repo 從零開始 建置資料夾 git init )
```
	specify init <PROJECT_NAME>
	specify check
```
4. 已存在的Repo 下載後複製
5. 執行 
	1.先定義憲法
		```  
		#vs code ide copilot
			/constiution  
			單位:資訊部 網站基建管理員 高度注意: 網路資安/系統資安/資料存取權限
		```	
		copilot 會進行一連串的憲法定義，並貫徹至其他檔案(plan/spec....)  [交付總結](交付總結.md)
	     
	
		```
4. chore/constitution-zh-TW PR 處理[合併PR](合併PR.md)
5. 
