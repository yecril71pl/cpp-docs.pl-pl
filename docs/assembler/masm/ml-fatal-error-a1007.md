---
title: Błąd krytyczny ML A1007 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A1007
dev_langs:
- C++
helpviewer_keywords:
- A1007
ms.assetid: bcf9c826-beb3-4e93-91fe-1ffd34995fbf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 10b883fad01943cd8cff71b3da9dee66407ccc93
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="ml-fatal-error-a1007"></a>Błąd krytyczny ML A1007
**poziom zagnieżdżenia zbyt głęboko**  
  
 Asembler osiągnęła limit zagnieżdżania. Limit wynosi 20 poziomy, z wyjątkiem przypadków, gdy zaznaczono inaczej.  
  
 Jedną z następujących zostało zagnieżdżone zbyt głęboko:  
  
-   Dyrektywy wysokiego poziomu, takich jak [. Jeśli](../../assembler/masm/dot-if.md), [. Powtórz](../../assembler/masm/dot-repeat.md), lub [. GDY](../../assembler/masm/dot-while.md).  
  
-   Definicja struktury.  
  
-   Dyrektywa zestawu warunkowego.  
  
-   Definicja procedury.  
  
-   A [pushcontext —](../../assembler/masm/pushcontext.md) — dyrektywa (limit wynosi 10).  
  
-   Definicja segmentu.  
  
-   Dołącz plik.  
  
-   Makra.  
  
## <a name="see-also"></a>Zobacz też  
 [Komunikaty o błędach ML](../../assembler/masm/ml-error-messages.md)