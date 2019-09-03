---
title: function — Wartość dyrektywy pragma
ms.date: 08/29/2019
f1_keywords:
- function_CPP
- vc-pragma.function
helpviewer_keywords:
- function pragma
- pragmas, function
ms.assetid: cbd1bd60-fabf-4b5a-9c3d-2d9f4b871365
ms.openlocfilehash: f99f3c878789a6c47fdb0d48e0a8690d65fa8062
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220140"
---
# <a name="function-pragma"></a>function — Wartość dyrektywy pragma

Instruuje kompilator, aby generował wywołania do funkcji określonych na liście argumentów pragma, zamiast umieszczać je w nich.

## <a name="syntax"></a>Składnia

> **funkcja #pragma (** *function1* [ **,** *function2* ...] **)**

## <a name="remarks"></a>Uwagi

Funkcje wewnętrzne są zwykle generowane jako kod wbudowany, a nie jako wywołania funkcji. Jeśli używasz [wewnętrznej dyrektywy pragma](intrinsic.md) lub opcji kompilatora [/Oi](../build/reference/oi-generate-intrinsic-functions.md) , aby poinformować kompilator, aby wygenerował funkcje wewnętrzne, możesz użyć dyrektywy pragma, aby jawnie wymusić wywołanie funkcji. Gdy zostanie wyświetlona **Funkcja** pragma, obowiązuje ona w pierwszej definicji funkcji, która zawiera określoną funkcję wewnętrzną. Efekt jest kontynuowany na końcu pliku źródłowego lub do wyglądu `intrinsic` dyrektywy pragma określającej tę samą funkcję wewnętrzną. **Funkcji** pragma można używać tylko poza funkcją, na poziomie globalnym.

Listę funkcji, które mają wewnętrzne formularze, można znaleźć w temacie [wewnętrzna pragma](intrinsic.md).

## <a name="example"></a>Przykład

```cpp
// pragma_directive_function.cpp
#include <ctype.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

// use intrinsic forms of memset and strlen
#pragma intrinsic(memset, strlen)

// Find first word break in string, and set remaining
// chars in string to specified char value.
char *set_str_after_word(char *string, char ch) {
   int i;
   int len = strlen(string);  /* NOTE: uses intrinsic for strlen */

   for(i = 0; i < len; i++) {
      if (isspace(*(string + i)))
         break;
   }

   for(; i < len; i++)
      *(string + i) = ch;

   return string;
}

// do not use strlen intrinsic
#pragma function(strlen)

// Set all chars in string to specified char value.
char *set_str(char *string, char ch) {
   // Uses intrinsic for memset, but calls strlen library function
   return (char *) memset(string, ch, strlen(string));
}

int main() {
   char *str = (char *) malloc(20 * sizeof(char));

   strcpy_s(str, sizeof("Now is the time"), "Now is the time");
   printf("str is '%s'\n", set_str_after_word(str, '*'));
   printf("str is '%s'\n", set_str(str, '!'));
}
```

```Output
str is 'Now************'
str is '!!!!!!!!!!!!!!!'
```

## <a name="see-also"></a>Zobacz także

[Dyrektywy pragma i słowo kluczowe __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
