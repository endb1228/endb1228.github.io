---
title: 이미지 관련 api 정리
author: Jonghyeok Lee
date: 2022-06-25
category: javascript
layout: post
---

이미지 관리가 좀 복잡할 것 같아서 따로 정리.

1. front  
	- 이미지 오브젝트  
	[id], [file]로 구성.  
	이미지는 [gym] 오브젝트 안에 저장.  
	이미지 array에 넣어서 사용.  
	변경이 모두 update로 한 번에 처리되므로 정해진 기준에 따라 CUD 중 어떤 방식으로 처리할지를 결정.
	
	- create  
	[id]는 null로 설정하여 array의 맨 뒤에 추가.  
	최대 10장의 이미지까지 추가 가능.  

	- read  
	그냥 받으면 됨.
	  
	- update  
	순서 변경 가능. (우선순위는 낮음)  
	동일한 [id]에 대해 이미지 파일만 변경되는 것은 허용하지 않으므로  
	[id]는 동일하고 array 내에서 순서만 변경하도록 하며,  
	요청을 보낼 시 수정 전에도 있는 id의 경우 [file]을 null로 설정 

	- delete  
	이미지 array에서 해당 이미지를 제거.
	
	- 위와 같이 CRUD로 나눌 수 있지만, 모든 변경은 마지막에 submit시 이루어지므로 CUD는 모두 update로 처리.  

	
2. back
	- 이미지 오브젝트
	[id], [gym], [order]로 구성.  
	이미지는 [gym]과 many to one으로 매핑되어 있음.  
	이미지 파일의 이름은 [id]로 설정.  
	front와는 다르게 [order] 변수가 추가되어 front에서 이미지를 로드할 때 어떤 순서로 이미지를 제공할 지 결정.  
	변경이 모두 update로 한 번에 처리되므로 정해진 기준에 따라 CUD 중 어떤 방식으로 처리할지를 결정.

	- create  
	[id]가 null인 이미지가 추가될 경우 create로 간주함.  
	추가된 이미지는 storage에 저장.
	
	- read  
	저장된 이미지를 order에 따라 form-data에 담아서 보냄.  
	
	- update  
	[id]가 있는 이미지(의 순서)가 변경될 경우 update로 간주함.  
	  
	- delete  
	array에 없는 [id]를 가진 이미지는 delete로 간주.  
	삭제된 이미지는 storage에서도 삭제.  