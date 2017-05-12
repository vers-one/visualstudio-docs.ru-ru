---
title: "Развертывание решения Office"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "ClickOnce - развертывание [разработка решений Office в Visual Studio], сведения о развертывании решения ClickOnce"
  - "ClickOnce - развертывание [разработка решений Office в Visual Studio], просмотр событий"
  - "ClickOnce - развертывание [разработка решений Office в Visual Studio], устранение неполадок"
  - "развертывание приложений [разработка решений Office в Visual Studio], просмотр событий"
  - "развертывание приложений [разработка решений Office в Visual Studio], решения Office (система 2007)"
  - "развертывание приложений [разработка решений Office в Visual Studio], устранение неполадок"
  - "Office - приложения [разработка решений Office в Visual Studio], развертывание решений Office"
  - "Office - разработка решений в Visual Studio, развертывание решений Office"
  - "Office - разработка решений в Visual Studio, просмотр событий"
  - "Office - разработка решений в Visual Studio, устранение неполадок"
  - "Office - решения [разработка решений Office в Visual Studio], развертывание"
  - "решения [разработка решений Office в Visual Studio], развертывание решений Office (система 2007)"
ms.assetid: 4cdf4bc6-72c5-4166-8019-d5fd61281079
caps.latest.revision: 78
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 74
---
# Развертывание решения Office
  Решения Office можно развертывать с помощью ClickOnce или установщика Windows.  Использование ClickOnce позволяет сократить число шагов, необходимых для развертывания и обновления решения.  При использовании установщика Windows разработчик получает больший контроль над процессом установки решения и над тем, какие именно страницы программы установки отображаются, когда пользователь устанавливает решение.  
  
## Развертывание решения с помощью ClickOnce  
 При развертывании решения с помощью ClickOnce оно публикуется в центральном расположении, откуда пользователи могут устанавливать и запускать его.  Решение можно обновить без необходимости передачи пользователям новой программы установки.  Этот вариант развертывания проще, но он не позволяет работать с пользовательскими страницами мастера установки.  Кроме того, на компьютерах с несколькими пользователями решения должны устанавливаться по несколько раз.  См. раздел [Развертывание решения Office с помощью ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
## Развертывание решения с помощью установщика Windows  
 При развертывании решения с помощью установщика Windows программа установки распространяется среди пользователей, а пользователи, в свою очередь, устанавливают решение с помощью этой программы.  Программа установки позволяет установить решение сразу для всех пользователей компьютера, а не только для текущего пользователя.  Также она дает больший контроль над тем, какие параметры видны пользователям при установке решения.  Например, можно показать пользователям лицензионное соглашение или позволить им установить только часть компонентов решения.  Однако при обновлении решения необходимо передать пользователям новую программу установки.  См. раздел [Развертывание решения Office с помощью установщика Windows](../vsto/deploying-an-office-solution-by-using-windows-installer.md).  
  
## См. также  
 [Обеспечение безопасности решений Office](../vsto/securing-office-solutions.md)   
 [Развертывание решения Office с помощью ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Развертывание решения Office с помощью установщика Windows](../vsto/deploying-an-office-solution-by-using-windows-installer.md)   
 [Устранение неполадок, связанных с развертыванием решения Office](../vsto/troubleshooting-office-solution-deployment.md)  
  
  