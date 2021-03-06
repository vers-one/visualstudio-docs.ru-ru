---
title: "Необходимых изменений для выполнения проектов Office, которые переносятся на платформу .NET Framework 4 или .NET Framework 4.5 | Документы Microsoft"
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
helpviewer_keywords: Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: ee90d5c205f58736f7ccb6536e29b2fd6d16b152
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="required-changes-to-run-office-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>Изменения, необходимые для выполнения проектов Office, которые переносятся на платформу .NET Framework 4 или .NET Framework 4.5
  Если требуемая версия .NET framework проекта Office изменяется на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии с более ранней версии платформы .NET Framework, необходимо выполнить следующие задачи, чтобы убедиться, что решение может выполняться на компьютере разработки и на компьютерах конечных пользователей:  
  
-   Удалите <xref:System.Security.SecurityTransparentAttribute> из проекта, если он был обновлен с версии Visual Studio 2008.  
  
-   Выполнить **Очистить** в Visual Studio, чтобы иметь возможность запуска или отладки проекта на компьютере разработчика.  
  
-   Обновите платформу .NET Framework, необходимую для проекта.  
  
-   Конечные пользователи также должны переустановить решение, если оно было развернуто с помощью технологии ClickOnce до того, как вы изменили целевую платформу.  
  
 Дополнительные сведения о всех этих задачах см. в соответствующих разделах ниже.  
  
## <a name="removing-the-securitytransparent-attribute-from-projects-that-you-upgrade-from-visual-studio-2008"></a>Удаление атрибута SecurityTransparent из проектов, которые обновляются с версии Visual Studio 2008  
 При обновлении проекта Office с версии Visual Studio 2008 и последующем изменении целевой платформы .NET Framework проекта на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более позднюю версию атрибут <xref:System.Security.SecurityTransparentAttribute> необходимо удалить из проекта. Visual Studio не удаляет этот атрибут автоматически. Если не удалить этот атрибут, при компиляции проекта вы получите сообщение об ошибке.  
  
 Дополнительные сведения об условиях, в которых Visual Studio может изменить целевую платформу обновленного проекта [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], в разделе [обновление и перенос решений Office](../vsto/upgrading-and-migrating-office-solutions.md).  
  
#### <a name="to-remove-the-securitytransparentattribute"></a>Удаление атрибута SecurityTransparentAttribute  
  
1.  Откройте проект в Visual Studio, а затем откройте **Обозреватель решений**.  
  
2.  В узле **Свойства** (для C#) или **Мой проект** (для Visual Basic) дважды щелкните файл кода AssemblyInfo, чтобы открыть его в редакторе кода.  
  
    > [!NOTE]  
    >  В проектах Visual Basic для просмотра файла с кодом AssemblyInfo необходимо нажать кнопку **Показать все файлы** в **обозревателе решений** .  
  
3.  Найдите <xref:System.Security.SecurityTransparentAttribute> и удалите его из файла или закомментируйте его.  
  
    ```vb  
    <Assembly: SecurityTransparent()>  
    ```  
  
    ```csharp  
    [assembly: SecurityTransparent()]  
    ```  
  
## <a name="performing-the-clean-command-to-debug-or-run-a-project-on-the-development-computer"></a>Выполнение команды очистки для отладки или запуска проекта на компьютере разработчика  
 Если проект Office был создан до требуемая версия .NET framework проекта изменяется на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии, то необходимо выполнить **Очистить** а затем перестройте проект после изменения целевой версии .NET framework. Если не выполнять **Очистить** команды, вы получите <xref:System.Runtime.InteropServices.COMException> при попытке отладки или запуска нового проекта.  
  
 Дополнительные сведения о **Очистить** см. в разделе [построение решений Office](../vsto/building-office-solutions.md).  
  
## <a name="updating-the-prerequisites-for-deployment"></a>Обновление необходимых компонентов для развертывания  
 При изменении целевой платформы проекта Office на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии, необходимо обновить соответствующие необходимые компоненты .NET Framework в **необходимые компоненты** диалоговое окно. В противном случае процесс развертывания с помощью ClickOnce или проект InstallShield Limited Edition проверяет наличие предыдущей версии платформы .NET Framework и устанавливает ее.  
  
 Дополнительные сведения об обновлении компонентов, необходимых для развертывания на компьютерах конечных пользователей см. в разделе [как: Установка необходимых компонентов на компьютерах конечных пользователей для запуска решений Office](http://msdn.microsoft.com/en-us/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98).  
  
## <a name="reinstalling-solutions-on-end-user-computers"></a>Повторная установка решений на компьютерах конечных пользователей  
 Если вы используете технологию ClickOnce для развертывания решения Office, которое ориентируется на платформу .NET Framework 3.5, а затем переориентируете проект на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более позднюю версию, необходимо удалить решение, а затем переустановить после его повторной публикации. Если вы повторно публикуете переориентированное решение и оно обновляется на компьютерах конечных пользователей, то эти пользователи получат <xref:System.Runtime.InteropServices.COMException> во время выполнения обновленного решения.  
  
## <a name="see-also"></a>См. также  
 [Перенос решений Office на платформу .NET Framework 4 или более поздней версии](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)  
  
  