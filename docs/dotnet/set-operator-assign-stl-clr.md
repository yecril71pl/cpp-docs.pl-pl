---
title: set::operator = (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::set::operator=
dev_langs: C++
helpviewer_keywords: operator= member [STL/CLR]
ms.assetid: 14e16799-d188-4e0d-a0ce-be2c98f93cc8
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c9e8e8eda7c9f147bf05bc8b24727a2335dbf41a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="setoperator-stlclr"></a>set::operator= (STL/CLR)
Zastępuje kontrolowanej sekwencji.  
  
## <a name="syntax"></a>Składnia  
  
```  
set<Key>% operator=(set<Key>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 w prawo  
 Kontener do skopiowania.  
  
## <a name="remarks"></a>Uwagi  
 Element członkowski operatora kopie `right` do obiektu, zwraca `*this`. Umożliwia ona Zamień kontrolowanej sekwencji kopię w kontrolowanej sekwencji `right`.  
  
## <a name="example"></a>Przykład  
  
```  
// cliext_set_operator_as.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (Myset::value_type elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myset c2;   
    c2 = c1;   
// display contents " a b c"   
    for each (Myset::value_type elem in c2)   
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
 **Nagłówek:** \<cliext/set >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [Ustaw (STL/CLR)](../dotnet/set-stl-clr.md)