---
title: Tablica i WriteOnlyArray (C++/CX)
ms.date: 01/22/2017
ms.assetid: ef7cc5f9-cae6-4636-8220-f789e5b6aea4
ms.openlocfilehash: e050fad38d4f70c651fc0ebfddb51a33e31da6f3
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032411"
---
# <a name="array-and-writeonlyarray-ccx"></a>Tablica i WriteOnlyArray (C++/CX)

Można swobodnie używać zwykłych tablic w stylu C lub [std::array](../standard-library/array-class-stl.md) w programie C++/CX (chociaż [std::vector](../standard-library/vector-class.md) jest często lepszym wyborem), ale w dowolnym interfejsie API, który jest publikowany w metadanych, należy przekonwertować tablicę w stylu C lub wektor na [platformę::Tablica](../cppcx/platform-array-class.md) lub [Platform::WriteOnlyArray](../cppcx/platform-writeonlyarray-class.md) typu w zależności od sposobu jego używania. [Platforma::Typ tablicy](../cppcx/platform-array-class.md) nie jest tak wydajny, ani tak potężny jak [std::vector](../standard-library/vector-class.md), więc jako ogólne wytyczne należy unikać jego użycia w kodzie wewnętrznym, który wykonuje wiele operacji na elementach tablicy.

Następujące typy tablic mogą być przekazywane przez ABI:

1. const Platforma::Tablica^

1. Platforma::Tablica^*

1. Platforma::WriteOnlyArray

1. zwraca wartość platformy::Tablica^

Te typy tablic służą do zaimplementowania trzech rodzajów wzorców tablic, które są zdefiniowane przez środowisko wykonawcze systemu Windows.

PassArray używane, gdy wywołujący przekazuje tablicy do metody. Typ parametru wejściowego `const`języka C++ to [Platform::Array](../cppcx/platform-array-class.md)\<T>.

FillArray Używane, gdy wywołujący przekazuje tablicy dla metody do wypełnienia. Typ parametru wejściowego C++ to [Platform::WriteOnlyArray](../cppcx/platform-writeonlyarray-class.md)\<T>.

ReceiveArray używane, gdy wywołujący odbiera tablicy, że metoda przydziela. W języku C++/CX można zwrócić tablicę w wartości zwracanej jako tablica^ lub zwrócić ją jako parametr out jako typ Array^*.

## <a name="passarray-pattern"></a>Wzór PassArray

Gdy kod klienta przekazuje tablicę do metody C++, a metoda nie modyfikuje jej, metoda akceptuje tablicę jako tablicę const^. Na poziomie interfejsu binarnego aplikacji środowiska wykonawczego systemu Windows (ABI) jest to nazywane PassArray. W następnym przykładzie pokazano, jak przekazać tablicy, która jest alokowana w języku JavaScript do funkcji Języka C++, która odczytuje z niego.

[!code-javascript[cx_arrays#101](../cppcx/codesnippet/JavaScript/array-and-writeonlyarray-c-_1.js)]

Następujący fragment kodu pokazuje metodę C++:

[!code-cpp[cx_arrays#01](../cppcx/codesnippet/CPP/js-array/class1.cpp#01)]

## <a name="receivearray-pattern"></a>Wzór ReceiveArray

We wzorcu ReceiveArray kod klienta deklaruje tablicę i przekazuje ją do metody, która przydziela dla niej pamięć i inicjuje ją. Typ parametru wejściowego C++ jest wskaźnikiem do czapki: `Array<T>^*`. W poniższym przykładzie pokazano, jak zadeklarować obiekt tablicy w języku JavaScript i przekazać go do funkcji Języka C++, która przydziela pamięć, inicjuje elementy i zwraca go do języka JavaScript. JavaScript traktuje przydzieloną tablicę jako wartość zwracaną, ale funkcja C++ traktuje ją jako parametr out.

[!code-javascript[cx_arrays#102](../cppcx/codesnippet/JavaScript/array-and-writeonlyarray-c-_3.js)]

Poniższy fragment kodu pokazuje dwa sposoby implementacji metody C++:

[!code-cpp[cx_arrays#02](../cppcx/codesnippet/CPP/js-array/class1.cpp#02)]

## <a name="fill-arrays"></a>Tablice wypełnienia

Jeśli chcesz przydzielić tablicę w wywołującym i zainicjować ją lub zmodyfikować w wywoływanej, użyj programu `WriteOnlyArray`. W następnym przykładzie pokazano, jak zaimplementować funkcję Języka C++, która używa `WriteOnlyArray` i wywołać go z języka JavaScript.

[!code-javascript[cx_arrays#103](../cppcx/codesnippet/JavaScript/array-and-writeonlyarray-c-_5.js)]

Poniższy fragment kodu pokazuje, jak zaimplementować metodę C++:

[!code-cpp[cx_arrays#03](../cppcx/codesnippet/CPP/js-array/class1.cpp#03)]

## <a name="array-conversions"></a>Konwersje tablicowe

W tym przykładzie pokazano, jak używać [Platform::Array](../cppcx/platform-array-class.md) do konstruowania innych rodzajów kolekcji:

[!code-cpp[cx_arrays#05](../cppcx/codesnippet/CPP/js-array/class1.cpp#05)]

W następnym przykładzie pokazano, jak skonstruować [Platform::Array](../cppcx/platform-array-class.md) z tablicy w stylu C i zwrócić ją z metody publicznej.

[!code-cpp[cx_arrays#06](../cppcx/codesnippet/CPP/js-array/class1.cpp#06)]

## <a name="jagged-arrays"></a>Tablice postrzępione

System typu środowiska wykonawczego systemu Windows nie obsługuje pojęcia postrzępione tablice i dlatego nie można użyć `IVector<Platform::Array<T>>` jako wartość zwracana lub parametr metody w metodzie publicznej. Aby przekazać postrzępioną tablicę lub sekwencję `IVector<IVector<T>^>`sekwencji w całej ABI, użyj .

## <a name="use-arrayreference-to-avoid-copying-data"></a>Użyj funkcji ArrayReference, aby uniknąć kopiowania danych

W niektórych scenariuszach, w których dane są przekazywane przez ABI do [Platformy::Array](../cppcx/platform-array-class.md), a ostatecznie chcesz przetworzyć te dane w tablicy w stylu C dla wydajności, można użyć [Platform::ArrayReference,](../cppcx/platform-arrayreference-class.md) aby uniknąć dodatkowej operacji kopiowania. Po przekroeniu [Platform::ArrayReference](../cppcx/platform-arrayreference-class.md) jako argument do `Platform::Array`parametru, który przyjmuje , `ArrayReference` będzie przechowywać dane bezpośrednio do tablicy w stylu C, które określisz. Wystarczy pamiętać, `ArrayReference` że nie ma blokady danych źródłowych, więc jeśli te dane są modyfikowane lub usuwane w innym wątku przed zakończeniem wywołania, wyniki będą niezdefiniowane.

Poniższy fragment kodu pokazuje, jak skopiować wyniki operacji [DataReader](/uwp/api/windows.storage.streams.datareader) do `Platform::Array` (zwykły wzorzec), a następnie jak zastąpić, `ArrayReference` aby skopiować dane bezpośrednio do tablicy w stylu C:

[!code-cpp[cx_arrays#07](../cppcx/codesnippet/CPP/js-array/class1.h#07)]

## <a name="avoid-exposing-an-array-as-a-property"></a>Unikaj ujawniania array jako właściwości

Ogólnie rzecz biorąc należy unikać `Platform::Array` ujawniania typu jako właściwości w klasie ref, ponieważ cała tablica jest zwracana nawet wtedy, gdy kod klienta próbuje uzyskać dostęp tylko do pojedynczego elementu. Gdy trzeba udostępnić kontener sekwencji jako właściwość w klasie public ref, [Windows::Foundation::IVector](/uwp/api/windows.foundation.collections.ivector-1) jest lepszym wyborem. W prywatnych lub wewnętrznych interfejsach API (które nie są publikowane w metadanych) należy rozważyć użycie standardowego kontenera Języka C++, takiego jak [std::vector](../standard-library/vector-class.md).

## <a name="see-also"></a>Zobacz też

[System typów](../cppcx/type-system-c-cx.md)<br/>
[Odwołanie do języka C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Dokumentacja przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)
