---
title: 'Bitowy Operator AND: &amp; | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- bitand
dev_langs:
- C++
helpviewer_keywords:
- AND operator
- bitwise operators [C++], AND operator
- '& operator [C++], bitwise operators'
ms.assetid: 76f40de3-c417-47b9-8a77-532f3fc990a5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: aeacac8afb7a8195642ebbfb6aac7c697544cd16
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="bitwise-and-operator-amp"></a>Bitowy Operator AND: &amp;
## <a name="syntax"></a>Składnia  
  
```  
  
expression   
&  
 expression  
  
```  
  
## <a name="remarks"></a>Uwagi  
 Wyrażenia mogą być inne, a wyrażenia lub (podlegające ograniczenia typu wymienione poniżej) wyrażenia równości, relacyjne wyrażenia, wyrażenia dodatku, wyrażenia mnożenia, wskaźnik do elementu członkowskiego wyrażeń wyrażenia rzutowania jednoargumentowe wyrażenia przyrostków wyrażeń lub wyrażenia podstawowe.  
  
 Bitowy operator AND (**&**) porównuje każdy bit pierwszego operandu na odpowiadający mu bit drugiego argumentu operacji. Jeśli oba bity 1, odpowiadający mu bit wynik jest równa 1. W przeciwnym razie odpowiadający mu bit wynik jest równa 0.  
  
 Oba argumenty do bitowy operator AND musi być typów całkowitych. Popularne konwersje arytmetyczne objęte [konwersje standardowe](standard-conversions.md), są stosowane do argumentów operacji.  
  
## <a name="operator-keyword-for-"></a>Operator — słowo kluczowe dla &  
 `bitand` Operator jest odpowiednikiem tekst **&**. Istnieją dwa sposoby `bitand` operatora w programach: uwzględnić plik nagłówka `iso646.h`, lub skompiluj z [/Za](../build/reference/za-ze-disable-language-extensions.md) — opcja kompilatora (Wyłącz rozszerzenia językowe).  
  
## <a name="example"></a>Przykład  
  
```  
// expre_Bitwise_AND_Operator.cpp  
// compile with: /EHsc  
// Demonstrate bitwise AND  
#include <iostream>  
using namespace std;  
int main() {  
   unsigned short a = 0xFFFF;      // pattern 1111 ...  
   unsigned short b = 0xAAAA;      // pattern 1010 ...  
  
   cout  << hex << ( a & b ) << endl;   // prints "aaaa", pattern 1010 ...  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Wbudowane operatory, pierwszeństwo i kojarzenie języka C++](cpp-built-in-operators-precedence-and-associativity.md)  
 [Operatory C++ wbudowanych, priorytet i łączność](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Operatory bitowe języka C](../c-language/c-bitwise-operators.md)