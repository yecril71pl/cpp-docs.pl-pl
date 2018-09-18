---
title: Błąd BSCMAKE BK1514 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- BK1514
dev_langs:
- C++
helpviewer_keywords:
- BK1514
ms.assetid: 7c7e2504-a490-44ab-bb1f-47385ee2f4b0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 20f66c5c48547e92aef00568d5488a6293303be1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46094718"
---
# <a name="bscmake-error-bk1514"></a>Błąd BSCMAKE BK1514

wszystkie. Przycięty pliki SBR, nie znaleziono w nazwie pliku

Żaden z plików SBR dla aktualizacji były częścią oryginalnego pliku informacyjnego przeglądarki (.bsc). Aby znaleźć nazwy plików SBR, będących przyczyną tego błędu, przeczytaj [BK4502](../../error-messages/tool-errors/bscmake-warning-bk4502.md) ostrzeżeń, które należy poprzedzić go.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny

1. Problem nie określono nazwy pliku SBR lub .bsc.

1. Plik .bsc uszkodzony wymagany BSCMAKE skompilować go ponownie.