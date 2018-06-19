---
title: operator&lt;= (kolejki) (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::queue::operator<=
dev_langs:
- C++
helpviewer_keywords:
- operator<= member [STL/CLR]
ms.assetid: 63b7f908-4f6b-40d6-bcc6-22970760789d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 1ffdf411d60c9ebdb404899f1f7048174b9be2c6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33136382"
---
# <a name="operatorlt-queue-stlclr"></a>operator&lt;= (kolejki) (STL/CLR)
Kolejka mniejsza lub równa porównania.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<typename Value,  
    typename Container>  
    bool operator<=(queue<Value, Container>% left,  
        queue<Value, Container>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 left  
 Po lewej stronie kontenera do porównania.  
  
 w prawo  
 Kontener prawo do porównania.  
  
## <a name="remarks"></a>Uwagi  
 Funkcja operatora `!(right < left)`. Można go użyć do przetestowania czy `left` porządkowania nie po `right` kiedy dwie kolejki są porównaniu elementu przez element.  
  
## <a name="example"></a>Przykład  
  
```  
// cliext_queue_operator_le.cpp   
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
  
    System::Console::WriteLine("[a b c] <= [a b c] is {0}",   
        c1 <= c1);   
    System::Console::WriteLine("[a b d] <= [a b c] is {0}",   
        c2 <= c1);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
 a b d  
[a b c] <= [a b c] is True  
[a b d] <= [a b c] is False  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/kolejki >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [kolejki (STL/CLR)](../dotnet/queue-stl-clr.md)   
 [Operator == (kolejki) (STL/CLR)](../dotnet/operator-equality-queue-stl-clr.md)   
 [Operator! = (kolejki) (STL/CLR)](../dotnet/operator-inequality-queue-stl-clr.md)   
 [operator\< (kolejki) (STL/CLR)](../dotnet/operator-less-than-queue-stl-clr.md)   
 [operator > = (kolejki) (STL/CLR)](../dotnet/operator-greater-or-equal-queue-stl-clr.md)   
 [operator> (queue) (STL/CLR)](../dotnet/operator-greater-than-queue-stl-clr.md)