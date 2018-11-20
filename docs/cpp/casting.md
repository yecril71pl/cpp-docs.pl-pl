---
title: Rzutowanie
ms.date: 11/19/2018
helpviewer_keywords:
- casting [C++]
- coercion [C++]
- virtual functions [C++], in derived classes [C++]
- static cast operator
- dynamic cast operator
- polymorphic classes [C++]
- classes [C++], polymorphism
ms.assetid: 3dbeb06e-2f4b-4693-832d-624bc8ec95de
ms.openlocfilehash: 02ade663ee92d3a301fda95bb385c3ffa48ead12
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2018
ms.locfileid: "52175551"
---
# <a name="casting"></a>Rzutowanie

Język C++ zapewnia, że jeśli klasa dziedziczy po klasie bazowej, zawierającej funkcje wirtualne, wskaźnik do tej klasy bazowej może służyć do implementacji funkcji wirtualnych znajdujących się w obiekcie klasie pochodnej. Klasa zawierająca funkcje wirtualne jest czasami nazywana „klasą polimorficzną”.

Ponieważ klasa pochodna zawiera definicje wszystkich klas bazowych, po których dziedziczy, bezpieczne jest rzutowanie wskaźnika w górę hierarchii na jedną z tych klas bazowych. Podając wskaźnik do klasy bazowej, rzutowanie wskaźnika w dół hierarchii może być bezpieczne. Jest to bezpieczne, jeśli wskazywany obiekt jest rzeczywiście typu dziedziczonego z klasy bazowej. W takim przypadku faktyczny obiekt jest określany jako „obiekt kompletny”. Wskaźnik do klasy bazowej jest nazywany wskaźnikiem do „podobiektu” obiektu kompletnego. Na przykład, rozważmy hierarchię klas pokazaną na poniższym rysunku.

![Hierarchia klas](../cpp/media/vc38zz1.gif "klasy hierarchii") <br/>
Hierarchia klas

Obiekt typu `C` może zostać zwizualizowany jak pokazano na poniższym rysunku.

![Klasa C z sub&#45;obiekty B i A](../cpp/media/vc38zz2.gif "klasy C z sub&#45;obiekty B i A") <br/>
Klasa C za pomocą obiektów podrzędnych, B i A

Biorąc pod uwagę wystąpienie klasy `C`, istnieje podobiekt `B` i podobiekt `A`. Wystąpienie klasy `C`, oraz podobiekty `A` i `B` to „obiekt kompletny”.

Korzystając z informacji o typie uzyskiwanej w czasie wykonywania, możliwe jest sprawdzenie, czy wskaźnik faktycznie wskazuje na obiekt kompletny i może być bezpiecznie rzutowany na wskaźnik na inny obiekt w jego hierarchii. [Dynamic_cast](../cpp/dynamic-cast-operator.md) operator może służyć dokonanie takiego właśnie rzutowania. Wykonuje także niezbędne sprawdzenie w czasie wykonania w celu bezpiecznego wykonania operacji.

W przypadku konwersji typów niepolimorficznych, można użyć [static_cast](../cpp/static-cast-operator.md) — operator (w tym temacie opisano różnicę między rzutowaniami statycznych i dynamicznych i kiedy należy używać każdego).

W tej sekcji omówiono następujące tematy:

- [Operatory rzutowania](../cpp/casting-operators.md)

- [Informacje typu Run-time](../cpp/run-time-type-information.md)

## <a name="see-also"></a>Zobacz także

[Wyrażenia](../cpp/expressions-cpp.md)