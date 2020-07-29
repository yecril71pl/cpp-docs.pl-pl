---
title: Ósemkowe i szesnastkowe specyfikacje znaków
ms.date: 11/04/2016
helpviewer_keywords:
- octal characters
- hexadecimal characters
ms.assetid: 9264f3ec-46b8-41a5-b21a-8f7ed0a11871
ms.openlocfilehash: bcd6eb84503b80b1e38be5d134e7506a0f490891
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229587"
---
# <a name="octal-and-hexadecimal-character-specifications"></a>Ósemkowe i szesnastkowe specyfikacje znaków

Sekwencja **\\** <em>OOO</em> oznacza, że można określić dowolny znak w zestawie znaków ASCII jako trzy-cyfrowy kod znaku ósemkowego. Liczbowa wartość ósemkowej liczby całkowitej określa wartość wymaganego znaku lub znak dwubajtowy.

Podobnie sekwencja **\x**<em>HHH</em> umożliwia określenie dowolnego znaku ASCII jako kodu znaku szesnastkowego. Na przykład, można nadać znak backspace ASCII jako normalną sekwencję języka C (**\b**) lub kod jako **\ 010** (ósemkową) lub **\x008** (szesnastkowo).

Można użyć tylko cyfr od 0 do 7 w ósemkowej sekwencji ucieczki. Ósemkowe sekwencje ucieczki nigdy nie mogą być dłuższe niż trzy cyfry i są zakończone pierwszym znakiem, który nie jest cyfrą ósemkową. Chociaż nie trzeba używać wszystkich trzech cyfr, należy użyć co najmniej jednej. Na przykład reprezentacja ósemkowa to **\ 10** dla znaku backspace ASCII i **\ 101** dla litery a, jak określono w wykresie ASCII.

Podobnie, należy użyć co najmniej jednej cyfry do szesnastkowej sekwencji ucieczki, ale można pominąć drugą i trzecią cyfrę. W związku z tym można określić szesnastkową sekwencję ucieczki dla znaku backspace jako **\x8**, **\x08**lub **\x008**.

Wartość ósemkowej lub szesnastkowej sekwencji ucieczki musi znajdować się w przedziale wartości dla typu **`unsigned char`** stała znaku i wpisać **`wchar_t`** dla stałej o szerokim znaku. Zobacz [znaki wielobajtowe i szerokie,](../c-language/multibyte-and-wide-characters.md) Aby uzyskać informacje o stałych znakach.

W odróżnieniu od ósemkowych stałych wyjścia, nie ma limitu dotyczącego liczby cyfr szesnastkowych w sekwencji wyjścia. Szesnastkowa sekwencja ucieczki kończy się przy pierwszym znaku, który nie jest cyfrą szesnastkową. Ponieważ cyfry szesnastkowe zawierają litery **od a** do **f**, należy zachować ostrożność, aby upewnić się, że sekwencja ucieczki kończy się na zamierzonej cyfrze. Aby uniknąć nieporozumień, można umieścić definicje znaku ósemkowego lub szesnastkowego w definicji makra:

```
#define Bell '\x07'
```

W przypadku wartości szesnastkowych, można podzielić ciąg znaków w celu wyraźnego pokazania poprawnej wartości:

```
"\xabc"    /* one character  */
"\xab" "c" /* two characters */
```

## <a name="see-also"></a>Zobacz także

[Stałe znakowe języka C](../c-language/c-character-constants.md)
