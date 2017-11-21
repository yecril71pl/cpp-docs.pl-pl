---
title: hash_map::operator(STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::hash_map::operator[]
dev_langs: C++
helpviewer_keywords: operator[] member [STL/CLR]
ms.assetid: b0b8c1bd-4250-447d-9c69-3f8c34e9b6af
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ae7a414f08a0bc40ab39c3835084a4456e02b685
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="hashmapoperatorstlclr"></a>hash_map::operator(STL/CLR)
Mapuje klucz, do jej powiązaną wartość mapowane.  
  
## <a name="syntax"></a>Składnia  
  
```  
mapped_type operator[](key_type key);  
```  
  
#### <a name="parameters"></a>Parametry  
 klawisz  
 Wartość klucza do wyszukania.  
  
## <a name="remarks"></a>Uwagi  
 Funkcje Członkowskie kwot można znaleźć elementu za równoważne kolejności do `key`. Jeśli zostanie znaleziony, zwraca skojarzona wartość zamapowanego; w przeciwnym razie wstawia `value_type(key, mapped_type())` i zwraca skojarzony wartość mapowane (ustawienie domyślne). Możesz użyć wartość mapowane na podany skojarzonego z nim klucza lub upewnij się, że istnieje wpis dla klucza, w przypadku nieodnalezienia.  
  
## <a name="example"></a>Przykład  
  
```  
// cliext_hash_map_operator_sub.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1;   
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("c1[{0}] = {1}",   
        L'A', c1[L'A']);   
    System::Console::WriteLine("c1[{0}] = {1}",   
        L'b', c1[L'b']);   
  
// redisplay altered contents   
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// alter mapped values and redisplay   
    c1[L'A'] = 10;   
    c1[L'c'] = 13;   
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
c1[A] = 0  
c1[b] = 2  
 [a 1] [A 0] [b 2] [c 3]  
 [a 1] [A 10] [b 2] [c 13]  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/hash_map >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [hash_map — (STL/CLR)](../dotnet/hash-map-stl-clr.md)   
 [hash_map::Find (STL/CLR)](../dotnet/hash-map-find-stl-clr.md)   
 [hash_map::INSERT (STL/CLR)](../dotnet/hash-map-insert-stl-clr.md)