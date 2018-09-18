---
title: Błąd kompilatora C2661 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2661
dev_langs:
- C++
helpviewer_keywords:
- C2661
ms.assetid: 60021467-71cd-451b-9877-23840c69309f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a8443e21db273aa7def879bd82ab823afb8a508a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46074399"
---
# <a name="compiler-error-c2661"></a>Błąd kompilatora C2661

'Funkcja': Brak przeciążonej funkcji przyjmującej liczba parametrów

Możliwe przyczyny:

1. Niepoprawne rzeczywistych parametrów w wywołaniu funkcji.

1. Brak deklaracji funkcji.

Poniższy przykład spowoduje wygenerowanie C2661:

```
// C2661.cpp
void func( int ){}
void func( int, int ){}
int main() {
   func( );   // C2661 func( void ) was not declared
   func( 1 );   // OK func( int ) was declared
}
```