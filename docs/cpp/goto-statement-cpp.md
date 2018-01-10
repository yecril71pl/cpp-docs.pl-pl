---
title: "goto — instrukcja (C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: goto_cpp
dev_langs: C++
helpviewer_keywords: goto keyword [C++]
ms.assetid: 724c5deb-2de1-42d8-8ef1-23589d9bf5ed
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a002071bdb4e271df525b138647b0544cfe9f3c0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="goto-statement-c"></a>goto — instrukcja (C++)
`goto` Instrukcji bezwarunkowo przekazuje sterowanie do instrukcji, którego etykietą jest określony identyfikator.  
  
## <a name="syntax"></a>Składnia  
  
```  
goto identifier;  
```  
  
## <a name="remarks"></a>Uwagi  
 Instrukcja labeled wskazywany przez `identifier` musi znajdować się w bieżącej funkcji. Wszystkie `identifier` nazwy są członkami wewnętrznego obszaru nazw i w związku z tym nie zakłóca innych identyfikatorów.  
  
 Etykieta instrukcji jest znaczący tylko `goto` instrukcji; w przeciwnym razie są ignorowane, etykiet instrukcji. Nie można ponownie zadeklarować etykiety.  
  
 Zaleca programowania stylu `break`, `continue`, i `return` instrukcje zamiast `goto` instrukcji, jeśli to możliwe. Jednak ponieważ `break` instrukcji zamknie tylko jeden poziom w pętli, może być konieczne użycie `goto` instrukcji, aby zakończyć głęboko zagnieżdżone pętli.  
  
 Aby uzyskać więcej informacji na temat etykiety i `goto` instrukcji, zobacz [Labeled — instrukcje](../cpp/labeled-statements.md) i [za pomocą etykiety instrukcji goto](http://msdn.microsoft.com/en-us/6cd7c31a-9822-4241-8566-f79f51be48fe).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie `goto` instrukcji przekazuje sterowanie do punktu z etykietą `stop` podczas `i` jest równe 3.  
  
```  
// goto_statement.cpp  
#include <stdio.h>  
int main()  
{  
    int i, j;  
  
    for ( i = 0; i < 10; i++ )  
    {  
        printf_s( "Outer loop executing. i = %d\n", i );  
        for ( j = 0; j < 2; j++ )  
        {  
            printf_s( " Inner loop executing. j = %d\n", j );  
            if ( i == 3 )  
                goto stop;  
        }  
    }  
  
    // This message does not print:   
    printf_s( "Loop exited. i = %d\n", i );  
  
    stop:   
    printf_s( "Jumped to stop. i = %d\n", i );  
}  
```  
  
```Output  
Outer loop executing. i = 0  
 Inner loop executing. j = 0  
 Inner loop executing. j = 1  
Outer loop executing. i = 1  
 Inner loop executing. j = 0  
 Inner loop executing. j = 1  
Outer loop executing. i = 2  
 Inner loop executing. j = 0  
 Inner loop executing. j = 1  
Outer loop executing. i = 3  
 Inner loop executing. j = 0  
Jumped to stop. i = 3  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje skoku](../cpp/jump-statements-cpp.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)