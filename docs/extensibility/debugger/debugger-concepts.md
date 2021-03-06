---
title: "Основные понятия отладчика | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK]
ms.assetid: 2d371d38-f1a0-4a9a-8ea3-100e8c0149b7
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 920706adb86d79e635e4f5289ca010e03282853e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="debugger-concepts"></a>Основные понятия отладчика
Для построения на отладочный пакет Visual Studio, необходимо уметь работать с архитектурные принципы, используемые при разработке пакета.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Сеанс отладки](../../extensibility/debugger/debug-session.md)  
 Описывается роль сеанса в архитектура отладки.  
  
 [Серверы](../../extensibility/debugger/servers-visual-studio-sdk.md)  
 Определяет какой сервер является с точки зрения отладки архитектуры, в терминах абстрактным и физический.  
  
 [Поставщики портов](../../extensibility/debugger/port-suppliers.md)  
 Определяет, что является поставщика порта с точки зрения архитектуры отладки.  
  
 [Порты](../../extensibility/debugger/ports.md)  
 Определяет какой порт — с точки зрения архитектуры отладки.  
  
 [Процессы](../../extensibility/debugger/processes.md)  
 Определяет какие процесс — с точки зрения архитектуры отладки.  
  
 [Узлы программы](../../extensibility/debugger/program-nodes.md)  
 Определяет узел с точки зрения отладки архитектуры, в том числе порядок ее идентификации себя и процессов, выполняемых в программе.  
  
 [Программы](../../extensibility/debugger/programs.md)  
 Определяет программу с точки зрения архитектуры отладки.  
  
 [Потоки](../../extensibility/debugger/threads.md)  
 Определяет характеристики потоков с точки зрения архитектуры отладки.  
  
 [Кадры стека](../../extensibility/debugger/stack-frames.md)  
 Определяет кадр стека с точки зрения архитектуры отладки. Кадр стека является абстракцией стека, который предоставляет контекст выполнения потока.  
  
 [Модули](../../extensibility/debugger/modules.md)  
 Определяет модуль, с точки зрения отладки архитектуры, в качестве физического контейнера кода, такие как выполнение исполняемого файла или библиотеки DLL.  
  
 [Точки останова](../../extensibility/debugger/breakpoints-visual-studio-sdk.md)  
 Определяет три вида точек останова — ожидание, границы и ошибки, с точки зрения архитектуры отладки.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Контексты отладчика](../../extensibility/debugger/debugger-contexts.md)  
 Объясняет, как модуль отладки (DE) одновременно работает в пределах кода, документацию и контекстов выражения вычисления. Описание для каждого из трех контекстов, расположения, положение или оценки, относящиеся к нему.  
  
 [Компоненты отладчика](../../extensibility/debugger/debugger-components.md)  
 Обзор компонентов отладки Visual Studio, которые включают модуль отладки (DE), средство оценки выражений (EE) и обработчик символ (SH).  
  
 [Задачи отладки](../../extensibility/debugger/debugging-tasks.md)  
 Содержит ссылки на различные задачи отладки, например, запустив программу и оценки выражений.