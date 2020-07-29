---
title: Zakresy typu danych
ms.date: 05/28/2020
helpviewer_keywords:
- float keyword [C++]
- char keyword [C++]
- unsigned long
- __wchar_t keyword [C++]
- unsigned short int [C++]
- enum keyword [C++]
- unsigned char keyword [C++]
- integer data type [C++], data type ranges
- int data type
- data types [C++], ranges
- unsigned int [C++]
- short data type
- short int data
- signed types [C++], data type ranges
- long long keyword [C++]
- long double keyword [C++]
- double data type [C++], data type ranges
- signed short int [C++]
- unsigned short
- sized integer types
- signed int [C++]
- signed long int [C++]
- signed char keyword [C++]
- wchar_t keyword [C++]
- long keyword [C++]
- ranges [C++]
- unsigned types [C++], data type ranges
- floating-point numbers [C++]
- data type ranges
- ranges [C++], data types
- long int keyword [C++]
- unsigned long int [C++]
ms.assetid: 3691ceca-05fb-4b82-b1ae-5c4618cda91a
ms.openlocfilehash: f7658d0c0a61180193de268414e214595198e8fa
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228976"
---
# <a name="data-type-ranges"></a>Zakresy typu danych

Kompilatory Microsoft C++ 32-bit i 64-bitowe rozpoznają typy w tabeli w dalszej części tego artykułu.

- **`int`** (**`unsigned int`**)

- **`__int8`** (**`unsigned __int8`**)

- **`__int16`** (**`unsigned __int16`**)

- **`__int32`** (**`unsigned __int32`**)

- **`__int64`** (**`unsigned __int64`**)

- **`short`** (**`unsigned short`**)

- **`long`** (**`unsigned long`**)

- **`long long`** (**`unsigned long long`**)

Jeśli nazwa zaczyna się od dwóch znaków podkreślenia ( `__` ), typem danych nie jest standard.

Zakresy, które są określone w poniższej tabeli, obejmują włącznie.

|Nazwa typu|Bajty|Inne nazwy|Zakres wartości|
|---------------|-----------|-----------------|---------------------|
|**`int`**|4|**`signed`**|-2 147 483 648 do 2 147 483 647|
|**`unsigned int`**|4|**`unsigned`**|od 0 do 4 294 967 295|
|**`__int8`**|1|**`char`**|-128 do 127|
|**`unsigned __int8`**|1|**`unsigned char`**|od 0 do 255|
|**`__int16`**|2|**`short`**, **`short int`**, **`signed short int`**|-32 768 do 32 767|
|**`unsigned __int16`**|2|**`unsigned short`**, **`unsigned short int`**|od 0 do 65 535|
|**`__int32`**|4|**`signed`**, **`signed int`**, **`int`**|-2 147 483 648 do 2 147 483 647|
|**`unsigned __int32`**|4|**`unsigned`**, **`unsigned int`**|od 0 do 4 294 967 295|
|**`__int64`**|8|**`long long`**, **`signed long long`**|-zakresu od do 9 223 372 036 854 775 807|
|**`unsigned __int64`**|8|**`unsigned long long`**|od 0 do 18446744073709551615 są|
|**`bool`**|1|brak|**`false`** oraz**`true`**|
|**`char`**|1|brak|-128 do 127 domyślnie<br /><br /> od 0 do 255 w przypadku skompilowania przy użyciu[`/J`](../build/reference/j-default-char-type-is-unsigned.md)|
|**`signed char`**|1|brak|-128 do 127|
|**`unsigned char`**|1|brak|od 0 do 255|
|**`short`**|2|**`short int`**, **`signed short int`**|-32 768 do 32 767|
|**`unsigned short`**|2|**`unsigned short int`**|od 0 do 65 535|
|**`long`**|4|**`long int`**, **`signed long int`**|-2 147 483 648 do 2 147 483 647|
|**`unsigned long`**|4|**`unsigned long int`**|od 0 do 4 294 967 295|
|**`long long`**|8|Brak (ale równoważne **`__int64`** )|-zakresu od do 9 223 372 036 854 775 807|
|**`unsigned long long`**|8|Brak (ale równoważne **`unsigned __int64`** )|od 0 do 18446744073709551615 są|
|**`enum`**|różni się|brak| |
|**`float`**|4|brak|3.4 e +/-38 (7 cyfr)|
|**`double`**|8|brak|1.7 e +/-308 (15 cyfr)|
|**`long double`**|tak samo jak**`double`**|brak|Tak samo jak**`double`**|
|**`wchar_t`**|2|**`__wchar_t`**|od 0 do 65 535|

W zależności od tego, jak jest używany, zmienna wyznacza typ dwubajtowy **`__wchar_t`** lub typ znaku wieloznacznego. Użyj `L` prefiksu przed znakiem lub stałą ciągu, aby oznaczyć stałą typu znaku dwubajtowego.

**`signed`** i **`unsigned`** są modyfikatorami, których można używać z dowolnym typem całkowitym z wyjątkiem **`bool`** . Należy pamiętać, że, **`char`** **`signed char`** i **`unsigned char`** są trzema różnymi typami do celów mechanizmów, takich jak Przeciążenie i szablony.

**`int`** Typy i **`unsigned int`** mają rozmiar czterech bajtów. Jednak kod przenośny nie powinien zależeć od rozmiaru, **`int`** ponieważ Standard języka pozwala na to, aby było to specyficzne dla implementacji.

Język C/C++ w programie Visual Studio obsługuje również typy liczb całkowitych. Aby uzyskać więcej informacji, zobacz [`__int8, __int16, __int32, __int64`](../cpp/int8-int16-int32-int64.md) i [limity liczb całkowitych](../cpp/integer-limits.md).

Aby uzyskać więcej informacji na temat ograniczeń rozmiarów poszczególnych typów, zobacz [typy wbudowane](../cpp/fundamental-types-cpp.md).

Zakres wyliczeniowych typów różni się w zależności od kontekstu języka i określonych flag kompilatora. Aby uzyskać więcej informacji, zobacz [deklaracje](../c-language/c-enumeration-declarations.md) i [wyliczenia](../cpp/enumerations-cpp.md)języka C.

## <a name="see-also"></a>Zobacz także

[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[Typy wbudowane](../cpp/fundamental-types-cpp.md)
