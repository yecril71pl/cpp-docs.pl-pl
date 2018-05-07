---
title: list::sort (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::list::sort
dev_langs:
- C++
helpviewer_keywords:
- sort member [STL/CLR]
ms.assetid: f811d5f4-a19e-4194-8765-1e68097c52f0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 670b18e5901ef264474256a1a1e57cde7a28ef01
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="listsort-stlclr"></a>list::sort (STL/CLR)
Ustala kolejność kontrolowanej sekwencji.  
  
## <a name="syntax"></a>Składnia  
  
```  
void sort();  
template<typename Pred2>  
    void sort(Pred2 pred);  
```  
  
#### <a name="parameters"></a>Parametry  
 pred  
 Moduł porównujący dla elementu pary.  
  
## <a name="remarks"></a>Uwagi  
 Pierwszy funkcji członkowskiej zmienia kolejność elementów w kontrolowanej sekwencji, dzięki czemu są one uporządkowane według `operator<` --elementów nie można jej zmniejszyć wartości w czasie z sekwencją. Ta funkcja członkowska umożliwia sortowanie w kolejności rosnącej w sekwencji.  
  
 Drugi funkcji członkowskiej działa tak samo jako pierwszy, z wyjątkiem tego, że sekwencja jest określona przez `pred`  --  `pred(X, Y)` ma wartość false dla każdego elementu `X` następujący element `Y` wynikowe sekwencji. Umożliwia ona sortowanie sekwencji w kolejności określonej przez funkcję predykatu ani obiektem delegowanym.  
  
 Zarówno funkcje wykonywać stabilna sortowania — nie pary elementów w oryginalnym kontrolowanej sekwencji została odwrócona w wynikowej kontrolowanej sekwencji.  
  
## <a name="example"></a>Przykład  
  
```  
// cliext_list_sort.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// sort descending and redisplay   
    c1.sort(cliext::greater<wchar_t>());   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// sort ascending and redisplay   
    c1.sort();   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
c b a  
a b c  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/listy >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [Lista (STL/CLR)](../dotnet/list-stl-clr.md)   
 [list::merge (STL/CLR)](../dotnet/list-merge-stl-clr.md)   
 [list::reverse (STL/CLR)](../dotnet/list-reverse-stl-clr.md)   
 [list::splice (STL/CLR)](../dotnet/list-splice-stl-clr.md)   
 [list::unique (STL/CLR)](../dotnet/list-unique-stl-clr.md)