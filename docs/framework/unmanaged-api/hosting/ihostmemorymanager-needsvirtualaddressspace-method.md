---
title: IHostMemoryManager::NeedsVirtualAddressSpace 메서드
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.NeedsVirtualAddressSpace
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::NeedsVirtualAddressSpace
helpviewer_keywords:
- IHostMemoryManager::NeedsVirtualAddressSpace method [.NET Framework hosting]
- NeedsVirtualAddressSpace method [.NET Framework hosting]
ms.assetid: 71f0eab5-0170-46f8-9f88-1df5abdeb34a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 87c97a678fce4c25a113670a4668515a898e5251
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="ihostmemorymanagerneedsvirtualaddressspace-method"></a>IHostMemoryManager::NeedsVirtualAddressSpace 메서드
공용 언어 런타임 (CLR)이 지정 된 메모리 사용을 시도 하려는 호스트에 알립니다.  
  
## <a name="syntax"></a>구문  
  
```  
HRESULT NeedsVirtualAddressSpace (  
    [in] LPVOID  startAddress,  
    [in] SIZE_T  size  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `startAddress`  
 [in] 시작 주소는 메모리입니다.  
  
 `size`  
 [in] 메모리의 바이트 크기입니다.  
  
## <a name="remarks"></a>설명  
 `NeedsVirtualAddressSpace` 메서드는 콜백 메서드 및 호스팅 응용 프로그램의 작성자가 구현 해야 합니다. CLR에서 호출 됩니다.  
  
 호스트에서 지정된 된 메모리를 사용 하는 CLR을 원하지 않을 경우 E_OUTOFMEMORY HRESULT를 반환할 수 있습니다.  
  
## <a name="requirements"></a>요구 사항  
 **플랫폼:** 참조 [시스템 요구 사항](../../../../docs/framework/get-started/system-requirements.md)합니다.  
  
 **헤더:** MSCorEE.h  
  
 **라이브러리:** MSCorEE.dll에 리소스로 포함  
  
 **.NET framework 버전:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>참고 항목  
 [IHostMemoryManager 인터페이스](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
