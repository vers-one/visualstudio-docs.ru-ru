---
title: "IRemoteDebugApplication110::GetCurrentDebuggerOptions | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IRemoteDebugApplication110::GetCurrentDebuggerOptions"
ms.assetid: a6e9cae1-e8f3-4d62-b133-52e9ca12ba7a
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IRemoteDebugApplication110::GetCurrentDebuggerOptions
Возвращает набор параметров, которые в данный момент включены.  
  
> [!IMPORTANT]
>  [Интерфейс IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md) реализуется PDM v11.0 и большим.  Обнаружен в activdbg100.h.  
  
## Синтаксис  
  
```cpp  
HRESULT GetCurrentDebuggerOptions([out] enum SCRIPT_DEBUGGER_OPTIONS* pCurrentOptions);  
```  
  
#### Параметры  
 `pCurrentOptions`  
 \[out\] текущие параметры.  
  
## См. также  
 [Интерфейс IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md)   
 [IRemoteDebugApplication110 — интерфейс](../../winscript/reference/iremotedebugapplication110-interface.md)