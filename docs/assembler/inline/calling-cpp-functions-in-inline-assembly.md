---
title: Wywoływanie funkcji C++ w asemblerze wbudowanym | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- functions [C++], calling in inline assembly
- function calls, C++ functions
- function calls, in inline assembly
- Visual C++, functions
- inline assembly, calling functions
- __asm keyword [C++], calling functions
ms.assetid: 1f0d1eb3-54cf-45d5-838d-958188616b38
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ffbd8038d240bc2ab0240d172d914790b6ca02ab
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="calling-c-functions-in-inline-assembly"></a>Wywoływanie funkcji C++ w asemblerze wbudowanym
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 `__asm` Bloku można wywołać tylko globalne funkcje języka C++, które nie są przeciążone. Wywołanie przeciążonej funkcji C++ globalnej lub funkcji członkowskiej C++, kompilator generuje błąd.  
  
 Możesz również wywołaniem dowolnej funkcji zadeklarowana z **zewnętrzne "C"** połączenie. Dzięki temu `__asm` blok w ramach programu C++ do wywołania funkcji biblioteki C, ponieważ funkcje biblioteki, aby zadeklarować wszystkie pliki standardowy nagłówek **zewnętrzne "C"** połączenie.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Wbudowany asembler](../../assembler/inline/inline-assembler.md)