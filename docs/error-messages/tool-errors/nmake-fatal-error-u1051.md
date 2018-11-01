---
title: Błąd krytyczny NMAKE U1051
ms.date: 11/04/2016
f1_keywords:
- U1051
helpviewer_keywords:
- U1051
ms.assetid: fede5cd5-dac3-47b7-b86d-e1acfb78699f
ms.openlocfilehash: ddf1d262fb8dfc6e63b0bf5cc098b7b140539310
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50641509"
---
# <a name="nmake-fatal-error-u1051"></a>Błąd krytyczny NMAKE U1051

Za mało pamięci

NMAKE za mało pamięci, w tym pamięci wirtualnej, ponieważ pliku reguł programu make jest zbyt duże lub zbyt złożone.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Aby rozwiązać problem, korzystając z poniższymi możliwymi rozwiązaniami

1. Zwolnij miejsce na dysku.

1. Zwiększenie rozmiaru pliku stronicowania systemu Windows NT lub pliku wymiany Windows.

1. Jeśli tylko część pliku reguł programu make jest używany, dzielenie pliku reguł programu make w osobnych plikach albo użyj **! Jeśli** dyrektywy, aby ograniczyć, które musi przetworzyć NMAKE przetwarzania wstępnego. **! Jeśli** dyrektywy zawierają **! Jeśli**, `!IFDEF`, **! IFNDEF**, **! Jeśli nie**, **! ELSE** `IFDEF`, i **! ELSE** `IFNDEF`.