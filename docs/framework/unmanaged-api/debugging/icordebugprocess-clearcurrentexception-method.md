---
title: ICorDebugProcess::ClearCurrentException 메서드
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.ClearCurrentException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::ClearCurrentException
helpviewer_keywords:
- ClearCurrentException method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::ClearCurrentException method [.NET Framework debugging]
ms.assetid: 9e02ee1a-e495-4578-bfb5-b946274bede7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d2515e21ec00bd656eafd21a092a27304f7b1769
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugprocessclearcurrentexception-method"></a>ICorDebugProcess::ClearCurrentException 메서드
지정 된 스레드에 대해 현재 관리 되지 않는 예외를 지웁니다.  
  
## <a name="syntax"></a>구문  
  
```  
HRESULT ClearCurrentException([in] DWORD threadID);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `threadID`  
 [in] 현재 관리 되지 않는 예외는 지워집니다 스레드의 ID입니다.  
  
## <a name="remarks"></a>설명  
 이 메서드를 호출 하기 전에 호출 [icordebugcontroller:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) 스레드가 디버기에 서 무시 해야 하는 관리 되지 않는 예외에서 보고 하는 경우. 처리 중인 대역 (IB)와 지정한 스레드에서 밴드의 범위를 벗어난 (OOB) 이벤트를 지웁니다. 모든 OOB 중단점 및 단일 단계 예외 자동으로 지워집니다.  
  
 사용 하 여 [icordebugthread2:: Interceptcurrentexception](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md) 현재 가로채기 위해 스레드의 예외를 관리 합니다.  
  
## <a name="requirements"></a>요구 사항  
 **플랫폼:** 참조 [시스템 요구 사항](../../../../docs/framework/get-started/system-requirements.md)합니다.  
  
 **헤더:** CorDebug.idl, CorDebug.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET framework 버전:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
