---
title: Interfejsy (C + +/ CX)
ms.date: 01/22/2017
ms.assetid: 11034314-d54a-426d-923b-5ab7a6b9f8ce
ms.openlocfilehash: 33fe0df457a4f1bab3a7cffab585501364d5750c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50626632"
---
# <a name="interfaces-ccx"></a>Interfejsy (C + +/ CX)

Chociaż klasa ref może dziedziczyć z co najwyżej jedną konkretną klasę bazową, on implementować dowolną liczbę klas interfejsów. Klasa interfejsu (lub struktury interfejsu) sama może być dziedziczony (lub wymagają) wielu interfejsu klasy, może doprowadzić do przeciążenia jej funkcje Członkowskie i może mieć parametrów typu.

## <a name="characteristics"></a>Właściwości

Interfejs ma następujące cechy:

- Klasa interfejsu (lub struktura) musi być zadeklarowany w przestrzeni nazw i może być publicznym lub prywatnym ułatwień dostępu. Tylko publiczne interfejsy są emitowane do metadanych.

- Elementy członkowskie interfejsu może zawierać właściwości, metody i zdarzenia.

- Wszyscy członkowie interfejsu są niejawnie publicznych i wirtualnych.

- Pola i statyczne elementy członkowskie nie są dozwolone.

- Typy, które są używane jako parametry metody, właściwości lub zwracanych wartości można tylko typów środowiska wykonawczego Windows; obejmuje to typy podstawowe i typy klas typu wyliczeniowego.

## <a name="declaration-and-usage"></a>Deklaracja i użycia

Poniższy przykład pokazuje sposób deklarowania interfejsu. Należy zauważyć, że interfejs może być zadeklarowany jako typ klasy lub struktury.

[!code-cpp[cx_interfaces#01](../cppcx/codesnippet/CPP/interfacestest/class1.h#01)]

Aby zaimplementować interfejs, klasa ref lub ref struct deklaruje i implementuje właściwości i metod wirtualnych. Interfejs i dla klasy implementującej ref muszą używać takie same nazwy parametrów metody, jak pokazano w poniższym przykładzie:

[!code-cpp[cx_interfaces#02](../cppcx/codesnippet/CPP/interfacestest/class1.h#02)]

## <a name="interface-inheritance-hierarchies"></a>Hierarchie dziedziczenia interfejsu

Interfejs może dziedziczyć z jednego lub więcej interfejsów. Jednak w odróżnieniu od klasy ref lub strukturze, interfejsie nie deklaruj składowych dziedziczony interfejs. Jeśli interfejs B dziedziczy z interfejsu, A klasa ref C dziedziczy B, C, należy zaimplementować A i B. Jest to pokazane w następnym przykładzie.

[!code-cpp[cx_interfaces#03](../cppcx/codesnippet/CPP/interfacestest/class1.h#03)]

## <a name="implementing-interface-properties-and-events"></a>Implementowanie interfejsu właściwości i zdarzenia

Jak pokazano w poprzednim przykładzie, można użyć proste właściwości wirtualnego do zaimplementowania właściwości interfejsu. Można również dołączyć niestandardowych metod pobierających i ustawiających w klasy implementującej.  Zarówno getter i setter muszą być publiczne we właściwości interfejsu.

[!code-cpp[cx_interfaces#04](../cppcx/codesnippet/CPP/interfacestest/class1.h#04)]

Jeśli interfejs deklaruje właściwości tylko do get lub tylko do zestawu, klasy implementującej należy podać jawne pobierającą czy ustawiającą.

[!code-cpp[cx_interfaces#05](../cppcx/codesnippet/CPP/interfacestest/class1.h#05)]

Możesz również wdrożyć niestandardowy dodawać i usuwać metody dla zdarzeń w klasy implementującej.

## <a name="explicit-interface-implementation"></a>Jawna implementacja interfejsu

Gdy klasy referencyjnej implementuje wiele interfejsów i metody mają te interfejsy, których nazwy i podpisy są takie same, jak kompilator, można użyć następującej składni, aby jawnie wskazać metodę interfejsu, która implementuje metody klasy.

[!code-cpp[cx_interfaces#06](../cppcx/codesnippet/CPP/interfacestest/class1.h#06)]

## <a name="generic-interfaces"></a>Interfejsy ogólne

W języku C + +/ CX, `generic` — słowo kluczowe jest używana do reprezentowania typów środowiska wykonawczego Windows sparametryzowanych. Typ sparametryzowany jest emitowane w metadanych i mogą być używane przez kod, który jest napisane w dowolnym języku, który obsługuje parametry typu. Środowisko wykonawcze Windows definiuje kilka interfejsów ogólnych — na przykład [Windows::Foundation::Collections::IVector\<T >](Windows::Foundation::Collections::IVector)—, ale go nie obsługuje tworzenia publicznych interfejsów ogólnych zdefiniowanych przez użytkownika w języku C + +/ CX. Można jednak utworzyć prywatnego interfejsów ogólnych.

Poniżej przedstawiono, jak typów środowiska wykonawczego Windows może służyć do tworzenia ogólny interfejs:

- Ogólny zdefiniowany przez użytkownika `interface class` w składnika nie może być wydane do jego pliku metadanych Windows; w związku z tym, nie może on zawierać powszechnej dostępności i nie może go zaimplementować kod klienta w innych plikach winmd. Może być implementowany przez klasy ref niepublicznych w jednym składniku. Klasa ref publicznych może mieć interfejs ogólny typ od prywatnej składowej.

   Poniższy fragment kodu pokazuje sposób deklarowania ogólnego `interface class` zaimplementowaniu jej w prywatnej klasy ref i korzystanie z klasy ref jako od prywatnej składowej w klasie ref publicznych.

   [!code-cpp[cx_interfaces#07](../cppcx/codesnippet/CPP/interfacestest/class1.h#07)]

- Ogólny interfejs należy przestrzegać reguł standardowy interfejs, określające ułatwień dostępu, elementy członkowskie, *wymaga* relacje, klas podstawowych i tak dalej.

- Ogólny interfejs może potrwać co najmniej jeden parametr typu ogólnego, które są poprzedzone `typename` lub `class`. Parametry bez typu nie są obsługiwane.

- Parametr typu mogą być dowolnego typu środowiska wykonawczego Windows. Oznacza to, że parametr typu może być typem referencyjnym, typem wartości, klasy interfejsu, delegata, typ podstawowy lub klasy publicznym typie wyliczeniowym.

- A *zamknięte ogólny interfejs* jest interfejsem, który dziedziczy interfejs ogólny i określa konkretny typ argumenty dla wszystkich parametrów typu. Może służyć wszędzie może służyć nieogólnego interfejs prywatny.

- *Otwórz interfejs ogólny* to interfejs, który ma co najmniej jeden parametr typu, dla których jeszcze podano żadnego konkretnego typu. Może służyć wszędzie że typu mogą być używane, w tym jako argument typu innym ogólna interfejsu.

- Można zdefiniować parametry tylko cały interfejs, nie do poszczególnych metod.

- Parametry typu nie może być ograniczona.

- Zamknięte ogólny interfejs ma niejawnie wygenerowanego identyfikatora UUID. Użytkownik nie może określić identyfikator UUID.

- W interfejsie, wszelkie odwołanie do bieżącego interfejsu — WE parametr metody zwracają wartość lub właściwość — przyjęto, że do odwoływania się do bieżącego wystąpienia. Na przykład *IMyIntf* oznacza *IMyIntf\<T >*.

- Jeśli typ parametru metody jest parametrem typu, deklaracja ten parametr lub zmienna korzysta z nazwy parametru typu bez wskaźnik, odwołanie natywne lub deklaratory dojście. Innymi słowy, nigdy nie zapisu "T ^".

- Klasy oparte na szablonach ref musi być prywatna. Można zaimplementować interfejsów ogólnych i przekazać parametr szablonu *T* do argumentu ogólnego *T*. Każdego wystąpienia klasy ref z szablonem jest klasą ref.

## <a name="see-also"></a>Zobacz też

[System typów](../cppcx/type-system-c-cx.md)<br/>
[Dokumentacja języka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Odwołanie do przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)