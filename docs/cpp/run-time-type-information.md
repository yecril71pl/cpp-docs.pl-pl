---
title: Informacje typu Run-Time | Dokumentacja firmy Microsoft
ms.custom: index-page
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- RTTI compiler option
- run-time type information
- run time, type checking
- type information, run-time type checking
- run-time checks, type checking
ms.assetid: becbd0e5-0439-4c61-854f-8a74f7160c54
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b23188b3dd49afb619576fa9cdcece69feca94f3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="run-time-type-information"></a>Informacje o typie uzyskiwanym w czasie rzeczywistym
Informacje typu Run-time (RTTI) jest mechanizm umożliwiający typ obiektu określonych podczas wykonywania programu. RTTI został dodany do języka C++, ponieważ wielu dostawców bibliotek klas zostały wdrażanie tej funkcji samodzielnie. Przyczyną niezgodności między bibliotekami. W związku z tym stała się oczywista że obsługa została potrzebne informacje typu run-time na poziomie języka.  
  
 Dla jasności ten omówienie RTTI jest prawie całkowicie ograniczone do wskaźników. Jednak kwestie omówione dotyczą również odwołań.  
  
 Istnieją trzy główne elementy języka C++ do informacje typu run-time:  
  
-   [Dynamic_cast](../cpp/dynamic-cast-operator.md) operatora.  
  
     Używany na potrzeby konwersji typów polimorficznym.  
  
-   [Typeid](../cpp/typeid-operator.md) operatora.  
  
     Umożliwia identyfikowanie dokładnego typu obiektu.  
  
-   [Type_info —](../cpp/type-info-class.md) klasy.  
  
     Służy do przechowywania informacji o typie zwrócony przez `typeid` operatora.  
  
## <a name="see-also"></a>Zobacz też  
 [Rzutowanie](../cpp/casting.md)