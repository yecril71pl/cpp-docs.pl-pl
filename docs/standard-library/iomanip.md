---
title: '&lt;iomanip&gt;'
ms.date: 11/04/2016
f1_keywords:
- iomanip/std::<iomanip>
- <iomanip>
helpviewer_keywords:
- iomanip header
ms.assetid: 3681c346-4763-4037-bba4-cf0dc3447974
ms.openlocfilehash: 983fbc190fb83b81534e3888c748c0bf9c235638
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2018
ms.locfileid: "51524667"
---
# <a name="ltiomanipgt"></a>&lt;iomanip&gt;

Obejmują `iostreams` standardowy nagłówek \<iomanip > Aby zdefiniować kilka manipulatory wykonać każdy pojedynczy argument.

## <a name="syntax"></a>Składnia

```cpp
#include <iomanip>
```

## <a name="remarks"></a>Uwagi

Każda z tych manipulatory zwraca nieokreślonego typu o nazwie `T1` za pośrednictwem `T10`, że oba przeciążenia `basic_istream` \< **Elem**, **Tr** > `::` [operator >>](../standard-library/istream-operators.md#op_gt_gt) i `basic_ostream` \< **Elem**, **Tr** > `::` [operator <<](../standard-library/ostream-operators.md#op_lt_lt).

### <a name="manipulators"></a>Manipulatory

|||
|-|-|
|[get_money](../standard-library/iomanip-functions.md#iomanip_get_money)|Pobiera wartość pieniężna opcjonalnie w formacie międzynarodowym.|
|[get_time](../standard-library/iomanip-functions.md#iomanip_get_time)|Pobiera czas w strukturze czasu przy użyciu określonego formatu.|
|[put_money](../standard-library/iomanip-functions.md#iomanip_put_money)|Zawiera kwotę pieniężną, opcjonalnie w formacie międzynarodowym.|
|[put_time](../standard-library/iomanip-functions.md#iomanip_put_time)|Zawiera godzinę w strukturze czasu i ciąg formatu do użycia.|
|[w cudzysłowach](../standard-library/iomanip-functions.md#quoted)|Umożliwia wygodne obustronne Konwertowanie ciągów z operatorów wstawiania i wyodrębniania.|
|[resetiosflags](../standard-library/iomanip-functions.md#resetiosflags)|Czyści określone flagi.|
|[setbase](../standard-library/iomanip-functions.md#setbase)|Ustawianie bazy dla liczb całkowitych.|
|[setfill](../standard-library/iomanip-functions.md#setfill)|Określa znak, który będzie używany do wypełnienia miejsca do magazynowania w wyświetlaną z prawej strony.|
|[setiosflags](../standard-library/iomanip-functions.md#setiosflags)|Ustawia określone flagi.|
|[setprecision](../standard-library/iomanip-functions.md#setprecision)|Ustawia precyzja wartości zmiennoprzecinkowych.|
|[setw](../standard-library/iomanip-functions.md#setw)|Określa szerokość wyświetlanego pola.|

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream, programowanie](../standard-library/iostream-programming.md)<br/>
[Konwencje iostream](../standard-library/iostreams-conventions.md)<br/>
