---
title: "Указание файла обработчики для расширений имен файлов | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: file extensions, specifying file handlers
ms.assetid: e3de4730-a95c-465a-b3b2-92ca85364ad7
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: d5db7a218a718e27f584abbf350b49907b56fb17
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="specifying-file-handlers-for-file-name-extensions"></a>Указание файла обработчики для расширений имен файлов
Существует несколько способов определения приложения, который обрабатывает файл, который имеет расширение конкретного файла. Команды OpenWithList и подключу двумя способами для указания файла обработчики в разделе реестра для расширения файла.  
  
## <a name="openwithlist-verb"></a>Команда OpenWithList  
 При щелчке правой кнопкой мыши файл в проводнике Windows, отображается **откройте** команды. Если более одного продукта связан с расширением, вы видите **открыть с помощью** подменю.  
  
 Можно зарегистрировать другой приложениям открывать расширение путем установки раздела OpenWithList расширению файла в раздел HKEY_CLASSES_ROOT. Приложения, перечисленные в этом разделе для расширения имени файла отображаются под **рекомендуемых программ** заголовок в **открыть с помощью** диалоговое окно. В следующем примере показано приложений, зарегистрированных для открытия расширением VCPROJ-файл.  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)="VisualStudio.vcproj.14.0"  
      OpenWithList\  
         devenv.exe  
```  
  
> [!NOTE]
>  Указание приложений ключи являются HKEY_CLASSES_ROOT\Applications в списке.  
  
 Добавив ключ OpenWithList, объявить, что приложение поддерживает расширение файла, даже если другое приложение принимает право на владение расширения. Это может быть следующей версии приложения или другое приложение.  
  
## <a name="openwithprogids"></a>Подключу  
 Программные идентификаторы (ProgID), понятные версии реестра, определяющий версию приложения или COM-объекта. Каждый воссоздаваемым объект должен иметь собственный идентификатор ProgID. Например, VisualStudio.DTE.7.1 запускает Visual Studio .NET 2003, во время запуска VisualStudio.DTE.10.0 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Как владелец проекта типа или типа элемента проекта необходимо создать зависящие от версии идентификатор ProgID для расширения файла. Эти идентификаторы ProgID может быть избыточным в том, что несколько ProgID может запустить то же приложение. Дополнительные сведения см. в разделе [регистрации команд для расширений имен файлов](../extensibility/registering-verbs-for-file-name-extensions.md).  
  
 Используйте следующее соглашение об именовании для версий файла идентификаторы ProgID во избежание дублирования с регистрацией других поставщиков:  
  
|Расширение файла|С версиями ProgID|  
|--------------------|----------------------|  
|.Extension|ProductName. extension.versionMajor.versionMinor|  
  
 Вы можете зарегистрировать различных приложений, которые могут открывать файлов с определенным расширением, добавив идентификаторы ProgID с версиями HKEY_CLASSES_ROOT в качестве значения\\*\<расширения >*\OpenWithProgids ключа. Этот раздел реестра со списком альтернативные идентификаторы ProgID, связанный с расширением файла. Приложения, связанные с перечисленных идентификаторы ProgID появляются в **открыть с помощью***название продукта* подменю. Если указано и то же приложение в обоих `OpenWithList` и `OpenWithProgids` ключей, операционная система выполняет слияние повторяющиеся значения.  
  
> [!NOTE]
>  `OpenWithProgids` Ключа поддерживается только в Windows XP. Так как в других операционных системах игнорировать этот ключ, не используйте его как только регистрация для обработчиков файлов. Используйте этот ключ для повышения удобства работы пользователя в Windows XP.  
  
 В качестве значения типа REG_NONE добавьте нужные идентификаторы ProgID. Ниже приведен пример регистрации идентификаторы ProgID для расширения имени файла (. *ext*).  
  
```  
HKEY_CLASSES_ROOT\  
   .ext\  
      (default)="MyProduct.ext.14.0"  
      OpenWithProgids  
         progid        REG_NONE (zero-length binary value)  
         otherprogid   REG_NONE (zero-length binary value)  
```  
  
 Идентификатор ProgID, заданный как значение по умолчанию для расширения файла — обработчика файлов по умолчанию. Если изменить идентификатор ProgID для расширения имени файла, которая поставлялась с предыдущей версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] или может выполняться на другие приложения, то необходимо зарегистрировать `OpenWithProgids` ключ для расширения файла и укажите новый идентификатор ProgID в списке вместе с старые идентификаторы ProgID, обслуживаемых. Пример:  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)="VisualStudio.vcproj.14.0"  
      OpenWithProgids  
         vcprojfile              //old progid  
         VisualStudio.vcproj.12.0 //old progid  
         VisualStudio.vcproj.14.0 //new progid  
```  
  
 Если старый идентификатор ProgID содержит команды, связанные с ним, а затем эти команды также будет отображаться в разделе **открыть с помощью** *название продукта* в контекстном меню.  
  
## <a name="see-also"></a>См. также  
 [По расширениям файлов](../extensibility/about-file-name-extensions.md)   
 [Регистрация команд для расширений имен файлов](../extensibility/registering-verbs-for-file-name-extensions.md)