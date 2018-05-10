---
title: '&lt;iomanip&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- iomanip/std::<iomanip>
- <iomanip>
dev_langs:
- C++
helpviewer_keywords:
- iomanip header
ms.assetid: 3681c346-4763-4037-bba4-cf0dc3447974
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9a410dae35771d89b9d9ae72c8221501f051d10e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="ltiomanipgt"></a>&lt;iomanip&gt;

Obejmują `iostreams` standardowy nagłówek \<iomanip — > Aby zdefiniować kilka manipulatory każdy wykonać jeden argument.

## <a name="syntax"></a>Składnia

```cpp
#include <iomanip>

```

## <a name="remarks"></a>Uwagi

Zwraca każdy z tych manipulatory nieokreślonego typu o nazwie **T1** za pośrednictwem **T10**, który zarówno overloads `basic_istream` \< **elementu**, **Tr**>`::`[operator >>](../standard-library/istream-operators.md#op_gt_gt) i `basic_ostream` \< **elementu**, **Tr** > `::` [operator <<](../standard-library/ostream-operators.md#op_lt_lt).

### <a name="manipulators"></a>Manipulatory

|||
|-|-|
|[get_money](../standard-library/iomanip-functions.md#iomanip_get_money)|Uzyskuje kwotę pieniężną, opcjonalnie w formacie międzynarodowej.|
|[get_time](../standard-library/iomanip-functions.md#iomanip_get_time)|Pobiera czas w strukturze czasu przy użyciu określonego formatu.|
|[put_money](../standard-library/iomanip-functions.md#iomanip_put_money)|Udostępnia pieniężnego, opcjonalnie w formacie międzynarodowej.|
|[put_time](../standard-library/iomanip-functions.md#iomanip_put_time)|Miejsce na godzinę w strukturze czasu i ciąg formatu do użycia.|
|[w cudzysłowach](../standard-library/iomanip-functions.md#quoted)|Umożliwia wygodne dwustronną komunikację ciągów z operatorów wstawiania i wyodrębniania.|
|[resetiosflags](../standard-library/iomanip-functions.md#resetiosflags)|Usuwa określone flagi.|
|[setbase](../standard-library/iomanip-functions.md#setbase)|Ustaw podstawowej liczb całkowitych.|
|[setfill](../standard-library/iomanip-functions.md#setfill)|Ustawia znak używany do wypełniania miejsc w prawej strony ekranu.|
|[setiosflags](../standard-library/iomanip-functions.md#setiosflags)|Ustawia określone flagi.|
|[setprecision](../standard-library/iomanip-functions.md#setprecision)|Ustawia dokładność wartości zmiennoprzecinkowych.|
|[setw](../standard-library/iomanip-functions.md#setw)|Określa szerokość pola wyświetlania.|

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream, programowanie](../standard-library/iostream-programming.md)<br/>
[Konwencje iostream](../standard-library/iostreams-conventions.md)<br/>
