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
ms.openlocfilehash: d826ba5a2252ba11a0b9206a0555c7a022a9382c
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947925"
---
# <a name="logical-and-operator-ampamp"></a>Operator logiczny AND: &amp;&amp;
## <a name="syntax"></a>Składnia  
  
```  
  
expression && expression  
  
```  
  
## <a name="remarks"></a>Uwagi  
 Operator logiczny AND (**&&**) zwraca wartość logiczną PRAWDA, jeśli oba operandy są prawdziwe, a w przeciwnym razie zwraca wartość FALSE. Argumenty operacji są niejawnie konwertowane na typ **bool** przed oceny, a wynik jest typu **bool**. Operator logiczny oraz ma łączność od lewej do prawej.  
  
 Argumenty operacji dla operatora logicznego i nie muszą być tego samego typu, ale muszą być typu wartości całkowitej lub wskaźnika. Argumenty operacji są często relacyjnych lub wyrażeniach porównania.  
  
 Pierwszy operand jest obliczane całkowicie, wraz ze wszystkimi efektami ubocznymi odbywa się przed kontynuowaniem oceny wyrażenie logiczne AND.  
  
 Drugi operand jest oceniany, tylko wtedy, gdy pierwszy operand ma wartość true (niezerową) wartość. Ta ocena eliminuje niepotrzebnego oceny drugiego operandu, gdy wyrażenie logiczne AND ma wartość false. Możesz użyć tej funkcji ocena zwarcia zapobiegające wyłuskanie wskaźnika o wartości null, jak pokazano w poniższym przykładzie:  
  
```cpp 
char *pch = 0;  
...  
(pch) && (*pch = 'a');  
```  
  
 Jeśli `pch` ma wartość null (0), po prawej stronie wyrażenia nigdy nie jest obliczane. W związku z tym przypisania poprzez wskaźnik o wartości null jest niemożliwe.  
  
## <a name="operator-keyword-for-"></a>Słowo kluczowe operator & &  
 **i** operator jest odpowiednikiem tekstu **&&**. Istnieją dwa sposoby dostępu do **i** operatora w programach: uwzględnić plik nagłówka `iso646.h`, lub kompilowanie z [/Za](../build/reference/za-ze-disable-language-extensions.md) — opcja kompilatora (Wyłącz rozszerzenia językowe).  
  
## <a name="example"></a>Przykład  
  
```cpp 
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
 [Operatory języka C++ wbudowane pierwszeństwo i kojarzenie](cpp-built-in-operators-precedence-and-associativity.md) [C++ wbudowane operatory, pierwszeństwo i kojarzenie](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Operatory logiczne języka C](../c-language/c-logical-operators.md)