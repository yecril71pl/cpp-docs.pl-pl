---
title: Asembler wbudowany | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- assembler [C++]
- assembler [C++], inline
- assembly language [C++], inline
- inline assembler [C++]
- inline assembly [C++]
ms.assetid: 7e13f18f-3628-4306-8b81-4a6d09c043fe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 277ba0aab4f2e756fcf9b5eb1f3a9765b8da3a7b
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43683453"
---
# <a name="inline-assembler"></a>Asembler wbudowany

**Microsoft Specific**

Język asembler ma wiele zastosowań, takich jak poprawa szybkości działania programu, zmniejszenie wymagań dotyczących pamięci i kontrola sprzętu. Można użyć wbudowanego asemblera, aby osadzić instrukcje języka asemblera bezpośrednio w programach źródłowych C i C++, bez dodatkowych kroków asemblacji i łączenia. Asembler wbudowany jest wbudowany w kompilator, więc nie ma potrzeby stosowania oddzielnego asemblera, jak Microsoft Macro Assembler (MASM).

> [!NOTE]
>  Programy z kodem wbudowanego asemblera nie są całkowicie przenośne na inne platformy sprzętowe. Jeśli projektujesz do celów przenośności, unikaj stosowania asemblera wbudowanego.

Wbudowany zestaw nie jest obsługiwany na ARM i x64 procesorów.  W następujących tematach opisano, jak używać asemblera wbudowanego Visual C/C++ z procesorami x86:

- [Omówienie wbudowanego asemblera](../../assembler/inline/inline-assembler-overview.md)

- [Zalety wbudowanego asemblera](../../assembler/inline/advantages-of-inline-assembly.md)

- [__asm](../../assembler/inline/asm.md)

- [Korzystanie z języka Asembler w blokach __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)

- [Korzystanie z C lub C++ w blokach __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)

- [Korzystanie z rejestrów i zachowywanie ich w asemblerze wbudowanym](../../assembler/inline/using-and-preserving-registers-in-inline-assembly.md)

- [Przeskakiwanie do etykiet w asemblerze wbudowanym](../../assembler/inline/jumping-to-labels-in-inline-assembly.md)

- [Wywoływanie funkcji C w asemblerze wbudowanym](../../assembler/inline/calling-c-functions-in-inline-assembly.md)

- [Wywoływanie funkcji C++ w asemblerze wbudowanym](../../assembler/inline/calling-cpp-functions-in-inline-assembly.md)

- [Definiowanie bloków __asm jako makr C](../../assembler/inline/defining-asm-blocks-as-c-macros.md)

- [Optymalizacja wbudowanego asemblera](../../assembler/inline/optimizing-inline-assembly.md)

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora i język asemblera](../../intrinsics/compiler-intrinsics-and-assembly-language.md)<br/>
[Dokumentacja języka C++](../../cpp/cpp-language-reference.md)<br/>