---
title: hash_set::hash_delegate (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::hash_set::hash_delegate
dev_langs:
- C++
helpviewer_keywords:
- hash_delegate member [STL/CLR]
ms.assetid: 34e39d2d-f2ef-4755-9201-3cdb4e41ea56
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e636ce4e508b4ea6ae2b681dd915e016817cd0ef
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33135550"
---
# <a name="hashsethashdelegate-stlclr"></a>hash_set::hash_delegate (STL/CLR)
Wyszukuje element, który odpowiada określonemu kluczowi.  
  
## <a name="syntax"></a>Składnia  
  
```  
hasher^ hash_delegate();  
```  
  
## <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca delegata służący do konwertowania wartości klucza na liczbę całkowitą. Służy do wyznaczania wartości skrótu klucza.  
  
## <a name="example"></a>Przykład  
  
```  
// cliext_hash_set_hash_delegate.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    Myhash_set::hasher^ myhash = c1.hash_delegate();   
  
    System::Console::WriteLine("hash(L'a') = {0}", myhash(L'a'));   
    System::Console::WriteLine("hash(L'b') = {0}", myhash(L'b'));   
    return (0);   
    }  
  
```  
  
```Output  
hash(L'a') = 1616896120  
hash(L'b') = 570892832  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/hash_set >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [hash_set — (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [hash_set::hasher (STL/CLR)](../dotnet/hash-set-hasher-stl-clr.md)