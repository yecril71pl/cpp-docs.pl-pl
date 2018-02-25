---
title: '&lt;nowe&gt; funkcje | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- new/std::nothrow
- new/std::set_new_handler
ms.assetid: e250f06a-b025-4509-ae7a-5356d56aad7d
caps.latest.revision: 
manager: ghogen
ms.openlocfilehash: b22177cf641fca8de8d6f6e59b5e7e25caea8b32
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="ltnewgt-functions"></a>&lt;nowe&gt; funkcje
|||  
|-|-|  
|[nothrow](#nothrow)|[set_new_handler](#set_new_handler)|  
  
##  <a name="nothrow"></a>  nothrow  
 Udostępnia obiekt ma być używany jako argument `nothrow` wersji **nowe** i **usunąć**.  
  
```  
extern const std::nothrow_t nothrow;  
```  
  
### <a name="remarks"></a>Uwagi  
 Obiekt służy jako argument funkcji jest zgodny z typem parametru [std::nothrow_t](../standard-library/nothrow-t-structure.md).  
  
### <a name="example"></a>Przykład  
  Zobacz [nowy operator](../standard-library/new-operators.md#op_new) i [nowy operator &#91; &#93;](../standard-library/new-operators.md#op_new_arr) przykłady `std::nothrow_t` jest używany jako parametr funkcji.  
  
##  <a name="set_new_handler"></a>  set_new_handler —  
 Instaluje funkcji użytkownika, który ma być wywoływana, gdy `operator new` nie powiedzie się może przydzielić pamięci.  
  
```  
new_handler set_new_handler(new_handler Pnew) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `Pnew`  
 New_handler do zainstalowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 0 w pierwszym wywołaniu i poprzedniej `new_handler` w kolejnych wywołaniach.  
  
### <a name="remarks"></a>Uwagi  
 Magazyny funkcja `Pnew` w statycznego [nowy program obsługi](../standard-library/new-typedefs.md#new_handler) wskaźnika, który przechowuje, zwracana wartość wcześniej zapisanych we wskaźniku. Nowy program obsługi jest używany przez [nowy operator](../standard-library/new-operators.md#op_new)( **size_t**).  
  
### <a name="example"></a>Przykład  
  
```cpp  
// new_set_new_handler.cpp  
// compile with: /EHsc  
#include<new>  
#include<iostream>  
  
using namespace std;  
void __cdecl newhandler( )  
{  
   cout << "The new_handler is called:" << endl;  
   throw bad_alloc( );  
   return;  
}  
  
int main( )   
{  
   set_new_handler (newhandler);  
   try  
   {  
      while ( 1 )   
      {  
         new int[5000000];  
         cout << "Allocating 5000000 ints." << endl;  
      }  
   }  
   catch ( exception e )  
   {  
      cout << e.what( ) << endl;  
   }  
}  
```  
  
```Output  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
The new_handler is called:  
bad allocation  
```  
  
## <a name="see-also"></a>Zobacz też  
 [\<new>](../standard-library/new.md)

