---
title: '&lt;nowe&gt; funkcji'
ms.date: 11/04/2016
f1_keywords:
- new/std::get_new_handler
- new/std::nothrow
- new/std::set_new_handler
ms.assetid: e250f06a-b025-4509-ae7a-5356d56aad7d
ms.openlocfilehash: c912e5be07ea0ebdd3148d30c80c39a5f8cfa1a5
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68243667"
---
# <a name="ltnewgt-functions"></a>&lt;nowe&gt; funkcji

## <a name="get_new_handler"></a> get_new_handler

```cpp
new_handler get_new_handler() noexcept;
```

### <a name="remarks"></a>Uwagi

Zwraca bieżącą `new_handler`.

## <a name="launder"></a> prania

```cpp
template <class T>
    constexpr T* launder(T* ptr) noexcept;
```

### <a name="parameters"></a>Parametry

*PTR*\
Adres bajtów w pamięci, która zawiera obiekt, którego typ jest podobny do *T*.

### <a name="return-value"></a>Wartość zwracana

Wartości typu *T\**  wskazującej X.

### <a name="remarks"></a>Uwagi

Również określany jako czynnik blokujący optymalizacji wskaźnika.

Używane jako wyrażenie stałe, wartość argumentu może być używana w wyrażeniu stałym. Bajtów magazynu jest dostępny za pośrednictwem wartość wskaźnika, który wskazuje na obiekt, jeśli w ramach magazynu zajmowane przez inny obiekt, obiekt o wskaźnik podobne.

### <a name="example"></a>Przykład

```cpp
struct X { const int n; };

X *p = new X{3};
const int a = p->n;
new (p) X{5}; // p does not point to new object because X::n is const
const int b = p->n; // undefined behavior
const int c = std::launder(p)->n; // OK
```

## <a name="nothrow"></a> nothrow

Zapewnia obiekt ma być używany jako argument dla **nothrow** wersje **nowe** i **Usuń**.

```cpp
extern const std::nothrow_t nothrow;
```

### <a name="remarks"></a>Uwagi

Obiekt jest używany jako argumentu funkcji będzie pasował do typu parametru [std::nothrow_t](../standard-library/nothrow-t-structure.md).

### <a name="example"></a>Przykład

Zobacz [nowy operator](../standard-library/new-operators.md#op_new) i [nowy operator&#91; &#93; ](../standard-library/new-operators.md#op_new_arr) przykładów dotyczących sposobów `std::nothrow_t` jest używany jako parametr funkcji.

## <a name="set_new_handler"></a> set_new_handler

Instaluje funkcję użytkownika, który ma być wywoływana, gdy **nowy operator** zakończy się niepowodzeniem w próba przydzielić pamięci.

```cpp
new_handler set_new_handler(new_handler Pnew) throw();
```

### <a name="parameters"></a>Parametry

*Pnew*\
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
