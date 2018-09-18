---
title: Błąd kompilatora C2783 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2783
dev_langs:
- C++
helpviewer_keywords:
- C2783
ms.assetid: 1ce94a11-bb8b-4be3-a222-f1f105da74b3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0bc4c28224ce19964087da2c7d116fcc67cd41ef
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46017654"
---
# <a name="compiler-error-c2783"></a>Błąd kompilatora C2783

"deklaracją": nie można wywnioskować argumentu szablonu dla 'Identyfikator'

Kompilator nie może określić argument szablonu. Argumenty domyślne nie można wywnioskować argumentu szablonu.

Poniższy przykład spowoduje wygenerowanie C2783:

```
// C2783.cpp
template<typename T1, typename T2>
T1 f(T2) {
   return 248;
}

int main() {
   f(1);   // C2783
   // try the following line instead
   int i = f<int>(1);
}
```

C2783 może również wystąpić, gdy za pomocą typów ogólnych:

```
// C2783b.cpp
// compile with: /clr
using namespace System;
generic<typename T1, typename T2>
T1 gf(T2) {
   T1 t1 = safe_cast<T1>( Activator::CreateInstance(T1::typeid));
   return t1;
}

ref class MyClass{};

int main() {
   int i;
   i = gf(9);   // C2783

   // OK
   i = gf<int>(9);
}
```