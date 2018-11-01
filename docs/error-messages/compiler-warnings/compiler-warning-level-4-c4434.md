---
title: Kompilator ostrzeżenie (poziom 4) C4434
ms.date: 11/04/2016
f1_keywords:
- C4434
helpviewer_keywords:
- C4434
ms.assetid: 24b8785e-353a-4c37-8bed-ed61001a871d
ms.openlocfilehash: 6a7d760a7d192c7e0a7bd5e16f77efe1a4099c31
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50591268"
---
# <a name="compiler-warning-level-4-c4434"></a>Kompilator ostrzeżenie (poziom 4) C4434

Konstruktor klasy musi posiadać prywatną dostępność; Zmiana na prywatny dostęp

C4434 wskazuje, że kompilator zmienione dostępność Konstruktor statyczny. Konstruktory statyczne musi posiadać prywatną dostępność, ponieważ są one przeznaczone tylko do wywołania przez środowisko uruchomieniowe języka wspólnego. Aby uzyskać więcej informacji, zobacz [konstruktorów statycznych](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Static_constructors).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4434.

```
// C4434.cpp
// compile with: /W4 /c /clr
public ref struct R {
   static R(){}   // C4434
};
```