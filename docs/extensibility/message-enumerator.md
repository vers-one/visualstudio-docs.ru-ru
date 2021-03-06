---
title: "Сообщение перечислитель | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- message enumerator
- source control plug-ins, message enumeration
ms.assetid: 4a4faa0d-d352-40ea-a21d-c09ea286a8e1
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 6a24db9c50bd298f068c23af0b6bad5755ec252d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="message-enumerator"></a>Перечислителя сообщений
Следующие флаги, используемые для `TEXTOUTPROC` функции, которая является функцией обратного вызова, интегрированная среда разработки предоставляет при вызове [SccOpenProject](../extensibility/sccopenproject-function.md) (см. [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) сведения о функции обратного вызова функция).  
  
 При запросе интегрированной среды разработки для отмены процесса появляется одно из сообщений "Отмена". В этом случае система управления подключаемый модуль использует `SCC_MSG_STARTCANCEL` для запроса IDE, чтобы отобразить **отменить** кнопки. После этого можно отправлять любой набор обычных сообщений. Если любой из этих возвращает `SCC_MSG_RTN_CANCEL`, то подключаемый модуль завершает операцию и возвращает. Подключаемый модуль также опрашивает `SCC_MSG_DOCANCEL` периодически для проверки, если операция отменена пользователем. Когда все операции осуществляются, или если пользователь отменил, подключаемый модуль отправляет `SCC_MSG_STOPCANCEL`. `SCC_MSG_INFO`, SCC_MSG_WARNING, и SCC_MSG_ERROR типы используются для сообщений, которые отображаются в списке прокрутки сообщений. `SCC_MSG_STATUS`— Это специальный тип, который указывает, что текст должно отображаться в строке состояния или временный отображаемую область. Не будет окончательно в списке.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
enum {   
   SCC_MSG_RTN_CANCEL = -1,   
   SCC_MSG_RTN_OK = 0,   
   SCC_MSG_INFO = 1   
   SCC_MSG_WARNING,   
   SCC_MSG_ERROR,   
   SCC_MSG_STATUS,   
   SCC_MSG_DOCANCEL,   
   SCC_MSG_STARTCANCEL,   
   SCC_MSG_STOPCANCEL   
};  
```  
  
## <a name="members"></a>Участники  
 SCC_MSG_RTN_CANCEL  
 Возврат из обратного вызова, чтобы указать "Отмена".  
  
 SCC_MSG_RTN_OK  
 Возврат из обратного вызова, чтобы продолжить.  
  
 SCC_MSG_INFO  
 Сообщение является информационным.  
  
 SCC_MSG_WARNING  
 Сообщение является предупреждением.  
  
 SCC_MSG_ERROR  
 Сообщение является ошибкой.  
  
 SCC_MSG_STATUS  
 Сообщение предназначено для строки состояния.  
  
 SCC_MSG_DOCANCEL  
 Нет текста; Возвращает IDE `SCC_MSG_RTN_OK` или `SCC_MSG_RTN_CANCEL`.  
  
 SCC_MSG_STARTCANCEL  
 Запускает цикл "Отмена".  
  
 SCC_MSG_STOPCANCEL  
 Останавливает цикла "Отмена".  
  
## <a name="see-also"></a>См. также  
 [Подключаемые модули управления версиями](../extensibility/source-control-plug-ins.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)