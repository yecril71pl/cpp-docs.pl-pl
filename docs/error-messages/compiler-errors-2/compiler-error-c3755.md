---
title: Błąd kompilatora C3755
ms.date: 11/04/2016
f1_keywords:
- C3755
helpviewer_keywords:
- C3755
ms.assetid: 9317b55e-a52e-4b87-b915-5a208d6eda38
ms.openlocfilehash: 90dc3b7a0e1dbc4e0dc6c42ca722ca1db462fca9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50558213"
---
# <a name="compiler-error-c3755"></a>Błąd kompilatora C3755

"delegowanie": Delegat może nie być zdefiniowana.

A [delegate (C++ Component Extensions)](../../windows/delegate-cpp-component-extensions.md) zadeklarowana ale niezdefiniowana.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3755.

```
// C3755.cpp
// compile with: /clr /c
delegate void MyDel() {};   // C3755
```

## <a name="example"></a>Przykład

C3755 może również wystąpić, Jeśli spróbujesz utworzyć szablon delegata. Poniższy przykład spowoduje wygenerowanie C3755.

```
// C3755_b.cpp
// compile with: /clr /c
ref struct R {
   template<class T>
   delegate void D(int) {}   // C3755
};
```