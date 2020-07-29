---
title: Podsumowanie reguł zakresu
ms.date: 11/04/2016
helpviewer_keywords:
- class scope [C++], rules
- classes [C++], scope
- class names [C++], scope rules
- names [C++], class
- scope [C++], class names
ms.assetid: 47e26482-0111-466f-b857-598c15d05105
ms.openlocfilehash: 024a61419129f669485944a427379dd41c385404
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231068"
---
# <a name="summary-of-scope-rules"></a>Podsumowanie reguł zakresu

Użycie nazwy musi być jednoznaczne w swoim zakresie (do momentu określenia przeciążenia). Jeśli nazwa oznacza funkcję, funkcja musi być niejednoznaczna w odniesieniu do liczby i typu parametrów. Jeśli nazwa pozostanie niejednoznaczna, stosowane są reguły [dostępu do elementów członkowskich](../cpp/member-access-control-cpp.md) .

## <a name="constructor-initializers"></a>Inicjatory konstruktora

[Inicjatory konstruktora](constructors-cpp.md#member_init_list) są oceniane w zakresie najbardziej zewnętrznego bloku konstruktora, dla którego są określone. W związku z tym mogą używać nazw parametrów konstruktora.

## <a name="global-names"></a>Nazwy globalne

Nazwa obiektu, funkcji lub modułu wyliczającego jest globalna, jeśli jest wprowadzana poza jakąkolwiek funkcją lub klasą lub poprzedzona przez globalny operator zakresu jednoargumentowego ( `::` ) i jeśli nie jest używany w połączeniu z żadnym z tych operatorów binarnych:

- Scope-Solution ( `::` )

- Wybór elementów członkowskich dla obiektów i odwołań (**.**)

- Wybór elementu członkowskiego dla wskaźników ( **->** )

## <a name="qualified-names"></a>Kwalifikowane nazwy

Nazwy używane z binarnym operatorem rozwiązywania zakresu (`::`) są nazywane „nazwami kwalifikowanymi”. Nazwa określona po binarnym operatorze rozwiązywania zakresu musi być składową klasy określonej po lewej stronie operatora lub składową jej klas podstawowych.

Nazwy określone po operatorze wyboru elementu członkowskiego (**.** lub **->** ) musi być elementami członkowskimi typu klasy obiektu określonego po lewej stronie operatora lub składowymi jego klas podstawowych. Nazwy określone po prawej stronie operatora wyboru elementu członkowskiego ( **->** ) mogą być również obiektami innego typu klasy, pod warunkiem, że lewa strona **->** jest obiektem klasy i że klasa definiuje przeciążony operator wyboru elementu członkowskiego ( **->** ), który jest obliczany jako wskaźnik do innego typu klasy. (Ta obsługa jest omówiona bardziej szczegółowo w [dostępie do elementu członkowskiego klasy](../cpp/member-access.md)).

Kompilator wyszukuje nazwy w następującej kolejności, zatrzymując się, gdy nazwa zostanie znaleziona:

1. Bieżący blok zakresu, jeśli nazwa jest używana wewnątrz funkcji; w przeciwnym przypadku, zakres globalny.

1. Na zewnątrz przez każdy otaczający zakres bloku, łącznie z zewnętrznym zakresem funkcji (który obejmuje parametry funkcji).

1. Jeśli nazwa jest używana wewnątrz funkcji składowej, to nazwa jest wyszukiwana w zakresie klasy.

1. Nazwa jest wyszukiwana w klasach bazowych klasy.

1. Przeszukiwany jest otaczający, zagnieżdżony zakres klasy (jeśli istnieje) oraz jego klasy podstawowe. Wyszukiwanie jest kontynuowane, dopóki nie zostanie przeszukany najbardziej zewnętrzny, otaczający zakres klasy.

1. Przeszukiwany jest zakres globalny.

Jednakże, możesz wykonać następujące modyfikacje kolejności wyszukiwania:

1. Nazwy poprzedzone operatorem `::` wymuszają rozpoczęcie wyszukiwania od zakresu globalnego.

1. Nazwy poprzedzone przez **`class`** , **`struct`** i **`union`** słowa kluczowe, wymuszają kompilatorowi wyszukanie **`class`** tylko **`struct`** nazw,, lub **`union`** .

1. Nazwy po lewej stronie operatora rozpoznawania zakresu ( `::` ) mogą dotyczyć tylko **`class`** **`struct`** nazw,, **`namespace`** , lub **`union`** .

Jeśli nazwa odwołuje się do niestatycznego elementu członkowskiego, ale jest używana w statycznej funkcji członkowskiej, to wygenerowany zostanie komunikat o błędzie. Podobnie, jeśli nazwa odwołuje się do dowolnego niestatycznej składowej w otaczającej klasie, generowany jest komunikat o błędzie, ponieważ zawarte w nich klasy nie mają wskaźników otaczających klas **`this`** .

## <a name="function-parameter-names"></a>Nazwy parametrów funkcji

Nazwy parametrów funkcji w definicjach funkcji są uważane za należące do zakresu najbardziej zewnętrznego bloku funkcji. W związku z tym są nazwami lokalnymi i wykraczają poza zakres, gdy funkcja zostanie zakończona.

Nazwy parametrów funkcji w deklaracjach funkcji (prototypach) znajdują się w lokalnym zakresie deklaracji i wykraczają poza zakres na końcu deklaracji.

Parametry domyślne znajdują się w zakresie parametru, dla którego są domyślne, zgodnie z opisem w poprzednich dwóch akapitach. Nie mogą jednak uzyskać dostępu do zmiennych lokalnych ani niestatycznych elementów członkowskich klas. Parametry domyślne są oceniane w punkcie wywołania funkcji, ale są oceniane w oryginalnym zakresie deklaracji funkcji. W związku z tym domyślne parametry funkcji Członkowskich są zawsze oceniane w zakresie klasy.

## <a name="see-also"></a>Zobacz także

[Dziedziczenie](../cpp/inheritance-cpp.md)
