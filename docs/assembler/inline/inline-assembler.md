---
title: Asembler wbudowany | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 5236bebdeef2db519556d3dace4c20d9529d0e23
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
ms.locfileid: "32055043"
---
# <a name="inline-assembler"></a>Asembler wbudowany
**Microsoft Specific**  
  
 Język asembler ma wiele zastosowań, takich jak poprawa szybkości działania programu, zmniejszenie wymagań dotyczących pamięci i kontrola sprzętu. Można użyć wbudowanego asemblera, aby osadzić instrukcje języka asemblera bezpośrednio w programach źródłowych C i C++, bez dodatkowych kroków asemblacji i łączenia. Asembler wbudowany jest wbudowany w kompilator, więc nie ma potrzeby stosowania oddzielnego asemblera, jak Microsoft Macro Assembler (MASM).  
  
> [!NOTE]
>  Programy z kodem wbudowanego asemblera nie są całkowicie przenośne na inne platformy sprzętowe. Jeśli projektujesz do celów przenośności, unikaj stosowania asemblera wbudowanego.  
  
 Wbudowany zestaw nie jest obsługiwana na RAMIĘ i [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] procesorów.  W następujących tematach opisano, jak używać asemblera wbudowanego Visual C/C++ z procesorami x86:  
  
-   [Omówienie wbudowanego asemblera](../../assembler/inline/inline-assembler-overview.md)  
  
-   [Zalety wbudowanego asemblera](../../assembler/inline/advantages-of-inline-assembly.md)  
  
-   [__asm](../../assembler/inline/asm.md)  
  
-   [Korzystanie z języka Asembler w blokach __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)  
  
-   [Korzystanie z C lub C++ w blokach __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)  
  
-   [Korzystanie z rejestrów i zachowywanie ich w asemblerze wbudowanym](../../assembler/inline/using-and-preserving-registers-in-inline-assembly.md)  
  
-   [Przeskakiwanie do etykiet w asemblerze wbudowanym](../../assembler/inline/jumping-to-labels-in-inline-assembly.md)  
  
-   [Wywoływanie funkcji C w asemblerze wbudowanym](../../assembler/inline/calling-c-functions-in-inline-assembly.md)  
  
-   [Wywoływanie funkcji C++ w asemblerze wbudowanym](../../assembler/inline/calling-cpp-functions-in-inline-assembly.md)  
  
-   [Definiowanie bloków __asm jako makr C](../../assembler/inline/defining-asm-blocks-as-c-macros.md)  
  
-   [Optymalizacja wbudowanego asemblera](../../assembler/inline/optimizing-inline-assembly.md)  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne i język asemblera](../../intrinsics/compiler-intrinsics-and-assembly-language.md)   
 [Dokumentacja języka C++](../../cpp/cpp-language-reference.md)