---
title: "Общие сведения о свойствах пользовательского документа | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], custom properties
- custom document properties
- document-level customizations [Office development in Visual Studio], custom properties
- Office documents [Office development in Visual Studio], custom properties
- _AssemblyLocation property
- _AssemblyName property
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 672eaf3ed82a80983b919a37b2aeff4c99621f43
ms.sourcegitcommit: bfa26fd7426af0d065cb2eef3d6827b5d6f7986c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/20/2018
---
# <a name="custom-document-properties-overview"></a>Custom Document Properties Overview

При построении проекта уровня документа Visual Studio добавляет два пользовательских свойств документа в проекте: \_AssemblyLocation и \_AssemblyName. Когда пользователь открывает документ, приложение Microsoft Office проверяет эти настраиваемые свойства документа. Если они существуют в документе, приложение загружает [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], которая запускает настройку. Дополнительные сведения см. в разделе [архитектура решений Office в Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="assemblyname"></a>\_Имя сборки

Это свойство содержит идентификатор CLSID интерфейса в компоненте загрузчика решения Office [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Значение идентификатора CLSID — 4 4E3C66D5 - 58D-491E-A7D4-64AF99AF6E8B. Никогда не следует изменять это значение.

## <a name="assemblylocation"></a>\_AssemblyLocation

Это свойство содержит строку, подробную информацию о манифеста развертывания для настройки. Дополнительные сведения о манифестах см. в разделе [манифесты приложения и развертывания в решениях Office](../vsto/application-and-deployment-manifests-in-office-solutions.md).

 Значение свойства The_AssemblyLocation может иметь различные форматы, в зависимости от способа развертывания решения:

- Если решение публикуется устанавливаться с веб-сайта, UNC-путь или компакт-ДИСК или USB-накопитель, свойства _AssemblyLocation имеет формат *DeploymentManifestPath*|*SolutionID*. Следующая строка представляет пример:

     file://deployserver/MyShare/ExcelWorkbook1.vsto|74744e4b-e4d6-41eb-84f7-ad20346fe2d9

- При выполнении или отладке решения из Visual Studio, свойства _AssemblyLocation имеет формат *DeploymentManifestName*|*SolutionID*| vstolocal. Следующая строка представляет пример:

     ExcelWorkbook1.vsto|74744e4b-e4d6-41eb-84f7-ad20346fe2d9|vstolocal

 *SolutionID* представляет собой идентификатор GUID, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] используется для идентификации решения. *SolutionID* создается автоматически при построении проекта. **Vstolocal** условие указывает на [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , сборка должна быть загружена из той же папке, что и документ.

## <a name="see-also"></a>См. также

[Архитектура решений Office в Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
[архитектура настроек на уровне документа](../vsto/architecture-of-document-level-customizations.md)
[манифесты приложений и развертывания в решениях Office ](../vsto/application-and-deployment-manifests-in-office-solutions.md) 
 [Как: публикация решения Office с помощью ClickOnce](http://msdn.microsoft.com/en-us/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)
[как: создавать и изменять настраиваемые свойства документа](../vsto/how-to-create-and-modify-custom-document-properties.md)
