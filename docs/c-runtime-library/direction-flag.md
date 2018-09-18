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
ms.openlocfilehash: 7db91b20b76ef06130cbb8357344352b820ed731
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46093208"
---
# <a name="direction-flag"></a>Flaga kierunku

Flaga kierunku jest specyficzne dla procesorów Intel 80 x 86 flagą procesora CPU. Ma to zastosowanie do wszystkich instrukcji zestawu, korzystających z przedstawiciela (powtórzeń) prefiksem, na przykład MOVS MOVSD, MOVSW i inne. Jeśli flaga kierunku jest wyczyszczone, zwiększa się adresy podane odpowiednie instrukcje.

Procedury czasu wykonywania C zakładają, że flaga kierunku jest wyczyszczone. Jeśli używane są inne funkcje za pomocą funkcji wykonawczej języka C, upewnij się, że innych funkcji pozostaw Flaga kierunku samodzielnie lub przywrócenia stanu. Oczekiwano Flaga kierunku się jasne po wejściu sprawia, że kod wykonywalny, szybsze i wydajniejsze.

Funkcje biblioteki C Run-Time, takich jak procedury manipulowania ciągami i manipulowanie buforem oczekiwać, że flaga kierunku, aby możliwy.

## <a name="see-also"></a>Zobacz też

[Biblioteka CRT, funkcje](../c-runtime-library/crt-library-features.md)