---
title: Asembler wbudowany (C)
ms.date: 11/04/2016
helpviewer_keywords:
- __asm keyword [C]
- inline assembler [C]
ms.assetid: 821acc77-60b1-434c-ba54-2ba930a25ab4
ms.openlocfilehash: 08507c7ce0c1163e8768ed3551cd7053503058e9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50549685"
---
# <a name="inline-assembler-c"></a>Asembler wbudowany (C)

**Microsoft Specific**

Asembler wbudowany pozwala osadzić instrukcje języka asemblera bezpośrednio w programach źródłowych C bez dodatkowego zestawu i kroki łącza. Asembler wbudowany jest wbudowany w kompilator — nie ma potrzeby stosowania oddzielnego asemblera takich jak Microsoft Macro Assembler (MASM).

Ponieważ wbudowanego asemblera nie wymaga osobny zestaw i kroki łącze, jest bardziej wygodne niż stosowania oddzielnego asemblera. Wbudowany kod asemblera, można użyć dowolnego języka C nazwy zmiennej lub funkcji, która znajduje się w zakresie, dzięki czemu można łatwo ją zintegrować z kodu C programu. A ponieważ kodu zestawu mogą być mieszane w instrukcjach języka C, wykonania zadania, które są uciążliwe lub wręcz niemożliwe w języku C samodzielnie.

`__asm` — Słowo kluczowe wywoła asembler wbudowany i może znajdować się wszędzie tam, gdzie instrukcja C jest dozwolony. Nie może występować samodzielnie. Jego musi następować instrukcja zestawu, grupa instrukcji ujęta w nawiasy klamrowe, lub co najmniej, para pustych nawiasów klamrowych. Termin "`__asm` blok" odnosi się tutaj do każdej instrukcji lub grupy instrukcji, czy w nawiasach klamrowych.

Poniższy kod jest prosty `__asm` bloku ujęte w nawiasy klamrowe. (Kod jest funkcję niestandardową sekwencję prologu).

```
__asm
{
   push ebp
   mov  ebp, esp
   sub  esp, __LOCAL_SIZE
}
```

Alternatywnie, możesz umieścić `__asm` przed każdą instrukcję montażu:

```
__asm push ebp
__asm mov  ebp, esp
__asm sub  esp, __LOCAL_SIZE
```

Ponieważ `__asm` — słowo kluczowe jest separatorem instrukcji, instrukcje zestawu można także umieścić w tym samym wierszu:

```
__asm push ebp   __asm mov  ebp, esp   __asm sub  esp, __LOCAL_SIZE
```

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Atrybuty funkcji](../c-language/function-attributes.md)