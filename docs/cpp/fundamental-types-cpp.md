---
title: Typy podstawowe (C++)
ms.date: 11/04/2016
f1_keywords:
- __int128_cpp
- __wchar_t_cpp
- char_cpp
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
- long keyword [C++], C++ data types
- storing types [C++]
- data types [C++], void
ms.assetid: 58b0106a-0406-4b74-a430-7cbd315c0f89
ms.openlocfilehash: f4af392ed559349b0e49fd26f3ecb4406a70b74b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62153804"
---
# <a name="fundamental-types--c"></a>Typy podstawowe (C++)

Podstawowe typy w języku C++ są podzielone na trzy kategorie: całkowitych, zmiennoprzecinkowych oraz typ void. Typy zintegrowane są zdolne do obsługi liczb całkowitych. Typy zmiennoprzecinkowe są wartości, które mogą mieć części ułamkowych.

[Void](../cpp/void-cpp.md) typ opisuje pusty zestaw wartości. Żadnej zmiennej typu **void** można określić — jest używany głównie do deklarowania funkcji, które nie zwracają żadnych wartości lub deklarowania ogólnych wskaźników do niewpisanych lub arbitralnie wpisanych danych. Dowolne wyrażenie może być jawnie konwertowany lub rzutowane na typ **void**. Jednakże takie wyrażenia są ograniczone do następujących zastosowań:

- Instrukcja wyrażenia. (Zobacz [wyrażeń](../cpp/expressions-cpp.md), aby uzyskać więcej informacji.)

- Lewy operand operatora "przecinek". (Zobacz [operatora przecinka](../cpp/comma-operator.md) Aby uzyskać więcej informacji.)

- Drugi lub trzeci operand operatora warunkowego (`? :`). (Zobacz [wyrażenia z Operatoemr warunkowy](../cpp/conditional-operator-q.md) Aby uzyskać więcej informacji.)

W poniższej tabeli opisano ograniczenia dla rozmiarów typu. Te ograniczenia są niezależne od implementacji Microsoft.

### <a name="fundamental-types-of-the-c-language"></a>Podstawowe typy języka C++

|Kategoria|Typ|Spis treści|
|--------------|----------|--------------|
|całkowite|**char**|Typ **char** to integralny typ, który zazwyczaj zawiera elementy członkowskie zestawu znaków wykonania podstawowego — domyślnie jest to ASCII w Microsoft C++.<br /><br /> Kompilator C++ traktuje zmienne typu **char**, **podpisany char**, i **unsigned char** jako posiadające różne typy. Zmienne typu **char** są promowane do **int** tak, jakby są typu **podpisany char** domyślnie, chyba że używana jest opcja kompilacji/j. W takim przypadku będą one traktowane jako typ **unsigned char** i były promowane do **int** bez rozszerzenia znaku.|
||**bool**|Typ **bool** to integralny typ, który może mieć jedną z dwóch wartości **true** lub **false**. Jego rozmiar jest nieokreślony.|
||**short**|Typ **krótka wartość całkowita** (lub po prostu **krótki**) to integralny typ, który jest większy niż lub równy rozmiarowi typu **char**oraz krótszy niż lub równy rozmiarowi typu **int**.<br /><br /> Obiekty typu **krótki** mogą być deklarowane jako **short ze znakiem** lub **typ unsigned short**. **Short ze znakiem** jest synonimem dla **krótki**.|
||**int**|Typ **int** to integralny typ, który jest większy niż lub równy rozmiarowi typu **krótka wartość całkowita**oraz krótszy niż lub równy rozmiarowi typu **długie**.<br /><br /> Obiekty typu **int** mogą być deklarowane jako **podpisany int** lub **unsigned int**. **Podpisana int** jest synonimem dla **int**.|
||**__int8**, **__int16**, **__int32**, **__int64**|Całkowite o określonym rozmiarze `__int n`, gdzie `n` rozmiar w bitach zmiennej liczby całkowitej. **__int8**, **__int16**, **__int32** i **__int64** słowa kluczowe specyficzne dla firmy Microsoft. Nie wszystkie typy są dostępne we wszystkich architekturach. (**__int128** nie jest obsługiwany.)|
||**long**|Typ **długie** (lub **long int**) to integralny typ, który jest większy niż lub równy rozmiarowi typu **int**.<br /><br /> Obiekty typu **długie** mogą być deklarowane jako **podpisany długo** lub **unsigned long**. **Podpisana długo** jest synonimem dla **długie**.|
||**długi długi**|Większe niż typ unsigned **długie**.<br /><br /> Obiekty typu **long long** mogą być deklarowane jako **podpisany long long** lub **unsigned long long**. **long long podpisany** jest synonimem dla **long long**.|
||**wchar_t**, **__wchar_t**|Zmienna typu **wchar_t** Określa typ szerokich znaków lub wielobajtowych znaków. Domyślnie **wchar_t** jest typem natywnym, ale można użyć [/Zc:wchar_t-](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) się **wchar_t** element typedef dla **typ unsigned short**. **__Wchar_t** typ jest synonimem specyficzne dla firmy Microsoft dla natywnych **wchar_t** typu.<br /><br /> Użyj przedrostka L przed znakiem lub literał ciągu do wyznaczania typu znaku dwubajtowego.|
|Liczba zmiennoprzecinkowa|**float**|Typ **float** jest wartość zmiennoprzecinkowa najmniejszą typu punktu.|
||**double**|Typ **double** jest typ zmiennoprzecinkowy punktu, który jest większy niż lub równe wpisz **float**, ale krótszy lub równy rozmiarowi typu **typu long double**.<br /><br /> Specyficzne dla firmy Microsoft: Reprezentacja **typu long double** i **double** jest taka sama. Jednak **typu long double** i **double** są oddzielnymi typami.|
||**Liczba typu double**|Typ **typu long double** zmiennoprzecinkowy typ punktu, który jest większy niż lub równy wpisz **double**.|

**Microsoft Specific**

W poniższej tabeli wymieniono ilość miejsca wymaganego dla podstawowych typów w Microsoft C++.

### <a name="sizes-of-fundamental-types"></a>Rozmiary typów podstawowych

|Typ|Rozmiar|
|----------|----------|
|**wartość logiczna**, **char**, **unsigned char**, **podpisany char**, **__int8**|1 bajt|
|**__int16**, **krótki**, **typ unsigned short**, **wchar_t**, **__wchar_t**|2 bajty|
|**float**, **__int32**, **int**, **unsigned int**, **długie**, **unsigned long**|4 bajty|
|**podwójne**, **__int64**, **typu long double**, **długi długi**|8 bajtów|

**END specyficzny dla Microsoft**

Zobacz [zakresy typu danych](../cpp/data-type-ranges.md) dla podsumowania zakresu wartości każdego typu.

Aby uzyskać więcej informacji dotyczących typu konwersji, zobacz [konwersje standardowe](../cpp/standard-conversions.md).

## <a name="see-also"></a>Zobacz także

[Zakresy typu danych](../cpp/data-type-ranges.md)