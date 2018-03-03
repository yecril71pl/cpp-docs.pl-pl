---
title: "Prefiksów inkrementacji i dekrementacji: ++ i--| Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- --
- ++
dev_langs:
- C++
helpviewer_keywords:
- increment operators [C++], syntax
- ++ operator [C++], prefix increment operators
- operators [C++], decrement
- -- operator [C++], prefix decrement operators [C++]
- operators [C++], increment
- decrement operators [C++], syntax
- decrement operators [C++]
ms.assetid: 45ea7fc7-f279-4be9-a216-1d9a0ef9eb7b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ff153c462361e8b6bac8f3c10192025352da650f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="prefix-increment-and-decrement-operators--and---"></a>Operatory prefiksów inkrementacji i dekrementacji: ++ i --
## <a name="syntax"></a>Składnia  
  
```  
++ unary-expression  
-- unary-expression  
```  
  
## <a name="remarks"></a>Uwagi  
 Operator inkrementacji prefiksu (`++`) dodaje je do jej argument operacji; ta wartość zwiększany jest wynikiem wyrażenia. Argument musi być l wartość nie jest typu **const**. Wynik jest wartością l-value tego samego typu jako argument.  
  
 Operator dekrementacji prefiksu (**--**) jest odpowiednikiem operatora inkrementacji prefiksu, że argument jest zmniejszana o jeden wynik jest zmniejszany wartości.  

 **Visual Studio 2017 wersji 15.3 i nowszych** (dostępnych z [/std:c ++ 17](../build/reference/std-specify-language-standard-version.md)): argument operacji operatora inkrementacji lub dekrementacji nie może być typu `bool`.
  
 Prefiks i operatory przyrostka inkrementacji i dekrementacji operatorów mają wpływ na ich argumentów operacji. Najważniejsza różnica między nimi polega na kolejność, w którym zwiększania lub zmniejszania ma miejsce podczas obliczania wyrażenia. (Aby uzyskać więcej informacji, zobacz [przyrostka inkrementacji i dekrementacji](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md).) W formularzu prefiks zwiększania lub zmniejszania ma miejsce przed wartość wyrażenia, więc wartość wyrażenia jest inna niż wartość argumentu operacji. W formularzu operatory przyrostka inkrementacji lub dekrementacji odbywa się po wartość jest używana podczas oceny wyrażenia, więc wartość wyrażenia jest taka sama jak wartość operandu. Na przykład następujące program odbitek "`++i = 6`":  
  
```  
// expre_Increment_and_Decrement_Operators.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
  
int main() {  
   int i = 5;  
   cout << "++i = " << ++i << endl;  
}  
```  
  
 Argument typu całkowitą lub zmiennoprzecinkową jest zwiększone lub zmniejszone przez całkowitą wartość 1. Typ wyniku jest taki sam jak typ argumentu. Argument typu wskaźnika jest zwiększone lub zmniejszone według rozmiaru obiektu, który spełnia. Wskazuje zwiększany wskaźnik do następnego obiektu. zmniejszona wskaźnik wskazuje poprzedniego obiektu.  
  
 Ponieważ operatory inkrementacji i dekrementacji ma efekty uboczne, za pomocą wyrażenia z operatorami zwiększania lub zmniejszania w [makro preprocesora](../preprocessor/macros-c-cpp.md) może mieć niepożądane wyniki. Rozważmy następujący przykład:  
  
```  
// expre_Increment_and_Decrement_Operators2.cpp  
#define max(a,b) ((a)<(b))?(b):(a)  
  
int main()  
{  
   int i = 0, j = 0, k;  
   k = max( ++i, j );  
}  
```  
  
 Makro rozwijany do:  
  
```  
k = ((++i)<(j))?(j):(++i);  
```  
  
 Jeśli `i` jest większa niż lub równa `j` lub mniej niż `j` na 1, jego jest zwiększany dwa razy.  
  
> [!NOTE]
>  Funkcji śródwierszowych języka C++ są preferowane makra w wielu przypadkach, ponieważ eliminuje efekty uboczne, takich jak opisane tutaj i Zezwalaj na język do sprawdzania bardziej szczegółowy typu.  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia z operatorami Jednoargumentowymi](../cpp/expressions-with-unary-operators.md)   
 [Operatory C++ wbudowanych, priorytet i łączność](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Operatory prefiksów inkrementacji i dekrementacji](../c-language/prefix-increment-and-decrement-operators.md)