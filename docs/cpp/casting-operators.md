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
ms.openlocfilehash: 5b2aa683f539e643127f8f71ff536d4c2ca2c9c0
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39407529"
---
# <a name="casting-operators"></a>Operatory rzutowania
Wiele operatorów rzutowania są specyficzne dla języka C++. Te operatory są przeznaczone do usunięcia części niejednoznaczności i zagrożenia związane z stare rzutowań języka C w stylu. Są to:  
  
-   [dynamic_cast](../cpp/dynamic-cast-operator.md) używany na potrzeby konwersji polimorficzne typy.  
  
-   [static_cast](../cpp/static-cast-operator.md) używany na potrzeby konwersji typów niepolimorficznych.  
  
-   [Operator const_cast](../cpp/const-cast-operator.md) służy do usuwania **const**, **volatile**, i **__unaligned** atrybutów.  
  
-   [reinterpret_cast](../cpp/reinterpret-cast-operator.md) używane dla prostych reinterpretation bitów.  
  
-   [safe_cast](../windows/safe-cast-cpp-component-extensions.md) użyta do wyprodukowania podlegające weryfikacji MSIL.  
  
 Użyj **const_cast** i **reinterpret_cast** w ostateczności, ponieważ te operatory przedstawić same zagrożenia jako stary rzutowań w stylu. Jednak są nadal niezbędne w celu całkowitego zastąpienia starego rzutowań w stylu.  
  
## <a name="see-also"></a>Zobacz także  
 [Rzutowanie](../cpp/casting.md)