---
title: Asembler wbudowany | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- assembler [C++]
- assembler [C++], inline
- assembly language [C++], inline
- inline assembler [C++]
- inline assembly [C++]
ms.assetid: 7e13f18f-3628-4306-8b81-4a6d09c043fe
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 22f428a21af037b86e063261003baf9849357c9e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="inline-assembler"></a>Asembler wbudowany
**Dotyczące firmy Microsoft**  
  
 Język asembler ma wiele zastosowań, takich jak poprawa szybkości działania programu, zmniejszenie wymagań dotyczących pamięci i kontrola sprzętu. Można użyć wbudowanego asemblera, aby osadzić instrukcje języka asemblera bezpośrednio w programach źródłowych C i C++, bez dodatkowych kroków asemblacji i łączenia. Asembler wbudowany jest wbudowany w kompilator, więc nie ma potrzeby stosowania oddzielnego asemblera, jak Microsoft Macro Assembler (MASM).  
  
> [!NOTE]
>  Programy z kodem wbudowanego asemblera nie są całkowicie przenośne na inne platformy sprzętowe. Jeśli projektujesz do celów przenośności, unikaj stosowania asemblera wbudowanego.  
  
 Wbudowany zestaw nie jest obsługiwana na RAMIĘ i [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] procesorów.  W następujących tematach opisano, jak używać asemblera wbudowanego Visual C/C++ z procesorami x86:  
  
-   [Omówienie wbudowanego asemblera](../../assembler/inline/inline-assembler-overview.md)  
  
-   [Zalety wbudowanego asemblera](../../assembler/inline/advantages-of-inline-assembly.md)  
  
-   [__asm](../../assembler/inline/asm.md)  
  
-   [Korzystanie z języka asembler w blokach __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)  
  
-   [Przy użyciu języka C lub C++ w blokach __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)  
  
-   [Przy użyciu rejestrów i zachowanie ich w zestawie wbudowanym](../../assembler/inline/using-and-preserving-registers-in-inline-assembly.md)  
  
-   [Przeskakiwanie do etykiet w zestawie wbudowanym](../../assembler/inline/jumping-to-labels-in-inline-assembly.md)  
  
-   [Wywoływanie funkcji języka C w asemblerze wbudowanym](../../assembler/inline/calling-c-functions-in-inline-assembly.md)  
  
-   [Wywoływanie funkcji C++ w asemblerze wbudowanym](../../assembler/inline/calling-cpp-functions-in-inline-assembly.md)  
  
-   [Definiowanie bloków __asm jako makr C](../../assembler/inline/defining-asm-blocks-as-c-macros.md)  
  
-   [Optymalizowanie zestawu wbudowanego](../../assembler/inline/optimizing-inline-assembly.md)  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne i język asemblera](../../intrinsics/compiler-intrinsics-and-assembly-language.md)   
 [Dokumentacja języka C++](../../cpp/cpp-language-reference.md)