---
title: "&lt;customErrorReporting&gt; элемент (развертывание ClickOnce) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords: <customErrorReporting> element [ClickOnce deployment manifest]
ms.assetid: 7d31816e-c692-46b5-9cc9-753284b3bcda
caps.latest.revision: "6"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: b6b6726ebf45522834d916897f456952b66a3605
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ltcustomerrorreportinggt-element-clickonce-deployment"></a>&lt;customErrorReporting&gt; элемент (развертывание ClickOnce)
Задает отображаемый в случае ошибки URI.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<customErrorReporting  
   uri  
/>  
```  
  
## <a name="remarks"></a>Примечания  
 Этот элемент является необязательным. Без него [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] отображает диалоговое окно ошибки, показывающая стека исключений. Если `customErrorReporting` элемент присутствует, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] будет отображаться вместо URI, обозначенном `uri` параметра. Целевой URI будет включать класс внешних исключений, класс внутренних исключений и во внутреннем сообщении исключения в качестве параметров.  
  
 Этот элемент используется для добавления в приложение функций создания отчетов. Поскольку сформированный URI включает сведения о типе ошибки, веб-сайта можно проанализировать эти сведения и отобразить, например, об устранении.  
  
## <a name="example"></a>Пример  
 В следующем фрагменте кода показано `customErrorReporting` элемента вместе с сформированный URI, он может выдавать.  
  
```  
<customErrorReporting uri=http://www.contoso.com/applications/error.asp />  
  
Example Generated Error:  
http://www.contoso.com/applications/error.asp? outer=System.Deployment.Application.InvalidDeploymentException&&inner=System.Deployment.Application.InvalidDeploymentException&&msg=The%20application%20manifest%20is%20signed,%20but%20the%20deployment%20manifest%20is%20unsigned.%20Both%20manifests%20must%20be%20either%20signed%20or%20unsigned.  
```  
  
## <a name="see-also"></a>См. также  
 [Манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md)