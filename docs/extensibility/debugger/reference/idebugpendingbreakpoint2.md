---
title: "IDebugPendingBreakpoint2 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPendingBreakpoint2
helpviewer_keywords: IDebugPendingBreakpoint2 interface
ms.assetid: d416b095-917e-475e-b796-ec0a03ffb8da
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ef986bd657a080c08fd0ebb85908ba59757bf207
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugpendingbreakpoint2"></a>IDebugPendingBreakpoint2
Этот интерфейс представляет точку останова, можно привязать расположение кода.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugPendingBreakpoint2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) реализует этот интерфейс в рамках поддержки точек останова.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Вызов [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) создает ожидающая точка останова из [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) интерфейса. Вызов [привязки](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) создает `IDebugBreakpoint2` интерфейс, который представляет связанная точка останова в программе.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugPendingBreakpoint2`.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Определяет, можно привязать ли это ожидающая точка останова расположение кода.|  
|[BIND](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Привязывает этот ожидающая точка останова одно или несколько расположений кода.|  
|[GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Возвращает состояние данного объекта ожидающих точек останова.|  
|[GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Возвращает точку останова запрос, который использовался для создания этой ожидающая точка останова.|  
|[Виртуализация](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)|Переключает состояние виртуализированных этого ожидающих точек останова.|  
|[Включить](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Переключает состояние выполнения это ожидающих точек останова.|  
|[SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)|Задает или изменяет условие, связанное с этим ожидающих точек останова.|  
|[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)|Задает или изменяет количество прохода, связанные с данным ожидающим точки останова.|  
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Перечисляет все точки останова, связанный с этой ожидающая точка останова.|  
|[EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Перечисляет все точки останова ошибки, вызванные этой ожидающая точка останова.|  
|[Удалить](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Удаляет этот ожидающая точка останова и все точки останова, привязанный из него.|  
  
## <a name="remarks"></a>Примечания  
 `IDebugPendingBreakpoint2`может рассматриваться как поставщик всю необходимую информацию, требуемую для привязки точки останова кода, которая может применяться для одного или нескольких программ.  
  
 Ожидающая точка останова потенциально может привести к более одного связанная точка останова. Например точки останова в стиле с ++ шаблона может привести к связанная точка останова для каждой уникальный экземпляр этого шаблона.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)