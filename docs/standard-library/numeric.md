---
title: '&lt;przypada&gt;'
ms.date: 11/04/2016
f1_keywords:
- <numeric>
helpviewer_keywords:
- <numeric> header
ms.assetid: 6d6ccb94-48cc-479b-b4a9-bd9c78d4896a
ms.openlocfilehash: ee1e26d3f174d21ab1ad2c847d292ad075cc0f71
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88830595"
---
# <a name="ltnumericgt"></a>&lt;przypada&gt;

Definiuje funkcje szablonu kontenera, które wykonują algorytmy dla przetwarzania numerycznego.

## <a name="requirements"></a>Wymagania

**Nagłówek**: \<numeric>

**Przestrzeń nazw:** std

## <a name="remarks"></a>Uwagi

Algorytmy numeryczne są podobne do algorytmów standardowej biblioteki języka C++ w systemie [\<algorithm>](algorithm.md) i mogą działać na różnych strukturach danych. Należą do nich klasy kontenerów biblioteki standardowej — na przykład [wektorowe](../standard-library/vector-class.md) i [listę](../standard-library/list-class.md)oraz struktury danych zdefiniowane przez program i tablice elementów, które spełniają wymagania określonego algorytmu. Te algorytmy osiągają ten poziom ogólności przez dostęp i przechodzenie przez elementy kontenera pośrednio poprzez iteratory. Te algorytmy przetwarzają zakresy iteratorów, które zazwyczaj są określane przez ich początkową lub końcową pozycję. Odnośne zakresy muszą być prawidłowe w tym sensie, że wszystkie wskaźniki w zakresach muszą być wyłuskiwalne i znajdować się w ramach sekwencji każdego zakresu, a ostatnia pozycja musi być osiągalna od pierwszej przez inkrementację.

Algorytmy zwiększają działania, które są obsługiwane przez operacje i funkcje elementów członkowskich każdego z kontenerów standardowej biblioteki C++ i umożliwiają interakcję z różnymi typami obiektów kontenera w tym samym czasie.

## <a name="members"></a>Elementy członkowskie

### <a name="functions"></a>Functions

|Nazwa|Opis|
|-|-|
|[Accumulate](../standard-library/numeric-functions.md#accumulate)|Oblicza sumę wszystkich elementów w określonym zakresie — w tym niektóre wartości początkowe — przez obliczanie kolejnych sum częściowych, lub oblicza kolejne wyniki częściowe, które są uzyskiwane przy użyciu określonej operacji binarnej zamiast operacji sumowania.|
|[adjacent_difference](../standard-library/numeric-functions.md#adjacent_difference)|Oblicza kolejne różnice między każdym elementem i jego poprzednikiem w zakresie wejściowym i generuje wyjściowe wyniki do zakresu docelowego, lub oblicza wynik ogólnej procedury, gdzie operacja różnicy zostaje zastąpiona przez inną określoną operację binarną.|
|[exclusive_scan](../standard-library/numeric-functions.md#exclusive_scan)||
|[GCD](../standard-library/numeric-functions.md#gcd)||
|[inclusive_scan](../standard-library/numeric-functions.md#inclusive_scan)||
|[inner_product](../standard-library/numeric-functions.md#inner_product)|Oblicza sumę wyników mnożenia elementów z dwóch zakresów i dodaje ją do określonej wartości początkowej lub oblicza wynik opis ogólnej procedury, gdzie operacje sumowania i mnożenia są zastępowane przez inne określone operacje binarne.|
|[IOTA](../standard-library/numeric-functions.md#iota)|Przechowuje wartość początkową, zaczynając od pierwszego elementu i wypełniając kolejne przyrosty wartości ( `value++` ) w każdym z elementów w interwale `[first, last)` .|
|[LCM](../standard-library/numeric-functions.md#lcm)||
|[partial_sum](../standard-library/numeric-functions.md#partial_sum)|Oblicza serię sum w zakresie wejściowym od pierwszego elementu za pośrednictwem *i i*zapisuje wynik każdej sumy w *i*-tym elemencie zakresu docelowego lub oblicza wynik ogólnej procedury, gdzie operacja sum jest zastępowana przez inną określoną operację binarną.|
|[zmniejszenie](../standard-library/numeric-functions.md#reduce)||
|[transform_exclusive_scan](../standard-library/numeric-functions.md#transform_exclusive_scan)||
|[transform_inclusive_scan](../standard-library/numeric-functions.md#transform_inclusive_scan)||
|[transform_reduce](../standard-library/numeric-functions.md#transform_reduce)||

## <a name="see-also"></a>Zobacz też

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Dokumentacja standardowej biblioteki języka C++](../standard-library/cpp-standard-library-reference.md)
