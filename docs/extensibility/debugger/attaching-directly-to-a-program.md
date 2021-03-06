---
title: "Подключение к программе | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debug engines, attaching to programs
ms.assetid: ad2b7db8-821c-440c-ba07-c55c6a395e0f
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c528925e323e4cff5784365e3097cc7f5f414963
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="attaching-directly-to-a-program"></a>Подключение к программе
Пользователи, желающие отладку программ, в процессе, который обычно уже выполняется выполните следующие действия:  
  
1.  В Интегрированной среде разработки выберите **отладить процессы** из **средства** меню.  
  
     **Процессов** откроется диалоговое окно.  
  
2.  Выберите процесс и нажмите кнопку **присоединение** кнопки.  
  
     **Присоединиться к процессу** отображается диалоговое окно со списком всех отладчики (DEs) установлен на компьютере.  
  
3.  Укажите DEs для использования выбранного процесса отладки, а затем нажмите кнопку **ОК**.  
  
 Отладочный пакет запускает сеанс отладки и передает ей список DEs. Сеанс отладки, в свою очередь, передает этот список, а также функцию обратного вызова для выбранного процесса и запрашивает процесса для перечисления его выполняющиеся программы.  
  
 Программным способом в ответ на запрос пользователя отладочный пакет создает экземпляр диспетчера сеанса отладки (SDM) и передает ей список выбранных DEs. Вместе со списком, отладочный пакет передает SDM [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) интерфейса. Отладочный пакет передает список DEs для выбранного процесса путем вызова [IDebugProcess2::Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md). Затем вызывает SDM [IDebugProcess2::EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) через порт для программы, запущенные в процессе перечисления.  
  
 С этого момента каждого модуля отладки присоединяется к программе точно так, как описано в [присоединение после запуска](../../extensibility/debugger/attaching-after-a-launch.md), с двумя исключениями.  
  
 Для повышения эффективности DEs, которые реализованы для совместного использования адресное пространство с SDM сгруппированы так, чтобы каждый DE набор программ, который будет присоединен. В этом случае [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) вызовы [IDebugEngine2::Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) и передает его массив программы для присоединения.  
  
 Второе исключение: что запуска события, отправляемые DE, подключение к программе, которая запущена обычно не включают события точки входа.  
  
## <a name="see-also"></a>См. также  
 [Отправка события запуска после запуска](../../extensibility/debugger/sending-startup-events-after-a-launch.md)   
 [Задачи отладки](../../extensibility/debugger/debugging-tasks.md)