---
title: "sizeof — Operator | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sizeof_cpp
dev_langs:
- C++
helpviewer_keywords:
- sizeof operator
ms.assetid: 8bc3b6fb-54a1-4eb7-ada0-05f8c5efc532
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 072dbd8d41a867f7cd31316ef0bc1c20660952ef
ms.sourcegitcommit: 9a0a287d6940591523af959ebdac5affa36220da
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2018
---
# <a name="sizeof-operator"></a>sizeof — operator
Zwraca rozmiar jej argument operacji względem rozmiar typu `char`.  
  
> [!NOTE]
>  Aby uzyskać informacje o `sizeof ...` operatora, zobacz [wielokropki i szablony Wariadyczne](../cpp/ellipses-and-variadic-templates.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
sizeof unary-expression  
sizeof  ( type-name )  
```  
  
## <a name="remarks"></a>Uwagi  
 Wynik `sizeof` operator jest typu `size_t`, typem całkowitym zdefiniowane w pliku dołączanego \<stddef.h >. Ten operator umożliwia Unikaj określania rozmiarów maszyny zależne od danych w programach.  
  
 Argument operacji do `sizeof` może być jedną z następujących czynności:  
  
-   Nazwa typu. Aby użyć `sizeof` z nazwą typu nazwa musi być ujęta w nawiasy.  
  
-   Wyrażenie. W przypadku użycia z wyrażeniem, `sizeof` można określić z lub bez nawiasów. Wyrażenie nie jest obliczane.  
  
 Gdy `sizeof` operator jest stosowane do obiektu typu `char`, jego daje 1. Gdy `sizeof` operator zostaną zastosowane do tablicy, jego daje całkowita liczba bajtów w tablicy, nie rozmiaru wskaźnika reprezentowany przez identyfikator tablicy. Aby uzyskać rozmiaru wskaźnika reprezentowany przez identyfikator tablicy, przekaż go jako parametr do funkcji, która używa `sizeof`. Na przykład:  
  
## <a name="example"></a>Przykład  
  
```  
#include <iostream>  
using namespace std;  
  
size_t getPtrSize( char *ptr )  
{  
   return sizeof( ptr );  
}  
  
int main()  
{  
   char szHello[] = "Hello, world!";  
  
   cout  << "The size of a char is: "  
         << sizeof( char )  
         << "\nThe length of " << szHello << " is: "  
         << sizeof szHello  
         << "\nThe size of the pointer is "  
         << getPtrSize( szHello ) << endl;  
}  
```  
  
## <a name="sample-output"></a>Przykładowe dane wyjściowe  
  
```  
The size of a char is: 1  
The length of Hello, world! is: 14  
The size of the pointer is 4  
```  
  
 Gdy `sizeof` operator jest stosowany do `class`, `struct`, lub `union` typu, wynik jest to liczba bajtów w obiekcie tego typu, a także wszelkie uzupełnienia dodane do wyrównywanie elementów członkowskich na granice programu word. Wynik nie zawsze odpowiada rozmiar obliczany przez dodanie wymagania dotyczące magazynu w poszczególnych członków. [/Zp](../build/reference/zp-struct-member-alignment.md) — opcja kompilatora i [pakietu](../preprocessor/pack.md) pragma wpływu na granice wyrównania elementów członkowskich.  
  
 `sizeof` Operator nigdy nie daje 0, nawet w przypadku pustą klasę.  
  
 `sizeof` Nie można używać operatora z następujących argumentów:  
  
-   Funkcje. (Jednak `sizeof` można zastosować do wskaźników do funkcji.)  
  
-   Bit pola.  
  
-   Niezdefiniowany klasy.  
  
-   Typ `void`.  
  
-   Dynamicznie przydzielane tablic.  
  
-   Tablice zewnętrznych.  
  
-   Niekompletne typy.  
  
-   Niekompletne typy nazwy na ujętego w nawiasy.  
  
 Podczas `sizeof` operator dotyczy odwołanie, wynikiem jest taki sam jak `sizeof` zastosowane na obiekt.  
  
 Jeśli tablica bez określonego rozmiaru jest ostatnim elementem struktury, operator `sizeof` zwróci rozmiar struktury bez tablicy.  
  
 `sizeof` Operator jest często używane do obliczania liczby elementów w tablicy przy użyciu wyrażenia w postaci:  
  
```  
sizeof array / sizeof array[0]  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia z operatorami Jednoargumentowymi](../cpp/expressions-with-unary-operators.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)