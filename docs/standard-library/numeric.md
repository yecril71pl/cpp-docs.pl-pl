---
title: '&lt;liczbowa&gt; | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <numeric>
dev_langs:
- C++
helpviewer_keywords:
- <numeric> header
ms.assetid: 6d6ccb94-48cc-479b-b4a9-bd9c78d4896a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c5705414bdc6915e758d66576855a45db5fcad23
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="ltnumericgt"></a>&lt;numeryczne&gt;

Definiuje funkcje szablonu kontenera, które wykonują algorytmy dla przetwarzania numerycznego.

## <a name="syntax"></a>Składnia

```cpp
#include <numeric>
```

## <a name="remarks"></a>Uwagi

Numeryczne algorytmów przypominać algorytmy standardowa biblioteka C++ [ \<algorytm >](algorithm.md)i może działać na różnych struktury danych. Należą do klasy kontenerów biblioteki standardowej — na przykład [wektor](../standard-library/vector-class.md) i [listy](../standard-library/list-class.md)i struktur danych programu i tablice elementów, które spełniają wymagania dotyczące konkretnego algorytmu. Te algorytmy osiągają ten poziom ogólności przez dostęp i przechodzenie przez elementy kontenera pośrednio poprzez iteratory. Te algorytmy przetwarzają zakresy iteratorów, które zazwyczaj są określane przez ich początkową lub końcową pozycję. Odnośne zakresy muszą być prawidłowe w tym sensie, że wszystkie wskaźniki w zakresach muszą być wyłuskiwalne i znajdować się w ramach sekwencji każdego zakresu, a ostatnia pozycja musi być osiągalna od pierwszej przez inkrementację.

Algorytmy rozszerzyć akcje, które są obsługiwane przez operacje i funkcje Członkowskie każdego kontenery standardowa biblioteka C++ i włączyć współdziałanie z różnymi typami obiektów kontenera w tym samym czasie.

### <a name="functions"></a>Funkcje

|Funkcja|Opis|
|-|-|
|[accumulate](../standard-library/numeric-functions.md#accumulate)|Oblicza sumę wszystkich elementów w określonym zakresie — w tym niektóre wartości początkowe — przez obliczanie kolejnych sum częściowych, lub oblicza kolejne wyniki częściowe, które są uzyskiwane przy użyciu określonej operacji binarnej zamiast operacji sumowania.|
|[adjacent_difference](../standard-library/numeric-functions.md#adjacent_difference)|Oblicza kolejne różnice między każdym elementem i jego poprzednikiem w zakresie wejściowym i generuje wyjściowe wyniki do zakresu docelowego, lub oblicza wynik ogólnej procedury, gdzie operacja różnicy zostaje zastąpiona przez inną określoną operację binarną.|
|[inner_product](../standard-library/numeric-functions.md#inner_product)|Oblicza sumę wyników mnożenia elementów z dwóch zakresów i dodaje ją do określonej wartości początkowej lub oblicza wynik opis ogólnej procedury, gdzie operacje sumowania i mnożenia są zastępowane przez inne określone operacje binarne.|
|[iota](../standard-library/numeric-functions.md#iota)|Przechowuje wartość początkową, zaczynając od pierwszego elementu i wypełnianie kolejne przyrosty wartości (`value++`) w każdym z elementów w interwale `[first, last)`.|
|[partial_sum](../standard-library/numeric-functions.md#partial_sum)|Oblicza szereg sum zakresu wejściowego od pierwszego elementu za pomocą *i*th element i zapisuje wynik każdego Suma w *i*element th zakresu docelowego, lub oblicza wynik ogólnych gdzie operacji suma zostanie zastąpiony przez inną operację binarną określona.|

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
