---
title: Interfejsy (C++/CX)
ms.date: 01/22/2017
ms.assetid: 11034314-d54a-426d-923b-5ab7a6b9f8ce
ms.openlocfilehash: 716bf86eddf621244415033dae1b9c93ad1baba5
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032359"
---
# <a name="interfaces-ccx"></a>Interfejsy (C++/CX)

Chociaż ref klasy można dziedziczyć z co najwyżej jednej konkretnej klasy podstawowej, można zaimplementować dowolną liczbę klas interfejsu. Sama klasa interfejsu (lub struktura interfejsu) może dziedziczyć (lub wymagać) wielu klas interfejsu, może przeciążać jego funkcje członkowskie i może mieć parametry typu.

## <a name="characteristics"></a>Właściwości

Interfejs ma następujące cechy:

- Klasa interfejsu (lub struktura) musi być zadeklarowana w obszarze nazw i może mieć dostępność publiczną lub prywatną. Tylko interfejsy publiczne są emitowane do metadanych.

- Elementy członkowskie interfejsu mogą zawierać właściwości, metody i zdarzenia.

- Wszyscy członkowie interfejsu są niejawnie publiczne i wirtualne.

- Pola i elementy statyczne nie są dozwolone.

- Typy, które są używane jako właściwości, parametry metody lub zwracane wartości mogą być tylko typami środowiska wykonawczego systemu Windows; obejmuje to podstawowe typy i typy klas wyliczenia.

## <a name="declaration-and-usage"></a>Deklaracja i użycie

W poniższym przykładzie pokazano, jak zadeklarować interfejs. Należy zauważyć, że interfejs może być zadeklarowany jako typ klasy lub struktury.

[!code-cpp[cx_interfaces#01](../cppcx/codesnippet/CPP/interfacestest/class1.h#01)]

Aby zaimplementować interfejs, ref klasy lub ref struct deklaruje i implementuje metody wirtualne i właściwości. Interfejs i implementująca klasa ref muszą używać tych samych nazw parametrów metody, jak pokazano w tym przykładzie:

[!code-cpp[cx_interfaces#02](../cppcx/codesnippet/CPP/interfacestest/class1.h#02)]

## <a name="interface-inheritance-hierarchies"></a>Hierarchie dziedziczenia interfejsu

Interfejs może dziedziczyć z jednego lub więcej interfejsów. Ale w przeciwieństwie do ref klasy lub struktury, interfejs nie deklaruje członków interfejsu dziedziczonego. Jeśli interfejs B dziedziczy z interfejsu A, a klasa ref C dziedziczy od B, C musi implementować zarówno A, jak i B. Jest to pokazane w następnym przykładzie.

[!code-cpp[cx_interfaces#03](../cppcx/codesnippet/CPP/interfacestest/class1.h#03)]

## <a name="implementing-interface-properties-and-events"></a>Implementowanie właściwości i zdarzeń interfejsu

Jak pokazano w poprzednim przykładzie, można użyć właściwości wirtualne trywialne do zaimplementowania właściwości interfejsu. Można również podać niestandardowe getters i ustawiających w klasie implementacji.  Zarówno metody ustawiacza, jak i ustawiacza muszą być publiczne we właściwości interfejsu.

[!code-cpp[cx_interfaces#04](../cppcx/codesnippet/CPP/interfacestest/class1.h#04)]

Jeśli interfejs deklaruje właściwość tylko do uzyskania lub tylko do zestawu, klasa implementująca powinna jawnie podać metodyą ustawiającą lub ustawiającą.

[!code-cpp[cx_interfaces#05](../cppcx/codesnippet/CPP/interfacestest/class1.h#05)]

Można również zaimplementować niestandardowe metody dodawania i usuwania zdarzeń w klasie implementującej.

## <a name="explicit-interface-implementation"></a>Jawna implementacja interfejsu

Gdy klasa ref implementuje wiele interfejsów, a te interfejsy mają metody, których nazwy i podpisy są identyczne z kompilatorem, można użyć następującej składni, aby jawnie wskazać metodę interfejsu, którą implementuje metoda klasy.

[!code-cpp[cx_interfaces#06](../cppcx/codesnippet/CPP/interfacestest/class1.h#06)]

## <a name="generic-interfaces"></a>Interfejsy ogólne

W języku C++/CX `generic` słowo kluczowe jest używane do reprezentowania typu sparametryzowanego środowiska wykonawczego systemu Windows. Typ sparametryzowany jest emitowany w metadanych i może być zużywany przez kod, który jest napisany w dowolnym języku, który obsługuje parametry typu. Środowisko wykonawcze systemu Windows definiuje niektóre interfejsy ogólne — na przykład [Windows::Foundation::Collections::IVector\<T>](/uwp/api/windows.foundation.collections.ivector-1)— ale nie obsługuje tworzenia publicznych interfejsów ogólnych zdefiniowanych przez użytkownika w języku C++/CX. Można jednak tworzyć prywatne interfejsy ogólne.

Oto jak można użyć typów środowiska wykonawczego systemu Windows do tworzenia ogólnego interfejsu:

- Ogólny zdefiniowany `interface class` przez użytkownika w składniku nie może być emitowany do pliku metadanych systemu Windows; w związku z tym nie może mieć publicznych ułatwień dostępu, a kod klienta w innych plikach .winmd nie można go zaimplementować. Może być zaimplementowana przez niepubliczne klasy ref w tym samym składniku. Klasa public ref może mieć typ interfejsu ogólnego jako element członkowski prywatny.

   Poniższy fragment kodu pokazuje, jak zadeklarować rodzajowy, `interface class` a następnie zaimplementować go w prywatnej klasie ref i użyć klasy ref jako prywatnego elementu członkowskiego w klasie public ref.

   [!code-cpp[cx_interfaces#07](../cppcx/codesnippet/CPP/interfacestest/class1.h#07)]

- Interfejs ogólny musi być zgodny ze standardowymi regułami interfejsu, które regulują dostępność, elementy członkowskie, *wymaga* relacji, klas podstawowych i tak dalej.

- Interfejs ogólny może przyjmować jeden lub więcej parametrów typu ogólnego, które są poprzedzone `typename` lub `class`. Parametry nienakładowe nie są obsługiwane.

- Parametrem typu może być dowolny typ środowiska wykonawczego systemu Windows. Oznacza to, że parametr typu może być typem odwołania, typem wartości, klasą interfejsu, delegatem, typem podstawowym lub publiczną klasą wyliczenia.

- *Zamknięty interfejs ogólny* jest interfejsem, który dziedziczy z interfejsu ogólnego i określa konkretne argumenty typu dla wszystkich parametrów typu. Może być używany wszędzie tam, gdzie można użyć niegenerycznego interfejsu prywatnego.

- *Otwarty interfejs ogólny* jest interfejsem, który ma jeden lub więcej parametrów typu, dla których nie ma jeszcze typu betonu. Może być używany wszędzie tam, gdzie może być używany typ, w tym jako argument typu innego interfejsu ogólnego.

- Można sparametryzować tylko cały interfejs, a nie poszczególne metody.

- Nie można ograniczyć parametrów typu.

- Zamknięty interfejs ogólny ma niejawnie wygenerowany identyfikator UUID. Użytkownik nie może określić identyfikatora UUID.

- W interfejsie przyjmuje się, że wszelkie odwołania do bieżącego interfejsu — w parametrze metody, wartości zwracanej lub właściwości — odnoszą się do bieżącego wystąpienia. Na przykład *IMyIntf* oznacza *IMyIntf\<T>*.

- Gdy typ parametru metody jest parametrem typu, deklaracja tego parametru lub zmiennej używa nazwy parametru typu bez żadnego wskaźnika, odwołania macierzystego lub deklaratorów dojścia. Innymi słowy, nigdy nie piszesz "T^".

- Klasy ref szablonu muszą być prywatne. Mogą zaimplementować interfejsy ogólne i mogą przekazać parametr szablonu *T* do ogólnego argumentu *T*. Każde wystąpienie klasy ref z szablonem jest klasą ref.

## <a name="see-also"></a>Zobacz też

[System typów](../cppcx/type-system-c-cx.md)<br/>
[Odwołanie do języka C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Dokumentacja przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)
