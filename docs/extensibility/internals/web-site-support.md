---
title: "Веб-сайт поддержки | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: web site projects
ms.assetid: ce9f4266-bb64-4c09-be88-4bd6413f60d0
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 09b43963d657e8d1fe7aa24e98632d2ca46240c6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="web-site-support"></a>Поддержка веб-сайта
Веб-сайт проекта система представляет собой систему проектов, которая создает веб-проектов. Веб-проекты в свою очередь создавать веб-приложения. Проект веб-сайта создает один исполняемый файл для каждой веб-страницы, связанный код. Дополнительные исполняемые файлы создаются из файлов исходного кода в папке /App_Code.  
  
 Системы проектов веб-сайта создаются путем добавления шаблоны и атрибуты регистрации в существующей системе проектов. Один из этих атрибутов выбирает поставщика IntelliSense для языка. Реализация поставщика IntelliSense обрабатывает ссылки и вызывает компилятор языка, когда запрашивается смарт-веб-страницы, не кэшируется.  
  
 Компилятор языка, используемый для компиляции веб-страницы должны быть зарегистрированы в [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)]. Можно использовать [ \<компилятора > элемент](/dotnet/framework/configure-apps/file-schema/compiler/compiler-element) в файле Web.config для регистрации компилятора, как показано в следующем примере:  
  
```  
<system.codedom>  <compilers>    <compiler language="py;IronPython" extension=".py"       type="IronPython.CodeDom.PythonProvider, IronPython,       Version=1.0.2391.18146, Culture=neutral,       PublicKeyToken=b03f5f7f11d50a3a" />  </compilers></system.codedom>  
```  
  
## <a name="in-this-section"></a>В этом разделе  
 [Шаблоны поддержки веб-сайтов](../../extensibility/internals/web-site-support-templates.md)  
 Список шаблонов, которые можно использовать для создания новых проектов веб-сайтов и связанных элементах.  
  
 [Атрибуты поддержки веб-сайтов](../../extensibility/internals/web-site-support-attributes.md)  
 Представляет атрибуты регистрации, которые проект веб-сайта для подключения [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] и [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)].  
  
## <a name="related-sections"></a>Связанные разделы  
 [Веб-проекты](../../extensibility/internals/web-projects.md)  
 Представляет обзор двух видов веб-проектов, проектов веб-сайтов и проектов веб-приложений.