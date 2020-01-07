---
title: Zakresy typu danych
ms.date: 05/07/2019
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
ms.openlocfilehash: 43eb5f34bc587e3ce86532c56d393da3e07c1b03
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301564"
---
# <a name="data-type-ranges"></a>Zakresy typu danych

Kompilatory C++ Microsoft 32-bit i 64-bitowe rozpoznaje typy w tabeli w dalszej części tego artykułu.

- `int` (`unsigned int`)

- `__int8` (`unsigned __int8`)

- `__int16` (`unsigned __int16`)

- `__int32` (`unsigned __int32`)

- `__int64` (`unsigned __int64`)

- `short` (`unsigned short`)

- `long` (`unsigned long`)

- `long` `long` (`unsigned long long`)

Jeśli nazwa zaczyna się od dwóch znaków podkreślenia (`__`), typem danych nie jest standard.

Zakresy, które są określone w poniższej tabeli, obejmują włącznie.

|Nazwa typu|Bajty|Inne nazwy|Zakres wartości|
|---------------|-----------|-----------------|---------------------|
|**int**|4|**opatrzon**|-2 147 483 648 do 2 147 483 647|
|**niepodpisany int**|4|**bajt**|od 0 do 4 294 967 295|
|**__int8**|1|**char**|-128 do 127|
|**__int8 bez znaku**|1|**znak bez znaku**|od 0 do 255|
|**__int16**|2|**krótka**, **krótka**, krótka liczba **całkowita**|-32 768 do 32 767|
|**__int16 bez znaku**|2|**unsigned Short**, **unsigned short int**|od 0 do 65 535|
|**__int32**|4|ze **znakiem**, liczba **całkowita ze znakiem**, **int**|-2 147 483 648 do 2 147 483 647|
|**__int32 bez znaku**|4|**unsigned**, **int bez znaku**|od 0 do 4 294 967 295|
|**__int64**|8|**Long**Long, **podpisał Long** Long|-zakresu od do 9 223 372 036 854 775 807|
|**__int64 bez znaku**|8|**bez znaku Long Long**|od 0 do 18446744073709551615 są|
|**bool**|1|brak|**Fałsz** lub **prawda**|
|**char**|1|brak|-128 do 127 domyślnie<br /><br /> od 0 do 255 w przypadku skompilowania przy użyciu [/j](../build/reference/j-default-char-type-is-unsigned.md)|
|**znak ze znakiem**|1|brak|-128 do 127|
|**znak bez znaku**|1|brak|od 0 do 255|
|**short**|2|**krótka int**, **podpisana krótka liczba całkowita**|-32 768 do 32 767|
|**bez znaku Short**|2|**unsigned short int**|od 0 do 65 535|
|**long**|4|**long int**, **nolonged int**|-2 147 483 648 do 2 147 483 647|
|**bez znaku**|4|**unsigned long int**|od 0 do 4 294 967 295|
|**Long Long**|8|Brak (ale równoważne **__int64**)|-zakresu od do 9 223 372 036 854 775 807|
|**bez znaku Long Long**|8|Brak (ale równoważne z **niepodpisanym __int64**)|od 0 do 18446744073709551615 są|
|**enum**|różni się|brak| |
|**float**|4|brak|3.4 e +/-38 (7 cyfr)|
|**double**|8|brak|1.7 e +/-308 (15 cyfr)|
|**Long Double**|taka sama jak **Double**|brak|Taka sama jak **Double**|
|**wchar_t**|2|**__wchar_t**|od 0 do 65 535|

W zależności od tego, jak jest używany, zmienna **__wchar_t** wyznacza typ znaku dwubajtowego lub typ znaku wieloznacznego. Użyj prefiksu `L` przed znakiem lub stałą ciągu, aby wyznaczyć stałą typu znaku dwubajtowego.

**podpisane** i **niepodpisane** są modyfikatorami, których można użyć z dowolnym typem całkowitym, z wyjątkiem **bool**. Należy zauważyć **, że znaki, znaki** **podpisane**i **znaki bez znaku** to trzy odrębne typy do celów takich mechanizmów jak Przeciążenie i szablony.

Typy **int** i **unsigned int** mają rozmiar czterech bajtów. Jednak kod przenośny nie powinien zależeć od rozmiaru **int** , ponieważ Standard języka pozwala na to, aby było to specyficzne dla implementacji.

Język CC++ /w programie Visual Studio obsługuje również typy liczb całkowitych. Aby uzyskać więcej informacji, zobacz [__int8, \__int16, \__int32, \_](../cpp/int8-int16-int32-int64.md) _Int64 i [liczby całkowite](../cpp/integer-limits.md).

Aby uzyskać więcej informacji na temat ograniczeń rozmiarów poszczególnych typów, zobacz [typy wbudowane](../cpp/fundamental-types-cpp.md).

Zakres wyliczeniowych typów różni się w zależności od kontekstu języka i określonych flag kompilatora. Aby uzyskać więcej informacji, zobacz [deklaracje](../c-language/c-enumeration-declarations.md) i [wyliczenia](../cpp/enumerations-cpp.md)języka C.

## <a name="see-also"></a>Zobacz także

[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[Typy wbudowane](../cpp/fundamental-types-cpp.md)