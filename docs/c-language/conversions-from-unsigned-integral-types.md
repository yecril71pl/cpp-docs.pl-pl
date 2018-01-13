---
title: "Konwersje z niepodpisanych typów całkowitych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- integers, converting
- type casts, involving integers
- data type conversion [C++], signed and unsigned integers
- type conversion [C++], signed and unsigned integers
- integral conversions, from unsigned
ms.assetid: 60fb7e10-bff9-4a13-8a48-e19f25a36a02
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6c2ecc7c4a0308a1a7d182cc0bdaf04c2ed6b6e9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="conversions-from-unsigned-integral-types"></a>Konwersje z niepodpisanych typów całkowitych
Całkowitą bez znaku jest konwertowana na krótszą całkowitą bez znaku lub podpisany tworzy bardziej znaczących bitów lub już niepodpisany lub podpisany liczby całkowitej przez zero, rozszerzanie (zobacz [konwersje z niepodpisanych typów całkowitych](#_clang_table_4..3) tabeli).  
  
 Podczas obniżania poziomu wartość z typu całkowitego na liczbę całkowitą ze znakiem o rozmiarze mniejszym lub liczbą całkowitą bez znaku jest konwertowana na jego odpowiedniej liczby całkowitej ze znakiem, wartość jest bez zmian, jeśli może być reprezentowany w nowego typu. Jednak wartość reprezentuje zmiany, jeśli ustawiono bit logowania, jak w poniższym przykładzie.  
  
```  
int j;  
unsigned short k = 65533;  
  
j = k;  
printf_s( "%hd\n", j );   // Prints -3  
```  
  
 Jeśli nie można przedstawić, wynikiem jest zdefiniowane w implementacji. Zobacz [konwersje rzutowania typów](../c-language/type-cast-conversions.md) informacji na temat obsługi kompilator Microsoft C zwężanie liczb całkowitych. Zachowanie wyniki z konwersja liczby całkowitej lub typ rzutowanie liczb całkowitych.  
  
 Wartości bez znaku są konwertowane w taki sposób, który zachowuje ich wartości, a nie można przedstawić bezpośrednio w C. Jedynym wyjątkiem jest konwersja `unsigned long` do **float**, które co najwyżej traci mniej znaczące bity. W przeciwnym razie wartość są zachowywane, podpisem lub bez. Jeśli wartość typu całkowitego jest konwertowana na liczby zmiennoprzecinkowe, a wartość jest poza zakresem reprezentacja, wynik jest niezdefiniowany. (Zobacz [magazyn typów podstawowych](../c-language/storage-of-basic-types.md) uzyskać informacje na temat zakresu dla typów całkowitych i zmiennoprzecinkowych.)  
  
 Poniższa tabela zawiera podsumowanie konwersje z niepodpisanych typów całkowitych.  
  
### <a name="conversions-from-unsigned-integral-types"></a>Konwersje z niepodpisanych typów całkowitych  
  
|Z|Do|Metoda|  
|----------|--------|------------|  
|`unsigned char`|`char`|Zachowaj wzorca bitowego; bit znaczących staje się bitu znaku|  
|`unsigned char`|**short**|Rozszerzanie zero|  
|`unsigned char`|**long**|Rozszerzanie zero|  
|`unsigned char`|**short bez znaku**|Rozszerzanie zero|  
|`unsigned char`|`unsigned long`|Rozszerzanie zero|  
|`unsigned char`|**float**|Konwertuj na **długi**; przekonwertować **długi** do **liczb zmiennoprzecinkowych**|  
|`unsigned char`|**double**|Konwertuj na **długi**; przekonwertować **długi** do **podwójne**|  
|`unsigned char`|`long double`|Konwertuj na **długi**; przekonwertować **długi** do **podwójne**|  
|**short bez znaku**|`char`|Zachowaj mniej znaczącego bajtu|  
|**short bez znaku**|**short**|Zachowaj wzorca bitowego; bit znaczących staje się bitu znaku|  
|**short bez znaku**|**long**|Rozszerzanie zero|  
|**short bez znaku**|`unsigned char`|Zachowaj mniej znaczącego bajtu|  
|**short bez znaku**|`unsigned long`|Rozszerzanie zero|  
|**short bez znaku**|**float**|Konwertuj na **długi**; przekonwertować **długi** do **liczb zmiennoprzecinkowych**|  
|**short bez znaku**|**double**|Konwertuj na **długi**; przekonwertować **długi** do **podwójne**|  
|**short bez znaku**|`long double`|Konwertuj na **długi**; przekonwertować **długi** do **podwójne**|  
|`unsigned long`|`char`|Zachowaj mniej znaczącego bajtu|  
|`unsigned long`|**short**|Zachowaj znaczącymi bitami programu word|  
|`unsigned long`|**long**|Zachowaj wzorca bitowego; bit znaczących staje się bitu znaku|  
|`unsigned long`|`unsigned char`|Zachowaj mniej znaczącego bajtu|  
|`unsigned long`|**short bez znaku**|Zachowaj znaczącymi bitami programu word|  
|`unsigned long`|**float**|Konwertuj na **długi**; przekonwertować **długi** do **liczb zmiennoprzecinkowych**|  
|`unsigned long`|**double**|Konwertuj bezpośrednio do **podwójne**|  
|`unsigned long`|`long double`|Konwertuj na **długi**; przekonwertować **długi** do **podwójne**|  
  
 **Dotyczące firmy Microsoft**  
  
 Dla kompilatora C Microsoft 32-bitowych `unsigned int` typu jest odpowiednikiem `unsigned long` typu. Konwersja `unsigned int` wartość będzie kontynuowana w taki sam sposób jak konwersja `unsigned long`. Konwersje z `unsigned long` wartości do **float** nie są dokładne, jeśli wartość konwertowanej jest większa niż maksymalna dodatnich podpisany **długi** wartość.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Konwersje przypisań](../c-language/assignment-conversions.md)