---
title: "Команда \"Запустить\" | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: debug.start
helpviewer_keywords:
- Start command
- Debug.Start command
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8eb0efae140613c6caa7bd71d72e0ce4cda37db8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="start-command"></a>Команда Start
Начинает отладку запускаемого проекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Debug.Start [address]  
```  
  
## <a name="arguments"></a>Аргументы  
 `address`  
 Необязательный. Адрес, по которому программа приостанавливает выполнение, сходен с точкой останова в исходном коде. Этот аргумент применяется только в режиме отладки.  
  
## <a name="remarks"></a>Примечания  
 При запуске команды **Запустить** она выполняет операцию RunToCursor по указанному адресу.  
  
## <a name="example"></a>Пример  
 Этот пример запускает отладчик и игнорирует все возникающие исключения.  
  
```  
>Debug.Start  
```  
  
## <a name="see-also"></a>См. также  
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Командное окно](../../ide/reference/command-window.md)   
 [Поле "Поиск/Команда"](../../ide/find-command-box.md)   
 [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)