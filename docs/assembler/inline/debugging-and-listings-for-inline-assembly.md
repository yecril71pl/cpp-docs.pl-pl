---
title: Debugowanie i listy dla zestawu wbudowanego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- source level debugger
- __asm keyword [C++], debugging
- inline assembly, listings
- bugs, __asm blocks
- debugging [C++], inline assembly code
- inline assembly, debugging
ms.assetid: 69266930-6f9a-433d-b704-f4f44e7b2583
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 457402626edcdb2be05923aa33bbd26b1cab7137
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="debugging-and-listings-for-inline-assembly"></a>Debugowanie i listy dla zestawu wbudowanego
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 Programy zawierają kodu zestawu wbudowanego może być debugowany przy użyciu debuger poziomu źródła Jeśli kompilacji z [/zi](../../build/reference/z7-zi-zi-debug-information-format.md) opcji.  
  
 W ramach debugera można ustawić punktów przerwania C lub C++ i języka zestawu wierszy. Po włączeniu mieszanego zestawu i tryb źródła można wyświetlić na źródłowym i rozłożonych kodu zestawu.  
  
 Należy pamiętać, że wprowadzanie wielu instrukcje zestawu lub instrukcje języka źródłowego w jednym wierszu może utrudniać debugowania. W trybie źródła można użyć debuger można ustawić punktów przerwania w jednym wierszu, ale nie na pojedyncze instrukcje w tym samym wierszu. Ta sama zasada ma zastosowanie do `__asm` bloku zdefiniowany jako makr C, rozwijany do pojedynczej linii logiczne.  
  
 Jeśli tworzenie mieszanych źródła i lista z zestawu [/FAS](../../build/reference/fa-fa-listing-file.md) — opcja kompilatora, listę zawiera zarówno źródłowy, jak i zestawu metod każdego wiersza języka zestawu. Makra nie zostaną rozwinięte na listach zawartości, ale są one rozwinięte podczas kompilacji.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z języka Asembler w blokach __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)