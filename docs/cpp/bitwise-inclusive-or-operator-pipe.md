---
title: "Operator Włączny OR Operator: || Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- bitor
- '|'
dev_langs: C++
helpviewer_keywords:
- OR operator [C++], bitwise inclusive
- bitwise operators [C++], OR operator
- inclusive OR operator
- '| operator'
ms.assetid: 4c8a6a68-d828-447d-875a-aedb4ce3aa9a
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 792a5ef5576f68925459d8e7a34168afa11871c5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="bitwise-inclusive-or-operator-"></a>Operator wyłączny sumy bitowej OR: |
## <a name="syntax"></a>Składnia  
  
```  
  
expression   
|  
 expression  
  
```  
  
## <a name="remarks"></a>Uwagi  
 Bitowy operator OR włącznie (**&#124;**) porównuje każdy bit jego pierwszego operandu na odpowiadający mu bit jej drugi argument operacji. Jeśli albo bit ma wartość 1, odpowiadający mu bit wynik jest równa 1. W przeciwnym razie odpowiadający mu bit wynik jest równa 0.  
  
 Obydwa argumenty operacji na poziomie bitowym włączny operator OR musi być typów całkowitych. Popularne konwersje arytmetyczne objęte [konwersje standardowe](standard-conversions.md) są stosowane do argumentów operacji.  
  
## <a name="operator-keyword-for-124"></a>Operator — słowo kluczowe dla &#124;  
 `bitor` Operator jest odpowiednikiem tekst **&#124;**. Istnieją dwa sposoby `bitor` operatora w programach: uwzględnić plik nagłówka `iso646.h`, lub skompiluj z [/Za](../build/reference/za-ze-disable-language-extensions.md) — opcja kompilatora (Wyłącz rozszerzenia językowe).  
  
## <a name="example"></a>Przykład  
  
```  
// expre_Bitwise_Inclusive_OR_Operator.cpp  
// compile with: /EHsc  
// Demonstrate bitwise inclusive OR  
#include <iostream>  
using namespace std;  
  
int main() {  
   unsigned short a = 0x5555;      // pattern 0101 ...  
   unsigned short b = 0xAAAA;      // pattern 1010 ...  
  
   cout  << hex << ( a | b ) << endl;   // prints "ffff" pattern 1111 ...  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Operatory C++ wbudowanych, priorytet i łączność](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Operatory bitowe języka C](../c-language/c-bitwise-operators.md)

