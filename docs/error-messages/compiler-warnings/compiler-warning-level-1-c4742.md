---
title: Ostrzeżenie kompilatora (poziom 1) C4742
ms.date: 11/04/2016
f1_keywords:
- C4742
helpviewer_keywords:
- C4742
ms.assetid: e520881d-1eeb-48b1-9df0-8017ee8ba076
ms.openlocfilehash: 11663a9b8672e2f91feb59e275181dbe645484e9
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051310"
---
# <a name="compiler-warning-level-1-c4742"></a>Ostrzeżenie kompilatora (poziom 1) C4742

element "var" ma inne wyrównanie w "plik1" i "plik2": Number i Number

Zmienna zewnętrzna, do której odwołuje się lub została zdefiniowana w dwóch plikach, ma inne wyrównanie w tych plikach. To ostrzeżenie jest emitowane po znalezieniu przez kompilator `__alignof` dla zmiennej w *plik1* różni się od `__alignof` dla zmiennej w *plik2*. Może to być spowodowane użyciem niezgodnych typów podczas deklarowania zmiennej w różnych plikach lub przy użyciu `#pragma pack` niezgodnych z innymi plikami.

Aby rozwiązać to ostrzeżenie, należy użyć tej samej definicji typu lub użyć różnych nazw dla zmiennych.

Aby uzyskać więcej informacji, zobacz [pakiet](../../preprocessor/pack.md) i [operator __alignof](../../cpp/alignof-operator.md).

## <a name="example"></a>Przykład

Jest to pierwszy plik, który definiuje typ.

```c
// C4742a.c
// compile with: /c
struct X {
   char x, y, z, w;
} global;
```

## <a name="example"></a>Przykład

Poniższy przykład generuje C4742.

```c
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