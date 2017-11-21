---
title: Operator przecinkowy:, | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '%2C'
dev_langs: C++
helpviewer_keywords: comma operator
ms.assetid: 38e0238e-19da-42ba-ae62-277bfdab6090
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 444b13ea2dc01930d7ce667eb25345d635c5a3de
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="comma-operator-"></a>Operator przecinkowy: ,
Umożliwia grupowanie dwie instrukcje, gdzie oczekiwany jest jeden wiersz.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
expression , expression  
```  
  
## <a name="remarks"></a>Uwagi  
 Operator przecinkowy ma łączność od lewej do prawej. Dwóch wyrażeń oddzielonych przecinkami są wykonywane od lewej do prawej. Lewy argument operacji zawsze jest obliczane, a wszystkie efekty uboczne są wykonywane przed prawy operand jest obliczane.  
  
 Jako separatorów w niektórych kontekstach, takie jak listy argumentów funkcji można używać przecinków. Nie należy mylić użycie przecinka jako separatora z jako operatora; używa dwóch różnią się całkowicie.  
  
 Należy wziąć pod uwagę wyrażenie  
  
 *E1* , *e2*  
  
 Typ i wartość wyrażenia są typu i wartości *e2*; wynikiem obliczenia *e1* zostaną odrzucone. Wynik jest wartością l-value, jeśli prawy operand jest wartością l-value.  
  
 W przypadku, gdy przecinek jest zwykle używany jako separator (na przykład w rzeczywistych argumentów do funkcji lub agregacji inicjatory), przecinka i argumentów musi być ujęta w nawiasy. Na przykład:  
  
```  
func_one( x, y + 2, z );  
func_two( (x--, y + 2), z );  
```  
  
 W funkcji wywołanie `func_one` powyżej, trzech argumentów rozdzielonych przecinkami, są przekazywane: `x`, `y + 2`, i `z`. W funkcji wywołanie `func_two`, kompilator, aby zinterpretować przecinkiem jako operator obliczania sekwencyjnego wymusić nawiasów. Wywołanie tej funkcji przekazuje dwa argumenty do `func_two`. Pierwszy argument jest wynik operacji obliczania sekwencyjnego `(x--, y + 2)`, która zawiera wartości i typ wyrażenia `y + 2`; drugi argument jest `z`.  
  
## <a name="example"></a>Przykład  
  
```  
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
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia z operatorami Dwuargumentowymi](../cpp/expressions-with-binary-operators.md)   
 [Operatory C++ wbudowanych, priorytet i łączność](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Operator obliczania sekwencyjnego](../c-language/sequential-evaluation-operator.md)
