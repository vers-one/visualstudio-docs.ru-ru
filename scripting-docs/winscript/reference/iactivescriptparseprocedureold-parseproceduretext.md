---
title: "IActiveScriptParseProcedureOld::ParseProcedureText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptParseProcedureOld.ParseProcedureText
apilocation: jscript.dll
helpviewer_keywords: 
  - "IActiveScriptParseProcedureOld::ParseProcedureText"
ms.assetid: 21a21313-35ce-432d-b9a6-7999065f19ac
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptParseProcedureOld::ParseProcedureText
Анализирует заданную процедура кода и добавляет анонимная процедуры в пространстве имен.  
  
## Синтаксис  
  
```  
HRESULT ParseProcedureText(  
   LPCOLESTR    pstrCode,  
   LPCOLESTR    pstrFormalParams,  
   LPCOLESTR    pstrItemName,  
   IUnknown*    punkContext,  
   LPCOLESTR    pstrDelimiter,  
   DWORD_PTR    dwSourceContextCookie,  
   ULONG        ulStartingLineNumber,  
   DWORD        dwFlags,  
   IDispatch**  ppdisp  
);  
```  
  
#### Параметры  
 `pstrCode`  
 \[in\] текст процедуры, которые необходимо вычислить.  Интерпретация зависит от этой строки язык сценариев.  
  
 `pstrFormalParams`  
 \[in\] имена формальных параметров для процедуры.  Имена параметров необходимо отделить с соответствующими разделителями для обработчика скриптов.  Имена не должны быть заключены в скобки.  
  
 `pstrItemName`  
 \[in\] имя именованного элемента, который предоставляет контекст, в котором необходимо оценить процедуры.  Если этот параметр `NULL`, код выполняется в контексте обработчика скриптов глобальном.  
  
 `punkContext`  
 \[in\] объект контекста.  Этот объект зарезервирован для использования в среду отладки, где тот контекст может быть предусмотрен отладчиком, представленный активный контекст среды выполнения.  Если этот параметр `NULL`, система использует `pstrItemName` для указания контекста.  
  
 `pstrDelimiter`  
 \[in\] разделитель элемент \-\- процедуры.  При `pstrCode` анализироватьо из потока текста, основное приложение обычно использует разделитель, например 2 одинарных кавычки \("\), чтобы определить окончание процедуры.  Этот параметр задает разделитель, используемый основным приложением, что обработчик скриптов, чтобы обеспечить определенное условное, примитивное предварительная обработка \(например, заменящ одинарная кавычка \('\) с 2 одинарными кавычками для использования в качестве разделителя\).  То, как \(и, если\), то обработчик скриптов использует этот зависит от информации обработчика скриптов.  Установите этот параметр в `NULL` если основное приложение не использует разделитель для обозначения конца процедуры.  
  
 `dwSourceContextCookie`  
 \[in\] Приложение\- указанное значение, которое используется для отладки.  
  
 `ulStartingLineNumber`  
 \[in\] Нул\- на основе значение, указывающее, на которой линию синтаксического анализа.  
  
 `dwFlags`  
 \[in\] флаги, связанные с процедурой.  Может оказаться сочетание этих значений.  
  
|Константа|Значение|Значение|  
|---------------|--------------|--------------|  
|SCRIPTPROC\_ISEXPRESSION|0x00000020|Указывает, что выполнение кода в `pstrCode` выражение, которое представляет возвращаемое значение процедуры.|  
|SCRIPTPROC\_IMPLICIT\_THIS|0x00000100|Указывает, что указатель `this` включен в области процедуры.|  
|SCRIPTPROC\_IMPLICIT\_PARENTS|0x00000200|Указывает, что указатель `this` родительские объекты включаются в области процедуры.|  
  
 `ppdisp`  
 \[out\] возвращает программу\-оболочку диспетчера, где по умолчанию метод процедура внешним синтаксическим анализом этим методом.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_INVALIDARG`|Аргумент был недопустимым.|  
|`E_POINTER`|Недопустимый указатель был определен.|  
|`E_NOTIMPL`|Этот метод не поддерживается.  Обработчик скриптов не поддерживает добавление времени выполнения процедур в пространстве имен.|  
|`E_UNEXPECTED`|Вызов не ожидался \(например, обработчик скриптов в неинициализированном состоянии или закрыть\).|  
|`OLESCRIPT_E_SYNTAX`|Произошла неопознанная синтаксическая ошибка в процедуре.|  
|`S_FALSE`|Обработчик скриптов не поддерживает объект диспетчера; параметр `ppdisp` ему присваивается `NULL`.|  
  
## Заметки  
 Код скрипта не оценивается во время этого вызова; вместо этого процедуру компилироватьа в метод `ppdisp`, где она может быть Позвонитьа скриптом в будущем.  
  
 Этот интерфейс нерекомендуем в использование интерфейса `IActiveScriptParseProcedure`.  Метод `IActiveScriptParseProcedure::ParseProcedureText` аналогичен этому методу, но он позволяет имя процедуры, которую необходимо задать.  Во всех случаях, `IActiveScriptParseProcedure::ParseProcedureText` должно использоваться.  
  
## См. также  
 [Интерфейс IActiveScriptParseProcedureOld](../../winscript/reference/iactivescriptparseprocedureold-interface.md)   
 [IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)