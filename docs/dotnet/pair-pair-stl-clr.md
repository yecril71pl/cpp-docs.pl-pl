---
title: Pair::Pair (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::pair::pair
dev_langs:
- C++
helpviewer_keywords:
- pair member [STL/CLR]
ms.assetid: 188035f3-bd37-4b46-96dd-5ceb9a16df79
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 62e16307a96f1f6b672013c2e3c37946942736b8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="pairpair-stlclr"></a>pair::pair (STL/CLR)
Tworzy obiekt pary.  
  
## <a name="syntax"></a>Składnia  
  
```  
pair();  
pair(pair<Coll>% right);  
pair(pair<Coll>^ right);  
pair(Value1 val1, Value2 val2);  
```  
  
#### <a name="parameters"></a>Parametry  
 w prawo  
 Para do przechowywania.  
  
 val1  
 Pierwsza wartość do przechowywania.  
  
 Wart2  
 Druga wartość do przechowywania.  
  
## <a name="remarks"></a>Uwagi  
 Konstruktor:  
  
 `pair();`  
  
 Inicjuje przechowywanych pary z wartościami domyślnymi skonstruowany.  
  
 Konstruktor:  
  
 `pair(pair<Value1, Value2>% right);`  
  
 Inicjuje przechowywanych para z `right.` [pair::first (STL/CLR)](../dotnet/pair-first-stl-clr.md) i `right.` [pair::second (STL/CLR)](../dotnet/pair-second-stl-clr.md).  
  
 `pair(pair<Value1, Value2>^ right);`  
  
 Inicjuje przechowywanych para z `right->` [pair::first (STL/CLR)](../dotnet/pair-first-stl-clr.md) i `right>` [pair::second (STL/CLR)](../dotnet/pair-second-stl-clr.md).  
  
 Konstruktor:  
  
 `pair(Value1 val1, Value2 val2);`  
  
 Inicjuje przechowywanych para z z `val1` i `val2`.  
  
## <a name="example"></a>Przykład  
  
```  
// cliext_pair_construct.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
// construct an empty container   
    cliext::pair<wchar_t, int> c1;   
    System::Console::WriteLine("[{0}, {1}]",   
        c1.first == L'\0' ? "\\0" : "??", c1.second);   
  
// construct with a pair of values   
    cliext::pair<wchar_t, int> c2(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);   
  
// construct by copying another pair   
    cliext::pair<wchar_t, int> c3(c2);   
    System::Console::WriteLine("[{0}, {1}]", c3.first, c3.second);   
  
// construct by copying a pair handle   
    cliext::pair<wchar_t, int> c4(%c3);   
    System::Console::WriteLine("[{0}, {1}]", c4.first, c4.second);   
  
    return (0);   
    }  
  
```  
  
```Output  
[\0, 0]  
[x, 3]  
[x, 3]  
[x, 3]  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/Narzędzia >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [pair (STL/CLR)](../dotnet/pair-stl-clr.md)