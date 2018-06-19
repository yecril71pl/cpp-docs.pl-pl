---
title: Queue::operator = (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::queue::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator= member [STL/CLR]
ms.assetid: 826c335a-5680-498c-b57d-e7bc93a914be
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 539ffbd3320d248e3832e3f48b8c9cc5b7a00e1b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33161795"
---
# <a name="queueoperator-stlclr"></a>queue::operator= (STL/CLR)
Zastępuje kontrolowanej sekwencji.  
  
## <a name="syntax"></a>Składnia  
  
```  
queue <Value, Container>% operator=(queue <Value, Container>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 w prawo  
 Karta kontenera do skopiowania.  
  
## <a name="remarks"></a>Uwagi  
 Element członkowski operatora kopie `right` do obiektu, zwraca `*this`. Umożliwia ona Zamień kontrolowanej sekwencji kopię w kontrolowanej sekwencji `right`.  
  
## <a name="example"></a>Przykład  
  
```  
// cliext_queue_operator_as.cpp   
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
    c2 = c1;   
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
 [queue::assign (STL/CLR)](../dotnet/queue-assign-stl-clr.md)