---
title: "Время выполнения машинного проверяет настройки | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.crt
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- runtime_checks pragma
- debugger, native run-time checks
- /RTC compiler option [C++], native run-time checks
- customizing CRT error checking
- native run-time checks, customizing
ms.assetid: 76a365fe-6439-49db-8603-34058b78e5a8
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a9483983b6cbd5644827af8f647425cce61502ab
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="native-run-time-checks-customization"></a>Настройка проверок во время выполнения машинного кода
При компиляции с **/RTC** (проверки времени выполнения) или использовать `runtime_checks` pragma, библиотеки времени выполнения C предоставляет проверки времени выполнения машинного кода. В некоторых случаях необходимо настроить проверки времени выполнения:  
  
-   для направления сообщений о проверке, осуществляемой во время выполнения, в файл или в другое место назначения, отличающиеся от используемого по умолчанию;  
  
-   чтобы определить место назначения для сообщения о проверке, осуществляемой во время выполнения отладчиком стороннего поставщика;  
  
-   для представления сообщений о проверке во время выполнения из программы, скомпилированной с рабочей версией библиотеки времени выполнения языка C. Для представления сообщения об ошибке во время выполнения окончательные версии библиотеки не используют `_CrtDbgReportW`. Вместо этого они отображают **Assert** диалоговое окно для каждой ошибки времени выполнения.  
  
 Для настройки процесса проверки ошибок во время выполнения можно:  
  
-   написать функцию, сообщающую об ошибке времени выполнения. Дополнительные сведения см. в разделе [как: написать функцию отчетов во время выполнения ошибки](../debugger/how-to-write-a-run-time-error-reporting-function.md).  
  
-   настроить место назначения для сообщения об ошибке;  
  
-   запросить сведения об ошибках проверок времени выполнения;  
  
## <a name="customize-the-error-message-destination"></a>Настройка места назначения для сообщения об ошибке  
 Если для уведомления об ошибках используется функция `_CrtDbgReportW`, то для определения места назначения сообщений об этих ошибках можно использовать `_CrtSetReportMode`.  
  
 Когда применяется пользовательская функция, сообщающая об ошибках, для связывания ошибки и типа сообщения следует использовать функцию `_RTC_SetErrorType`.  
  
## <a name="query-for-information-about-run-time-checks"></a>Запрос сведений о проверках времени выполнения  
 `_RTC_NumErrors` возвращает количество типов ошибок, обнаруженных в процессе проверки во время выполнения. Для получения краткого описания каждой ошибки можно использовать цикл от 0 до возвращенного `_RTC_NumErrors` значения, передавая номер итерации на каждом шаге в функцию `_RTC_GetErrDesc`. Дополнительные сведения см. в разделе [_RTC_NumErrors](/cpp/c-runtime-library/reference/rtc-numerrors) и [_RTC_GetErrDesc](/cpp/c-runtime-library/reference/rtc-geterrdesc).  
  
## <a name="see-also"></a>См. также  
 [Как: использовать проверки времени выполнения машинного кода](../debugger/how-to-use-native-run-time-checks.md)   
 [runtime_checks](/cpp/preprocessor/runtime-checks)   
 [_CrtDbgReport, _CrtDbgReportW](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw)