---
title: '&lt;Numeryczne&gt;'
ms.date: 11/04/2016
f1_keywords:
- <numeric>
helpviewer_keywords:
- <numeric> header
ms.assetid: 6d6ccb94-48cc-479b-b4a9-bd9c78d4896a
ms.openlocfilehash: ce195742605c3dd2e127c84ac2f4e1e696c75bd0
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246694"
---
# <a name="ltnumericgt"></a>&lt;Numeryczne&gt;

Definiuje funkcje szablonu kontenera, które wykonują algorytmy dla przetwarzania numerycznego.

## <a name="requirements"></a>Wymagania

**Nagłówek**: \<liczbowych >

**Namespace:** standardowe

## <a name="remarks"></a>Uwagi

Algorytmy numeryczne przypominają algorytmy standardowej biblioteki języka C++ w [ \<algorytm >](algorithm.md)i mogą działać na różnych strukturach danych. Należą do nich klasy kontenera standardowej biblioteki — na przykład [wektor](../standard-library/vector-class.md) i [listy](../standard-library/list-class.md)i struktury danych zdefiniowane przez program i tablice elementów, które spełniają wymogi określonego algorytmu. Te algorytmy osiągają ten poziom ogólności przez dostęp i przechodzenie przez elementy kontenera pośrednio poprzez iteratory. Te algorytmy przetwarzają zakresy iteratorów, które zazwyczaj są określane przez ich początkową lub końcową pozycję. Odnośne zakresy muszą być prawidłowe w tym sensie, że wszystkie wskaźniki w zakresach muszą być wyłuskiwalne i znajdować się w ramach sekwencji każdego zakresu, a ostatnia pozycja musi być osiągalna od pierwszej przez inkrementację.

Te algorytmy rozszerzają działania, które są obsługiwane przez operacje i funkcje elementów członkowskich każdego kontenery standardowej biblioteki języka C++ i umożliwiają interakcję z różnymi typami obiektów kontenera, w tym samym czasie.

## <a name="members"></a>Elementy członkowskie

### <a name="functions"></a>Funkcje

|||
|-|-|
|[accumulate](../standard-library/numeric-functions.md#accumulate)|Oblicza sumę wszystkich elementów w określonym zakresie — w tym niektóre wartości początkowe — przez obliczanie kolejnych sum częściowych, lub oblicza kolejne wyniki częściowe, które są uzyskiwane przy użyciu określonej operacji binarnej zamiast operacji sumowania.|
|[adjacent_difference](../standard-library/numeric-functions.md#adjacent_difference)|Oblicza kolejne różnice między każdym elementem i jego poprzednikiem w zakresie wejściowym i generuje wyjściowe wyniki do zakresu docelowego, lub oblicza wynik ogólnej procedury, gdzie operacja różnicy zostaje zastąpiona przez inną określoną operację binarną.|
|[exclusive_scan](../standard-library/numeric-functions.md#exclusive_scan)||
|[GCD](../standard-library/numeric-functions.md#gcd)||
|[inclusive_scan](../standard-library/numeric-functions.md#inclusive_scan)||
|[inner_product](../standard-library/numeric-functions.md#inner_product)|Oblicza sumę wyników mnożenia elementów z dwóch zakresów i dodaje ją do określonej wartości początkowej lub oblicza wynik opis ogólnej procedury, gdzie operacje sumowania i mnożenia są zastępowane przez inne określone operacje binarne.|
|[iota](../standard-library/numeric-functions.md#iota)|Przechowuje wartość początkową, zaczynając od pierwszego elementu i wypełniając kolejne przyrosty wartości (`value++`) we wszystkich elementów w interwale `[first, last)`.|
|[LCM](../standard-library/numeric-functions.md#lcm)||
|[partial_sum —](../standard-library/numeric-functions.md#partial_sum)|Oblicza serię sum zakresu wejściowego od pierwszego elementu przez *i*Ty element i zapisuje wynik każdej sumy w *i*-tym elemencie zakresu docelowego lub oblicza wynik ogólnej procedury, gdzie suma operacji jest zastępowana inną określoną operacją binarną.|
|[Zmniejsz](../standard-library/numeric-functions.md#reduce)||
|[transform_exclusive_scan](../standard-library/numeric-functions.md#transform_exclusive_scan)||
|[transform_inclusive_scan](../standard-library/numeric-functions.md#transform_inclusive_scan)||
|[transform_reduce](../standard-library/numeric-functions.md#transform_reduce)||

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
