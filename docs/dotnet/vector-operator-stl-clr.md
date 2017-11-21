---
title: Vector::operator(STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::vector::operator[]
dev_langs: C++
helpviewer_keywords: operatormember [] [STL/CLR]
ms.assetid: 379a7029-460d-4de8-918b-c79e3e13b9d4
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 73d58a8e1c4a677a248c0a4af90199fd50b36d56
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="vectoroperatorstlclr"></a>Vector::operator(STL/CLR)
Uzyskuje dostęp do elementu w określonej pozycji.  
  
## <a name="syntax"></a>Składnia  
  
```  
reference operator[](size_type pos);  
```  
  
#### <a name="parameters"></a>Parametry  
 POS  
 Pozycja elementu, aby uzyskać dostęp.  
  
## <a name="remarks"></a>Uwagi  
 Operator członkowski zwraca referene do elementu na pozycji `pos`. Umożliwia ona uzyskiwanie dostępu do elementu, którego pozycja znasz.  
  
## <a name="example"></a>Przykład  
  
```  
// cliext_vector_operator_sub.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c" using subscripting   
    for (int i = 0; i < c1.size(); ++i)   
        System::Console::Write(" {0}", c1[i]);   
    System::Console::WriteLine();   
  
// change an entry and redisplay   
    c1[1] = L'x';   
    for (int i = 0; i < c1.size(); ++i)   
        System::Console::Write(" {0}", c1[i]);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a x c  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/wektor >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [Wektor (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [Vector::AT (STL/CLR)](../dotnet/vector-at-stl-clr.md)