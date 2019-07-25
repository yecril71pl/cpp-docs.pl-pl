---
title: '&lt;iomanip&gt;'
ms.date: 11/04/2016
f1_keywords:
- iomanip/std::<iomanip>
- <iomanip>
helpviewer_keywords:
- iomanip header
ms.assetid: 3681c346-4763-4037-bba4-cf0dc3447974
ms.openlocfilehash: b9da0de64bbb0ef48a6a9741ff941e6abda0e705
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449207"
---
# <a name="ltiomanipgt"></a>&lt;iomanip&gt;

Uwzględnij \<standardowy nagłówek iomanip >, aby zdefiniować kilka manipulowania, które każdy z nich przyjmuje jeden argument. `iostreams`

## <a name="syntax"></a>Składnia

```cpp
#include <iomanip>
```

## <a name="remarks"></a>Uwagi

Każdy z tych elementów manipuluje zwraca nieokreślony typ, który `T1` jest `T10`wywoływany przez, `basic_istream`który przeciąża \< **elem**,[> operator](../standard-library/istream-operators.md#op_gt_gt) **TR**>`::`> i `basic_ostream` **Elem,** [operator](../standard-library/ostream-operators.md#op_lt_lt) **TR**<<.> \<`::`

### <a name="manipulators"></a>Manipulatory

|||
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

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[Bezpieczeństwo wątku w C++ standardowej bibliotece](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programowanie iostream](../standard-library/iostream-programming.md)\
[Konwencje iostream](../standard-library/iostreams-conventions.md)
