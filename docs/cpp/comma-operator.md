---
title: Operator przecinkowy:, | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- '%2C'
dev_langs:
- C++
helpviewer_keywords:
- comma operator
ms.assetid: 38e0238e-19da-42ba-ae62-277bfdab6090
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9a139efed1fadd8f7b821363b7cb9cdbf97c9a29
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39408645"
---
# <a name="comma-operator-"></a>Operator przecinkowy: ,
Umożliwia grupowanie dwóch instrukcji, gdzie oczekiwany jest jeden wiersz.  
  
## <a name="syntax"></a>Składnia  
  
```  
expression , expression  
```  
  
## <a name="remarks"></a>Uwagi  
 Operator przecinkowy ma łączność od lewej do prawej. Dwóch wyrażeń, oddzielając wartości przecinkami są obliczane od lewej do prawej. Lewy operand zawsze jest obliczane, a wszystkie efekty uboczne są wykonywane przed prawy operand jest oceniany.  
  
 Przecinki może służyć jako separatorów w niektórych kontekstach, takich jak listy argumentów funkcji. Nie należy mylić użycie przecinka jako separatora przy jego użyciu jako operator; używa dwóch całkowicie różnią się.  
  
 Rozważ wyrażenie  
  
 *E1* , *e2*  
  
 Typ i wartość wyrażenia są typu i wartości *e2*; wynik obliczania wartości *e1* jest odrzucany. Wynik jest wartością l, jeśli prawy operand jest l wartością.  
  
 W przypadku, gdy przecinek jest zwykle używany jako separator (na przykład w rzeczywiste argumenty do funkcji lub inicjatory agregacji), operatora przecinka i jego operandy muszą być ujęte w nawiasy. Na przykład:  
  
```cpp 
func_one( x, y + 2, z );  
func_two( (x--, y + 2), z );  
```  
  
 W funkcji wywołanie `func_one` powyżej, trzech argumentów, oddzielając je średnikami, są przekazywane: `x`, `y + 2`, i `z`. W funkcji wywołanie `func_two`, nawiasy wymuszają na kompilatorze interpretowanie przecinkiem jako operator obliczania sekwencyjnego. Wywołanie tej funkcji przekazuje dwa argumenty `func_two`. Pierwszy argument jest wynikiem operacji obliczania sekwencyjnego `(x--, y + 2)`, który ma wartość i typ wyrażenia `y + 2`; drugi argument funkcji jest `z`.  
  
## <a name="example"></a>Przykład  
  
```cpp 
// cpp_comma_operator.cpp  
#include <stdio.h>  
int main () {  
   int i = 10, b = 20, c= 30;  
   i = b, c;  
   printf("%i\n", i);  
  
   i = (b, c);  
   printf("%i\n", i);  
}  
```  
  
```Output  
20  
30  
```  
  
## <a name="see-also"></a>Zobacz także  
 [Wyrażenia z operatorami Dwuargumentowymi](../cpp/expressions-with-binary-operators.md)   
 [C++ wbudowane operatory, pierwszeństwo i kojarzenie](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Operator obliczania sekwencyjnego](../c-language/sequential-evaluation-operator.md)