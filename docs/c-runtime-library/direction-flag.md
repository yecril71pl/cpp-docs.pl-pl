---
title: Flaga kierunku | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.flags
dev_langs:
- C++
helpviewer_keywords:
- direction flag
ms.assetid: 0836b4af-dbbb-4ab8-a4b2-156f2e2099e2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3737304d2443b4f67f00a03e23a0529ad5bcbfe3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="direction-flag"></a>Flaga kierunku
Flaga kierunku jest specyficzne dla procesorów Intel 80 x 86 flagę procesora CPU. Ma to zastosowanie do wszystkich instrukcji zestawu używających REP prefiksu (powtarzania), takich jak MOVS, MOVSD MOVSW i inne. Adresy podane odpowiednie instrukcje zwiększa się, jeśli flaga kierunku jest wyczyszczone.  
  
 Procedury czasu wykonywania języka C założono, że flaga kierunku jest wyczyszczone. Jeśli inne funkcje korzystają z funkcji środowiska wykonawczego języka C, upewnij się czy inne funkcje pozostaw Flaga kierunku samodzielnie, lub przywrócić go do stanu. Oczekiwano Flaga kierunku być wyczyść po wejściu sprawia, że kod wykonywalny szybszych i bardziej wydajnych.  
  
 Funkcje bibliotek C-Run-Time, takie jak procedury manipulowanie ciągami i manipulowanie buforem, oczekują Flaga kierunku być Wyczyść.  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteka CRT, funkcje](../c-runtime-library/crt-library-features.md)