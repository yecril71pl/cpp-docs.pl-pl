---
title: "Operator wyłączny sumy bitowej OR — Operator: ^ | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- operators [C++], bitwise
- exclusive OR operator
- XOR operator
- bitwise operators [C++], OR operator
- ^ operator
- OR operator [C++], bitwise exclusive
- operators [C++], logical
ms.assetid: f9185d85-65d5-4f64-a6d6-679758d52217
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5cb405f2892ea344f145ae5f25716e1143cda38b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="bitwise-exclusive-or-operator-"></a>Operator wyłączny sumy bitowej OR: ^
## <a name="syntax"></a>Składnia  
  
```  
expression ^ expression  
```  
  
## <a name="remarks"></a>Uwagi  
Bitowy operator OR wyłączne (**^**) porównuje każdy bit jego pierwszego operandu na odpowiadający mu bit jej drugi argument operacji. Jeśli jeden bit ma wartość 0, a inne bit ma wartość 1, odpowiadający mu bit wynik jest równa 1. W przeciwnym razie odpowiadający mu bit wynik jest równa 0.  
  
Obydwa argumenty operacji na poziomie bitowym wyłączny operator OR musi być typów całkowitych. Popularne konwersje arytmetyczne objęte [konwersje standardowe](standard-conversions.md) są stosowane do argumentów operacji.  
  
## <a name="operator-keyword-for-"></a>Operator — słowo kluczowe dla ^  
**Xor** operator jest odpowiednikiem tekst  **^** . Istnieją dwa sposoby **xor** operatora w programach: uwzględnić plik nagłówka `iso646.h`, lub skompiluj z [/Za](../build/reference/za-ze-disable-language-extensions.md) — opcja kompilatora (Wyłącz rozszerzenia językowe).  
  
## <a name="example"></a>Przykład  
  
```cpp  
// expre_Bitwise_Exclusive_OR_Operator.cpp  
// compile with: /EHsc  
// Demonstrate bitwise exclusive OR  
#include <iostream>  
using namespace std;  
int main() {  
   unsigned short a = 0x5555;      // pattern 0101 ...  
   unsigned short b = 0xFFFF;      // pattern 1111 ...  
  
   cout  << hex << ( a ^ b ) << endl;   // prints "aaaa" pattern 1010 ...  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Operatory C++ wbudowanych, priorytet i łączność](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   


