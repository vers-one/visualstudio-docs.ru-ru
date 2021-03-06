---
title: "Практическое руководство. Создание сравнительного отчета профилировщика с помощью командной строки | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 00548d16-eb5b-46f7-8a65-862f98a43831
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b3eb863a53b1e03ca71db9c18a1d8188ef47b392
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-profiler-comparison-report-from-a-command-prompt"></a>Практическое руководство. Создание отчета сравнения профилировщиков с помощью командной строки
Вы можете создать отчет Средств профилирования [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] о результатах сравнения данных по производительности в двух файлах данных профилирования (VSP или VSPS). В отчете приводятся различия, снижение производительности и улучшения в одном сеансе профилирования по сравнению с другим. Значения в отчете отражают отклонения или степень изменения по сравнению с базовым планом в первом из указанных файлов. Это отклонение вычисляется на основе разности между старым (базовым) значением и результатом нового анализа. Сравнение данных профилирования может выполняться на основе функций кода, модулей приложения, строк, указателей инструкций и типов.  
  
 Чтобы получить список идентификаторов сопоставляемых категорий и полей, используйте следующую команду:  
  
 **VSPerfReport /querydifftables**  *имя_файла_VSP1* *имя_файла_VSP2*  
  
 Для создания сравнительного отчета используйте следующий синтаксис:  
  
 **VSPerfReport /diff**  `VspFileName1` *имя_файла_VSP2* [**/**`Options`]  
  
 В команду **VSPerfReport /diff** можно добавить параметры из приведенной ниже таблицы.  
  
|Параметр|Описание:|  
|------------|-----------------|  
|**DiffThreshold:**[*Значение*]|Различия между значениями не учитываются, если они ниже заданного порогового значения. Кроме того, значения ниже данного порога не отображаются.|  
|**DiffTable:** *Имя_таблицы*|Для сравнения файлов используется указанная таблица. По умолчанию используется таблица функций. Укажите идентификатор, содержащийся в списке **VSPerfReport /querydifftables**.|  
|**DiffColumn:** *Имя_столбца*|Для сравнения значений используется указанный столбец. По умолчанию используется столбец, содержащий процентное значение исключительного времени. Укажите идентификатор, содержащийся в списке **VSPerfReport /querydifftables**.|