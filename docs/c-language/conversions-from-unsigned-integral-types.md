---
title: Konwersje z niepodpisanych typów całkowitych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/29/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- integers, converting
- type casts, involving integers
- data type conversion [C++], signed and unsigned integers
- type conversion [C++], signed and unsigned integers
- integral conversions, from unsigned
ms.assetid: 60fb7e10-bff9-4a13-8a48-e19f25a36a02
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6a8a77e898feb6676487c557b8e96d54dc793ace
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32391525"
---
# <a name="conversions-from-unsigned-integral-types"></a>Konwersje z niepodpisanych typów całkowitych

Całkowitą bez znaku jest konwertowana na krótszą całkowitą bez znaku lub podpisany tworzy bardziej znaczących bitów lub już niepodpisany lub podpisany liczby całkowitej przez zero, rozszerzanie (zobacz [konwersje z niepodpisanych typów całkowitych](#_clang_table_4..3) tabeli).

Podczas obniżania poziomu wartość z typu całkowitego na liczbę całkowitą ze znakiem o rozmiarze mniejszym lub liczbą całkowitą bez znaku jest konwertowana na jego odpowiedniej liczby całkowitej ze znakiem, wartość jest bez zmian, jeśli może być reprezentowany w nowego typu. Jednak wartość reprezentuje zmiany, jeśli ustawiono bit logowania, jak w poniższym przykładzie.

```C
int j;
unsigned short k = 65533;

j = k;
printf_s( "%hd\n", j );   // Prints -3
```

Jeśli nie można przedstawić, wynikiem jest zdefiniowane w implementacji. Zobacz [konwersje rzutowania typów](../c-language/type-cast-conversions.md) informacji na temat obsługi kompilator Microsoft C zwężanie liczb całkowitych. Zachowanie wyniki z konwersja liczby całkowitej lub typ rzutowanie liczb całkowitych.

Wartości bez znaku są konwertowane w taki sposób, który zachowuje ich wartości, a nie można przedstawić bezpośrednio w C. Jedynym wyjątkiem jest konwersja **unsigned long** do **float**, które co najwyżej traci mniej znaczące bity. W przeciwnym razie wartość są zachowywane, podpisem lub bez. Jeśli wartość typu całkowitego jest konwertowana na liczby zmiennoprzecinkowe, a wartość jest poza zakresem reprezentacja, wynik jest niezdefiniowany. (Zobacz [magazyn typów podstawowych](../c-language/storage-of-basic-types.md) uzyskać informacje na temat zakresu dla typów całkowitych i zmiennoprzecinkowych.)

Poniższa tabela zawiera podsumowanie konwersje z niepodpisanych typów całkowitych.

## <a name="conversions-from-unsigned-integral-types"></a>Konwersje z niepodpisanych typów całkowitych

|Z|Do|Metoda|
|----------|--------|------------|
|**char bez znaku**|**char**|Zachowaj wzorca bitowego; bit znaczących staje się bitu znaku|
|**char bez znaku**|**short**|Rozszerzanie zero|
|**char bez znaku**|**long**|Rozszerzanie zero|
|**char bez znaku**|**short bez znaku**|Rozszerzanie zero|
|**char bez znaku**|**unsigned long**|Rozszerzanie zero|
|**char bez znaku**|**float**|Konwertuj na **długi**; przekonwertować **długi** do **liczb zmiennoprzecinkowych**|
|**char bez znaku**|**double**|Konwertuj na **długi**; przekonwertować **długi** do **podwójne**|
|**char bez znaku**|**Liczba typu double**|Konwertuj na **długi**; przekonwertować **długi** do **podwójne**|
|**short bez znaku**|**char**|Zachowaj mniej znaczącego bajtu|
|**short bez znaku**|**short**|Zachowaj wzorca bitowego; bit znaczących staje się bitu znaku|
|**short bez znaku**|**long**|Rozszerzanie zero|
|**short bez znaku**|**char bez znaku**|Zachowaj mniej znaczącego bajtu|
|**short bez znaku**|**unsigned long**|Rozszerzanie zero|
|**short bez znaku**|**float**|Konwertuj na **długi**; przekonwertować **długi** do **liczb zmiennoprzecinkowych**|
|**short bez znaku**|**double**|Konwertuj na **długi**; przekonwertować **długi** do **podwójne**|
|**short bez znaku**|**Liczba typu double**|Konwertuj na **długi**; przekonwertować **długi** do **podwójne**|
|**unsigned long**|**char**|Zachowaj mniej znaczącego bajtu|
|**unsigned long**|**short**|Zachowaj znaczącymi bitami programu word|
|**unsigned long**|**long**|Zachowaj wzorca bitowego; bit znaczących staje się bitu znaku|
|**unsigned long**|**char bez znaku**|Zachowaj mniej znaczącego bajtu|
|**unsigned long**|**short bez znaku**|Zachowaj znaczącymi bitami programu word|
|**unsigned long**|**float**|Konwertuj na **długi**; przekonwertować **długi** do **liczb zmiennoprzecinkowych**|
|**unsigned long**|**double**|Konwertuj bezpośrednio do **podwójne**|
|**unsigned long**|**Liczba typu double**|Konwertuj na **długi**; przekonwertować **długi** do **podwójne**|

**Microsoft Specific**

Dla kompilatora Microsoft C **unsigned int** typu jest odpowiednikiem **unsigned long** typu. Konwersja **unsigned int** wartość będzie kontynuowana w taki sam sposób jak konwersja **unsigned long**. Konwersje z **unsigned long** wartości do **float** nie są dokładne, jeśli wartość konwertowanej jest większa niż maksymalna dodatnich podpisany **długi** wartość.

**KOŃCOWY określonych firmy Microsoft**

## <a name="see-also"></a>Zobacz także

[Konwersje przypisań](../c-language/assignment-conversions.md)  
