---
title: Operator == (kolejki) (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::queue::operator==
dev_langs: C++
helpviewer_keywords: operator== member [STL/CLR]
ms.assetid: ad183c61-a24a-4851-aac7-2a47a1371ec2
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 07e674dff56bc64f8b549b7f5d541032d1eaf310
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="operator-queue-stlclr"></a>operator== (queue) (STL/CLR)
Porównanie równy kolejki.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<typename Value,  
    typename Container>  
    bool operator==(queue<Value, Container>% left,  
        queue<Value, Container>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 left  
 Po lewej stronie kontenera do porównania.  
  
 w prawo  
 Kontener prawo do porównania.  
  
## <a name="remarks"></a>Uwagi  
 Funkcja operatora zwraca wartość true, tylko wtedy, gdy w sekwencji, które są kontrolowane przez `left` i `right` ma taką samą długość i dla każdej pozycji `i`, `left[i] ==` `right[i]`. Można go użyć do przetestowania czy `left` jest taka sama jak określona `right` kiedy dwie kolejki są porównaniu elementu przez element.  
  
## <a name="example"></a>Przykład  
  
```  
// cliext_queue_operator_eq.cpp   
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
  
    System::Console::WriteLine("[a b c] == [a b c] is {0}",   
        c1 == c1);   
    System::Console::WriteLine("[a b c] == [a b d] is {0}",   
        c1 == c2);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
 a b d  
[a b c] == [a b c] is True  
[a b c] == [a b d] is False  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/kolejki >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [kolejki (STL/CLR)](../dotnet/queue-stl-clr.md)   
 [Operator! = (kolejki) (STL/CLR)](../dotnet/operator-inequality-queue-stl-clr.md)   
 [operator\< (kolejki) (STL/CLR)](../dotnet/operator-less-than-queue-stl-clr.md)   
 [operator > = (kolejki) (STL/CLR)](../dotnet/operator-greater-or-equal-queue-stl-clr.md)   
 [operator > (kolejki) (STL/CLR)](../dotnet/operator-greater-than-queue-stl-clr.md)   
 [Operator < = (kolejki) (STL/CLR)](../dotnet/operator-less-or-equal-queue-stl-clr.md)