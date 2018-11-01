---
title: funkcja (C/C++)
ms.date: 11/04/2016
f1_keywords:
- function_CPP
- vc-pragma.function
helpviewer_keywords:
- function pragma
- pragmas, function
ms.assetid: cbd1bd60-fabf-4b5a-9c3d-2d9f4b871365
ms.openlocfilehash: 1c8c250e3ea28d56aec837f5c3353c3bb6515442
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50611461"
---
# <a name="function-cc"></a>funkcja (C/C++)
Określa, że wywołania funkcji określonych na liście argumentów pragma być generowane.

## <a name="syntax"></a>Składnia

```
#pragma function( function1 [, function2, ...] )
```

## <a name="remarks"></a>Uwagi

Jeśli używasz `intrinsic` pragma (lub /Oi) aby poinformować kompilator, aby wygenerować funkcje wewnętrzne (funkcje wewnętrzne są generowane jako kodu wbudowanego, nie jako wywołania funkcji), można użyć **funkcja** pragmy do jawnego wymuszenia wywołania funkcji. Po pragmie funkcji jest widoczny, zaczyna obowiązywać przy pierwszej definicji funkcji zawierający określoną funkcję wewnętrzne. Efekt kontynuuje do końca pliku źródłowego lub wyglądu `intrinsic` pragma, określając tę samą funkcję wewnętrzne. **Funkcja** dyrektywa może zostać użyta tylko poza funkcją — na poziomie globalnym.

Aby uzyskać listę funkcji, które mają wewnętrzne formularzy, zobacz [#pragma wewnętrzne](../preprocessor/intrinsic.md).

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

## <a name="see-also"></a>Zobacz też

[Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)