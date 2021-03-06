---
title: "Синтаксис пути домена | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, domain path
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: fb2b1dfa13bf00c29452798253198b2ad0e72e97
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="domain-path-syntax"></a>Синтаксис пути домена
В определениях доменного языка для поиска определенных элементов в модели используется синтаксис типа XPath.  
  
 Обычно работать с синтаксисом напрямую не нужно. Там, где он появляется в окне "Сведения" или "Свойства" доменного языка, можно щелкнуть стрелку вниз и использовать редактор пути. При этом путь появляется в поле формы только после того, как вы воспользуетесь редактором.  
  
 Путь домена имеет следующий вид:  
  
 *RelationshipName.PropertyName/!Role*  
  
 ![Отношение ссылки CommentReferencesSubjects](../modeling/media/dsl_reference.png "dsl_reference")  
  
 Синтаксис перебирает дерево модели. Например, доменной связи **CommentReferencesSubjects** в приведенном выше рисунке имеет **субъектов** роли. Сегмент пути **/! Subjectt** указывает, что путь завершается для элементов, доступных через **субъектов** роли.  
  
 Каждый сегмент начинается с имени доменной связи. Если обход, из элемента с отношением сегмента пути отображается как *Relationship.PropertyName*. В случае перехода по ссылке на элемент, сегмент пути отображается как *связь /! RoleName*.  
  
 Синтаксис пути разделяется косыми чертами. Каждый сегмент пути является переходом от элемента к связи (экземпляра отношения) или от связи к элементу. Сегменты пути часто отображаются в парах. Один сегмент пути представляет собой переход от элемента к связи, а следующий — от связи к элементу на другом конце. (Любая связь также может быть источником или целью самого отношения.)  
  
 Имя, используемое для перехода от элемента к связи, является значением роли `Property Name`. Имя, используемое для перехода от связи к элементу, является именем целевой роли.  
  
## <a name="see-also"></a>См. также  
 [Сведения о моделях, классах и отношениях](../modeling/understanding-models-classes-and-relationships.md)