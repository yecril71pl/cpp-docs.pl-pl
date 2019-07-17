---
title: '&lt;string&gt;'
ms.date: 11/04/2016
f1_keywords:
- string/std::<string>
- <string>
helpviewer_keywords:
- string header
ms.assetid: a2fb9d00-d7ae-4170-bfea-2dc337aa37cf
ms.openlocfilehash: 3f3874b1d439326c97b015007ad8d5ede06341f7
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245391"
---
# <a name="ltstringgt"></a>&lt;string&gt;

Definiuje klasę szablonu pojemnika `basic_string` i różnych szablonów pomocniczych.

Aby uzyskać więcej informacji na temat `basic_string`, zobacz [basic_string — klasa](../standard-library/basic-string-class.md)

## <a name="syntax"></a>Składnia

```cpp
#include <string>
```

## <a name="remarks"></a>Uwagi

Język C++ i standardowej biblioteki języka C++ obsługuje dwa typy parametrów:

- Tablice znaków zakończony znakiem null, często określane jako ciągi C.

- Obiekty klasy szablonu, typu `basic_string`, które obsługują wszystkie **char**— argumentów szablonu, takie jak.

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[string](../standard-library/string-typedefs.md#string)|Typ, który opisuje specjalizacji szablonu klasy `basic_string` elementami typu **char** jako `string`.|
|[wstring](../standard-library/string-typedefs.md#wstring)|Typ, który opisuje specjalizacji szablonu klasy `basic_string` elementami typu **wchar_t** jako `wstring`.|
|[u16string](../standard-library/string-typedefs.md#u16string)|Typ, który opisuje specjalizacji szablonu klasy `basic_string` oparte na elementach typu `char16_t`.|
|[u32string](../standard-library/string-typedefs.md#u32string)|Typ, który opisuje specjalizacji szablonu klasy `basic_string` oparte na elementach typu `char32_t`.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator +](../standard-library/string-operators.md#op_add)|Łączy dwa obiekty ciągu.|
|[operator!=](../standard-library/string-operators.md#op_neq)|Sprawdza, czy obiekt ciągu po lewej stronie operatora nie jest taki sam jak obiekt ciągu z prawej strony.|
|[operator==](../standard-library/string-operators.md#op_eq_eq)|Sprawdza, czy obiekt ciągu po lewej stronie operatora jest równy obiektowi ciągu z prawej strony.|
|[Operator <](../standard-library/string-operators.md#op_lt)|Sprawdza, czy z obiektem ciągu po lewej stronie operatora jest mniejszy niż obiekt ciągu z prawej strony.|
|[Operator < =](../standard-library/string-operators.md#op_lt_eq)|Sprawdza, czy ciąg obiektu po lewej stronie operatora jest mniejszy niż lub równy obiektowi ciągu po prawej stronie.|
|[Operator <\<](../standard-library/string-operators.md#op_lt_lt)|Funkcja szablonu, który wstawia ciąg do strumienia wyjściowego.|
|[operator>](../standard-library/string-operators.md#op_gt)|Sprawdza, czy obiekt ciągu po lewej stronie operatora jest większy niż z obiektem ciągu z prawej strony.|
|[operator>=](../standard-library/string-operators.md#op_gt_eq)|Sprawdza, czy obiekt ciągu po lewej stronie operatora jest większy lub równy obiektowi ciągu z prawej strony.|
|[operator>>](../standard-library/string-operators.md#op_gt_gt)|Funkcja szablonu, która wyodrębnia ciąg ze strumienia wejściowego.|

### <a name="specialized-template-functions"></a>Specialized Template — Funkcje

|||
|-|-|
|[Skrót]()||
|[swap](../standard-library/string-functions.md#swap)|Zamienia tablic z dwóch ciągów znaków.|
|[stod —](../standard-library/string-functions.md#stod)|Konwertuje sekwencję znaków do **double**.|
|[stof](../standard-library/string-functions.md#stof)|Konwertuje sekwencję znaków do **float**.|
|[stoi](../standard-library/string-functions.md#stoi)|Konwertuje sekwencję znaków na liczbę całkowitą.|
|[stold](../standard-library/string-functions.md#stold)|Konwertuje sekwencję znaków do **typu long double**.|
|[stoll](../standard-library/string-functions.md#stoll)|Konwertuje sekwencję znaków do **long long**.|
|[stoul](../standard-library/string-functions.md#stoul)|Konwertuje sekwencję znaków do **unsigned long**.|
|[stoull](../standard-library/string-functions.md#stoull)|Konwertuje sekwencję znaków do **unsigned long long**.|
|[to_string](../standard-library/string-functions.md#to_string)|Konwertuje wartość `string`.|
|[to_wstring](../standard-library/string-functions.md#to_wstring)|Konwertuje wartość na całej `string`.|

### <a name="functions"></a>Funkcje

|Funkcja|Opis|
|-|-|
|[getline — szablon](../standard-library/string-functions.md#getline)|Wyodrębnij ciągi znaków ze strumienia wejściowego wiersz po wierszu.|

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[basic_string, klasa](../standard-library/basic-string-class.md)|Klasa szablonu, który opisuje obiekty, można przechowywać sekwencji dowolnego znaku przypominającej obiektów.|
|[char_traits, struktura](../standard-library/char-traits-struct.md)|Klasa szablonu, który opisuje atrybuty skojarzone z znaku typu CharType|

### <a name="specializations"></a>Specjalizacje

|||
|-|-|
|[char_traits\<char > — Struktura](../standard-library/char-traits-char-struct.md)|Struktura, która jest specjalizacją szablonu struktury `char_traits` \<CharType > do elementu typu `char`.|
|[char_traits<wchar_t>, struktura](../standard-library/char-traits-wchar-t-struct.md)|Struktura, która jest specjalizacją szablonu struktury `char_traits` \<CharType > do elementu typu `wchar_t`.|
|[char_traits<char16_t>, struktura](../standard-library/char-traits-char16-t-struct.md)|Struktura, która jest specjalizacją szablonu struktury `char_traits` \<CharType > do elementu typu `char16_t`.|
|[char_traits<char32_t>, struktura](../standard-library/char-traits-char32-t-struct.md)|Struktura, która jest specjalizacją szablonu struktury `char_traits` \<CharType > do elementu typu `char32_t`.|

## <a name="requirements"></a>Wymagania

- **Nagłówek:** \<ciąg >

- **Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
