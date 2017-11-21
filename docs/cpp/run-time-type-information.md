---
title: Informacje typu Run-Time | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: 'index-page '
dev_langs: C++
helpviewer_keywords:
- RTTI compiler option
- run-time type information
- run time, type checking
- type information, run-time type checking
- run-time checks, type checking
ms.assetid: becbd0e5-0439-4c61-854f-8a74f7160c54
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4fb5f7413f613aab2d02ee2548a460adfca57b90
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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