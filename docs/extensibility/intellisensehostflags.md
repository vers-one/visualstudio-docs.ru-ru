---
title: "IntelliSenseHostFlags | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IntellisenseHostFlags
helpviewer_keywords:
- IntelliSense, IntellisenseHostFlags enumeration
- IntellisenseHostFlags enumeration
ms.assetid: 0930640b-eb84-48ef-a8f7-d4268f55c99c
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 36cf7ba40deba4bd133f2c4baf92c310665ed275
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="intellisensehostflags"></a>IntelliSenseHostFlags
Задает флаги узла IntelliSense.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum IntellisenseHostFlags  
{  
    IHF_READONLYCONTEXT      = 0x00000001  
    IHF_NOSEPARATESUBJECT    = 0x00000002  
    IHF_SINGLELINESUBJECT    = 0x00000004  
    IHF_FORCECOMMITTOCONTEXT = 0x00000008  
    IHF_OVERTYPE             = 0x00000010  
};  
```  
  
#### <a name="parameters"></a>Параметры  
  
|Участники|Описание:|  
|-------------|-----------------|  
|`IHF_READONLYCONTEXT`|Контекст буфер доступен только для чтения.|  
|`IHF_NOSEPARATESUBJECT`|Нет текста для темы. Контекст буфер содержит целевой IntelliSense (подразумевает `!IHF_READONLYCONTEXT`).|  
|`IHF_SINGLELINESUBJECT`|Текст темы не несколькими-строки поддерживает.|  
|`IHF_FORCECOMMITTOCONTEXT`|Эквивалентно `CanCommitIntoReadOnlyBuffer`.|  
|`IHF_OVERTYPE`|Изменение (в теме или контекста) должны выполняться в режиме замены.|  
  
## <a name="requirements"></a>Требования  
 SingleFileeditor.idl  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.TextManager.Interop>