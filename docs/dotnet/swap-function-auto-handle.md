---
title: Funkcja swap (auto_handle)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- swap function
ms.assetid: 7dd91b5c-f0de-4634-a2e2-642626706e27
ms.openlocfilehash: ed0e4ab7bce52d4dee54e7f9149edae535445d65
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91498577"
---
# <a name="swap-function-auto_handle"></a>Funkcja swap (auto_handle)

Zamienia obiekty między nimi `auto_handle` .

## <a name="syntax"></a>Składnia

```
template<typename _element_type>
void swap(
   auto_handle<_element_type> % _left,
   auto_handle<_element_type> % _right
);
```

#### <a name="parameters"></a>Parametry

*_left*<br/>
A `auto_handle` .

*_right*<br/>
Inny `auto_handle` .

## <a name="example"></a>Przykład

```cpp
// msl_swap_auto_handle.cpp
// compile with: /clr
#include <msclr\auto_handle.h>

using namespace System;
using namespace msclr;

int main() {
   auto_handle<String> s1 = "string one";
   auto_handle<String> s2 = "string two";

   Console::WriteLine( "s1 = '{0}', s2 = '{1}'",
      s1->ToString(), s2->ToString() );
   swap( s1, s2 );
   Console::WriteLine( "s1 = '{0}', s2 = '{1}'",
      s1->ToString(), s2->ToString() );
}
```

```Output
s1 = 'string one', s2 = 'string two'
s1 = 'string two', s2 = 'string one'
```

## <a name="requirements"></a>Wymagania

**Plik nagłówka**\<msclr\auto_handle.h>

Msclr **przestrzeni nazw**

## <a name="see-also"></a>Zobacz też

[auto_handle](../dotnet/auto-handle.md)<br/>
[auto_handle::swap](./auto-handle-class.md#swap)
