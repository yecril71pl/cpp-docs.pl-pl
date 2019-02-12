---
title: Funkcje śródwierszowe
ms.date: 10/16/2017
helpviewer_keywords:
- fast code
- inline functions, __inline keyword
- functions [C++], inline functions
ms.assetid: 00f4b2ff-8ad0-4165-9f4c-2ef157d03f31
ms.openlocfilehash: ebe0fd3d785903c149999bd4ec8de9eabeabdb05
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56147261"
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

## <a name="see-also"></a>Zobacz także

[w tekście, __inline, \__forceinline](../cpp/inline-functions-cpp.md)
