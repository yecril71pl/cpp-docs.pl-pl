---
title: Omówienie wbudowanego asemblera | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inline assembler
- __asm keyword [C++], invoking inline assembler
- invoking inline assembler
- inline assembly, inline assembler
ms.assetid: d990331a-0e33-4760-8d7a-b720b0288335
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0e52316a5080ce7d64d34a09aa265ea561c186ed
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43681222"
---
# <a name="inline-assembler-overview"></a>Omówienie wbudowanego asemblera

**Microsoft Specific**

Asembler wbudowany pozwala osadzić instrukcje języka asemblera w programach źródłowych C i C++, bez dodatkowych kroków asemblacji i łączenia. Asembler wbudowany jest wbudowany w kompilator — nie ma potrzeby stosowania oddzielnego asemblera takich jak Microsoft Macro Assembler (MASM).

Ponieważ wbudowanego asemblera nie wymaga osobny zestaw i kroki łącze, jest bardziej wygodne niż stosowania oddzielnego asemblera. Wbudowany kod asemblera, można użyć dowolnego języka C lub C++ nazwy zmiennej lub funkcji, która znajduje się w zakresie, dzięki czemu można łatwo ją zintegrować z kodu C i C++ programu. A ponieważ kodu zestawu mogą być mieszane w instrukcjach języka C i C++, można to zrobić zadania, które są uciążliwe lub wręcz niemożliwe w C lub C++ samodzielnie.

[__Asm](../../assembler/inline/asm.md) — słowo kluczowe wywoła asembler wbudowany i może znajdować się wszędzie tam, gdzie instrukcja C lub C++ jest legalna. Nie może występować samodzielnie. Jego musi następować instrukcja zestawu, grupa instrukcji ujęta w nawiasy klamrowe, lub co najmniej, para pustych nawiasów klamrowych. Termin "`__asm` blok" odnosi się tutaj do każdej instrukcji lub grupy instrukcji, czy w nawiasach klamrowych.

Poniższy kod jest prosty `__asm` bloku ujęte w nawiasy klamrowe. (Kod jest funkcję niestandardową sekwencję prologu).

```cpp
// asm_overview.cpp
// processor: x86
void __declspec(naked) main()
{
    // Naked functions must provide their own prolog...
    __asm {
        push ebp
        mov ebp, esp
        sub esp, __LOCAL_SIZE
    }

    // ... and epilog
    __asm {
        pop ebp
        ret
    }
}
```

Alternatywnie, możesz umieścić `__asm` przed każdą instrukcję montażu:

```cpp
__asm push ebp
__asm mov  ebp, esp
__asm sub  esp, __LOCAL_SIZE
```

Ponieważ `__asm` — słowo kluczowe jest separatorem instrukcji, instrukcje zestawu można także umieścić w tym samym wierszu:

```cpp
__asm push ebp   __asm mov  ebp, esp   __asm sub  esp, __LOCAL_SIZE
```

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Wbudowany asembler](../../assembler/inline/inline-assembler.md)<br/>