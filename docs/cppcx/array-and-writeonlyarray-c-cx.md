---
title: Tablica i WriteOnlyArray (C++/CX)
ms.date: 01/22/2017
ms.assetid: ef7cc5f9-cae6-4636-8220-f789e5b6aea4
ms.openlocfilehash: 1980fbcd1e2fa8cdaa48e00d2e7de9e45ac96a92
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231029"
---
# <a name="array-and-writeonlyarray-ccx"></a>Tablica i WriteOnlyArray (C++/CX)

Można swobodnie używać zwykłych tablic w stylu C lub [`std::array`](../standard-library/array-class-stl.md) w programie C++/CX (chociaż [`std::vector`](../standard-library/vector-class.md) często jest to lepszy wybór), ale w dowolnym interfejsie API, który jest publikowany w metadanych, należy przekonwertować tablicę w stylu C lub wektor na [`Platform::Array`](../cppcx/platform-array-class.md) Typ lub w [`Platform::WriteOnlyArray`](../cppcx/platform-writeonlyarray-class.md) zależności od sposobu jego użycia. [`Platform::Array`](../cppcx/platform-array-class.md)Typ nie jest skuteczny ani tak samo jak w przypadku [`std::vector`](../standard-library/vector-class.md) ogólnego wytycznych, dlatego należy unikać używania w kodzie wewnętrznym, który wykonuje wiele operacji na elementach tablicy.

Następujące typy tablic można przekazywać przez ABI:

1. `const Platform::Array^`

1. `Platform::Array^*`

1. `Platform::WriteOnlyArray`

1. wartość zwracana przez`Platform::Array^`

Te typy tablic są używane do implementowania trzech rodzajów wzorców tablicowych, które są zdefiniowane przez środowisko wykonawcze systemu Windows.

PassArray\
Używany, gdy obiekt wywołujący przekazuje tablicę do metody. Typ parametru wejściowego C++ to **`const`** [`Platform::Array`](../cppcx/platform-array-class.md) \<T> .

Metodzie FillArray
Używany, gdy obiekt wywołujący przekazuje tablicę dla metody do wypełnienia. Typ parametru wejściowego C++ to [`Platform::WriteOnlyArray`](../cppcx/platform-writeonlyarray-class.md) \<T> .

ReceiveArray\
Używany, gdy obiekt wywołujący otrzymuje tablicę, która jest przydzielona przez metodę. W języku C++/CX można zwrócić tablicę w zwracanej wartości jako tablicę ^ lub można ją zwrócić jako parametr out jako tablicę typu.

## <a name="passarray-pattern"></a>Wzorzec PassArray

Gdy kod klienta przekazuje tablicę do metody języka C++, a metoda nie modyfikuje go, Metoda akceptuje tablicę jako `const Array^` . Na poziomie środowisko wykonawcze systemu Windows aplikacji interfejs binarny (ABI) jest on znany jako *PassArray*. W następnym przykładzie pokazano, jak przekazać tablicę, która jest przypisana w języku JavaScript do funkcji języka C++, która odczytuje z niej.

[!code-javascript[cx_arrays#101](../cppcx/codesnippet/JavaScript/array-and-writeonlyarray-c-_1.js)]

Poniższy fragment kodu przedstawia metodę języka C++:

[!code-cpp[cx_arrays#01](../cppcx/codesnippet/CPP/js-array/class1.cpp#01)]

## <a name="receivearray-pattern"></a>Wzorzec ReceiveArray

W wzorcu *ReceiveArray* kod klienta deklaruje tablicę i przekazuje ją do metody, która przydziela pamięć dla niej i inicjuje ją. Typ parametru wejściowego C++ jest wskaźnikiem do Hat: `Array<T>^*` . Poniższy przykład pokazuje, jak zadeklarować obiekt Array w języku JavaScript i przekazać go do funkcji języka C++, która przypisuje pamięć, inicjuje elementy i zwraca je do języka JavaScript. Kod JavaScript traktuje przydzieloną tablicę jako wartość zwracaną, ale funkcja C++ traktuje ją jako parametr out.

[!code-javascript[cx_arrays#102](../cppcx/codesnippet/JavaScript/array-and-writeonlyarray-c-_3.js)]

Poniższy fragment kodu przedstawia dwa sposoby implementacji metody C++:

[!code-cpp[cx_arrays#02](../cppcx/codesnippet/CPP/js-array/class1.cpp#02)]

## <a name="fill-arrays"></a>Wypełnianie tablic

Jeśli chcesz przydzielić tablicę obiektu wywołującego i zainicjować lub zmodyfikować w obiekcie wywoływanym, użyj metody `WriteOnlyArray` . W następnym przykładzie pokazano, jak zaimplementować funkcję języka C++, która używa `WriteOnlyArray` i wywołać ją z poziomu języka JavaScript.

[!code-javascript[cx_arrays#103](../cppcx/codesnippet/JavaScript/array-and-writeonlyarray-c-_5.js)]

Poniższy fragment kodu przedstawia sposób implementacji metody języka C++:

[!code-cpp[cx_arrays#03](../cppcx/codesnippet/CPP/js-array/class1.cpp#03)]

## <a name="array-conversions"></a>Konwersje tablic

Ten przykład pokazuje, jak używać [`Platform::Array`](../cppcx/platform-array-class.md) do tworzenia innych rodzajów kolekcji:

[!code-cpp[cx_arrays#05](../cppcx/codesnippet/CPP/js-array/class1.cpp#05)]

W następnym przykładzie pokazano, jak utworzyć obiekt [`Platform::Array`](../cppcx/platform-array-class.md) z tablicy w stylu C i zwrócić go z metody publicznej.

[!code-cpp[cx_arrays#06](../cppcx/codesnippet/CPP/js-array/class1.cpp#06)]

## <a name="jagged-arrays"></a>Tablice nieregularne

System typu środowisko wykonawcze systemu Windows nie obsługuje koncepcji tablic nieregularnych, dlatego nie można użyć `IVector<Platform::Array<T>>` jako wartości zwracanej lub parametru metody w metodzie publicznej. Aby przekazać nieregularną tablicę lub sekwencję sekwencji w ramach ABI, użyj `IVector<IVector<T>^>` .

## <a name="use-arrayreference-to-avoid-copying-data"></a>Użyj ArrayReference, aby uniknąć kopiowania danych

W niektórych scenariuszach, w których dane są przesyłane przez ABI do obiektu [`Platform::Array`](../cppcx/platform-array-class.md) , a ostatecznie chcesz przetworzyć te dane w tablicy w stylu C w celu zwiększenia wydajności, możesz użyć [platformy:: ArrayReference](../cppcx/platform-arrayreference-class.md) , aby uniknąć dodatkowej operacji kopiowania. Gdy przekazujesz [`Platform::ArrayReference`](../cppcx/platform-arrayreference-class.md) jako argument do parametru, który pobiera `Platform::Array` , `ArrayReference` dane będą przechowywane bezpośrednio w tablicy w stylu C, którą określisz. Należy pamiętać, że `ArrayReference` nie ma blokady danych źródłowych, więc jeśli dane są modyfikowane lub usuwane w innym wątku przed ukończeniem wywołania, wyniki będą niezdefiniowane.

Poniższy fragment kodu przedstawia sposób kopiowania wyników [`DataReader`](/uwp/api/windows.storage.streams.datareader) operacji do `Platform::Array` (zwykły wzorzec), a następnie sposób podstawiania `ArrayReference` w celu skopiowania danych bezpośrednio do tablicy w stylu C:

[!code-cpp[cx_arrays#07](../cppcx/codesnippet/CPP/js-array/class1.h#07)]

## <a name="avoid-exposing-an-array-as-a-property"></a>Unikaj ujawniania tablicy jako właściwości

Ogólnie rzecz biorąc, należy unikać ujawniania `Platform::Array` typu jako właściwości w klasie referencyjnej, ponieważ cała tablica jest zwracana nawet wtedy, gdy kod klienta próbuje uzyskać dostęp do pojedynczego elementu. Jeśli trzeba uwidocznić kontener sekwencji jako właściwość w publicznej klasie referencyjnej, [`Windows::Foundation::IVector`](/uwp/api/windows.foundation.collections.ivector-1) jest to lepszy wybór. W prywatnych lub wewnętrznych interfejsach API (które nie są publikowane w metadanych) Rozważ użycie standardowego kontenera C++, takiego jak [`std::vector`](../standard-library/vector-class.md) .

## <a name="see-also"></a>Zobacz także

[System typów](../cppcx/type-system-c-cx.md)<br/>
[Dokumentacja języka C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Dokumentacja przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)
