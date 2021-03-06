---
title: "Регистрация VSPackage | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: ecd20da8-b04b-4141-a8f4-a2ef91dd597a
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1405fbeba34f3e3aa9c645f6eaffe90fe6ac9036
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="vspackage-registration"></a>Регистрация VSPackage
Пакеты VSPackage необходимо сообщить [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , устанавливаются и должен быть загружен. Этот процесс выполняется путем записи данных в реестре. Это типичный задания установщика.  
  
> [!NOTE]
>  Распространенной практикой является во время разработки пакета VSPackage для использования автоматической регистрации. Однако [!INCLUDE[vsipprvsip](../../extensibility/includes/vsipprvsip_md.md)] партнеры не может поставляться своих продуктов с помощью автоматической регистрации в процессе установки.  
  
 Записи реестра в пакет установщика Windows обычно устанавливаются в таблице реестра. Можно также зарегистрировать расширения файлов в таблице реестра. Тем не менее установщик Windows предоставляет встроенную поддержку через программный идентификатор (ProgId), класса, расширение и таблицы команд. Дополнительные сведения см. в разделе [таблиц базы данных](http://msdn.microsoft.com/library/aa368259\(VS.85\).aspx).  
  
 Убедитесь, что записей реестра, связаны с компонентом, который подходит для выбранной стратегии side-by-side. Например записи реестра для общего файла должен быть связан с компонентом этот файл установщика Windows. Аналогичным образом записи реестра для конкретной версии файла должен быть связан с компонентом этого файла. В противном случае установка или удаление VSPackage для одной версии [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] может привести к нарушению VSPackage в других версиях. Дополнительные сведения см. в разделе [поддержка нескольких версий Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)  
  
> [!NOTE]
>  Чтобы управлять регистрацией проще всего использовать те же данные в те же файлы для регистрации во время установки и регистрации разработчика. Например некоторые средства развертывания установщика можно использовать файл в формате реестра во время построения. Если разработчики Ведение REG-файлы для своих собственных ежедневной разработки и отладки, эти файлы могут быть включены в установщик автоматически. Если вы не можете делиться автоматически регистрационные данные, необходимо убедиться, что установщик копию данных регистрации текущего.  
  
## <a name="registering-unmanaged-vspackages"></a>Регистрация неуправляемые пакеты VSPackage  
 Файлы .rgs стиле ATL использовать неуправляемые пакеты VSPackage, (включая выданные шаблона пакета Visual Studio) для хранения сведений о регистрации. Формат файла .rgs относится к ATL и обычно не могут быть использованы в качестве-— при установке средства разработки. Сведения о регистрации для установщика VSPackage должна поддерживаться отдельно. Например разработчики можно хранить файлы в формате .reg в соответствии с .rgs изменения в файле. REG-файлов может быть объединены с RegEdit разработках или занятая установщика.  
  
## <a name="registering-managed-vspackages"></a>Регистрация управляемые пакеты VSPackage  
 Средство RegPkg считывает атрибуты регистрации из управляемого пакета VSPackage и могут либо записывать сведения непосредственно реестра или записи .reg формат файлов, которые могут быть использованы программой установки.  
  
> [!NOTE]
>  Средство RegPkg не распространяются и не может использоваться для регистрации VSPackage на компьютере пользователя.  
  
## <a name="why-vspackages-should-not-self-register-at-install-time"></a>Почему пакеты VSPackage не нужно самостоятельно регистрировать во время установки  
 К установщикам VSPackage не следует полагаться на автоматическую регистрацию. На первый взгляд для сохранения значений реестра VSPackage только в пакете VSPackage, сам может показаться хорошей идеей. Учитывая, что разработчики должны значений реестра, доступных для своей работы, процедуры и тестирования, имеет смысл во избежание обслуживание отдельную копию данных реестра в установщике. Установщик можно полагаться на сам пакет VSPackage для записи значений реестра.  
  
 Наряду с хорошо теоретически самостоятельной регистрации имеет несколько недостатков, сделать его непригодным для установки пакета VSPackage:  
  
-   Правильно поддержки установки, удаления, откат установки и удаления отката необходимо создать четыре настраиваемые действия для каждого управляемого пакета VSPackage, которая самостоятельно регистрируется путем вызова RegPkg.  
  
-   Подхода к поддержке side-by-side может потребоваться создать четыре настраиваемые действия, которые следует вызвать RegSvr32 или RegPkg для каждой поддерживаемой версии [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
-   Установка с самостоятельно зарегистрированных модулей невозможно безопасно откат, поскольку никак не получали Если самостоятельно зарегистрирован ключи используются в другой функции или приложением.  
  
-   Самостоятельно Зарегистрированные DLL иногда ссылки на вспомогательные библиотеки DLL, которые не существуют или имеют неправильную версию. Напротив установщика Windows можно зарегистрировать библиотеки DLL с помощью таблицы независимо от текущего состояния системы.  
  
-   Код автоматической регистрации может быть запрещен доступ к сетевым ресурсам, например библиотек типов, если компонент не указан как выполнения из источника и перечислены в таблице SelfReg. Это может привести к установке компонента к сбою при выполнении административной установки.  
  
## <a name="see-also"></a>См. также  
 [Установщик Windows](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)   
 [Регистрация управляемых пакетов](http://msdn.microsoft.com/en-us/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)