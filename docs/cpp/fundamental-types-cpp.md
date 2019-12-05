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
- long keyword [C++]
- storing types [C++]
- data types [C++], void
ms.assetid: 58b0106a-0406-4b74-a430-7cbd315c0f89
ms.openlocfilehash: daa2ad2680a9d7d0239a70ed37ec1d90a3d96d97
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857544"
---
# <a name="fundamental-types--c"></a>Typy podstawowe (C++)

Podstawowe typy w C++ programie są podzielone na trzy kategorie: Całka, liczba zmiennoprzecinkowa i typ void. Typy zintegrowane są zdolne do obsługi liczb całkowitych. Typy zmiennoprzecinkowe mogą określać wartości, które mogą mieć części ułamkowe.

Typ [void](../cpp/void-cpp.md) opisuje pusty zestaw wartości. Nie można określić żadnej zmiennej typu **void** — jest ona używana głównie do deklarowania funkcji, które nie zwracają żadnych wartości lub deklarują ogólne wskaźniki do niewpisanych lub arbitralnie wpisanych danych. Każde wyrażenie może być jawnie konwertowane lub rzutowane na typ **void**. Jednakże takie wyrażenia są ograniczone do następujących zastosowań:

- Instrukcja wyrażenia. (Zobacz [wyrażenia](../cpp/expressions-cpp.md), aby uzyskać więcej informacji.)

- Lewy operator operatora przecinka. (Zobacz [operator przecinkiem](../cpp/comma-operator.md) , aby uzyskać więcej informacji).

- Drugi lub trzeci operand operatora warunkowego (`? :`). (Aby uzyskać więcej informacji, zobacz [wyrażenia z operatorem warunkowym](../cpp/conditional-operator-q.md) ).

W poniższej tabeli opisano ograniczenia dla rozmiarów typu. Te ograniczenia są niezależne od implementacji Microsoft.

### <a name="fundamental-types-of-the-c-language"></a>Podstawowe typy w języku C++

|Kategoria|Typ|Spis treści|
|--------------|----------|--------------|
|Typ całkowity|**char**|Typ **char** jest typem całkowitym, który zwykle zawiera elementy członkowskie podstawowego zestawu znaków wykonywania — domyślnie jest to ASCII w firmie Microsoft C++.<br /><br /> Kompilator traktuje zmienne typu **char** **, ze znakiem**znaku i **unsigned char** jako mające różne typy. C++ Zmienne typu **char** są podwyższane do wartości **int** , tak jakby były typu ze znakiem **podpisane** domyślnie, chyba że zostanie użyta opcja/j kompilacja. W tym przypadku są one traktowane jako **znaki typu unsigned** i są podwyższane do **int** bez rozszerzenia znaku.|
||**bool**|Typ **bool** jest typem całkowitym, który może mieć jedną z dwóch wartości **true** lub **false**. Jego rozmiar jest nieokreślony.|
||**short**|Typ **short int** (lub po prostu **Short**) jest typem całkowitym, który jest większy niż lub równy rozmiarowi typu **char**, i krótszy niż lub równy rozmiarowi typu **int**.<br /><br /> Obiekty typu **Short** mogą być deklarowane jako **krótkie** lub **niepodpisane**. **Krótka ze znakiem** jest synonimem dla **krótkiej**.|
||**int**|Typ **int** jest typem całkowitym, który jest większy niż lub równy rozmiarowi typu **short int**i krótszy niż lub równy rozmiarowi typu **Long**.<br /><br /> Obiekty typu **int** mogą być deklarowane jako liczba całkowita ze **znakiem int** lub **unsigned int**. **Cyfra ze znakiem int** jest synonimem dla **int**.|
||**__int8**, **__int16**, **__int32** **__int64**|Liczba całkowita o rozmiarze `__int n`, gdzie `n` jest rozmiar w bitach zmiennej całkowitej. **__int8**, **__int16**, **__int32** i **__int64** są słowami kluczowymi specyficznymi dla firmy Microsoft. Nie wszystkie typy są dostępne we wszystkich architekturach. ( **__int128** nie jest obsługiwana).|
||**long**|Typ **Long** (lub **long int**) jest typem całkowitym, który jest większy niż lub równy rozmiarowi typu **int**. (W systemie Windows **Long** ma taki sam rozmiar jak **int**).<br /><br /> Obiekty typu **Long** mogą być deklarowane jako **długie** lub **niepodpisane**. **Znak Long** jest synonimem dla **Long**.|
||**Long Long**|Większe niż **znak bez znaku**.<br /><br /> Obiekty typu **Long Long** mogą być deklarowane jako **podpisane o długim** długim lub **bez znaku**long long. **podpisana long long** jest synonimem dla **długiej**długości.|
||**wchar_t**, **__wchar_t**|Zmienna typu **wchar_t** wyznacza typ dwubajtowy lub znak wieloznaczny. Domyślnie **wchar_t** jest typem natywnym, ale można użyć [/Zc: wchar_t-](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) , aby **wchar_t** typedef dla **niepodpisanego Short**. Typ **__wchar_t** jest synonimem specyficznym dla firmy Microsoft dla natywnego typu **wchar_t** .<br /><br /> Użyj prefiksu L przed znakiem lub literałem ciągu, aby wyznaczyć typ szerokich znaków.|
|Liczba zmiennoprzecinkowa|**float**|Typ **float** jest najmniejszym typem zmiennoprzecinkowym.|
||**double**|Typ **Double** to typ zmiennoprzecinkowy, który jest większy niż lub równy typowi **zmiennoprzecinkowej**, ale krótszy niż lub równy rozmiarowi typu **Long Double**.<br /><br /> Specyficzne dla firmy Microsoft: reprezentacja typu **Long Double** i **Double** jest taka sama. Jednak **długie podwójne** i **podwójne** są oddzielnymi typami.|
||**Long Double**|Typ **Long Double** jest typem zmiennoprzecinkowym, który jest większy niż lub równy typ **Double**.|

**Microsoft Specific**

Poniższa lista zawiera ilość miejsca wymaganego dla podstawowych typów w Microsoft C++.

### <a name="sizes-of-fundamental-types"></a>Rozmiary typów podstawowych

|Typ|Rozmiar|
|----------|----------|
|**bool**, **char**, **znak bez znaku**, znak **podpisany**, **__int8**|1 bajt|
|**__int16**, **krótkie**, **niepodpisane, krótkie**, **wchar_t**, **__wchar_t**|2 bajty|
|**float**, **__int32**, **int**, **unsigned int**, **Long**i **unsigned long**|4 bajty|
|**Double**, **__int64**, **Long Double**, **Long Long**|8 bajtów|

**ZAKOŃCZENIE określonych przez firmę Microsoft**

Zobacz [zakresy typów danych](../cpp/data-type-ranges.md) , aby uzyskać podsumowanie zakresu wartości poszczególnych typów.

Aby uzyskać więcej informacji na temat konwersji typów, zobacz [Konwersje standardowe](../cpp/standard-conversions.md).

## <a name="see-also"></a>Zobacz także

[Zakresy typu danych](../cpp/data-type-ranges.md)