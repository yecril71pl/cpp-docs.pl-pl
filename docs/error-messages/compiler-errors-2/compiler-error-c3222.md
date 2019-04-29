---
title: Błąd kompilatora C3222
ms.date: 11/04/2016
f1_keywords:
- C3222
helpviewer_keywords:
- C3222
ms.assetid: 5624bde8-2fd0-4b8b-92ce-5dfbaf91cf93
ms.openlocfilehash: 9f2c245e98609c8da8f5f89902d5c51bbf9d2b4f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62364015"
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
