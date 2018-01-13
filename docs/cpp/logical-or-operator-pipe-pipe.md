---
title: 'Logiczny OR Operator: || | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '||'
dev_langs: C++
helpviewer_keywords:
- OR operator [C++], logical
- '|| operator'
- OR operator
- logical OR operator
ms.assetid: 31837c99-2655-4bf3-8ded-f13b7a9dc533
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a826b23f94c4eae4a4fdb5379563b015f05dde71
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="logical-or-operator-"></a>Operator logiczny OR: ||
## <a name="syntax"></a>Składnia  
  
```  
  
logical-or-expression   
||  
 logical-and-expression  
  
```  
  
## <a name="remarks"></a>Uwagi  
 Operator logiczny OR (`||`) zwraca wartość boolean **true** Jeśli lub obydwa argumenty operacji **true** i zwraca **false** inaczej. Argumenty operacji są niejawnie konwertowane na typ `bool` przed oceny i wynik jest typu `bool`. Logiczne lub ma łączność od lewej do prawej.  
  
 Operandów w celu operator logiczny OR nie muszą być tego samego typu, ale muszą być typu wartości całkowitej lub wskaźnika. Argumenty operacji są często relacyjne lub wyrażeń równości.  
  
 Pierwszy argument operacji jest całkowicie obliczane i wszystkie efekty uboczne są wykonywane przed kontynuowaniem Obliczanie wyrażenia logicznego OR.  
  
 Drugi argument operacji jest oceniane tylko wtedy, gdy pierwszy argument operacji daje w wyniku wartość false (0). Eliminuje to zbędne oceny drugiego argumentu operacji, gdy wyrażenia logicznego lub ma wartość true.  
  
```  
printf( "%d" , (x == w || x == y || x == z) );  
```  
  
 W powyższym przykładzie Jeśli `x` jest równa albo `w`, `y`, lub `z`, drugi argument `printf` funkcja zwraca wartość true, a wartość 1 jest drukowana. W przeciwnym razie jest spełniony, drukowana wartość 0. Gdy tylko jeden z warunków zwraca wartość true, wygasa oceny.  
  
## <a name="operator-keyword-for-124124"></a>Operator — słowo kluczowe dla &#124; &#124;  
 **Lub** operator jest odpowiednikiem tekstu `||`. Istnieją dwa sposoby **lub** operatora w programach: uwzględnić plik nagłówka `iso646.h`, lub skompiluj z [/Za](../build/reference/za-ze-disable-language-extensions.md) — opcja kompilatora (Wyłącz rozszerzenia językowe).  
  
## <a name="example"></a>Przykład  
  
```  
// expre_Logical_OR_Operator.cpp  
// compile with: /EHsc  
// Demonstrate logical OR  
#include <iostream>  
using namespace std;  
int main() {  
   int a = 5, b = 10, c = 15;  
   cout  << boolalpha  
         << "The true expression "  
         << "a < b || b > c yields "  
         << (a < b || b > c) << endl  
         << "The false expression "  
         << "a > b || b > c yields "  
         << (a > b || b > c) << endl;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
[Operatory C++ wbudowanych priorytet i łączność](cpp-built-in-operators-precedence-and-associativity.md) [operatory C++ wbudowanych, priorytet i łączność](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Operatory logiczne języka C](../c-language/c-logical-operators.md)