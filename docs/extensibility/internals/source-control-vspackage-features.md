---
title: "Источник VSPackage возможности управления | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control packages, features
ms.assetid: 26c3ffda-22b8-4345-9fb6-2883f37699aa
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c16fde6cb9dcb29428ad2d52a08b53cffb9f9850
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="source-control-vspackage-features"></a>Возможностей VSPackage системы управления версиями
В этом разделе описываются различные возможности элемента управления источника пакета VSPackage. В нем изложены регистрации и выбора сведения для таких пакетов VSPackage и рассматриваются три функции, связанные с управлением главный источник: обработка событий запроса сохранить изменения запроса (QEQS), глифов замены и пользовательского интерфейса (UI) для системы управления версиями функции.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Регистрация и выбора](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)  
 Описаны способы регистрации и выбора пакета.  
  
 [Изменение запроса запроса сохранения](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)  
 Объясняется роль изменения запроса запроса-сохранить события и как они обрабатываются системой управления версиями пакета VSPackage.  
  
 [Глиф управления](../../extensibility/internals/glyph-control-source-control-vspackage.md)  
 Описание уровней управления глиф и способы их реализации.  
  
 [Пользовательский интерфейс](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)  
 Описываются элементы пользовательского интерфейса, можно указать VSPackage системы управления версиями.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Создание пакета VSPackage системы управления версиями](../../extensibility/internals/creating-a-source-control-vspackage.md)  
 Описывает, как создать пакет VSPackage, который не только предоставляет функций системы управления версиями, но можно использовать для настройки системы управления версиями [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] система управления версиями пользовательского интерфейса.