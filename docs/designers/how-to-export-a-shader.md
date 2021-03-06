---
title: "Практическое руководство. Экспорт шейдера | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0bd48bf4-9792-4456-a545-e462a2be668d
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 6b4c7cedd267ba02772db16e026803061933cf5d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-export-a-shader"></a>Практическое руководство. Экспорт шейдера
В этом документе показано, как использовать конструктор шейдеров для экспорта шейдера DGSL для использования в приложении.  
  
 В этом документе описана следующая операция:  
  
-   Экспорт шейдера  
  
## <a name="exporting-a-shader"></a>Экспорт шейдера  
 Чтобы использовать шейдер в приложении после создания с помощью конструктора шейдеров, его нужно экспортировать в формате, совместимый с API графики. Шейдер можно экспортировать разными способами для достижения различных целей.  
  
#### <a name="to-export-a-shader"></a>Экспорт шейдера  
  
1.  В [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] откройте файл **Визуальный граф шейдера (DGSL)**.  
  
     Если у вас нет файла **Визуальный граф шейдера (DGSL)**, создайте его, как описано в разделе [Практическое руководство. Создание простейшего шейдера цвета](../designers/how-to-create-a-basic-color-shader.md).  
  
2.  На панели инструментов **Конструктор шейдеров** выберите **Дополнительно**, **Экспорт**, **Экспортировать как**. Открывается диалоговое окно **Экспортировать шейдер**.  
  
3.  В раскрывающемся списке **Тип файла** выберите формат для экспорта.  
  
     Ниже приведен список доступных форматов:  
  
     **Шейдер пикселей HLSL (\*.hlsl)**  
     Экспортирует шейдер в виде исходного кода HLSL. Этот параметр позволяет позднее изменить шейдер, даже после его развертывания в приложении. Это может упростить отладку и исправление кода с учетом проблем, возникших у конечных пользователей, но также позволяет пользователю легче вносить в шейдер нежелательные изменения, например чтобы получить незаслуженное преимущество в конкурентной игре. Это также может увеличить время загрузки шейдера.  
  
     **Скомпилированный шейдер пикселей (\*.cso)**  
     Экспортирует шейдер в виде байт-кода HLSL. Этот параметр позволяет позднее изменить шейдер, даже после его развертывания в приложении. Это может упростить отладку и исправление кода с учетом проблем, возникших у конечных пользователей, а так как шейдер компилируется предварительно, его загрузка приложением не создает дополнительных издержек во время выполнения. Достаточно опытные пользователи все равно могут внести нежелательные изменения в шейдер, однако компиляция шейдера значительно усложняет эту задачу.  
  
     **Заголовок C++ (\*.h)**  
     Экспортирует шейдер в виде заголовка в стиле C, который определяет массив байтов, содержащий байт-код HLSL. Этот параметр увеличивает временные затраты на отладку и исправление кода с учетом проблем, возникших у конечных пользователей, так как для проверки исправления приложения требуется перекомпилировать. Однако этот параметр делает практически невозможным внесение нежелательных изменений в шейдер после его развертывания в приложении.  
  
4.  В поле со списком **Имя файла** укажите имя для экспортируемого шейдера и нажмите кнопку **Сохранить**.  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Создание простейшего шейдера цвета](../designers/how-to-create-a-basic-color-shader.md)   
 [Конструктор шейдеров](../designers/shader-designer.md)