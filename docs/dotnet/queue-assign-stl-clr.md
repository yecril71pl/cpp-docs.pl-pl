---
title: Queue::ASSIGN (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::queue::assign
dev_langs:
- C++
helpviewer_keywords:
- assign member [STL/CLR]
ms.assetid: 5bec8a84-9561-43f7-ad7f-f845d0edef41
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 8e68b937e2e32ce76ba77c6e615335f5a733d08d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="queueassign-stlclr"></a>queue::assign (STL/CLR)
Zamienia wszystkie elementy.  
  
## <a name="syntax"></a>Składnia  
  
```  
void assign(queue<Value, Container>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 w prawo  
 Karta kontenera do wstawienia.  
  
## <a name="remarks"></a>Uwagi  
 Funkcja członkowska przypisuje `right.get_container()` do podstawowej kontenera. Możesz użyć do zmiany całej zawartości kolejki.  
  
## <a name="example"></a>Przykład  
  
```  
// cliext_queue_assign.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign a repetition of values   
    Myqueue c2;   
    c2.assign(c1);   
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/kolejki >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [kolejki (STL/CLR)](../dotnet/queue-stl-clr.md)   
 [queue::operator= (STL/CLR)](../dotnet/queue-operator-assign-stl-clr.md)