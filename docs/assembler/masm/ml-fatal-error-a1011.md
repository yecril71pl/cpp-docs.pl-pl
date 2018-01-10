---
title: "Błąd krytyczny ML A1011 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: A1011
dev_langs: C++
helpviewer_keywords: A1011
ms.assetid: 7fbf092d-4189-4330-a884-dfa2268fc3dd
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 470340e76897394e5b8ecb042ff97562b0c94c2d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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
  
-   [. ELSE](../../assembler/masm/dot-else.md) następujące`.ELSE`  
  
## <a name="see-also"></a>Zobacz też  
 [Komunikaty o błędach ML](../../assembler/masm/ml-error-messages.md)