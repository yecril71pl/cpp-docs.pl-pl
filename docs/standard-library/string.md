---
title: '&lt;string&gt;'
ms.date: 11/04/2016
f1_keywords:
- string/std::<string>
- <string>
helpviewer_keywords:
- string header
ms.assetid: a2fb9d00-d7ae-4170-bfea-2dc337aa37cf
ms.openlocfilehash: 68b1865fd9c45c3782917edba273083dac086548
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212127"
---
# <a name="ltstringgt"></a>&lt;string&gt;

Definiuje szablon klasy kontenera `basic_string` i różne szablony pomocnicze.

Aby uzyskać więcej informacji na temat `basic_string` , zobacz [basic_string Class](../standard-library/basic-string-class.md)

## <a name="syntax"></a>Składnia

```cpp
#include <string>
```

## <a name="remarks"></a>Uwagi

Język C++ i Standardowa biblioteka C++ obsługują dwa typy ciągów:

- Tablice znaków zakończonych znakiem null często określane jako ciągi języka C.

- obiekty szablonu klasy, typu `basic_string` , które obsługują wszystkie **`char`** podobne argumenty szablonu.

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[ciąg](../standard-library/string-typedefs.md#string)|Typ, który opisuje specjalizację szablonu klasy `basic_string` z elementami typu **`char`** jako `string` .|
|[wstring](../standard-library/string-typedefs.md#wstring)|Typ, który opisuje specjalizację szablonu klasy `basic_string` z elementami typu **`wchar_t`** jako `wstring` .|
|[u16string](../standard-library/string-typedefs.md#u16string)|Typ, który opisuje specjalizację szablonu klasy `basic_string` na podstawie elementów typu **`char16_t`** .|
|[u32string](../standard-library/string-typedefs.md#u32string)|Typ, który opisuje specjalizację szablonu klasy `basic_string` na podstawie elementów typu **`char32_t`** .|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator +](../standard-library/string-operators.md#op_add)|Łączy dwa obiekty String.|
|[operator! =](../standard-library/string-operators.md#op_neq)|Testuje, czy obiekt String po lewej stronie operatora nie jest równy obiektowi ciągu po prawej stronie.|
|[operator = =](../standard-library/string-operators.md#op_eq_eq)|Testuje, czy obiekt String po lewej stronie operatora jest równy obiektowi ciągu po prawej stronie.|
|[<operatora](../standard-library/string-operators.md#op_lt)|Testuje, czy obiekt String po lewej stronie operatora jest mniejszy niż obiekt ciągu po prawej stronie.|
|[<operatora =](../standard-library/string-operators.md#op_lt_eq)|Testuje, czy obiekt String po lewej stronie operatora jest mniejszy niż lub równy obiektowi ciągu po prawej stronie.|
|[<operatora\<](../standard-library/string-operators.md#op_lt_lt)|Funkcja szablonu, która wstawia ciąg do strumienia wyjściowego.|
|[>operatora](../standard-library/string-operators.md#op_gt)|Testuje, czy obiekt String po lewej stronie operatora jest większy niż obiekt ciągu po prawej stronie.|
|[>operatora =](../standard-library/string-operators.md#op_gt_eq)|Testuje, czy obiekt String po lewej stronie operatora jest większy niż lub równy obiektowi ciągu po prawej stronie.|
|[>>operatora](../standard-library/string-operators.md#op_gt_gt)|Funkcja szablonu, która wyodrębnia ciąg ze strumienia wejściowego.|

### <a name="specialized-template-functions"></a>Specialized Template — Funkcje

|||
|-|-|
|hash|Tworzy skrót ciągu.|
|[wymiany](../standard-library/string-functions.md#swap)|Wymienia tablice znaków dwóch ciągów.|
|[stod](../standard-library/string-functions.md#stod)|Konwertuje sekwencję znaków na **`double`** .|
|[stof](../standard-library/string-functions.md#stof)|Konwertuje sekwencję znaków na **`float`** .|
|[stoi](../standard-library/string-functions.md#stoi)|Konwertuje sekwencję znaków na liczbę całkowitą.|
|[stold](../standard-library/string-functions.md#stold)|Konwertuje sekwencję znaków na **`long double`** .|
|[stoll](../standard-library/string-functions.md#stoll)|Konwertuje sekwencję znaków na **`long long`** .|
|[stoul](../standard-library/string-functions.md#stoul)|Konwertuje sekwencję znaków na **`unsigned long`** .|
|[stoull](../standard-library/string-functions.md#stoull)|Konwertuje sekwencję znaków na **`unsigned long long`** .|
|[to_string](../standard-library/string-functions.md#to_string)|Konwertuje wartość na `string` .|
|[to_wstring](../standard-library/string-functions.md#to_wstring)|Konwertuje wartość na szeroką `string` .|

### <a name="functions"></a>Funkcje

|Funkcja|Opis|
|-|-|
|[getline — szablon](../standard-library/string-functions.md#getline)|Wyodrębnianie ciągów z wiersza strumienia wejściowego w wierszu.|

### <a name="classes"></a>Klasy

|Klasa|Opis|
|-|-|
|[Klasa basic_string](../standard-library/basic-string-class.md)|Szablon klasy opisujący obiekty, które mogą przechowywać sekwencję dowolnych obiektów podobnej do znaku.|
|[Struktura char_traits](../standard-library/char-traits-struct.md)|Szablon klasy, który opisuje atrybuty skojarzone ze znakiem typu CharType|

### <a name="specializations"></a>Specjalizacje

|||
|-|-|
|[\<char>struktura char_traits](../standard-library/char-traits-char-struct.md)|Struktura, która jest specjalizacją struktury szablonu `char_traits` \<CharType> do elementu typu **`char`** .|
|[char_traits<wchar_t>, struktura](../standard-library/char-traits-wchar-t-struct.md)|Struktura, która jest specjalizacją struktury szablonu `char_traits` \<CharType> do elementu typu **`wchar_t`** .|
|[char_traits<char16_t>, struktura](../standard-library/char-traits-char16-t-struct.md)|Struktura, która jest specjalizacją struktury szablonu `char_traits` \<CharType> do elementu typu **`char16_t`** .|
|[char_traits<char32_t>, struktura](../standard-library/char-traits-char32-t-struct.md)|Struktura, która jest specjalizacją struktury szablonu `char_traits` \<CharType> do elementu typu **`char32_t`** .|

## <a name="requirements"></a>Wymagania

- **Nagłówek:**\<string>

- **Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz też

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
