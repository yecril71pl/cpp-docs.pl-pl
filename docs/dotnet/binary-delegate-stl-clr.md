---
title: "binary_delegate — (STL/CLR) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::binary_delegate
dev_langs: C++
helpviewer_keywords: binary_delegate function [STL/CLR]
ms.assetid: 52a9291a-e354-4b9e-a035-78dac1179ec5
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 46faf7218486d6c1016a15ab832a902a0b76009a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="binarydelegate-stlclr"></a>binary_delegate (STL/CLR)
Klasa genereic opisuje delegata dwóch argumentów. Można go używać delegata pod względem jego typów argumentów i określić.  
  
## <a name="syntax"></a>Składnia  
  
```  
generic<typename Arg1,  
    typename Arg2,  
    typename Result>  
    delegate Result binary_delegate(Arg1, Arg2);  
```  
  
#### <a name="parameters"></a>Parametry  
 arg1  
 Typ pierwszego argumentu.  
  
 Arg2  
 Typ drugiego argumentu.  
  
 Wynik  
 Typ zwracany.  
  
## <a name="remarks"></a>Uwagi  
 Delegat genereic opisano funkcję dwóch argumentów.  
  
 Należy pamiętać, że dla:  
  
 `binary_delegate<int, int, int> Fun1;`  
  
 `binary_delegate<int, int, int> Fun2;`  
  
 typy `Fun1` i `Fun2` są synonimy, podczas gdy dla:  
  
 `delegate int Fun1(int, int);`  
  
 `delegate int Fun2(int, int);`  
  
 nie są tego samego typu.  
  
## <a name="example"></a>Przykład  
  
```  
// cliext_binary_delegate.cpp   
// compile with: /clr   
#include <cliext/functional>   
  
bool key_compare(wchar_t left, wchar_t right)   
    {   
    return (left < right);   
    }   
  
typedef cliext::binary_delegate<wchar_t, wchar_t, bool> Mydelegate;   
int main()   
    {   
    Mydelegate^ kcomp = gcnew Mydelegate(&key_compare);   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
compare(L'a', L'a') = False  
compare(L'a', L'b') = True  
compare(L'b', L'a') = False  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/funkcjonalności >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [binary_delegate_noreturn — (STL/CLR)](../dotnet/binary-delegate-noreturn-stl-clr.md)   
 [unary_delegate — (STL/CLR)](../dotnet/unary-delegate-stl-clr.md)   
 [unary_delegate_noreturn — (STL/CLR)](../dotnet/unary-delegate-noreturn-stl-clr.md)