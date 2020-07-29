---
title: Typy wbudowane (C++)
ms.date: 07/22/2020
f1_keywords:
- __int128_cpp
- __wchar_t_cpp
- char_cpp
- char8_t_cpp
- char16_t_cpp
- char32_t_cpp
- double_cpp
- float_cpp
- int_cpp
- long_cpp
- long_double_cpp
- short_cpp
- signed_cpp
- unsigned_cpp
- unsigned_int_cpp
- wchar_t_cpp
helpviewer_keywords:
- specifiers [C++], type
- float keyword [C++]
- char keyword [C++]
- __wchar_t keyword [C++]
- signed types [C++], summary of data types
- Integer data type [C++], C++ data types
- arithmetic operations [C++], types
- int data type
- unsigned types [C++], summary of data types
- short data type [C++]
- double data type [C++], summary of types
- long long keyword [C++]
- long double keyword [C++]
- unsigned types [C++]
- signed types [C++]
- void keyword [C++]
- storage [C++], basic type
- integral types, C++
- wchar_t keyword [C++]
- floating-point numbers [C++], C++ data types
- long keyword [C++]
- type specifiers [C++]
- integral types
- long keyword [C++]
- storing types [C++]
- data types [C++], void
ms.assetid: 58b0106a-0406-4b74-a430-7cbd315c0f89
ms.openlocfilehash: 73486dd4d81fc91007f078ec5c509bcb963d2706
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232277"
---
# <a name="built-in-types-c"></a>Typy wbudowane (C++)

Typy wbudowane (zwane również *typami podstawowymi*) są określane przez Standard języka C++ i są wbudowane w kompilator. Wbudowane typy nie są zdefiniowane w żadnym pliku nagłówkowym. Typy wbudowane są podzielone na trzy główne kategorie: *Całka*, *zmiennoprzecinkowa*i *void*. Typy całkowite reprezentują liczby całkowite. Typy zmiennoprzecinkowe mogą określać wartości, które mogą mieć części ułamkowe. Większość typów wbudowanych jest traktowana jako odrębne typy przez kompilator. Jednak niektóre typy są *synonimami*lub traktowane jako równoważne typy przez kompilator.

## <a name="void-type"></a>Typ void

[`void`](void-cpp.md)Typ opisuje pusty zestaw wartości. Nie można określić żadnej zmiennej typu **`void`** . **`void`** Typ jest używany głównie do deklarowania funkcji, które nie zwracają wartości ani do deklarowania wskaźników ogólnych do niewpisanych lub arbitralnie wpisanych danych. Każde wyrażenie może być jawnie konwertowane lub rzutowane na typ **`void`** . Jednakże takie wyrażenia są ograniczone do następujących celów:

- Instrukcja wyrażenia. (Aby uzyskać więcej informacji, zobacz [Expressions](expressions-cpp.md)).

- Lewy operand operatora przecinka. (Aby uzyskać więcej informacji, zobacz [operator przecinka](comma-operator.md)).

- Drugi lub trzeci operand operatora warunkowego ( `? :` ). (Aby uzyskać więcej informacji, zobacz [wyrażenia z operatorem warunkowym](conditional-operator-q.md)).

## <a name="stdnullptr_t"></a>std:: nullptr_t

Słowo kluczowe **`nullptr`** jest stałą wskaźnika o wartości null typu `std::nullptr_t` , który jest konwertowany na dowolny nieprzetworzony typ wskaźnika. Aby uzyskać więcej informacji, zobacz [`nullptr`](nullptr.md).

## <a name="boolean-type"></a>Typ wartości logicznej

[`bool`](bool-cpp.md)Typ może mieć wartości [`true`](../cpp/true-cpp.md) i [`false`](../cpp/false-cpp.md) . Rozmiar **`bool`** typu jest specyficzny dla implementacji. Zobacz [rozmiary typów wbudowanych](#sizes-of-built-in-types) dla szczegółów implementacji specyficznych dla firmy Microsoft.

## <a name="character-types"></a>Typy znaków

**`char`** Typ jest typem reprezentacji znaku, który efektywnie koduje elementy członkowskie podstawowego zestawu znaków wykonania. Kompilator języka C++ traktuje zmienne typu **`char`** , **`signed char`** i **`unsigned char`** jako mające różne typy.

**Specyficzne dla firmy Microsoft**: zmienne typu **`char`** są podwyższane **`int`** jako Jeśli **`signed char`** Domyślnie, chyba że [`/J`](../build/reference/j-default-char-type-is-unsigned.md) jest używana opcja kompilacji. W tym przypadku są one traktowane jako typ **`unsigned char`** i są promowane do **`int`** bez rozszerzenia znaku.

Zmienna typu **`wchar_t`** jest typu szerokiego lub wielobajtowego. Użyj **`L`** prefiksu przed znakiem lub literałem ciągu, aby określić typ szerokich znaków.

**Specyficzne dla firmy Microsoft**: Domyślnie **`wchar_t`** jest typem natywnym, ale można użyć, [`/Zc:wchar_t-`](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) Aby utworzyć **`wchar_t`** element typedef dla **`unsigned short`** . **`__wchar_t`** Typ jest synonimem specyficznym dla firmy Microsoft dla typu natywnego **`wchar_t`** .

**`char8_t`** Typ jest używany dla reprezentacji znaków UTF-8. Ma taką samą reprezentację jak **`unsigned char`** , ale jest traktowana jako odrębny typ przez kompilator. **`char8_t`** Typ jest nowy w języku c++ 20. **Specyficzne dla firmy Microsoft**: użycie **`char8_t`** wymaga [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) opcji kompilatora.

**`char16_t`** Typ jest używany dla reprezentacji znaków UTF-16. Musi być wystarczająco duży, aby reprezentować dowolną jednostkę kodu w formacie UTF-16. Jest on traktowany jako typ odrębny przez kompilator.

**`char32_t`** Typ jest używany dla reprezentacji znaków UTF-32. Musi być wystarczająco duży, aby reprezentować dowolną jednostkę kodu w formacie UTF-32. Jest on traktowany jako typ odrębny przez kompilator.

## <a name="floating-point-types"></a>Typy zmiennoprzecinkowe

Typy zmiennoprzecinkowe wykorzystują reprezentację IEEE-754, aby zapewnić przybliżenie wartości ułamkowych w szerokim zakresie wielkości. Poniższa tabela zawiera listę typów zmiennoprzecinkowych w języku C++ i ograniczenia porównawcze dla rozmiaru typu zmiennoprzecinkowego. Ograniczenia te są wymagane przez standard C++ i są niezależne od implementacji firmy Microsoft. Rozmiar bezwzględny wbudowanych typów zmiennoprzecinkowych nie jest określany w standardzie.

| Typ | Zawartość |
|--|--|
| **`float`** | Typ **`float`** to najmniejszy typ zmiennoprzecinkowy w języku C++. |
| **`double`** | Typ **`double`** jest typem zmiennoprzecinkowym, który jest większy niż lub równy typ **`float`** , ale krótszy niż lub równy rozmiarowi typu **`long double`** . |
| **`long double`** | Typ **`long double`** wskazuje typ zmiennoprzecinkowy, który jest większy niż lub równy typowi **`double`** . |

**Specyficzne dla firmy Microsoft**: reprezentacja **`long double`** i **`double`** jest identyczna. Jednak **`long double`** i **`double`** są traktowane jako różne typy przez kompilator. Kompilator języka Microsoft C++ używa reprezentacji zmiennoprzecinkowych 4-i 8-bajtowych IEEE-754. Aby uzyskać więcej informacji, zobacz [reprezentacja zmiennoprzecinkowa IEEE](../build/ieee-floating-point-representation.md).

## <a name="integer-types"></a>Typy całkowite

**`int`** Typ jest domyślnym Basic typu Integer. Może reprezentować wszystkie liczby całkowite w zakresie określonym dla implementacji.

Reprezentacja liczby całkowitej ze *znakiem* jest taka, która może zawierać zarówno wartości dodatnie, jak i ujemne. Jest ona używana domyślnie lub kiedy **`signed`** słowo kluczowe modyfikatora jest obecne. **`unsigned`** Słowo kluczowe modyfikatora określa *niepodpisany* reprezentację, która może zawierać tylko wartości nieujemne.

Modyfikator rozmiaru Określa szerokość w bitach używanej reprezentacji liczb całkowitych. Język obsługuje **`short`** **`long`** modyfikatory, i **`long long`** . **`short`** Typ musi mieć co najmniej 16 bitów. **`long`** Typ musi mieć co najmniej 32 bitów. **`long long`** Typ musi mieć co najmniej 64 bitów. Standard określa relację rozmiaru między typami całkowitymi:

`1 == sizeof(char) <= sizeof(short) <= sizeof(int) <= sizeof(long) <= sizeof(long long)`

Implementacja musi zachować minimalne wymagania dotyczące rozmiaru i relację rozmiaru dla każdego typu. Jednak rzeczywiste rozmiary mogą być różne w zależności od implementacji. Zobacz [rozmiary typów wbudowanych](#sizes-of-built-in-types) dla szczegółów implementacji specyficznych dla firmy Microsoft.

**`int`** Słowo kluczowe może zostać pominięte **`signed`** , jeśli **`unsigned`** określono modyfikatory, lub rozmiaru. Modyfikatory i **`int`** typy, jeśli istnieją, mogą pojawiać się w dowolnej kolejności. Na przykład, **`short unsigned`** i **`unsigned int short`** odwołują się do tego samego typu.

### <a name="integer-type-synonyms"></a>Synonimy typu Integer

Następujące grupy typów są uznawane za synonimy przez kompilator:

- **`short`**, **`short int`**, **`signed short`**, **`signed short int`**

- **`unsigned short`**, **`unsigned short int`**

- **`int`**, **`signed`**, **`signed int`**

- **`unsigned`**, **`unsigned int`**

- **`long`**, **`long int`**, **`signed long`**, **`signed long int`**

- **`unsigned long`**, **`unsigned long int`**

- **`long long`**, **`long long int`**, **`signed long long`**, **`signed long long int`**

- **`unsigned long long`**, **`unsigned long long int`**

Typy liczb całkowitych **specyficznych dla firmy Microsoft** obejmują **`__int8`** określone **`__int16`** typy,, **`__int32`** i **`__int64`** . Te typy mogą używać **`signed`** **`unsigned`** modyfikatorów i. **`__int8`** Typ danych jest synonimem typu **`char`** , **`__int16`** jest synonimem typu **`short`** , **`__int32`** jest synonimem typu **`int`** i **`__int64`** jest synonimem typu **`long long`** .

## <a name="sizes-of-built-in-types"></a>Rozmiary typów wbudowanych

Większość typów wbudowanych ma rozmiary zdefiniowane przez implementację. W poniższej tabeli przedstawiono ilość pamięci wymaganej dla wbudowanych typów w programie Microsoft C++. W szczególności program **`long`** ma 4 bajty nawet w 64-bitowych systemach operacyjnych.

| Typ | Rozmiar |
|--|--|
| **`bool`**, **`char`**, **`char8_t`**, **`unsigned char`**, **`signed char`**, **`__int8`** | 1 bajt |
| **`char16_t`**, **`__int16`**, **`short`**, **`unsigned short`**, **`wchar_t`**, **`__wchar_t`** | 2 bajty |
| **`char32_t`**, **`float`**, **`__int32`**, **`int`**, **`unsigned int`**, **`long`**, **`unsigned long`** | 4 bajty |
| **`double`**, **`__int64`**, **`long double`**, **`long long`**, **`unsigned long long`** | 8 bajtów |

Zobacz [zakresy typów danych](data-type-ranges.md) , aby uzyskać podsumowanie zakresu wartości poszczególnych typów.

Aby uzyskać więcej informacji na temat konwersji typów, zobacz [Konwersje standardowe](standard-conversions.md).

## <a name="see-also"></a>Zobacz także

[Zakresy typu danych](data-type-ranges.md)
