---
title: "CA1810: Инициализируйте ссылочного типа статических полей встроенными | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
helpviewer_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
ms.assetid: e9693118-a914-4efb-9550-ec659d8d97d2
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4b3a6ffe04be6116fddc225d0820d3709644fe52
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ca1810-initialize-reference-type-static-fields-inline"></a>CA1810: инициализируйте статические поля ссылочного типа встроенными средствами
|||  
|-|-|  
|TypeName|InitializeReferenceTypeStaticFieldsInline|  
|CheckId|CA1810|  
|Категория|Microsoft.Performance|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Ссылочный тип объявляет явный статический конструктор.  
  
## <a name="rule-description"></a>Описание правила  
 Если в типе объявляется явный статический конструктор, компилятор JIT добавляет проверку в каждый статический метод и конструктор экземпляров этого типа, чтобы убедиться, что статический конструктор уже вызывался ранее. Статическая инициализация выполняется при доступе к статическому члену или при создании экземпляра типа. Тем не менее статическая инициализация не выполняется, если объявить переменную типа, но она не используется, который может быть важно, если инициализация изменяет глобальное состояние.  
  
 При всех статических данных инициализированный встроенным образом и не объявляется явный статический конструктор, добавить промежуточного языка MSIL компиляторы Microsoft `beforefieldinit` флаг и неявный статический конструктор, который инициализирует статические данные в тип MSIL Определение. Когда JIT-компилятор встречает `beforefieldinit` флаг в большинстве случаев проверки статических конструкторов не добавляются. Статическая инициализация будет гарантированно выполнена перед осуществляется статических полей, но не перед вызовом статического метода или экземпляр конструктора. Обратите внимание, что статическая инициализация может произойти в любое время после объявления переменной типа.  
  
 Проверки статических конструкторов могут привести к снижению производительности. Статический конструктор, часто используется только для инициализации статических полей, в которых необходимо только убедиться статическая инициализация происходит до первого обращения статического поля. `beforefieldinit` Поведение подходит для этих и других типов. Это только подходит, если статическая инициализация влияет на глобальное состояние и выполняется одно из следующих условий:  
  
-   Влияние на глобальное состояние является затрат и не является обязательным, если тип не используется.  
  
-   Изменение глобального состояния может осуществляться без обращения к любому статическому полю типа.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, выполните инициализацию всех статических данных при их объявлении и удалите статический конструктор.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Можно безопасно подавить предупреждение из этого правила, если производительность не имеет значения; Если или глобальное состояние изменения, вызванные статическая инициализация сопряжено необходимо гарантировать возникает до вызова статического метода типа, или создать экземпляр типа.  
  
## <a name="example"></a>Пример  
 В следующем примере показано типом, `StaticConstructor`, нарушает правило и тип `NoStaticConstructor`, который заменяет статический конструктор на встроенную инициализацию в соответствии с правилом.  
  
 [!code-csharp[FxCop.Performance.RefTypeStaticCtor#1](../code-quality/codesnippet/CSharp/ca1810-initialize-reference-type-static-fields-inline_1.cs)]
 [!code-vb[FxCop.Performance.RefTypeStaticCtor#1](../code-quality/codesnippet/VisualBasic/ca1810-initialize-reference-type-static-fields-inline_1.vb)]  
  
 Обратите внимание, добавление `beforefieldinit` флаг в определении MSIL `NoStaticConstructor` класса.  
  
 **открытый .class автоматически ansi StaticConstructor**  
 **расширяет [mscorlib]System.Object**  
**{**  
**} / / конечного класса StaticConstructor**  
**.class открытый автоматически ansi beforefieldinit NoStaticConstructor**  
 **расширяет [mscorlib]System.Object**  
**{**  
**} / / конечного класса NoStaticConstructor**   
## <a name="related-rules"></a>Связанные правила  
 [CA2207: инициализируйте статические поля типа значений встроенными средствами](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)