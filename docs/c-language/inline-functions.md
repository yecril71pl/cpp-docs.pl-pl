---
title: Funkcje śródwierszowe
ms.date: 10/16/2017
helpviewer_keywords:
- fast code
- inline functions, __inline keyword
- functions [C++], inline functions
ms.assetid: 00f4b2ff-8ad0-4165-9f4c-2ef157d03f31
ms.openlocfilehash: 2f2ed8ccff0ecbdeff7f3ebac94d5e19ec8042f6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50452640"
---
# <a name="inline-functions"></a>Funkcje śródwierszowe

**Microsoft Specific**

`__inline` — Słowo kluczowe informuje kompilator, aby zastąpić kod w definicji funkcji dla każdego wystąpienia w wywołaniu funkcji. Jednak podstawieniem tylko według uznania kompilatora. Na przykład kompilator wykonuje niewyrównane funkcji adresu jest zajęta lub jest zbyt duży, aby wbudowanego.

Dla funkcji, należy uznać kandydatem do wstawienia, zrównoważenia musi używać definicji stylu nowych funkcji.

Ten formularz służy do określania wbudowanej funkcji:

> **__inline** *typu*<sub>zoptymalizowany pod kątem</sub> *definicji funkcji*

Korzystanie z funkcji śródwierszowych generuje kod szybszy i czasami może generować kod mniejszych niż wywołanie funkcji równoważnej generuje z następujących powodów:

- Można zaoszczędzić czas wymagany do wykonania wywołania funkcji.

- Małe wbudowane funkcje, być może trzy wiersze lub mniej, utworzyć mniejszej ilości kodu niż wywołanie funkcji równoważne, ponieważ kompilator nie generuje kod służący do obsługi argumenty i wartość zwracana.

- Wbudowane funkcje generowane jest zależna od optymalizacji kodu nie jest dostępna do normalnej pracy, ponieważ kompilator nie wykonuje optymalizacje interprocedural.

Funkcje przy użyciu `__inline` nie należy mylić z kodem wbudowanego asemblera. Zobacz [asemblera wbudowanego](../c-language/inline-assembler-c.md) Aby uzyskać więcej informacji.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[w tekście, __inline, \__forceinline](../cpp/inline-functions-cpp.md)

