---
title: "Практическое руководство. Создание наследования между типами (конструктор классов) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.classdesigner.inheritanceline
helpviewer_keywords:
- inheritance, relationship defining
- relationships, defining inheritance
ms.assetid: 3786a21c-8022-4bf5-9d13-740fd354e93c
caps.latest.revision: "30"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b939da3ae4020cc6412f9b1767d5bef8bce05472
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-inheritance-between-types-class-designer"></a>Практическое руководство. Создание наследования между типами (конструктор классов)
Чтобы создать отношение наследования между двумя типами на диаграмме классов, используя Конструктор классов, соедините базовый тип с производными типами. Отношение наследования может существовать между двумя классами, между классом и интерфейсом или между двумя интерфейсами.  
  
### <a name="to-create-an-inheritance-between-types"></a>Создание наследования между типами  
  
1.  В Обозревателе решений выберите проект и откройте файл схемы классов (CD-файл).  
  
     Если диаграмма классов не существует, создайте ее. См. раздел [Практическое руководство. Добавление схем классов в проекты](how-to-add-class-diagrams-to-projects.md).  
  
2.  На **панели инструментов** в разделе **Конструктор классов** щелкните элемент **Наследование**.  
  
3.  На диаграмме классов нарисуйте линию наследования между нужными типами, начав с:  
  
    -   производного класса, связав его с базовым классом;  
  
    -   класса реализации, связав его с реализованным интерфейсом;  
  
    -   расширяемого интерфейса, связав его с расширенным интерфейсом.  
  
4.  Если производный тип основан на универсальном типе, можно щелкнуть линию наследования. В окне **Свойства** задайте свойство **Аргументы типа** в соответствии с типом, который необходим для универсального типа.  
  
    > [!NOTE]
    >  Если родительский абстрактный класс содержит хотя бы один абстрактный член, то все абстрактные члены реализуются как неабстрактные наследующие классы.  
    >   
    >  Хотя вы можете визуализировать существующие универсальные типы, создавать новые универсальные типы нельзя. Вы также не можете изменить параметры существующих универсальных типов.  
  
## <a name="see-also"></a>См. также
[Наследование](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)   
[Основы наследования](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)   
[Практическое руководство. Просмотр отношения наследования между типами](how-to-view-inheritance-between-types.md)   
[Классы Visual C++ в конструкторе классов](visual-cpp-classes.md)