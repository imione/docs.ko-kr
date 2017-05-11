---
title: "Cert2spc.exe(SPC 테스트 도구) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Cert2spc.exe"
  - "인증서, 소프트웨어 게시자 인증서"
  - "소프트웨어 게시자 인증서"
  - "SPC 테스트 도구"
  - "SPC"
ms.assetid: be434d7d-9c0d-46e7-8392-58a9b542d11d
caps.latest.revision: 21
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 21
---
# Cert2spc.exe(SPC 테스트 도구)
SPC\(소프트웨어 게시자 인증서\) 테스트 도구를 사용하면 하나 이상의 X.509 인증서에서 SPC를 만들 수 있습니다.  Cert2spc.exe는 테스트 전용이며,  VeriSign 또는 Thawte 같은 인증 기관에서 유효한 SPC를 받을 수 있습니다.  X.509 인증서를 만드는 방법은 [Makecert.exe\(인증서 작성 도구\)](../Topic/Makecert.exe%20\(Certificate%20Creation%20Tool\).md)를 참조하십시오.  
  
 이 도구는 자동으로 Visual Studio와 함께 설치됩니다.  이 도구를 실행하려면 개발자 명령 프롬프트\(또는 Windows 7의 Visual Studio 명령 프롬프트\)를 사용합니다.  자세한 내용은 [명령 프롬프트](../../../docs/framework/tools/developer-command-prompt-for-vs.md)을 참조하십시오.  
  
 명령 프롬프트에 다음을 입력합니다.  
  
## 구문  
  
```  
  
cert2spc cert1.cer | crl1.crl [... certN.cer | crlN.crl] outputSPCfile.spc  
```  
  
#### 매개 변수  
  
|인수|설명|  
|--------|--------|  
|`certN.cer`|SPC 파일에 포함할 X.509 인증서의 이름입니다.  여러 개의 이름을 공백으로 구분하여 지정할 수 있습니다.|  
|`crlN.crl`|SPC 파일에 포함할 인증서 해지 목록의 이름입니다.  여러 개의 이름을 공백으로 구분하여 지정할 수 있습니다.|  
|`outputSPCfile.spc`|X.509 인증서가 들어 있는 PKCS \#7 개체의 이름을 나타냅니다.|  
  
|옵션|설명|  
|--------|--------|  
|**\/?**|이 도구의 명령 구문 및 옵션을 표시합니다.|  
  
## 예제  
 다음 명령을 사용하여 `myCertificate.cer`에서 SPC를 만들고 이를 `mySPCFile.spc`에 포함시킵니다.  
  
```  
cert2spc myCertificate.cer mySPCFile.spc  
```  
  
 다음 명령을 사용하여 `oneCertificate.cer` 및 `twoCertificate.cer`에서 SPC를 만들고 이를 `mySPCFile.spc`에 포함시킵니다.  
  
```  
cert2spc oneCertificate.cer twoCertificate.cer mySPCFile.spc  
```  
  
## 참고 항목  
 [도구](../../../docs/framework/tools/index.md)   
 [Makecert.exe\(인증서 작성 도구\)](../Topic/Makecert.exe%20\(Certificate%20Creation%20Tool\).md)   
 [명령 프롬프트](../../../docs/framework/tools/developer-command-prompt-for-vs.md)