---
title: "IEnumDebugFields::GetCount | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugFields::GetCount
helpviewer_keywords: IEnumDebugFields::GetCount method
ms.assetid: 3f471b40-4db3-49f7-b504-58b2476eef74
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 4da98967ac8841b0bf91d30aa3a1dae6c2668d30
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ienumdebugfieldsgetcount"></a>IEnumDebugFields::GetCount
Этот метод возвращает количество элементов в перечислении.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetCount(  
   [out] ULONG* pcelt  
);  
```  
  
```csharp  
int GetCount(  
   out uint pcelt  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pcelt`  
 [out] Возвращает число элементов в перечислении.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод не является частью обычной COM-интерфейс перечисления которого указывает, что только Далее, клонирования, Skip и сброса необходимо реализовать.  
  
## <a name="see-also"></a>См. также  
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)