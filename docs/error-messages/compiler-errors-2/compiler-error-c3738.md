---
title: Błąd kompilatora C3738
ms.date: 11/04/2016
f1_keywords:
- C3738
helpviewer_keywords:
- C3738
ms.assetid: dd3ee011-e204-4264-bf3a-da32c4ef7038
ms.openlocfilehash: e313c7d66bc030183e330dd961fad2fb35f02ac2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62327811"
---
# <a name="compiler-error-c3738"></a>Błąd kompilatora C3738

"calling_convention": Konwencja wywołania jawnego utworzenia wystąpienia musi być zgodna z szablonu wystąpienia

Zaleca się, że nie należy określać Konwencja wywoływania na jawne utworzenie wystąpienia. Jeśli trzeba, jednak konwencji wywoływania muszą być zgodne.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3738.

```
// C3738.cpp
// compile with: /clr
// processor: x86
#include <stdio.h>
template< class T >
void f ( T arg ) {   // by default calling convention is __cdecl
   printf ( "f: %s\n", __FUNCSIG__ );
}

template
void __stdcall f< int > ( int arg );   // C3738
// try the following line instead
// void f< int > ( int arg );

int main () {
   f(1);
   f< int > ( 1 );
}
```