---
title: Błąd kompilatora C2593 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2593
dev_langs:
- C++
helpviewer_keywords:
- C2593
ms.assetid: 4a0fe9bb-2163-447d-91f6-1890ed8250f6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1a3b0d1a8574aa5c05bbca023a1209cf1801f57e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46042731"
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