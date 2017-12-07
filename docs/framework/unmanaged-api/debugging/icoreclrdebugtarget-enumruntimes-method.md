---
title: "ICoreClrDebugTarget::EnumRuntimes 메서드"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICoreClrDebugTarget.EnumRuntimes
api_location: mscordbi_macx86.dll
api_type: COM
f1_keywords: ICoreClrDebugTarget::EnumRuntimes
helpviewer_keywords:
- remote debugging API [Silverlight]
- ICorClrDebugTarget::EnumRuntimes method [Silverlight debugging]
- EnumRuntimes method, ICoreClrDebugTarget interface [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: 316df866-442d-40cc-b049-45e8adcb65d1
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d28e5f3f529f72607e2ddd84789e89f82dcdaba0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2017
---
# <a name="icoreclrdebugtargetenumruntimes-method"></a>ICoreClrDebugTarget::EnumRuntimes 메서드
원격 컴퓨터에서 실행 중인 지정된 프로세스의 CLR(공용 언어 런타임)을 열거합니다.  
  
## <a name="syntax"></a>구문  
  
```  
HRESULT EnumRuntimes (  
      [in] DWORD       dwInternalProcessID,  
      [out] DWORD*     pcRuntimes,  
      [out] CoreClrDebugRuntimeInfo**    ppRuntimes  
    );  
```  
  
#### <a name="parameters"></a>매개 변수  
 `dwInternalProcessID`  
 [in] 런타임을 열거하려는 프로세스의 내부 프로세스 ID입니다. 이 `m_dwInternalID` 해당 [CoreClrDebugProcInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md)합니다.  
  
 `pcRuntimes`  
 [out] `ppRuntimes`에 반환된 런타임 수입니다. 이 값은 0일 수 있습니다.  
  
 `ppRuntimes`  
 [out] 배열을 [CoreClrDebugRuntimeInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md) 원격 대상 프로세스에 로드 된 런타임을 나타내는 구조입니다.  
  
## <a name="return-value"></a>반환 값  
 S_OK  
 명령 실행 성공  
  
 S_FALSE  
 `dwInternalProcessID`가 컴퓨터에서 실행 중인 프로세스와 일치하지 않습니다. 프로세스가 종료된 것 같습니다. `pcRuntimes` 및 `ppRuntimes`가 null이 됩니다.  
  
 E_OUTOFMEMORY  
 `ppRuntimes`에 대해 충분한 메모리를 할당할 수 없습니다.  
  
 E_FAIL(또는 다른 E_ 반환 코드)  
 기타 실패  
  
## <a name="remarks"></a>설명  
 이 메서드에 의해 할당 된 메모리를 확보 하기 위해 호출 된 [icoreclrdebugtarget:: Freememory](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) 메서드.  
  
## <a name="requirements"></a>요구 사항  
 **플랫폼:** 참조 [시스템 요구 사항](../../../../docs/framework/get-started/system-requirements.md)합니다.  
  
 **헤더:** CoreClrRemoteDebuggingInterfaces.h  
  
 **라이브러리:** mscordbi_macx86.dll  
  
 **.NET framework 버전:** 3.5 SP1  
  
## <a name="see-also"></a>참고 항목  
 [ICoreClrDebugTarget 인터페이스](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)