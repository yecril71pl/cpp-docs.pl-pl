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
ms.openlocfilehash: bb06db3af6aee031b6cb2d69b38a9404304420fc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190141"
---
# <a name="casting"></a>Rzutowanie

Język C++ zapewnia, że jeśli klasa dziedziczy po klasie bazowej, zawierającej funkcje wirtualne, wskaźnik do tej klasy bazowej może służyć do implementacji funkcji wirtualnych znajdujących się w obiekcie klasie pochodnej. Klasa zawierająca funkcje wirtualne jest czasami nazywana „klasą polimorficzną”.

Ponieważ klasa pochodna zawiera definicje wszystkich klas bazowych, po których dziedziczy, bezpieczne jest rzutowanie wskaźnika w górę hierarchii na jedną z tych klas bazowych. Podając wskaźnik do klasy bazowej, rzutowanie wskaźnika w dół hierarchii może być bezpieczne. Jest to bezpieczne, jeśli wskazywany obiekt jest rzeczywiście typu dziedziczonego z klasy bazowej. W takim przypadku faktyczny obiekt jest określany jako „obiekt kompletny”. Wskaźnik do klasy bazowej jest nazywany wskaźnikiem do „podobiektu” obiektu kompletnego. Na przykład, rozważmy hierarchię klas pokazaną na poniższym rysunku.

![Hierarchia klas](../cpp/media/vc38zz1.gif "Hierarchia klas") <br/>
Hierarchia klas

Obiekt typu `C` może zostać zwizualizowany jak pokazano na poniższym rysunku.

![Klasa C z obiektami&#45;podrzędnymi B i](../cpp/media/vc38zz2.gif "Klasa C z obiektami&#45;podrzędnymi B i") <br/>
Klasa C z obiektami podrzędnymi B i

Biorąc pod uwagę wystąpienie klasy `C`, istnieje podobiekt `B` i podobiekt `A`. Wystąpienie klasy `C`, oraz podobiekty `A` i `B` to „obiekt kompletny”.

Korzystając z informacji o typie uzyskiwanej w czasie wykonywania, możliwe jest sprawdzenie, czy wskaźnik faktycznie wskazuje na obiekt kompletny i może być bezpiecznie rzutowany na wskaźnik na inny obiekt w jego hierarchii. Operatora [dynamic_cast](../cpp/dynamic-cast-operator.md) można użyć, aby utworzyć te typy rzutowania. Wykonuje także niezbędne sprawdzenie w czasie wykonania w celu bezpiecznego wykonania operacji.

W przypadku konwersji typów niepolimorficznych można użyć operatora [static_cast](../cpp/static-cast-operator.md) (w tym temacie objaśniono różnicę między konwersjami statycznymi a dynamicznymi, a gdy jest on odpowiedni do użycia.

W tej sekcji omówiono następujące tematy:

- [Operatory rzutowania](../cpp/casting-operators.md)

- [Informacje o typie w czasie wykonywania](../cpp/run-time-type-information.md)

## <a name="see-also"></a>Zobacz też

[Wyrażenia](../cpp/expressions-cpp.md)
