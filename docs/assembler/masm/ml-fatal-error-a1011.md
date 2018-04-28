---
title: Błąd krytyczny ML A1011 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A1011
dev_langs:
- C++
helpviewer_keywords:
- A1011
ms.assetid: 7fbf092d-4189-4330-a884-dfa2268fc3dd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 843d676cba61e0da5f917a48408e56e79abb9efd
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="ml-fatal-error-a1011"></a>Błąd krytyczny ML A1011
**dyrektywa musi być w bloku sterowania**  
  
 Asembler znaleziono dyrektywy wysokiego poziomu, której nie oczekiwano jednej. Znaleziono jednej z następujących dyrektyw:  
  
-   [. ELSE](../../assembler/masm/dot-else.md) bez [. JEŚLI](../../assembler/masm/dot-if.md)  
  
-   [. ENDIF](../../assembler/masm/dot-endif.md) bez [. JEŚLI](../../assembler/masm/dot-if.md)  
  
-   [. ENDW](../../assembler/masm/dot-endw.md) bez [. WHILE](../../assembler/masm/dot-while.md)  
  
-   [. UNTILCXZ](../../assembler/masm/dot-untilcxz.md) bez [. POWTÓRZ](../../assembler/masm/dot-repeat.md)  
  
-   [. KONTYNUOWAĆ](../../assembler/masm/dot-continue.md) bez [. GDY](../../assembler/masm/dot-while.md) lub [. POWTÓRZ](../../assembler/masm/dot-repeat.md)  
  
-   [. PODZIEL](../../assembler/masm/dot-break.md) bez [. GDY](../../assembler/masm/dot-while.md) lub [. POWTÓRZ](../../assembler/masm/dot-repeat.md)  
  
-   [. ELSE](../../assembler/masm/dot-else.md) następujące `.ELSE`  
  
## <a name="see-also"></a>Zobacz też  
 [Komunikaty o błędach ML](../../assembler/masm/ml-error-messages.md)