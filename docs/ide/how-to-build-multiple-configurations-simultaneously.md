---
title: "Практическое руководство. Сборка с использованием нескольких конфигураций | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba830937-3317-4674-8cc2-c0cd565603c5
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 86c0a9fbbfe7e4b0b38b0286cf10f06dd7eec89c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-build-multiple-configurations-simultaneously"></a>Практическое руководство. Построение с использованием нескольких конфигураций
Большинство типов проектов можно создать с использованием нескольких или даже всех конфигураций сборки одновременно с помощью диалогового окна **Пакетная сборка**. Однако вы не можете одновременно выполнять сборку следующих типов проектов в нескольких конфигурациях сборок:  
  
1.  Приложения [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)], созданные для Windows с использованием JavaScript.  
  
2.  Все проекты Visual Basic.  
  
 Дополнительные сведения о конфигурациях сборки см. в разделе [Общие сведения о конфигурациях сборки](../ide/understanding-build-configurations.md).  
  
### <a name="to-build-a-project-in-multiple-build-configurations"></a>Сборка проекта в нескольких конфигурациях сборок  
  
1.  В строке меню выберите **Сборка** и **Пакетная сборка**.  
  
2.  В столбце **Сборка** установите флажки для конфигураций, с которыми требуется выполнить сборку проекта.  
  
    > [!TIP]
    >  Если вы хотите изменить или создать конфигурацию сборки для решения, выберите **Сборка**, **Диспетчер конфигураций** в строке меню, чтобы открыть диалоговое окно **Диспетчер конфигураций**. После изменения конфигурации сборки для решения нажмите кнопку **Пересобрать** в диалоговом окне **Пакетная сборка**, чтобы обновить все конфигурации сборки для проектов в решении.  
  
3.  Нажмите кнопку **Сборка** или **Пересобрать** для сборки проекта с указанными конфигурациями.  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Создание и изменение конфигураций](../ide/how-to-create-and-edit-configurations.md)   
 [Общие сведения о конфигурациях построения](../ide/understanding-build-configurations.md)   
 [Параллельная сборка нескольких проектов](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)