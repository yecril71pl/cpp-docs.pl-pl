---
title: '&lt;iomanip&gt;'
ms.date: 11/04/2016
f1_keywords:
- iomanip/std::<iomanip>
- <iomanip>
helpviewer_keywords:
- iomanip header
ms.assetid: 3681c346-4763-4037-bba4-cf0dc3447974
ms.openlocfilehash: f3f6c4886d22c7cd12b29950c114fbcde8905c28
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845747"
---
# <a name="ltiomanipgt"></a>&lt;iomanip&gt;

Dołącz `iostreams` standardowy nagłówek, \<iomanip> Aby zdefiniować kilka manipulowania, które każdy z nich przyjmuje jeden argument.

## <a name="syntax"></a>Składnia

```cpp
#include <iomanip>
```

## <a name="remarks"></a>Uwagi

Każdy z tych elementów manipulowanych zwraca nieokreślony typ wywoływany `T1` przez `T10` , który przeciąża zarówno `basic_istream` \<**Elem**, **Tr**> `::` [>>operatora](../standard-library/istream-operators.md#op_gt_gt) , jak i `basic_ostream` \<**Elem**, **Tr**> `::` [<<operatora ](../standard-library/ostream-operators.md#op_lt_lt).

### <a name="manipulators"></a>Manipulatory

|Nazwa|Opis|
|-|-|
|[get_money](../standard-library/iomanip-functions.md#iomanip_get_money)|Uzyskuje kwotę pieniężną, opcjonalnie w formacie międzynarodowym.|
|[get_time](../standard-library/iomanip-functions.md#iomanip_get_time)|Uzyskuje czas w strukturze czasu przy użyciu określonego formatu.|
|[put_money](../standard-library/iomanip-functions.md#iomanip_put_money)|Zapewnia kwotę pieniężną, opcjonalnie w formacie międzynarodowym.|
|[put_time](../standard-library/iomanip-functions.md#iomanip_put_time)|Zapewnia godzinę w strukturze czasu i ciąg formatu do użycia.|
|[znak](../standard-library/iomanip-functions.md#quoted)|Umożliwia wygodną rundę ciągów z operatorami wstawiania i wyodrębniania.|
|[resetiosflags](../standard-library/iomanip-functions.md#resetiosflags)|Czyści określone flagi.|
|[setbase](../standard-library/iomanip-functions.md#setbase)|Ustaw bazę dla liczb całkowitych.|
|[setfill](../standard-library/iomanip-functions.md#setfill)|Ustawia znak, który będzie używany do wypełniania spacji w wyświetlaniu wyrównanym do prawej strony.|
|[setiosflags](../standard-library/iomanip-functions.md#setiosflags)|Ustawia określone flagi.|
|[setprecision](../standard-library/iomanip-functions.md#setprecision)|Ustawia precyzję dla wartości zmiennoprzecinkowych.|
|[setw](../standard-library/iomanip-functions.md#setw)|Określa szerokość pola wyświetlanego.|

## <a name="see-also"></a>Zobacz też

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programowanie iostream](../standard-library/iostream-programming.md)\
[Konwencje iostreams](../standard-library/iostreams-conventions.md)
