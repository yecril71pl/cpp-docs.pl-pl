---
title: czy-while — instrukcja (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- do_cpp
dev_langs:
- C++
helpviewer_keywords:
- do keyword [C++], do-while
- do-while keyword [C++]
- do keyword [C++]
- while keyword [C++], do-while
ms.assetid: e01e6f7c-7da1-4591-87f9-c26ff848e7b0
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7e03a20ad2b49d5c9337e0c8250e5d7c321ee882
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="do-while-statement-c"></a>do-while — instrukcja (C++)
Wykonuje *instrukcji* wielokrotnie aż do zakończenia określony warunek ( *wyrażenie*) daje w wyniku wartość zero.  
  
## <a name="syntax"></a>Składnia  
  
```  
do  
   statement  
while ( expression ) ;  
```  
  
## <a name="remarks"></a>Uwagi  
 Badanie stanu zakończenia staje się po każdej wykonywania pętli. w związku z tym `do-while` pętla jest wykonywana jeden lub więcej razy, w zależności od wartości wyrażenia zakończenia. `do-while` Instrukcji można również zakończyć kiedy [podziału](../cpp/break-statement-cpp.md), [goto](../cpp/goto-statement-cpp.md), lub [zwracać](../cpp/return-statement-cpp.md) instrukcja jest wykonywana w treści instrukcji.  
  
 *Wyrażenie* musi mieć typ arytmetyczny lub wskaźnikowy. Wykonanie przebiega w następujący sposób:  
  
1.  Treść instrukcji jest wykonywana.  
  
2.  Następnie *wyrażenie* oceny. Jeśli *wyrażenie* ma wartość false, `do-while` kończy instrukcji i kontrola przechodzi do następnej instrukcji w programie. Jeśli *wyrażenie* ma wartość true, (niezerowej), proces jest powtarzany, poczynając od kroku 1.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano `do-while` instrukcji:  
  
```  
// do_while_statement.cpp  
#include <stdio.h>  
int main()  
{  
    int i = 0;  
    do  
    {  
        printf_s("\n%d",i++);  
    } while (i < 3);  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Iteracja — instrukcje](../cpp/iteration-statements-cpp.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)   
 [while — instrukcja (C++)](../cpp/while-statement-cpp.md)   
 [for — instrukcja (C++)](../cpp/for-statement-cpp.md)   
 [Range-based for, instrukcja (C++)](../cpp/range-based-for-statement-cpp.md)