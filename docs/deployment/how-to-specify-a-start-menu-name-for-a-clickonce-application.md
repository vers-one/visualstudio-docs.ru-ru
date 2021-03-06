---
title: "Как: укажите имя приложения ClickOnce меню Пуск | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Start menu resource name
- Start menu name
- ClickOnce deployment, Start menu name
ms.assetid: 4b5183b2-2fd4-4433-9310-4a73bb12c4e3
caps.latest.revision: "17"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: f01bb5750f31101a6d8ec0cb5f33669e5fbf2b4b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-a-start-menu-name-for-a-clickonce-application"></a>Практическое руководство. Задание имени в меню "Пуск" для приложения ClickOnce
Когда [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложение устанавливается для документации и в автономном режиме, будет добавлена запись для **запустить** меню и **Установка и удаление программ** списка. По умолчанию, отображаемое имя является именем сборки приложения, но отображаемое имя можно изменить, задав **название продукта** в **параметры публикации** диалоговое окно.  
  
 **Название продукта** будет отображаться на странице publish.htm; для установленного приложения вне сети, он будет использоваться имя записи в **запустить** меню, а также быть имя, которое отображается в **добавления или удаления Программы**.  
  
 **Имя издателя** будет отображаться на странице publish.htm выше **название продукта**, а для установленного автономного приложения, он будет также имя папки, содержащей значок приложения в **запуск**  меню.  
  
 Можно задать **название продукта** и **имя издателя** свойства в **параметры публикации** диалоговом на **публикации** страницы из **в конструкторе проектов**.  
  
### <a name="to-specify-a-start-menu-name"></a>Чтобы указать имя меню Пуск  
  
1.  Выберите проект в **обозревателе решений**, а затем в меню **Проект** щелкните **Свойства**.  
  
2.  Нажмите кнопку **публикации** вкладки.  
  
3.  Нажмите кнопку **параметры** кнопку, чтобы открыть **параметры публикации** диалоговое окно.  
  
4.  Нажмите кнопку **описание**.  
  
5.  В **параметры публикации** диалогового окна введите имя, отображаемое в **название продукта**.  
  
6.  При необходимости можно ввести имя издателя в **имя издателя**.  
  
## <a name="see-also"></a>См. также  
 [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Практическое руководство. Публикация приложения ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)