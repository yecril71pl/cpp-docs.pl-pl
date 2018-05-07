---
title: mniej (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::less
dev_langs:
- C++
helpviewer_keywords:
- less function [STL/CLR]
ms.assetid: fae56216-af66-4cb9-a688-be58a7c7edbb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e7f1aa80a8a4f05f398931c4c6f744ad43f824ad
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="less-stlclr"></a>less (STL/CLR)
Obiekt opisano klasy szablonu, że po wywołaniu zwraca wartość true tylko wtedy, gdy pierwszy argument jest mniejszy od drugiego. Można go użyć Określ obiekt funkcja pod względem jego typ argumentu.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<typename Arg>  
    ref class less  
    { // wrap operator()  
public:  
    typedef Arg first_argument_type;  
    typedef Arg second_argument_type;  
    typedef bool result_type;  
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<  
        first_argument_type, second_argument_type, result_type>  
        delegate_type;  
  
    less();  
    less(less<Arg>% right);  
  
    result_type operator()(first_argument_type left,  
        second_argument_type right);  
    operator delegate_type^();  
    };  
```  
  
#### <a name="parameters"></a>Parametry  
 ARG  
 Typy argumentów.  
  
## <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|Definicja typu|Opis|  
|---------------------|-----------------|  
|delegate_type|Typ ogólny delegata.|  
|first_argument_type|Typ pierwszego argumentu obiekt.|  
|result_type|Typ wyniku obiekt.|  
|second_argument_type|Typ drugiego argumentu obiekt.|  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|less|Tworzy obiekt.|  
  
|Operator|Opis|  
|--------------|-----------------|  
|Operator()|Oblicza odpowiednią funkcję.|  
|Operator delegate_type ^|Rzutuje obiekt do delegata.|  
  
## <a name="remarks"></a>Uwagi  
 Klasa szablonu opisuje obiekt dwóch argumentów. Definiuje operator członkowski `operator()` tak, aby, gdy obiekt jest wywoływana w funkcji, zwraca wartość true, tylko jeśli pierwszy argument jest mniejsza od drugiego.  
  
 Można również przekazać obiekt jako argumentu funkcji, których typ jest `delegate_type^` i zostanie on przekonwertowany odpowiednio.  
  
## <a name="example"></a>Przykład  
  
```  
// cliext_less.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(3);   
    Myvector c2;   
    c2.push_back(4);   
    c2.push_back(4);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 3" and " 4 4"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (int elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c2.begin(), c3.begin(), cliext::less<int>());   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
4 3  
4 4  
0 1  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/funkcjonalności >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [greater_equal (STL/CLR)](../dotnet/greater-equal-stl-clr.md)