---
title: '&lt;ciąg&gt; | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- string/std::<string>
- <string>
dev_langs:
- C++
helpviewer_keywords:
- string header
ms.assetid: a2fb9d00-d7ae-4170-bfea-2dc337aa37cf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d335c684ab46846e9d3c49ef45522cf7288d916a
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="ltstringgt"></a>&lt;string&gt;

Definiuje klasę szablonu kontenera `basic_string` i różne szablony pomocniczych.

Aby uzyskać więcej informacji na temat `basic_string`, zobacz [basic_string — klasa](../standard-library/basic-string-class.md)

## <a name="syntax"></a>Składnia

```cpp
#include <string>
```

## <a name="remarks"></a>Uwagi

Języka C++ i standardowej biblioteki C++ obsługuje dwa typy parametrów:

- Tablice znaków zakończony znakiem null często określany jako ciągi C.

- Obiekty klasy szablonu, typu `basic_string`, obsługę wszystkich `char`— takich jak argumentów szablonu.

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[string](../standard-library/string-typedefs.md#string)|Typ, który opisuje specjalizacji szablonu klasy `basic_string` elementami typu `char` jako `string`.|
|[wstring](../standard-library/string-typedefs.md#wstring)|Typ, który opisuje specjalizacji szablonu klasy `basic_string` elementami typu `wchar_t` jako `wstring`.|
|[u16string](../standard-library/string-typedefs.md#u16string)|Typ, który opisuje specjalizacji szablonu klasy `basic_string` oparte na elementach typu `char16_t`.|
|[u32string](../standard-library/string-typedefs.md#u32string)|Typ, który opisuje specjalizacji szablonu klasy `basic_string` oparte na elementach typu `char32_t`.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator +](../standard-library/string-operators.md#op_add)|Łączy dwa obiekty ciągu.|
|[operator!=](../standard-library/string-operators.md#op_neq)|Testy, jeśli obiekt ciągu po lewej stronie operatora nie równa się z obiektem ciągu po prawej stronie.|
|[operator==](../standard-library/string-operators.md#op_eq_eq)|Testy, jeśli obiekt ciągu po lewej stronie operatora jest taki sam jak obiekt ciągu po prawej stronie.|
|[Operator <](../standard-library/string-operators.md#op_lt)|Sprawdza, czy z obiektem ciągu po lewej stronie operatora jest mniejsza niż z obiektem ciągu po prawej stronie.|
|[Operator < =](../standard-library/string-operators.md#op_lt_eq)|Testy, jeśli ciąg obiekt po lewej stronie operatora jest mniejsza niż lub równe z obiektem ciągu po prawej stronie.|
|[Operator <\<](../standard-library/string-operators.md#op_lt_lt)|Funkcja szablonu, która wstawia ciąg do strumienia wyjściowego.|
|[operator>](../standard-library/string-operators.md#op_gt)|Testy, jeśli obiekt ciągu po lewej stronie operatora jest większa niż z obiektem ciągu po prawej stronie.|
|[operator>=](../standard-library/string-operators.md#op_gt_eq)|Testy, jeśli obiekt ciągu po lewej stronie operatora jest większa niż lub równa z obiektem ciągu po prawej stronie.|
|[operator>>](../standard-library/string-operators.md#op_gt_gt)|Funkcja szablonu, który wyodrębnia ciąg ze strumienia wejściowego.|

### <a name="specialized-template-functions"></a>Specialized Template — Funkcje

|||
|-|-|
|[swap](../standard-library/string-functions.md#swap)|Zamienia tablic znaki z dwóch ciągów.|
|[stod —](../standard-library/string-functions.md#stod)|Konwertuje sekwencję znaków `double.`|
|[stof](../standard-library/string-functions.md#stof)|Konwertuje sekwencję znaków `float`.|
|[stoi](../standard-library/string-functions.md#stoi)|Konwertuje sekwencja znaków na liczbę całkowitą.|
|[stold](../standard-library/string-functions.md#stold)|Konwertuje sekwencję znaków `long double`.|
|[stoll](../standard-library/string-functions.md#stoll)|Konwertuje sekwencję znaków `long long`.|
|[stoul](../standard-library/string-functions.md#stoul)|Konwertuje sekwencję znaków `unsigned long`.|
|[stoull](../standard-library/string-functions.md#stoull)|Konwertuje sekwencję znaków `unsigned long long`.|
|[to_string](../standard-library/string-functions.md#to_string)|Konwertuje wartość na `string`.|
|[to_wstring](../standard-library/string-functions.md#to_wstring)|Konwertuje wartość na całej `string`.|

### <a name="functions"></a>Funkcje

|Funkcja|Opis|
|-|-|
|[getline szablonu](../standard-library/string-functions.md#getline)|Wyodrębnij ciągi ze strumienia wejściowego wiersz po wierszu.|

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[basic_string, klasa](../standard-library/basic-string-class.md)|Klasa szablonu, który opisuje obiekty który przechowywania sekwencji dowolnego znaku typu obiektów.|
|[char_traits, struktura](../standard-library/char-traits-struct.md)|Klasy szablonów opisujący atrybuty skojarzone ze znakiem typu CharType|

### <a name="specializations"></a>Specjalizacje

|||
|-|-|
|[char_traits\<char > — Struktura](../standard-library/char-traits-char-struct.md)|Struktury, która jest specjalizacją szablonu struktury `char_traits` \<CharType > do elementu typu `char`.|
|[char_traits<wchar_t>, struktura](../standard-library/char-traits-wchar-t-struct.md)|Struktury, która jest specjalizacją szablonu struktury `char_traits` \<CharType > do elementu typu `wchar_t`.|
|[char_traits<char16_t>, struktura](../standard-library/char-traits-char16-t-struct.md)|Struktury, która jest specjalizacją szablonu struktury `char_traits` \<CharType > do elementu typu `char16_t`.|
|[char_traits<char32_t>, struktura](../standard-library/char-traits-char32-t-struct.md)|Struktury, która jest specjalizacją szablonu struktury `char_traits` \<CharType > do elementu typu `char32_t`.|

## <a name="requirements"></a>Wymagania

- **Nagłówek:** \<ciąg >

- **Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
