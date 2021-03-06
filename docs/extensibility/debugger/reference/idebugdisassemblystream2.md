---
title: "IDebugDisassemblyStream2 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDisassemblyStream2
helpviewer_keywords: IDebugDisassemblyStream2 interface
ms.assetid: b03cab0c-3f0b-4cc6-88dc-acb3b48c567a
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 63426abcc059da3278569f433907d9f073e510b3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugdisassemblystream2"></a>IDebugDisassemblyStream2
Этот интерфейс представляет поток инструкций.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugDisassemblyStream2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки реализует этот интерфейс для поддержки Дизассемблированный код для кода программы.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Вызов [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) метод возвращает этот интерфейс.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugDisassemblyStream2`.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[Чтение](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)|Считывает инструкции, начиная с текущей позиции в потоке Дизассемблированный код.|  
|[Поиск](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)|Перемещает указатель чтения в потоке Дизассемблирование заданное количество инструкции относительно указанной позиции.|  
|[GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)|Возвращает идентификатор, расположение кода для контекста определенного кода.|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)|Возвращает объект контекста кода, соответствующий идентификатору расположение указанного кода.|  
|[GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)|Возвращает идентификатор расположение кода, который представляет текущего расположения в коде.|  
|[GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)|Возвращает исходный документ, связанный с этого потока Дизассемблированный код.|  
|[GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)|Возвращает область этого потока Дизассемблированный код.|  
|[GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)|Получает размер этого потока Дизассемблированный код.|  
  
## <a name="remarks"></a>Примечания  
 Можно создать поток Дизассемблированный код для представления все адресное пространство, или просто функции или модуля в пространстве. Каждая инструкция, представленного [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) структуры, возвращенный вызовом к [чтения](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) метод.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)