---
title: Błąd krytyczny NMAKE U1051 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1051
dev_langs:
- C++
helpviewer_keywords:
- U1051
ms.assetid: fede5cd5-dac3-47b7-b86d-e1acfb78699f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d3d3a14b75a30aa22bcc9faafb97a218051bb080
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46045019"
---
# <a name="nmake-fatal-error-u1051"></a>Błąd krytyczny NMAKE U1051

Za mało pamięci

NMAKE za mało pamięci, w tym pamięci wirtualnej, ponieważ pliku reguł programu make jest zbyt duże lub zbyt złożone.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Aby rozwiązać problem, korzystając z poniższymi możliwymi rozwiązaniami

1. Zwolnij miejsce na dysku.

1. Zwiększenie rozmiaru pliku stronicowania systemu Windows NT lub pliku wymiany Windows.

1. Jeśli tylko część pliku reguł programu make jest używany, dzielenie pliku reguł programu make w osobnych plikach albo użyj **! Jeśli** dyrektywy, aby ograniczyć, które musi przetworzyć NMAKE przetwarzania wstępnego. **! Jeśli** dyrektywy zawierają **! Jeśli**, `!IFDEF`, **! IFNDEF**, **! Jeśli nie**, **! ELSE** `IFDEF`, i **! ELSE** `IFNDEF`.