---
title: 'Operator logiczny AND: &amp; &amp; | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- '&&'
dev_langs:
- C++
helpviewer_keywords:
- logical AND operator
- AND operator
- '&& operator'
ms.assetid: 50cfa664-a8c4-4b31-9bab-2f80d7cd2d1f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f683b7ff17a1dd3945f5cb554a7440ab47fad454
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="logical-and-operator-ampamp"></a>Operator logiczny AND: &amp;&amp;
## <a name="syntax"></a>Składnia  
  
```  
  
expression   
&&  
 expression  
  
```  
  
## <a name="remarks"></a>Uwagi  
 Operator logiczny AND (**&&**) zwraca wartość boolean **true** Jeśli obydwa argumenty operacji są **true** i zwraca **false** w przeciwnym razie wartość. Argumenty operacji są niejawnie konwertowane na typ `bool` przed oceny i wynik jest typu `bool`. Logiczne i ma łączność od lewej do prawej.  
  
 Operandów w celu operator logiczny AND nie muszą być tego samego typu, ale muszą być typu wartości całkowitej lub wskaźnika. Argumenty operacji są często relacyjne lub wyrażeń równości.  
  
 Pierwszy argument operacji jest całkowicie obliczane i wszystkie efekty uboczne są wykonywane przed kontynuowaniem Obliczanie wyrażenia logicznego AND.  
  
 Drugi argument operacji jest oceniane tylko wtedy, gdy pierwszy argument operacji zwraca wartość true (różną od zera). Ocena eliminuje zbędne oceny drugi operand, gdy wyrażenie logiczne i ma wartość false. Możesz użyć tej funkcji zwarcia oceny, aby uniknąć usunięcia odwołania wskaźnik null, jak pokazano w poniższym przykładzie:  
  
```  
char *pch = 0;  
...  
(pch) && (*pch = 'a');  
```  
  
 Jeśli `pch` ma wartość null (0), z prawej strony wyrażenia nigdy nie jest obliczane. W związku z tym przypisania za pomocą wartości null wskaźnika jest niemożliwe.  
  
## <a name="operator-keyword-for-"></a>Operator — słowo kluczowe dla & &  
 **i** operator jest odpowiednikiem tekst **&&**. Istnieją dwa sposoby **i** operatora w programach: uwzględnić plik nagłówka `iso646.h`, lub skompiluj z [/Za](../build/reference/za-ze-disable-language-extensions.md) — opcja kompilatora (Wyłącz rozszerzenia językowe).  
  
## <a name="example"></a>Przykład  
  
```  
// expre_Logical_AND_Operator.cpp  
// compile with: /EHsc  
// Demonstrate logical AND  
#include <iostream>  
  
using namespace std;  
  
int main() {  
   int a = 5, b = 10, c = 15;  
   cout  << boolalpha  
         << "The true expression "  
         << "a < b && b < c yields "  
         << (a < b && b < c) << endl  
         << "The false expression "  
         << "a > b && b < c yields "  
         << (a > b && b < c) << endl;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Operatory C++ wbudowanych priorytet i łączność](cpp-built-in-operators-precedence-and-associativity.md) [operatory C++ wbudowanych, priorytet i łączność](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Operatory logiczne języka C](../c-language/c-logical-operators.md)