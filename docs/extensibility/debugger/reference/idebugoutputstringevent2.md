---
title: "IDebugOutputStringEvent2 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugOutputStringEvent2
helpviewer_keywords: IDebugOutputStringEvent2 interface
ms.assetid: 86596fd1-cecc-4813-8add-dc3d70068f9b
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f222df8aa2a6fc35db08ceae3e8f49dfe7537960
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugoutputstringevent2"></a>IDebugOutputStringEvent2
Этот интерфейс отправляется подсистема отладки (DE) диспетчера сеанса отладки (SDM) для вывода строки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugOutputStringEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 DE реализует этот интерфейс для отправки строки для **вывода** окна интегрированной среды разработки. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) на один и тот же объект как этот интерфейс должен быть реализован интерфейс. Использует SDM [QueryInterface](/cpp/atl/queryinterface) для доступа к `IDebugEvent2` интерфейса.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 DE создает и отправляет этот объект события для передачи строки в **вывода** окна. Это событие отправляется с помощью [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) функции обратного вызова, предоставляемую SDM, когда он присоединяется к отлаживаемой программы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны метод `IDebugOutputStringEvent2`.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[GetString](../../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md)|Получает отображаемое сообщение.|  
  
## <a name="remarks"></a>Примечания  
 Например, в неуправляемом коде строку, чтобы ее выходные данные могут быть получены при передаче строки отлаживаемой программы Win32 `OutputDebugString` функции. Эта строка является перехвачен DE и отправляемые SDM как `IDebugOutputStringEvent2` событий.  
  
 Используйте [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md) для отправки сообщения, требующий ответа пользователя.  
  
 Используйте [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) Чтобы отправить сообщение об ошибке, не требующих отклика.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)   
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)