---
title: Transferowanie kontroli | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- control flow, branching
- control flow, transferring control
ms.assetid: aa51e7f2-060f-4106-b0fe-331f04357423
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 594ec49242e919f1ea9bd059588b21292af55409
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="transfers-of-control"></a>Transferowanie kontroli
Można użyć `goto` instrukcji lub **przypadku** etykiety w `switch` instrukcji, aby określić program, który gałęzi poza inicjatora. Taki kod jest niedozwolone, chyba że deklaracji, która zawiera inicjator jest w bloku wewnątrz bloku, w której występuje instrukcja przeskoku.  
  
 W poniższym przykładzie przedstawiono pętli, który deklaruje i inicjuje obiekty `total`, `ch`, i `i`. Istnieje również błędne `goto` instrukcji, która przekazuje sterowanie poza inicjatora.  
  
```  
// transfers_of_control.cpp  
// compile with: /W1  
// Read input until a nonnumeric character is entered.  
int main()  
{  
   char MyArray[5] = {'2','2','a','c'};  
   int i = 0;  
   while( 1 )  
   {  
      int total = 0;  
  
      char ch = MyArray[i++];  
  
      if ( ch >= '0' && ch <= '9' )  
      {  
         goto Label1;  
  
         int i = ch - '0';  
      Label1:  
         total += i;   // C4700: transfers past initialization of i.  
      } // i would be destroyed here if  goto error were not present  
   else  
      // Break statement transfers control out of loop,  
      //  destroying total and ch.  
      break;  
   }  
}  
```  
  
 W powyższym przykładzie `goto` instrukcji próbuje przekazywania kontroli poza inicjowanie `i`. Jednak jeśli `i` zostały zadeklarowane, ale nie został zainicjowany, transfer byłoby prawnych.  
  
 Obiekty `total` i `ch`, zadeklarowanych w bloku, która służy jako *instrukcji* z `while` instrukcji, zostaną zniszczone po tym bloku jest zakończony, przy użyciu `break` instrukcji.  
  
