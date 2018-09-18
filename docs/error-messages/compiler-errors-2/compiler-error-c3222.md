---
title: Błąd kompilatora C3222 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3222
dev_langs:
- C++
helpviewer_keywords:
- C3222
ms.assetid: 5624bde8-2fd0-4b8b-92ce-5dfbaf91cf93
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 30231f74b379cd9d69806fbd4b49ba0cb55ad871
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46048321"
---
# <a name="compiler-error-c3222"></a>Błąd kompilatora C3222

"parametru": nie można zadeklarować domyślnych argumentów dla elementu członkowskiego, z zarządzanej lub typu WinRT lub funkcji ogólnych

Zadeklaruj parametru metody, za pomocą domyślnego argumentu nie jest dozwolone. Przeciążona metoda jest jednym ze sposobów obejścia tego problemu. Oznacza to należy zdefiniować metodę o takiej samej nazwie bez parametrów, a następnie zainicjować zmienną w treści metody.

Poniższy przykład spowoduje wygenerowanie C3222:

```
// C3222_2.cpp
// compile with: /clr
public ref class G {
   void f( int n = 0 );   // C3222
};
```
