---
title: Zakresy typu danych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: aa0efd3fa89ad10809217a0e484d3776d3c0ea5b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46052156"
---
# <a name="data-type-ranges"></a>Zakresy typu danych

Kompilatory języka Visual C++ 32-bitowych i 64-bitowych rozpoznają typy w tabeli w dalszej części tego artykułu.

- `int` (`unsigned int`)

- `__int8` (`unsigned __int8`)

- `__int16` (`unsigned __int16`)

- `__int32` (`unsigned __int32`)

- `__int64` (`unsigned __int64`)

- `short` (`unsigned short`)

- `long` (`unsigned long`)

- `long` `long` (`unsigned long long`)

Jeśli nazwa zaczyna się od dwóch podkreśleń (`__`), typ danych jest niestandardowy.

Zakresy, które są określone w poniższej tabeli są włączne włączne.

|Nazwa typu|Bajty|Inne nazwy|Zakres wartości|
|---------------|-----------|-----------------|---------------------|
|**int**|4|**Podpisany**|-2 147 483 2 147 483 648 do 647|
|**unsigned int**|4|**Bez znaku**|4 294 967 0 Aby 295|
|**__int8**|1|**char**|-128 do 127 znaków.|
|**nieoznaczonyu__int8**|1|**unsigned char**|od 0 do 255|
|**__int16**|2|**krótki**, **krótka wartość całkowita**, **podpisany krótka wartość całkowita**|-32768 do 32767.|
|**__int16 bez znaku**|2|**typ unsigned short**, **niepodpisane krótka wartość całkowita**|0 do 65 535.|
|**__int32**|4|**podpisana**, **podpisany int**, **int**|-2 147 483 2 147 483 648 do 647|
|**__int32 bez znaku**|4|**niepodpisane**, **unsigned int**|4 294 967 0 Aby 295|
|**__int64**|8|**Long long**, **podpisany long long**|-9,223,372,036,854,775,808 do 9,223,372,036,854,775,807|
|**__int64 bez znaku**|8|**Nieoznaczony długi długi**|0 — 18,446,744,073,709,551,615|
|**bool**|1|brak|**FALSE** lub **true**|
|**char**|1|brak|-128 do 127 domyślnie<br /><br /> od 0 do 255 gdy kompilowany przy użyciu  [ /j.](../build/reference/j-default-char-type-is-unsigned.md)|
|**podpisany char**|1|brak|-128 do 127 znaków.|
|**unsigned char**|1|brak|od 0 do 255|
|**short**|2|**krótka wartość całkowita**, **podpisany krótka wartość całkowita**|-32768 do 32767.|
|**short bez znaku**|2|**niepodpisane krótka wartość całkowita**|0 do 65 535.|
|**long**|4|**long int**, **podpisany long int**|-2 147 483 2 147 483 648 do 647|
|**unsigned long**|4|**unsigned long int**|4 294 967 0 Aby 295|
|**długi długi**|8|Brak (ale równoważne **__int64**)|-9,223,372,036,854,775,808 do 9,223,372,036,854,775,807|
|**Nieoznaczony długi długi**|8|Brak (ale równoważne **unsigned __int64**)|0 — 18,446,744,073,709,551,615|
|**enum**|Różni się|brak| |
|**float**|4|brak|3.4e/38 (7 cyfr)|
|**double**|8|brak|308 (15 cyfr) 1, 7e|
|**Liczba typu double**|taki sam jak **double**|brak|taki sam jak **double**|
|**wchar_t**|2|**__wchar_t**|0 do 65 535.|

W zależności od sposobu ich wykorzystania, zmienna **__wchar_t** szerokie znaki typu lub typów znaków wielobajtowych. Użyj `L` prefiksu przed znakiem lub stałą ciągu, aby oznaczyć stałą typu znaku dwubajtowego.

**podpisana** i **niepodpisane** są modyfikatorami, które można używać z dowolnym typem integralnym oprócz **bool**. Należy pamiętać, że **char**, **podpisany char**, i **unsigned char** są trzema różnymi typami do celów mechanizmów takich jak przeciążenia i szablony.

**Int** i **unsigned int** typy mają rozmiar czterech bajtów. Jednak kod przenośny nie powinien być zależny od rozmiaru **int** ponieważ standard językowy pozwala, żeby było to specyficzne dla implementacji.

C/C++ w programie Visual Studio obsługuje również typy wielkości liczb całkowitych. Aby uzyskać więcej informacji, zobacz [__int8, \__int16, \__int32, \__int64](../cpp/int8-int16-int32-int64.md) i [limity liczb całkowitych](../cpp/integer-limits.md).

Aby uzyskać więcej informacji na temat ograniczeń rozmiarów każdego typu, zobacz [podstawowych typów](../cpp/fundamental-types-cpp.md).

Zakres wymienionych typów różni się w zależności od kontekstu językowego i określonych flag kompilatora. Aby uzyskać więcej informacji, zobacz [deklaracje modułów Wyliczających języka C](../c-language/c-enumeration-declarations.md) i [wyliczenia](../cpp/enumerations-cpp.md).

## <a name="see-also"></a>Zobacz także

[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[Typy podstawowe](../cpp/fundamental-types-cpp.md)