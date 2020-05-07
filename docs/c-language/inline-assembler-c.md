---
title: Asembler wbudowany (C)
ms.date: 11/04/2016
helpviewer_keywords:
- __asm keyword [C]
- inline assembler [C]
ms.assetid: 821acc77-60b1-434c-ba54-2ba930a25ab4
ms.openlocfilehash: 8fb2a1dd3e87ef452083935e23048d80b4cdc8c3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62233180"
---
# <a name="inline-assembler-c"></a>Asembler wbudowany (C)

**Specyficzne dla firmy Microsoft**

Wbudowany asembler umożliwia osadzenie instrukcji języka asemblera bezpośrednio w programach źródłowych C bez dodatkowych kroków zestawu i łącza. Wbudowany asembler jest wbudowany w kompilator — nie potrzebujesz oddzielnego asemblera, takiego jak asembler programu Microsoft Macro (MASM).

Ponieważ wbudowany asembler nie wymaga oddzielnego zestawu i kroków łączy, jest bardziej wygodne niż oddzielny asembler. Wbudowany kod asemblera może używać dowolnej zmiennej języka C lub nazwy funkcji, która znajduje się w zakresie, dzięki czemu można łatwo zintegrować ją z kodem C programu. I ponieważ kod zestawu może być mieszany z instrukcjami języka C, można wykonywać zadania, które są nieskomplikowane lub niemożliwe w języku C.

`__asm` Słowo kluczowe wywołuje asembler wbudowany i może występować wszędzie tam, gdzie instrukcja C jest prawna. Nie może być wyświetlana sama przez siebie. Po nim musi następować instrukcja zestawu, Grupa instrukcji ujętych w nawiasy klamrowe lub, co najmniej, pustą parę nawiasów klamrowych. Termin "`__asm` blok" odnosi się do dowolnej instrukcji lub grupy instrukcji, niezależnie od tego, czy znajdują się w nawiasach klamrowych.

Poniższy kod to prosty `__asm` blok ujęty w nawiasy klamrowe. (Kod jest sekwencją funkcji niestandardowej.)

```
__asm
{
   push ebp
   mov  ebp, esp
   sub  esp, __LOCAL_SIZE
}
```

Alternatywnie możesz umieścić `__asm` przed każdą instrukcją zestawu:

```
__asm push ebp
__asm mov  ebp, esp
__asm sub  esp, __LOCAL_SIZE
```

Ponieważ `__asm` słowo kluczowe jest separatorem instrukcji, można również umieścić instrukcje zestawu w tym samym wierszu:

```
__asm push ebp   __asm mov  ebp, esp   __asm sub  esp, __LOCAL_SIZE
```

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[Atrybuty funkcji](../c-language/function-attributes.md)
