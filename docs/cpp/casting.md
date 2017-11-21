---
title: Rzutowanie | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- casting [C++]
- coercion [C++]
- virtual functions [C++], in derived classes [C++]
- static cast operator
- dynamic cast operator
- polymorphic classes [C++]
- classes [C++], polymorphism
ms.assetid: 3dbeb06e-2f4b-4693-832d-624bc8ec95de
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 85f26c61e1e4fa996f73b4f61f4f961ba59dec98
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="casting"></a>Rzutowanie
Język C++ zapewnia, że jeśli klasa dziedziczy po klasie podstawowej, zawierającej funkcje wirtualne, wskaźnik do tej klasy podstawowej może służyć do implementacji funkcji wirtualnych znajdujących się w obiekcie klasie pochodnej. Klasa zawierająca funkcje wirtualne jest czasami nazywana „klasą polimorficzną”.  
  
 Ponieważ klasa pochodna zawiera definicje wszystkich klas podstawowych, po których dziedziczy, bezpieczne jest rzutowanie wskaźnika w górę hierarchii na jedną z tych klas podstawowych. Podając wskaźnik do klasy podstawowej, rzutowanie wskaźnika w dół hierarchii może być bezpieczne. Jest to bezpieczne, jeśli wskazywany obiekt jest rzeczywiście typu dziedziczonego z klasy podstawowej. W takim przypadku faktyczny obiekt jest określany jako „obiekt kompletny”. Wskaźnik do klasy podstawowej jest nazywany wskaźnikiem do „podobiektu” obiektu kompletnego. Na przykład, rozważmy hierarchię klas pokazaną na poniższym rysunku.  
  
 ![Hierarchia klas](../cpp/media/vc38zz1.gif "vc38ZZ1")  
Hierarchia klas  
  
 Obiekt typu `C` może zostać zwizualizowany jak pokazano na poniższym rysunku.  
  
 ![Klasa C z sub &#45; obiekty B i A](../cpp/media/vc38zz2.gif "vc38ZZ2")  
Klasa C z podobiektem B i podobiektem A  
  
 Biorąc pod uwagę wystąpienie klasy `C`, istnieje podobiekt `B` i podobiekt `A`. Wystąpienie klasy `C`, oraz podobiekty `A` i `B` to „obiekt kompletny”.  
  
 Korzystając z informacji o typie uzyskiwanej w czasie wykonywania, możliwe jest sprawdzenie, czy wskaźnik faktycznie wskazuje na obiekt kompletny i może być bezpiecznie rzutowany na wskaźnik na inny obiekt w jego hierarchii. [Dynamic_cast](../cpp/dynamic-cast-operator.md) operator może służyć do tworzenie tych typów rzutowania. Wykonuje także niezbędne sprawdzenie w czasie wykonania w celu bezpiecznego wykonania operacji.  
  
 Konwersja typów nonpolymorphic, można użyć [static_cast](../cpp/static-cast-operator.md) — operator (w tym temacie objaśniono różnicę między konwersje rzutowania statycznych i dynamicznych oraz gdy należy używać każdego).  
  
 W tej sekcji omówiono następujące tematy:  
  
-   [Operatory rzutowania](../cpp/casting-operators.md)  
  
-   [Informacje typu Run-time](../cpp/run-time-type-information.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia](../cpp/expressions-cpp.md)