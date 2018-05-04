---
title: Operatory rzutowania | Dokumentacja firmy Microsoft
ms.custom: index-page
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], casting
- casting operators [C++]
ms.assetid: 16240348-26bc-4f77-8eab-57253f00ce52
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bf4204e55811cd33fa48e2b3a07d3058100729ac
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="casting-operators"></a>Operatory rzutowania
Operatory rzutowania kilka są specyficzne dla języka C++. Te operatory są przeznaczone do usunięcia części niejednoznaczności i ryzyka związanego z używaniem w starym stylu C języka rzutowania. Są to:  
  
-   [dynamic_cast](../cpp/dynamic-cast-operator.md) używany na potrzeby konwersji typach polimorficznych.  
  
-   [static_cast](../cpp/static-cast-operator.md) używany na potrzeby konwersji typów nonpolymorphic.  
  
-   [Operator const_cast](../cpp/const-cast-operator.md) służy do usuwania `const`, `volatile`, i `__unaligned` atrybutów.  
  
-   [reinterpret_cast](../cpp/reinterpret-cast-operator.md) używany dla prostego reinterpretation bitów.  
  
-   [safe_cast](../windows/safe-cast-cpp-component-extensions.md) użyta do wyprodukowania MSIL możliwe do zweryfikowania.  
  
 Użyj `const_cast` i `reinterpret_cast` w ostateczności, ponieważ te operatory przedstawienia tego samego zagrożenia jako starego rzutowania w stylu. Jednak są nadal potrzebne do całkowicie zastąpić starego rzutowania w stylu.  
  
## <a name="see-also"></a>Zobacz też  
 [Rzutowanie](../cpp/casting.md)