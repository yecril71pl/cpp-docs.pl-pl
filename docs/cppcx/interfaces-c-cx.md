---
title: Interfejsy (C++/CX)
ms.date: 01/22/2017
ms.assetid: 11034314-d54a-426d-923b-5ab7a6b9f8ce
ms.openlocfilehash: 263feb7b9c8a472a6077236596107bdeff26a5a4
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740189"
---
# <a name="interfaces-ccx"></a>Interfejsy (C++/CX)

Chociaż Klasa ref może dziedziczyć z co najwyżej jednej konkretnej klasy podstawowej, może zaimplementować dowolną liczbę klas interfejsu. Klasa interfejsu (lub struktura interfejsu) może dziedziczyć (lub wymagać) wielu klas interfejsów, może przeciążać jej funkcje członkowskie i może mieć parametry typu.

## <a name="characteristics"></a>Elementy

Interfejs ma następujące cechy:

- Klasa interfejsu (lub struktura) musi być zadeklarowana w przestrzeni nazw i może mieć dostępność publiczną lub prywatną. Tylko interfejsy publiczne są emitowane do metadanych.

- Elementy członkowskie interfejsu mogą zawierać właściwości, metody i zdarzenia.

- Wszystkie elementy członkowskie interfejsu są niejawnie publiczne i wirtualne.

- Pola i statyczne elementy członkowskie są niedozwolone.

- Typy, które są używane jako właściwości, parametry metody lub wartości zwracane mogą być tylko środowisko wykonawcze systemu Windows typów; obejmuje to typy podstawowe i typy klas enum.

## <a name="declaration-and-usage"></a>Deklaracja i użycie

Poniższy przykład pokazuje, jak zadeklarować interfejs. Należy zauważyć, że interfejs może być zadeklarowany jako Klasa lub typ struktury.

[!code-cpp[cx_interfaces#01](../cppcx/codesnippet/CPP/interfacestest/class1.h#01)]

Aby zaimplementować interfejs, Klasa referencyjna lub struktura ref deklaruje i implementuje metody wirtualne i właściwości. Interfejs i Klasa referencyjna implementująca muszą używać tych samych nazw parametrów metody, jak pokazano w tym przykładzie:

[!code-cpp[cx_interfaces#02](../cppcx/codesnippet/CPP/interfacestest/class1.h#02)]

## <a name="interface-inheritance-hierarchies"></a>Hierarchie dziedziczenia interfejsu

Interfejs może dziedziczyć z jednego lub większej liczby interfejsów. Ale w przeciwieństwie do klasy lub struktury ref, interfejs nie deklaruje dziedziczonych elementów członkowskich interfejsu. Jeśli interfejs B dziedziczy z interfejsu A, i Klasa ref C dziedziczy z B, C musi implementować zarówno a, jak i B. Jest to pokazane w następnym przykładzie.

[!code-cpp[cx_interfaces#03](../cppcx/codesnippet/CPP/interfacestest/class1.h#03)]

## <a name="implementing-interface-properties-and-events"></a>Implementowanie właściwości interfejsu i zdarzeń

Jak pokazano w poprzednim przykładzie, można użyć właściwości uproszczonych, aby zaimplementować właściwości interfejsu. Można również dostarczyć niestandardowe metody pobierające i metody ustawiające w klasie implementującej.  Zarówno metoda pobierająca, jak i setter musi być publiczna we właściwości interfejsu.

[!code-cpp[cx_interfaces#04](../cppcx/codesnippet/CPP/interfacestest/class1.h#04)]

Jeśli interfejs deklaruje właściwość tylko do get lub Set-Only, Klasa implementująca powinna jawnie dostarczyć metodę pobierającą lub setter.

[!code-cpp[cx_interfaces#05](../cppcx/codesnippet/CPP/interfacestest/class1.h#05)]

Możesz również zaimplementować niestandardowe metody dodawania i usuwania dla zdarzeń w klasie implementującej.

## <a name="explicit-interface-implementation"></a>Implementacja interfejsu jawnego

Gdy Klasa referencyjna implementuje wiele interfejsów, a interfejsy te mają metody, których nazwy i podpisy są identyczne z kompilatorem, można użyć następującej składni, aby jawnie wskazać metodę interfejsu, która implementuje metodę klasy.

[!code-cpp[cx_interfaces#06](../cppcx/codesnippet/CPP/interfacestest/class1.h#06)]

## <a name="generic-interfaces"></a>Interfejsy ogólne

W C++/CX, `generic` słowo kluczowe jest używane do reprezentowania środowisko wykonawcze systemu Windows sparametryzowany typ. Typ sparametryzowany jest emitowany w metadanych i może być używany przez kod, który jest pisany w dowolnym języku, który obsługuje parametry typu. Środowisko wykonawcze systemu Windows definiuje niektóre interfejsy ogólne — na przykład [Windows:: Foundation:: Collections:: IVector\<T >](Windows::Foundation::Collections::IVector), ale nie obsługuje tworzenia publicznych interfejsów zdefiniowanych przez użytkownika w/CX. C++ Można jednak tworzyć prywatne interfejsy ogólne.

Poniżej przedstawiono sposób, w jaki typy środowisko wykonawcze systemu Windows mogą służyć do tworzenia interfejsu generycznego:

- Nie można emitować ogólnego użytkownika `interface class` zdefiniowanego w składniku do jego pliku metadanych systemu Windows; w związku z tym nie może on mieć publicznej dostępności, a kod klienta w innych plikach winmd nie może go wdrożyć. Może być implementowana przez niepubliczne klasy referencyjne w tym samym składniku. Publiczna Klasa referencyjna może mieć typ interfejsu generycznego jako prywatny element członkowski.

   Poniższy fragment kodu przedstawia sposób deklarowania ogólnego `interface class` , a następnie implementowania go w prywatnej klasie ref i używania klasy ref jako prywatnego elementu członkowskiego w publicznej klasie referencyjnej.

   [!code-cpp[cx_interfaces#07](../cppcx/codesnippet/CPP/interfacestest/class1.h#07)]

- Interfejs generyczny musi być zgodny z regułami standardowego interfejsu, które regulują ułatwienia dostępu, członków, *wymaga* relacji, klas bazowych i tak dalej.

- Interfejs generyczny może przyjmować jeden lub więcej parametrów typu ogólnego, które są poprzedzone `typename` lub `class`. Parametry bez typu nie są obsługiwane.

- Parametr typu może być dowolnego typu środowisko wykonawcze systemu Windows. Oznacza to, że parametr typu może być typem referencyjnym, typem wartości, klasą interfejsu, delegatem, typem podstawowym lub publiczną klasą enum.

- *Zamknięty interfejs generyczny* jest interfejsem, który dziedziczy z interfejsu ogólnego i określa argumenty konkretnych typów dla wszystkich parametrów typu. Można go użyć w dowolnym miejscu, w którym można użyć nieogólnego interfejsu prywatnego.

- *Otwarty interfejs generyczny* jest interfejsem, który ma co najmniej jeden parametr typu, dla którego nie podano żadnego konkretnego typu. Można go użyć w dowolnym miejscu, w którym można użyć typu, w tym jako argument typu innego interfejsu ogólnego.

- Można Sparametryzuj tylko cały interfejs, a nie poszczególne metody.

- Parametry typu nie mogą być ograniczone.

- Zamknięty interfejs ogólny ma niejawnie wygenerowany identyfikator UUID. Użytkownik nie może określić identyfikatora UUID.

- W interfejsie wszystkie odwołania do bieżącego interfejsu — w parametrze metody, wartości zwracanej lub właściwości — jest założono, że odwołuje się do bieżącego wystąpienia. Na przykład *IMyIntf* oznacza *\<IMyIntf > T*.

- Gdy typ parametru metody jest parametrem typu, deklaracja tego parametru lub zmiennej używa nazwy parametru typu bez żadnego wskaźnika, natywnego odwołania lub uchwytu Deklaratory. Inaczej mówiąc, nigdy nie piszesz "T ^".

- Klasy ref z szablonami muszą być prywatne. Mogą implementować interfejsy generyczne i mogą przekazywać parametry szablonu *t* do argumentu ogólnego *t*. Każde wystąpienie klasy ref z szablonami jest samą klasą ref.

## <a name="see-also"></a>Zobacz także

[System typów](../cppcx/type-system-c-cx.md)<br/>
[Dokumentacja języka C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Dokumentacja przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)
