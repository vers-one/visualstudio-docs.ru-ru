---
title: "IDiaPropertyStorage::ReadPropertyNames | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaPropertyStorage::ReadPropertyNames
ms.assetid: f8bcab77-afca-4a8f-8710-697842f8a518
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 95f535bd314ec998c83ec9c02aab2190646f3c53
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idiapropertystoragereadpropertynames"></a>IDiaPropertyStorage::ReadPropertyNames
Извлекает соответствующие имена строки для заданного идентификаторов свойств.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT ReadPropertyNames (  
   ULONG         cpropid,  
   PROPID const* rgpropid,  
   BSTR*         rglpwstrName  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `cpropid`  
 [in] Количество идентификаторов свойств в `rgpropid`.  
  
 `rgpropid`  
 [in] Массив идентификаторов свойств, для которого необходимо получить имена (`PROPID` определяется в файле WTypes.h как `ULONG`).  
  
 `rglpwstrName`  
 [in, out] Массив имен свойств для указанного свойства идентификаторов. Массив должен быть предварительно выделить запрошенное число имен свойств и должен иметь возможность по крайней мере `cpropid``BSTR` строки.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Имя возвращаемого свойства освобождения (путем вызова `SysFreeString` функция) когда они больше не нужны.  
  
## <a name="see-also"></a>См. также  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)