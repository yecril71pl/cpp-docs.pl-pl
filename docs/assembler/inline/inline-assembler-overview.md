---
title: Omówienie wbudowanego asemblera
ms.date: 08/30/2018
helpviewer_keywords:
- inline assembler
- __asm keyword [C++], invoking inline assembler
- invoking inline assembler
- inline assembly, inline assembler
ms.assetid: d990331a-0e33-4760-8d7a-b720b0288335
ms.openlocfilehash: 6233e07e115c21a0a173f094079dc9c1753533b6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169400"
---
# <a name="inline-assembler-overview"></a>Omówienie wbudowanego asemblera

**Specyficzne dla firmy Microsoft**

Wbudowany asembler umożliwia osadzenie instrukcji języka asemblera w programach C i C++ source bez dodatkowych kroków zestawu i łącza. Wbudowany asembler jest wbudowany w kompilator — nie potrzebujesz oddzielnego asemblera, takiego jak asembler programu Microsoft Macro (MASM).

Ponieważ wbudowany asembler nie wymaga oddzielnego zestawu i kroków łączy, jest bardziej wygodne niż oddzielny asembler. Wbudowany kod asemblera może używać dowolnej nazwy C++ języka c lub zmiennej lub funkcji, która znajduje się w zakresie, dzięki czemu można łatwo zintegrować ją z kodem C++ c i. I ponieważ kod zestawu może być mieszany z C i C++ instrukcjami, może wykonywać zadania, które są uciążliwe lub niemożliwe w języku c C++ lub samodzielnie.

Słowo kluczowe [__asm](../../assembler/inline/asm.md) wywołuje wbudowany asembler i może występować wszędzie tam, gdzie C++ jest to dozwolone. Nie może być wyświetlana sama przez siebie. Po nim musi następować instrukcja zestawu, Grupa instrukcji ujętych w nawiasy klamrowe lub, co najmniej, pustą parę nawiasów klamrowych. Termin "`__asm` blok" odnosi się do dowolnej instrukcji lub grupy instrukcji, niezależnie od tego, czy znajdują się w nawiasach klamrowych.

Poniższy kod to prosty blok `__asm` ujęty w nawiasy klamrowe. (Kod jest sekwencją funkcji niestandardowej.)

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

Alternatywnie można umieścić `__asm` przed każdą instrukcją zestawu:

```cpp
__asm push ebp
__asm mov  ebp, esp
__asm sub  esp, __LOCAL_SIZE
```

Ponieważ `__asm` słowo kluczowe jest separatorem instrukcji, można również umieścić instrukcje zestawu w tym samym wierszu:

```cpp
__asm push ebp   __asm mov  ebp, esp   __asm sub  esp, __LOCAL_SIZE
```

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[Wbudowany asembler](../../assembler/inline/inline-assembler.md)<br/>
