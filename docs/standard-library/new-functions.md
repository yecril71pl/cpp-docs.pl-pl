---
title: '&lt;nowe &gt; funkcje'
ms.date: 11/04/2016
f1_keywords:
- new/std::get_new_handler
- new/std::nothrow
- new/std::set_new_handler
ms.assetid: e250f06a-b025-4509-ae7a-5356d56aad7d
ms.openlocfilehash: 6b51a5bcbb9c90370cef1391d4020862d2e2cefd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212179"
---
# <a name="ltnewgt-functions"></a>&lt;nowe &gt; funkcje

## <a name="get_new_handler"></a><a name="get_new_handler"></a>get_new_handler

```cpp
new_handler get_new_handler() noexcept;
```

### <a name="remarks"></a>Uwagi

Zwraca bieżącą wartość `new_handler` .

## <a name="launder"></a><a name="launder"></a>brudn

```cpp
template <class T>
    constexpr T* launder(T* ptr) noexcept;
```

### <a name="parameters"></a>Parametry

*PTR*\
Adres bajtu w pamięci, który zawiera obiekt, którego typ jest podobny do *T*.

### <a name="return-value"></a>Wartość zwracana

Wartość typu *T \* * , która wskazuje na X.

### <a name="remarks"></a>Uwagi

Nazywana również barierą optymalizacji wskaźnika.

Używane jako wyrażenie stałe, gdy wartość jego argumentu może być używana w wyrażeniu stałym. Bajty magazynu są dostępne za pomocą wartości wskaźnika, która wskazuje na obiekt, jeśli w ramach magazynu zajętego przez inny obiekt, obiekt o podobnym wskaźniku.

### <a name="example"></a>Przykład

```cpp
struct X { const int n; };

X *p = new X{3};
const int a = p->n;
new (p) X{5}; // p does not point to new object because X::n is const
const int b = p->n; // undefined behavior
const int c = std::launder(p)->n; // OK
```

## <a name="nothrow"></a><a name="nothrow"></a>nothrow

Dostarcza obiekt, który ma być używany jako argument dla **`nothrow`** wersji **`new`** i **`delete`** .

```cpp
extern const std::nothrow_t nothrow;
```

### <a name="remarks"></a>Uwagi

Obiekt jest używany jako argument funkcji do dopasowania do typu parametru [std:: nothrow_t](../standard-library/nothrow-t-structure.md).

### <a name="example"></a>Przykład

Zobacz [operator new](../standard-library/new-operators.md#op_new) i [operator new&#91;&#93;](../standard-library/new-operators.md#op_new_arr) , aby poznać przykłady `std::nothrow_t` użycia jako parametru funkcji.

## <a name="set_new_handler"></a><a name="set_new_handler"></a>set_new_handler

Instaluje funkcję użytkownika, która ma być wywoływana, gdy **operator new** nie powiedzie się w trakcie próby przydzielenia pamięci.

```cpp
new_handler set_new_handler(new_handler Pnew) throw();
```

### <a name="parameters"></a>Parametry

*Pnew*\
`new_handler`Do zainstalowania.

### <a name="return-value"></a>Wartość zwracana

0 pierwszego wywołania i poprzedni `new_handler` przy kolejnych wywołaniach.

### <a name="remarks"></a>Uwagi

Funkcja przechowuje *Pnew* w statycznym nowym wskaźniku [procedury obsługi](../standard-library/new-typedefs.md#new_handler) , który utrzymuje, a następnie zwraca wartość wcześniej przechowywaną we wskaźniku. Nowy program obsługi jest używany przez [operator new](../standard-library/new-operators.md#op_new)(**size_t**).

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
