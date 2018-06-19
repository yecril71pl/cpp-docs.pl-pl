---
title: Dyrektywy preprocesora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: adc6251e-cf6b-4508-bdbb-55f446c838d3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 711e28a569cefbb500a98ab33cd22c527a5fd7c5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32382906"
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