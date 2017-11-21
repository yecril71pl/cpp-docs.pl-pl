---
title: "Wywoływanie funkcji C++ w asemblerze wbudowanym | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- functions [C++], calling in inline assembly
- function calls, C++ functions
- function calls, in inline assembly
- Visual C++, functions
- inline assembly, calling functions
- __asm keyword [C++], calling functions
ms.assetid: 1f0d1eb3-54cf-45d5-838d-958188616b38
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0c91829eac3247255d8fe3cb966a61fca5319f94
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="calling-c-functions-in-inline-assembly"></a>Wywoływanie funkcji C++ w asemblerze wbudowanym
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 `__asm` Bloku można wywołać tylko globalne funkcje języka C++, które nie są przeciążone. Wywołanie przeciążonej funkcji C++ globalnej lub funkcji członkowskiej C++, kompilator generuje błąd.  
  
 Możesz również wywołaniem dowolnej funkcji zadeklarowana z **zewnętrzne "C"** połączenie. Dzięki temu `__asm` blok w ramach programu C++ do wywołania funkcji biblioteki C, ponieważ funkcje biblioteki, aby zadeklarować wszystkie pliki standardowy nagłówek **zewnętrzne "C"** połączenie.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Asembler wbudowany](../../assembler/inline/inline-assembler.md)