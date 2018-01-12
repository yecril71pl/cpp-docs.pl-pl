---
title: "logical_not — (STL/CLR) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::logical_not
dev_langs: C++
helpviewer_keywords: logical_not function [STL/CLR]
ms.assetid: 32a2c6e2-1c58-41ac-8827-f3ee5adfe81d
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 8d27e18d540d9638caf819636a37f243b362d369
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="logicalnot-stlclr"></a>logical_not (STL/CLR)
Obiekt opisano klasy szablonu, że po wywołaniu zwraca wartość true tylko wtedy, gdy albo jej argument testów jako FAŁSZ. Można go użyć Określ obiekt funkcja pod względem jego typ argumentu.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<typename Arg>  
    ref class logical_not  
    { // wrap operator()  
public:  
    typedef Arg argument_type;  
    typedef bool result_type;  
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<  
        argument_type, result_type>  
        delegate_type;  
  
    logical_not();  
    logical_not(logical_not<Arg> %right);  
  
    result_type operator()(argument_type left);  
    operator delegate_type^();  
    };  
```  
  
#### <a name="parameters"></a>Parametry  
 ARG  
 Typy argumentów.  
  
## <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|Definicja typu|Opis|  
|---------------------|-----------------|  
|argument_type|Typ argumentu obiekt.|  
|delegate_type|Typ ogólny delegata.|  
|result_type|Typ wyniku obiekt.|  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|logical_not|Tworzy obiekt.|  
  
|Operator|Opis|  
|--------------|-----------------|  
|Operator()|Oblicza odpowiednią funkcję.|  
|Operator delegate_type ^|Rzutuje obiekt do delegata.|  
  
## <a name="remarks"></a>Uwagi  
 Klasa szablonu opisuje obiekt jeden argument. Definiuje operator członkowski `operator()` tak, aby, gdy obiekt jest wywoływana w funkcji, jego zwraca wartość true, tylko jeśli jej argument testów jako wartość false.  
  
 Można również przekazać obiekt jako argumentu funkcji, których typ jest `delegate_type^` i zostanie on przekonwertowany odpowiednio.  
  
## <a name="example"></a>Przykład  
  
```  
// cliext_logical_not.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(0);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 0"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c3.begin(), cliext::logical_not<int>());   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
4 0  
0 1  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/funkcjonalności >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [negate (STL/CLR)](../dotnet/negate-stl-clr.md)