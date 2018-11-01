---
title: '&lt;nowe&gt; funkcji'
ms.date: 11/04/2016
f1_keywords:
- new/std::nothrow
- new/std::set_new_handler
ms.assetid: e250f06a-b025-4509-ae7a-5356d56aad7d
ms.openlocfilehash: b5803b5fdf44392b6096f9c9a5ebdde7f94eae59
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50604025"
---
# <a name="ltnewgt-functions"></a>&lt;nowe&gt; funkcji

|||
|-|-|
|[nothrow](#nothrow)|[set_new_handler](#set_new_handler)|

## <a name="nothrow"></a>  nothrow

Zapewnia obiekt ma być używany jako argument dla **nothrow** wersje **nowe** i **Usuń**.

```cpp
extern const std::nothrow_t nothrow;
```

### <a name="remarks"></a>Uwagi

Obiekt jest używany jako argumentu funkcji będzie pasował do typu parametru [std::nothrow_t](../standard-library/nothrow-t-structure.md).

### <a name="example"></a>Przykład

Zobacz [nowy operator](../standard-library/new-operators.md#op_new) i [nowy operator&#91; &#93; ](../standard-library/new-operators.md#op_new_arr) przykładów dotyczących sposobów `std::nothrow_t` jest używany jako parametr funkcji.

## <a name="set_new_handler"></a>  set_new_handler

Instaluje funkcję użytkownika, który ma być wywoływana, gdy **nowy operator** zakończy się niepowodzeniem w próba przydzielić pamięci.

```cpp
new_handler set_new_handler(new_handler Pnew) throw();
```

### <a name="parameters"></a>Parametry

*Pnew*<br/>
`new_handler` Do zainstalowania.

### <a name="return-value"></a>Wartość zwracana

0 w pierwszym wywołaniu i poprzedniej `new_handler` w kolejnych wywołaniach.

### <a name="remarks"></a>Uwagi

Magazyny funkcja *Pnew* w statycznych [nowy program obsługi](../standard-library/new-typedefs.md#new_handler) wskaźnika, który przechowuje, zwracana wartość wcześniej przechowywany we wskaźniku. Nowy program obsługi jest używany przez [nowy operator](../standard-library/new-operators.md#op_new)(**size_t**).

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

## <a name="see-also"></a>Zobacz także

[\<new>](../standard-library/new.md)<br/>
