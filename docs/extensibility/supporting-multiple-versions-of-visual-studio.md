---
title: "Поддержка нескольких версий Visual Studio | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio, supporting multiple versions
- VSPackages, side-by-side compatibility
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0c03df6edc54948060fa3b1f8eee264646a80f38
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="supporting-multiple-versions-of-visual-studio"></a>Поддержка нескольких версий Visual Studio
Термин *side-by-side* означает, что можно установить и поддерживать несколько версий продукта на одном компьютере. Для пакетов VSPackage, это означает, что пользователь может иметь несколько версий Visual Studio установлена на том же компьютере. Тем не менее не может иметь side-by-side версии пакетов VSPackage загружаются в одной версии Visual Studio.  
  
 Прежде чем вносить VSPackage может быть загружена в side-by-side версий Visual Studio, необходимо учитывайте следующее:  
  
-   Необходимо определить стратегию side-by-side реализации, необходимо следовать.  
  
     Дополнительные сведения см. в разделе [Выбор между общим и пакеты VSPackage с версиями](../extensibility/choosing-between-shared-and-versioned-vspackages.md).  
  
-   Стратегии реализации должен лежать в собственных форматах файлов решения и проекта.  
  
     Дополнительные сведения см. в разделе [обновление пользовательских проектов](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects) и [регистрации расширения имен файлов для развертываний Side-By-Side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).  
  
-   Установщик должен обрабатывать стратегии реализации, чтобы версий компонентов и компонентов, совместно используется всеми версиями правильности установки и регистрации.  
  
     Дополнительные сведения см. в разделе [Установка пакетов VSPackage с помощью установщика Windows](../extensibility/internals/installing-vspackages-with-windows-installer.md) , а также [управления компонентами](../extensibility/internals/component-management.md).  
  
    > [!NOTE]
    >  Установка версии Visual Studio также устанавливает соответствующую версию [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Например, вместе с Visual Studio 2010 и Visual Studio 2012 на том же компьютере устанавливается версии 4.0 и 4.5 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]соответственно.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Выбор между общими пакетами VSPackage и пакетами с контролем версий](../extensibility/choosing-between-shared-and-versioned-vspackages.md)  
 Описываются способы решения проблемы side-by-side в пакете VSPackage.  
  
 [Регистрация расширений имен файлов для параллельных развертываний](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)  
 Описывает, как VSPackage можно зарегистрировать в сценарии side-by-side сопоставления файлов.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Установка пакетов VSPackage с помощью установщика Windows](../extensibility/internals/installing-vspackages-with-windows-installer.md)  
