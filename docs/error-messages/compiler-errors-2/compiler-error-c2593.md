---
title: Błąd kompilatora C2593
ms.date: 11/04/2016
f1_keywords:
- C2593
helpviewer_keywords:
- C2593
ms.assetid: 4a0fe9bb-2163-447d-91f6-1890ed8250f6
ms.openlocfilehash: c358553a36104b5c389076f5a5ce02f94f85e85a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50667314"
---
# <a name="compiler-error-c2593"></a>Błąd kompilatora C2593

'operator identyfikator' jest niejednoznaczny

Więcej niż jeden operator możliwe jest zdefiniowany dla przeciążonego operatora.

Ten błąd może być ustalony, użycie jawnego rzutowania na jeden lub więcej parametrów rzeczywistych.

Poniższy przykład spowoduje wygenerowanie C2593:

```
// C2593.cpp
struct A {};
struct B : A {};
struct X {};
struct D : B, X {};
void operator+( X, X );
void operator+( A, B );
D d;

int main() {
   d +  d;         // C2593, D has an A, B, and X
   (X)d + (X)d;    // OK, uses operator+( X, X )
}
```

Ten błąd może być spowodowany przez serializacji zmiennoprzecinkowych zmiennej za pomocą `CArchive` obiektu. Kompilator identyfikuje `<<` operatora jako niejednoznaczny. C++ tylko typy pierwotne typy, które `CArchive` może wykonać serializację typu stałym rozmiarze są `BYTE`, `WORD`, `DWORD`, i `LONG`. Wszystkie typy liczba całkowita musi być rzutowany jednego z następujących typów do serializacji. Typy zmiennoprzecinkowe musi być archiwizowane, przy użyciu `CArchive::Write()` funkcja elementu członkowskiego.

Poniższy przykład pokazuje, jak archiwizowanie zmienną zmiennoprzecinkowych (`f`) do archiwum `ar`:

```
ar.Write(&f, sizeof( float ));
```