---
title: 'Operatory porównania: == i! = | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- not_eq
- '!='
- ==
dev_langs:
- C++
helpviewer_keywords:
- '!= operator'
- equality operator
- not equal to comparison operator
- equality operator [C++], syntax
- == operator
- not_eq operator
- equal to operator
ms.assetid: ba4e9659-2392-4fb4-be5a-910a2a6df45a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 16e4a85f31777581df1a138de6d50b1057253e5b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="equality-operators--and-"></a>Operatory porównania: == i !=
## <a name="syntax"></a>Składnia  
  
```  
expression == expression  
expression != expression  
```  
  
## <a name="remarks"></a>Uwagi  
 Operatory równości binarne porównywanie operandy strict równości i nierówności.  
  
 Operatory porównania, równa się (`==`) i nie równa się (`!=`), należy mieć niższego pierwszeństwa niż operatory relacyjne, ale zachowują się podobnie. Typ wyniku dla tych operatorów jest `bool`.  
  
 Operator równości (`==`) zwraca **true** (1) Jeśli oba argumenty mają taką samą wartość; w przeciwnym razie zwraca **false** (0). Nie równe — operator (`!=`) zwraca **true** Jeśli operandy nie mają taką samą wartość; w przeciwnym razie zwraca **false**.  
  
## <a name="operator-keyword-for-"></a>Operator — słowo kluczowe dla! =  
 `not_eq` Operator jest odpowiednikiem tekstu `!=`. Istnieją dwa sposoby `not_eq` operatora w programach: uwzględnić plik nagłówka `iso646.h`, lub skompiluj z [/Za](../build/reference/za-ze-disable-language-extensions.md) — opcja kompilatora (Wyłącz rozszerzenia językowe).  
  
## <a name="example"></a>Przykład  
  
```  
// expre_Equality_Operators.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
  
int main() {  
   cout  << boolalpha  
         << "The true expression 3 != 2 yields: "  
         << (3 != 2) << endl  
         << "The false expression 20 == 10 yields: "  
         << (20 == 10) << endl;  
}  
```  
  
 Operatory równości można porównywać wskaźników do elementów członkowskich tego samego typu. W takie porównanie konwersje wskaźników do elementów członkowskich są wykonywane. Wskaźniki do elementów członkowskich można porównywać w taki sposób, aby stałe wyrażenie, którego wartością 0.  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia z operatorami Dwuargumentowymi](../cpp/expressions-with-binary-operators.md)   
 [Operatory C++ wbudowanych, priorytet i łączność](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Operatory relacyjne i porównania języka C](../c-language/c-relational-and-equality-operators.md)