---
title: "make_pair — (STL/CLR) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::make_pair
dev_langs: C++
helpviewer_keywords: make_pair function [STL/CLR]
ms.assetid: 74733f2c-97b0-4d69-b431-5ab8f0de9e3e
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8fba63cb9e10fcdccba8ed5c6a8a405184a4bca5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="makepair-stlclr"></a>make_pair (STL/CLR)
Wprowadź `pair` z pary wartości.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<typename Value1,  
    typename Value2>  
    pair<Value1, Value2> make_pair(Value1 first, Value2 second);  
```  
  
#### <a name="parameters"></a>Parametry  
 `Value1`  
 Typ pierwszego zakodowana wartość.  
  
 `Value2`  
 Typ drugiego zakodowana wartość.  
  
 `first`  
 Pierwsza wartość do zakodowania.  
  
 `second`  
 Druga wartość do zakodowania.  
  
## <a name="remarks"></a>Uwagi  
 Funkcja szablonu `pair<Value1, Value2>(first, second)`. Można go użyć do utworzenia `pair<Value1, Value2>` obiektu z pary wartości.  
  
## <a name="example"></a>Przykład  
  
```cpp  
// cliext_make_pair.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
    cliext::pair<wchar_t, int> c1(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
  
    c1 = cliext::make_pair(L'y', 4);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
    return (0);   
    }  
  
```  
  
```Output  
[x, 3]  
[y, 4]  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/Narzędzia >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [range_adapter — (STL/CLR)](../dotnet/range-adapter-stl-clr.md)