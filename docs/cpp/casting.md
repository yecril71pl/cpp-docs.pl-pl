---
title: Rzutowanie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- casting [C++]
- coercion [C++]
- virtual functions [C++], in derived classes [C++]
- static cast operator
- dynamic cast operator
- polymorphic classes [C++]
- classes [C++], polymorphism
ms.assetid: 3dbeb06e-2f4b-4693-832d-624bc8ec95de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 472fc8f8f505b3c5c214fddd5b59436fb4e52e5f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46090402"
---
# <a name="casting"></a>Rzutowanie

Język C++ zapewnia, że jeśli klasa dziedziczy po klasie bazowej, zawierającej funkcje wirtualne, wskaźnik do tej klasy bazowej może służyć do implementacji funkcji wirtualnych znajdujących się w obiekcie klasie pochodnej. Klasa zawierająca funkcje wirtualne jest czasami nazywana „klasą polimorficzną”.

Ponieważ klasa pochodna zawiera definicje wszystkich klas bazowych, po których dziedziczy, bezpieczne jest rzutowanie wskaźnika w górę hierarchii na jedną z tych klas bazowych. Podając wskaźnik do klasy bazowej, rzutowanie wskaźnika w dół hierarchii może być bezpieczne. Jest to bezpieczne, jeśli wskazywany obiekt jest rzeczywiście typu dziedziczonego z klasy bazowej. W takim przypadku faktyczny obiekt jest określany jako „obiekt kompletny”. Wskaźnik do klasy bazowej jest nazywany wskaźnikiem do „podobiektu” obiektu kompletnego. Na przykład, rozważmy hierarchię klas pokazaną na poniższym rysunku.

![Hierarchia klas](../cpp/media/vc38zz1.gif "vc38ZZ1") hierarchii klas

Obiekt typu `C` może zostać zwizualizowany jak pokazano na poniższym rysunku.

![Klasa C z sub&#45;obiekty B i A](../cpp/media/vc38zz2.gif "vc38ZZ2") klasy C z Podobiektem B i Podobiektem A

Biorąc pod uwagę wystąpienie klasy `C`, istnieje podobiekt `B` i podobiekt `A`. Wystąpienie klasy `C`, oraz podobiekty `A` i `B` to „obiekt kompletny”.

Korzystając z informacji o typie uzyskiwanej w czasie wykonywania, możliwe jest sprawdzenie, czy wskaźnik faktycznie wskazuje na obiekt kompletny i może być bezpiecznie rzutowany na wskaźnik na inny obiekt w jego hierarchii. [Dynamic_cast](../cpp/dynamic-cast-operator.md) operator może służyć dokonanie takiego właśnie rzutowania. Wykonuje także niezbędne sprawdzenie w czasie wykonania w celu bezpiecznego wykonania operacji.

W przypadku konwersji typów niepolimorficznych, można użyć [static_cast](../cpp/static-cast-operator.md) — operator (w tym temacie opisano różnicę między rzutowaniami statycznych i dynamicznych i kiedy należy używać każdego).

W tej sekcji omówiono następujące tematy:

- [Operatory rzutowania](../cpp/casting-operators.md)

- [Informacje typu Run-time](../cpp/run-time-type-information.md)

## <a name="see-also"></a>Zobacz także

[Wyrażenia](../cpp/expressions-cpp.md)