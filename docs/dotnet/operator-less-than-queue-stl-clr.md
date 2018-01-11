---
title: operator&lt; (kolejki) (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::queue::operator<
dev_langs: C++
helpviewer_keywords: operator< member [STL/CLR]
ms.assetid: 2c981e2b-9a88-4b4a-8060-9ac24d5631f5
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a4cebd9330dd58d93a0afa4b87ed09ddeab51373
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="operatorlt-queue-stlclr"></a>operator&lt; (kolejki) (STL/CLR)
Kolejki mniej niż porównania.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<typename Value,  
    typename Container>  
    bool operator<(queue<Value, Container>% left,  
        queue<Value, Container>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 left  
 Po lewej stronie kontenera do porównania.  
  
 w prawo  
 Kontener prawo do porównania.  
  
## <a name="remarks"></a>Uwagi  
 Operator funkcja zwraca wartość true, jeśli, dla najniżej `i` dla którego `!(right[i] < left[i])` jest również wartość true, który `left[i] < right[i]`. W przeciwnym razie zwraca `left->` [queue::size (STL/CLR)](../dotnet/queue-size-stl-clr.md) `() <` `right->size()` używanej do testowania czy `left` jest umieszczane przed `right` kiedy dwie kolejki są porównaniu elementu przez element.  
  
## <a name="example"></a>Przykład  
  
```  
// cliext_queue_operator_lt.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myqueue c2;   
    c2.push(L'a');   
    c2.push(L'b');   
    c2.push(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] < [a b c] is {0}",   
        c1 < c1);   
    System::Console::WriteLine("[a b c] < [a b d] is {0}",   
        c1 < c2);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
 a b d  
[a b c] < [a b c] is False  
[a b c] < [a b d] is True  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/kolejki >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [kolejki (STL/CLR)](../dotnet/queue-stl-clr.md)   
 [Operator == (kolejki) (STL/CLR)](../dotnet/operator-equality-queue-stl-clr.md)   
 [Operator! = (kolejki) (STL/CLR)](../dotnet/operator-inequality-queue-stl-clr.md)   
 [operator > = (kolejki) (STL/CLR)](../dotnet/operator-greater-or-equal-queue-stl-clr.md)   
 [operator > (kolejki) (STL/CLR)](../dotnet/operator-greater-than-queue-stl-clr.md)   
 [operator<= (queue) (STL/CLR)](../dotnet/operator-less-or-equal-queue-stl-clr.md)