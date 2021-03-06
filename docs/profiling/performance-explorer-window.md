---
title: "Окно \"Обозреватель производительности\" | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performanceexplorer
- vs.performance.explorer
helpviewer_keywords: performance tools, Performance Explorer
ms.assetid: cb6a6efc-93a5-49a2-8d03-6969b5f3b6d7
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3ab16dca3d4d27c157620f59774ec37f57aae020
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="performance-explorer-window"></a>Окно "Обозреватель производительности"
Окно **Обозреватель производительности** в интегрированной среде разработки (IDE)[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] позволяет настраивать и запускать сеансы анализа производительности при помощи средств профилирования [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 **Требования**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
## <a name="performance-explorer-toolbar"></a>Панель инструментов обозревателя производительности  
 На панели инструментов **обозревателя производительности** доступны следующие параметры.  
  
-   **Запустить мастер производительности.** Запускает мастер производительности, который позволяет добавить новый сеанс анализа производительности в окно обозревателя производительности.  
  
-   **Новый сеанс производительности.** Добавляет пустой сеанс анализа производительности в окно обозревателя производительности.  
  
-   **Запуск.** Кнопка **Запуск** позволяет запустить целевое приложение с немедленным началом профилирования (**Запустить с профилированием**) или с приостановкой профилирования (**Запустить с приостановкой профилирования**).  
  
-   **Метод.** Определяет метод профилирования, используемый для сеанса: выборка или инструментирование.  
  
-   **Остановить.** Позволяет немедленно завершить работу целевого приложения и профилировщика.  
  
-   **Присоединить и отсоединить.** Отображает диалоговое окно **Присоединить профилировщик к процессу**, позволяющее выбрать запущенный процесс, к которому требуется присоединить профилировщик.  
  
## <a name="performance-explorer-window"></a>Окно "Обозреватель производительности"  
 В окне **Обозреватель производительности** находится элемент управления "Дерево", в котором отображаются двоичные файлы и файлы данных отчета для одного или нескольких сеансов анализа.  
  
-   **Имя сеанса.** В корне элемента управления "Дерево" содержится имя сеанса. Чтобы задать свойства сеанса или запустить целевое приложение и профилировщик, щелкните имя сеанса правой кнопкой мыши.  
  
-   **Целевые объекты.** Отображаются имена двоичных файлов, профилирование которых выполняется в ходе сеанса. Щелкните элемент **Целевые объекты**, чтобы добавить или удалить двоичный файл, проект [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] или веб-сайт. Чтобы задать свойства отдельного двоичного файла, щелкните имя целевого объекта правой кнопкой мыши.  
  
-   **Отчеты.** Отображаются имена файлов данных профилировщика, которые были созданы в ходе сеанса. Чтобы добавить существующий отчет или сравнить два файла данных профилировщика, щелкните **Отчеты** правой кнопкой мыши. Чтобы открыть, удалить или экспортировать файл данных профилировщика, щелкните имя отчета правой кнопкой мыши.  
  
## <a name="see-also"></a>См. также  
 [Разделы общих сведений](../profiling/overviews-performance-tools.md)   
 [Настройка сеансов анализа производительности](../profiling/configuring-performance-sessions.md)   
 [Управление сбором данных](../profiling/controlling-data-collection.md)