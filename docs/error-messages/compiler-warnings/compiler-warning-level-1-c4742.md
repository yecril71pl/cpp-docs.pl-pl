---
title: Kompilator ostrzeżenie (poziom 1) C4742
ms.date: 11/04/2016
f1_keywords:
- C4742
helpviewer_keywords:
- C4742
ms.assetid: e520881d-1eeb-48b1-9df0-8017ee8ba076
ms.openlocfilehash: 00ac67fec3aafa5a259b5222bd6bb8654210fa61
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390428"
---
# <a name="compiler-warning-level-1-c4742"></a>Kompilator ostrzeżenie (poziom 1) C4742

"var" ma inne wyrównanie w 'plik1' i 'plik2': i numer

Zewnętrzne zmiennej, która została lub odwołuje się zdefiniowane w dwóch plikach ma inne wyrównanie w tych plikach. To ostrzeżenie jest emitowane, gdy kompilator wykryje, że `__alignof` dla zmiennej w *plik1* różni się od `__alignof` dla zmiennej w *plik2*. Może to być spowodowane przy użyciu niezgodne typy podczas deklarowania zmiennej w różnych plików lub przy użyciu niezgodny `#pragma pack` w różnych plikach.

Aby rozwiązać to ostrzeżenie, użyj jednej definicji typu albo używać różnych nazw zmiennych.

Aby uzyskać więcej informacji, zobacz [pakiet](../../preprocessor/pack.md) i [__alignof Operator](../../cpp/alignof-operator.md).

## <a name="example"></a>Przykład

Jest to pierwszy plik, który definiuje typ.

```
// C4742a.c
// compile with: /c
struct X {
   char x, y, z, w;
} global;
```

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4742.

```
// C4742b.c
// compile with: C4742a.c /W1 /GL
// C4742 expected
extern struct X {
   int a;
} global;

int main() {
   global.a = 0;
}
```