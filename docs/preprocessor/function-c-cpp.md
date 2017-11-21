---
title: Funkcja (C/C++) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- function_CPP
- vc-pragma.function
dev_langs: C++
helpviewer_keywords:
- function pragma
- pragmas, function
ms.assetid: cbd1bd60-fabf-4b5a-9c3d-2d9f4b871365
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 956c02d7b7df4998187c82cc1dd1c31f196e68b3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="function-cc"></a>funkcja (C/C++)
Określa, że wywołania funkcji znajduje się na liście argumentów pragma jest generowany.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
#pragma function( function1 [, function2, ...] )  
```  
  
## <a name="remarks"></a>Uwagi  
 Jeśli używasz **wewnętrzne** pragma (lub /Oi) aby nakazuje kompilatorowi Generuj funkcje wewnętrzne (funkcje wewnętrzne są generowane jako kodu wbudowanego nie jako wywołania funkcji), można użyć **funkcja** pragma Aby jawnie wymusić wywołania funkcji. Po pragma funkcji jest widoczne, będzie wprowadzona w pierwszym definicji funkcji zawierających określony funkcji wewnętrznej. Efekt nadal na końcu pliku źródłowego lub wygląd **wewnętrzne** pragma określenie tej samej funkcji wewnętrznej. **Funkcja** pragmy można użyć tylko poza funkcją — na poziomie globalnym.  
  
 List funkcje, które mają wewnętrzne formularzy, zobacz [#pragma wewnętrzne](../preprocessor/intrinsic.md).  
  
## <a name="example"></a>Przykład  
  
```  
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