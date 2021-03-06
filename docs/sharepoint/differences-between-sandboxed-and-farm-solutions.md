---
title: "Различия между изолированными решениями и решениями фермы | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, sandboxed solutions
- sandboxed solutions [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, farm solutions
- farm solutions [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: c9123f028bab5319f47e4bdc0ada0dbbee49bc2c
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="differences-between-sandboxed-and-farm-solutions"></a>Различия между изолированными решениями и решениями фермы
  При компиляции решения SharePoint, он будет развернут на сервере SharePoint и присоединяет отладчик для отладки. Процесс, используемый для отладки решения зависит от значения свойства изолированное решение: изолированное решение или решение фермы.  
  
 Дополнительные сведения см. в разделе [замечания об изолированных решениях](../sharepoint/sandboxed-solution-considerations.md).  
  
## <a name="farm-solutions"></a>Решения фермы  
 Решения фермы, размещенных в рабочем процессе IIS (W3WP.exe), выполнение кода, которые могут повлиять на всю ферму. При отладке проекта SharePoint, свойства которого изолированное решение устанавливается «решение фермы» пула приложений IIS в системе перезапускается до SharePoint отзовет или развертывает компонент таким образом, чтобы освободить все файлы, заблокированные рабочим процессом IIS. Удаляется только пула приложений IIS обслуживает URL-адрес сайта проекта SharePoint.  
  
## <a name="sandboxed-solutions"></a>Изолированные решения  
 Изолированные решения, которые размещены в SharePoint пользователь кода решения рабочий процесс (SPUCWorkerProcess.exe), запустите код, который может повлиять только на коллекцию сайтов решения. Так как изолированные решения не выполняются в рабочем процессе IIS, необходимо перезапустить пул приложений IIS, ни сервер IIS. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Присоединяет отладчик SPUCWorkerProcess процесса, которое автоматически запускает службу SPUserCodeV4 в SharePoint и элементов управления. Это необходимо для процесс SPUCWorkerProcess повторно загрузить последнюю версию решения.  
  
## <a name="either-type-of-solution"></a>Оба типа решения  
 Для обоих типов решения [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] также присоединяет отладчик в браузере, чтобы включить отладку клиентского скрипта. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]использует для этой цели ядро отладки скрипта. Включение отладки скриптов, необходимо изменить параметры браузера по умолчанию при появлении.  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Присоединяет отладчик только W3WP или SPUCWorkerProcess процессов, запущенных на текущем узле. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]также присоединяет управляемого COM Plus и ядро отладки рабочих процессов.  
  
## <a name="see-also"></a>См. также  
 [Отладка решений SharePoint](../sharepoint/debugging-sharepoint-solutions.md)   
 [Построение и отладка решений SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [Замечания об изолированных решениях](../sharepoint/sandboxed-solution-considerations.md)  
  
  