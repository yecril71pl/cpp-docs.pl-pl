---
title: "Błąd krytyczny ML A1007 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: A1007
dev_langs: C++
helpviewer_keywords: A1007
ms.assetid: bcf9c826-beb3-4e93-91fe-1ffd34995fbf
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 619f1eae458b52eb7851118d6702dccec769a1ca
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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