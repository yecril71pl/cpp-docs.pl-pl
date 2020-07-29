---
title: Omówienie wbudowanego asemblera
ms.date: 08/30/2018
helpviewer_keywords:
- inline assembler
- __asm keyword [C++], invoking inline assembler
- invoking inline assembler
- inline assembly, inline assembler
ms.assetid: d990331a-0e33-4760-8d7a-b720b0288335
ms.openlocfilehash: 3872dcb194146bf0f4c89b0be03a49b5fe3a9e37
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87192083"
---
# <a name="inline-assembler-overview"></a>Omówienie wbudowanego asemblera

**Specyficzne dla firmy Microsoft**

Wbudowany asembler umożliwia osadzenie instrukcji języka asemblera w programach źródłowych C i C++ bez dodatkowych kroków zestawu i łącza. Wbudowany asembler jest wbudowany w kompilator — nie potrzebujesz oddzielnego asemblera, takiego jak asembler programu Microsoft Macro (MASM).

Ponieważ wbudowany asembler nie wymaga oddzielnego zestawu i kroków łączy, jest bardziej wygodne niż oddzielny asembler. Wbudowany kod asemblera może używać dowolnej zmiennej C lub C++ lub nazwy funkcji, która znajduje się w zakresie, dzięki czemu można łatwo zintegrować ją z kodem C i C++ programu. I ponieważ kod zestawu może być mieszany z instrukcjami C i C++, może wykonywać zadania, które są uciążliwe lub niemożliwe w języku C lub C++.

Słowo kluczowe [__asm](../../assembler/inline/asm.md) wywołuje wbudowany asembler i może występować wszędzie tam, gdzie instrukcja C lub C++ ma charakter prawny. Nie może być wyświetlana sama przez siebie. Po nim musi następować instrukcja zestawu, Grupa instrukcji ujętych w nawiasy klamrowe lub, co najmniej, pustą parę nawiasów klamrowych. Termin " **`__asm`** blok" odnosi się do dowolnej instrukcji lub grupy instrukcji, niezależnie od tego, czy znajdują się w nawiasach klamrowych.

Poniższy kod to prosty **`__asm`** blok ujęty w nawiasy klamrowe. (Kod jest sekwencją funkcji niestandardowej.)

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

Alternatywnie możesz umieścić **`__asm`** przed każdą instrukcją zestawu:

```cpp
__asm push ebp
__asm mov  ebp, esp
__asm sub  esp, __LOCAL_SIZE
```

Ponieważ **`__asm`** słowo kluczowe jest separatorem instrukcji, można również umieścić instrukcje zestawu w tym samym wierszu:

```cpp
__asm push ebp   __asm mov  ebp, esp   __asm sub  esp, __LOCAL_SIZE
```

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Asembler wbudowany](../../assembler/inline/inline-assembler.md)<br/>
