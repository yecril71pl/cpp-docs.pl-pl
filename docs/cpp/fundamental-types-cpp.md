---
title: Typy wbudowane (C++)
ms.date: 12/11/2019
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
ms.openlocfilehash: 14d96453785a55f625b5467458f9cf79e6739acf
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188619"
---
# <a name="built-in-types-c"></a>Typy wbudowane (C++)

Typy wbudowane (zwane również *typami podstawowymi*) są określane przez standard C++ języka i są wbudowane w kompilator. Wbudowane typy nie są zdefiniowane w żadnym pliku nagłówkowym. Wbudowane typy są podzielone na trzy kategorie: całek, zmiennoprzecinkowe i void. Typy całkowite mogą obsługiwać liczbę całkowitą. Typy zmiennoprzecinkowe mogą określać wartości, które mogą mieć części ułamkowe.

Typ [void](void-cpp.md) opisuje pusty zestaw wartości. Nie można określić żadnej zmiennej typu **void** — jest ona używana głównie do deklarowania funkcji, które nie zwracają żadnych wartości lub deklarują ogólne wskaźniki do niewpisanych lub arbitralnie wpisanych danych. Każde wyrażenie może być jawnie konwertowane lub rzutowane na typ **void**. Jednakże takie wyrażenia są ograniczone do następujących celów:

- Instrukcja wyrażenia. (Aby uzyskać więcej informacji, zobacz [Expressions](expressions-cpp.md)).

- Lewy operand operatora przecinka. (Aby uzyskać więcej informacji, zobacz [operator przecinka](comma-operator.md)).

- Drugi lub trzeci operand operatora warunkowego (`? :`). (Aby uzyskać więcej informacji, zobacz [wyrażenia z operatorem warunkowym](conditional-operator-q.md)).

W poniższej tabeli opisano ograniczenia dotyczące rozmiarów typów w zależności od siebie. Ograniczenia te są wymagane przez C++ Standard i są niezależne od implementacji firmy Microsoft. Rozmiar bezwzględny niektórych typów wbudowanych nie jest określony w standardzie.

### <a name="built-in-type-size-restrictions"></a>Ograniczenia rozmiaru typu wbudowanego

|Kategoria|Typ|Zawartość|
|--------------|----------|--------------|
|Integraln|**char**|Typ **char** jest typem całkowitym, który zwykle zawiera elementy członkowskie podstawowego zestawu znaków wykonywania — domyślnie jest to ASCII w firmie Microsoft C++.<br /><br /> Kompilator traktuje zmienne typu **char** **, ze znakiem**znaku i **unsigned char** jako mające różne typy. C++ Zmienne typu **char** są podwyższane do wartości **int** , tak jakby były typu ze znakiem **podpisane** domyślnie, chyba że zostanie użyta opcja/j kompilacja. W tym przypadku są one traktowane jako znaki typu **unsigned** i są promowane jako **int** bez rozszerzenia.|
||**bool**|Typ **bool** jest typem całkowitym, który może mieć jedną z dwóch wartości **true** lub **false**. Nie określono jego rozmiaru.|
||**short**|Typ **short int** (lub po prostu **Short**) jest typem całkowitym, który jest większy niż lub równy rozmiarowi typu **char**, i krótszy niż lub równy rozmiarowi typu **int**.<br /><br /> Obiekty typu **Short** mogą być deklarowane jako **krótkie** lub **niepodpisane**. **Krótka ze znakiem** jest synonimem dla **krótkiej**.|
||**int**|Typ **int** jest typem całkowitym, który jest większy niż lub równy rozmiarowi typu **short int**i krótszy niż lub równy rozmiarowi typu **Long**.<br /><br /> Obiekty typu **int** mogą być deklarowane jako liczba całkowita ze **znakiem int** lub **unsigned int**. **Cyfra ze znakiem int** jest synonimem dla **int**.|
||**__int8**, **__int16**, **__int32** **__int64**|Liczba całkowita o rozmiarze `__int n`, gdzie `n` jest rozmiar w bitach zmiennej całkowitej. **__int8**, **__int16**, **__int32** i **__int64** są słowami kluczowymi specyficznymi dla firmy Microsoft. Nie wszystkie typy są dostępne we wszystkich architekturach. ( **__int128** nie jest obsługiwana).|
||**long**|Typ **Long** (lub **long int**) jest typem całkowitym, który jest większy niż lub równy rozmiarowi typu **int**. (W systemie Windows **Long** ma taki sam rozmiar jak **int**).<br /><br /> Obiekty typu **Long** mogą być deklarowane jako **długie** lub **niepodpisane**. **Znak Long** jest synonimem dla **Long**.|
||**Long Long**|Większe niż **znak bez znaku**.<br /><br /> Obiekty typu **Long Long** mogą być deklarowane jako **podpisane o długim** długim lub **bez znaku**long long. **podpisana long long** jest synonimem dla **długiej**długości.|
||**wchar_t**, **__wchar_t**|Zmienna typu **wchar_t** wyznacza typ dwubajtowy lub znak wieloznaczny. Domyślnie **wchar_t** jest typem natywnym, ale można użyć [/Zc: wchar_t-](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) , aby **wchar_t** typedef dla **niepodpisanego Short**. Typ **__wchar_t** jest synonimem specyficznym dla firmy Microsoft dla natywnego typu **wchar_t** .<br /><br /> Użyj prefiksu L przed znakiem lub literałem ciągu, aby wyznaczyć typ szerokich znaków.|
|Liczba zmiennoprzecinkowa|**float**|Typ **float** jest najmniejszym typem zmiennoprzecinkowym.|
||**double**|Typ **Double** to typ zmiennoprzecinkowy, który jest większy niż lub równy typowi **zmiennoprzecinkowej**, ale krótszy niż lub równy rozmiarowi typu **Long Double**.<br /><br /> Specyficzne dla firmy Microsoft: reprezentacja typu **Long Double** i **Double** jest taka sama. Jednak **długie podwójne** i **podwójne** są oddzielnymi typami.|
||**Long Double**|Typ **Long Double** jest typem zmiennoprzecinkowym, który jest większy niż lub równy typ **Double**.|

**Specyficzne dla firmy Microsoft**

W poniższej tabeli przedstawiono ilość pamięci wymaganej dla wbudowanych typów w firmie Microsoft C++. W szczególności należy zauważyć, że **Long** to 4 bajty nawet w 64-bitowych systemach operacyjnych.

### <a name="sizes-of-built-in-types"></a>Rozmiary typów wbudowanych

|Typ|Rozmiar|
|----------|----------|
|**bool**, **char**, **znak bez znaku**, znak **podpisany**, **__int8**|1 bajt|
|**__int16**, **krótkie**, **niepodpisane, krótkie**, **wchar_t**, **__wchar_t**|2 bajty|
|**float**, **__int32**, **int**, **unsigned int**, **Long**i **unsigned long**|4 bajty|
|**Double**, **__int64**, **Long Double**, **Long Long**|8 bajtów|

**ZAKOŃCZENIE określonych przez firmę Microsoft**

Zobacz [zakresy typów danych](data-type-ranges.md) , aby uzyskać podsumowanie zakresu wartości poszczególnych typów.

Aby uzyskać więcej informacji na temat konwersji typów, zobacz [Konwersje standardowe](standard-conversions.md).

## <a name="see-also"></a>Zobacz też

[Zakresy typu danych](data-type-ranges.md)
