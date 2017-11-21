---
title: 'Operator logiczny negacji: ! | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '!'
- Not
dev_langs: C++
helpviewer_keywords:
- '! operator'
- NOT operator
- logical negation
ms.assetid: 650add9f-a7bc-426c-b01d-5fc6a81c8b62
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cd8169d2281f1cbd77063eddc312fa93655b99dc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="logical-negation-operator-"></a>Operator logiczny negacji: !
## <a name="syntax"></a>Składnia  
  
```  
  
! cast-expression  
```  
  
## <a name="remarks"></a>Uwagi  
 Operator logiczny negacji (**!**) odwraca znaczenie jej argument. Argument musi być typu arytmetycznego lub wskaźnikowego (lub wyrażenie obliczane do typu arytmetycznego lub wskaźnikowego). Argument operacji jest niejawnie przekonwertować na typ `bool`. Wynik jest **true** Jeśli przekonwertowanego argument operacji jest **false**; wynik jest **false** Jeśli przekonwertowanego argument operacji jest **true**. Wynik jest typu `bool`.  
  
 Wyrażenie *e*, wyrażenie jednoargumentowe **!** *e* jest równoznaczne z wyrażeniem **(***e* `==` 0), z wyjątkiem przypadków, w których przeciążone operatory są zaangażowane.  
  
## <a name="operator-keyword-for-"></a>Operator — słowo kluczowe dla!  
 **Nie** operator jest odpowiednikiem tekst **!**. Istnieją dwa sposoby **nie** operatora w programach: uwzględnić plik nagłówka `iso646.h`, lub skompiluj z [/Za](../build/reference/za-ze-disable-language-extensions.md) — opcja kompilatora (Wyłącz rozszerzenia językowe).  
  
## <a name="example"></a>Przykład  
  
```  
// expre_Logical_NOT_Operator.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
int main() {  
   int i = 0;  
   if (!i)  
      cout << "i is zero" << endl;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia z operatorami Jednoargumentowymi](../cpp/expressions-with-unary-operators.md)   
 [Operatory C++ wbudowanych, priorytet i łączność](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Jednoargumentowe operatory arytmetyczne](../c-language/unary-arithmetic-operators.md)