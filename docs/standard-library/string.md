---
title: '&lt;string&gt;'
ms.date: 11/04/2016
f1_keywords:
- string/std::<string>
- <string>
helpviewer_keywords:
- string header
ms.assetid: a2fb9d00-d7ae-4170-bfea-2dc337aa37cf
ms.openlocfilehash: fda00cd5a8f8768688c8e10f25a0d1f2370a256f
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459187"
---
# <a name="ltstringgt"></a>&lt;string&gt;

Definiuje klasę `basic_string` szablonu kontenera i różne szablony pomocnicze.

Aby uzyskać więcej informacji `basic_string`na temat, zobacz [basic_string class](../standard-library/basic-string-class.md)

## <a name="syntax"></a>Składnia

```cpp
#include <string>
```

## <a name="remarks"></a>Uwagi

C++ Język i C++ standardowa biblioteka obsługują dwa typy ciągów:

- Tablice znaków zakończonych znakiem null często określane jako ciągi języka C.

- Obiekty klasy szablonu, `basic_string`które obsługują wszystkie argumenty szablonu podobne do **znaków**.

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[string](../standard-library/string-typedefs.md#string)|Typ, który opisuje specjalizację klasy `basic_string` szablonu z elementami typu  `string`char jako.|
|[wstring](../standard-library/string-typedefs.md#wstring)|Typ, który opisuje specjalizację klasy `basic_string` szablonu z elementami typu  `wstring`wchar_t jako.|
|[u16string](../standard-library/string-typedefs.md#u16string)|Typ, który opisuje specjalizację klasy `basic_string` szablonu na podstawie elementów typu. `char16_t`|
|[u32string](../standard-library/string-typedefs.md#u32string)|Typ, który opisuje specjalizację klasy `basic_string` szablonu na podstawie elementów typu. `char32_t`|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator +](../standard-library/string-operators.md#op_add)|Łączy dwa obiekty String.|
|[operator!=](../standard-library/string-operators.md#op_neq)|Testuje, czy obiekt String po lewej stronie operatora nie jest równy obiektowi ciągu po prawej stronie.|
|[operator==](../standard-library/string-operators.md#op_eq_eq)|Testuje, czy obiekt String po lewej stronie operatora jest równy obiektowi ciągu po prawej stronie.|
|[< operatora](../standard-library/string-operators.md#op_lt)|Testuje, czy obiekt String po lewej stronie operatora jest mniejszy niż obiekt ciągu po prawej stronie.|
|[< operatora =](../standard-library/string-operators.md#op_lt_eq)|Testuje, czy obiekt String po lewej stronie operatora jest mniejszy niż lub równy obiektowi ciągu po prawej stronie.|
|[< operatora\<](../standard-library/string-operators.md#op_lt_lt)|Funkcja szablonu, która wstawia ciąg do strumienia wyjściowego.|
|[operator>](../standard-library/string-operators.md#op_gt)|Testuje, czy obiekt String po lewej stronie operatora jest większy niż obiekt ciągu po prawej stronie.|
|[operator>=](../standard-library/string-operators.md#op_gt_eq)|Testuje, czy obiekt String po lewej stronie operatora jest większy niż lub równy obiektowi ciągu po prawej stronie.|
|[operator>>](../standard-library/string-operators.md#op_gt_gt)|Funkcja szablonu, która wyodrębnia ciąg ze strumienia wejściowego.|

### <a name="specialized-template-functions"></a>Specialized Template — Funkcje

|||
|-|-|
|[skrótu]()||
|[swap](../standard-library/string-functions.md#swap)|Wymienia tablice znaków dwóch ciągów.|
|[stod](../standard-library/string-functions.md#stod)|Konwertuje sekwencję znaków na wartość typu **Double**.|
|[stof](../standard-library/string-functions.md#stof)|Konwertuje sekwencję znaków na wartość **zmiennoprzecinkową**.|
|[stoi](../standard-library/string-functions.md#stoi)|Konwertuje sekwencję znaków na liczbę całkowitą.|
|[stold](../standard-library/string-functions.md#stold)|Konwertuje sekwencję znaków na wartość typu **Long Double**.|
|[stoll](../standard-library/string-functions.md#stoll)|Konwertuje sekwencję znaków na **długą długą**.|
|[stoul](../standard-library/string-functions.md#stoul)|Konwertuje sekwencję znaków na wartość **unsigned long**.|
|[stoull](../standard-library/string-functions.md#stoull)|Konwertuje sekwencję znaków na unsigned long **Long**.|
|[to_string](../standard-library/string-functions.md#to_string)|Konwertuje wartość na `string`.|
|[to_wstring](../standard-library/string-functions.md#to_wstring)|Konwertuje wartość na szeroką `string`.|

### <a name="functions"></a>Funkcje

|Funkcja|Opis|
|-|-|
|[getline — szablon](../standard-library/string-functions.md#getline)|Wyodrębnianie ciągów z wiersza strumienia wejściowego w wierszu.|

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[basic_string, klasa](../standard-library/basic-string-class.md)|Klasa szablonu opisująca obiekty, które mogą przechowywać sekwencję dowolnych obiektów podobnej do znaku.|
|[char_traits, struktura](../standard-library/char-traits-struct.md)|Klasa szablonu opisująca atrybuty skojarzone ze znakiem typu CharType|

### <a name="specializations"></a>Specjalizacje

|||
|-|-|
|[char_traits\<char > struct](../standard-library/char-traits-char-struct.md)|Struktura, która jest specjalizacją struktury `char_traits` \<szablonu CharType > do elementu typu `char`.|
|[char_traits<wchar_t>, struktura](../standard-library/char-traits-wchar-t-struct.md)|Struktura, która jest specjalizacją struktury `char_traits` \<szablonu CharType > do elementu typu `wchar_t`.|
|[char_traits<char16_t>, struktura](../standard-library/char-traits-char16-t-struct.md)|Struktura, która jest specjalizacją struktury `char_traits` \<szablonu CharType > do elementu typu `char16_t`.|
|[char_traits<char32_t>, struktura](../standard-library/char-traits-char32-t-struct.md)|Struktura, która jest specjalizacją struktury `char_traits` \<szablonu CharType > do elementu typu `char32_t`.|

## <a name="requirements"></a>Wymagania

- **Nagłówek:** \<ciąg >

- **Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
