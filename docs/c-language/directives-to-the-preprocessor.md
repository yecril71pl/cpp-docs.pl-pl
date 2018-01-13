---
title: Dyrektywy preprocesora | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: adc6251e-cf6b-4508-bdbb-55f446c838d3
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 764bfd086612a10076e5c4800768b7b850ddbc7e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="directives-to-the-preprocessor"></a>Dyrektywy preprocesora
"Dyrektywy" powoduje, że preprocesora C, aby wykonywać konkretną akcję na tekst program przed kompilacji. [Dyrektywy preprocesora](../preprocessor/preprocessor-directives.md) w pełni opisano *odwołania preprocesora*. W tym przykładzie użyto dyrektywy preprocesora `#define`:  
  
```  
#define MAX 100  
```  
  
 Ta instrukcja informuje kompilator, aby zamienić każde wystąpienie `MAX` przez `100` przed kompilacji. Dyrektywy preprocesora kompilatora C są:  
  
|#define|#endif|#ifdef|#line|  
|--------------|-------------|-------------|------------|  
|`#elif`|`#error`|**#ifndef**|**#pragma**|  
|`#else`|`#if`|`#include`|`#undef`|  
  
## <a name="see-also"></a>Zobacz też  
 [Pliki źródłowe i programy źródłowe](../c-language/source-files-and-source-programs.md)