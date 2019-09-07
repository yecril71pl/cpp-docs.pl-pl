---
title: Array i WriteOnlyArray (C++/CX)
ms.date: 01/22/2017
ms.assetid: ef7cc5f9-cae6-4636-8220-f789e5b6aea4
ms.openlocfilehash: 2ade7981d391288edd78f622b4753d546c5eaa04
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740690"
---
# <a name="array-and-writeonlyarray-ccx"></a>Array i WriteOnlyArray (C++/CX)

Można swobodnie używać zwykłych tablic w stylu C lub [std:: Array](../standard-library/array-class-stl.md) w programie C++/CX (chociaż [std:: Vector](../standard-library/vector-class.md) jest często lepszym wyborem), ale w dowolnym interfejsie API, który jest publikowany w metadanych, należy skonwertować tablicę w stylu C lub wektor na [platformę:: Array ](../cppcx/platform-array-class.md)lub [platform:: WriteOnlyArray](../cppcx/platform-writeonlyarray-class.md) , w zależności od tego, jak jest używany. Typ [platform:: Array](../cppcx/platform-array-class.md) nie jest wydajny ani bardzo wydajny jak [std:: Vector](../standard-library/vector-class.md), dlatego w ogólnym wytycznych należy unikać używania w kodzie wewnętrznym, który wykonuje wiele operacji na elementach tablicy.

Następujące typy tablic można przekazywać przez ABI:

1. const platform:: Array ^

1. Platform:: Array ^ *

1. Platforma:: WriteOnlyArray

1. wartość zwracana platformy:: Array ^

Te typy tablic są używane do implementowania trzech rodzajów wzorców tablicowych, które są zdefiniowane przez środowisko wykonawcze systemu Windows.

PassArray używany, gdy obiekt wywołujący przekazuje tablicę do metody. Typ C++ parametru wejściowego to `const` [platform:: Array](../cppcx/platform-array-class.md)\<T >.

Metodzie FillArray używany, gdy obiekt wywołujący przekazuje tablicę dla metody do wypełnienia. Typ C++ parametru wejściowego to [platform:: WriteOnlyArray](../cppcx/platform-writeonlyarray-class.md)\<T >.

ReceiveArray używany, gdy obiekt wywołujący otrzymuje tablicę, która jest przydzielana przez metodę. W C++/CX można zwrócić tablicę w zwracanej wartości jako tablicę ^ lub można ją zwrócić jako parametr out jako tablicę typu% *.

## <a name="passarray-pattern"></a>Wzorzec PassArray

Gdy kod klienta przekazuje tablicę do C++ metody, a metoda nie modyfikuje go, Metoda akceptuje tablicę jako tablicę const ^. Na poziomie środowisko wykonawcze systemu Windows aplikacji interfejs binarny (ABI) jest on znany jako PassArray. W następnym przykładzie pokazano, jak przekazać tablicę, która jest przypisana w języku C++ JavaScript do funkcji, która odczytuje z niej.

[!code-javascript[cx_arrays#101](../cppcx/codesnippet/JavaScript/array-and-writeonlyarray-c-_1.js)]

Poniższy fragment kodu przedstawia C++ metodę:

[!code-cpp[cx_arrays#01](../cppcx/codesnippet/CPP/js-array/class1.cpp#01)]

## <a name="receivearray-pattern"></a>Wzorzec ReceiveArray

W wzorcu ReceiveArray kod klienta deklaruje tablicę i przekazuje ją do metody, która przydziela pamięć dla niej i inicjuje ją. Typ C++ parametru wejściowego jest wskaźnikiem do Hat: `Array<T>^*`. Poniższy przykład pokazuje, jak zadeklarować obiekt Array w języku JavaScript i przekazać go do C++ funkcji, która przypisuje pamięć, inicjuje elementy i zwraca je do języka JavaScript. Kod JavaScript traktuje przydzieloną tablicę jako wartość zwracaną C++ , ale funkcja traktuje ją jako parametr out.

[!code-javascript[cx_arrays#102](../cppcx/codesnippet/JavaScript/array-and-writeonlyarray-c-_3.js)]

Poniższy fragment kodu przedstawia dwa sposoby implementacji C++ metody:

[!code-cpp[cx_arrays#02](../cppcx/codesnippet/CPP/js-array/class1.cpp#02)]

## <a name="fill-arrays"></a>Wypełnianie tablic

Jeśli chcesz przydzielić tablicę obiektu wywołującego i zainicjować lub zmodyfikować w obiekcie wywoływanym, użyj `WriteOnlyArray`metody. W następnym przykładzie pokazano, jak zaimplementować C++ funkcję, która używa `WriteOnlyArray` i wywołać ją z poziomu języka JavaScript.

[!code-javascript[cx_arrays#103](../cppcx/codesnippet/JavaScript/array-and-writeonlyarray-c-_5.js)]

Poniższy fragment kodu przedstawia sposób implementacji C++ metody:

[!code-cpp[cx_arrays#03](../cppcx/codesnippet/CPP/js-array/class1.cpp#03)]

## <a name="array-conversions"></a>Konwersje tablic

Ten przykład pokazuje, jak używać klasy [platform:: Array](../cppcx/platform-array-class.md) do konstruowania innych rodzajów kolekcji:

[!code-cpp[cx_arrays#05](../cppcx/codesnippet/CPP/js-array/class1.cpp#05)]

W następnym przykładzie pokazano, jak utworzyć [platformę:: Array](../cppcx/platform-array-class.md) z tablicy w stylu C i zwrócić ją z metody publicznej.

[!code-cpp[cx_arrays#06](../cppcx/codesnippet/CPP/js-array/class1.cpp#06)]

## <a name="jagged-arrays"></a>Tablice nieregularne

System typu środowisko wykonawcze systemu Windows nie obsługuje koncepcji tablic nieregularnych, dlatego nie można użyć `IVector<Platform::Array<T>>` jako wartości zwracanej lub parametru metody w metodzie publicznej. Aby przekazać nieregularną tablicę lub sekwencję sekwencji w ramach ABI, użyj `IVector<IVector<T>^>`.

## <a name="use-arrayreference-to-avoid-copying-data"></a>Użyj ArrayReference, aby uniknąć kopiowania danych

W niektórych scenariuszach, w których dane są przesyłane przez ABI do obiektu [platform:: Array](../cppcx/platform-array-class.md), a ostatecznie chcesz przetworzyć te dane w tablicy w stylu C w celu zwiększenia wydajności, możesz użyć [platformy:: ArrayReference](../cppcx/platform-arrayreference-class.md) , aby uniknąć dodatkowej operacji kopiowania. Gdy przekazujesz [platformę:: ArrayReference](../cppcx/platform-arrayreference-class.md) jako argument do parametru, który pobiera obiekt `Platform::Array`, `ArrayReference` dane będą przechowywane bezpośrednio w tablicy w stylu C, którą określisz. Należy pamiętać, że `ArrayReference` nie ma blokady danych źródłowych, więc jeśli dane są modyfikowane lub usuwane w innym wątku przed ukończeniem wywołania, wyniki będą niezdefiniowane.

Poniższy fragment kodu przedstawia sposób kopiowania wyników operacji elementu [DataReader](/uwp/api/Windows.Storage.Streams.DataReader) do `Platform::Array` (zwykły wzorzec), a następnie sposób podstawiania `ArrayReference` w celu skopiowania danych bezpośrednio do tablicy w stylu C:

[!code-cpp[cx_arrays#07](../cppcx/codesnippet/CPP/js-array/class1.h#07)]

## <a name="avoid-exposing-an-array-as-a-property"></a>Unikaj ujawniania tablicy jako właściwości

Ogólnie rzecz biorąc, należy unikać ujawniania `Platform::Array` typu jako właściwości w klasie referencyjnej, ponieważ cała tablica jest zwracana nawet wtedy, gdy kod klienta próbuje uzyskać dostęp do pojedynczego elementu. Gdy konieczne jest uwidocznienie kontenera sekwencji jako właściwości w publicznej klasie ref, należy poprawić wybór [systemu Windows:: Foundation:: IVector](/uwp/api/Windows.Foundation.Collections.IVector_T_) . W prywatnych lub wewnętrznych interfejsach API (które nie są publikowane w metadanych) Rozważ użycie standardowego C++ kontenera, takiego jak [std:: Vector](../standard-library/vector-class.md).

## <a name="see-also"></a>Zobacz także

[System typów](../cppcx/type-system-c-cx.md)<br/>
[Dokumentacja języka C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Dokumentacja przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)
