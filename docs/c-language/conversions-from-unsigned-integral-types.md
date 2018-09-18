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
ms.openlocfilehash: 38ef2c16c92322ae54dcc6dd7d577268daf74831
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46058279"
---
# <a name="conversions-from-unsigned-integral-types"></a>Konwersje z niepodpisanych typów całkowitych

Liczba całkowita bez znaku jest konwertowany krótszy całkowitą bez znaku lub podpisany przez obcinanie bardziej znaczących bitów lub już bez znaku lub podpisany liczby całkowitej przez zero, rozszerzenie (zobacz [konwersje z niepodpisanych typów całkowitych](#_clang_table_4..3) tabeli).

Gdy wartością typu całkowitego jest obniżony do liczby całkowitej ze znakiem o rozmiarze mniejszym lub liczbą całkowitą bez znaku jest konwertowany na liczbę całkowitą ze znakiem odpowiednie, wartość jest bez zmian, jeśli mogą być reprezentowane w nowego typu. Jednak wartość reprezentuje zmiany, jeśli ustawiono bit znaku, jak w poniższym przykładzie.

```C
int j;
unsigned short k = 65533;

j = k;
printf_s( "%hd\n", j );   // Prints -3
```

Jeśli nie może być przedstawiona, wynik zależy od implementacji. Zobacz [konwersje rzutowania typów](../c-language/type-cast-conversions.md) informacji na temat obsługi kompilator Microsoft C: zwężanie liczb całkowitych. Te same zachowanie wyniki z konwersji liczby całkowitej lub Rzutowanie liczb całkowitych.

Wartości bez znaku są konwertowane w sposób, który zachowuje ich wartości i nie jest stałego bezpośrednio w C. Jedynym wyjątkiem jest konwersja **unsigned long** do **float**, która co najwyżej traci mniej znaczące bity. W przeciwnym razie wartość jest zachowywana, znakiem lub bez znaku. Wartość typu Liczba całkowita jest konwertowana do zmiennoprzecinkowych, gdy wartość jest poza zakresem stałego, wynik jest niezdefiniowany. (Zobacz [magazyn typów podstawowych](../c-language/storage-of-basic-types.md) uzyskać informacji na temat zakresu dla typów całkowitych i zmiennoprzecinkowych.)

W poniższej tabeli przedstawiono konwersje z niepodpisanych typów całkowitych.

## <a name="conversions-from-unsigned-integral-types"></a>Konwersje z niepodpisanych typów całkowitych

|Z|Zadanie|Metoda|
|----------|--------|------------|
|**unsigned char**|**char**|Zachowaj wzorzec bitowy; bit wyższego rzędu staje się bitu znaku|
|**unsigned char**|**short**|Rozszerzanie zero|
|**unsigned char**|**long**|Rozszerzanie zero|
|**unsigned char**|**short bez znaku**|Rozszerzanie zero|
|**unsigned char**|**unsigned long**|Rozszerzanie zero|
|**unsigned char**|**float**|Konwertuj na **długie**; Konwertuj **długie** do **float**|
|**unsigned char**|**double**|Konwertuj na **długie**; Konwertuj **długie** do **double**|
|**unsigned char**|**Liczba typu double**|Konwertuj na **długie**; Konwertuj **długie** do **double**|
|**short bez znaku**|**char**|Zachowaj mniej znaczący bajt|
|**short bez znaku**|**short**|Zachowaj wzorzec bitowy; bit wyższego rzędu staje się bitu znaku|
|**short bez znaku**|**long**|Rozszerzanie zero|
|**short bez znaku**|**unsigned char**|Zachowaj mniej znaczący bajt|
|**short bez znaku**|**unsigned long**|Rozszerzanie zero|
|**short bez znaku**|**float**|Konwertuj na **długie**; Konwertuj **długie** do **float**|
|**short bez znaku**|**double**|Konwertuj na **długie**; Konwertuj **długie** do **double**|
|**short bez znaku**|**Liczba typu double**|Konwertuj na **długie**; Konwertuj **długie** do **double**|
|**unsigned long**|**char**|Zachowaj mniej znaczący bajt|
|**unsigned long**|**short**|Zachowaj niskiego rzędu programu word|
|**unsigned long**|**long**|Zachowaj wzorzec bitowy; bit wyższego rzędu staje się bitu znaku|
|**unsigned long**|**unsigned char**|Zachowaj mniej znaczący bajt|
|**unsigned long**|**short bez znaku**|Zachowaj niskiego rzędu programu word|
|**unsigned long**|**float**|Konwertuj na **długie**; Konwertuj **długie** do **float**|
|**unsigned long**|**double**|Konwertuj bezpośrednio do **double**|
|**unsigned long**|**Liczba typu double**|Konwertuj na **długie**; Konwertuj **długie** do **double**|

**Microsoft Specific**

Dla kompilatora Microsoft C **unsigned int** typu jest odpowiednikiem **unsigned long** typu. Konwersja **unsigned int** wartość przechodzi w ten sam sposób jak konwersja **unsigned long**. Konwersje z **unsigned long** wartości **float** nie są prawidłowe, jeśli konwertowana wartość jest większa niż maksymalna wynik dodatni podpisany **długie** wartość.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Konwersje przypisań](../c-language/assignment-conversions.md)
