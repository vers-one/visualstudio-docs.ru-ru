---
title: "IDebugCoreServer3::EnableAutoAttach | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCoreServer3::EnableAutoAttach
helpviewer_keywords: IDebugCoreServer3::EnableAutoAttach
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: d0b7fbfc1d7c3d9d4ab5214e8c0c5518c6dad5cb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugcoreserver3enableautoattach"></a>IDebugCoreServer3::EnableAutoAttach
Включает автоматическое присоединение для указанного отладчики.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT EnableAutoAttach(  
   GUID*     rgguidSpecificEngines,  
   DWORD     celtSpecificEngines,  
   LPCOLESTR pszStartPageUrl,  
   BSTR*     pbstrSessionId  
);  
```  
  
```csharp  
int EnableAutoAttach(  
   Guid[]     rgguidSpecificEngines,  
   uint       celtSpecificEngines,  
   string     pszStartPageUrl,  
   out string pbstrSessionId  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `rgguidSpecificEngines`  
 [in] Массив идентификаторов GUID для каждого ядра отладки для пометки как автоматическое присоединение.  
  
 `celtSpecificEngines`  
 [in] Количество обработчиков, указанный в `rgguidSpecificEngines`.  
  
 `pszStartPageUrl`  
 [in] Начальный URL-адрес для использования при присоединении автоматически.  
  
 `pbstrSessionID`  
 [out] Идентификатор сеанса, который был подключен автоматически.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки. Один код ошибки- `E_AUTO_ATTACH_NOT_REGISTERED`, указывающая, что фабрика класса auto-attach не был зарегистрирован.  
  
## <a name="remarks"></a>Примечания  
 При запуске программы, связанные с указанным URL-адрес, указанный отладчики автоматически запущен и присоединенного.  
  
## <a name="see-also"></a>См. также  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)